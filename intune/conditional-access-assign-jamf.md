---
title: Jamf デバイスのデバイス コンプライアンス ポリシー | Microsoft Intune
titlesuffix: Microsoft Intune
description: Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使って、Jamf で管理されるデバイスをセキュリティ保護できます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d7d054b11a4abc969ad411169d0222be37fd6711
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817230"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro で管理された Mac にコンプライアンスを適用します

適用先:Azure Portal での Intune

Azure Active Directory および Microsoft Intune の条件付きアクセス ポリシーを使用して、エンド ユーザーが組織の要件に準拠することを確実にできます。 これらのポリシーは [Jamf Pro で管理されている](conditional-access-integrate-jamf.md) Mac に適用できます。 これには、Intune と Jamf Pro の両方のコンソールへのアクセスが必要です。

## <a name="set-up-device-compliance-policies-in-intune"></a>Intune のデバイス コンプライアンス ポリシーを設定する

1. Microsoft Azure を開き、**[Intune]** > **[デバイスのポリシー準拠]** > **[ポリシー]** に移動します。 準拠していないユーザーとグループに対する一連のアクション (警告の電子メールの送信など) の選択を含む、macOS 用のポリシーを作成できます。
2. 目的のグループを検索し、それらにポリシーを適用します。

> [!Note]
> Intune では、ポリシーに準拠するためにディスク全体の暗号化が必要です。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>macOS 用ポータル サイト アプリを Jamf Pro に展開する

以下の手順に従って、macOS 用ポータル サイト アプリをバックグラウンドのインストールとして Jamf Pro に展開する必要があります。

1. macOS デバイスで、[macOS 用のポータル サイト アプリ](https://go.microsoft.com/fwlink/?linkid=862280)の現在のバージョンをダウンロードします。 インストールはしないでください。Jamf Pro にアップロードするには、アプリのコピーが必要です。
2. Jamf Pro を開き、**[コンピューターの管理]** > **[パッケージ]** に移動します。
3. macOS 用のポータル サイト アプリで新しいパッケージを作成し、**[保存]** をクリックします。
4. **[コンピューター]** > **[ポリシー]** を開き、**[新規]** を選択します。
5. **[全般]** ペイロードを使用して、ポリシーの設定を構成します。 これらの設定は次のとおりです。
   - トリガー: **[登録完了]** と **[Recurring Check-in]\(定期的なチェックイン\)** を選択します。
   - 実行の頻度: **[Once per computer]\(コンピューターにつき 1 回\)** を選択します。
6. **[パッケージ]** ペイロードを選択し、**[構成]** をクリックします。
7. **[追加]** をクリックし、ポータル サイト アプリでパッケージを選択します。
8. **[アクション]** ポップアップ メニューから **[インストール]** を選択します。
9. パッケージの設定を構成します。
10. **[スコープ]** タブをクリックし、ポータル サイト アプリをインストールするコンピューターを指定します。 **[Save]**(保存) をクリックします。 ポリシーは、次回、選択したトリガーがコンピューターで発生し、**[全般]** ペイロードの条件を満たしている場合にスコープのデバイスで実行されます。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>ユーザーに Azure Active Directory で自分のデバイスを登録させるためのポリシーを Jamf Pro で作成する

> [!NOTE]
> 次の手順に進む前に、macOS 用の[ポータル サイトの展開](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)を行う必要があります。  

エンドユーザーは、デバイスを Jamf Pro によって管理されるデバイスとして Azure AD で登録するために、Jamf セルフ サービスを経由してポータル サイト アプリを起動する必要があります。 この場合、エンドユーザーは操作を実行する必要があります。 電子メール、Jamf Pro 通知、またはエンドユーザーへの他の通知方法を通して、Jamf セルフ サービスでボタンをクリックするように[エンド ユーザーに連絡する](end-user-educate.md)ことをお勧めします。

> [!WARNING]
> ポータル サイト アプリを Jamf セルフ サービスから起動してデバイスの登録を開始する必要があります。 <br><br>ポータル サイト アプリを手動で起動した場合 (たとえば、アプリケーション フォルダーまたはダウンロード フォルダーから起動)、デバイスは登録されません。 エンドユーザーがポータル サイトを手動で起動した場合は、"AccountNotOnboarded" という警告が表示されます。

1. Jamf Pro で **[コンピューター]** > **[ポリシー]** に移動し、デバイス登録用の新しいポリシーを作成します。
2. トリガーや実行の頻度など、**[Microsoft Intune 統合]** ペイロードを構成します。
3. **[スコープ]** タブをクリックし、ポリシーのスコープをすべての対象デバイスにします。
4. **[セルフ サービス]** タブをクリックし、Jamf セルフ サービスでポリシーを利用可能にします。 ポリシーを **[デバイスのポリシー準拠]** カテゴリに含めます。 **[Save]**(保存) をクリックします。

## <a name="removing-a-jamf-managed-device-from-intune"></a>Intune から Jamf で管理されたデバイスを削除する

**[すべてのデバイス]** ビューで **[削除]** を選択することで、Intune コンソールから Jamf で管理されるデバイスを削除できます。 複数のデバイスを選択し、**[削除]** をクリックすることで、デバイスの一括削除を有効にすることができます。

Jamf で管理されるデバイスの削除方法については、[Jamf Pro のドキュメント](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)を参照してください。[Jamf サポート](https://www.jamf.com/support/)にサポート チケットを提出して、さらなる支援を受けることもができます。 

## <a name="next-steps"></a>次の手順

- [Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory の条件付きアクセスの概要](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
