---
title: Jamf デバイスのデバイス コンプライアンス ポリシー
titleSuffix: Microsoft Intune
description: Microsoft Intune コンプライアンス ポリシーと Azure Active Directory の条件付きアクセスを使って、Jamf で管理されるデバイスをセキュリティ保護できます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74161596"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Jamf Pro で管理された Mac にコンプライアンスを適用します

[Jamf Pro を Intune と統合する](conditional-access-integrate-jamf.md)と、条件付きアクセス ポリシーを使用して、組織の要件に従って Mac デバイスにコンプライアンスを適用できるようになります。  この記事では、次のタスクについて説明します。  

- 条件付きアクセス ポリシーを作成する。
- Jamf Pro を構成して、Jamf で管理するデバイスに Intune ポータル サイト アプリを展開します。
- Jamf Self Service アプリ内から起動するポータル サイト アプリにデバイス ユーザーがサインインするときに、Azure AD に登録するようにデバイスを構成します。 デバイス登録によって Azure AD の ID が確立され、条件付きアクセス ポリシーによって、会社のリソースへのアクセスについてデバイスを評価できるようになります。  
 
この記事の手順では、Intune と Jamf Pro の両方のコンソールにアクセスする必要があります。

## <a name="set-up-device-compliance-policies-in-intune"></a>Intune のデバイス コンプライアンス ポリシーを設定する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]**  >  **[コンプライアンス ポリシー]** の順に選択します。 以前に作成したポリシーを使用している場合は、コンソールでそのポリシーを選択し、この手順の次の手順に進みます。 新しいポリシーを作成する場合は、 **[ポリシーの作成]** を選択してから、**macOS** の *[プラットフォーム]* を含むポリシーの詳細を指定します。 組織の要件を満たすように *[設定]* と *[コンプライアンス非対応に対するアクション]* を構成してから、 **[作成]** を選択してポリシーを保存します。

3. ポリシーの *[概要]* ウィンドウで **[割り当て]** を選択します。 使用できるオプションを使用して、このポリシーを受け取る Azure Active Directory (Azure AD) ユーザーとセキュリティ グループを構成します。 Jamf と Intune の統合では、デバイス グループを対象とするコンプライアンス ポリシーがサポートされません。

4. **[保存]** を選択すると、ポリシーがユーザーに展開されます。  

展開するポリシーは、割り当てられたユーザーによって使用されるデバイスを対象とします。 これらのデバイスのコンプライアンスが評価されます。 準拠しているデバイスは、Azure AD の *[デバイスは準拠としてマーク済みである必要があります]* 設定について準拠とマークされます。  

> [!NOTE]
> Intune では、ポリシーに準拠するためにディスク全体の暗号化が必要です。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>macOS 用ポータル サイト アプリを Jamf Pro に展開する

Jamf Pro でポリシーを作成して Intune ポータル サイトを展開します。 このポリシーではポータル サイト アプリが展開され、Jamf Self Service で使用できるようになります。 ユーザーが Azure AD にデバイスを登録できるようにするには、このポリシーを作成してから、Jamf Pro でポリシーを作成します。  

次の手順を完了するには、macOS デバイスと Jamf Pro ポータルにアクセスする必要があります。 

### <a name="to-deploy-the-company-portal-app"></a>ポータル サイト アプリを展開するには  

