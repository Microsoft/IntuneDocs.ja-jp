---
title: "Microsoft Intune の過去数か月の新機能"
titleSuffix: Intune on Azure
description: "Intune の新機能に関するページの過去の通知を確認する"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 06/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf2322a4009310e5dd561693ea6b3cdb97ab6e28
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune の新機能 (過去数か月)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>Apple Classroom アプリの管理のサポート

iPad デバイスで iOS Classroom アプリを管理できるようになりました。 クラスと学生の正しいデータで教師の iPad に Classroom アプリをセットアップした後、アプリを使って制御できるように、クラスに登録されている学生の iPad を構成します。
詳しくは、「[Configure iOS education settings](education-settings-configure-ios.md)」 (iOS の教育設定を構成する) をご覧ください。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Android アプリ向けの管理対象構成オプションのサポート<!-- 621621 -->

管理対象構成オプションをサポートする Play ストアの Android アプリを、Intune で構成できるようになりました。  この機能は、アプリによってサポートされる構成値の一覧を表示できるようにし、値を構成できるガイド付きの使いやすい UI を提供します。

### <a name="new-android-policy-for-complex-pins----722069---"></a>複雑な暗証番号 (PIN) に対する新しい Android ポリシー <!-- 722069 -->

Android 5.0 以降を搭載しているデバイスの Android デバイス プロファイルに、数値複素数タイプの必須[パスワード](device-restrictions-android.md#password)を設定できるようになりました。  反復する値や連続する値 (1111 や 1234 など) を含む暗証番号 (PIN) をデバイスのユーザーが作成しないようにするには、この設定を使います。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work デバイスの追加サポート

- **パスワードと仕事用プロファイルの設定を管理する** <!-- 612808 -->

  この新しい Android for Work デバイス制限ポリシーにより、管理対象の Android for Work デバイスで、パスワードと仕事用プロファイルの設定を管理できるようになりました。

- **仕事用プロファイルと個人プロファイル間でのデータ共有を許可する** <!-- 1045102 -->

この Android for Work デバイス制限プロファイルには、仕事用プロファイルと個人用プロファイルでのデータ共有の設定ができる新しいオプションが用意されました。

- **仕事用プロファイルと個人プロファイルの間でのコピーと貼り付けを制限する** <!-- 1046094 -->

  Android for Work デバイス用の新しいカスタム デバイス プロファイルでは、仕事用アプリと個人用アプリの間でのコピーと貼り付け操作を許可するかどうかを制限できます。

詳細については、[Android for Work 用のデバイスの制限](device-restrictions-android-for-work.md)に関するページをご覧ください。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>iOS デバイスと Android デバイスに LOB アプリを割り当てる <!-- 1057568 -->

[iOS](lob-apps-ios.md) 用 (.ipa ファイル) と [Android](lob-apps-android.md) 用 (.apk ファイル) の基幹業務 (LOB) アプリを、ユーザーまたはデバイスに割り当てることができるようになりました。

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS 用の新しいデバイス ポリシー <!-- 723774, 723815, 723826, 723830 -->

- **ホーム画面のアプリ** - [iOS デバイスのホーム画面](home-screen-settings-ios.md)に表示されるアプリを制御します。 このポリシーはホーム画面のレイアウトを変更しますが、アプリの展開は行いません。

- **AirPrint デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPrint デバイス](air-print-settings-ios-macos.md) (ネットワーク プリンター) を制御します。

- **AirPlay デバイスへの接続** - iOS デバイスのエンド ユーザーが接続できる [AirPlay デバイス](airplay-settings-ios.md) (Apple TV など) を制御します。

- **ロック画面のカスタム メッセージ** - ユーザーの iOS デバイスのロック画面に表示されるカスタム メッセージを構成して、既定のメッセージと置き換えます。 詳しくは、「[iOS デバイスで紛失モードをアクティブ化する](device-lost-mode.md)」を参照してください。

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>iOS アプリのプッシュ通知を制限する <!-- 723767 -->

Intune のデバイス制限プロファイルでは、iOS デバイスに対して次の[通知設定](app-notification-settings-ios.md)を構成できるようになりました。

