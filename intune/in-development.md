---
title: で開発 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune の機能の開発
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756821"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>Microsoft Intune での開発 2019 年 3 月します。

準備が整っているし、計画、このページで支援するために Intune UI の更新プログラムし、機能をリストは、開発中がリリースされていません。 さらに

- 予想、変更する前にアクションを実行する必要があります、無償の Office メッセージ センター投稿を公開しますします。
- 機能がプレビューとして、運用環境で起動するか、一般公開機能の説明はこのページを無効と移動にときに、[は新しいページ](whats-new.md)します。
- このページと[は新しいページ](whats-new.md)定期的に更新されます。 適宜確認してください。
- 参照してください、 [M365 ロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)の戦略的な成果物、およびタイムライン。

> [!Note]
> これらの項目には、将来のリリースで導入される Intune の機能について Microsoft の現在の予測が反映されます。 日付と個々 の機能を変更することがあります。 開発ではすべてのアイテムでは、このページで、機能の説明があります。

**RSS フィード**: ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページの更新時に通知を受け取ることができます。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal での Intune


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>レポートの暗号化  <!-- 2351538 -->
新しいレポートの暗号化を使用して、デバイスの暗号化状態の詳細を表示することができます。 使用可能な詳細には、デバイスの TPM のバージョン、暗号化の準備と状態、エラー レポート、および詳細が含まれます。  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Intune ポータルから BitLocker 回復キーへのアクセスします。  <!-- 2351547  -->
Azure Active Directory (AAD) については、BitLocker キー ID と BitLocker 回復キーの詳細を表示するデバイスで新しいエントリ ポイントを追加いたします。

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>アプリ構成ポリシーのスコープのタグ <!--2371891 -->
またそのスコープのタグを割り当てられたロールを持つユーザーだけが、アプリ構成ポリシーにアクセスできるように、アプリ構成ポリシーにスコープのタグを追加することができます。 アプリ構成ポリシーを対象とするのみまたは同じスコープのタグを割り当てられているアプリに関連付けられています。

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Autopilot プロファイルを [すべてのデバイス] 仮想グループに割り当てる <!--2715522 -->
Autopilot プロファイルを [すべてのデバイス] 仮想グループに割り当てられるようになります。 これを行うには、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment Profiles]\(展開プロファイル\)** の順に選択し、プロファイルを選択し、**[割り当て]**、**[割り当て先]** の順に進み、**[すべてのデバイス]** を選択します。 Autopilot プロファイルについて詳しくは、「[Windows Autopilot を使用して Windows デバイスを登録する](enrollment-autopilot.md)」をご覧ください。

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Windows 一括登録した後、ポータル サイト アプリを使用して、使用可能なアプリをインストールします。 <!-- 2751523  -->
使用して Intune に登録されている Windows デバイス[Windows 一括登録](windows-bulk-enroll.md)(プロビジョニング パッケージ) は、ポータル サイト アプリを使用して、使用可能なアプリをインストールすることになります。 ポータル サイト アプリの詳細については、次を参照してください。 [Windows 10 ポータル サイトを手動で追加](store-apps-company-portal-app.md)と[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)します。

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>IOS アプリ プロビジョニング プロファイルのスコープのタグ <!--2934430 -->
またそのスコープのタグを割り当てられたロールを持つユーザーだけが iOS アプリ プロビジョニング プロファイルにアクセスできるように、iOS アプリ プロビジョニング プロファイルにスコープのタグを追加することができます。 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office 展開ツール (ODT) の Office ProPlus の展開の XML <!-- 3192477  -->
Intune 管理コンソールで、Office Pro Plus のインスタンスを作成するときに、Office 展開ツール (ODT) XML を提供することができます。 既存の Intune の UI オプションは、ニーズを満たしていない場合は、この大きいなカスタマイズ機能、できます。 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Windows 更新プログラムをスキャンからユーザーをブロック    <!-- 3316758    -->
新しい Windows 更新プログラム リングに使用できる設定で Windows 更新プログラムをスキャンからのユーザーがブロックされますを追加しています。 この設定は、ポータル内から使用可能ではありませんが、Intune Graph API を使用して構成することができます。

