---
title: Intune ポータルサイトと DISA Purebred を使用して iOS または iPadOS デバイスを登録する
description: IOS または iPadOS デバイスを登録し、DISA Purebred を使用して派生された資格情報の認証を設定する方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c484b98466c1418016f4ebc6cc805e412d7891e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415790"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>ポータルサイトと DISA Purebred を使用して iOS または iPadOS デバイスを設定する  

組織の電子メール、ファイル、およびアプリに安全にモバイルからアクセスするために、Intune ポータル サイト アプリでデバイスを登録します。 デバイスが登録されると、*マネージド*になります。 組織は、Intune などのモバイル デバイス管理 (MDM) プロバイダーを介してデバイスにポリシーとアプリを割り当てることができます。  

登録時に、デバイスに派生した資格情報もインストールします。 リソースにアクセスする場合、または電子メールに署名して暗号化する場合は、認証方法として派生資格情報の使用が必要になることがあります。 

スマートカードを使用して次のことを行う場合は、派生した資格情報を設定する必要があります。

* 学校または仕事用アプリ、Wi-fi、仮想プライベートネットワーク (VPN) にサインインする
* S/MIME 証明書を使用して学校または勤務先の電子メールに署名して暗号化する  

この記事では、次のことについて説明します。  

   * Intune ポータルサイトを使用して、モバイル iOS または iPadOS デバイスを登録します。  
   * 組織の派生資格情報プロバイダーである[Disa Purebred](https://cyber.mil/pki-pke/purebred/)から派生した資格情報を取得します。  

## <a name="what-are-derived-credentials"></a>派生した資格情報とは何ですか。  
派生資格情報は、スマートカードの資格情報から派生した証明書で、デバイスにインストールされます。 これにより、承認されていないユーザーが機密情報にアクセスするのを防ぐと同時に、作業リソースへのリモートアクセスが許可されます。  

派生した資格情報は、次の場合に使用されます。 
* 学校または仕事用アプリ、Wi-fi、VPN にサインインする学生と従業員を認証します
* S/MIME 証明書を使用して学校または職場の電子メールに署名して暗号化する

派生資格情報は、Special Publication (SP) 800-157 に含まれている Derived Personal Identity Verification (PIV) 資格情報に対する米国標準技術研究所 (NIST) ガイドラインの実装です。  

## <a name="prerequisites"></a>必要条件

 登録を完了するには、次のものが必要です。

* 学校または職場提供のスマートカード
* スマートカードを使用してサインインできるコンピューターまたはキオスクへのアクセス
* モバイル デバイス
* デバイスにインストールされている iOS および iPadOS 用の Intune ポータルサイトアプリ   

また、セットアップ中に Purebred エージェントまたは担当者に問い合わせる必要があります。      

## <a name="enroll-device"></a>デバイスを登録する  
1. モバイルデバイスで iOS/iPadOS のポータルサイトアプリを開き、職場のアカウントでサインインします。  

2. 画面上のコードを書き留めます。  

    ![画面に表示されるメッセージとコードを使用したポータルサイトアプリの画像の例。](./media/copy-code-intercede.png)  
3. スマートカード対応のデバイスに切り替えて、 https://microsoft.com/devicelogin に移動します。 
4. 前に書き留めたコードを入力します。  

    ![ポータルサイト web サイトの "Enter code" プロンプトのスクリーンショットの例。](./media/enter-code-intercede.png)   

5. スマートカードを挿入してサインインします。  
6. モバイルデバイスのポータルサイトアプリに戻り、画面の指示に従ってデバイスを登録します。  
7. 登録が完了すると、ポータルサイトによって、スマートカードのセットアップが通知されます。 通知をタップします。 通知が表示されない場合は、電子メールを確認してください。   

    ![デバイスのホーム画面でのポータルサイトプッシュ通知のスクリーンショットの例。](./media/action-required-in-app-intercede.png)  
8. **[モバイルスマートカードアクセスのセットアップ]** 画面で、次のようにします。  
    」を参照します。 組織の設定手順へのリンクをタップします。 組織で追加の手順が提供されていない場合は、この記事に送信します。  
    b. **[開く]** をクリックして、Purebred アプリを開きます。  

    ![モバイルスマートカードアクセス画面のセットアップポータルサイトのスクリーンショットの例。](./media/smart-card-open-disa-purebred.png)  
9. Purebred Registration アプリを開くポータルサイトを許可するように求めるメッセージが表示されたら、 **[開く]** を選択します。   

    ![DISA Purebred アプリを開くためのポータルサイトプロンプトのスクリーンショットの例。](./media/open-app-prompt-disa-purbred.png)  
10. アプリが動作する場合は、組織の Purebred エージェントと連携して、Purebred 事前登録構成プロファイルを構成してダウンロードします。   
11. 設定アプリ >**全般** > **プロファイル & デバイス管理** > **インストールプロファイルをインストール**し、 **[インストール]** をタップします。  
12. デバイスのパスコードを入力します。  
13. プロファイルをインストールします。 インストールを開始するには、複数**回タップする**必要がある場合があります。 
14. Purebred Registration アプリに戻ります。 Purebred エージェントの指示に従って続行します。  
 
15. 構成プロファイルをダウンロードした後、設定 アプリ > **全般** > **プロファイル & デバイス管理** > **インストールプロファイル** の順に開き、**インストール** をタップします。   
16.  デバイスのパスコードを入力します。
17. プロファイルをインストールします。 インストールを開始するには、複数**回タップする**必要がある場合があります。 
18. インストールが完了したら、ポータルサイトアプリに戻ります。  
19.  **[モバイルスマートカードアクセスのセットアップ]** 画面で、 **[続行]** をタップします。  

20. **[証明書のインポート]** 画面で、Disa Purebred から取得した派生資格情報を取得してインポートします。  

    」を参照します。 **[続行]** をタップします。   

    ![のポータルサイト [証明書のインポート] 画面のスクリーンショットの例を次に示します。](./media/import-certificate-disa-purebred.png)  
    b. ICloud ドライブに移動して > の**場所**を**参照**し、 **[その他の場所]** をタップします。  

    iCloud ドライブの例を ![、[参照] メニューで [その他の場所] オプションを強調表示します。](./media/icloud-drive-more-locations.png)  
    c. スイッチをタップして、 **Purebred キーチェーン**を有効にします。  

    ![Purebred キーチェーンスイッチが有効になっていることを強調する iCloud ドライブの参照ビューのスクリーンショットの例。](./media/icloud-drive-enable-purebred-keychain.png)   

    d. **Purebred Credential Package (資格情報パッケージ**) をタップします。  

    選択可能な Purebred Credential Package オプションを使用した iOS 画面のスクリーンショットの例を ![します。](./media/purebred-credential-package.png)  
    f. 証明書の一覧が表示されます。 1つを選択し、 **[キーのインポート]** をタップします。  

    ![選択可能な証明書の一覧のスクリーンショットの例 (既に選択されているもの)。](./media/import-purebred-keychain.png) 
21. ポータルサイトアプリに戻り、ポータルサイトがデバイスのセットアップを完了するまで待ちます。   

## <a name="next-steps"></a>次の手順  
登録が完了すると、電子メール、Wi-fi、組織によって提供されるすべてのアプリなどの職場リソースにアクセスできるようになります。 でアプリを取得、検索、インストール、およびアンインストールする方法の詳細についてはポータルサイト「」を参照してください。

* [ポータル サイト Web サイトからアプリを管理する](manage-apps-cpweb.md)  
* [デバイスで管理対象アプリを使用する](use-managed-apps-on-your-device-ios.md)  

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
