---
title: Microsoft Intune で秘密キーと公開キーの証明書を使用する - Azure | Microsoft Docs
description: Microsoft Intune で Public Key Cryptography Standards (PKCS) 証明書を追加または作成します。これには、ルート証明書をエクスポートする、証明書テンプレートを構成する、Microsoft Intune Certificate Connector (NDES) をダウンロードしてインストールする、デバイス構成プロファイルを作成す。Azure とご利用の証明機関で PKCS 証明書プロファイルを作成するという手順が含まれます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87a7f7f77914b899b7173b8bfacb82cd0c50c6e7
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230042"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Intune で PKCS 証明書を構成して使用する

証明書は、VPN や WiFi ネットワークなど、企業リソースへのアクセスを認証し、セキュリティで保護します。 PKCS 証明書とも呼ばれる秘密キーと公開キーのペアを使用する証明書は、多くの組織で使用されています。 Microsoft Intune には、組織のリソースへのアクセスと認証に PKCS 証明書を使用するための組み込みの設定が含まれています。 このような設定は、Intune でデバイス構成プロファイルを使用してデバイスにプッシュ (または展開) されます。

この記事では、PKCS 証明書を使用するための要件の一覧を示し、PKCS 証明書をエクスポートする方法について説明し、証明書を Intune デバイス構成プロファイルに追加する方法について説明します。

## <a name="requirements"></a>要件

Intune で PKCS 証明書を使用するには、次のインフラストラクチャが必要です。

- **Active Directory ドメイン**: このセクションで示されているすべてのサーバーは、Active Directory ドメインに参加する必要があります。

  ADDS をインストールし、構成する方法については、「[Active Directory の設計と計画について](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)」を参照してください。

