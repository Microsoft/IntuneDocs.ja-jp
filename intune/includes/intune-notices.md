---
title: ファイルを含める
description: ファイルを含める
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fa251a0edd943d566849b138af5cbab0be248a53
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726402"
---
以下の通知では、今後の Intune の変更と機能に備えるために役立つ重要な情報が提供されます。 


### <a name="decreasing-support-for-android-device-administrator"></a>Android デバイス管理者のサポートの縮小 
Android デバイス管理者 ("従来の" Android 管理とも呼ばれ、Android 2.2 でリリースされました) は、Android デバイスを管理する方法の 1 つです。 しかし、[Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (Android 5.0 でリリース) では、強化された管理機能を使用できるようになりました。 Google では、より豊富で安全な最新のデバイス管理に移行するための努力の一環として、新しい Android リリースでのデバイス管理者のサポートを縮小させています。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
Google によるこのような変更により、Intune ユーザーは次のような影響を受けます。 
- Intune では、デバイス管理者が管理する Android デバイスで、Android 10 以降 (Android Q とも呼ばれる) を稼働しているもののサポートを、2020 年夏までのみ提供できます。 これは、Android の次のメジャー バージョンのリリースが予定されている日付です。  
- 2020 年夏以降、デバイス管理者が管理するデバイスで、Android 10 以降を稼働しているものは、完全に管理することはできなくなります。    
- デバイス管理者が管理する Android デバイスで、Android 10 より前の Android バージョンのままであるものは影響を受けません。デバイス管理者で引き続き完全に管理できます。  
- Google では、Android 10 以降のすべてのデバイスに対して、ポータル サイトのようなデバイス管理者の管理エージェントを使ってデバイス識別子の情報にアクセスする機能を制限しています。 これにより、Android 10 以降にデバイスを更新した後、次の Intune 機能が影響を受けます。 
    - VPN のネットワーク アクセス制御が機能しなくなる。  
    - IMEI またはシリアル番号を使用した企業所有のデバイスの識別で、デバイスが企業所有として自動的にマークされなくなる。 
    - Intune で IT 管理者に IMEI とシリアル番号が表示されなくなる。 
        > [!Note]
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
利用統計情報では、5.0.4269.0 よりも前のバージョンのポータル サイトを備えたデバイスがあることが示されています。 このバージョン以上のポータル サイト アプリをインストールしないと、ワイプ、パスワードのリセット、入手可能な必須アプリのインストール、証明書の登録のような、IT プロフェッショナルが開始したデバイス アクションが意図したとおりに機能しない場合があります。 自分のデバイスが Intune の MDM に登録されている場合は、[クライアント アプリ] – [検出されたアプリ] に移動することで、ポータル サイトのバージョンとユーザーを確認できます。 以前のバージョンのポータル サイトを選択すると、どのエンド ユーザーがポータル サイトを更新していないデバイスを持っているのかを確認できます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
更新していない Android デバイスを使っているエンド ユーザーに、Google Play を使ってポータル サイトを更新するよう依頼します。 ユーザーがポータル サイト アプリの自動更新を維持していない場合は、ヘルプ デスクに通知します。 Google の FCM プラットフォームと変更について詳しくは、「追加情報」にあるリンクをご覧ください。

#### <a name="additional-information"></a>追加情報
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Intune に設置された新しい全画面のエクスペリエンス <!--4593669-->
Azure portal では、Intune に対する UI 作成と編集のエクスペリエンスを更新して公開しました。 この新しいエクスペリエンスでは、1 つのブレード内にまとめられたウィザード形式のフォーマットを使用することで、既存のワークフローを簡素化します。 この更新によって、"ブレードが無秩序に増える" ことや、ブレードを詳細にドリルダウンしていくことが求められる作成および編集のフローを回避します。 また、作成のワークフローは、割り当て (アプリ割り当て以外) を含むように更新されます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
portal.azure.com および devicemanagement.microsoft.com の両方で、次の数か月間にわたって全画面のエクスペリエンスが Intune に公開されます。 この UI の更新は、既存のポリシーとプロファイルの機能には影響を及ぼしませんが、少し変更されたワークフローが表示されます。 たとえば、新しいポリシーを作成するときに、いくつかの割り当てをポリシーの作成後に行うのではなく、このフローの一部として設定できます。 コンソールでの新しいエクスペリエンスの外観を示したスクリーンショットは、「追加情報」にあるブログ投稿で確認してください。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
何らかのアクションを行う必要はありませんが、必要に応じて IT プロフェッショナル向けのガイダンスの更新を検討できます。 Microsoft では、Azure portal 上で Intune 内の各種のブレードに対してこのエクスペリエンスが公開され次第、ドキュメントを更新する予定です。

#### <a name="additional-information"></a>追加情報 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>変更の計画:Intune での新しい Windows 更新設定 <!-- 4464404 -->
Intune サービスの 8 月のリリースまたは 1908 以降、[ユーザーに再起動を許可する (再起動猶予期間)] 設定の代わりに構成できる、新しい "期限の設定" が追加されます。 再起動猶予期間の設定は、1909 または 9 月の更新プログラムの UI で無効になり、その後 10 月末にかけてコンソールから完全に削除される予定です。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
ご自身の環境内で Windows 10 デバイスを管理する場合:

- Intune の 8 月の更新プログラムまたは 1908 から、前の再起動猶予期間の設定に加えて新しい期限の設定がコンソールに表示されます。
- この古い設定と新しい設定を両方構成した場合は、期限の設定値によって再起動猶予期間の設定値が上書きされます。
- 1910 更新プログラムのコンソールから、期限の設定によって [ユーザーに再起動を許可する (再起動猶予期間)] オプションが置き換えられます。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
1908 に含まれる期限の設定を必要な値で構成し、その使用を開始してください。 それが完了したら、再起動猶予期間の設定を [未構成] に設定し、これらの設定が 10 月にコンソールから削除されることに備えることができます。

必要に応じて、ご自身のドキュメントや自動化スクリプトを更新します。

Microsoft では最新情報を随時お知らせし、再起動猶予期間の設定を削除する前にメッセージ センターにリマインダーを投稿いたします。

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>変更の計画:Android 用の Intune App SDK およびアプリ保護ポリシーで 10 月に Android 5.0 以降のサポートを開始 <!--4911065 -->
Intune では、10月に Android 5.x (Lollipop) 以降のサポートが開始されます。 ラップされたすべてのアプリを最新の Intune App SDK で更新し、デバイスを更新してください。

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
最新の Intune App SDK でアプリをラップしてください。 また、[最低限の OS バージョンを必要とします (警告のみ)] という条件付き起動を設定して、個人用デバイスを使用しているエンドユーザーにアップグレードするよう通知することもできます。

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune の変更の計画: Windows 7 のサポート終了間近 <!-- 3042987 -->
2018 年 9 月に投稿した MC148476 および 2019 年 3 月の MC176794 で再びお伝えしたとおり、Windows 7 の延長サポートは 2020 年 1 月 14 日に終了いたします。 その時点で、Windows 7 を稼働しているデバイスに対する Intune のサポートは終了します。これにより、より新しいテクノロジのサポートと、優れた新しいエンド ユーザー エクスペリエンスの提供に注力することが可能になります。 当該日付以降は、お使いの Windows 7 PC を保護するための技術的なサポートと自動更新が Intune で利用できなくなります。 もう利用できないサービスやサポートが必要になるシナリオを回避するために、2020 年 1 月より前に Windows 10 に移行することを強くお勧めします。 Windows のサポート ライフサイクルについて詳しくは、[こちら](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)をご覧ください。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
このメッセージは、現在レガシ Intune PC ソフトウェア エージェントを使って Windows 7 PC を管理しているお客様に送信されます。 Windows 7 の延長サポート終了まで 1 年未満となりました。お客様の組織が、できるだけ早く Windows 10 へのアップグレードを開始することを強くお勧めします。 PC 管理機能は Windows 10 オペレーティング システムに直接組み込まれているため、Windows 7 用の Intune ソフトウェア クライアントなどのクライアント エージェントをインストールする必要はもうありません。 Windows 8.1 以降、Microsoft では、Windows PC のプロビジョニング、構成、更新、および管理を行うためにモバイル デバイス管理 (MDM) アーキテクチャが使われています。 Intune の設定が完了した後は、MDM チャネルを通じて [Intune に Windows 10 PC を登録](..\windows-enroll.md)することで、Windows の登録を簡易化できます。 この "エージェントレス" MDM 管理ソリューションを使って Windows 10 PC を管理することをお勧めします。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
お客様の組織で次のアクション プランをすぐに検討することをお勧めします。

- 2020 年 1 月 14 日より前に、一連の Windows 7 の Windows 10 へのアップグレードを計画し、実行する。
- [Windows 10 の展開サポート](https://docs.microsoft.com/windows/deployment/)に関するページを参照し、使用している Windows 7 PC を Windows 10 にアップグレードする方法について詳しく学習する。
- Fast Track を通じて [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) サービスを確認する (Microsoft のアプリケーション互換性に関する約束が支援されます)。
- 既存のレガシ Intune ソフトウェア クライアントのマネージド デバイスを Microsoft 推奨のソリューションに移行し、MDM 管理を使用して Windows 10 を管理する。 すべての新しい Windows 10 PC を、Azure portal で Intune の MDM 管理を使って登録する。
- さらなる情報について、[こちらのブログ投稿](https://aka.ms/Windows7_Intune)を参照する。
