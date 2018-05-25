---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 62028232e4d6c9ab20a05480811978234ed0a3c1
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>Microsoft Intune の初期エディション - 2018 年 5 月

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている新機能の一覧を提供しています。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 社外ではこの情報を共有しないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

> [!Note]
>Intune に関して以下の機能が現在開発されています。 新しいハイブリッド機能については、[ハイブリッド環境の新機能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)に関するページをご覧ください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GlobalProtect VPN プロファイルのサポート <!-- 1333680 eeready ! -->

今回の更新で、Intune での VPN プロファイルの VPN 接続の種類として、Palo Alto Networks GlobalProtect を選択できるようになりました (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[プロファイルの種類]** > **[VPN]**)。 このリリースでは、次のプラットフォームがサポートされます。 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>デバイスの場所によるコンプライアンスの設定 <!-- 851881 ! -->
状況によっては、ネットワーク接続で定義される特定の場所に、企業リソースへのアクセスを制限することが必要な場合あります。 デバイスの IP アドレスに基づき、コンプライアンス ポリシーを作成できます (**[デバイスのポリシー準拠]** > **[場所]**)。 デバイスが IP 範囲外に移動した場合、デバイスは会社のリソースにアクセスできません。

適用対象: Android デバイス 6.0 以降 (ポータル サイト アプリ更新済み)

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>アプリのインストールのトラブルシューティングの向上 <!-- 928990 -->
Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 アプリ トラブルシューティング機能のパブリック プレビューが提供されています。 各デバイスの下に **[管理対象アプリ]** という新しいノードがあります。 これには、Intune MDM 経由で配布されたアプリが表示されます。 ノード内では、アプリのインストール状態が一覧表示されます。 個々のアプリを選ぶと、その特定のアプリのトラブルシューティング ビューが表示されます。 トラブルシューティング ビューでは、アプリが作成、変更、ターゲット指定、デバイス配布されたときなど、アプリのエンド ツー エンドのライフサイクルが表示されます。 さらに、アプリのインストールが成功しなかった場合は、エラー コードとエラーの原因に関する便利なメッセージが表示されます。 

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>未承認のデバイス ベンダーとモデルに基づくアプリのアクセスのブロック <!-- 1425689 ! -->
Intune の IT 管理者は、Intune App Protection ポリシーによって、Android 製造元や iOS モデルの指定された一覧を適用できます。 IT 管理者は、Android ポリシーの製造元と iOS ポリシーのデバイス モデルのセミコロン区切り一覧を提供できます。 Intune App Protection ポリシーは、Android および iOS 専用です。 この指定されたリストでは 2 つの個別操作を実行できます。
- 指定されていないデバイスでのアプリ アクセスからブロック。
- または、指定されていないデバイスでの企業データの選択的ワイプ。 

ユーザーは、ポリシーによる要件が満たされない場合、対象となるアプリケーションにアクセスすることができません。 設定に基づいて、ユーザーは、ブロックされるか、アプリ内の企業データを選択的にワイプされます。 iOS デバイスのこの機能で、最低バージョンの設定を対象アプリケーションに適用するには、アプリケーション (つまり、 WXP、Outlook、Managed Browser、Yammer) が参加して、Intune APP SDK を統合する必要があります。 この統合は、ローリング方式で行われ、特定のアプリケーション チームによって異なります。 Android でこの機能を利用するには、最新の Intune ポータル サイトが必要です。

