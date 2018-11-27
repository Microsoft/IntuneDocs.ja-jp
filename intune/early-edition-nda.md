---
title: 初期エディション
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: fbe8cc0fc3e835ee5807dfbe56ea1aa3c728547e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184728"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Microsoft Intune の初期エディション - 2018 年 11 月

> [!Note]
> NDA 通知: Intune に関して、以下の機能が現在開発されています。 この情報は、NDA に基づき、非常に限られた範囲で共有されます。 Twitter、UserVoice、Reddit などの、ソーシャル メディアやパブリック Web サイトには、この情報を投稿しないでください。 

**初期エディション**では、Microsoft Intune の今後のリリースで予定されている、NDA に基づいて共有される新機能のリストを提供します。 ここに記載されている情報は、限られた範囲について開示されたものであり、また今後変更される可能性があります。 ツイート、UserVoice への投稿、またそれ以外の方法で、社外でこの情報を共有したりしないでください。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Microsoft 製品グループにお問い合わせください。

このページは定期的に更新されます。 適宜確認してください。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>企業所有の監視対象 iOS デバイス上のアプリのアンインストール <!-- 1281677 -->
企業所有の監視対象 iOS デバイス上のアプリを削除できるようになります。 **[アンインストール]** 割り当て種類でユーザーまたはデバイスのグループを対象とすることにより、すべてのアプリを削除できます。 個人所有または監視対象外の iOS デバイスの場合は、引き続き Intune を使用してインストールされたアプリのみを削除できます。

