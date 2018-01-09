---
title: "Intune で PKCS 証明書を構成して管理する"
titleSuffix: Intune on Azure
description: "Intune で PKCS 証明書を作成して割り当てます。"
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: angrobe
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a51d260718e0d0c3984966fab69e202b854c1847
ms.sourcegitcommit: b2467a653ffd36c2248a30b69cb88e3dc7cca2ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2017
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Intune で PKCS 証明書を構成して管理する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="requirements"></a>要件

Intune でPKCS 証明書を使用するには、次のようなインフラストラクチャが必要です。

* 構成済みの既存の Active Directory Domain Services (AD DS) ドメイン。
 
  AD DS のインストールや構成の方法の詳細については、「[AD DS の設計と計画](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)」の記事をご覧ください。

* 構成済みの既存のエンタープライズ証明機関 (CA)。

  Active Directory 証明書サービス (AD CS) のインストールや構成の方法の詳細が必要な場合は、「[Active Directory 証明書サービス ステップ バイ ステップ ガイド](https://technet.microsoft.com/library/cc772393)」の記事をご覧ください。

  > [!WARNING]
  > Intune ではスタンドアロン CA ではなく、エンタープライズ証明機関 (CA) の AD CS を実行する必要があります。

* エンタープライズ CA に接続されているクライアント。
* エンタープライズ CA のルート証明書のエクスポートされたコピーです。
* Intune ポータルからダウンロードされた Microsoft Intune Certificate Connector (NDESConnectorSetup.exe)。
* Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) をホスト可能な Windows Server。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>エンタープライズ CA からルート証明書をエクスポートする

VPN、WiFi、およびその他のリソースの認証には、各デバイスにルート CA 証明書または中間 CA 証明書が必要となります。 次の手順では、エンタープライズ CA から必要な証明書を取得する方法について説明します。

1. 管理特権があるアカウントでエンタープライズ CA にログインします。
2. コマンド プロンプトを管理者として開きます。
3. あとでアクセスできる場所にルート CA 証明書をエクスポートします。

   次に例を示します。

4.  ウィザードが完了した後、ウィザードを閉じる前に、**[証明書コネクタの UI を起動]** をクリックします。

   `certutil -ca.cert certnew.cer`

   詳細については、[証明書を管理するための Certutil タスク](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)に関する記事をご覧ください。

## <a name="configure-certificate-templates-on-the-certification-authority"></a>証明機関で証明書テンプレートを構成する

1. 管理特権があるアカウントでエンタープライズ CA にログインします。
2. **[証明機関]** コンソールを開きます。
3. **[証明書テンプレート]** を右クリックして、**[管理]** を選択します。
4. [**ユーザー**証明書テンプレート] に移動して右クリックし、**[テンプレートの複製]** を選択します。 **[新しいテンプレートのプロパティ]** ウィンドウが開きます。
5. **[互換性]** タブで次のように設定します。
   * **[証明機関]** に**[Windows Server 2008 R2]** を設定します。
   * **[証明書の受信者]** に**[Windows 7 / Server 2008 R2]** を設定します。
6. **[全般]** タブで次のように設定します。
   * **[テンプレート表示名]** にわかりやすい名前を設定します。

   > [!WARNING]
   > 既定では、**[テンプレート名]** は **[テンプレート表示名]** (*スペースなし*) と同じです。 後で使用するために、テンプレート名をメモします。

7. **[要求処理]** タブで **[プライベート キーのエクスポートを許可する]** ボックスをオンにします。
8. **[暗号化]** タブで、**[最小キー サイズ]** が 2048 に設定されていることを確認します。
9. **[サブジェクト名]** タブで、**[要求に含まれる]** ラジオ ボタンをオンにします。
10. **[拡張子]** タブで、**[アプリケーション ポリシー]** に暗号化ファイル システム、セキュリティで保護された電子メール、および クライアント認証が表示されていることを確認します。
    
      > [!IMPORTANT]
      > iOS および macOS の証明書テンプレートの場合、**[拡張]** タブで、**[キー使用法]** を編集し、**[署名は発行元の証明である]** がオンになっていないことを確認します。

11. **[セキュリティ]** タブで、Microsoft Intune Certificate Connector をインストールするサーバーのコンピューター アカウントを追加します。
    * このアカウントに、**読み取り**と**登録**のアクセス許可を割り当てます。
12. **[適用]** をクリックし、**[OK]** をクリックして証明書テンプレートを保存します。
13. **証明書テンプレート コンソール**を閉じます。
14. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして **[新規作成]** をクリックし、**[発行する証明書テンプレート]** をクリックします。
    * 上記の手順で作成したテンプレートを選択して、**[OK]** をクリックします。
15. Intune に登録されたデバイスとユーザーに代わって証明書を管理するサーバーの場合、次の手順を実行します。

    」を参照します。 証明機関を右クリックして、**[プロパティ]** を選択します。

    b. [セキュリティ] タブで、Microsoft Intune Certificate Connector を実行するサーバーのコンピューター アカウントを追加します。
      * このコンピューター アカウントに、**証明書の発行と管理**と**証明書の要求**のアクセス許可を付与します。
16. エンタープライズ CA からログアウトします。

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connector のダウンロード、インストール、および構成