- **証明機関** (CA): エンタープライズ証明機関 (CA)

  Active Directory 証明書サービス (AD CS) のインストールや構成の方法については、「[Active Directory 証明書サービス ステップ バイ ステップ ガイド](https://technet.microsoft.com/library/cc772393)」を参照してください。

  > [!WARNING]
  > Intune ではスタンドアロン CA ではなく、エンタープライズ証明機関 (CA) の AD CS を実行する必要があります。

- **クライアント**:エンタープライズ CA に接続するには

- **ルート証明書**:エンタープライズ CA のルート証明書のエクスポートされたコピー

- **Microsoft Intune Certificate Connector**: Azure portal を使用して **Certificate Connector** インストーラー (**NDESConnectorSetup.exe**) をダウンロードします。 

  コネクタは、認証または S/MIME メールの署名で使用される PKCS 証明書の要求を処理します。

  NDES 証明書コネクタは、Federal Information Processing Standard (FIPS) モードもサポートしています。 FIPS は必須ではありませんが、有効になっている場合は、証明書の発行および失効を行うことができます。

- **PFX Certificate Connector for Microsoft Intune**:S/MIME メールの暗号化を使用する予定である場合は、Azure portal を使用して **PFX Certificate Connector for Microsoft Intune** インストーラー (**PfxCertificateConnectorBootstrapper.exe**) をダウンロードします。 コネクタでは、特定のユーザーを対象にした S/MIME メールの暗号化で Intune にインポートされる PFX ファイルに対する要求を処理します。

- **Windows Server**:以下をホストします。

  - 認証および S/MIME メールの署名のシナリオ用の Microsoft Intune Certificate Connector (NDESConnectorSetup.exe)。
  - S/MIME メールの暗号化シナリオ用の PFX Certificate Connector for Microsoft Intune (PfxCertificateConnectorBootstrapper.exe)。

  同じサーバー上で両方のコネクタ (**Microsoft Intune Certificate Connector** および **PFX Certificate Connector for Microsoft Intune**) を実行することができます。

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>エンタープライズ CA からルート証明書をエクスポートする

VPN、WiFi、その他のリソースを使用して認証するには、ルートまたは中間の CA 証明書が各デバイスで必要になります。 次の手順では、エンタープライズ CA から必要な証明書を取得する方法について説明します。

1. 管理特権があるアカウントでエンタープライズ CA にサインインします。
2. コマンド プロンプトを管理者として開きます。
3. 後でアクセスできる場所にルート CA 証明書 (.cer) をエクスポートします。
4. ウィザードが完了した後、ウィザードを閉じる前に、**[証明書コネクタの UI を起動]** をクリックします。

   `certutil -ca.cert certnew.cer`

   詳細については、[証明書を管理するための Certutil タスク](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)に関する記事をご覧ください。

## <a name="configure-certificate-templates-on-the-ca"></a>CA 上で証明書テンプレートを構成する

1. 管理特権があるアカウントでエンタープライズ CA にサインインします。
2. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして **[管理]** を選択します。
3. **User** 証明書テンプレートを探して右クリックし、**[テンプレートの複製]** を選択します。 **[新しいテンプレートのプロパティ]** が開きます。

    > [!NOTE]
    > S/MIME メールの署名と暗号化のシナリオの場合、管理者の多くは、署名と暗号化に対して別々の証明書を使用します。 Microsoft Active Directory Certificate Services を使用している場合、S/MIME メールの署名証明書には **[Exchange 署名のみ]** テンプレートを使用し、S/MIME 暗号化証明書には **[Exchange ユーザー]** テンプレートを使用することができます。  サード パーティ証明機関を使用している場合は、該当するガイダンスを確認して署名および暗号化のテンプレートを設定することをお勧めします。

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
11. **[適用]** > **[OK]** をクリックして証明書テンプレートを保存します。 **証明書テンプレート コンソール**を閉じます。
12. **[証明機関]** コンソールで **[証明書テンプレート]** を右クリックして、**[新規作成]** > **[発行する証明書テンプレート]** をクリックします。 上記の手順で作成したテンプレートを選択します。 **[OK]** を選択します。
13. 登録されたデバイスとユーザーの証明書をサーバーで管理する場合は、次の手順を使用します。

    1. 証明機関を右クリックして、**[プロパティ]** を選択します。
    2. [セキュリティ] タブで、コネクタ (**Microsoft Intune Certificate Connector** または **PFX Certificate Connector for Microsoft Intune**) を実行するサーバーのコンピューター アカウントを追加します。 
    3. このコンピューター アカウントに、**証明書の発行と管理**と**証明書の要求**のアクセス許可を付与します。

14. エンタープライズ CA からサインアウトします。

## <a name="download-install-and-configure-the-certificate-connectors"></a>証明書コネクタをダウンロードし、インストールして、構成する

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune 証明書コネクタ

> [!IMPORTANT] 
> Microsoft Intune 証明書コネクタは、別の Windows サーバーにインストールする**必要があります**。 発行元の証明機関 (CA) にインストールすることはできません。

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]** > **[証明機関]** > **[追加]** の順に選択します。
3. コネクタ ファイルをダウンロードして保存します。 コネクタをインストールするサーバーからアクセスできる場所に保存します。

    ![ConnectorDownload][ConnectorDownload]

4. ダウンロードが完了したら、サーバーにサインインします。 次のことを行います。

    1. .NET Framework 4.5 以降がインストールされていることを確認します。NDES 証明書コネクタで必要となるからです。 .NET Framework 4.5 は、Windows Server 2012 R2 およびそれ以降の新しいバージョンには自動的に含められます。
    2. インストーラー (NDESConnectorSetup.exe) を実行し、既定の場所を受け入れます。 コネクターは `\Program Files\Microsoft Intune\NDESConnectorUI` にインストールされます。 [インストーラー オプション] で **[PFX の配布]** を選択します。 インストールを継続し完了させます。
    3. 既定では、コネクタ サービスはローカル システム アカウントの下で実行されます。 インターネットにアクセスするのにプロキシが必要な場合は、ローカル サービス アカウントがサーバー上のプロキシ設定にアクセスできることを確認します。

