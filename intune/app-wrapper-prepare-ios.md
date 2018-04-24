---
title: Intune アプリ ラッピング ツールで iOS アプリをラップする
description: アプリ自体のコードを変更することなく、iOS アプリをラップする方法について説明します。 モバイル アプリ管理ポリシーを適用できるように、アプリを準備します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8e2783be3c515aa742a3adc149304e0a2ae3b99
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Intune アプリ ラッピング ツールでアプリ保護ポリシーを利用するために iOS アプリを準備する

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

iOS 用 Microsoft Intune アプリ ラッピング ツールを使用すれば、アプリ自体のコードを変更せずに社内の iOS アプリの Intune アプリ保護ポリシーを有効にすることができます。

このツールはアプリを囲むように "ラッパー" を作成する macOS コマンド ライン アプリケーションです。 アプリが処理されると、[アプリ保護ポリシー](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)をアプリに展開することで、アプリの機能を変更できます。

このツールをダウンロードする場合は、GitHub の「[iOS 用 Microsoft Intune アプリ ラッピング ツール](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios)」を参照してください。



## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>アプリ ラッピング ツールの一般的な前提条件

アプリ ラッピング ツールを実行する前に、いくつかの一般的な前提条件を満たす必要があります。

* GitHub から [iOS 用 Microsoft Intune アプリ ラッピング ツール](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios)をダウンロードします。

* OS X 10.8.5 以降を実行し、Xcode ツールセットのバージョン 5 以降がインストールされている mac OS コンピューター。