1. macOS デバイスに、最新バージョンの [macOS 用ポータル サイト アプリ](https://go.microsoft.com/fwlink/?linkid=862280)をダウンロードします (ただし、インストールしません)。 アプリを Jamf Pro にアップロードできるようにするために必要なものは、アプリのコピーのみです。  

2. Jamf Pro を開き、 **[Computer management]\(コンピューターの管理\)**  >  **[Packages]\(パッケージ\)** に移動します。

3. macOS 用のポータル サイト アプリで新しいパッケージを作成し、 **[保存]** を選択します。

4. **[コンピューター]**  >  **[ポリシー]** を開き、 **[新規]** を選択します。

5. **[全般]** ペイロードを使用して、ポリシーの設定を構成します。 これらの設定は次のとおりです。
   - トリガー: **[登録完了]** と **[Recurring Check-in]\(定期的なチェックイン\)** を選択します。
   - 実行の頻度: **[Once per computer]\(コンピューターにつき 1 回\)** を選択します。

6. **[パッケージ]** ペイロードを選択し、 **[構成]** をクリックします。

7. **[追加]** をクリックし、ポータル サイト アプリでパッケージを選択します。

8. **[アクション]** ポップアップ メニューから **[インストール]** を選択します。
9. パッケージの設定を構成します。

10. **[スコープ]** タブを選択し、ポータル サイト アプリをインストールするコンピューターを指定します。 **[保存]** を選択します。 ポリシーは、次回、選択したトリガーがコンピューターで発生し、 **[全般]** ペイロードの条件を満たしている場合にスコープのデバイスで実行されます。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>ユーザーに Azure Active Directory で自分のデバイスを登録させるためのポリシーを Jamf Pro で作成する  

Jamf Pro Self Service を使用して macOS 用の[ポータル サイトを展開](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)した後は、ユーザーのデバイスを Azure AD に登録する Jamf Pro ポリシーを作成できるようになります。 

デバイス登録を行うには、デバイス ユーザーが Jamf Self Service 内から手動で Intune ポータル サイト アプリを選択する必要があります。 メール、Jamf Pro の通知、または組織が使用しているその他の方法で[エンド ユーザーに連絡し](../fundamentals/end-user-educate.md)、この操作を完了してデバイスを登録するように指示することをお勧めします。 

> [!WARNING]
> ポータル サイト アプリを手動で起動した場合 (たとえば、アプリケーション フォルダーまたはダウンロード フォルダーから起動)、デバイスは登録されません。 デバイス ユーザーがポータル サイトを手動で起動した場合は、"**AccountNotOnboarded**" という警告が表示されます。

### <a name="to-create-the-registration-policy"></a>登録ポリシーを作成するには  

1. Jamf Pro で **[Computers]\(コンピューター\)**  >  **[Policies]\(ポリシー\)** に移動し、デバイス登録用の新しいポリシーを作成します。

2. トリガーや実行の頻度など、 **[Microsoft Intune 統合]** ペイロードを構成します。

3. **[スコープ]** タブを選択し、ポリシーのスコープをすべての対象デバイスに限定します。

4. **[セルフ サービス]** タブを選択し、Jamf Self Service でポリシーを利用可能にします。 ポリシーを **[デバイスのポリシー準拠]** カテゴリに含めます。 **[Save]** (保存) をクリックします。

## <a name="validate-intune-and-jamf-integration"></a>Intune と Jamf の統合を検証する  

Jamf Pro コンソールを使用して、Jamf Pro と Microsoft Intune 間の通信が成功していることを確認します。 

- Jamf Pro で、 **[Settings]\(設定\)**  >  **[Global Management]\(グローバル管理\)**  >  **[Microsoft Intune Integration]\(Microsoft Intune の統合\)** に移動し、 **[Test]\(テスト\)** を選択します。

    コンソールには、接続が成功したか失敗したかを示すメッセージが表示されます。  

Jamf Pro コンソールからの接続テストが失敗する場合は、Jamf の構成を確認します。 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Intune から Jamf で管理されたデバイスを削除する

Jamf で管理されているデバイスを削除するには、Microsoft Endpoint Manager 管理センターを開き、 **[デバイス]**  >  **[すべてのデバイス]** の順に選択してそのデバイスを選択した後、 **[削除]** を選択します。  複数のデバイスを選択し、 **[削除]** をクリックすることで、デバイスの一括削除を有効にすることができます。

Jamf で管理されるデバイスの削除方法については、[Jamf Pro のドキュメント](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)を参照してください。[Jamf サポート](https://www.jamf.com/support/)にサポート チケットを提出して、さらなる支援を受けることもができます。 

## <a name="next-steps"></a>次の手順

- [Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Azure Active Directory の条件付きアクセスの概要](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
