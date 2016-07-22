---
title: "新機能の公開履歴 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 051d06afb0f29f2a97c1f06dc1102138e5f2be8f


---


## 2015 年 9 月
### モバイル デバイスおよびアプリ管理の更新
**すべての Intune の iOS 管理機能が iOS 9 に対応** iOS 9 の管理機能に関する詳細については、[このブログ投稿](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx)を参照してください。

**新しくなった iOS のモバイル アプリの構成ポリシー** 新しいモバイル アプリの構成ポリシーを使用すると、iOS アプリの実行時に必要となる可能性がある設定が自動的に指定されます。 たとえば、ネットワーク ポートやユーザー名を指定できます。 詳細については、「[Microsoft Intune でのモバイル アプリ構成ポリシーを使用したアプリの構成](https://technet.microsoft.com/library/mt481447.aspx)」をご覧ください。

**iOS 9 ユーザーのアプリ管理が簡単に**
このリリースでは、展開済みのアプリを iOS 9 ユーザー向けに Intune で管理できます。 以前のバージョンの iOS の場合、アプリを展開するとき、そのアプリの管理されていないバージョンが既にデバイスにインストールされているなら、まずユーザーにアプリを手動でアンインストールしてもらってからでなければ、管理されているアプリを Intune でインストールすることはできません。

 しかし、このリリースの Intune 以降では、Intune でアプリの管理を引き継ぎ、関連するモバイル アプリケーションの管理ポリシーを適用できるよう、iOS 9 デバイスのユーザーにダイアログを表示できます。

 **Windows 10 管理:** 新しい [Windows 10 の全般構成ポリシー](https://technet.microsoft.com/library/mt404697.aspx)を使用して、Windows 10 および Windows 10 Mobile を実行している登録済みデバイスのパスワード、デバイス、ブラウザーなどの設定を構成します。

 **登録済みの Windows 10 デバイスに対するアプリの作成と展開:** 新しいソフトウェア インストーラーの種類である MDM 経由の Windows インストーラー (&#42;.msi) により、Windows 10 を実行している登録済みデバイスに対して Windows インストーラー アプリを作成し、展開することができます。 詳細については、「[Microsoft Intune でのアプリ展開の開始](https://technet.microsoft.com/library/dn646955.aspx)」をご覧ください。

### Microsoft ポータル サイト アプリの変更と更新
このリリースでは、ポータル サイト アプリに次の変更が加えられました。

**iOS**
* Microsoft は、Microsoft の製品やサービスを改善するために、ポータル サイトのパフォーマンスおよび使用に関する匿名データを自動的に収集します。 エンド ユーザーがデバイスの使用状況データ設定を使用してデータの収集を無効にすることはできますが、管理者がデータの収集を制御したり、エンド ユーザーが選択した設定を変更したりすることはできません。
* iPhone 6 および iPhone 6 Plus で全画面解像度をサポート
* セキュリティ強化のためのバグ修正

### Intune ドキュメントの最新情報 -- 2015 年 9 月
**新しいトピック**

|名前|説明|
|----|--------|
|[Microsoft Intune の Windows 10 構成ポリシー設定](https://technet.microsoft.com/library/mt404697.aspx)|これは、Windows 10 および Windows 10 Mobile を実行しているデバイスの設定や機能を管理できる新しい構成ポリシーです。
| [Microsoft Intune でのモバイル アプリ構成ポリシーを使用したアプリの構成](https://technet.microsoft.com/library/mt481447.aspx)|ユーザーが iOS アプリを実行している場合に必要となる可能性のある設定を自動的に提供できる新しいポリシーの種類です。 |

**更新されたトピック**

|名前|説明|
|----|-------|
|[Microsoft Intune でポリシーを使用してコンピューターとモバイル デバイスを管理する](https://technet.microsoft.com/library/dn743712.aspx)|ポリシーの理解と作成に役立つ最新の情報が含まれるように更新されました。|

## 2015 年 8 月
### モバイル デバイスおよびアプリ管理の更新
* **Intune の登録および会社アクセスに関する使用条件** が、 [ポリシーを使って管理されるようになりました](https://technet.microsoft.com/library/mt405893.aspx)。 このため、特定のユーザー グループに対する要件に応じて、さまざまな使用条件を展開できるようになりました。 たとえば、地域に応じて定義したユーザー グループに対して、さまざまな言語の使用条件を展開できます。 また、 [使用条件の編集](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) や、バージョン番号を一定単位で増加させるかどうかの指定のほか、ポータル サイトの使用に先立ってユーザーに新しい使用条件に対する同意を求めることができるようになっています。
* **Intune ポリシーの名称が多数変更になりました** 。これは、製品内で一貫性を高め、ユーザーがポリシーを探しやすくするためのものです。 使用可能なすべての Intune ポリシーの一覧については、「[Microsoft Intune でポリシーを使用してコンピューターとモバイル デバイスを管理する](https://technet.microsoft.com/library/dn743712.aspx)」をご覧ください。
* **PKCS #12 (.PFX) 証明書プロファイル**を使用できるようになりました。これは、Android 4.0 以降および Windows 10 以降 (Desktop および Mobile) が対象です。 .PFX の使用には、NDES サーバーは必要ありません。 .PFX 証明書プロファイルの使用方法については、「[Microsoft Intune で証明書プロファイルを使用して会社のリソースへのアクセスを有効にする](http://technet.microsoft.com/library/dn818904.aspx)」を参照してください。
* **Windows 10 Desktop および Mobile に会社の境界を設定する**ことによって、詳細な VPN 設定が可能になりました。詳細については、「[Microsoft Intune での VPN プロファイルを使用したユーザー作業への接続](https://technet.microsoft.com/library/dn818905.aspx)」を参照してください。
* **Android 用の OneDrive アプリが、複数の ID をサポートするようになりました**。 この更新とモバイル アプリの管理ポリシーに対するその他の更新については、 [管理可能な Microsoft アプリケーションの一覧](https://technet.microsoft.com/library/dn708489.aspx)で説明しています。
* **iOS のアクティベーション ロックのバイパス機能**が追加されました。 会社所有の iOS デバイスがアクティべーション ロックで保護されている場合には、デバイスを消去したり、再アクティブ化したりする前に、ユーザーの Apple ID とパスワードを入力する必要があります。 そのため、ユーザーが会社を退職する際に、アクティブ化ロックをオフにせずに会社所有のデバイスを返却した場合に問題が発生することがあります。 この問題の解決方法として、[Intune のアクティブ化ロックのバイパス](https://technet.microsoft.com/library/mt414176.aspx)を使用できます。

### PC の条件付きアクセス
PC を対象とした条件付きアクセス ポリシーを構成できるようになりました。 これにより、Office デスクトップ アプリで Exchange Online および SharePoint のオンライン サービスにアクセスすることができます。
PC の条件付きアクセス ポリシーを有効にするには、PC がドメインに参加または対応している必要があります。
* PC に対する条件付きアクセスを有効にするための要件の一覧については、「[Microsoft Intune を使用して電子メールと SharePoint へのアクセスを管理する](http://technet.microsoft.com/library/dn818907)」で**条件付きアクセスの使用の準備**に関するセクションをご覧ください。
* メール アクセスに対する条件付きアクセスを有効にするときに設定できるオプションについては、「[Microsoft Intune での電子メールへのアクセスの管理](https://technet.microsoft.com/library/dn705841.aspx)」をご覧ください。
* SharePoint Online に対する条件付きアクセスを有効にするときに設定できるオプションについては、「[Microsoft Intune を使用した SharePoint Online アクセスの管理](https://technet.microsoft.com/library/dn705844.aspx)」をご覧ください。

### Microsoft ポータル サイト アプリの変更と更新
このリリースでは、ポータル サイト アプリに次の変更が加えられました。

**Android**

ユーザーがまだデバイスを管理対象として登録していない場合、サインインした後に、デバイスの登録手順が表示されるようになりました。

### Intune ドキュメントの最新情報 -- 2015 年 8 月
**新しいトピック**

|タイトル|説明|
|-----|-------|
|[Microsoft Intune でアクティブ化ロックのバイパスを使用して iOS デバイスを保護する](https://technet.microsoft.com/library/mt414176.aspx)|会社を退職したユーザーから返却されたデバイスがロックされている場合に、Intune で iOS のアクティべーション ロックをバイパスする方法について説明します。|

**更新されたトピック**

|タイトル|説明|
|-----|-------|
|[Microsoft Intune のモバイル アプリケーション管理ポリシーと共に使用できる Microsoft アプリ](https://technet.microsoft.com/library/dn708489.aspx)|モバイル アプリケーションの管理ポリシーを使って管理できるアプリに関する情報が更新されました。
|[Microsoft Intune でポリシーを使用してコンピューターとモバイル デバイスを管理する](http://technet.microsoft.com/library/dn743712.aspx)|Intune に追加された最新のポリシーについて、情報を更新しました。|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jun16_HO4-->