### <a name="track-installation-of-office-proplus---2620217--"></a>Office ProPlus のインストールの追跡 <!--2620217-->
[[登録ステータス] ページ](windows-enrollment-status.md)を使用して、[Office ProPlus](apps-add-office365.md) のインストールの進行状況を追跡することができます。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Apple School Manager アカウントに対する macOS Device Enrollment Program のサポート <!--3006133-->
Intune では、macOS デバイスで Apple School Manager アカウントに対する Device Enrollment Program の使用がサポートされるようになります。

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Android デバイスで変更を行うためのキオスク モードの一時停止 <!-- 3041935 -->
IT 管理者は、マルチアプリ キオスク モードで使用している Android デバイスの変更が必要になることがあります。 新しいマルチアプリ キオスクの設定では、IT 管理者は、PIN を使用してキオスク モードを一時的に停止し、デバイス全体にアクセスすることができます。
現在のキオスク設定を確認するには、「[Android キオスクの設定](android-kiosk-settings.md)」をご覧ください。

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Managed Home Screen アプリでのカスタム背景の設定 <!-- 3041945 -->
Android エンタープライズのマルチアプリ キオスク モード デバイス上の Managed Home Screen アプリの背景の外観をカスタマイズできる設定が追加されます。  **カスタム URL の背景**を構成するには、Azure portal で Intune に移動し、[デバイス構成] を選択します。 現在のデバイス構成プロファイルを選択するか、新しいプロファイルを作成してキオスク設定を編集します。

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Android エンタープライズ キオスク デバイスでの仮想ホーム ボタンの有効化 <!-- 3042021 -->
新しい設定により、ユーザーは、デバイスのソフトキー ボタンをタップして、マルチアプリ キオスク デバイスの Managed Home Screen アプリと他の割り当て済みアプリを切り替えることができるようになります。 この設定は、ユーザーのキオスク アプリが戻るボタンに適切に応答しない状況で特に役に立ちます。 この設定は、企業所有の単一ユーザー Android デバイスに対して構成することができます。 **[仮想ホーム ボタン]** を有効または無効にするには、Azure portal で Intune に移動し、[デバイス構成] を選択します。 現在のデバイス構成プロファイルを選択するか、新しいプロファイルを作成してキオスク設定を編集します。

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>アプリ保護ポリシーの割り当ての保存と適用 <!-- 3104570 -->
アプリ保護ポリシーの割り当ての制御が向上します。 アプリ保護ポリシーの割り当てを保存して適用することにより、目的のユーザーに対してのみアプリ保護割り当てポリシーが直接反映されます。

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Windows 10 以降向けの新しい Microsoft Edge ブラウザー設定 <!-- 3174639 -->
デバイス上の Microsoft Edge ブラウザーを制御および管理するための新しい設定が追加されます。 現在の設定の一覧については、「[Intune での Windows 10 (以降) の設定に対するデバイスの制限](device-restrictions-windows-10.md#microsoft-edge-browser)」をご覧ください。

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>[登録ステータス] ページで追跡するアプリの選択 <!-- 2531007 -->
[登録ステータス] ページで追跡するアプリを選択できるようになります。

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Intune アプリ保護ポリシーの UI の更新 <!-- 3251427 -->

Intune アプリ保護ポリシーを使用すると、Microsoft Outlook や Word など、Intune で保護されているアプリに対するさまざまなデータ保護設定を構成できます。 理解しやすいように、設定とボタン ラベルの変更を行っています。 コントロールは**はい**/**いいえ**コントロールから主として**ブロック**/**許可**および**無効**/**有効**コントロールに変更され、ラベルもわかりやすく更新されます。 設定も再フォーマットされ、設定とそのラベルがコントロールに並べて配置されるようになり、ナビゲーションが容易になります。 既定の設定および多くの設定は同じままですが、この変更により、ユーザーは、これまでより簡単に設定を理解し、ナビゲートし、利用して、選択したアプリ保護ポリシーを適用できるようになります。



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>セキュリティ ベースラインに対して Microsoft 推奨の設定を使用する<!-- 2055484 -->
Intune は、セキュリティに的を絞ったその他のサービス (Windows Defender ATP や Office 365 ATP など) と統合されます。 一般的な戦略と、Microsoft 365 サービス間での結束的なエンドツーエンドのセキュリティ ワークフローをお客様から求められています。 目標としているのは、セキュリティの運用と一般的な管理者タスクをブリッジするソリューションを構築できるように戦略を調整することにあります。 Intune では、Microsoft が推奨する一連の "セキュリティ ベースライン" を公開することによって、この目標の達成を目指しています (**[Intune]** > **セキュリティ ベースライン**)。  管理者はこれらのベースラインからセキュリティ ポリシーを直接作成し、それをユーザーに展開することができるようになります。 それらのユーザーは、組織のニーズに合わせてベスト プラクティスの推奨事項をカスタマイズすることもできます。 Intune では、これらのベースラインにデバイスが準拠した状態に維持されていることが確認され、管理者には準拠した状態にないユーザーまたはデバイスが通知されます。

### <a name="scope-tags-for-apps---1081941---"></a>アプリのスコープ タグ <!--1081941 -->
Intune リソースへのアクセスを制限する目的で、スコープ タグを作成できるようになります。 スコープ タグをロールの割り当てに追加し、同じスコープ タグを構成プロファイルに追加します。 そのロールでは、スコープ タグが一致する (あるいはスコープ タグがない) 構成プロファイルを持つリソースにのみアクセスできます。
スコープ タグを作成するには、**[Intune ロール]**、**[スコープ (タグ)]**、**[作成]** の順に選択します。
スコープ タグをロールの割り当てに追加するには、**[Intune ロール]**、**[すべてのロール]**、**[ポリシーおよびプロファイル マネージャー]**、**[割り当て]**、**[スコープ (タグ)]** の順に選択します。
スコープ タグを構成プロファイルに追加するには、**[デバイス構成]**、**[プロファイル]** の順に選択し、プロファイルを選択して **[プロパティ]**、**[スコープ (タグ)]** の順に選択します。

### <a name="tenant-health-dashboard----1124854---"></a>テナントの正常性ダッシュボード<!-- 1124854 -->
Intune の [テナントの状態] ページでは、テナントの状態に関する情報が 1 か所に表示されます。 このページは、次の 4 つのセクションに分かれています。  
- **テナントの詳細**: ご利用の MDM 機関、ご利用のテナントに登録されたデバイスの総数、ご利用のライセンス数などの情報が含まれています。 このセクションには、そのテナントに対する現在のサービス リリースも示されます。
- **コネクタの状態**: Apple VPP、ビジネス向け Windows ストア、証明書コネクタなど、構成されているコネクタに関する情報が含まれています。 コネクタには、その現在の状態に基づいて、*正常*、*警告*、または*異常*を示すフラグが付けられます。
- **Intune サービスの正常性**: ご利用のテナントでのアクティブなインシデントまたは障害が含まれています。 このセクション内の情報は、Office メッセージ センター ([https://portal.office.com](https://portal.office.com)) から直接取得されます。
- **Intune ニュース**: ご利用のテナントに対するアクティブなメッセージが含まれています。ご利用のテナントに最新の Intune 機能が届いたことを示す通知などがあります。 このセクション内の情報は、Office メッセージ センター ([https://portal.office.com](https://portal.office.com)) から直接取得されます。


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>ユーザー登録なしでの WIP ポリシーの展開 <!-- 1434452 -->
使用している Windows 10 デバイスを登録することを MDM ユーザーに求めることなく、Windows 情報保護 (WIP) ポリシーを展開できるようになります。 この構成により、会社は WIP 構成に基づいて会社のドキュメントを保護することができ、一方、ユーザーは独自の Windows デバイスの管理を維持することができます。 WIP ポリシーを使用してドキュメントが保護されると、Intune 管理者は保護されたデータを選択的にワイプすることができます。 ユーザーとデバイスを選択してワイプ要求を送信することにより、WIP ポリシーを介して保護されたデータはすべて使用できなくなります。 Azure portal 内で Intune から、**[モバイル アプリ]** > **[アプリの選択的ワイプ]** の順に選択します。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Web データ用のアプリ保護ポリシー (APP) 設定 <!-- 2662995 -->
Android デバイスと iOS デバイスの両方での Web コンテンツに対する APP ポリシー設定は、http リンクと https Web リンクの両方の処理、ならびに iOS ユニバーサル リンクおよび Android アプリ リンクを介したデータ転送の処理をより適切に行えるように更新されます。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>別の MDM によって使用される Apple VPP トークン <!-- 1488946 -->
Intune では、Apple のボリューム購入プログラム (VPP) トークンが Intune と別の MDM の両方で使用されている場合、詳細が検出され、表示されます。

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-available-in-compliance-policies----1892471---"></a>iOS および macOS のバージョン番号とビルド番号はコンプライアンス ポリシーにあります<!-- 1892471 -->
**[デバイスのポリシー準拠]** > **[デバイスのポリシー準拠]** に、iOS および macOS のオペレーティング システム バージョンが表示され、コンプライアンス ポリシーで使用できます。 今後の更新で、両方のプラットフォームのビルド番号も構成できるようになります。

セキュリティ更新がリリースされるとき、Apple は通常、バージョン番号を現状のまま残しますが、ビルド番号を更新します。 コンプライアンス ポリシーでビルド番号を使用することで、脆弱性更新がインストールされているかどうかを簡単に確認できます。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[デバイスのポリシー準拠] ダッシュボードのデバイスが廃止に <!-- 1981119 -->
今後の更新で、廃止になっているデバイスが [デバイスのポリシー準拠] ダッシュボードから削除されます。 それにより、コンプライアンス番号が変更されます。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>オンプレミス コネクタの更新プロセスの変更 <!-- 2277554 -->
ユーザーからのフィードバックに基づき、オンプレミス コネクタの更新方法が変更されます。 オンプレミス コネクタの初回インストール後、更新は自動的に行われます。 この変更は新しい PFX Certificate Connector for Microsoft Intune から始まり、その後、その他の種類のオンプレミス コネクタにロールアウトされる予定です。 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager コンプライアンスの確認 <!-- 2192052 -->
今後の更新には、新しい System Center Configuration Manager コンプライアンス設定 (**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** > **[Windows 10]**) が含まれます。 Configuration Manager から Intune コンプライアンスにシグナルが送信されます。 Intune の設定を使用して、すべての Configuration Manager シグナルで "準拠" を返すように要求することができます。

たとえば、すべてのソフトウェア更新プログラムをデバイスにインストールすることを要求します。 Configuration Manager では、この要求は "インストール済み" 状態となります。 デバイス上のプログラムが不明な状態である場合、Intune ではデバイスが非準拠となります。

Windows 10 以降に適用されます

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP トークンの期限が切れているか、ポータル サイトのライセンスが不足している場合のアラート <!-- 2237572 -->
Volume Purchase Program (VPP) を使用して、DEP 登録時にポータル サイトを事前プロビジョニングする場合、Intune では、VPP トークンの有効期限が近づいている場合やポータル サイトのライセンスが不足している場合にアラートが表示されます。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

現在のところ、アクティブな通知はありません。

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。



