---
title: "Intune への Windows アプリと Windows Phone アプリのサイドロード"
description: "Intune を使用して展開できるように、基幹業務アプリに署名する方法について説明します。"
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
ms.custom: intune-classic
ms.openlocfilehash: d6b66c44b1c6b5b5977d7a26d279c32eb39ff7ff
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Intune を使用して Windows デバイスに展開できるように基幹業務アプリに署名する

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune 管理者は、ポータル サイト アプリを含め、基幹業務 (LOB) アプリを Windows および Windows 10 Mobile デバイスに展開することができます。 Windows 10 および Windows 10 Mobile デバイスに .appx または .xap アプリを展開する場合や、Windows 8.1 または Windows Phone 8.1 デバイスに LOB アプリを展開する場合は、**Symantec エンタープライズ モバイル コード署名証明書**を取得する必要があります。 これらの各 Windows デバイスのアプリで信頼されているのは Symantec 証明書のみです。 Windows 10 アプリと "ユニバーサル" アプリの場合は独自の証明機関を使用できます。 この証明書は、以下の操作を行うために必要です。

-   Windows PC、Windows 10 Mobile デバイス、Windows Phone デバイスに展開するためにポータル サイト アプリに署名する

-   Intune で Windows デバイスに展開できるように、会社の基幹業務アプリに署名する

次の手順は、必要な証明書を取得し、アプリに署名する場合に役立ちます。 Microsoft 開発者として登録し、Symantec 証明書を購入する必要があります。