### <a name="windows-update-notifications-----3316782---"></a>Windows の更新通知  <!-- 3316782 -->
Windows 更新プログラム リングの構成にサポートを追加いたしますので、ユーザーに表示される Windows 更新プログラムの通知を構成することができます。 この設定は、ポータル内から使用可能ではありませんが、Intune Graph API を使用して構成することができます。

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>12 の iOS デバイスのユーザーの登録をポータル サイトへの変更 <!--3448635 -->  
IOS 用ポータル サイト アプリの登録画面と Apple iOS 12.2 でリリースされた MDM 登録の変更とを連携させる手順を更新することです。 更新されたワークフローには、ユーザーに求めるようになりましたが。

- (Safari) を使用して、ポータル サイト web サイトを開き、ポータル サイト アプリに戻る前に管理プロファイルをダウンロードする Safari を許可します。 
- 自分のデバイスに管理プロファイルをインストール、設定アプリを開きます。
- 登録を完了してポータル サイト アプリに戻ります。  

これらの変更を準備する方法の詳細については、次を参照してください。、 [Microsoft Tech Community post](https://techcommunity.microsoft.com/)します。 それまでは、会社のポータルで新しい iOS の登録をサポートするために更新しました」の手順[Intune に iOS デバイスを登録](https://docs.microsoft.com/en-us/intune/ios-enroll)します。 これらのドキュメントの変更は、Apple iOS 12.2 のバージョンのリリース後、ライブになります。 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>テナントの状態 ページの追加のコネクタのサポート <!-- 3617202     -->
など、追加のコネクタの状態情報は、テナントの状態ページ表示*Windows Defender Advanced Threat Protection* (ATP) とその他の Mobile Threat Defense コネクター。

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune は Azure Active Directory の役割の一部へのアクセスのみ読み取り <!-- 3637917 -->
私たちは、Intune は、次の Azure AD ロールへのアクセスのみを読み取る許可します。 Azure AD ロールに付与されるアクセス許可では、Intune のロールベースのアクセス制御 (RBAC) で付与されるアクセス許可より優先されます。

Intune の監査データへのアクセスのみを参照してください。

- コンプライアンス管理者
- コンプライアンス データの管理者

Intune のすべてのデータへのアクセスのみを参照してください。

- セキュリティ管理者
- セキュリティの演算子
- セキュリティ閲覧者
- グローバル リーダー

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>診断設定に簡単にアクセス   <!-- 3804627   -->
新しいオプションを追加しています、**監査ログ**ブレードにすべてを直接開くに使用できる Intune コンソールですべての監査ログ ワークロードで、*診断設定*ページ。

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>作成し、Intune で Android Zebra デバイスでデバイス構成プロファイルを使用 <!-- 3895244  -->
Intune は Android Zebra デバイスの構成をサポートします。 具体的には、することができます。 

- デバイス構成プロファイルを作成し、StageNow によって生成されるモビリティ拡張機能 (MX) プロファイルを使用して Android Zebra デバイスに設定を適用 (**デバイス構成** > **プロファイル** > **プロファイルを作成する** > **Android**プラットフォーム)。

適用先:  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>オンラインでライセンスされたビジネス向け Microsoft Store アプリの展開 <!-- 1672660  -->
オンラインでライセンスされた必要なビジネス向け Microsoft Store アプリをデバイスのコンテキストで割り当てることができます。 このようにして、ビジネス向け Microsoft Store アプリを展開すると、デバイス上のすべてのユーザーにアプリをインストールできます。 対象は Windows 10 RS4 以上のデスクトップ デバイスのみです。 デバイスのコンテキストでインストールするオプションは、MSFB オンラインのライセンスされたアプリのクライアント アプリの割り当てページにあります。

## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。
