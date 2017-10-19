---
title: "Microsoft Intune の新機能"
titlesuffix: Azure portal
description: "Intune Azure Portal の新機能を確認する"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1bc322567505506f63e2eb002fd330fc151bc70d
ms.sourcegitcommit: 6004fe51e3cee6fb34514ed0d56e20587ecafeb4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。

> [!Note]
> これらの機能の多くは、最終的に Configuration Manager とのハイブリッド環境でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を参照してください。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>ポータル サイトでのデバイスのセットアップ ワークフローの機能強化<!--1490692-->
Android 用のポータル サイト アプリでデバイスのセットアップ ワークフローを改良しました。 言語がよりわかりやすく、会社固有のものとなり、可能な範囲で画面をまとめるようにしました。 詳細については、「[アプリ UI の新機能](whats-new-app-ui.md#week-of-october-2-2017)」ページをご覧ください。

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Android デバイスでの連絡先へのアクセス要求に関するガイダンスの改善<!--1484985-->

Android 用ポータル サイト アプリは、連絡先アクセス許可を受け入れるようにエンド ユーザーに求めることがよくあります。 エンド ユーザーがこのアクセスを拒否すると、条件付きアクセス用のアクセス許可を付与するように通知するアプリ内通知が表示されるようになります。 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Android でのセキュリティで保護された起動の修復<!--1490712-->

Android デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできるようになります。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Android Oreo のポータル サイト アプリにエンド ユーザー向けプッシュ通知が追加<!--1475932-->

エンド ユーザーには、Android Oreo のポータル サイト アプリが Intune サービスからのポリシーの取得などのバックグラウンド タスクが実行されているときにそれを示す追加の通知が表示されます。 これにより、ポータル サイトがデバイス上でいつ管理タスクを実行しているかが、エンド ユーザーにとってより分かりやすくなります。 これは、Android Oreo のポータル サイト アプリの[ポータル サイト UI の最適化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)の一環です。 

Android Oreo で有効になっている新しい UI 要素がさらに最適化されています。  エンドユーザーには、ポータル サイトが Intune サービスからのポリシーの取得などのバックグラウンド タスクを実行しているときにそれを示す追加の通知が表示されます。  これにより、ポータル サイトがデバイスで管理タスクをいつ実行しているかがエンド ユーザーにわかりやすくなります。

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>仕事用プロファイルを使った Android 用ポータル サイト アプリの新しい動作 <!---1485783--->

仕事用プロファイルがある Android for Work デバイスを登録すると、仕事用プロファイル内のポータル サイト アプリによって、そのデバイス上での管理タスクが実行されます。 

個人プロファイルで MAM 対応アプリを使っている場合を除き、Android 用ポータル サイト アプリを使用する機会がなくなります。 仕事用プロファイルのエクスペリエンスを向上させるために、Intune では仕事用プロファイルの登録が正常に完了した後、個人用ポータル サイト アプリが自動的に非表示になります。

Android 用ポータル サイト アプリは、[Play ストアでポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) を参照して **[Enable]\(有効化\)** をタップすると、個人プロファイルでいつでも有効にできます。

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 および Windows Phone 8.1 のポータル サイトの維持モードへの移行 <!--1428681-->

2017 年 10 月より、Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリは、維持モードに移行されます。 つまり、当該アプリに加え、登録やコンプライアンスといった既存のシナリオは、これらのプラットフォームで引き続きサポートされます。 当該アプリは、Microsoft Store など、既存のリリース チャネル経由で引き続きダウンロード可能です。 

維持モードになると、当該アプリは、重要なセキュリティ更新プログラムのみを受信するようになります。 当該アプリの更新プログラムや機能が追加でリリースされることはありません。 新機能を使用するには、デバイスを Windows 10 や Windows 10 Mobile に更新することをお勧めします。 

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>サポートされていない Samsung KNOX デバイスの登録をブロックする<!--- 1490695 --->

ポータル サイト アプリでは、サポートされている Samsung KNOX デバイスのみ、登録を試みます。 MDM の登録を妨げる KNOX ライセンス認証エラーの発生を回避するために、登録対象のデバイスが [Samsung によって発行されたデバイス一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)に掲載されている場合にのみ、その登録が試行されます。 Samsung デバイスには、KNOX をサポートするモデル番号を持つものがある一方で、そうでないものもあります。 Samsung デバイスを購入および展開する前に、デバイスの再販業者に KNOX 対応の有無について確認してください。 検証済みのデバイスの完全な一覧については、「[Android and Samsung KNOX Standard policy settings](/intune-classic/android-policy-settings-in-microsoft-intune.md#supported-samsung-knox-standard-devices)」 (Android および Samsung KNOX Standard のポリシー設定) をご覧ください。

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>Android 4.3 以前のサポートの終了<!---1171126, 1326920 --->
Android 用の管理対象アプリとポータル サイト アプリで会社のリソースにアクセスするには、Android 4.4 以降を使用している必要があります。 12 月には、登録されているすべてのデバイスがインベントリから削除され、会社のリソースにアクセスできなくなります。 MDM を使わずにアプリの保護ポリシーを使用している場合、アプリは更新プログラムを受信できなくなり、時間の経過と共にエクスペリエンスの質が低下していきます。

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>登録されているデバイスで確認可能なデバイス情報のエンドユーザーへの通知<!--1165314-->
すべてのポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されます。 これにより、ユーザーは、「[デバイスを登録した場合に会社が確認できる情報](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)」の記事から直接プライバシーの詳細を確認できるようになります。 これは近い将来、すべてのポータル サイト アプリに導入される予定です。 iOS 用については、[9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)に発表しました。 


## <a name="week-of-september-25-2017"></a>2017 年 9 月 25 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="intune-supports-ios-11---1428975--"></a>Intune が iOS 11 をサポート<!--1428975-->
Intune は iOS 11 をサポートします。 これについては、[Intune サポート ブログ](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)ですでに発表しました。

### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0 のサポートの終了 <!---1164477--->
iOS 用の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降を使用している必要があります。 この 9 月までに更新されないデバイスは、ポータル サイトまたはそれらのアプリにアクセスできなくなります。 

### <a name="intune-apps"></a>Intune アプリ

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Windows 10 用ポータル サイト アプリに追加された更新アクション <!--1132468-->

Windows 10 向けのポータル サイト アプリでは、ユーザーがプルして更新するか、デスクトップで F5 キーを押して、アプリのデータを更新できます。

## <a name="week-of-september-11-2017"></a>2017 年 9 月 11 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>確認可能な iOS デバイス情報のエンドユーザーへの通知<!--739894-->

iOS 用ポータル サイト アプリの [デバイスの詳細] 画面に **[Ownership Type]\(所有権の種類\)** が追加されました。 これにより、ユーザーはこのページから直接、Intune のエンド ユーザー ドキュメントにあるプライバシーの詳細を参照できます。この情報は、[バージョン情報] 画面でも確認できます。

#### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>エンドユーザーの Android 用のポータル サイト アプリへのアクセスを登録なしで許可する<!---1169910--->

エンドユーザーは間もなく Android 用のポータル サイト アプリにアクセスするために、デバイスを登録しなくて済むようになります。 アプリの保護ポリシーを使用する組織のエンドユーザーが、ポータル サイト アプリを開いたときに、デバイスの登録を求めるプロンプトが表示されなくなります。 エンドユーザーはデバイスを登録することなく、ポータル サイトからアプリをインストールできるようにもなります。 


#### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 用ポータル サイト アプリの文言をわかりやすいように変更 <!---1396349--->  

Android 用ポータル サイト アプリについて、エンドユーザーが登録しやすくなるよう、テキストを変更して登録プロセスを簡易化しました。 カスタム登録ドキュメントをお持ちの場合は、ドキュメントを更新して新しい画面を反映したいと思われるかもしれません。 サンプル画像は「[Intune とエンドユーザー アプリの UI の更新](whats-new-app-ui.md#week-of-september-11-2017)」のページにあります。

#### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 情報保護許可ポリシーに追加された Windows 10 ポータル サイト アプリ <!-- 677129 -->

Windows 10 ポータル サイト アプリが更新され、Windows 情報保護 (WIP) がサポートされます。 WIP 許可ポリシーにアプリを追加できます。 この変更により、アプリを **[除外対象]** ボックスの一覧に追加する必要がなくなります。


## <a name="week-of-august-21-2017"></a>2017 年 8 月 21 日の週

### <a name="device-enrollment"></a>デバイスの登録
#### <a name="improvements-to-device-overview----1404453---"></a>デバイス機能強化の概要 <!-- 1404453 -->  
デバイス機能強化の概要に、登録済みデバイスが表示されるようになりましたが、Exchange ActiveSync で管理されるデバイスは除外されます。 Exchange ActiveSync デバイスには、登録済みデバイスと同じ管理オプションがありません。 Azure Portal の Intune で、登録済みデバイスの数とプラットフォーム別登録済みデバイスの数を表示するには、**[デバイス]**、**[概要]** の順に進みます。

### <a name="device-management"></a>デバイス管理
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune で収集されるデバイス インベントリの機能強化
<!-- 961134, 1104426, 1281327, 1333543 -->
今回のリリースでは、ユーザーが管理するデバイスで収集されるインベントリ情報が次のように改善されました。
 
-   Android devices デバイスの場合、各デバイスの最新パッチ レベルを示す列をデバイス インベントリに追加できるようになりました。 デバイスの一覧に **[セキュリティ パッチ レベル]** 列を追加し、これを表示します。
-   デバイス ビューにフィルターを適用するとき、登録日付でデバイスを絞り込めるようになりました。 たとえば、指定した日付の後に登録されたデバイスのみを表示できます。
-   **[Last Check-in Date]\(最終チェックイン日付\)** 項目で使用されるフィルターを改善しました。
-   デバイスの一覧で、会社所有デバイスの電話番号を表示できるようになりました。
さらに、フィルター ウィンドウを利用し、電話番号でデバイスを検索できます。
 
デバイス インベントリの詳細については、「[Intune デバイス インベントリを表示する方法](device-inventory.md)」を参照してください。

#### <a name="conditional-access-support-for-macos-devices"></a>macOS デバイスの条件付きアクセスのサポート 
<!-- 720172 -->
Mac デバイスを Intune に登録し、そのデバイス コンプライアンス ポリシーに準拠することを求める条件付きアクセス ポリシーを設定できるようになりました。 たとえば、ユーザーは macOS 用の Intune ポータル サイト アプリをダウンロードして、Mac デバイスを Intune に登録します。 Intune は、暗証番号 (PIN)、暗号化、OS バージョン、およびシステムの整合性などの要件にその Mac デバイスが準拠しているかどうかを評価します。

- macOS デバイスの条件付きアクセスのサポートについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)をご覧ください。

#### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>macOS 用ポータル サイト アプリはパブリック レビュー中です <!---1484796--->
macOS 用ポータル サイト アプリが Enterprise Mobility + Security の条件付きアクセス向けパブリック レビューの一部として利用可能になりました。 このリリースでは macOS 10.11 以降をサポートしています。 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) から入手してください。 


#### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 の新しいデバイスの制限設定    
<!--1063965, 1308850  -->
このリリースでは、次のカテゴリに [Windows 10 デバイス制限プロファイル](/intune/device-restrictions-windows-10)の新しい設定が追加されました。

-   Windows Defender SmartScreen
-   アプリ ストア

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Windows 10 エンドポイント保護デバイス プロファイルの BitLocker 設定の更新
<!--1459533 -->    
今回のリリースでは、Windows 10 エンドポイント保護デバイス プロファイルにおける BitLocker 設定の動作が次のように改善されました。
 
**[BitLocker OS ドライブの設定]** の **[互換性のない TPM チップでの BitLocker]** 設定で **[ブロック]** を選択すると、以前は、BitLocker が実際には許可されていました。 ブロックを選択すると BitLocker がブロックされるように修正されました。
**[BitLocker OS ドライブの設定]** の **[証明書ベースのデータ回復エージェント]** 設定で、証明書ベースのデータ回復エージェントを明示的にブロックできるようになりました。 ただし、既定では、エージェントが許可されます。
**[BitLocker 固定データ ドライブの設定]** の **[データ回復エージェント]** 設定で、データ回復エージェントを明示的にブロックできるようになりました。
詳しくは、「[Microsoft Intune での Windows 10 以降用の Endpoint Protection 設定](endpoint-protection-windows-10.md)」をご覧ください。


### <a name="app-management"></a>アプリ管理
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android ポータル サイト ユーザーおよびアプリ保護ポリシー ユーザーに対する新しいサインイン エクスペリエンス<!-- 621669 -->
エンドユーザーは、Android デバイスを登録しなくても、Android ポータル サイト アプリを使用して、今すぐにアプリを閲覧したり、デバイスを管理したり、IT 連絡先情報を確認したりできます。 また、エンドユーザーが既に Intune App Protection ポリシーによって保護されているアプリを使用しているときに、Android ポータル サイトを起動した場合、エンドユーザーに、デバイスの登録をするプロンプトが表示されなくなりました。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android ポータル サイト アプリのバッテリの最適化を切り替える新しい設定<!--1405990-->
Android ポータル サイト アプリの **[設定]** ページには、ポータル サイトと Microsoft Authenticator アプリのバッテリ最適化をユーザーが簡単にオフにできる新しい設定があります。 この設定で表示されるアプリ名は、どのアプリが職場アカウントを管理しているかによって異なります。 電子メールとデータを同期する職場アプリのパフォーマンスの向上には、バッテリの最適化をオフにすることをお勧めします。 

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>OneNote for iOS の複数 ID のサポート      <!-- 1234281 -->
エンド ユーザーは Microsoft OneNote for iOS で複数のアカウントを利用できるようになりました (職場用と個人用)。 アプリ保護ポリシーを、個人のノートブックに適用することなく、職場のノートブックの企業データに適用できます。 たとえば、職場のノートブックでは情報を検索できるが、職場のノートブックから個人のノートブックに企業データをコピーして貼り付ける行為は禁止するポリシーを適用できます。
 
- Intune で [アプリ保護と複数の ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) をサポートするアプリについての詳細を参照してください。

#### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Samsung KNOX Standard デバイス用のアプリを許可またはブロックするための新しい設定
<!-- 1305423 822899-->  
このリリースでは、次のアプリ一覧を指定できる[デバイスの制限設定](device-restrictions-android.md)が新規に追加されています。
 
- ユーザーがインストールを許可されているアプリ
- ユーザーが実行をブロックされているアプリ
- デバイスのユーザーに非表示となっているアプリ
 
アプリは、URL、パッケージ名、管理対象のアプリ一覧から指定できます。

#### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune からリンクされる新しい Azure AD のアプリ ベースの条件付きアクセス ポリシーの UI
<!-- 1016201 -->
IT 管理者が、Azure AD のワークロードで新しい条件付きアクセス ポリシーの UI を使用してアプリ ベースの条件付きポリシーを設定できるようになりました。 Azure Portal の Intune App Protection セクションにあるアプリ ベースの条件付きアクセス ポリシーは当面そのまま残り、サイド バイ サイドで強制されます。 また、Intune ワークロードから新しい条件付きアクセス ポリシー UI への便利なリンクもあります。

- Azure AD のアプリ ベースの条件付きアクセスについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)をご覧ください。


