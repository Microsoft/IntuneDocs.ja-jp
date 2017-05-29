---
title: "Office 365 アプリの基本的なデータ管理を設定する - Intune Azure プレビュー"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Manage Office 365 apps (Office 365 アプリの管理) ウィザードのサポート ドキュメント。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 639d045e036ecdc6ff40d6ae335d2c5109d9e420
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---


# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps"></a>管理対象の Office 365 アプリの基本的な保護に関するユーザー エクスペリエンス

**Manage Office 365 apps (Office 365 アプリの管理)** ウィザードでは、各デバイス プラットフォームのアプリ保護ポリシーを作成します。

このウィザードでは、次のポリシーが有効になります。

**iOS**
* [アプリ データの暗号化]

**Android**
* [アプリ データの暗号化]
* [アクセスには簡易暗証番号が必要]

これらのポリシーにより、Office 365 アプリを管理し、必要に応じて Office アプリからの仕事のデータをワイプできるようになります。 また、仕事のデータを暗号化し、PIN を入力しないと Office 365 アプリでデータを表示できないようにすることで、デバイスを紛失したり盗まれたりした場合の基本的な保護が提供されます。


この記事では、例として OneDrive for Business を使用して、Intune で管理されているアプリケーションでのユーザー エクスペリエンスについて説明します。


>[!NOTE]
>個人用デバイスの場合は、通常、エンドユーザーがアプリをダウンロードします。 デバイスがモバイル デバイス管理 (MDM) ソリューションで管理されている場合は、管理者がアプリをデバイスに展開できます。

## <a name="user-experience-on-an-ios-device"></a>iOS デバイスでのユーザー エクスペリエンス

1. OneDrive for Business アプリを起動し、サインイン ページを開きます。  <br/> ![iOS の OneDrive サインイン画面の画像](./media/onedrive-ios-sign-in.png)
2. 自分の作業アカウントのユーザー名を入力します。 Office 365 認証ページにリダイレクトされたら、作業用の資格情報を入力します。 <br/> ![Office 365 サインイン ページの画像](./media/o365-sign-in-ios.png)
3. Azure Active Directory によって資格情報が正常に認証されると、モバイル デバイス管理 (MDM) ポリシーが適用され、OneDrive for Business アプリを再起動するように求められます。  <br/>![iOS の再起動を求めるメッセージの画像](./media/ios-restart-prompt.png)
>[!NOTE]
>再起動を求めるメッセージは、Intune に登録されていないデバイスにのみ表示されます。


4. OneDrive for Business アプリを再起動します。 MAM ポリシーが有効になっている状態でアプリが起動すると、デバイスの PIN を設定するように求められます (デバイスで PIN をまだ構成していない場合)。 <br/> ![PIN を作成するように求めるメッセージの画像](./media/pin-prompt-ios.png)

>[!NOTE]
>ほとんどのユーザーには、このメッセージが表示されません。 iOS デバイスで PIN を有効にしていないユーザーにのみこのメッセージが表示されます。


5. PIN を設定して確認すると、OneDrive for Business アプリに戻ります。 IT 管理者が OneDrive の仕事のデータを保護していることを伝える 1 回限りの通知が表示されます。 <br/> ![IT 管理者からの 1 回限りの通知の画像](./media/one-time-notice.png)
6. この通知をクリックして、OneDrive for Business のファイルにアクセスします。 <br/> ![iOS デバイスでの OneDrive ファイルの画像](./media/onedrive-files-ios.png) <br/>

>[!NOTE]
>展開済みのポリシーを変更すると、次回アプリを開いたときにその変更が適用されます。


## <a name="user-experience-on-an-android-device"></a>Android デバイスでのユーザー エクスペリエンス

1. OneDrive for Business アプリを起動し、サインイン ページを開きます。  <br/> ![OneDrive アプリのようこそ画面の画像](./media/onedrive-android-welcome.png)
2. 自分の作業アカウントのユーザー名を入力します。 Office 365 認証ページにリダイレクトされたら、作業用の資格情報を入力します。 <br/> ![Android での O365 サインインの画像](./media/o365-sign-in-android.png)
3. Azure Active Directory によって資格情報が正常に認証されると、まだポータル サイト アプリがデバイスにインストールされていない場合はインストールするよう指示するメッセージが表示されます。 **[ストアにアクセス]** をタップして、続行します。 <br/> ![ポータル サイト アプリを入手する際のメッセージの画像](./media/get-company-portal-android.png) <br/>ポータル サイト アプリが電話に既にインストールされている場合は、OneDrive for Business アプリが自動的に起動し、文末脚注にスキップできます。
>[!IMPORTANT]
>Office アプリを MAM ポリシーで管理するように設定すると、Android では、エンド ユーザーが電子メールやドキュメントを実際に読むのにポータル サイト アプリを開いたり、ポータル サイト アプリにサインインしたりする必要がない場合でも、デバイスのユーザーは仕事の電子メールやドキュメントにアクセスするためにポータル サイト アプリをインストールする**必要があります**。

