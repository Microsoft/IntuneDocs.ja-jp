---
title: Microsoft Intune で PKCS 証明書を使用する - Azure | Micrososft Docs
description: Microsoft Intune で PKCS (Public Key Cryptography Standards/公開鍵暗号標準) 証明書を追加または作成します。これには、ルート証明書をエクスポートする、証明書テンプレートを構成する、Microsoft Intune Certificate Connector (NDES) をダウンロードしてインストールする、デバイス構成プロファイルを作成す。Azure とご利用の証明機関で PKCS 証明書プロファイルを作成するという手順が含まれます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271543"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Intune で PKCS 証明書を構成して使用する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

証明書は、VPN や WiFi ネットワークなど、企業リソースにアクセスするとき、認証やセキュリティ目的で利用されます。 この記事では、PKCS 証明書をエクスポートし、Intune プロファイルに追加する方法について説明します。 

## <a name="requirements"></a>要件

Intune で PKCS 証明書を使用するには、次のインフラストラクチャが必要です。

- **Active Directory ドメイン**: このセクションで示されているすべてのサーバーは、Active Directory ドメインに参加する必要があります。

  ADDS をインストールし、構成する方法については、「[Active Directory の設計と計画について](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)」を参照してください。

- **証明機関** (CA): エンタープライズ証明機関 (CA)

  Active Directory 証明書サービス (AD CS) のインストールや構成の方法については、「[Active Directory 証明書サービス ステップ バイ ステップ ガイド](https://technet.microsoft.com/library/cc772393)」を参照してください。

  > [!WARNING]
  > Intune ではスタンドアロン CA ではなく、エンタープライズ証明機関 (CA) の AD CS を実行する必要があります。

- **クライアント**: エンタープライズ CA に接続するには

- **ルート証明書**: エンタープライズ CA のルート証明書のエクスポートされたコピーです。

- **Microsoft Intune Certificate Connector**: Azure Portal を使用して **証明書コネクタ** インストーラー (**NDESConnectorSetup.exe**) をダウンロードします。 

  NDES 証明書コネクタは、Federal Information Processing Standard (FIPS) モードもサポートしています。 FIPS は必須ではありませんが、有効になっている場合は、証明書の発行および失効を行うことができます。

- **Windows Server**: Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) をホストします。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>エンタープライズ CA からルート証明書をエクスポートする

VPN、WiFi、その他のリソースで認証するには、ルートまたは中間の CA 証明書が各デバイスで必要になります。 次の手順では、エンタープライズ CA から必要な証明書を取得する方法について説明します。

1. 管理特権があるアカウントでエンタープライズ CA にサインインします。
2. コマンド プロンプトを管理者として開きます。
3. 後でアクセスできる場所にルート CA 証明書 (.cer) をエクスポートします。

   次に例を示します。

4. ウィザードが完了した後、ウィザードを閉じる前に、**[証明書コネクタの UI を起動]** をクリックします。

   `certutil -ca.cert certnew.cer`

   詳細については、[証明書を管理するための Certutil タスク](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)に関する記事をご覧ください。

## <a name="configure-certificate-templates-on-the-certification-authority"></a>証明機関で証明書テンプレートを構成する

1. 管理特権があるアカウントでエンタープライズ CA にサインインします。
2. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして **[管理]** を選択します。
3. **[ユーザー証明書テンプレート]** に移動して右クリックし、**[テンプレートの複製]** を選択します。 **[新しいテンプレートのプロパティ]** が開きます。
4. **[互換性]** タブで:

  - **[証明機関]** に **[Windows Server 2008 R2]** を設定します。
  - **[証明書の受信者]** に **[Windows 7 / Server 2008 R2]** を設定します。

5. **[全般]** タブで、**[テンプレート表示名]** にわかりやすい名前を設定します。

   > [!WARNING]
   > 既定では、**[テンプレート名]** は **[テンプレート表示名]** (*スペースなし*) と同じです。 テンプレートの名前をメモします。後で必要になります。

6. **[要求処理]** で、**[プライベート キーのエクスポートを許可する]** を選択します。
7. **[暗号化]** で、**[最小キー サイズ]** が 2048 に設定されていることを確認します。
8. **[サブジェクト名]** で **[要求に含まれる]** を選択します。
9. **[拡張子]** で、**[アプリケーション ポリシー]** に暗号化ファイル システム、セキュリティで保護された電子メール、クライアント認証が表示されていることを確認します。

    > [!IMPORTANT]
    > iOS の証明書テンプレートの場合、**[拡張]** タブで、**[キー使用法]** を更新し、**[署名は発行元の証明である]** が選択されていないことを確認します。

10. **[セキュリティ]** で、Microsoft Intune Certificate Connector をインストールするサーバーのコンピューター アカウントを追加します。 このアカウントに、**読み取り**と**登録**のアクセス許可を割り当てます。
11. **[適用]** をクリックし、**[OK]** をクリックして証明書テンプレートを保存します。
12. **証明書テンプレート コンソール**を閉じます。
13. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして **[新規作成]** をクリックし、**[発行する証明書テンプレート]** をクリックします。 上記の手順で作成したテンプレートを選択して、**[OK]** を選択します。
14. Intune に登録されたデバイスとユーザーに代わって証明書を管理するサーバーの場合、次の手順を実行します。

    1. 証明機関を右クリックして、**[プロパティ]** を選択します。
    2. [セキュリティ] タブで、Microsoft Intune Certificate Connector を実行するサーバーのコンピューター アカウントを追加します。 このコンピューター アカウントに、**証明書の発行と管理**と**証明書の要求**のアクセス許可を付与します。

