---
title: Sophos Mobile と Intune の統合をセットアップする
titleSuffix: Intune on Azure
description: Microsoft Intune で Sophos Mobile ソリューションをセットアップし、モバイル デバイスから会社のリソースへのアクセスを制御する方法。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aad6268606dfcf69c304bb5c5b270c8c4795e4b2
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72681283"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Sophos Mobile を Intune と統合する  

Sophos Mobile Threat Defense ソリューションを Intune と統合するには、次の手順を実行します。  

> [!NOTE]
> この Mobile Threat Defense ベンダーは、未登録のデバイスではサポートされていません。

## <a name="before-you-begin"></a>始める前に  

Sophos Mobile と Intune の統合を始める前に、次のものがあることを確認します。  
- Microsoft Intune サブスクリプション  
- 次のアクセス許可を付与する Azure Active Directory 管理者資格情報:  
  - サインインしてユーザー プロファイルを読み取る  
  - サインインしたユーザーとしてディレクトリにアクセスする  
  - ディレクトリ データの読み込み  
  - Intune にデバイス情報を送信する  
- Sophos Mobile 管理コンソールにアクセスするための管理者資格情報。  


### <a name="sophos-mobile-app-authorization"></a>Sophos Mobile アプリの承認  
  
Sophos Mobile アプリの承認プロセスは以下で構成されます。  
- Sophos Mobile サービスがデバイスの正常性状態に関する情報を Intune に戻すことが許可されます。  
- Sophos Mobile が Azure AD 登録グループ メンバーシップと同期され、そのデバイスのデータベースに入力が行われます。  
- Sophos Mobile 管理コンソールが Azure AD シングル サインオン (SSO) を使用できるようになります。  
- Sophos Mobile アプリで Azure AD SSO を使用してサインインできるようになります。  


## <a name="to-set-up-sophos-mobile-integration"></a>Sophos Mobile の統合を設定するには  

1. [Azure portal]( https://portal.azure.com/) にサインインし、 **[Intune]**  >  **[デバイスのポリシー準拠]**  >  **[Mobile Threat Defense]** の順に移動し、 **[追加]** を選択します。  
2. **[コネクタの追加]** ページで、ドロップダウン リストを使用して **[Sophos]** を選択します。 次いで **[作成]** を選択します。  
3. *[Open the Sophos admin console]* \(Sophos の管理者コンソールを開く\) のリンクを選択します。  
4. Sophos の資格情報を使用して、[Sophos の管理コンソール](https://central.sophos.com/)にサインインします。  
5. **[モバイル]**  >  **[設定]**  >  **[セットアップ]**  >  **[Sophos setup]** \(Sophos のセットアップ\) に移動します。  
6. **[Sophos setup]** \(Sophos のセットアップ\) ページで、 **[Intune MTD]** \(Intune MTD\) タブを選択します。  
   ![Sophos のセットアップ](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. **[Bind]** \(バインド\)、 **[はい]** の順に選択します。 Sophos が Intune に接続し、お使いの Intune サブスクリプションへのサインインを求めます。 
8. Microsoft Intune の認証ウィンドウで Intune の資格情報を入力し、*Sophos Mobile Thread Defense* に対するアクセス許可に **[同意する]** を選択します。  
   ![Intune の認証](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. **[Sophos setup]** \(Sophos のセットアップ\) ページで **[保存]** を選択し、Intune の構成を完了します。  
   ![Sophos のセットアップの保存](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. **[Successful Integration]** (統合に成功しました) というメッセージが表示されると統合は完了です。  
1. これで Intune のコンソールで Sophos を使用できます。  


## <a name="next-steps"></a>次の手順  
[Sophos のクライアント アプリを構成する](mtd-apps-ios-app-configuration-policy-add-assign.md)