5. NDES Connector によって **[登録]** タブが開かれます。Intune への接続を有効にするには、**[サインイン]** を選択し、グローバル管理アクセス許可を持つアカウントを入力します。
6. **[詳細設定]** タブでは、**[このコンピューターの SYSTEM アカウントを使用する (既定)]** をオンのままにすることをお勧めします。
7. **[適用]** > **[閉じる]** を選択します
8. Azure ポータルに戻ります (**[Intune]**、**[デバイス構成]**、**[証明機関]**)。 しばらくすると、緑のチェックマークが表示され、**[接続の状態]** が **[アクティブ]** になります。 これでコネクタ サーバーは Intune と通信できます。
9. ご利用のネットワーク環境に Web プロキシがある場合、コネクタが動作するように追加の構成が必要になる可能性があります。 詳細については、Azure Active Directory ドキュメントの「[既存のオンプレミス プロキシ サーバーと連携する](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)」を参照してください。

> [!NOTE]
> Microsoft Intune Certificate Connector には、TLS 1.2 のサポートが含まれています。 したがって、Microsoft Intune Certificate Connector がインストールされているサーバーが TLS 1.2 をサポートする場合、TLS 1.2 が使用されます。 サーバーが TLS 1.2 をサポートしない場合、TLS 1.1 が使用されます。 現在、デバイスとサーバー間の認証には、TLS 1.1 が使用されています。

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>PFX Certificate Connector for Microsoft Intune

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]** > **[証明機関]** > **[追加]** の順に選択します
3. PFX Certificate Connector for Microsoft Intune をダウンロードして保存します。 コネクタをインストールするサーバーからアクセスできる場所に保存します。
4. ダウンロードが完了したら、サーバーにサインインします。 次のことを行います。

    1. .NET Framework 4.6 以降がインストールされていることを確認します。PFX Certificate Connector for Microsoft Intune で必要となるからです。 .NET 4.6 Framework がインストールされていない場合は、インストーラーによって自動的にインストールされます。
    2. インストーラー (PfxCertificateConnectorBootstrapper.exe) を実行し、既定の場所をそのまま使用します。 コネクターは `Program Files\Microsoft Intune\PFXCertificateConnector` にインストールされます。
    3. コネクタ サービスはローカル システム アカウントの下で実行されます。 インターネットにアクセスするのにプロキシが必要な場合は、ローカル サービス アカウントがサーバー上のプロキシ設定にアクセスできることを確認します。

5. インストール後、PFX Certificate Connector for Microsoft Intune によって **[登録]** タブが開かれます。 Intune への接続を有効にするには、**[サインイン]** を選択し、Azure 全体管理者のアクセス許可または Intune 管理者のアクセス許可を持つアカウントを入力します。
6. ウィンドウを閉じます。
7. Azure ポータルに戻ります (**[Intune]**、**[デバイス構成]**、**[証明機関]**)。 しばらくすると、緑のチェックマークが表示され、**[接続の状態]** が **[アクティブ]** になります。 これでコネクタ サーバーは Intune と通信できます。

## <a name="create-a-trusted-certificate-profile"></a>信頼済み証明書プロファイルを作成する

1. [Azure portal](https://portal.azure.com) で、**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。

   ![NavigateIntune][NavigateIntune]

2. 次のプロパティを入力します。

    - プロファイルの**名前**
    - オプションで説明を設定
    - プロファイルをデプロイする**プラットフォーム**
    - **[プロファイルの種類]** に **[信頼済み証明書]** を設定

3. **[設定]** に移動し、以前エクスポートした .cer ファイルのルート CA 証明書を入力します。

   > [!NOTE]
   > **手順 3** で選択したプラットフォームに応じて、証明書の**保存先ストア**を選択するオプションが使用できる場合と使用できない場合があります。

   ![ProfileSettings][ProfileSettings]

4. **[OK]** > **[作成]** を選択してプロファイルを保存します。
5. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](device-profile-assign.md)に関するページをご覧ください。

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 証明書プロファイルを作成する

