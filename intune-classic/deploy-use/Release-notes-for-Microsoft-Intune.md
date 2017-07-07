---
title: "Microsoft Intune のリリース ノート"
description: "Intune リリース ノート"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 751bd0bc90b762c5b51b85fae2129e53773b54fe
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="release-notes-for-microsoft-intune"></a>Microsoft Intune のリリース ノート

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune は、クラウドベースの総合的なクライアント管理ソリューションで、さまざまな管理ツールとレポート機能が搭載され、Windows の最新バージョンへのアップグレード ライセンスも利用できます。 また、コンピューターを常に最新で安全な状態に保つことができます。 また、Intune を使用すると、ネットワーク上のモバイル デバイスを Microsoft Easy Assist または Intune で直接管理できます。 このリリース ノートでは、Microsoft Intune の重要な情報と既知の問題について説明します。

<!-- 3-6-17: customer asked if this is still current; Stacie asked Chris Baldwin about it. Chris said it's a Samsung issue, but that he hasn't heard any reports about it for months, so he suggested that I share that with the customer and remove this item from the release notes. I'm only going to comment it out in case it resurfaces.
## Android users can’t send email when conditional access for Exchange Online is implemented

**Issue:** Users running Samsung Android 5.1.1 and later on their devices can't send email when conditional access for Exchange Online has been set up. Samsung acknowledges that the issue is in its built-in email client in Android 5.1.1 and later, and is investigating a fix.

**Workaround 1:** Advise users to use the Outlook app for Android.

**Workaround 2:** To let affected users send email, you can follow these steps:

1. Put each affected user in a security group in the “exempted groups” section of the conditional access policy for Exchange Online.
2. Let the user temporarily sync email on the built-in email client.
3. Remove the affected user from the exempted group, and confirm that the user can now send email.

Microsoft will continue to work closely with Samsung on a fix or additional workarounds.
-->


## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>iOS と Android のグループ間でリソース アクセス プロファイルを変更するとエラーになる
**問題:** グループ間の電子メールまたは Simple Certificate Enrollment Protocol (SCEP) のリソース アクセス プロファイルを変更すると、プロファイルが競合し、失敗する場合があります。 たとえば、グループ A を対象にしたオンプレミスの Exchange サーバーをポイントする既存の電子メール プロファイルがあり、さらにグループ B を対象とした Exchange オンラインをポイントする新しい電子メール プロファイルを作成するとします。グループ A からグループ B にユーザーを移動すると、デバイスはオンプレミスの Exchange 電子メール プロファイルを保持し、グループ B を対象とした Exchange オンラインの電子メール プロファイルをインストールしようとします。

この時点で、次のいずれかが発生します。 
* 電子メール プロファイル A と B が同じである場合、電子メール プロファイル B に電子メール プロファイル A が既に含まれているため、デバイスが電子メール プロファイル B を拒否します。
* 例のように電子メール プロファイル A が電子メール プロファイル B と異なる場合は、デバイスに 2 つの電子メール プロファイルが作成されることになります。

> [!NOTE]
> 電子メール プロファイルを区別するため、ユーザー名に使用されるホスト名と属性が確認されます。

どちらの場合も、電子メールまたはクライアントの SCEP 証明書へのユーザー アクセスが誤って削除されないように、デバイスからリソース アクセス プロファイル (電子メール プロファイル) は削除されていません。

**対応策:** なし。

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>プロキシ サーバーに対して認証が必要な Windows 8.1 デバイスを登録すると、登録プロセスが失敗しますが、エラーの原因が表示されません
**問題:** Windows 8.1 デバイスを登録するときに、登録プロセスでデバイスをプロキシ サーバーに対して認証する必要がある場合、プロキシ サーバーの資格情報がデバイスにキャッシュされていなければ、登録は失敗します。 プロキシ サーバーの資格情報がデバイスにキャッシュされていない場合、登録プロセスはユーザーが資格情報を入力するまで待機する必要があります。 ただし、登録プロセス中は、プロキシ サーバーの資格情報を入力するプロンプトが表示されません。 結果として、登録プロセスはプロキシ サーバーに対して認証できません。 このエラーはユーザーに表示されません。

**対応策:** 認証済みのプロキシ サーバーを使用する必要があるネットワークで、Windows 8.1 デバイスを登録する必要がある場合は、プロキシ サーバーの資格情報をセットアップし、保存してから、デバイスを登録します。 Windows 8.1 デバイスで資格情報をセットアップして保存するには:

1.  Windows 8.1 デバイスで、Internet Explorer を開きます。
2.  プロキシ サーバーの資格情報を入力するプロンプトが表示されたら、資格情報を入力し、オプション **[資格情報を記憶する]**を選択します。
3.  デバイスを登録します。

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>AD FS でデバイス認証が有効になっていると Microsoft Intune に Windows Phone 8.1 デバイスを登録できません
**問題:** Windows Phone 8.1 デバイスを登録するとき、Active Directory フェデレーション サービス (AD FS) のグローバル認証ポリシーの一部としてデバイス認証のオプション設定が有効になっている場合、登録に失敗します。

**対応策:** **[グローバル認証ポリシーの編集]** で **[デバイス認証を有効にする]**のチェックを外し、AD FS サーバーでデバイス認証を無効にします。 詳細については、「[Configuring Authentication Policies](http://technet.microsoft.com/library/dn486781.aspx)」(認証ポリシーの構成) を参照してください。


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>Android 用の Microsoft Intune アプリ ラッピング ツールには、アンインストール機能が組み込まれていません。
**問題:** **Android 用の Microsoft アプリ ラッピング ツール**には、ツールをアンインストールする機能が組み込まれていません。

**対応策:** ツールがインストールされている場所を指定し、ディレクトリを削除します。 既定のインストール場所は、**C:\Program Files\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool です。 アプリ ラッピング ツールの詳細については、「[アプリ ラッピング ツールで管理するために Android アプリを準備する](/intune/app-wrapper-prepare-android)」を参照してください。

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>Windows 8 または Windows 8.1 を実行するコンピューターでリモート アシスタンスを使用できません
**問題:** このリリースでは、Windows 8 または Windows 8.1 を実行しているコンピューターでリモート アシスタンス機能を使用できません。

**対応策:** なし。

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>自動で追加された受信者に、アラート通知が機能しない場合がある
**問題:** アラート通知に受信者が自動的に追加された場合、この受信者は通知を受信しない可能性があります。

**対応策:** 受信者がメッセージ通知を受信するには、アラート通知に受信者を手動で追加する必要があります。

## <a name="language-support-in-the-azure-portal"></a>Azure ポータルの言語サポート
Azure ポータルがサポートしている言語は、簡体字中国語、繁体字中国語、チェコ語、オランダ語、英語、ドイツ語、ハンガリー語、イタリア語、日本語、ポルトガル (ブラジル) 語、ポルトガル (ポルトガル) 語、ロシア語、スペイン語、英語、フランス語、韓国語、ポーランド語、スウェーデン語、およびトルコ語です。

Intune 管理コンソールとユーザーが対面するモバイル エクスペリエンスでは、Azure ポータルでサポートされている言語だけでなくデンマーク語、ギリシャ語、フィンランド語、ノルウェー語、およびルーマニア語もサポートしています。
