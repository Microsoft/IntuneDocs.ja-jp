---
title: "アプリを追加する | Microsoft Docs"
description: "Intune でアプリの展開を開始する前に、このトピックで説明している概念について理解を深めてください。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 0945fb2f67c6cc49ca8d10bb5c24f3c4a5f9b2c5
ms.openlocfilehash: c65dc8ec22f717c5dcce51bb3c45d65bad8d8bde
ms.lasthandoff: 02/28/2017


---

# <a name="add-apps-with-microsoft-intune"></a>Microsoft Intune でアプリを追加する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune でアプリの展開を開始する前に、このトピックで説明している概念について理解を深めてください。 これらの概念は、どのプラットフォームにどのアプリを展開できるかを理解するのに役立ちます。 また、アプリを展開する前に満たす必要がある前提条件を理解するのにも役立ちます。

## <a name="app-types-that-you-can-deploy"></a>展開できるアプリの種類

### <a name="software-installer"></a>ソフトウェアのインストーラー

|アプリの種類|説明|
|----------------|-------|
|**Windows インストーラー (&#42;.exe、&#42;.msi)**|この種類のアプリは、ユーザー入力なしのサイレント インストールをサポートする必要があります。 アプリのマニュアルに、サイレント インストールの実行に関連するコマンドライン オプションが記載されている必要があります (たとえば、**/q**)。 一般的なコマンドライン オプションの一覧は、「[Microsoft Windows インストーラ ツールのコマンド ライン スイッチ](https://support.microsoft.com/en-us/kb/227091)」で見つかります。<br><br>アプリのセットアップ プログラムに必要なその他のファイルとフォルダーは、アプリのセットアップ ファイルに指定した場所から使用できるようにする必要があります。<br><br>多くの場合、Windows インストーラー (.msi) と Windows インストーラー パッチ (.msp) ファイルではコマンドライン引数をインストールするために Intune は必要ありません。 詳細については、アプリのマニュアルを確認してください。<br><br>コマンドライン引数が必要な場合は、"名前=値" の対 (例: TRANSFORMS=custom_transform.mst) の形式で入力します。<br><br>このアプリの種類は、Intune ソフトウェア クライアントを実行しているコンピューターのみに適用されます。|
|**Android 用アプリ パッケージ (&#42;.apk)**|Android アプリを展開するには、有効な .apk パッケージが必要です。|
|**iOS 用アプリ パッケージ (&#42;.ipa)**|iOS アプリを展開するには、有効な .ipa パッケージ ファイルが必要です。<br><br>.ipa パッケージは Apple によって署名され、プロビジョニング プロファイルの有効期限の期限内である必要があります。 Intune では、エンタープライズ証明書付き iOS アプリケーションを配布できます。<br><br>Apple のデベロッパー証明書付きアプリがすべてサポートされているわけではありません。<br><br>お客様の企業で、iOS Developer Enterprise Program に登録する必要があります。<br><br>組織のファイアウォールで、iOS の準備および認証用 Web サイトへのアクセスが許可されていることを確認してください。<br><br>アプリのマニフェスト ファイル (.plist) を展開する必要はありません。|
|**Windows Phone アプリケーション パッケージ (&#42;.xap、.appx、.appxbundle)**|アプリを展開するには、エンタープライズ モバイル コード署名証明書が必要です。 詳細については、「[Microsoft Intune を使用して Windows Phone の管理をセットアップする](set-up-windows-phone-management-with-microsoft-intune.md)」を参照してください。|
|**Windows アプリケーション パッケージ (.appx、.appxbundle)**|アプリを展開するには、エンタープライズ モバイル コード署名証明書が必要です。 詳細については、「[Set up Windows device management with Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)」 (Microsoft Intune を使用して Windows デバイスの管理をセットアップする) を参照してください。|
|**MDM を介した Windows インストーラー (&#42;.msi)**|このアプリを使用して Windows インストーラー ベースのアプリを作成し、Windows 10 を実行する登録済み PC に展開できます。 これらの PC は、モバイル デバイス管理 (MDM) によって管理されます。<br /><br />アップロードできるのは、拡張子が .msi であるファイルを&1; つのみです。<br><br>アプリの検出では、ファイルの製品コードと製品バージョンが使用されます。<br><br>アプリの既定の再起動動作が使用されます。 Intune ではこの機能を制御しません。<br><br>ユーザー単位の MSI パッケージは単一のユーザーにインストールされます。<br><br>コンピューター単位の MSI パッケージはデバイス上のすべてのユーザーにインストールされます。<br><br>デュアル モードの MSI パッケージは現在、デバイス上のすべてのユーザーに対してのみインストールされています。<br><br>アプリの更新プログラムは、各バージョンの MSI 製品コードが同じである場合にサポートされます。<br>
すべてのソフトウェア インストーラー アプリの種類は、クラウド ストレージ領域にアップロードされます。

### <a name="external-link"></a>**外部リンク**
次がある場合は外部リンクを使用します。
- アプリ ストアからユーザーがアプリをダウンロードできる URL。
- Web ブラウザーから実行する Web ベース アプリのリンク。

外部リンク ベースのアプリは、Intune のクラウド記憶域には格納されません。
### <a name="managed-ios-app-from-the-app-store"></a>**App Store の管理対象 iOS アプリ**
管理対象 iOS アプリを使用して App Store から無料で利用できる iOS アプリを管理および展開できます。 また、管理対象 iOS アプリを使用して[モバイル アプリケーションの管理ポリシー](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)を[互換性のあるアプリ](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)に関連付け、その状態を管理コンソールで確認することもできます。<br /><br />管理対象の iOS アプリは、Intune のクラウド記憶域には格納されません。

> [!TIP]
> [MDM 機関の設定](prerequisites-for-enrollment.md)を Intune にすると、モバイル デバイス用のオプションを使用できるようになります。

## <a name="intune-software-publisher"></a>Intune ソフトウェア パブリッシャー
Intune 管理者コンソールからアプリを追加または変更したときに、Microsoft Intune ソフトウェア パブリッシャーが起動します。 パブリッシャーから、次のいずれかを実施するソフトウェア インストーラーの種類を選択して構成します。

- Intune クラウド ストレージに格納するアプリ (コンピューター用のプログラムまたはモバイル デバイス用のアプリ) をアップロードする。
- オンライン ストアまたは Web アプリケーションにリンクする。

ソフトウェア パブリッシャーを使い始める前に、フル バージョンの [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851) をインストールする必要があります。 ソフトウェア パブリッシャーを正常に開くには、インストール後にコンピューターの再起動が必要になることがあります。

## <a name="cloud-storage-space"></a>クラウドの記憶域の容量
ソフトウェア インストーラーのインストールの種類を使用して作成したすべてのアプリ (たとえば、基幹業務アプリ) は、パッケージ化され、Microsoft Intune クラウドの記憶域にアップロードされます。 Intune の試用版サブスクリプションでは、管理対象のアプリと更新プログラムの保管用として、2 ギガバイト (GB) 分のクラウドの記憶域を使用できます。 完全版のサブスクリプションには、20 GB のストレージ領域が含まれています。

**[管理]** ワークスペースの **[記憶域の使用]** ノードで、使用中の記憶域を確認できます。 Intune の追加ストレージは、当初の購入方法を使用して購入できます。  請求書やクレジット カードでお支払いの場合は、[サブスクリプション管理ポータル](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)をご覧ください。  それ以外の場合は、パートナーまたは営業担当者にお問い合わせください。

クラウドの記憶域の容量の要件は次のとおりです。

-   すべてのアプリのインストール ファイルは、同じフォルダーにある必要がある。
-   アップロードするファイルの最大ファイルサイズは 2 GB。


## <a name="support-for-universal-windows-platform-uwp-apps"></a>ユニバーサル Windows プラットフォーム (UWP) アプリのサポート
Windows 10 PC で基幹業務アプリをインストールする場合、サイドローディング キーは不要です。 ただし、レジストリ キー **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** は、サイドローディングを有効にするため、値は **1** である必要があります。

このレジストリ キーが構成されていない場合は、アプリをデバイスに初めて展開する際に、Intune によってこの値が自動的に **1** に設定されます。 この値を **0** に設定した場合、Intune は値を自動的には変更することができず、基幹業務アプリの展開は失敗します。

ユニバーサル Windows プラットフォームの基幹業務アプリは、アプリが展開される各デバイス上で信頼されているコード署名証明書で署名される必要があります。 社内の公開キー基盤 (PKI) からの証明書を使用することも、デバイスにインストールされたサード パーティのパブリック ルート証明書からの証明書を使用することもできます。

Windows 10 Mobile デバイス上では、Symantec 以外のコード署名証明書を使用して、ユニバーサル **.appx** アプリに署名することができます。 **.xap** アプリの場合、また Windows 10 Mobile デバイスにインストールする Windows Phone 8.1 用にビルドされた **.appx** パッケージの場合は、Symantec コード署名証明書を使用する必要があります。

### <a name="dependencies-for-uwp-apps"></a>UWP アプリの依存関係

Intune に Windows 10 ユニバーサル appxbundle パッケージを追加する場合、アプリのあらゆる依存関係がアップロードされていることも確認する必要があります。
これを行うには、アプリの構築時に作成された **[Dependencies]** フォルダーが .appxbundle ファイル自体と同じフォルダーにあるようにします。
これにより、アプリを Intune にアップロードすると、**[Dependencies]** フォルダーにあるすべてのファイルもアップロードされます。 次のスクリーン ショットを使って説明します。


![Windows 10 UWP appxbundle の依存関係を選択する方法](./media/w10-dependencies.png)


## <a name="next-steps"></a>次のステップ

アプリを展開する前に、Intune コンソールでアプリを追加する必要があります。 [登録されたデバイス](add-apps-for-mobile-devices-in-microsoft-intune.md)と [Intune クライアント ソフトウェアで管理する Windows PC](add-apps-for-windows-pcs-in-microsoft-intune.md) にアプリを追加できます。

