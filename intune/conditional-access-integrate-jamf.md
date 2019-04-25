---
title: コンプライアンスのために Jamf Pro を Microsoft Intune と統合する
titleSuffix: Microsoft Intune
description: Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使って、Jamf で管理されるデバイスをセキュリティ保護できます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57527d0b1825d0e8d3fefb63d1b960ab3fb5c676
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508125"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>コンプライアンスのために Jamf Pro を Intune と統合する

適用対象:Azure Portal での Intune

組織で [Jamf Pro](https://www.jamf.com) を使用してエンド ユーザーの Mac を管理している場合、Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使用して、組織内のデバイスがコンプライアンスに確実に準拠するようにできます。

## <a name="prerequisites"></a>必要条件

Jamf Pro で条件付きアクセスを構成するには、次のものが必要です。

- Jamf Pro 10.1.0 以降
- [macOS 用ポータル サイト アプリ](https://aka.ms/macoscompanyportal)
- OS X 10.11 Yosemite 以降を使用する macOS デバイス

## <a name="connecting-intune-to-jamf-pro"></a>Intune の Jamf Pro への接続

Intune を Jamf Pro に接続するには、次の手順に従います。

1. Azure で新しいアプリケーションを作成する
2. Intune の Jamf Pro との統合を有効にする
3. Jamf Pro で条件付きアクセスを構成する

## <a name="create-an-application-in-azure-active-directory"></a>Azure Active Directory でアプリケーションを作成する

1. [Azure portal](https://portal.azure.com) で、**[Azure Active Directory]** > **[アプリの登録]** に移動します。
2. **[新しいアプリケーションの登録]** を選択します。
3. 「**Jamf 条件付きアクセス**」など、**表示名**を入力します。
4. **[Web アプリ/API]** を選択します。
5. Jamf Pro インスタンス URL を使用して、**サインオン URL** を指定します。
6. **[作成]** を選択します。 アプリケーションが作成され、ポータルにアプリケーションの詳細が表示されます。
7. 新しいアプリケーションの**アプリケーション ID** のコピーを保存します。 後の手順でこの ID を指定します。 次に、**[設定]** を選択し、**[API アクセス]** > **[キー]** に移動します。
8. *[キー]* ウィンドウで、**[説明]** と**有効期限**までの待機時間を指定し、**[保存]** を選択して、アプリケーション キー (値) を生成します。

   > [!IMPORTANT]
   > アプリケーション キーは、このプロセス中 1 回のみ表示されます。 簡単に取得できる場所に保存してください。

8. アプリの *[設定]* ウィンドウで、**[API アクセス]** > **[必要なアクセス許可]** に移動します。 既存のアクセス許可を選択し、**[削除]** をクリックして、すべてのアクセス許可を削除します。 新しいアクセス許可を追加する際には、既存のアクセス許可を削除する必要があります。アプリケーションは、1 つの必要なアクセス許可がある場合にのみ機能します。  
9. 新しいアクセス許可を割り当てるには、**[+ 追加]** > **[API を選択します]** > **[Microsoft Intune API]** を選択し、**[選択]** をクリックします。
10. *[アクセスの有効化]* ウィンドウで、**[Send device attributes to Microsoft Intune]\(Microsoft Intune にデバイスの属性を送信する\)** を選択し、**[選択]**、**[完了]** の順にクリックします。
11. *[必要なアクセス許可]* ウィンドウで、**[アクセス許可の付与]**、**[はい]** の順に選択して、アプリケーションに必要なアクセス許可を適用します。

    > [!NOTE]
    > アプリケーション キーが期限切れになった場合は、Microsoft Azure で新しいアプリケーション キーを作成し、Jamf Pro で条件付きアクセス データを更新する必要があります。 Azure では、サービスの中断を防ぐため、古いキーと新しいキーの両方をアクティブにすることができます。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Intune の Jamf Pro との統合を有効にする

1. [Azure portal](https://portal.azure.com) で、**[Microsoft Intune]** > **[デバイスのポリシー準拠]** > **[パートナー デバイスの管理]** に移動します。
2. 前の手順で保存したアプリケーション ID を **[Jamf Azure Active Directory App ID]** フィールドに貼り付けることによって、Jamf 用コンプライアンス コネクタを有効にします。
3. **[保存]** を選択します。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Jamf Pro で Microsoft Intune 統合を構成する

1. Jamf Pro で、**[グローバル管理]** > **[条件付きアクセス]** に移動します。 **[Microsoft Intune 統合]** タブの **[編集]** ボタンをクリックします。
2. **[Microsoft Intune 統合の有効化]** チェック ボックスをオンにします。
3. 前の手順で保存した、**場所**、**ドメイン名**、**アプリケーション ID**、**アプリケーション キー**を含む、Azure テナントについての必要な情報を入力します。
4. **[保存]** を選択します。 Jamf Pro は設定をテストし、成功を確認します。

## <a name="set-up-compliance-policies-and-register-devices"></a>コンプライアンス ポリシー設定してデバイスを登録する

Intune と Jamf の統合を構成したら、[Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)必要があります。



## <a name="next-steps"></a>次の手順

- [Jamf で管理されたデバイスにコンプライアンス ポリシーを適用する](conditional-access-assign-jamf.md)
- [Jamf から Intune に送られるデータ](data-jamf-sends-to-intune.md)