![ConnectorDownload][ConnectorDownload]

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
2. **[Intune]** ブレードで、**[デバイス構成]** を選択します。 
3. **[デバイス構成]** ブレードで **[証明機関]** を選択します。 
4. **[追加]** をクリックして、**[Download Connector file]\(コネクタ ファイルのダウンロード\)** を選択します。 インストールするサーバーからアクセスできる場所にダウンロードしたものを保存します。 
5.  Microsoft Intune Certificate Connector をインストールするサーバーにログインします。
6.  インストーラーを実行し、既定の場所を受け入れます。 コネクタが C:\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe としてインストールされます。
    1. [インストーラー オプション] ページで、**[PFX 配布]** を選択して **[次へ]** をクリックします。
    2. **[インストール]** をクリックして、インストールが完了するまで待ちます。
    3. [完了] ページで、**[Intune コネクタの起動]** のラベルの付いたボックスをオンにして、**[完了]** をクリックします。
7.  [NDES コネクタ] ウィンドウが開いて、**[登録]** タブが表示されます。Intune への接続を有効にするには、**[サインイン]** をクリックして、管理アクセス許可を持つアカウントを指定します。
8.  **[詳細設定]** タブで、**[Use this computer's SYSTEM account]\(このコンピューターのシステム アカウントを使用する\)** (既定値) ラジオ ボタンをオンのままにします。
9.  **[適用]** をクリックしてから、**[閉じる]** をクリックします。
10. Azure Portal に戻ります。 数分後、**[Intune]** > **[デバイス構成]** > **[証明機関]** の **[接続の状態]** に、緑のチェック マークと **[アクティブ]** という語が表示されます。 これにより、コネクタ サーバーが Intune と通信できることが確認できます。


## <a name="create-a-device-configuration-profile"></a>デバイス構成プロファイルを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[Intune]**、**[デバイス構成]**、**[プロファイル]** と移動して、**[プロファイルの作成]** をクリックします。

   ![NavigateIntune][NavigateIntune]

3. 次の情報を設定します。
   * プロファイルの**名前**
   * オプションで説明を設定
   * プロファイルをデプロイする**プラットフォーム**
   * **[プロファイルの種類]** に**[信頼済み証明書]** を設定
4. **[設定]** に移動して、以前エクスポートした .cer ファイルのルート CA 証明書を指定します。

   > [!NOTE]
   > **手順 3** で選択したプラットフォームに応じて、証明書の**保存先ストア**を選択するオプションが使用できる場合と使用できない場合があります。

   ![ProfileSettings][ProfileSettings]

5. **[OK]** をクリックしてから **[作成]** をクリックし、プロファイルを保存します。
6. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、「[Microsoft Intune のデバイス プロファイルを割り当てる方法](device-profile-assign.md)」をご覧ください。

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 証明書プロファイルを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[Intune]**、**[デバイス構成]**、**[プロファイル]** と移動して、**[プロファイルの作成]** をクリックします。
3. 次の情報を設定します。
   * プロファイルの**名前**
   * オプションで説明を設定
   * プロファイルをデプロイする**プラットフォーム**
   * **[プロファイルの種類]** に **[PKCS 証明書]** を設定
4. **[設定]** に移動して、次の情報を入力します。
   * **更新しきい値 (%)** - 推奨値は 20% です。
   * **証明書の有効期間** - 証明書テンプレートを変更していない場合には、このオプションには 1 年を設定します。
   * **証明機関** - このオプションは、エンタープライズ CA の内部完全修飾ドメイン名 (FQDN) です。
   * **証明機関名** - このオプションは、エンタープライズ CA の名前で、前の項目とは異なる場合があります。
   * **証明書テンプレート名** - このオプションは、先ほど作成したテンプレートの名前です。 既定では、**[テンプレート名]** は **[テンプレート表示名]** (*スペースなし*) と同じであることに注意してください。
   * **サブジェクト名の形式** - 特に指定がない限り、このオプションは**共通名**に設定します。
   * **サブジェクトの別名** - 特に指定がない限り、このオプションは**ユーザー プリンシパル名 (UPN)** に設定します。
   * **拡張キー使用法** - 前のセクション「**証明機関で証明書テンプレートを構成する**」の手順 10 で既定の設定を使用している限り、選択ボックスから次の**定義済みの値**を追加します。
      * **任意の目的**
      * **クライアント認証**
      * **セキュリティで保護された電子メール**
   * **ルート証明書** - (Android プロファイル用) このオプションは、前のセクション「[エンタープライズ CA からルート証明書をエクスポートする](#export-the-root-certificate-from-the-enterprise-ca)」の手順 3 でエクスポートした .cer ファイルです。

5. **[OK]** をクリックしてから **[作成]** をクリックし、プロファイルを保存します。
6. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、「[Microsoft Intune のデバイス プロファイルを割り当てる方法](device-profile-assign.md)」の記事をご覧ください。


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Azure Portal で Intune に移動して信頼された証明書用の新しいプロファイルを作成する"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "プロファイルを作成して信頼された証明書をアップロードする"
[ConnectorDownload]: ./media/certificates-download-connector.png "Azure Portal から Certificate Connector をダウンロードする"  
