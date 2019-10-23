---
title: Windows アプリと Windows Phone アプリのサイドロード
titleSuffix: Microsoft Intune
description: Intune を使用して展開できるように、基幹業務アプリに署名する方法について説明します。
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a89392dabe695cf49e989351cef822852676916
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507386"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Intune を使用して Windows デバイスに展開できるように基幹業務アプリに署名する

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Intune 管理者は、ポータル サイト アプリを含め、基幹業務 (LOB) ユニバーサル アプリを Windows 8.1 Desktop デバイスまたは Windows 10 Desktop および Mobile デバイスに展開することができます。 .appx アプリを Windows 8.1 Desktop デバイスまたは Windows 10 Desktop および Mobile デバイスに展開するには、Windows デバイスによって既に信頼されている公開証明機関からのコード署名証明書を使用するか、独自の証明機関を使用することができます。

 > [!NOTE]
 > Windows 8.1 Desktop では、サイドローディングを有効にするエンタープライズ ポリシー、または (ドメイン参加済みデバイスに対して自動的に有効にされる) サイドローディング キーの使用が必要です。 詳しくは、[Windows 8 のサイドローディング](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/)に関するページをご覧ください。

## <a name="windows-10-sideloading"></a>Windows 10 でのサイドローディング

Windows 10 でのサイドローディングは、以前のバージョンの Windows とは異なります。

- エンタープライズ ポリシーを使用して、デバイスのサイドローディングをロック解除できます。 Intune には、"信頼できるアプリのインストール" というデバイス構成ポリシーが用意されています。 appx アプリの署名に使用された証明書を既に信頼しているデバイスで必要なのは、これを <allow> に設定することだけです。

- Symantec Phone 証明書とサイドローディング ライセンス キーは必要ありません。 ただし、オンプレミスの証明機関を使用できない場合は、公開証明機関からコード署名証明書を取得することが必要になる場合があります。 詳しくは、「[コード署名の概要](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing)」をご覧ください。

### <a name="code-sign-your-app"></a>アプリにコード署名する

最初の手順では、appx パッケージにコード署名します。 詳細については、「[SignTool を使ってアプリ パッケージに署名する](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool)」を参照してください。

### <a name="upload-your-app"></a>アプリをアップロードする

次に、署名された appx ファイルをアップロードする必要があります。 詳細については、「[Add a Windows line-of-business app to Microsoft Intune (Windows の基幹業務アプリを Microsoft Intune に追加する)](lob-apps-windows.md)」を参照してください。

必要に応じてユーザーまたはデバイスにアプリを展開する場合は、Inutne ポータル サイト アプリは必要ありません。 ただし、ユーザーが利用できるようにアプリを展開する場合は、パブリック Microsoft Store のポータル サイト アプリを使用するか、ビジネス向けプライベート Microsoft Store のポータル サイト アプリを使用するか、または Intune ポータル サイト アプリに署名して手動で展開する必要があります。

### <a name="upload-the-code-signing-certificate"></a>コード署名証明書をアップロードする

Windows 10 デバイスで証明機関がまだ信頼されていない場合は、appx パッケージに署名して Intune サービスにアップロードした後、コード署名証明書を Intune ポータルにアップロードする必要があります。
1. [クライアント アプリ] をクリックします
2. [Windows Enterprise 証明書] をクリックします
3. コード署名証明書の下の [ファイルの選択] を選択します
4. .cer ファイルを選択して [アップロード] をクリックします

Intune サービスによって appx が展開された Windows 10 Desktop および Mobile デバイスでは、対応するエンタープライズ証明書が自動的にダウンロードされ、インストール後にアプリケーションは起動できるようになります。

Intune では、アップロードされた最新の .cer ファイルのみが展開されます。 組織に関連付けられていない異なる開発者によって作成された複数の appx ファイルがある場合は、自分の証明書で署名するために署名されていない appx ファイルを提供するよう開発者に頼むか、自分の組織で使用されているコード署名証明書を開発者に提供する必要があります。

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Symantec エンタープライズ コード署名証明書を更新する方法