4. Google Play ストアが開かれるので、そこからポータル サイト アプリをダウンロードしてインストールします。 ポータル サイト アプリを使うと、データを安全に保護できます。 <br/> ![Google Play ストアでのアプリの画像](./media/google-play-get-app-android.png)
5. アプリのインストールが完了したら、**[同意する]** を選択して使用条件に同意します。 OneDrive for Business アプリが自動的に起動します。


>[!NOTE]
>IT 管理者が PIN の設定を要求している場合、OneDrive for Business を次に開いたときに、PIN の設定を求められます。 PIN を設定して確認すると、OneDrive for Business を利用できます。

![PIN の入力を求めるメッセージの画像](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>このウィザードではどのようなポリシーが設定されますか。
|     |       | |
|----|--------|-|
|**名前**|Office 365 アプリの管理| |
| **説明**|Manage Office 365 apps (Office 365 アプリの管理) ウィザードで作成されました| |
| |  | |
| **設定の名前** |**iOS ポリシーの値** | **Android ポリシーの値** |
|[iTunes と iCloud でのバックアップを禁止する]| いいえ | N/A |
|[Android でのバックアップを禁止する] |N/A | いいえ|
|[アプリで他のアプリへのデータ転送を許可する] | すべてのアプリ | すべてのアプリ|
|[アプリで他のアプリからのデータの受信を許可する]| すべてのアプリ | すべてのアプリ|
|[名前を付けて保存] を禁止する | いいえ | いいえ|
|他のアプリとの間で切り取り、コピー、貼り付けを制限する | すべてのアプリ | すべてのアプリ |
|[Web コンテンツを会社の管理対象ブラウザーで表示するように制限する] | いいえ| いいえ|
|[アプリ データの暗号化] | デバイスがロックされている場合 | [はい]|
|連絡先の同期を無効にする | いいえ| いいえ|
|印刷を無効にする | いいえ | いいえ|
|アクセスのために PIN を要求する | いいえ | [はい]|
|[暗証番号をリセットするまでの試行数] | N/A |5|
|単純な PIN を許可する | N/A |Yes|
|PIN の長さ | N/A | 4|
|PIN の代わりに指紋を要求する | N/A | [はい] |
|[アクセスには会社の資格情報が必要] | いいえ | いいえ|
|[脱獄またはルート化されたデバイスで管理対象アプリが実行されないようにブロックする] | いいえ | いいえ|
|(分数) 後に、アクセス要件を再確認する - タイムアウト | 30 | 30|
|(分数) 後に、アクセス要件を再確認する - オフラインの猶予期間 | 720 |720|
|アプリのデータがワイプされるまでのオフライン期間 (日数) | 90 | 90|
|スクリーン キャプチャをブロックする (Android デバイスのみ) | N/A | いいえ |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>Android デバイスでのみアプリの PIN ポリシーが構成されるのはなぜですか。
iOS と Android で暗号化の動作が異なります。

iOS の場合、Intune MAM ポリシーに関連付けられているアプリでは、データはオペレーティング システムによって提供されるデバイス レベルの暗号化を使用して、格納中に暗号化されます。 そのため、アプリ暗号化ポリシーを有効にすると、デバイスの PIN を設定し、仕事のデータにアクセスする際に入力するようユーザーに自動的に要求します。 デバイスでデバイスの PIN をまだ構成していないユーザーは、デバイスの PIN を作成するよう求められます。

Android の場合、Intune MAM ポリシーに関連付けられているアプリでは、ファイル I/O タスク中にデータが同期的に暗号化されます。 デバイス ストレージ上のコンテンツは常に暗号化されます。 MDM で管理されていないデバイスの場合、MAM ポリシーでデバイスの PIN の要件を強制することはできません。 仕事のデータにアクセスする際に PIN を使用するようユーザーに求めるには、ウィザードでアプリの PIN ポリシーを有効にします。

これらのポリシー設定は、組織の要件に合わせていつでも編集できます。

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>ウィザードで作成したポリシーを表示および編集するにはどうすればよいですか。
これらのポリシーや、Intune Azure プレビューで作成したポリシーを表示または更新するには、ダッシュボードで **[アプリの管理]** > **[App Protection Policies (アプリ保護ポリシー)]** の順に選択します。 右側にポリシーの一覧が開きます。 設定を表示および編集するポリシーを選択します。 <br/>
![ポリシーを表示するユーザー インターフェイス パスの画像](./media/image-for-faq.png)

## <a name="next-steps"></a>次のステップ
アプリ保護ポリシーの詳細については、[こちら](https://docs.microsoft.comapp-protection-policy.md)を参照してください。

