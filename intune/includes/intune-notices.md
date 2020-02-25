---
title: ファイルを含める
description: インクルード ファイル
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: f23d81ddb07fcafb198cd725781747b61a3b73ea
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529339"
---
以下の通知では、今後の Intune の変更と機能に備えるために役立つ重要な情報が提供されます。

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Windows 10 Mobile 終了のための Microsoft Intune のサポート<!--3544938-->
Windows 10 Mobile の Microsoft メインストリーム サポートは、2019 年 12 月に終了しました。 このサポートの声明に記載されているように、Windows 10 Mobile のユーザーは、新しいセキュリティ更新プログラム、セキュリティ以外の修正プログラム、無償のサポート オプション、Microsoft からのオンライン技術コンテンツ更新プログラムを受け取ることができなくなります。 Microsoft Intune は、すべてのモバイル OS のサポートに基づいて、2020 年 5 月 11 日に Windows 10 Mobile アプリと Windows 10 Mobile オペレーティング システムの両方のポータル サイトのサポートを終了することになりました。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Windows 10 Mobile のデバイスが組織に展開されている場合、今から 2020 年 5 月 11 日まで、新しいデバイスを登録したり、ポリシーとアプリを追加または削除したり、管理設定を更新したりできます。 5 月 11 日以降は、新しい登録が停止され、最終的に Intune UI から Windows 10 Mobile の管理が削除されます。 デバイスが Intune サービスにチェックインされなくなり、デバイスとポリシーのデータが削除されます。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
Intune レポートをチェックして、影響を受ける可能性のあるデバイスまたはユーザーを確認できます。 **[デバイス]**  >  **[すべてのデバイス]** の順に移動し、OS でフィルター処理します。 さらに列を追加して、Windows 10 Mobile を稼働しているデバイスを持つ組織内のユーザーの特定に役立てることができます。 エンド ユーザーに対して、デバイスのアップグレードや、会社にアクセスするためのデバイスの使用中止を要求してください。



### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>変更の計画: Intune に Android エンタープライズ専用デバイスを登録するときのエクスペリエンスの変更<!--6114580-->
11 月のリリースでは、SCEP 証明書の展開のサポートが Android エンタープライズ専用デバイスに追加され、Wi-Fi プロファイルへの証明書ベースのアクセスが可能になりました。 この変更により、Android エンタープライズ専用デバイスの登録フローの一部がマイナー変更されました。 今後の 3 月のサービス更新または 2003 では、注意が必要なさらなる変更がいくつか行われます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
環境内の Android エンタープライズ専用デバイスを管理している場合は、3 月になるといくつかの変更のロールアウトを確認できるようになります。
- 2019 年 11 月 22 日または 1911 サービス更新よりも前に登録された既存の Android 専用デバイスの場合:これらのデバイスには、Microsoft Intune アプリがインストールされます。 3 月に Intune サービスにバックエンドの変更がロールアウトされると、デバイスに展開され Wi-Fi プロファイルに関連付けられている SCEP 証明書の適用が開始されます。
- 2019 年 11 月 22 日以降、3 月のこの変更のロールアウト以前に登録されたデバイスの場合:これらのデバイスには、Microsoft Intune アプリがインストールされます。 デバイスに展開され Wi-Fi プロファイルに関連付けられている SCEP 証明書は、引き続き適用されます。
- 3 月に変更がロールアウトされた後に新しい Android エンタープライズ専用デバイスを登録する場合:登録時にデバイスでエンド ユーザーに表示される一連の手順が異なります。 登録の開始方法は現在と同じですが (QR、NFC、ゼロタッチ、またはデバイス識別子を使用)、必須アプリのインストール手順はなくなります。 代わりに、Microsoft Intune アプリによってデバイス上に自動的にインストールされます。 さらに、エンド ユーザーがフロー中に "Intune エージェントを有効にする" をタップする必要がなくなります。 Wi-Fi プロファイルに関連付けられている SCEP 証明書を、これらのデバイスに展開できます。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
エンド ユーザー ガイドを更新し、ヘルプデスクにこの変更を周知させることができます。 この変更のロールアウトが開始されたら、私たちは新機能ページを更新し、メッセージ センターを通じてユーザーに通知します。

#### <a name="additional-information"></a>追加情報
[Android エンタープライズ専用デバイスでの SCEP 証明書のサポート](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>'Adobe Acrobat Reader for Intune' モバイル アプリのサポート ステートメントが更新されました<!--5746776-->
8 月の終わりに、MC188653 で、Adobe Acrobat Reader for Intune モバイル アプリが 2019 年 12 月 1 日に有効期限終了になり、Adobe が同社のメインの Acrobat Reader アプリ内で Intune のアプリ保護ポリシーのサポートを計画していることをお知らせしました。 その後、お客様から、IT 管理者が引き続きターゲットを指定して、エンド ユーザーが Adobe Acrobat Reader for Intune の使用を開始できるようにするために、もっと時間を提供してもらう必要があるというフィードバックを受け取りました。 エンド ユーザーのデバイスで Adobe Acrobat Reader for Intune の使用率が高く、エンタープライズ シナリオでのその重要性を考慮すると、あらゆるエクスペリエンスが、組織のアプリ保護のニーズを満たすようにする必要があります。 

Acrobat Reader モバイル アプリはアプリ保護ポリシーをサポートし、Intune SDK を統合しているため、一般的な Acrobat Reader モバイル アプリをポリシーでターゲット設定することを引き続きお勧めしますが、Adobe Acrobat Reader for Intune アプリは 2020 年 3 月 31 日まで引き続きサポートされます。 

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
このメッセージが表示されるのは、組織内の 1 つ以上のポリシーが Adobe Acrobat Reader for Intune アプリケーションを対象としているか、以前の EOL 通信を受け取った可能性があることを Microsoft のレポートで示しているためです。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
この変更について、エンド ユーザーとヘルプデスクに通知します。 [ポータル サイトのサポート情報機能](../apps/company-portal-app.md#support-information)を使用して、Intune 関連の質問のためのチャネルを確立できます。

#### <a name="additional-information"></a>追加情報
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


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