1. [Azure portal](https://portal.azure.com) で、**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
2. 次のプロパティを入力します。

    - プロファイルの**名前**
    - オプションで説明を設定
    - プロファイルをデプロイする**プラットフォーム**
    - **[プロファイルの種類]** に **[PKCS 証明書]** を設定

3. **[設定]** に移動し、次のプロパティを入力します。

    - **[更新しきい値 (%)]**: 推奨値は 20% です。
    - **[証明書の有効期間]**: 証明書テンプレートを変更していない場合、このオプションはおそらく 1 年に設定されています。
    - **キー記憶域プロバイダー (KSP)**:Windows では、デバイス上のキーを格納する場所を選択します。
    - **証明機関**:エンタープライズ CA の内部完全修飾ドメイン名 (FQDN) が表示されます。
    - **証明機関名**:"Contoso Certification Authority" など、エンタープライズ CA の名前が一覧表示されます。
    - **証明書テンプレート名**: 先に作成したテンプレートの名前。 既定では、**[テンプレート名]** は **[テンプレート表示名]** (*スペースなし*) と同じであることに注意してください。
    - **[サブジェクト名の形式]**: 特に指定がない限り、このオプションは**共通名**に設定します。
    - **[サブジェクトの別名]**: 特に指定がない限り、このオプションは**ユーザー プリンシパル名 (UPN)** に設定します。

4. **[OK]** > **[作成]** を選択してプロファイルを保存します。
5. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](device-profile-assign.md)に関するページをご覧ください。

## <a name="create-a-pkcs-imported-certificate-profile"></a>PKCS のインポートされた証明書プロファイルを作成する

任意の CA から特定のユーザーに向けて以前に発行された証明書を Intune にインポートすることができます。 インポートした証明書は、ユーザーが登録している各デバイスにインストールされます。 S/MIME メールの暗号化は、既存の PFX 証明書を Intune にインポートするための最も一般的なシナリオです。 ユーザーは、メールを暗号化するための証明書を多数持っている場合があります。 それらの証明書の秘密キーはユーザーのデバイスのすべてに存在している必要があるので、以前に暗号化されたメールを暗号化解除することができます。

証明書を Intune にインポートするには、[GitHub で提供されている PowerShell コマンドレット](https://github.com/Microsoft/Intune-Resource-Access)を使用できます。

証明書を Intune にインポートしたら、**[PKCS のインポートされた証明書]** プロファイルを作成し、それを Azure Active Directory グループに割り当てます。

1. [Azure portal](https://portal.azure.com) で、**[Intune]** > **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
2. 次のプロパティを入力します。

    - プロファイルの**名前**
    - オプションで説明を設定
    - プロファイルをデプロイする**プラットフォーム**
    - **[プロファイルの種類]** に **[PKCS のインポートされた証明書]** を設定

3. **[設定]** に移動し、次のプロパティを入力します。

    - **使用目的**:このプロファイルに対してインポートされた証明書の目的です。 管理者は、証明書をさまざまな目的でインポートしてある場合があります (認証、S/MIME 署名、S/MIME 暗号化など)。 証明書プロファイル内で選択された使用目的によって、証明書プロファイルは適切なインポートされた証明書と対応させられます。
    - **[証明書の有効期間]**: 証明書テンプレートを変更していない場合、このオプションはおそらく 1 年に設定されています。
    - **キー記憶域プロバイダー (KSP)**:Windows では、デバイス上のキーを格納する場所を選択します。

4. **[OK]** > **[作成]** を選択してプロファイルを保存します。
5. 1 つ以上のデバイスに新しいプロファイルを割り当てる場合は、[Microsoft Intune のデバイス プロファイルの割り当て](device-profile-assign.md)に関するページをご覧ください。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[SCEP 証明書を使用](certificates-scep-configure.md)するか、[Symantec PKI マネージャー Web サービスから PKCS 証明書を発行](certificates-symantec-configure.md)します。

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Azure Portal で Intune に移動して信頼された証明書用の新しいプロファイルを作成する"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "プロファイルを作成して信頼された証明書をアップロードする"
[ConnectorDownload]: ./media/certificates-download-connector.png "Azure Portal から Certificate Connector をダウンロードする"  