エンド ユーザー デバイスの Intune クライアントは、アプリケーション保護ポリシーに対して Intune ブレードで指定されている文字列の単純一致に基づいてアクションを実行します。 これは、デバイスを報告する値に完全に依存します。 そのため、IT 管理者には、意図した動作が正確であることを確認することをお勧めします。 これは、小さなユーザー グループを対象に、さまざまなデバイス製造元とモデルに基づいてこの設定をテストすることによって実現できます。 Microsoft Intune でアプリ保護ポリシーを表示および追加するには、**[Mobile Apps]** > **[アプリ保護ポリシー]** を選びます。 アプリ保護ポリシーについて詳しくは、「[アプリ保護ポリシーとは](app-protection-policy.md)」をご覧ください。

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 デバイスでキオスク モードを有効にする <!-- 1560072 ! -->
Windows 10 デバイスでは、構成プロファイルを作成して、キオスク モードを有効にすることができます (**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** > **[Windows 10]** > **[デバイスの制限]** > **[キオスク]**)。 この更新では、**[キオスク (プレビュー)]** の設定の名前が **[キオスク (古い)]** に変更されています。 **[キオスク (古い)]** は使用を推奨されませんが、7 月の更新までは機能し続けます。 **[キオスク (古い)]** は新しい **[キオスク]** プロファイルの種類に置き換えられ (**[プロファイルの作成]** > **[Windows 10]** > **[キオスク (プレビュー)]**)、Windows 10 RS4 以降でキオスクを構成する設定が含まれます。

Windows 10 以降に適用されます。

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>キオスク モードのビジネス向け Microsoft Store アプリの関連付けられたアプリ ユーザー モデル ID (AUMID) を取得する <!-- 1560077 ! -->
Intune は、ビジネス向け Microsoft Store (WSfB) アプリのアプリ ユーザー モデル ID (AUMID) を取得して、キオスク プロファイルの構成の向上を提供できます。

ビジネス向け Microsoft Store アプリについて詳しくは、「[ビジネス向け Microsoft Store からのアプリの管理](windows-store-for-business.md)」をご覧ください。

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>アプリ保護ポリシーのアクションにアクセスする <!-- 1483510 EEready -->
まもなく、非準拠デバイスを明示的にワイプ、ブロック、または警告するようアプリ保護ポリシーを構成できるようになります。 最新のアクション "*ワイプ*" は、デバイスから会社の企業データを削除します。 ワイプが発生した場合、デバイスのユーザーにはワイプの理由と修復手順の両方が通知されます。 最低 OS バージョンなどの一部の設定については、ブロックとワイプなど、複数のアクションを適用できます。

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Windows デバイスの新しいインベントリ情報 <!-- 1333569 eeready -->

Windows デバイスの場合は、**[ハードウェア]** タブ (**[グループ]** > **[すべてのモバイル デバイス]** > **[デバイス]** > ユーザーのデバイスを選択 > **[プロパティの表示]** > **[ハードウェア]**) で、次のインベントリ情報をデバイスごとに使用できます。
- TPM
- ウイルス対策
- スパイウェア対策
- ファイアウォール
- UAC
- バッテリ
- [ドメイン名]

CSP でこのデータを取得する方法について詳しくは、「[DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp)」で DeviceGuard のエントリをご覧ください。

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune と Microsoft Edge ブラウザー <!-- 1818969 -->
モバイル デバイス (iOS および Android) 向けの Microsoft Edge ブラウザーが、Intune アプリ保護ポリシーをサポートするようになります。 企業の Azure AD アカウントで Edge ブラウザー アプリケーションにサインインしたユーザーは、Intune によって保護されます。 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Autopilot の OOBE を構成するときの新しい言語/リージョンの設定 <!-- 1821766 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルの言語とリージョンを設定する、新しい構成設定を使用できます。

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>デバイス キーボードを構成するための新しい設定 <!-- 1821768 -->
Out of Box Experience (OOBE) の間に、Autopilot プロファイルのキーボードを構成する新しい設定を使用できます。

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer を使用して iOS デバイスと MacOS デバイスの画面を共有する <!-- 1985547 -->
現在、TeamViewer を使用して、[Intune で管理された Android および Windows デバイス](device-profile-android-teamviewer.md)をリモート管理することができますです。