15. エンタープライズ CA からサインアウトします。

## <a name="download-install-and-configure-the-certificate-connector"></a>証明書コネクタをダウンロードし、インストールして、構成する

![ConnectorDownload][ConnectorDownload]

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** を選択し、**[証明機関]** を選択します。
4. **[追加]** を選択し、**[Download the Connector file]\(コネクタ ファイルをダウンロードします\)** を選択します。 インストールするサーバーからアクセスできる場所にダウンロードしたものを保存します。
5. ダウンロードが完了したら、サーバーにサインインします。 次のことを行います。

    1. .NET Framework 4.5 がインストールされていることを確認します。NDES 証明書コネクタで必要となるからです。 .NET Framework 4.5 は、Windows Server 2012 R2 およびそれ以降の新しいバージョンには自動的に含められます。
    2. インストーラー (NDESConnectorSetup.exe) を実行し、既定の場所を受け入れます。 コネクターは `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe` にインストールされます。 [インストーラー オプション] で **[PFX の配布]** を選択します。 インストールを継続し完了させます。

6. NDES Connector によって **[登録]** タブが開かれます。Intune への接続を有効にするには、**[サインイン]** を選択し、グローバル管理アクセス許可を持つアカウントを入力します。
7. **[詳細設定]** タブで、**[Use this computer's SYSTEM account]\(このコンピューターの SYSTEM アカウントを使用する\)** (既定値) をオンのままにします。
8. **[適用]** を選択し、**[閉じる]** を選択します。
9. Azure ポータルに戻ります (**[Intune]**、**[デバイス構成]**、**[証明機関]**)。 しばらくすると、緑のチェックマークが表示され、**[接続状態]** が **[アクティブ]** になります。 これでコネクタ サーバーは Intune と通信できます。

> [!NOTE]
> NDES 証明書コネクタには、TLS 1.2 のサポートが含まれています。 したがって、NDES 証明書コネクタがインストールされているサーバーが TLS 1.2 をサポートする場合、TLS 1.2 が使用されます。 サーバーが TLS 1.2 をサポートしない場合、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

## <a name="create-a-device-configuration-profile"></a>デバイス構成プロファイルを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。

   ![NavigateIntune][NavigateIntune]

3. 次のプロパティを入力します。

  - プロファイルの**名前**
  - オプションで説明を設定
  - プロファイルをデプロイする**プラットフォーム**
  - **[プロファイルの種類]** に **[信頼済み証明書]** を設定

4. **[設定]** に移動し、以前エクスポートした .cer ファイルのルート CA 証明書を入力します。

   > [!NOTE]
   > **手順 3** で選択したプラットフォームに応じて、証明書の**保存先ストア**を選択するオプションが使用できる場合と使用できない場合があります。

   ![ProfileSettings][ProfileSettings]

5. **[OK]** を選択してから **[作成]** を選択し、プロファイルを保存します。
6. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](device-profile-assign.md)に関するページをご覧ください。

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 証明書プロファイルを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

  - プロファイルの**名前**
  - オプションで説明を設定
  - プロファイルをデプロイする**プラットフォーム**
  - **[プロファイルの種類]** に **[PKCS 証明書]** を設定

4. **[設定]** に移動し、次のプロパティを入力します。

  - **更新しきい値 (%)** - 推奨値は 20% です。
  - **証明書の有効期間** - 証明書テンプレートを変更していない場合、このオプションはおそらく 1 年に設定されています。
  - **証明機関** - エンタープライズ CA の内部完全修飾ドメイン名 (FQDN) が表示されます。
  - **証明機関名** - エンタープライズ CA の名前が一覧表示されます。前の項目とは異なる場合があります。
  - **証明書テンプレート名** - 先に作成したテンプレートの名前。 既定では、**[テンプレート名]** は **[テンプレート表示名]** (*スペースなし*) と同じであることに注意してください。
  - **サブジェクト名の形式** - 特に指定がない限り、このオプションは**共通名**に設定します。
  - **サブジェクトの別名** - 特に指定がない限り、このオプションは**ユーザー プリンシパル名 (UPN)** に設定します。
  - **拡張キー使用法** - (この記事の) セクション「[証明機関で証明書テンプレートを構成する](#configure-certificate-templates-on-the-certification-authority)」の手順 10 で既定の設定を使用している限り、選択範囲から次の**定義済みの値**を追加します。
    - **任意の目的**
    - **クライアント認証**
    - **セキュリティで保護された電子メール**
  - **ルート証明書** - (Android プロファイルの場合) (この記事の) 「[エンタープライズ CA からルート証明書をエクスポートする](#export-the-root-certificate-from-the-enterprise-ca)」セクションの手順 3 でエクスポートした .cer ファイルが一覧表示されます。

5. **[OK]** を選択してから **[作成]** を選択し、プロファイルを保存します。
6. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](device-profile-assign.md)に関するページをご覧ください。

## <a name="next-steps"></a>次の手順
[SCEP 証明書を使用](certificates-scep-configure.md)するか、または [Symantec PKI マネージャー Web サービスから PKCS 証明書を発行](certificates-symantec-configure.md)します。

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Azure Portal で Intune に移動して信頼された証明書用の新しいプロファイルを作成する"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "プロファイルを作成して信頼された証明書をアップロードする"
[ConnectorDownload]: ./media/certificates-download-connector.png "Azure Portal から Certificate Connector をダウンロードする"  