## <a name="notices"></a>通知

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Intune の IP アドレスの更新<!-- 1175274 -->
[DNS 名と IP アドレスの更新された一覧](/intune/network-bandwidth-use)を、ファイアウォールのプロキシ設定に使用できます。

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Azure Active Directory で条件付きアクセスを使用<!-- 967947 -->
Azure Portal の Azure Active Directory セクションで条件付きアクセスが使用できるようになりました。Office 365 Exchange Online や SharePoint Online などのクラウド アプリのポリシー設定のための、強力かつ柔軟なフレームワークをご利用いただけます。  Intune コンソールの代わりに **[Conditional access in Azure Active Directory]\(Azure Active Directory の条件付きアクセス\)** ブレードを使用して、ポリシーを構成します。 Intune コンソールで作成した既存のポリシーは、Azure Portal で再作成する必要があります。 詳細については、「[Azure AD の条件付きアクセス ポリシーを作成する](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)」をご覧ください。

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Intune クラシック ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール
Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](/intune/role-based-access-control)に関する記事を参照してください。



## <a name="whats-coming"></a>今後の更新情報

#### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>iOS 11 のメール アプリが OAuth をサポート <!---1196951--->
Intune での条件付きアクセスで、OAuth を使用した iOS デバイスのより安全な認証がサポートされます。 これをサポートし、より安全な認証を可能にするため、iOS のポータル サイト アプリに異なるフローが生成されます。 エンドユーザーがメール アプリで新しい Exchange アカウントにサインインしようとすると、Web ビューのプロンプトが表示されます。 Intune に登録すると、ネイティブのメール アプリによる証明書へのアクセスを許可するプロンプトがユーザーに表示されます。 ほとんどのエンドユーザーにはそれ以上の検疫済みメールは表示されません。 既存のメール アカウントは引き続き基本認証プロトコルを使用するため、これに該当するユーザーには検疫済みメールが配信されます。 このエンド ユーザー向けサインイン エクスペリエンスは Office モバイル アプリの場合と似ています。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>ポータル Web サイトの UI の更新 <!--1313244 part 2-->
__おすすめアプリの更新__  
機能を選択したアプリをユーザーが参照できる専用ページをサイトに追加し、ホームページのおすすめセクションでいくつかの UI の修正を行いました。 これらの変更後の外観は、「[アプリ UI の新機能](whats-new-app-ui.md)」ページで確認できます。

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>プラットフォーム サポートのお知らせ: Windows Phone 8.1 のメインストリーム サポートが 2017 年 7 月 11 日に終了
<!-- 1327781 -->
2017 年 7 月 11 日に、Windows Phone 8.1 プラットフォームのメインストリーム サポートは終了しました。 Windows 8.1 PC のサポートには影響ありません。

