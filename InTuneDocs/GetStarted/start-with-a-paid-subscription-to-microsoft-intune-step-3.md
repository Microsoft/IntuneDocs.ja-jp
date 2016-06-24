---
# required metadata

title: Active Directory を同期化して Intune にユーザーを追加する | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Active Directory を同期化して Intune にユーザーを追加する
ディレクトリの同期化によって、オンプレミスの Active Directory から Microsoft Azure Active Directory (Azure AD) にユーザー アカウントをインポートできます。 オンプレミスの Active Directory サービスが Azure Active Directory ベースの全サービスに反映され、ユーザー ID の管理が大幅に単純化されます。 また、シングル サインオン機能を構成することによってユーザー認証の利便性を高めることもできます。

より利便性を高めるには、同じ [Azure AD テナント](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)で複数のサービスを使用します。そうすると、以前に同期したユーザー アカウントを、同じ Azure AD テナントのサブスクリプションを共有するすべてのクラウドベースのサービスで利用できます。

## オンプレミスのユーザーを Azure AD と同期する
ユーザー アカウントを Azure AD と同期するために必要なツールは、[Azure AD Connect ウィザード](https://www.microsoft.com/download/details.aspx?id=47594)のみです。 Azure AD Connect ウィザードでは、簡単な画面の指示に従って、オンプレミスの ID インフラストラクチャをクラウドに接続できます。  目的のトポロジと要件 (単一ディレクトリと複数ディレクトリ、パスワードの同期、フェデレーションなど) を選ぶと、同期サービスや Active Directory フェデレーション サービス (AD FS)、Azure AD PowerShell モジュールなど、 接続した機能が稼働するために必要なすべてのコンポーネントが自動的に展開されて構成されます。

> [!TIP]
> Azure AD Connect には、過去に Dirsync や Azure AD Sync としてリリースされた機能がすべて備わっています。 [ディレクトリ統合](http://technet.microsoft.com/library/jj573653.aspx)の詳細を確認してください。 ローカル ディレクトリから Azure AD にユーザー アカウントを同期する利点の詳細については、「[Active Directory と Azure AD の類似点](http://technet.microsoft.com/library/dn518177.aspx)」を参照してください。.

## 管理者権限を付与する
Intune サブスクリプションにユーザーを追加した後で、ごく一部のユーザー アカウントに[管理者資格情報](administrative-accounts-websites-perms.md)を付与することをお勧めします。 管理者資格情報を割り当てるときに使うコンソールは、割り当てる管理者の種類によって異なります。

-   **テナント管理者**: 請求、クラウドの記憶域、Intune を使用できるユーザーの管理など、サブスクリプションを管理するには、**[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]**を使用して、この種類の管理者を割り当てます。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   **サービス管理者**: モバイル デバイスまたはコンピューターの管理、ポリシーまたはソフトウェアの展開、レポートの実行など、日常のタスクを管理するには、**[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]**を使用して、この種類の管理者を割り当てます。


### 次のステップ
これで終了です。 *Intune のクイック スタート ガイド*の手順 3. が完了しました。.

>[!div class="step-by-step"]

>[&larr; **ドメイン設定**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Intune のライセンスを管理する** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  


<!--HONumber=May16_HO1-->