1. **Microsoft 開発者として登録する**<br>
   ログイン時に使用した会社のアカウント情報を使用して、[Microsoft 開発者として登録](http://go.microsoft.com/fwlink/?LinkId=268442)し、自身の会社のアカウントを購入します。 コード署名証明書を受け取る前に、会社の担当者からこの要求の承認を受ける必要があります。

2. **会社の Symantec 証明書を取得する**<br>
  [Symantec の Web サイト](http://go.microsoft.com/fwlink/?LinkId=268441)から Symantec ID を使用して証明書を購入します。 証明書を購入すると、Microsoft 開発者として登録したときに指定した会社の承認者は、証明書要求の承認を求めるメールを受信します。 Symantec 証明書の要件の詳細については、「[Why Windows Phone requires a Symantec certificate? (Windows Phone で Symantec 証明書が必要な理由)](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec)」 (Windows デバイスの登録に関する FAQ) をご覧ください。

3.  **証明書をインポートする**<br>
    要求が承認されると、証明書をインポートするための手順を含む電子メールが届きます。 メールの指示に従って証明書をインポートします。

4.  **インポートされた証明書を確認する**<br>
    証明書が正しくインポートされたことを確認するには、**[証明書]** スナップインに進み、**[証明書]** を右クリックして **[証明書の検索]** を選択します。 **[含む]** フィールドに「Symantec」と入力し、 **[今すぐ検索]**をクリックします。 インポートした証明書が検索結果に表示されます。

    ![Symantec 証明書の検索](./media/wit.gif)

5. **署名証明書をエクスポートする**<br>
    証明書があることを確認したら、.pfx ファイルをエクスポートしてポータル サイトに署名できます。 **[使用目的]** が "コード署名" になっている Symantec 証明書を選択します。 そのコード署名証明書を右クリックして、**[エクスポート]** を選択します。

    ![署名証明書のエクスポート](./media/wit-walk-cert2.gif)

    **[証明書のエクスポート ウィザード]**が起動したら、 **[はい、秘密キーをエクスポートします]** を選択して **[次へ]**をクリックします。 **[Personal Information Exchange - PKCS #12 (.PFX)]** を選択し、**[証明のパスにある証明書を可能であればすべて含む]** チェック ボックスをオンにします。 ウィザードを完了します。 詳細については、「 [証明書を秘密キーと共にエクスポートする](http://go.microsoft.com/fwlink/?LinkID=203031)」をご覧ください。

6.  **Intune にアプリをアップロードする**<br>
    署名付きのアプリ ファイルと、コード署名証明書をアップロードして、アプリをエンド ユーザーが使用できるようにします。

    1.  Azure Portal で **[管理]** &gt; **[Windows Phone]** の順にクリックします。

    2.  **[署名済みアプリ ファイルのアップロード]** をクリックし、Intune 管理者 ID でサインインします。

    3.  エクスポートした証明書 (.pfx) ファイルを **[コード署名証明書]** に追加し、証明書のパスワードを作成します。

    4.  ウィザードを完了します。

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>例: Windows デバイス用ポータル サイト アプリのダウンロード、署名、および展開

Microsoft ストアからインストールしなくても、Intune を使用して、Windows Phone や Windows 10 Mobile デバイスなどの Windows デバイスにポータル サイト アプリを展開できます。 ポータル サイト アプリをダウンロードし、証明書を使用して署名する必要があります。  この手順は、ユーザーが会社のストアを使用しないが、ポータル サイトを Windows Phone 8.1 デバイスに展開する場合のみ必要です。


1.  **ポータル サイトをダウンロードする**

    Intune を使用してポータル サイト アプリを展開する場合は、ダウンロード センターから [Windows Phone 8.1 用 Microsoft Intune ポータル サイト アプリ](http://go.microsoft.com/fwlink/?LinkId=615799)をダウンロードし、自己解凍形式 (.exe) のファイルを実行します。 このファイルには、以下の 2 つのファイルが含まれています。

    -   CompanyPortal.appx – ポータル サイトの Windows Phone 8.1 用インストール アプリ

    -   WinPhoneCompanyPortal.ps1 – ポータル サイト アプリ ファイルへの署名に使用する PowerShell スクリプト。これにより、ポータル サイト アプリを Windows Phone 8.1 デバイスに展開できます。

    また、[ビジネス向け Microsoft ストア](http://businessstore.microsoft.com/)から Windows Phone 8.1 ポータル サイト (オフライン ライセンス パッケージ) または Windows 10 ポータル サイト (オフライン ライセンス パッケージ) をダウンロードすることもできます。 ポータル サイト アプリは、オフライン ライセンスと、オフラインで使用するためにダウンロードした適切なパッケージを使用して取得する必要があります。 選択項目の Windows 8 および Windows Phone 8 プラットフォーム リストでは、対応する 8.1 が参照されます。 Intune でそれを行う方法については、「[ビジネス向け Microsoft ストアから購入したアプリを管理する](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)」を参照してください。

2.  **Windows Phone SDK をダウンロードする** Windows Phone SDK 8.0 (http://go.microsoft.com/fwlink/?LinkId=615570) をダウンロードし、SDK をコンピューターにインストールします。 この SDK は、アプリケーション登録トークンを生成するために必要です。

3.  **AETX ファイルを生成する** Windows Phone SDK 8.0 に含まれる AETGenerator.exe を使用して、Symantec PFX ファイルからアプリケーション登録トークン (.aetx) ファイルを生成します。 AETX ファイルの作成手順については、「 [Windows Phone 用のアプリケーション登録トークンを生成する方法](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx)」をご覧ください。

4.  **Windows SDK for Windows 8.1 をダウンロードする** [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525) をダウンロードしてインストールします。 ポータル サイト アプリに付属の PowerShell スクリプトでは、既定のインストール場所 `${env:ProgramFiles(x86)}\Windows Kits\8.1`が使用される点に注意してください。 他の場所にインストールする場合は、コマンドレット パラメーターにその場所を含める必要があります。

5.  **PowerShell を使用してアプリにコード署名をする** Windows SDK と Symantec エンタープライズ モバイル コード署名証明書がインストールされたホスト コンピューターで、管理者として **Windows PowerShell** を開き、Sign-WinPhoneCompanyPortal.ps1 ファイルに移動してスクリプトを実行します。

    **例 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    この例では、C:\temp\ にある CompanyPortal.appx に署名し、CompanyPortalEnterpriseSigned.appx を生成します。 PFX パスワード 1234 を使用して、PFX ファイルから発行者 ID を読み取ります。 同様に、cert.aetx ファイルからはエンタープライズ ID を読み取ります。

    **例 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    この例では、C:\temp\ にある CompanyPortal.appx に署名し、CompanyPortalEnterpriseSigned.appx を生成します。 PFX パスワード 1234 を使用して、指定された発行者 ID を使用します。

    **パラメーター:**

    -   `-InputAppx` – 単一引用符で囲まれた、CompanyPortal.appx ファイルへのローカル パス。 たとえば、'C:\temp\CompanyPortal.appx'。

    -   `-OutputAppx` – 単一引用符で囲まれた、署名済みポータル サイト アプリのローカル パスとファイル名。 たとえば、'C:\temp\CompanyPortalEnterpriseSigned.appx'。

    -   `-PfxFilePath` – Symantec 証明書のエクスポート済み PFX ファイルのローカル パスとファイル名。 たとえば、'C:\signing\cert.pfx'。

    -   `-PfxPassword` – 単一引用符で囲まれた、PFX ファイルの署名に使用されるパスワード。 たとえば、'1234'。

    -   `-AetxPath` – 'EnterpriseId' 引数が定義されていない場合にエンタープライズ ID の読み取りに使用される、.aetx ファイルへのローカル パス。 この引数と EnterpriseId のいずれかを指定する必要があります。 たとえば、'C:\signing\cert.aetx'。

    -   `-PublisherId` - エンタープライズの発行者 ID。 指定しない場合、Symantec エンタープライズ モバイル コード署名証明書の 'Subject' フィールドが使用されます。 たとえば、'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'。

    -   `-SdkPath` - Windows 8.1 用 Windows SDK のルート フォルダーへのパス。 この引数は省略可能で、既定値は ${env:ProgramFiles(x86)}\Windows Kits\8.1 です。

    -   `-EnterpriseId` - エンタープライズ ID。 この引数と 'AetxPath' のいずれかを指定する必要があります。 この引数が指定されていない場合、AETX ファイルからエンタープライズ ID が読み取られます。 たとえば、1000000001。

6.  Windows Phone 8.1 ポータル サイト (SSP.appx) アプリを展開する ガイダンスについては、[Windows Phone の基幹業務 (LOB) アプリを追加する方法](lob-apps-windows-phone.md) ([クラシック ポータル](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)) に関する内容をご覧ください。

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Symantec エンタープライズ コード署名証明書を更新する方法

Windows および Windows Phone モバイル アプリを展開するのに使用する Symantec 証明書は、定期的に更新する必要があります。

1.  証明書の有効期限の約 14 日前に Symantec から送信される更新に関する電子メールを探します。 この電子メールには、エンタープライズ証明書の更新に関する Symantec から指示が記載されています。

    Symantec 証明書の詳細については、[www.symantec.com](http://www.symantec.com) にアクセスするか、1-877-438-8776 または 1-650-426-3400 に電話をかけてください。

2.  Web サイト (例: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) に移動し、証明書に関連付けられている Symantec 発行者 ID と電子メール アドレスを使用してログインします。 更新を開始するコンピューターは、証明書のダウンロードに使用するのと同じコンピューターである必要があります。

3.  更新が承認され支払いが済んだら、証明書をダウンロードします。

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>基幹業務 (LOB) アプリの更新された証明書をインストールする方法

1.  最新バージョンの基幹業務アプリに署名します。

2.  Azure Portal を開き、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows Phone]** の順に選択し、**[Upload Signed App]\(署名済みアプリのアップロード\)** をクリックします。

3.  新しく署名したポータル サイトをアップロードします。 新しく署名した SSP.xap と、Symantec から送信された新しい .PFX ファイルまたはこの新しい .PFX ファイルを使用して作成されたアプリケーション登録トークンが必要になります。

4.  アップロードが完了したら、 **[ソフトウェア]**  ワークスペースで古いバージョンのポータル サイトを削除します。

5.  新しい証明書を使用して、新しいエンタープライズ基幹業務アプリと更新されたエンタープライズ基幹業務アプリのすべてに署名します。 既存のアプリケーションを再署名して再展開する必要はありません。

## <a name="manually-deploy-windows-10-company-portal-app"></a>Windows 10 ポータル サイト アプリの手動展開
Intune をビジネス向け Microsoft ストアと統合していない場合でも、Intune から直接 Windows 10 ポータル サイト アプリを手動で展開できます。

 > [!NOTE]
 > このオプションでは、アプリの更新プログラムがリリースされるたびに、手動更新を展開する必要があります。

1. [ビジネス向け Microsoft ストア](https://www.microsoft.com/business-store)のアカウントにログインし、ポータル サイト アプリの**オフライン ライセンス** バージョンを取得します。  
2. アプリが取得されたら、**[インベントリ]** ページでアプリを選択します。  
3. **プラットフォーム**として **[Windows 10 all devices (Windows 10 のすべてのデバイス)]** を選択し、適切な**アーキテクチャ**を選択してダウンロードします。 このアプリは、アプリ ライセンス ファイルを必要としません。
![ダウンロードする Windows 10 のすべてのデバイスと Architecture X86 Package のイメージ](./media/Win10CP-all-devices.png)
4. [必要なフレームワーク] の下のすべてのパッケージをダウンロードします。 x86、x64、および ARM アーキテクチャ用に実行する必要があります。次に示すように、合計 9 個のパッケージのダウンロードが必要になる場合があります。

![ダウンロードする依存関係ファイルのイメージ ](./media/Win10CP-dependent-files.png)
5. ポータル サイト アプリを Intune にアップロードする前に、パッケージを次のように構成してフォルダー (C:&#92;ポータル サイトなど) を作成します。
  1. C:\ポータル サイトにポータル サイト パッケージを配置します。 また、この場所に依存関係サブフォルダーも作成します。  
  ![APPXBUN ファイルと共に保存された依存関係フォルダーのイメージ](./media/Win10CP-Dependencies-save.png)
  2. 依存関係フォルダーに 9 つの依存関係パッケージを配置します。  
  依存関係がこの形式で配置されていないと、Intune はパッケージのアップロード時にこれらを認識、アップロードすることができます、次のエラーでアップロードが失敗します。  
  ![このソフトウェア インストーラーに関する Windows アプリの依存関係がアプリケーション フォルダー内で見つかりませんでした。 このアプリケーションの作成と展開を続行できますが、不明な Windows アプリの依存関係が提供されるまでは実行されません。](./media/Win10CP-error-message.png)
6. Intune に戻り、ポータル サイト アプリを新しいアプリとしてアップロードします。 これを必要なアプリとして対象の一連のターゲット ユーザーに展開します。  

Intune がユニバーサル アプリ用に依存関係をどのように処理するかについて詳しくは、「[Deploying an appxbundle with dependencies via Microsoft Intune MDM (Microsoft Intune MDM 経由で依存関係を使用して appxbundle を展開する)](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)」ご覧ください。  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>ユーザーがストアから古いアプリを既にインストールしている場合に、ユーザーのデバイスのポータル サイトを更新する方法
貴社のユーザーがストアから Windows 8.1 または Windows Phone 8.1 ポータル サイト アプリを既にインストールしている場合は、お客様またはお客様のユーザーが特に操作を行わなくても新しいバージョンに自動的に更新されます。 更新が実行されない場合は、デバイスでストア アプリの自動更新を有効にしているかどうかをユーザーに確認してください。   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>サイドロードした Windows 8.1 のポータル サイト アプリを Windows 10 のポータル サイト アプリにアップグレードする方法
推奨される移行パスとして、展開アクションを "アンインストール" に設定して、Windows 8.1 ポータル サイト アプリの展開を削除します。 これが完了したら、上記のいずれかのオプションを使用して、Windows 10 ポータル サイト アプリを展開できるようになります。  

アプリをサイドロードする必要があり、Symantec 証明書で署名せずに Windows 8.1 ポータル サイトを展開した場合は、上の Intune セクションから直接、展開に関する手順に従ってアップグレードを完了します。

アプリをサイドロードする必要があり、Symantec コード署名証明書で Windows 8.1 ポータル サイトに署名し展開した場合は、以下のセクションの手順に従ってください。  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>署名およびサイドロードした Windows Phone 8.1 ポータル サイト アプリまたは Windows 8.1 ポータル サイト アプリを Windows 10 ポータル サイト アプリにアップグレードする方法
推奨される移行パスとして、展開アクションを "アンインストール" に設定して、Windows Phone 8.1 ポータル サイト アプリまたは Windows 8.1 ポータル サイト アプリの既存の展開を削除します。 これが完了したら、通常どおり Windows 10 ポータル サイト アプリを展開できるようになります。  

これ以外の場合は、アップグレードのパスが確実に考慮されるように Windows 10 ポータル サイト アプリを適切に更新し、署名する必要があります。  

この方法で Windows 10 ポータル サイト アプリに署名し展開した場合、ストアで入手可能になった新しいアプリの更新プログラムごとにこのプロセスを繰り返す必要があります。 ストアが更新されたときに、アプリは自動的に更新されません。  

この場合のアプリへの署名および展開方法は、次のとおりです。

1. Microsoft Intune Windows 10 ポータル サイト アプリの署名スクリプトを [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) からダウンロードします。  このスクリプトでは、Windows SDK for Windows 10 をホスト コンピューターにインストールする必要があります。 Windows SDK for Windows 10 をダウンロードするには、[https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296) にアクセスします。
2. 上記の説明のように、ビジネス向け Microsoft ストアから Windows 10 ポータル サイト アプリをダウンロードします。  
3. スクリプト ヘッダーに記載された入力パラメーターを使用してスクリプトを実行し、Windows 10 ポータル サイト アプリに署名します (以下に抜粋)。 スクリプトに依存関係を渡す必要はありません。 依存関係は、アプリが Intune 管理コンソールにアップロードされる場合にのみ必要です。

|パラメーター | 説明|
| ------------- | ------------- |
|InputWin10AppxBundle |ソース appxbundle ファイルが配置されるパス。 |
|OutputWin10AppxBundle |署名された appxbundle ファイルの出力パス |
|Win81Appx | Windows 8.1 または Windows Phone 8.1 ポータル サイト (.APPX) ファイルが配置されるパス。|
|PfxFilePath |Symantec エンタープライズ モバイル コード署名証明書 (.PFX) ファイルへのパス |
|PfxPassword| Symantec エンタープライズ モバイル コード署名証明書のパスワード |
|PublisherId |エンタープライズの発行者 ID 指定しない場合、Symantec エンタープライズ モバイル コード署名証明書の 'Subject' フィールドが使用されます。|
|SdkPath | Windows SDK for Windows 10 のルート フォルダーへのパス この引数は省略可能で、既定値は ${env:ProgramFiles(x86)}\Windows Kits\10 です。|
実行が終了したら、スクリプトにより Windows 10 ポータル サイト アプリの署名されたバージョンが出力されます。 その後、アプリの署名されたバージョンを Intune 経由で LOB アプリとして展開できます。これにより、現在展開されているバージョンがこの新しいアプリにアップグレードされます。  