Intune サービスによって管理されている Windows Phone 8.1 デバイスへの直接的な影響はありません。 登録されているデバイスは引き続き機能し、すべてのポリシー、構成、およびアプリは引き続き正常に動作します。 Intune サービスの Windows Phone 8.1 プラットフォームおよび Windows Phone 8.1 ポータル サイト アプリを対象とする機能強化は行われません。

できるだけ早い機会に、対象となる Windows Phone 8.1 デバイスを Windows 10 Mobile にアップグレードすることをお勧めします。 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS ポータル サイト アプリのサポートの変更  <!-- 1164474  -->
間もなく、iOS 用 Microsoft Intune ポータル サイト アプリが新しいバージョンになり、iOS 9.0 以降を実行しているデバイスのみがサポートされるようになります。 iOS 8 をサポートするバージョンのポータル サイトは、今後、非常に短い時間だけ使用を続けることができます。 ただし、MAM が有効な iOS アプリも使っている場合は、iOS 9.0 以降しかサポートされないので、エンド ユーザーを最新の OS に更新させる必要があります。 

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
具体的な日付は決まっていませんが、計画できるように事前にお知らせします。 ユーザーが iOS 9 以降に更新したことを確認し、ポータル サイト アプリのリリース時にはポータル サイト アプリを更新するようエンドユーザーに要求してください。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
新しい Intune の機能を最大限に活用するには iOS 9.0 以降に更新するようユーザーに推奨します。  新しいバージョンのポータル サイトをインストールして新しい機能を活用するようユーザーに推奨します。

Azure Portal の Intune で [デバイス] の [すべてのデバイス] に移動し、iOS のバージョンでフィルター処理して、現在 iOS 9 より前のオペレーティング システムを使っているデバイスを確認します。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple の要求による Application Transport Security 対応のための更新<!--748318-->
Apple は、Application Transport Security (ATS) の特定の要件を適用すると発表しました。 ATS では、HTTPS 経由で行われるアプリ通信すべてに、より厳格なセキュリティ保護が適用されます。 この変更により、iOS ポータル サイト アプリを使用している Intune ユーザーが影響を受けます。

Microsoft では、新しい ATS 要件を適用する Apple TestFlight プログラムから、iOS 用ポータル サイト アプリのバージョンを入手できるようにしています。 ATS コンプライアンスをテストできるように、このバージョンを試す場合は、お客様の姓名、電子メール アドレス、および会社名を <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> に電子メールで送信してください。 詳細については、[Intune サポートのブログ](https://aka.ms/compportalats)をご覧ください。

### <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