管理者は、TeamViewer に接続し、iOS および macOS デバイスとの画面共有セッションを開始できます。 iPhone、iPad、macOS ユーザーは、他のデスクトップ デバイスまたはモバイル デバイスと画面をライブで共有できます。 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>デバイス プロファイルのグラフィカル ユーザー グラフが戻った <!-- 2160133 -->
デバイス プロファイルのグラフィカルなグラフに表示される数値カウントの向上で (**[デバイス構成]** > **[プロファイル]** > 既存のプロファイルを選択 > **[概要]**)、グラフィカルなユーザー グラフが一時的に削除されました。

この更新では、グラフィカル ユーザー グラフが元に戻り、Azure portal に表示されます。

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>スコープ グループとしてすべてのユーザーとすべてのデバイスを割り当てる <!-- 2196803 -->
スコープ グループ内のすべてのユーザー、すべてのデバイス、およびすべてのユーザーとすべてのデバイスを、割り当てることができるようになります。

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot プロファイルの対象がグループに移動 <!-- 1877935 -->
現在は、AutoPilot のデプロイ プロファイルは選択したデバイスに割り当てることができます。 この機能のリリース後、これらのプロファイルを割り当てるには次のようにします。
- AutoPilot デバイスを含む (Azure AD) グループを作成します
- 目的のプロファイルを Azure AD グループに割り当てます。 AutoPilot プロファイルは、そのグループ内の AutoPilot デバイスに割り当てられるようになります。

### <a name="management-name-field-will-be-editable----1875989---"></a>管理名フィールドが編集可能になる <!-- 1875989 -->
デバイスの **[プロパティ]** ブレードで、管理名フィールドを編集できるようになります。 このフィールドを編集するには、**[デバイス]** > **[すべてのデバイス]** > デバイスを選択 > **[プロパティ]** の順に選びます。 管理名フィールドを使って、デバイスを一意に識別できます。

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>ローカル デバイス セキュリティ オプションの設定への追加 <!-- 1403702 -->
Windows 10 デバイスに対して追加のローカル デバイス セキュリティ オプションの設定を構成することができます。 追加設定を利用できるのは、Microsoft ネットワーク クライアント、Microsoft ネットワーク サーバー、ネットワーク アクセスとセキュリティ、および対話型ログオンなどに関する部分です。 これらの設定は、Windows 10 デバイスの構成ポリシーを作成するときに、[Endpoint Protection] カテゴリに表示されます。

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>ポリシー、アプリ、証明書、およびネットワーク プロファイルのインストールを必要にする <!-- 1553555 -->
管理者は、AutoPilot デバイスのプロビジョニングの間、Intune がポリシー、アプリ、証明書、ネットワーク プロファイルをインストールするまで、エンド ユーザーによる Windows 10 RS4 デスクトップへのアクセスをブロックすることができます。

### <a name="rules-for-removing-devices----1609459---"></a>デバイス削除のルール <!-- 1609459 -->
設定した日数の間チェックインしていないデバイスを自動的に削除する新しい規則を使用できます。 新しいルールを表示するには、**[Intune]** ウィンドウ、**[デバイス]**、**[Device removal rules]\(デバイス削除ルール\)** の順に選択します。

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot デバイスでのコンシューマー アプリおよびエクスペリエンスの禁止<!-- 1621980 -->
Windows 10 Enterprise RS4 Autopilot デバイスへのコンシューマー アプリおよびエクスペリエンスのインストールを禁止することができます。 この機能を表示するには、**[Intune]** > **[デバイスの登録]** > **[Windows の登録]** > **[Windows AutoPilot profiles]\(Windows AutoPilot プロファイル\)** > **[新規作成]** > **[登録設定]** の順に移動します。 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>複数の Exchange Connector のサポート <!-- 2070451 -->

テナントごとの Microsoft Intune Exchange Connector の数が 1 個だけという制限がなくなりました。 Intune は複数の Exchange Connector をサポートするようになるので、複数のオンプレミス Exchange の組織で Intune の条件付きアクセスを設定できます。