* 入力 iOS アプリはあなたの会社または独立系ソフトウェア ベンダー (ISV) が開発し、署名したものでなければなりません。

  * 入力アプリのファイルの拡張子は、**.ipa** または **.app** でなければなりません。

  * 入力アプリは、iOS 8.0 以降 用にコンパイルする必要があります。

  * 入力アプリは暗号化できません。

  * 入力アプリに拡張ファイル属性を持つことはできません。

  * 入力アプリを Intune アプリ ラッピング ツールで処理する前に、権限を設定する必要があります。 [権限](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html)によって、アプリに通常よりも多くのアクセス許可や機能が付与されます。 手順については、「[アプリ権限の設定](#setting-app-entitlements)」を参照してください。

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>アプリ ラッピング ツールの Apple Developer の前提条件

ラップされたアプリを組織のユーザーだけに配布するには、[Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/) のアカウントと、自分の Apple Developer アカウントとリンクしたアプリ署名のいくつかのエンティティが必要です。

組織のユーザーに内部的に iOS アプリを配布する方法の詳細については、「[Distributing Apple Developer Enterprise Program Apps](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1)」(Apple Developer Enterprise Program アプリの配布) の公式ガイドを参照してください。

Intune によってラップされたアプリを配布するには、次が必要となります。

* Apple Developer Enterprise Program の開発者アカウント。

* 有効なチーム識別子を持つ、社内およびアドホック配布の署名証明書。

  * Intune アプリ ラッピング ツールのパラメーターとして、署名証明書の SHA1 ハッシュが必要になります。


* 社内配布プロビジョニング プロファイル。

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Apple Developer Enterprise アカウントを作成する手順
1. [Apple Developer Enterprise Program のサイト](https://developer.apple.com/programs/enterprise/)に移動します。

2. ページの右上にある **[Enroll]** (登録) をクリックします。

3. 何を登録する必要があるかのチェックリストを参照してください。 ページの下部にある **[Start Your Enrollment]** (登録の開始) をクリックします。

4. 組織の Apple ID で**サインイン**します。 Apple ID がない場合は、**[Create Apple ID]** (Apple ID の作成) をクリックします。

5. **[Entity Type]** (エンティティ型) を選択して、**[Continue]** (続行) をクリックします。

6. 組織の情報をフォームに入力します。 **[続行]** をクリックします。 この時点で、組織を登録する権限があるかどうかが Apple によって確認されます。

8. 確認したら、**[Agree to License]** (ライセンスに同意する) をクリックします。

9. ライセンスに同意したら、**プログラムを購入し、アクティブ化して**終了します。

10. チーム エージェント (組織に代わって Apple Developer Enterprise Program に参加する人) である場合は、最初にチーム メンバーを招待して役割を割り当てて、チームを作成します。 チームを管理する方法については、Apple のドキュメント「[開発者アカウント チームの管理](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1)」を参照してください。

### <a name="steps-to-create-an-apple-signing-certificate"></a>Apple 署名証明書を作成する手順

1. [Apple Developer ポータル](https://developer.apple.com/)に移動します。

2. ページの右上にある **[アカウント]** をクリックします。

3. 組織の Apple ID を使用して**サインイン**します。

4. **[Certificates, IDs & Profiles]** (証明書、ID、プロファイル) をクリックします。

   ![Azure Developer ポータル](./media/iOS-signing-cert-1.png)

5. をクリックして ![右上隅の Apple Developer ポータルのプラス記号をクリックして、](./media/iOS-signing-cert-2.png) iOS 証明書を追加します。

6. **[Production]** (運用) の下にある **[In-House and Ad Hoc]** (社内およびアドホック) 証明書の作成を選択します。

   ![社内およびアドホック証明書を選択する](./media/iOS-signing-cert-3.png)

   >[!NOTE]
   >アプリを配布する予定がなく、内部でテストのみ行いたい場合、本番用の証明書の代わりに iOS アプリ開発用の証明書を使用できます。 開発用の証明書を使用する場合、モバイルのプロビジョニング プロファイルがアプリをインストールするデバイスを参照するようにしてください。

7. ページの下部にある **[Next]** (次へ) をクリックします。

8. macOS コンピューターでキーチェーン アクセス アプリケーションを使用して**証明書署名要求 (CSR)** を作成する方法を確認します。

   ![CSR を作成する方法を確認する](./media/iOS-signing-cert-4.png)

9. 上記の手順に従い、証明書署名要求を作成します。 macOS コンピューターで、**キーチェーン アクセス** アプリケーションを起動します。

10. 画面の上部にある macOS メニューで **[キーチェーン アクセス] > [証明書アシスタント] > [Request a Certificate From a Certificate Authority]\(証明機関から証明書を要求する)** の順に移動します。  

    ![キーチェーン アクセスで証明機関から証明書を要求する](./media/iOS-signing-cert-5.png)

11. 上記の Apple Developer サイトの指示に従い、CSR ファイルを作成します。 macOS コンピューターに CSR ファイルを保存します。

    ![キーチェーン アクセスで証明機関から証明書を要求する](./media/iOS-signing-cert-6.png)

12. Apple Developer サイトに戻ります。 **[続行]** をクリックします。 それから、CSR ファイルをアップロードします。

13. Apple から署名証明書が生成されます。 これをダウンロードして、macOS コンピューター上の覚えやすい場所に保存します。

    ![署名証明書をダウンロードする](./media/iOS-signing-cert-7.png)

14. ダウンロードした証明書ファイルをダブルクリックして、証明書をキーチェーンに追加します。

15. もう一度、**キーチェーン アクセス**を開きます。 右上の検索バーに証明書の名前を入力して探します。 項目を右クリックして開いたメニューから、**[Get Info]** (情報を取得する) をクリックします。 例の画面では、本番用の証明書の代わりに開発用の証明書を使用しています。

    ![証明書をキーチェーンに追加する](./media/iOS-signing-cert-8.png)

16. 情報ウィンドウが表示されます。 一番下までスクロールし、**[Fingerprints]** (指紋) ラベルの下を確認します。 アプリ ラッピング ツールの "-c" 引数として使用するため、**[SHA1]** 文字列 (図ではぼかしています) をコピーします。

    ![証明書をキーチェーンに追加する](./media/iOS-signing-cert-9.png)



### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>社内配布プロビジョニング プロファイルを作成する手順

1. [Apple Developer アカウント ポータル](https://developer.apple.com/account/)に戻り、組織の Apple ID で**サインイン**します。

2. **[Certificates, IDs & Profiles]** (証明書、ID、プロファイル) をクリックします。

3. をクリックして ![右上隅の Apple Developer ポータルのプラス記号をクリックして、](./media/iOS-signing-cert-2.png) iOS プロビジョニング プロファイルを追加します。

4. **[Distribution]** (配布) の下にある **[In House]** (社内) プロビジョニング ファイルの作成を選択します。

   ![社内プロビジョニング プロファイルを選択する](./media/iOS-provisioning-profile-1.png)

5. **[続行]** をクリックします。 以前に生成された署名証明書をこのプロビジョニング プロファイルにリンクさせてください。

6. 手順に従って、macOS コンピューターにプロファイル (拡張子 .mobileprovision) をダウンロードします。

7. ファイルを覚えやすい場所に保存します。 このファイルは、アプリ ラッピング ツールを使用しているときに -p パラメータで使用されます。



## <a name="download-the-app-wrapping-tool"></a>アプリ ラッピング ツールをダウンロードする

1.  アプリ ラッピング ツールのファイルを [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) から macOS コンピューターにダウンロードします。

2.  **Microsoft Intune App Wrapping Tool for iOS.dmg** をダブルクリックします。 エンド ユーザー ライセンス条項 (EULA) のウィンドウが表示されます。 ドキュメントをよくお読みください。

3. EULA に同意する場合は **[同意する]** をクリックします。コンピューターにパッケージがマウントされます。

4.  **IntuneMAMPackager** フォルダーを開き、その内容を macOS コンピューターに保存します。 これでアプリ ラッピング ツールを実行する準備が整いました。

> [!NOTE]
> Intune MAM Packager は、macOS コンピューターに個別にマウントでき、結果として、ラッピング コマンドを実行するときに "ファイルが見つかりません" というエラーが発生する可能性があります。 そのため、IntuneMAMPackager フォルダーの内容を移動にすると、Packager へのパスがラッピングの間に見つかります。

## <a name="run-the-app-wrapping-tool"></a>アプリ ラッピング ツールを実行する

### <a name="use-terminal"></a>ターミナルを使用する

macOS ターミナル プログラムを開き、アプリ ラッピング ツールのファイルを保存したフォルダーに移動します。 実行可能ツールの名前は IntuneMAMPackager で、IntuneMAMPackager/Contents/MacOS にあります。 次のようにコマンドを実行します。

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> 次の表に示すように、一部のパラメーターはオプションです。

**例:** 次のコマンド例では、MyApp.ipa という名前のアプリでアプリ ラッピング ツールを実行しています。 プロビジョニング ファイルと署名証明書の SHA-1 ハッシュが指定され、ラッピングされたアプリに署名するために使用されます。 出力アプリ (MyApp_Wrapped.ipa) が作成され、ユーザーのデスクトップ フォルダーに格納されます。

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>コマンド ライン パラメーター
アプリ ラッピング ツールでは次のコマンド ライン パラメーターを使用できます。

|プロパティ|使用方法|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`。 ファイル名は .app または .ipa で終わる必要があります。 |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**|アプリ ラッピング ツールに使用できるコマンド ライン プロパティの詳細な使用情報を表示します。|
|**-v**|(省略可能) 詳細なメッセージをコンソールに出力します。 このフラグを使用してすべてのエラーをデバッグすることをお勧めします。|
|**-e**| (省略可能) このフラグを使用すると、アプリ ラッピング ツールが、アプリを処理する際に不足している権利を削除します。 詳細については、「[アプリ権利の設定](#setting-app-entitlements)」を参照してください。|
|**-xe**| (省略可能) アプリの iOS 拡張機能に関する情報、およびそれを使用するために必要な権利を出力します。 詳細については、「[アプリ権利の設定](#setting-app-entitlements)」を参照してください。 |
|**-x**| (省略可能)`<An array of paths to extension provisioning profiles>`。 これは、アプリが拡張機能のプロビジョニング プロファイルを必要とする場合に使用します。|
|**-f**|(省略可能) `<Path to a plist file specifying arguments.>` このフラグは plist テンプレートを使用して -i、-o、-p といった残りの IntuneMAMPackager プロパティを指定する場合に、[plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) ファイルの前に使用します。 「plist を使用して引数を入力する」を参照してください。 |
|**-b**|(省略可能) ラッピングされた出力アプリに入力アプリと同じバンドル バージョンが含まれるようにする場合、-b を引数なしで使用します (推奨しません)。 <br/><br/> ラッピングされたアプリにカスタム CFBundleVersion が含まれるようにするには、`-b <custom bundle version>`を使用します。 カスタム CFBundleVersion を指定する場合、たとえば最下位のコンポーネントから、ネイティブ アプリの CFBundleVersion をインクリメントすることをお勧めします (例: 1.0.0 -> 1.0.1)。 |

### <a name="use-a-plist-to-input-arguments"></a>plist を使用して引数を入力する
すべてのコマンド引数を [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) ファイルに置くと、アプリ ラッピング ツールを簡単に実行できます。 Plist は XML に似たファイル形式で、フォームのインターフェイスを使用してコマンドライン引数を入力できます。

[IntuneMAMPackager/Contents/MacOS] フォルダーで、`Parameters.plist` (空白の plist テンプレート) をテキスト エディターまたは Xcode で開きます。 次のキーの引数を入力します。

| Plist キー |  既定値| 注 |
|------------------|--------------|-----|
| 入力アプリケーション パッケージのパス  |空| -i と同じ|
| 出力アプリケーション パッケージのパス |空| -o と同じ|
| プロビジョニング プロファイルのパス |空| -p と同じ|
| SHA-1 証明書ハッシュ |空| -c と同じ|
| 詳細が有効です |false| -v と同じ|
| 不足している権利を削除します | false| -c と同じ|
| 既定のビルドを防ぎます |false | 引数なしで -b を使用したのと同じ|
|ビルド文字列の上書き | 空| ラッピングされた出力アプリのカスタム CFBundleVersion |
|拡張機能のプロビジョニング プロファイルのパス | 空| アプリの拡張機能のプロビジョニング プロファイルの配列。


次のように IntuneMAMPackager と plist を単一の引数として実行します。

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>ラッピング後

ラッピング処理が完了すると、"アプリケーションが正常にラッピングされました" という内容のメッセージが表示されます。 エラーが発生した場合、対処方法については、「[エラー メッセージ](#error-messages-and-log-files)」を参照してください。

ラッピングされたアプリは先に指定した出力フォルダーに保存されます。 このアプリを Intune 管理コンソールにアップロードし、モバイル アプリケーション管理ポリシーに関連付けることができます。

> [!IMPORTANT]
> 古い (ラッピング済みまたはネイティブ) バージョンが既に Intune に展開されている場合、ラッピングされたアプリをアップロードするときに、古いバージョンのアプリの更新を試行することができます。 エラーが発生した場合は、アプリを新しいアプリとしてアップロードし、古いバージョンを削除します。

これで、アプリをユーザー グループに展開し、そのアプリをアプリ保護ポリシーの対象にすることができます。 アプリは、指定したアプリ保護ポリシーを使用して、デバイスで実行されます。

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>どれくらいの頻度で自分の iOS アプリケーションを Intune アプリ ラッピング ツールで再ラップする必要がありますか。
アプリケーションを再ラップしなければならない主なシナリオは、次のとおりです。
* アプリケーション自体で、新しいバージョンがリリースされた。 以前のバージョンのアプリがラップされ、Intune コンソールにアップロードされた。
* iOS 用 Intune アプリ ラッピング ツールで新しいバージョンがリリースされ、主要なバグ修正、または新しい具体的な Intune アプリケーション保護ポリシー機能が有効になった。 これは、[iOS 用 Microsoft Intune アプリ ラッピング ツール](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios)の GitHub リポジトリで 6 ～ 8 週間後に行われます。

iOS では、アプリへの署名に元々使用されたものとは異なる証明書/プロビジョニング プロファイルでラップすることができますが、アプリで指定された資格が新しいプロビジョニング プロファイルに含まれていないと、ラップは失敗します。 このシナリオで強制的にラッピングが失敗しないように、アプリから不足している資格を削除する "-e" コマンドライン オプションを使用すると、アプリの機能が損なわれる可能性があります。

再ラップの場合、次のようなベスト プラクティスがあります。
* 別のプロビジョニング プロファイルが、以前のプロビジョニング プロファイルと同じ必須の資格を持っていることを確認します。 

## <a name="error-messages-and-log-files"></a>エラー メッセージとログ ファイル
アプリ ラッピング ツールに関する問題を解決するには、次の情報を参照してください。

### <a name="error-messages"></a>エラー メッセージ
アプリ ラッピング ツールが正常に完了できない場合、次のエラー メッセージのいずれかがコンソールに表示されます。

|エラー メッセージ|詳細情報|
|-----------------|--------------------|
|有効な iOS プロビジョニング プロファイルを指定する必要があります。|プロビジョニング プロファイルが有効ではない可能性があります。 デバイスのアクセス許可が与えられていることとプロファイルの目標が開発または配布であることを確認します。 プロビジョニング プロファイルが期限切れになっている可能性もあります。|
|有効な入力アプリケーション名を指定します。|指定した入力アプリケーション名が正しいことを確認します。|
|出力アプリケーションの有効なパスを指定します。|指定した出力アプリケーションのパスが存在し、正しいことを確認します。|
|有効な入力プロビジョニング プロファイルを指定します。|有効なプロビジョニング プロファイル名と拡張子を指定したことを確認します。 プロビジョニング プロファイルに権利が足りないか、–p コマンドライン オプションを追加していない可能性があります。|
|指定した入力アプリケーションが見つかりませんでした。 有効な入力アプリケーションの名前とパスを指定します。|入力アプリ パスが有効であり、存在することを確認します。 入力アプリがその場所に存在することを確認します。|
|指定した入力プロビジョニング プロファイル ファイルが見つかりませんでした。 有効な入力プロビジョニング プロファイル ファイルを指定します。|入力のプロビジョニング ファイルのパスが有効であり、指定したファイルが存在することを確認します。|
|指定した出力アプリケーション フォルダーが見つかりませんでした。 出力アプリケーションの有効なパスを指定します。|指定した出力パスが有効であり、存在することを確認します。|
|出力アプリに **.ipa** 拡張子がありません。|アプリ ラッピング ツールは、**.app** 拡張子と **.ipa** 拡張子があるアプリのみを受け取ります。 出力ファイルに有効な拡張子があることを確認します。|
|無効な署名証明書が指定されました。 有効な Apple 署名証明書を指定します。|Apple 開発者ポータルから適切な署名証明書をダウンロードしていることを確認します。 証明書の期限が切れているか、公開キーまたは秘密キーがない可能性があります。 Apple 証明書とプロビジョニング プロファイルを使用し、Xcode 内で正しくアプリに署名できる場合、それらはアプリ ラッピング ツールで有効です。|
|指定した入力アプリケーションが無効です。 有効なアプリケーションを指定します。|.app または .ipa ファイルとしてコンパイルされた有効な iOS アプリケーションがあることを確認します。|
|指定した入力アプリケーションが暗号化されています。 有効な暗号化されていないアプリケーションを指定します。|アプリ ラッピング ツールでは、暗号化されたアプリはサポートされません。 暗号化されていないアプリを指定します。|
|指定した入力アプリケーションは PIE (Position Independent Executable/位置独立実行) 形式ではありません。 PIE 形式の有効なアプリケーションを指定します。|PIE (Position Independent Executable/位置独立実行) アプリは実行時にランダム メモリ アドレスで読み込むことができてます。 また、セキュリティ上の利点になります。 セキュリティ上の利点の詳細については、Apple 開発者ドキュメントを参照してください。|
|指定した入力アプリは既にラッピングされています。 ラッピングされていない有効なアプリケーションを指定します。|このツールによって既に処理されているアプリを処理することはできません。 アプリを再度処理する場合、元のバージョンのアプリを使用し、ツールを実行します。|
|指定した入力アプリケーションは署名されていません。 署名されている有効なアプリケーションを指定します。|アプリ ラッピング ツールでは、アプリに署名が必要です。 ラッピングされたアプリに署名する方法については、開発者ドキュメントを参照してください。|
|指定した入力アプリケーションは .ipa または .app 形式である必要があります。|アプリ ラッピング ツールは .app 拡張子と .ipa 拡張子のみを受け取ります。 入力ファイルに有効な拡張子があり、.app または .ipa ファイルとしてコンパイルされていることを確認します。|
|指定した入力アプリは既にラッピングされていて、最新のポリシー テンプレート バージョンです。|アプリ ラッピング ツールは、既にラッピングされ、ポリシー テンプレート バージョンが最新のアプリを再ラッピングしません。|
|警告: SHA1 証明書ハッシュを指定しませんでした。 展開前にラッピングされたアプリケーションが署名されていることを確認します。|-c コマンドライン フラグの後に有効な SHA1 ハッシュを指定します。 |

### <a name="log-files-for-the-app-wrapping-tool"></a>アプリ ラッピング ツールのログ ファイル
アプリ ラッピング ツールでラッピングされているアプリはログを生成し、ログが iOS クライアント デバイス コンソールに書き込まれます。 この情報は、アプリケーションで問題が発生し、問題がアプリ ラッピング ツールに関連するかどうかを判断する必要がある場合に役立ちます。 この情報を取得するには、次の手順を使用します。

1.  アプリケを実行し、問題を再現します。

2.  「 [展開された iOS アプリのデバッグ](https://developer.apple.com/library/ios/qa/qa1747/_index.html)」にある Apple の指示に従い、コンソール出力を集めます。

3.  次のスクリプトをコンソールに入力し、アプリ制限出力の保存ログをフィルター処理します。

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    Microsoft にフィルター処理したログを送信できます。

    > [!NOTE]
    > ログ ファイルで、「build version」という項目は Xcode のビルド バージョンを表します。

    ラッピングしたアプリはまた、アプリのクラッシュ後に電子メールでデバイスからログを直接送信するオプションをユーザーに提供します。 ユーザーはログをあなたに送信し、あなたはそれを調べ、必要に応じて Microsoft に転送できます。


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>証明書、プロビジョニング プロファイル、認証に関する要件

iOS 用アプリ ラッピング ツールには、すべての機能を保証するために満たす必要があるいくつかの要件があります。

|要件|説明|
|---------------|-----------|
|iOS プロビジョニング プロファイル|プロビジョニング プロファイルを追加する前に、これが有効であるかどうかを確認します。 アプリ ラッピング ツールは、iOS アプリを処理するとき、プロビジョニング プロファイルの有効期限が切れているかどうかを確認しません。 有効期限が切れたプロビジョニング プロファイルが指定された場合も、アプリ ラッピング ツールはそのプロファイルを追加します。iOS デバイスでアプリのインストールに失敗するまで、問題があることはわかりません。|
|iOS 署名証明書|署名証明書を指定する前に、これが有効であるかどうかを確認します。 このツールは、iOS アプリを処理するとき、証明書の有効期限が切れているかどうかを確認しません。 有効期限が切れた証明書のハッシュを指定すると、このツールはアプリを処理し、署名しますが、デバイスにインストールすると失敗します。<br /><br />ラッピングされたアプリに署名するために提供された証明書がプロビジョニング プロファイルと一致することを確認します。 このツールは、ラッピングされたアプリケーションに署名するために提供された証明書とプロビジョニング プロファイルが一致するかどうかを検証しません。|
|認証|暗号化を機能させるには、デバイスに PIN を設定する必要があります。 ラッピングされたアプリを展開したデバイスで、デバイスのステータス バーに触れると、ユーザーは職場のアカウントまたは学校のアカウントを使用して再度サインするように求められます。 ラッピングしたアプリの既定のポリシーは、*再起動時に認証*です。 iOS はアプリを終了してから、再起動して、あらゆる外部通知 (電話の着信など) を処理します。


## <a name="setting-app-entitlements"></a>アプリ権利の設定
アプリをラップする前に、アプリに*権利*を付与して、通常のアプリよりも多くのアクセス許可と機能を与えることができます。 *権利ファイル*は、アプリ内に特殊なアクセス許可 (たとえば、共有キーチェーンへのアクセスなど) を指定するコード署名で使用されます。 アプリの開発中に、Xcode 内で特定のアプリケーション サービス (*機能*と呼ばれます) が有効になります。 機能が有効になると、権利ファイルに反映されます。 権利と機能の詳細については、iOS 権利および機能の詳細については、iOS 開発者ライブラリの「[Adding Capabilities (機能の追加)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)」を参照してください。 サポートされる機能の一覧については、「[Supported capabilities (サポートされる機能)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html)」を参照してください。

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>iOS 用アプリ ラッピング ツールでサポートされる機能

|機能|説明|推奨される方法|
|--------------|---------------|------------------------|
|アプリ グループ|アプリ グループを使用して、複数のアプリが共有コンテナーにアクセスできるようにします。また、アプリ間の追加のプロセス間通信を許可します。<br /><br />アプリ グループを有効にするには、**[機能]** ウィンドウを開き、**[アプリ グループ]** の **[オン]** をクリックします。 アプリ グループを追加するか、既存のグループを選択することができます。|アプリ グループを使用する場合は、次のように逆引き DNS 表記を使用します。<br /><br />*group.com.companyName.AppGroup*|
|バックグラウンド モード|バックグラウンド モードを有効にすると、iOS アプリを継続的にバックグラウンドで実行できるようになります。||
|データの保護|データ保護を使用すると、iOS アプリでディスクに保存されているファイルのセキュリティ レベルを追加できます。 データ保護は、特定のデバイスに組み込まれている暗号化ハードウェアを使用して、暗号化された形式でディスクにファイルを保存します。 データ保護を使用するようにアプリをプロビジョニングする必要があります。||
|アプリ内購入|アプリ内購入は、ストアへの接続を有効にしてアプリにストアを直接組み込み、ユーザーから支払いを安全に処理します。 アプリ内購入を使用すると、強化された機能で支払いを収集し、アプリから追加のコンテンツを使用できるようになります。||
|キーチェーンの共有|キーチェーンの共有を有効にすると、同じチームで開発されたアプリ間でキーチェーン内のパスワードを共有できるようになります。|キーチェーンの共有を使用する場合は、次のように逆引き DNS 表記を使用します。<br /><br />*com.companyName.KeychainGroup*|
|個人の VPN|個人の VPN を有効にすると、アプリでネットワーク拡張機能フレームワークを使用して、カスタム システム VPN 構成を作成および制御できるようになります。||
|プッシュ通知|Apple Push Notification サービス (APNS) を使用すると、フォアグラウンドで実行されていないアプリでも、ユーザーに対する情報がある場合にユーザーに通知できます。|プッシュ通知を使用するには、アプリ固有のプロビジョニング プロファイルを使用する必要があります。<br /><br />[Apple 開発者ドキュメント](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)の手順を実行してください。|
|ワイヤレス アクセサリの構成|ワイヤレス アクセサリの構成を有効にすると、外部アクセサリ フレームワークをプロジェクトに追加し、アプリで MFi Wi-Fi アクセサリを設定できるようになります。||

### <a name="steps-to-enable-entitlements"></a>権利を有効にする手順

1.  アプリで機能を有効にします。

    」を参照します。  Xcode で、アプリのターゲットに移動し、**[Capabilities]** をクリックします。

    b.  目的の機能を有効にします。 各機能の詳細と正しい値の指定方法については、iOS 開発者ライブラリの「[Adding Capabilities (機能の追加)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)」を参照してください。

    c.  処理中に作成した ID をメモします。

    d.  ラップするアプリをビルドして署名します。

2.  プロビジョニング プロファイルで権利を有効にします。

    」を参照します。  Apple Developer Member Center にサインインします。

    b.  アプリのプロビジョニング プロファイルを作成します。 手順については、「[iOS 用 Intune アプリ ラッピング ツールの前提条件を取得する方法](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/)」を参照してください。

    c.  プロビジョニング プロファイルで、アプリ内と同じ権利を有効にします。 アプリの開発時に指定したものと同じ ID を指定する必要があります。

    d.  プロビジョニング プロファイル ウィザードを完了し、ファイルをダウンロードします。

3.  すべての前提条件を満たしていることを確認してから、アプリをラップします。

### <a name="troubleshoot-common-errors-with-entitlements"></a>権利に関する一般的なエラーのトラブルシューティング
iOS 用アプリ ラッピング ツールで権利のエラーが表示される場合は、次のトラブルシューティング手順を実行します。

|問題|原因|解決策|
|---------|---------|--------------|
|入力アプリケーションから生成された権利を解析できませんでした。|アプリ ラッピング ツールは、アプリから抽出された権利ファイルを読み取れません。 権利ファイルは、形式が正しくない可能性があります。|アプリの権利ファイルを調査します。 次の手順でこの方法について説明します。 権利ファイルを調査する場合、形式が正しくない構文がないかを確認します。 権利ファイルは、XML 形式である必要があります。|
|プロビジョニング プロファイルに足りない権利があります (不足している権利が表示されます)。 不足している権利を含むプロビジョニング プロファイルを使用してアプリを再パッケージします。|プロビジョニング プロファイルで有効な権利と、アプリで有効な機能が一致していません。 この不一致は、一部の機能 (アプリ グループ、キーチェーンのアクセスなど) に関連付けられた ID にも適用されます。|通常、アプリと同じ機能を有効にした新しいプロビジョニング プロファイルを作成できます。 プロファイルとアプリ間で ID が一致しない場合、アプリ ラッピング ツールは可能であれば ID を置き換えます。 新しいプロビジョニング プロファイルを作成した後もこのエラーが発生する場合、–e パラメーターを使用して権利を削除できます (以下の「–e パラメーターを使用してアプリから権利を削除する」セクションを参照してください)。|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>署名済みアプリの既存の権利を検索する
署名済みアプリの既存の権利とプロビジョニング プロファイルを確認するには:

1.  .ipa ファイルを検索して、拡張子を .zip に変更します。

2.  .zip ファイルを展開します。 .app バンドルを含む Payload フォルダーが生成されます。

3.  codesign ツールを使用して .app バンドルの権利を確認します。`YourApp.app` は .app バンドルの実際の名前です。

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4.  セキュリティ ツールを使用して、アプリに組み込まれているプロビジョニング プロファイルの権利を確認します。`YourApp.app` は .app バンドルの実際の名前です。

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>–e パラメーターを使用してアプリから権利を削除する
このコマンドは、権利ファイルに含まれていないアプリで有効になっているすべての機能を削除します。 アプリが使用している権利を削除すると、アプリは損なわれます。 欠落している機能を削除する例とは、既定ですべての機能を備えているベンダー製のアプリがある場合です。

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>アプリ ラッピング ツールのセキュリティとプライバシー
アプリ ラッピング ツールを使用するとき、セキュリティとプライバシーの次のベスト プラクティスを使用します。

-   指定した署名証明書、プロビジョニング プロファイル、基幹業務アプリは、アプリ ラッピング ツールを実行する同じ macOS マシンに置く必要があります。 ファイルが UNC パスにある場合、ファイルに macOS マシンからアクセスできることを確認します。 パスは IPsec または SMB 署名を使用して保護する必要があります。

    管理コンソールにインポートしたラッピングされたアプリケーションは、ツールを実行するのと同じコンピューター上に存在する必要があります。 ファイルが UNC パスにある場合、管理コンソールを実行するコンピューターでファイルにアクセスできることを確認します。 パスは IPsec または SMB 署名を使用して保護する必要があります。

-   アプリ ラッピング ツールを GitHub リポジトリからダウンロードする環境は IPsec または SMB 署名を使用して保護する必要があります。

-   攻撃を防ぐために、処理するアプリは信頼できる配信元のものである必要があります。

-   アプリ ラッピング ツールに指定する出力フォルダーが守られていることを確認します (リモート フォルダーの場合は特に)。

-   ファイル アップロードのダイアログ ボックスを含む iOS アプリでは、アプリに適用されている切り取り、コピー、貼り付けの制限を回避できます。 たとえば、ファイル アップロードのダイアログ ボックスを利用し、アプリ データのスクリーンショットをアップロードできます。

-   ラッピングされたアプリ内からデバイスのドキュメント フォルダーをユーザーが監視するとき、.msftintuneapplauncher という名前のフォルダーが表示されることがあります。 このファイルを変更または削除すると、制限付きのアプリの正常な動作に影響を与える可能性があります。

## <a name="getting-logs-for-your-wrapped-applications"></a>ラッピングされたアプリケーションのログを取得する
トラブルシューティング時に、次の手順を使用して、ラッピングされたアプリケーションのログを取得します。

1. デバイスで iOS の設定アプリに移動し、LOB アプリを選択します。
2. **[診断コンソール]** を **[オン]** に切り替えます。
3. LOB アプリケーションを起動します。
4. "開始" リンクをクリックします。
5. メールまたは OneDrive の保存先にコピーする方法を利用して、ログを共有できるようになりました。

> [!NOTE]
> ログ記録機能は、バージョン 7.1.13 以降の Intune アプリ ラッピング ツールでラッピングされたアプリで使用できます。

### <a name="see-also"></a>関連項目
- [Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](apps-prepare-mobile-application-management.md)</br>
- [Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)</br>
- [SDK を使用してモバイル アプリケーション管理に対応する](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