Windows Phone 8.1 モバイル アプリの展開に使用された証明書は、2019 年 2 月 28 日に廃止され、Symantec から更新されなくなりました。 Windows 10 Mobile に展開する場合は、[Windows 10 サイドローディング](app-sideload-windows.md#windows-10-sideloading)の指示に従って、引き続き Symantec Desktop Enterprise コード署名証明書を使用できます。

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>基幹業務 (LOB) アプリの更新された証明書をインストールする方法

Windows Phone 8.1

既存の Symantec Mobile Enterprise コード署名証明書の有効期限が切れた後は、Intune サービスではこのプラットフォームに対して LOB アプリを展開できなくなります。 それでもまだ、SD カードを使用するか、デバイスにファイルをダウンロードすることによって、署名されていない XAP/APPX ファイルをサイドロードすることはできます。 詳しくは、[Windows Phone に XAP ファイルをインストールする方法](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280)に関するページをご覧ください。

Windows 8.1 Desktop/Windows 10 Desktop および Mobile

証明書の期限が切れている場合、appx ファイルの起動が停止する可能性があります。 新しい .cer ファイルを入手し、指示に従って展開された各 appx ファイルにコード署名した後、すべての appx ファイルと更新された .cer ファイルを Intune ポータルの Windows エンタープライズ証明書セクションに再アップロードする必要があります

## <a name="manually-deploy-windows-10-company-portal-app"></a>Windows 10 ポータル サイト アプリの手動展開
Microsoft Store へのアクセスを提供したくない場合は、Intune をビジネス向け Microsoft Store (MSFB) と統合していない場合でも、Intune から直接 Windows 10 ポータル サイト アプリを手動で展開できます。 または、統合している場合は、[MSFB を使用したアプリの展開](store-apps-windows.md)を使用してポータル サイト アプリを展開できます。

 > [!NOTE]
 > このオプションでは、アプリの更新プログラムがリリースされるたびに、手動更新を展開する必要があります。

1. [ビジネス向け Microsoft Store](https://www.microsoft.com/business-store) のアカウントにサインインし、ポータル サイト アプリの**オフライン ライセンス** バージョンを取得します。  
2. アプリが取得されたら、 **[インベントリ]** ページでアプリを選択します。  
3. **プラットフォーム**として **[Windows 10 all devices (Windows 10 のすべてのデバイス)]** を選択し、適切な**アーキテクチャ**を選択してダウンロードします。 このアプリは、アプリ ライセンス ファイルを必要としません。
   ![ダウンロード用 Windows 10 X86 パッケージの詳細の画像](./media/app-sideload-windows/Win10CP-all-devices.png)
4. [必要なフレームワーク] の下のすべてのパッケージをダウンロードします。 x86、x64、および ARM アーキテクチャ用に実行する必要があります。次に示すように、合計 9 個のパッケージのダウンロードが必要になる場合があります。

   ![ダウンロードする依存関係ファイルのイメージ ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. ポータル サイト アプリを Intune にアップロードする前に、パッケージを次のように構成してフォルダー (C:&#92;ポータル サイトなど) を作成します。
   1. C:\ポータル サイトにポータル サイト パッケージを配置します。 また、この場所に依存関係サブフォルダーも作成します。  
      ![APPXBUN ファイルと共に保存された依存関係フォルダーのイメージ](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. 依存関係フォルダーに 9 つの依存関係パッケージを配置します。  
      依存関係がこの形式で配置されていないと、Intune はパッケージのアップロード時にこれらを認識、アップロードすることができます、次のエラーでアップロードが失敗します。  
      ![エラー メッセージ - Windows アプリの依存関係を指定する必要があります。](./media/app-sideload-windows/Win10CP-error-message.png)
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

1. Microsoft Intune Windows 10 ポータル サイト アプリの署名スクリプトを [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) からダウンロードします。  このスクリプトでは、Windows SDK for Windows 10 をホスト コンピューターにインストールする必要があります。 Windows 10 用 Windows SDK をダウンロードするには、[https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296) にアクセスします。
2. 上記の説明のように、ビジネス向け Microsoft ストアから Windows 10 ポータル サイト アプリをダウンロードします。  
3. スクリプト ヘッダーに記載された入力パラメーターを使用してスクリプトを実行し、Windows 10 ポータル サイト アプリに署名します (以下に抜粋)。 スクリプトに依存関係を渡す必要はありません。 依存関係は、アプリが Intune 管理コンソールにアップロードされる場合にのみ必要です。

|       パラメーター       |                                                                    説明                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             ソース appxbundle ファイルが配置されるパス。                                              |
| OutputWin10AppxBundle |                                                  署名された appxbundle ファイルの出力パス                                                  |
|       Win81Appx       |                          Windows 8.1 または Windows Phone 8.1 ポータル サイト (.APPX) ファイルが配置されるパス。                           |
|      PfxFilePath      |                                   Symantec エンタープライズ モバイル コード署名証明書 (.PFX) ファイルへのパス                                    |
|      PfxPassword      |                                     Symantec エンタープライズ モバイル コード署名証明書のパスワード                                      |
|      PublisherId      |      エンタープライズの発行者 ID 指定しない場合、Symantec エンタープライズ モバイル コード署名証明書の 'Subject' フィールドが使用されます。       |
|        SdkPath        | Windows SDK for Windows 10 のルート フォルダーへのパス この引数は省略可能で、既定値は ${env:ProgramFiles(x86)}\Windows Kits\10 です。 |

実行が終了したら、スクリプトにより Windows 10 ポータル サイト アプリの署名されたバージョンが出力されます。 その後、アプリの署名されたバージョンを Intune 経由で LOB アプリとして展開できます。これにより、現在展開されているバージョンがこの新しいアプリにアップグレードされます。  
