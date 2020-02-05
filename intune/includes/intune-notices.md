---
title: ファイルを含める
description: インクルード ファイル
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 6064fb657454106a8a7213e0bbbcecdcef765857
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966362"
---
以下の通知では、今後の Intune の変更と機能に備えるために役立つ重要な情報が提供されます。

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>'Adobe Acrobat Reader for Intune' モバイル アプリのサポート ステートメントが更新されました<!--5746776-->
8 月の終わりに、MC188653 で、Adobe Acrobat Reader for Intune モバイル アプリが 2019 年 12 月 1 日に有効期限終了になり、Adobe が同社のメインの Acrobat Reader アプリ内で Intune のアプリ保護ポリシーのサポートを計画していることをお知らせしました。 その後、お客様から、IT 管理者が引き続きターゲットを指定して、エンド ユーザーが Adobe Acrobat Reader for Intune の使用を開始できるようにするために、もっと時間を提供してもらう必要があるというフィードバックを受け取りました。 エンド ユーザーのデバイスで Adobe Acrobat Reader for Intune の使用率が高く、エンタープライズ シナリオでのその重要性を考慮すると、あらゆるエクスペリエンスが、組織のアプリ保護のニーズを満たすようにする必要があります。 

Acrobat Reader モバイル アプリはアプリ保護ポリシーをサポートし、Intune SDK を統合しているため、一般的な Acrobat Reader モバイル アプリをポリシーでターゲット設定することを引き続きお勧めしますが、Adobe Acrobat Reader for Intune アプリは 2020 年 3 月 31 日まで引き続きサポートされます。 

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
このメッセージが表示されるのは、組織内の 1 つ以上のポリシーが Adobe Acrobat Reader for Intune アプリケーションを対象としているか、以前の EOL 通信を受け取った可能性があることを Microsoft のレポートで示しているためです。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
この変更について、エンド ユーザーとヘルプデスクに通知します。 [ポータル サイトのサポート情報機能](../apps/company-portal-app.md#support-information)を使用して、Intune 関連の質問のためのチャネルを確立できます。

#### <a name="additional-information"></a>追加情報
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Windows Phone 8.1 に対するサポートの終了<!--3544909-->
Windows Phone 8.1 に対する Microsoft のメインストリーム サポートは 2017 年 7 月に終了し、拡張サポートは 2019 年 6 月に終了しました。 Windows Phone 8.1 用のポータル サイト アプリは、2017 年 10 月から維持モードになっています。 2020 年 2 月 20 日に、Windows Phone 8.1 に対する Microsoft Intune のサポートが終了します。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
2020 年 2 月 20 日を過ぎると、これらのデバイスはセキュリティ更新プログラムを受信しなくなり、新しいデバイスを登録できなくなります。 既存の Windows Phone 8.1 デバイスは登録されたままになります (ポリシー、アプリ、レポート) が、既存の登録に関するトラブルシューティングは、この日付を過ぎるとサポートされなくなります。これは、サード パーティ証明書など、多くのコンポーネントでこのプラットフォームのサポートが既に終了しているためです。 Intune では、Intune と Windows Phone 8.1 を使った互換性テストが停止されます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
Intune レポートをチェックして、影響を受ける可能性のあるデバイスまたはユーザーを確認できます。 [デバイス]、[すべてのデバイス]、の順に移動し、[OS] で絞り込みます。 さらに列を追加して、Windows Phone 8.1 を稼働しているデバイスを持つ組織内のユーザーの特定に役立てることができます。 エンド ユーザーに対して、各自のデバイスをサポートされている OS バージョンにアップグレードするようにリクエストしてください。


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>アクションの実行: 保護されている Intune ブラウザーエクスペリエンスに Microsoft Edge を使用する<!--5728447-->
過去 1 年にわたってお伝えしているように、Microsoft Edge モバイルでは Managed Browser と同じ管理機能セットをサポートしながら、エンド ユーザー エクスペリエンスも大幅に向上しています。 Microsoft Edge で提供されている堅牢なエクスペリエンスを推進するため、Intune Managed Browser を廃止します。 2020 年 1 月 27 日から、Intune では Intune Managed Browser がサポートされなくなります。  

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響 
2020 年 2 月 1 日以降、Intune Managed Browser は Google Play ストアまたは iOS アプリ ストアでは入手できなくなります。 この時点では、新しいアプリ保護ポリシーを Intune Managed Browser に適用することはできますが、新しいユーザーは Intune Managed Browser アプリをダウンロードできません。 また、iOS では、MDM に登録されたデバイスにプッシュされた新しい Web クリップは、Intune Managed Browser ではなく Microsoft Edge で開きます。  

2020 年 3 月 31 日に、Intune Managed Browser は Azure コンソールから削除されます。 これで、Intune Managed Browser に新しいポリシーを作成できなくなります。 既に設定されている Intune Managed Browser ポリシーは影響を受けません。 Intune Managed Browser は、コンソールでアイコンのない基幹業務アプリとして表示され、既存のポリシーは引き続きアプリの対象として表示されます。 この時点で、[アプリ保護] ポリシーの [データ保護] セクション内の Intune Managed Browser に Web コンテンツをリダイレクトするオプションも削除されます。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備 
Intune Managed Browser から Microsoft Edge へのスムーズな移行を実現するために、次のステップを事前に行うことをお勧めします。 

1. アプリ保護ポリシー (MAM とも呼ばれます) とアプリ構成設定を使用して、Microsoft Edge を iOS と Android の対象とします。 これらの既存のポリシーを Microsoft Edge にも適用することで、Microsoft Edge で Intune Managed Browser のポリシーを再利用できます。  
2. 環境内のすべての MAM で保護されたアプリで、アプリ保護ポリシーの設定 [その他のアプリでの Web コンテンツの転送を制限する] が [ポリシーで管理されているブラウザー] に設定されているようにします。 
3. MAM で保護されているものすべてのマネージド アプリ構成設定 "com.microsoft.intune.useEdge" を true に設定します。 翌月以降の 1911 のリリースで、ステップ 2 と 3 を簡単に実行できるようになります。[アプリ保護] ポリシーの [データ保護] セクションで [その他のアプリでの Web コンテンツの転送を制限する] の設定に "Microsoft Edge" を含めるだけです。 

iOS および Android での Web クリップのサポートが予定されています。 このサポートがリリースされたら、既存の Web クリップの対象を再設定して、それらが Managed Browser ではなく Microsoft Edge で開くようにする必要があります。 

#### <a name="additional-information"></a>追加情報
詳細については、[Microsoft Edge とアプリ保護ポリシーの使用](../apps/manage-microsoft-edge.md)に関するドキュメント、または[サポートのブログ記事](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269)を参照してください。


### <a name="end-of-support-for-legacy-pc-management"></a>従来の PC 管理のサポート終了

従来の PC 管理は 2020 年 10 月 15 日にサポートが終了します。 デバイスを Windows 10 にアップグレードし、Intune による管理が継続されるようにモバイル デバイス管理 (MDM) デバイスとして再登録してください。

[詳細情報](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Android デバイス管理者のサポートの縮小 
Android デバイス管理者 ("従来の" Android 管理とも呼ばれ、Android 2.2 でリリースされました) は、Android デバイスを管理する方法の 1 つです。 しかし、[Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5.0 でリリース) では、強化された管理機能を使用できるようになりました。 Google では、より豊富で安全な最新のデバイス管理に移行するための努力の一環として、新しい Android リリースでのデバイス管理者のサポートを縮小させています。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Google によるこのような変更により、Intune ユーザーは次のような影響を受けます。  
- Intune では、Android 10 以降を実行している、デバイス管理者が管理する Android デバイスのフル サポートは、2020 年度第 2 四半期までのみ提供できます。 この時以降、Android 10 以降を実行している、デバイス管理者が管理するデバイスは、まったく管理できなくなります。 具体的には、影響を受けるデバイスが新しいパスワード要件を受け取ることはありません。
    - Samsung Knox デバイスは、この時間枠内に影響を受けることはありません。これは、Intune と Knox プラットフォームとの統合によって延長サポートが提供されるためです。 これにより、デバイス管理者の管理の移行を計画する時間を増やすことができます。    
- デバイス管理者が管理する Android デバイスで、Android 10 より前の Android バージョンのままであるものは影響を受けません。デバイス管理者で引き続き完全に管理できます。    
- Google では、Android 10 以降を稼働しているすべてのデバイスに対して、ポータル サイトのようなデバイス管理者の管理エージェントを使ってデバイス識別子の情報にアクセスする機能を制限しています。 この制限により、Android 10 以降にデバイスを更新すると、次の Intune 機能が影響を受けます。  
    - VPN のネットワーク アクセス制御が機能しなくなる。   
    - IMEI またはシリアル番号を使用した企業所有のデバイスの識別で、デバイスが企業所有として自動的にマークされなくなる。  
    - Intune で IT 管理者に IMEI とシリアル番号が表示されなくなる。 
        > [!NOTE]
        > これが影響を与えるのは、デバイス管理者が管理するデバイスで Android 10 以降のもののみです。Android Enterprise として管理されているデバイスには影響しません。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
2020 年度第 3 四半期に予定されている機能の縮小を回避するために、次のことをお勧めします。
- 新しいデバイスをデバイス管理者の管理にオンボードしない。
- デバイスが Android 10 への更新プログラムを受け取ることが予想される場合は、それをデバイス管理者の管理から外し、Android Enterprise 管理、アプリ保護ポリシーのいずれかまたは両方に移行する。

#### <a name="additional-information"></a>追加情報
- [デバイス管理者から Android Enterprise への移行に関する Google のガイダンス](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [デバイス管理者 API の廃止計画に関する Google のドキュメント](https://developers.google.com/android/work/device-admin-deprecation)

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

詳細については、[こちらのブログ投稿](https://aka.ms/Windows7_Intune)を参照してください。


