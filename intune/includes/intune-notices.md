---
title: ファイルを含める
description: ファイルを含める
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 3d49d31ed08683508d3d231521e578688dd21bac
ms.sourcegitcommit: 737ad6c675deedfc6009f792023ff95981b06582
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2019
ms.locfileid: "74125527"
---
以下の通知では、今後の Intune の変更と機能に備えるために役立つ重要な情報が提供されます。

### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Intune の変更の計画: Windows 10 バージョン 1703 ポータル サイトのサポートが終了<!--5026679-->
Windows 10 バージョン 1703 (Windows 10、RS2 とも呼ばれます) は、2019 年 10 月 8 日に Enterprise エディションと EDU エディションのサービスを終了しました。 Intune では、2019 年 12 月 26 日より、RS2/RS1 に対応するポータル サイト アプリのサポートが終了します。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
今後、特定のバージョンのポータル サイト アプリの新機能は表示されませんが、2019 年 12 月 26 日まではこのバージョンのポータル サイト アプリが引き続きサポートされます。必要に応じてポータル サイト アプリに対するセキュリティ更新プログラムも提供します。 ただし、Windows 10 バージョン 1703 では、サービスの終了後、セキュリティ更新プログラムを受信しなくなるため、お使いの Windows デバイスを新しいバージョンの Windows に更新して、最新のポータル サイト アプリを使用することを強くお勧めします。これにより、引き続き新機能と追加機能が受信されます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
実行するステップは、環境の構成によって異なります。 ただし、一般的には、古いバージョンの OS またはポータル サイトが搭載されているデバイスを特定して更新する必要があります。 Windows 10 更新リングを設定するには、Intune にログインし、ソフトウェア更新プログラムで Windows 10 更新リングを選択します。 ポータル サイトの最新バージョンは、10.3.5601.0 です。 今後のリリースでも最新の状態を維持するため、ユーザーには Microsoft Store から取得するように指示してください。 Intune を使用して、[ビジネス向け Microsoft Store](https://docs.microsoft.com/intune/windows-store-for-business) から Windows デバイスに最新のものをインストールすることもできます。

#### <a name="additional-information"></a>追加情報
[Microsoft Intune を使用して Windows 10 ポータル サイト アプリを手動で追加する](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>アクションの実行: 保護されている Intune ブラウザーエクスペリエンスに Microsoft Edge を使用する<!--5728447-->
過去 1 年にわたってお伝えしているように、Microsoft Edge モバイルでは Managed Browser と同じ管理機能セットをサポートしながら、エンド ユーザー エクスペリエンスも大幅に向上しています。 Microsoft Edge で提供されている堅牢なエクスペリエンスを推進するため、Intune Managed Browser を廃止します。 2020 年 1 月 27 日から、Intune では Intune Managed Browser がサポートされなくなります。  

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響 
2020 年 2 月 1 日以降、Intune Managed Browser は Google Play ストアまたは iOS アプリ ストアでは入手できなくなります。 この時点では、新しいアプリ保護ポリシーを Intune Managed Browser に適用することはできますが、新しいユーザーは Intune Managed Browser アプリをダウンロードできません。 また、iOS では、MDM に登録されたデバイスにプッシュされた新しい Web クリップは、Intune Managed Browser ではなく Microsoft Edge で開きます。  

2020 年 3 月 31 日に、Intune Managed Browser は Azure コンソールから削除されます。 これで、Intune Managed Browser に新しいポリシーを作成できなくなります。 既に設定されている Intune Managed Browser ポリシーは影響を受けません。 Intune Managed Browser は、コンソールでアイコンのない基幹業務アプリとして表示され、既存のポリシーは引き続きアプリの対象として表示されます。 この時点で、[アプリ保護] ポリシーの [データ保護] セクション内の Intune Managed Browser に Web コンテンツをリダイレクトするオプションも削除されます。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備 
Intune Managed Browser から Microsoft Edge へのスムーズな移行を実現するために、次のステップを事前に行うことをお勧めします。 

1. アプリ保護ポリシー (MAM とも呼ばれます) とアプリ構成設定を使用して、Microsoft Edge を iOS と Android の対象とします。 これらの既存のポリシーを Microsoft Edge にも適用するだけで、Microsoft Edge で Intune Managed Browser のポリシーを再利用できます。  
2. 環境内のすべての MAM で保護されたアプリで、アプリ保護ポリシーの設定 [その他のアプリでの Web コンテンツの転送を制限する] が [ポリシーで管理されているブラウザー] に設定されているようにします。 
3. MAM で保護されているものすべてのマネージド アプリ構成設定 "com.microsoft.intune.useEdge" を true に設定します。 翌月以降の 1911 のリリースで、ステップ 2 と 3 を簡単に実行できるようになります。[アプリ保護] ポリシーの [データ保護] セクションで [その他のアプリでの Web コンテンツの転送を制限する] の設定に "Microsoft Edge" を含めるだけです。 

iOS および Android での Web クリップのサポートが予定されています。 このサポートがリリースされたら、既存の Web クリップの対象を再設定して、それらが Managed Browser ではなく Microsoft Edge で開くようにする必要があります。 

#### <a name="additional-information"></a>追加情報
詳細については、[Microsoft Edge とアプリ保護ポリシーの使用](../apps/manage-microsoft-edge.md) に関するドキュメント、または[サポートのブログ記事](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)を参照してください。


### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>変更の計画: Intune に Android エンタープライズ専用デバイスを登録するときのエクスペリエンスの更新<!--5198878-->
Intune の 11 月または 1911 のリリースでは、SCEP デバイス証明書の展開のサポートが Android エンタープライズ専用デバイスに追加され、Wi-Fi プロファイルへの証明書ベースのアクセスが可能になります。 この変更には、Android エンタープライズ専用デバイスを登録するときのフローに関する若干の変更も含まれます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
環境内の Android エンタープライズ専用デバイスを管理している場合は、11 月になるといくつかの変更のロールアウトを目にし始めます。

- 新しい Android エンタープライズ専用デバイスを登録する場合: 登録時にデバイスでエンド ユーザーに表示される一連の手順が異なります。 登録の開始方法は現在と同じですが (QR、NFC、ゼロタッチ、またはデバイス識別子を使用)、11月のサービス リリース後は、必須アプリのインストール手順が含まれるようになります。
- 専用デバイスとして登録されている既存の Android デバイスの場合: 11 月初め以降、Intune では、デバイスに Microsoft Intune アプリが自動的にインストールされるようになります。 ユーザーは何も行う必要はありません。 アプリは、自動的にダウンロードされて、デバイスにインストールされます。 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
エンド ユーザー ガイドを更新し、この変更をヘルプデスクに通知するように計画する必要があります。 詳細とスクリーンショットについては、「追加情報」をクリックしてください。 この変更のロールアウトが始まったら、"新機能" ページが更新されます。

#### <a name="additional-information"></a>追加情報
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>変更の計画: Intune コンソールからの 'Siri コマンドに対するサーバー側のログ記録' 設定の削除 <!-- 5468501-->

Intune サービスの 11 月の更新で、Intune コンソールから設定 "Siri コマンドに対するサーバー側のログ記録" が削除される予定です。 この変更により、既にこの設定が削除されている Apple との連携がもたらされます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
11 月の更新、または 11 月中旬の 1911 のロールアウトが行われると、ユーザーは、Intune コンソールで、iOS 構成プロファイルの [デバイスの制限] メニュー (組み込みアプリ) からこの設定が削除されていることを確認できます。 ポリシーと対象デバイスの管理プロファイルにこの設定が表示される場合がありますが、デバイスには影響しません。 管理プロファイルに表示されたとしても、これは現在デバイス上で機能していないため、機能に対する大きな影響はないと予測されます。

次の 2 つのパスのどちらかを選択できます。
- ポリシーからこの設定を削除したい場合は、この設定が含まれているプロファイルに移動し、小規模の編集を行ってポリシーを保存することができます。 バックエンドでポリシーが再計算され、ポリシーから設定が削除されます。
- この操作を行わないことを選んだ場合、エンド ユーザーのデバイスの管理プロファイルにこの設定が表示されますが、この設定による影響はありません。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
上記のセクションに従って対応策を取るか、ポリシーをそのままにしておくことができます。 この変更がロールアウトされたとき、Microsoft の新機能に関するページとドキュメントが更新されます。

### <a name="end-of-support-for-legacy-pc-management"></a>従来の PC 管理のサポート終了

従来の PC 管理は 2020 年 10 月 15 日にサポートが終了します。 デバイスを Windows 10 にアップグレードし、Intune による管理が継続されるように MDM デバイスとして再登録してください。

[詳細情報](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Android デバイス管理者のサポートの縮小 
Android デバイス管理者 ("従来の" Android 管理とも呼ばれ、Android 2.2 でリリースされました) は、Android デバイスを管理する方法の 1 つです。 しかし、[Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5.0 でリリース) では、強化された管理機能を使用できるようになりました。 Google では、より豊富で安全な最新のデバイス管理に移行するための努力の一環として、新しい Android リリースでのデバイス管理者のサポートを縮小させています。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Google によるこのような変更により、Intune ユーザーは次のような影響を受けます。  
- Intune では、デバイス管理者が管理する Android デバイスで、Android 10 以降 (Android Q とも呼ばれる) を稼働しているもののサポートを、2020 年夏までのみ提供できます。 これは、Android の次のメジャー バージョンのリリースが予定されている日付です。   
- 2020 年夏以降、デバイス管理者が管理するデバイスで、Android 10 以降を稼働しているものは、完全には管理できなくなります。       
- デバイス管理者が管理する Android デバイスで、Android 10 より前の Android バージョンのままであるものは影響を受けません。デバイス管理者で引き続き完全に管理できます。    
- Google では、Android 10 以降を稼働しているすべてのデバイスに対して、ポータル サイトのようなデバイス管理者の管理エージェントを使ってデバイス識別子の情報にアクセスする機能を制限しています。 これにより、Android 10 以降にデバイスを更新した後、次の Intune 機能が影響を受けます。  
    - VPN のネットワーク アクセス制御が機能しなくなる。   
    - IMEI またはシリアル番号を使用した企業所有のデバイスの識別で、デバイスが企業所有として自動的にマークされなくなる。  
    - Intune で IT 管理者に IMEI とシリアル番号が表示されなくなる。 
        > [!NOTE]
        > これが影響を与えるのは、デバイス管理者が管理するデバイスで Android 10 以降のもののみです。Android Enterprise として管理されているデバイスには影響しません。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
2020 年夏に実施される機能の縮小を回避するために、次のことをお勧めします。
- 新しいデバイスをデバイス管理者の管理にオンボードしない。
- デバイスが Android 10 への更新プログラムを受け取ることが予想される場合は、それをデバイス管理者の管理から外し、Android Enterprise 管理、アプリ保護ポリシーのいずれかまたは両方に移行する。

#### <a name="additional-information"></a>追加情報
- [デバイス管理者から Android Enterprise への移行に関する Google のガイダンス](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [デバイス管理者 API の廃止計画に関する Google のドキュメント](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android 用ポータル サイト アプリを最新バージョンに更新する <!--4536963-->
Intune では、Android 用ポータル サイト アプリに対する更新プログラムが定期的にリリースされます。 2018 年 11 月に、ポータル サイトの更新プログラムがリリースされました。これには、Google による既存の通知プラットフォームから Google の Firebase Cloud Messaging (FCM) への変更に備えるための、バックエンド スイッチが含まれていました。 Google が既存の通知プラットフォームを終了して FCM に移行したとき、エンド ユーザーは、Google Play ストアとの交信を継続するために、各自のポータル サイト アプリを少なくとも 2018 年 11 月のリリースに更新済みである必要があります。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
利用統計情報では、5.0.4269.0 よりも前のバージョンのポータル サイトを備えたデバイスがあることが示されています。 このバージョン以上のポータル サイト アプリをインストールしないと、ワイプ、パスワードのリセット、入手可能な必須アプリのインストール、証明書の登録のような、IT プロフェッショナルが開始したデバイス アクションが意図したとおりに機能しない場合があります。 ご自身のデバイスが Intune の MDM に登録されている場合は、[クライアント アプリ] – [検出されたアプリ] に移動することで、ポータル サイトのバージョンとユーザーを確認できます。 以前のバージョンのポータル サイト アプリを選択すると、どのエンド ユーザーがポータル サイト アプリを更新していないデバイスを持っているのかを確認できます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
更新していない Android デバイスを使っているエンド ユーザーに、Google Play を使ってポータル サイト アプリを更新するよう依頼します。 ユーザーがポータル サイト アプリの自動更新を維持していない場合は、ヘルプ デスクに通知します。 Google の FCM プラットフォームと変更について詳しくは、"*追加情報*" にあるリンクをご覧ください。

#### <a name="additional-information"></a>追加情報
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Intune に追加された新しい全画面のエクスペリエンス <!--4593669-->
Azure portal では、Intune に対する更新された UI 作成および編集のエクスペリエンスがロールアウトされています。 この新しいエクスペリエンスでは、1 つのブレード内にまとめられたウィザード形式のフォーマットを使用することで、既存のワークフローが簡素化されます。 この更新によって、"ブレードが無秩序に増える" ことや、ブレードを詳細にドリルダウンしていくことが求められる作成および編集のフローが回避されます。 また、作成のワークフローは、割り当て (アプリ割り当て以外) を含むように更新されます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
全画面のエクスペリエンスは、次の数か月間にわたって、portal.azure.com および devicemanagement.microsoft.com の両方で Intune にロールアウトされます。 この UI の更新は、既存のポリシーとプロファイルの機能には影響を及ぼしませんが、少し変更されたワークフローが表示されます。 たとえば、新しいポリシーを作成するときに、いくつかの割り当てをポリシーの作成後に行うのではなく、このフローの一部として設定できます。 コンソールでの新しいエクスペリエンスの外観を示したスクリーンショットは、"*追加情報*" にあるブログ投稿で確認してください。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
何らかのアクションを行う必要はありませんが、必要に応じて IT プロフェッショナル向けのガイダンスの更新を検討できます。 Microsoft では、Azure portal 上で Intune 内の各種のブレードに対してこのエクスペリエンスが公開され次第、ドキュメントを更新する予定です。

#### <a name="additional-information"></a>追加情報 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>変更の計画:今後のリリースで、Android 用の Intune App SDK およびアプリ保護ポリシーによる Android 5.0 以降のサポートを開始 <!--4911065 -->
Intune では、今後のリリースで、Android 5.x (Lollipop) 以降のサポートが開始されます。 ラップされたすべてのアプリを最新の Intune App SDK で更新し、デバイスを更新してください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Android 用の SDK またはアプリを使用していない、または使用する予定がない場合は、この変更による影響はありません。 Intune App SDK を使用している場合は、必ず最新バージョンに更新し、またデバイスも Android 5.x 以降に更新してください。 お客様が更新を行わなかった場合、アプリで更新プログラムを受信できなくなり、時間の経過と共にそのエクスペリエンスの質が低下していきます。

Intune に登録されていて、Android バージョン 4.x を稼働している一般的なデバイスの一覧を以下に示します。 これらのデバイスのいずれかを使用している場合は、適切な手順を実行して、必ずそのデバイスで Android バージョン 5.0 以降をサポートするようにするか、それを Android バージョン 5.0 以降をサポートするデバイスに置き換えるようにしてください。 この一覧は、評価が必要なすべてのデバイスを網羅しているわけではありません。

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
最新の Intune App SDK でアプリをラップしてください。 また、[最低限の OS バージョンを必要とします (警告のみ)] という条件付き起動を設定して、個人用デバイスを使用しているエンド ユーザーにアップグレードするよう通知することもできます。

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune の変更の計画:Windows 7 のサポート終了間近<!-- 3042987 -->
2018 年 9 月に投稿した MC148476 および 2019 年 3 月の MC176794 で再びお伝えしたとおり、Windows 7 の延長サポートは 2020 年 1 月 14 日に終了いたします。 その時点で、Windows 7 を稼働しているデバイスに対する Intune のサポートは終了します。これにより、より新しいテクノロジのサポートと、優れた新しいエンド ユーザー エクスペリエンスの提供に注力することが可能になります。 当該日付以降は、お使いの Windows 7 PC を保護するための技術的なサポートと自動更新が Intune で利用できなくなります。 もう利用できないサービスやサポートが必要になるシナリオを回避するために、2020 年 1 月より前に Windows 10 に移行することを強くお勧めします。 Windows のサポート ライフサイクルについて詳しくは、[こちら](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)をご覧ください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
このメッセージは、現在レガシ Intune PC ソフトウェア エージェントを使って Windows 7 PC を管理しているお客様に送信されます。 Windows 7 の延長サポート終了まで 1 年未満となったため、お客様の組織が、できるだけ早く Windows 10 へのアップグレードを開始することを強くお勧めします。  

PC 管理機能は Windows 10 オペレーティング システムに直接組み込まれているため、Windows 7 用の Intune ソフトウェア クライアントなどのクライアント エージェントをインストールする必要はもうありません。 Windows 8.1 以降、Microsoft では、Windows PC のプロビジョニング、構成、更新、および管理を行うためにモバイル デバイス管理 (MDM) アーキテクチャが使われています。 Intune の設定が完了したら、MDM チャネルを通じて [Intune に Windows 10 PC を登録](..\windows-enroll.md)することで、Windows の登録を簡易化できます。 この "エージェントレス" MDM 管理ソリューションを使って Windows 10 PC を管理することをお勧めします。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
お客様の組織で次のアクション プランをすぐに検討することをお勧めします。

- 2020 年 1 月 14 日より前に、一連の Windows 7 の Windows 10 へのアップグレードを計画し、実行する。
- [Windows 10 の展開サポート](https://docs.microsoft.com/windows/deployment/)に関するページを参照し、使用している Windows 7 PC 全体を Windows 10 にアップグレードする方法について詳しく学習する。
- FastTrack を通じて [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) サービスを確認する (Microsoft のアプリケーション互換性に関する約束が支援されます)。
- 既存のレガシ Intune ソフトウェア クライアントのマネージド デバイスを Microsoft 推奨のソリューションに移行し、MDM 管理を使用して Windows 10 を管理する。 すべての新しい Windows 10 PC を、Azure portal で Intune の MDM 管理を使って登録する。

さらなる情報については、[こちらのブログ投稿](https://aka.ms/Windows7_Intune)を参照してください。
