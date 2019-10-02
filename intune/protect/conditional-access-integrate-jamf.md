---
title: コンプライアンスのために Jamf Pro を Microsoft Intune と統合する
titleSuffix: Microsoft Intune
description: Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使って、Jamf で管理されるデバイスをセキュリティ保護できます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722723"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>コンプライアンスのために Jamf Pro を Intune と統合する

適用対象:Azure Portal での Intune

組織で [Jamf Pro](https://www.jamf.com) を使用してエンド ユーザーの Mac を管理している場合、Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使用して、組織内のデバイスがコンプライアンスに確実に準拠するようにできます。

## <a name="prerequisites"></a>必要条件

Jamf Pro で条件付きアクセスを構成するには、次のものが必要です。

- Jamf Pro 10.1.0 以降
- [macOS 用ポータル サイト アプリ](https://aka.ms/macoscompanyportal)
- OS X 10.11 Yosemite 以降を使用する macOS デバイス

## <a name="connect-intune-to-jamf-pro"></a>Intune を Jamf Pro に接続する

Intune を Jamf Pro に接続するには:

1. Azure 内で新しいアプリケーションを作成します。
2. Intune の Jamf Pro との統合を有効にします。
3. Jamf Pro 内で条件付きアクセスを構成します。

## <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory でアプリケーションを作成する

1. [Azure portal](https://portal.azure.com) で、 **[Azure Active Directory]**  >  **[アプリの登録]** に移動し、 **[New registration]\(新規登録\)** を選択します。 

2. **[アプリケーションの登録]** ページで、次の詳細を指定します。
   - **[名前]** セクションで、わかりやすいアプリケーション名を入力します (例: **Jamf 条件付きアクセス**)。
   - **[サポートされているアカウントの種類]** セクションで、 **[任意の組織のディレクトリ内のアカウント]** を選択します。 
   - **[リダイレクト URI]** については、既定値の [Web] のままにして、Jamf Pro インスタンスの URL を指定します。  

3. **[登録]** を選択してアプリケーションを作成し、新しいアプリの **[概要]** ページを開きます。  

4. アプリの **[概要]** ページで、 **[Application (client) ID]\(アプリケーション \(クライアント\) ID\)** の値をコピーし、後で使うので記録しておきます。 この値は後の手順で必要になります。  

5. **[管理]** の **[証明書とシークレット]** を選択します。 **[New client secret]\(新しいクライアント シークレット\)** ボタンを選択します。 **[説明]** に値を入力し、 **[有効期限]** で任意のオプションを選択して、 **[追加]** を選択します。

   > [!IMPORTANT]  
   > このページを終了する前に、クライアント シークレットの値をコピーし、後で使うので記録しておきます。 この値は後の手順で必要になります。 この値は、アプリの登録を作り直さない限り、再び入手することはできません。  

6. **[管理]** で **[API のアクセス許可]** を選択します。 既存のアクセス許可を選択して **[アクセス許可の削除]** を選択し、それらのアクセス許可を削除します。 これから新しいアクセス許可を追加しますが、アプリケーションは必要なアクセス許可が 1 つある場合にのみ機能するので、既存のアクセス許可をすべて削除する必要があります。  

7. 新しいアクセス許可を割り当てるには、 **[アクセス許可の追加]** を選択します。 **[API アクセス許可の要求]** ページで、 **[Intune]** を選択して、 **[アプリケーションのアクセス許可]** を選択します。 **update_device_attributes** のチェック ボックスだけをオンにします。  

   **[アクセス許可の追加]** を選択して、この構成を保存します。  

8. **[API のアクセス許可]** ページで、 **[Microsoft に管理者の同意を与えます]** を選択して、 **[はい]** を選択します。  

   Azure AD でのアプリの登録プロセスは完了です。


    > [!NOTE]
    > クライアント シークレットの有効期限が切れた場合は、Azure で新しいクライアント シークレットを作成し、Jamf Pro で条件付きアクセス データを更新する必要があります。 Azure では、サービスの中断を防ぐため、古いシークレットと新しいキーの両方をアクティブにすることができます。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune の Jamf Pro との統合を有効にする

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[Microsoft Intune]**  >  **[デバイスのポリシー準拠]**  >  **[パートナー デバイスの管理]** に移動します。

2. 前の手順で保存したアプリケーション ID を **[Jamf Azure Active Directory App ID]** フィールドに貼り付けることによって、Jamf 用コンプライアンス コネクタを有効にします。

3. **[保存]** を選択します。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro で Microsoft Intune 統合を構成する

1. Jamf Pro で、 **[グローバル管理]**  >  **[条件付きアクセス]** に移動します。 **[macOS Intune Integration]\(macOS Intune 統合\)** タブの **[編集]** ボタンをクリックします。

2. **[Enable Intune Integration for macOS]\(macOS の Intune 統合の有効化\)** チェック ボックスをオンにします。

3. **場所**、**ドメイン名**、**アプリケーション ID**、およびアプリを作成するときに Azure AD に保存した*クライアント シークレット*の値など、Azure テナントについての必要な情報を入力します。  

4. **[保存]** を選択します。 Jamf Pro によって設定がテストされ、成功したことが確認されます。

## <a name="set-up-compliance-policies-and-register-devices"></a>コンプライアンス ポリシー設定してデバイスを登録する

Intune と Jamf の統合を構成したら、[Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)必要があります。

## <a name="disconnect-jamf-pro-and-intune"></a>Jamf Pro と Intune を切断する 

Jamf Pro を使用して組織内の Mac を管理しなくなった場合、ユーザーを Intune で管理するには、Jamf Pro と Intune 間の接続を削除する必要があります。 Jamf Pro コンソールを使用して接続を削除します。 

1. Jamf Pro で、 **[グローバル管理]**  >  **[条件付きアクセス]** に移動します。 **[macOS Intune Integration]\(macOS Intune 統合\)** タブで、 **[編集]** を選択します。
2. **[Enable Intune Integration for macOS]\(macOS の Intune 統合の有効化\)** チェック ボックスをオフにします。
3. **[保存]** を選択します。 Jamf Pro によって構成が Intune に送信され、統合が終了します。
4. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。 **[Microsoft Intune]**  >  **[デバイスのポリシー準拠]**  >  **[パートナー デバイスの管理]** に移動して、状態が **[終了]** になっていることを確認します。 

   > [!NOTE]
   > 組織の Mac デバイスは、コンソールに表示されている日付 (3 か月後) に削除されます。 

## <a name="next-steps"></a>次の手順

- [Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)
- [Jamf から Intune に送られるデータ](data-jamf-sends-to-intune.md)