Intune のオンプレミス Exchange Connector を使うと、デバイスが Intune に登録されているかどうか、およびデバイスが Intune のデバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、お使いのオンプレミスの Exchange メールボックスに対するデバイス アクセスを管理できます。 コネクタを設定するには、Azure Portal から Intune のオンプレミス Exchange Connector をダウンロードして、Exchange の組織内のサーバーにインストールします。 Microsoft Intune ダッシュ ボードで **[オンプレミス アクセス]** を選択し、**[セットアップ]** で **[Exchange ActiveSync のコネクタ]** を選択します。 Exchange のオンプレミス コネクタをダウンロードし、Exchange の組織内のサーバーにインストールします。 テナントごとに 1 個という Exchange Connector の制限がなくなったので、他に Exchange の組織がある場合は、他の各 Exchange の組織にも同じ手順でコネクタをダウンロードしてインストールできます。

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>iOS 用の新しい Cisco AnyConnect クライアントのサポート <!-- 1333708 -->

iOS 用の Cisco AnyConnect 向けに作成された新しい VPN プロファイルが、Cisco AnyConnect 4.0.7x 以降で動作するようになります。 既存の iOS Cisco AnyConnect VPN プロファイルは **[Cisco Legacy AnyConnect]** と表示されるようになり、現在と同じように Cisco AnyConnect 4.0.5x で引き続き動作します。

> [!NOTE]
> この変更は iOS に対してのみ有効です。Android、Android for Work、macOS の Cisco AnyConnect オプションは、これまでどおり 1 つだけです。

#### <a name="more-information"></a>詳細情報

新しい Cisco AnyConnect アプリと Cisco Legacy AnyConnect アプリは異なるアプリなので、新しいアプリをサポートするには、新しい iOS Cisco AnyConnect VPN プロファイルを作成する必要があります。 環境内の AnyConnect クライアントを管理している場合は、新しい Cisco AnyConnect アプリを展開する必要もあります。 アップグレードを完了するには、Cisco Legacy AnyConnect VPN プロファイルを削除し、Cisco Legacy AnyConnect アプリを除去する必要もあります。

ネットワーク アクセス制御 (NAC) の統合は、新しい AnyConnect クライアントの初期リリースでは機能しません。 Intune の今後のリリースで NAC 統合を提供できるように、Cisco と協力しています。

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 デスクトップ デバイスのすべてのユーザーに対して必要な基幹業務 (LOB) アプリを展開する機能 <!-- 1627835 RS4 -->
お客様は、必要な基幹業務 Windows 10 アプリを展開してデバイス コンテキストにインストールできるようになります。 これにより、デバイスのすべてのユーザーがこれらのアプリを使用できるようになります。 対象は Windows 10 デスクトップ デバイスだけです。

### <a name="company-portal-enrollment-improved----1874230--"></a>会社ポータルの登録の機能強化 <!-- 1874230-->
Windows 10 ビルド 1703 以降の Intune ポータル サイトを使ってデバイスを登録するユーザーは、アプリを離れることなく登録の最初の手順を完了できます。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android 用 Intune ポータル サイト アプリでのヘルプとフィードバックのエクスペリエンスの更新 <!--1631531 -->

Android アプリのベスト プラクティスに合うように、Android 用 Intune ポータル サイト アプリのヘルプとフィードバックのエクスペリエンスが更新されます。 今後数か月かけて Android 用 Intune ポータル サイト アプリが更新され、**[ヘルプとフィードバック]** メニュー項目が **[ヘルプ]** と **[フィードバックの送信]** の異なるメニュー項目に分割されます。 **[ヘルプ]** ページには **[よく寄せられる質問]** セクションと **[メールでサポートに問い合わせる]** ボタンがあり、エンド ユーザーは Microsoft にログをアップロードしたり、会社のサポート部門に問題を説明するメールを送信したりできます。 **[フィードバックの送信]** では Microsoft の標準的なフィードバック送信を利用でき、"気に入った機能"、"気に入らない機能"、"アイデア" を選択できます。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>アプリ保護ポリシー  <!-- 679615 -->
Intune App Protection ポリシーは、既定のグローバル ポリシーを作成し、テナント全体のすべてのユーザーに保護をすばやく適用する機能を提供します。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