- 指定したアプリの通知を完全に有効または無効にします。
- 指定したアプリの通知センターでの通知を有効または無効にします。
- アラートの種類を、**なし**、**バナー**、または**モーダル アラート**に指定します。
- このアプリに対してバッジを許可するかどうかを指定します。
- 通知サウンドを許可するかどうかを指定します。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>単一アプリ モードで自律的に実行するように iOS アプリを構成する<!-- 737837 -->

Intune のデバイス プロファイルを使って、[自律的シングル App モード](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)で指定したアプリを実行するように iOS デバイスを構成できるようになりました。 このモードを構成した場合、指定したアプリが実行されると、デバイスはそのアプリだけを実行できるようにロックされます。 たとえば、ユーザーがデバイスでテストを受けられるようにアプリを構成するような場合です。 アプリのアクションが完了した場合、または管理者がこのポリシーを削除した場合、デバイスは通常の状態に戻ります。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>iOS デバイスでメールと Web ブラウザー用の信頼されたドメインを構成する <!-- 723765 -->

iOS デバイス制限プロファイルから、次の[ドメイン設定](device-restrictions-ios.md#domains)を構成できるようになりました。

- **[マークされていないメール ドメイン]** - ユーザーが送信または受信するメールのうち、ここで指定したドメインと一致しないものは、信頼されていないメールとしてマークされます。

- **[管理された Web ドメイン]** - ここで指定した URL からダウンロードされたドキュメントは、管理されているものと見なされます (Safari のみ)。  

- **[Safari パスワードの自動入力ドメイン]** - ユーザーは、ここで指定したパターンに一致する URL からのパスワードのみを Safari に保存できます。 この設定を使うには、デバイスが監視モードであり、複数ユーザー用に構成されていない必要があります。 (iOS 9.3 以降)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS ポータル サイトで使用できる VPP アプリ <!-- 748782 -->

**利用可能な**インストールとして、iOS ボリューム購入 (VPP) アプリをエンド ユーザーに割り当てられるようになりました。 エンド ユーザーがアプリをインストールするには、Apple ストア アカウントが必要です。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Apple VPP ストアから電子ブックを同期する <!-- 800878 -->

Intune と、Apple ボリューム購入プログラム ストアから購入した[本を同期](vpp-apps-ios.md)し、ユーザーに割り当てることができるようになりました。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung KNOX Standard デバイスのマルチ ユーザー管理 <!-- 971988 -->

Samsung KNOX Standard を実行するデバイスが、Intune による[マルチ ユーザー管理](android-enroll.md)のサポート対象になりました。 つまり、エンド ユーザーは Azure Active Directory の資格情報を使ってデバイスのサインインとサインアウトを行うことができ、デバイスは使用中かどうかに関わらず一元管理されます。  サインインしたエンド ユーザーはアプリにアクセスできます。ポリシーがあれば、それが適用されます。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

### <a name="additional-windows-device-restriction-settings----818566---"></a>追加の Windows デバイス制限設定 <!-- 818566 -->

追加の Edge ブラウザー サポート、デバイス ロック画面のカスタマイズ、スタート メニューのカスタマイズ、Windows スポットライト検索セットの壁紙、プロキシ設定など、追加の [Windows デバイス制限設定](device-restrictions-windows-10.md)のサポートが追加されました。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update のマルチユーザー サポート <!-- 822547 -->

Windows 10 Creators Update を実行し Azure Active Directory ドメインに参加しているデバイスの[マルチユーザー管理](windows-enroll.md)のサポートが追加されました。 つまり、異なる標準ユーザーが Azure AD 資格情報でデバイスにログインすると、ユーザー名に割り当てられているすべてのアプリとポリシーを受け取ります。 現時点では、アプリのインストールのようなセルフサービスのシナリオにポータル サイトは使用できません。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC の Fresh Start <!-- 1004830 -->

Windows 10 PC で、新しい [Fresh Start デバイス アクション](device-fresh-start.md)が使用できるようになりました。  このアクションを発行すると、PC にインストールされたすべてのアプリが削除され、PC は Windows の最新バージョンに自動的に更新されます。 この機能は、新しい PC に付属することの多い事前インストール済み OEM アプリを削除するのに使うことができます。 このデバイス アクションを発行するときにユーザー データを保持するかどうかを構成できます。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Windows 10 の追加アップグレード パス <!-- 903672 -->

以下のエディションの Windows 10 にも、[エディション アップグレード ポリシーの作成によりデバイスをアップグレード](edition-upgrade-configure-windows-10.md)できるようになりました。

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 デバイスを一括登録する <!-- 747607 -->

Windows 構成デザイナー (WCD) で Azure Active Directory と Intune に Windows 10 Creators Update を実行する多数のデバイスを参加させることができるようになりました。 Azure AD テナントの [一括 MDM 登録](windows-bulk-enroll.md) を有効にするには、Windows 構成デザイナーを使用して Azure AD テナントにデバイスを参加させるプロビジョニング パッケージを作成し、一括登録と管理を行う会社所有のデバイスにパッケージを適用します。 パッケージがデバイスに適用されると、デバイスは Azure AD に参加し、Intune に登録され、Azure AD ユーザーがログオンできる状態になります。  Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みのポリシーと必須アプリを受け取ります。 現在のところ、セルフ サービスとポータル サイトのシナリオはサポートされていません。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>暗証番号 (PIN) および管理対象記憶域の場所に対する新しい MAM 設定<!-- 581122, 736644 -->

モバイル アプリケーション管理 (MAM) シナリオに役立つ 2 つの新しいアプリ設定が使用できるようになりました。

- **[Disable app PIN when device PIN is managed (デバイスの PIN が管理されるときはアプリの PIN を無効にする)]** - 登録されたデバイスにデバイス暗証番号 (PIN) が存在するかどうかを検出し、存在する場合は、アプリ保護ポリシーによってトリガーされるアプリ PIN をバイパスします。 この設定を使うと、登録されたデバイスで MAM が有効なアプリケーションを開くユーザーに対して表示される PIN 要求の回数を減らすことができます。 この機能は、Android と iOS の両方で使うことができます。

- **[会社のデータを保存できるストレージ サービスの選択]** - 会社のデータを保存する記憶域の場所を指定できます。 ユーザーは選択したストレージ ロケーション サービスに保存できます。つまり、表示されていない他のすべてのストレージ ロケーション サービスはブロックされます。

  サポートされるストレージ ロケーション サービスの一覧は次のとおりです。

  - OneDrive
  - Business SharePoint Online
  - ローカル ストレージ

### <a name="help-desk-troubleshooting-portal----907448---"></a>ヘルプ デスクのトラブルシューティング ポータル<!-- 907448 -->

新しい[トラブルシューティング ポータル](help-desk-operators.md)を使用すると、ヘルプ デスクと Intune 管理者は、ユーザーと彼らのデバイスを表示して、Intune の技術的な問題を解決するタスクを実行できます。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>iOS 紛失モードのサポート<!--431695-->

iOS 9.3 以降のデバイスについて、Intune で**紛失モード**のサポートが追加されました。 デバイスをロックダウンしてすべての使用を回避し、デバイスのロック画面のメッセージおよび連絡先の電話番号を表示できるようになりました。

エンドユーザーは、管理者が紛失モードを無効にするまで、デバイスのロックを解除することはできません。 紛失モードを有効にした場合、**デバイスを探索する**アクションを使用して、Intune コンソールでマップ上にデバイスの地理的な場所を表示することができます。

会社所有の iOS デバイスを DEP で登録し、監視モードに設定している必要があります。

詳細については、「[Microsoft Intune デバイスの管理とは](device-management.md)」を参照してください。

### <a name="improvements-to-device-actions-report---677150--"></a>Device Actions レポートの機能強化 <!--677150-->

Device Actions レポートの機能が強化され、パフォーマンスが向上しました。 さらに、レポートを状態別にフィルター処理できるようになりました。 たとえば、レポートをフィルター処理して、完了したデバイス アクションのみを表示できます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->

Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>登録していないデバイスを使用しているユーザーに LOB アプリを割り当てる <!--748823-->

デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。

### <a name="new-compliance-reports---846671--"></a>新しいコンプライアンス レポート <!--846671-->

コンプライアンス レポートにより、会社内のコンプライアンスの状況を表示して、社内のユーザーがコンプライアンス関連の問題に直面したときに迅速にトラブルシューティングできるようになりました。 次の情報を表示できます。

- デバイスの総合的なコンプライアンスの状態
- 設定別のコンプライアンスの状態
- ポリシー別のコンプライアンスの状態

これらのレポートを使用して個々のデバイスをドリルダウンし、そのデバイスに影響を与えている特定の設定およびポリシーを確認することもできます。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->

Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューはクラシックの Intune ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントでプレビューにアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>モバイル デバイス登録を制限する機能 <!--747600, 795782-->
Intune では、登録を許可されるモバイル デバイス プラットフォームを制御する新しい登録制限が追加されています。 Intune では、モバイル デバイス プラットフォームが iOS、macOS、Android、Windows、Windows Mobile に分かれています。

* モバイル デバイスの登録を制限しても、PC クライアントの登録は制限されません。  
* iOS と Android のみに、個人所有デバイスの登録をブロックする 1 つの追加オプションがあります。

[この記事](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices)で説明されているように、IT 管理者が明示的に会社所有と指定しない限り、Intune はすべての新しいデバイスを個人所有としてマークします。

### <a name="view-all-actions-on-managed-devices---677150--"></a>管理対象デバイスのすべての操作を表示 <!--677150-->
新しい__デバイス操作__レポートには、デバイスでの出荷時の設定にリセットなどのリモート操作を実行したユーザーが表示され、さらにその操作の状態が表示されます。 「[デバイス管理とは](device-management.md)」を参照してください。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>管理されていないデバイスから割り当てられているアプリにアクセス可能 <!--664691-->
ポータル Web サイトでの設計変更に伴い、iOS と Android ユーザーは、管理されていないデバイスで "登録なしで使用可能" として割り当てられているアプリをインストールできるようになります。 Intune 資格情報を使用して、ユーザーはポータル Web サイトにログインし、割り当てられているアプリの一覧を表示することができます。 "登録なしで使用可能" なアプリのアプリ パッケージは、ポータル Web サイトからダウンロードできます。 この変更は、インストールするために登録が必要なアプリには影響しません。そのようなアプリをインストールする場合は、デバイスの登録が求められます。

### <a name="custom-app-categories---748805--"></a>カスタム アプリのカテゴリ <!--748805-->
Intune に追加するアプリのカテゴリを作成、編集、および割り当てることができるようになりました。 現時点では、カテゴリは英語でのみ指定できます。
[Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="display-device-categories---814654--"></a>デバイス カテゴリを表示する <!--814654-->
デバイスの一覧に、列としてデバイス カテゴリを表示できるようになりました。 デバイスのプロパティー ブレードのプロパティー セクションからカテゴリを編集することもできます。 [Intune にアプリを追加する方法](apps-add.md)に関するページを参照してください。

### <a name="configure-windows-update-for-business-settings---776716--"></a>ビジネス設定向けの Windows Update の構成<!--776716-->

サービスとしての Windows は、Windows 10 の更新プログラムを提供するための新しい方法です。 Windows 10 以降、すべての新しい機能更新プログラムと品質更新プログラムには、以前の更新プログラムすべての内容が含まれます。 つまり、最新の更新プログラムをインストールしている限り、Windows 10 デバイスが完全に最新の状態であることを把握できます。 以前のバージョンの Windows とは異なり、更新プログラムの一部ではなく全体をインストールすることが必要になります。

Windows Update for Business を使用することで、デバイスのグループに対して個々の更新プログラムを承認する必要がなくなるため、更新プログラム管理エクスペリエンスを簡略化できます。 更新プログラムの展開戦略を構成することで環境内のリスクを引き続き管理でき、さらに Windows Update により更新プログラムが適切なタイミングでインストールされるようになります。 Microsoft Intune では、デバイスでの更新プログラムの設定を構成でき、また更新プログラムのインストールを遅らせることができます。 Intune では更新プログラムは格納されず、更新プログラムのポリシー割り当てのみが格納されます。 デバイスは更新プログラムのため Windows Update に直接アクセスします。**Windows 10 更新プログラム リング**を構成し管理するには Intune を使用します。 更新プログラム リングには、Windows 10 更新プログラムがインストールされるタイミングと方法を構成する設定のグループが含まれています。 詳しくは、「[ビジネス設定向けの Windows Update の構成](windows-update-for-business-configure.md)」をご覧ください。

## <a name="january-2017"></a>2017 年 1 月

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>デバイスの登録に関係なく基幹業務アプリを割り当てられる <!--748823-->
デバイスが Intune に登録されているかどうかに関係なく、基幹業務アプリをストアからユーザーに割り当てられるようになりました。 ユーザーのデバイスが Intune に登録されていない場合は、ポータル サイト アプリではなく、ポータル Web サイトに移動してインストールする必要があります。 [アプリ管理](app-management.md)に関するページを参照してください。

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>デバイスが無効か、管理コンソールとデバイスが通信できない問題を解決
ユーザーのデバイスと Intune の接続が失われるとき、新しいトラブルシューティング手順を指示できます。会社リソースへのアクセスを回復するのに役立ちます。 「[デバイスが無効か、管理コンソールとデバイスが通信できない](enrollment-troubleshoot.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)」を参照してください。

## <a name="december-2016-initial-release"></a>2016 年 12 月 (初期リリース)

### <a name="telecom-expense-management-integration-in-azure-portal--747605--"></a>Azure Portal での電気通信経費管理の統合<!--747605-->
Azure Portal では、サード パーティの電気通信経費管理 (TEM) サービスとの統合のプレビューが始められています。 Intune を使用して、国内およびローミングのデータ使用量を制限できます。 これらの統合は、[Saaswedo](http://www.saaswedo.com) で始まっています。 試用テナントでこの機能を有効にする場合は、[Microsoft サポートにお問い合わせください](https://docs.microsoft.com/intune-classic/troubleshoot/get-support)。

- ストアから iOS、Android、Windows デバイスへのアプリの展開と管理
- iOS、Android、Windows デバイスへの基幹業務 (LOB) アプリの展開と管理
- iOS と Windows デバイスへのボリューム購入アプリの展開と管理
- Android、iOS、Windows デバイス用の Web アプリの展開と管理
- iOS 管理アプリの構成プロファイル
- アプリ保護ポリシーの構成、および Intune に登録されていないデバイスへの基幹業務アプリの展開
- VPN プロファイル、アプリごとの VPN、Wi-Fi、電子メール、証明書プロファイル
- Compliance ポリシー
- Azure AD の条件付きアクセス
- オンプレミス Exchange の条件付きのアクセス
- デバイスの登録
- ロールベースのアクセス制御

## <a name="deprecated-features-in-the-azure-portal"></a>Azure Portal の非推奨の機能

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>ハードウェア識別子の行単位レビューのサポート
Azure Portal では、IMEI 番号と Apple シリアル番号のハードウェア識別子に対する行単位のレビューがサポートされません。 従来の Intune コンソールでは、コンマ区切り値 (.csv) ファイルから詳細情報をインポートし、個別のハードウェア識別子の既存の情報を上書きできます。 Azure Portal には、効率的なオプションが 1 つ用意されており、ハードウェア識別子すべての詳細情報を自動的に上書きするか、既存の識別子の新しい詳細情報を無視することができます。

#### <a name="how-this-affects-you"></a>影響
Azure Portal では、どの International Mobile Equipment Identity (IMEI) デバイスを更新するかを、行単位で決めることができません。 従来の Intune コンソールでは、この機能が引き続きサポートされます。

#### <a name="how-to-get-ready-for-this-change"></a>この変更に対応する方法
この情報は事前に提供します。これにより、変更の影響を受ける場合に、サポート管理者に知らせることができます。 この変更は、2017 年の前半、Azure Portal への移行と同時に行われる予定です。


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Apple DEP での既定の企業デバイス登録プロファイルのサポート
Azure Portal では、Apple Device Enrollment Program (DEP) デバイス シリアル番号に対して、"既定" の業務用デバイス登録プロファイルがサポートされません。 この機能は、従来の Intune コンソールでは使用できますが、プロファイルが意図せず割り当てられることがないように、今後廃止される予定です。 Azure Portal では、Apple DEP アカウントから同期されたシリアル番号に、業務用デバイスの登録プロファイルが最初に割り当てられることはありません。

#### <a name="how-this-affects-you"></a>影響
Azure Portal では、すべての Apple デバイスに対して、既定のプロファイル ポリシーを設定することはできません。 従来の Intune コンソールでは、この機能が引き続きサポートされます。

#### <a name="how-to-get-ready-for-this-change"></a>この変更に対応する方法
この情報は事前に提供します。これにより、変更の影響を受ける場合に、サポート管理者に知らせることができます。 これは、2017 年の前半、Azure Portal への移行と同時に行われる予定です。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
