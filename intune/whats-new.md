---
title: "Microsoft Intune の新機能"
titlesuffix: Azure portal
description: "Intune Azure Portal の新機能を確認する"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8434d522423d8c99ce1318b600a63d2b1b4b3aea
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune の新機能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

週ごとにまとめた、Microsoft Intune の新機能をご覧ください。 [今後の変更](#whats-coming)、サービスに関する[重要なお知らせ](#notices)、[過去のリリース](whats-new-archive.md)に関する情報も確認できます。

> [!Note]
> ハイブリッド モバイル デバイス管理 (MDM) での新機能について詳しくは、[ハイブリッドの新機能に関するページ](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)を確認してください。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-january-29-2018"></a>2018 年 1 月 29 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>期限切れトークンと有効期限が近いトークンのアラート<!-- 1639263 -->
有効期限が切れているトークンと、有効期限が近づいているトークンのアラートが概要ページに表示されるようになりました。 1 つのトークンのアラートをクリックすると、そのトークンの詳細ページに移動します。  複数のトークンのアラートをクリックすると、トークンのステータスが表示された全トークンの一覧に移動します。 管理者は、有効期限が来る前にトークンを更新する必要があります。

### <a name="device-management"></a>デバイス管理

#### <a name="remote-erase-command-support----1438084---"></a>リモートの "消去" コマンド サポート <!-- 1438084 -->

管理者は、消去コマンドをリモートで発行できます。

> [!IMPORTANT]
> 消去コマンドは、元に戻すことができないため、使用する際は注意が必要です。

消去コマンドでは、オペレーティング システムを含むすべてのデータが、デバイスから削除されます。 また、そのデバイスも、Intune 管理から削除されます。 ユーザーに対して警告は表示されません。また、コマンドを発行すると、消去は即座に実行されます。

6 桁の回復用 PIN を構成する必要があります。 この PIN を使用すると、消去されたデバイスのロックが解除され、オペレーティング システムの再インストールが開始されます。 PIN は、消去が開始されると、Intune のデバイスの概要ブレードのステータス バーに表示されます。 消去が完了するまでの間、PIN はずっと表示されます。 消去が完了したら、デバイスは Intune 管理から完全に削除されます。 デバイスを復元する人が誰であっても、そのデバイスを使用できるように、回復用 PIN は必ず記録するようにしてください。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program トークンのライセンスの取り消し <!-- 820870 --> 
特定の VPP トークンのすべての iOS Volume Purchasing Program (VPP) アプリのライセンスを取り消すことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program アプリの取り消し  <!-- 820863 -->
1 つ以上の iOS Volume-Purchase Program (VPP) アプリがインストールされた特定のデバイスでは、そのデバイスで関連付けられているデバイス ベース アプリのライセンスを取り消すことができます。 アプリのライセンスを取り消しても、関連する VPP アプリがデバイスからアンインストールされるわけではありません。 VPP アプリをアンインストールするには、割り当てアクションを **[アンインストール]** に変更する必要があります。 詳細については、「[Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法](vpp-apps-ios.md)」をご覧ください。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>組み込み型のアプリを利用し、iOS デバイスまたは Android デバイスに Office 365 モバイル アプリを割り当てる <!-- 1332318 -->
**組み込み**型のアプリであれば、Office 365 アプリを作成し、管理している iOS または Android デバイスに割り当てることが簡単にできます。 これらのアプリには、Word、Excel、PowerPoint、OneDrive などの 0365 アプリがあります。 アプリの種類に特定のアプリを割り当て、アプリ情報構成を編集できます。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>グループに基づくアプリ割り当ての追加と除外<!-- 1406920 -->

アプリの割り当て時、および割り当ての種類の選択後に、含めるグループと、除外するグループを選択できます。

#### <a name="website-learning-mode----1631908---"></a>Web サイトの学習モード <!-- 1631908 -->

Intune では、Windows 情報保護 (WIP) 学習モードの拡張機能が含まれるようになりました。 WIP が有効になっているアプリの情報を表示できるだけでなく、作業データを Web サイトで共有しているデバイスの概要も表示できます。 この情報を使用して、グループおよびユーザーの WIP ポリシーに追加する Web サイトを判断できます。

#### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Android for Work のポータル サイト アプリの承認<!--1797090 -->
Android for Work を使用している組織は、Android 用のポータル サイト アプリを手動で承認して、管理された Google Play ストアから引き続き自動更新を受信できるようにする必要があります。

#### <a name="faceid-on-ios-devices----1807377---"></a>iOS デバイスの FaceID <!-- 1807377 -->
Intune アプリ保護ポリシーは、iOS デバイスの FaceID を制御する設定をサポートするようになりました。 この設定は、FaceID 機能をサポートするデバイス (現在は iPhone X のみ) 用です。 この設定は、現在サポートされている TouchID コントロールとは異なります。 組織は、TouchID コントロールの代替として有効な PIN プロンプトとして FaceID を信頼するかどうかを選択することができます。

### <a name="device-configuration"></a>デバイス構成

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>割り当てを含めたり除外したりしてグループにアプリケーション構成ポリシーを割り当てることができる <!-- 1480316 --> 

含める割り当てと除外する割り当ての組み合わせを使って、ユーザーとデバイスのグループにアプリケーション構成ポリシーを割り当てることができます。 割り当ては、グループのカスタム選択または仮想グループとして選べます。 仮想グループは、**すべてのユーザー**、**すべてのデバイス**、または**すべてのユーザーとすべてのデバイス**を含むことができます。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 エディション アップグレード ポリシーのサポート <!-- 903672(archived), 1119689 -->  
Windows 10 デバイスを Windows 10 Education、Windows 10 Education N、Windows 10 Professional、Windows 10 Professional N、Windows 10 Professional Education、Windows 10 Professional Education N にアップグレードする Windows 10 エディション アップグレード ポリシーを作成できます。Windows 10 エディションのアップグレードについては、「[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)」をご覧ください。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune の条件付きアクセス ポリシーの利用可能場所が Azure Portal のみに<!-- 1737088 1634311 -->

このリリース以降では、[Azure Portal](https://portal.azure.com) の **[Azure Active Directory]** > **[条件付きアクセス]** から条件付きアクセス ポリシーを構成および管理する必要があります。 便宜上、**[Intune]**  >  **[条件付きアクセス]**の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

#### <a name="updates-to-compliance-emails---1637547---"></a>コンプライアンスのメールに対する変更 <!--1637547 -->

コンプライアンス違反のデバイスを報告するメールが送信される際、そのコンプライアンス違反のデバイスの詳細が含まれるようになります。 


## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日の週

### <a name="intune-apps"></a>Intune アプリ

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android デバイスの "解決" アクションの新機能 <!--1583480-->

Android 用ポータル サイト アプリは、[デバイス暗号化の問題](/intune-user-help/encrypt-your-device-android)を解決するために、**[デバイス設定の更新]** の "解決" アクションを拡張しています。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10 用の Intune ポータル サイトで利用できるリモート ロック <!--676506-->
エンドユーザーは、Windows 10 向けポータル サイト アプリから自分のデバイスをリモートでロックできるようになりました。 この機能はエンド ユーザーがアクティブに使用しているローカル デバイスには表示されません。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Windows 10 でポータル サイト アプリのコンプライアンスの問題解決が簡単に<!--676546-->
Windows デバイスを持つエンド ユーザーは、ポータル サイト アプリのコンプライアンス非対応の理由をタップできます。 可能であれば、問題を解決するのに適切な、設定アプリ内の場所がエンド ユーザーに直接表示されます。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日の週

### <a name="device-configuration"></a>デバイス構成

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新しい自動再配置設定 <!-- 1469168 -->
**自動再展開**設定では、管理権限を持つユーザーが、デバイス ロック画面で **CTRL + Win + R** を使用してすべてのユーザー データとユーザー設定を削除できます。 このデバイスは自動的に再構成され、管理対象に再登録されます。 この設定には、[Windows 10] -> [デバイスの制限] -> [全般] -> [自動再展開] でアクセスできます。 詳細については、[Intune での Windows 10 のデバイス制限設定](device-restrictions-windows-10.md#general)に関するページをご覧ください。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Windows 10 エディションのアップグレード ポリシーにおける、その他のソース エディションのサポート<!-- 903672,  1119689 -->
Windows 10 エディションのアップグレード ポリシーを使用して、Windows 10 の他のエディション (Windows 10 Pro、Windows 10 Pro Education、Windows 10 Cloud など) からアップグレードできるようになりました。 以前のリリースでは、サポートされるエディションのアップグレードのパスは、今よりも限定されていました。 詳細については、[Windows 10 エディションのアップグレードを構成する方法](edition-upgrade-configure-windows-10.md)に関するページをご覧ください。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新しい Windows Defender セキュリティ センター (WDSC) デバイス構成プロファイルの設定 <!-- 1335507 -->

Intune の **Windows Defender セキュリティ センター**という名前の Endpoint Protection に、デバイス構成プロファイル設定の新しいセクションが追加されます。 IT 管理者は、Windows Defender セキュリティ センター アプリで、エンドユーザーがどの機能にアクセス可能かを構成できます。 IT 管理者が Windows Defender セキュリティ センター アプリで、ある機能を非表示にすると、ユーザーのデバイスで、その機能に関連するすべての通知が非表示になります。

管理者が Windows Defender セキュリティ センター デバイス構成プロファイル設定で非表示にできる機能は、以下のとおりです。
- ウイルスと脅威の防止
- デバイスのパフォーマンスと正常性
- ファイアウォールとネットワーク保護
- アプリとブラウザー コントロール
- ファミリー オプション

IT 管理者は、ユーザーが受け取る通知をカスタマイズすることもできます。 たとえば、ユーザーが WDSC に表示される機能で生成されたすべての通知を受け取るか、または重要な通知のみを受け取るかを構成できます。 重要度の低い通知には、Windows Defender Antivirus のアクティビティに関する定期的な概要や、スキャン完了時の通知があります。 その他のすべての通知は重要とみなされます。 さらに、通知の内容自体をカスタマイズすることもできます。たとえば、IT 担当の連絡先情報を、ユーザーのデバイスに表示される通知に組み込むなどです。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP の複数コネクタ サポートと PFX 証明書処理 <!-- 1361755 -->

オンプレミス NDES コネクタを使用してデバイスに証明書を配信するお客様は、1 つのテナントに複数のコネクタを構成できるようになりました。

この新しい機能では、次のシナリオがサポートされています。

- **高可用性**

各 NDES コネクタは、Intune から証明書の要求を取得します。  1 つの NDES コネクタがオフラインになっても、その他のコネクタは要求の処理を続行できます。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>カスタム サブジェクト名で AAD_DEVICE_ID 変数が使用可能に<!-- 1468599 -->

Intune で SCEP 証明書プロファイルを作成する際、カスタム サブジェクト名の作成時に AAD_DEVICE_ID 変数を使用できるようになりました。   この SCEP プロファイルを使用して証明書が要求されると、証明書の要求を行っているデバイスの AAD デバイス ID が、この変数に置き換わります。


### <a name="device-management"></a>デバイス管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理 <!-- 1592747 -->
Jamf を使って、macOS デバイスの状態情報を Intune に送信できるようになりました。情報はその後、Intune コンソールで定義されたポリシーに準拠しているかどうかが評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。 [Jamf 統合の設定](conditional-access-integrate-jamf.md)と [Jamf で管理されたデバイスのコンプライアンスの強制](conditional-access-assign-jamf.md)について、詳細をご覧ください。

#### <a name="new-ios-device-action------1424701---"></a>新しい iOS デバイス アクション <!-- 1424701 -->

iOS 10.3 監視下のデバイスをシャット ダウンできるようになりました。 このアクションでは、エンド ユーザーへの警告なしにデバイスが即時シャットダウンされます。 **シャット ダウン (監視モードのみ)** アクションは、**デバイス** ワークロードでデバイスを選択した場合に、デバイス プロパティに表示されます。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Samsung KNOX デバイスへの日付および時刻の変更禁止 <!-- 1468103 -->

Samsung KNOX デバイスでの日付と時刻の変更をブロックできる機能が新たに追加されました。 この機能は、**[デバイス構成プロファイル]** > **[デバイスの制限 (Android)]** > **[全般]** にあります。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>サポートされる Surface Hub リソース アカウント <!-- 1566442  -->

Surface Hub に関連付けられたリソース アカウントを、管理者が定義、更新できる新しいデバイス アクションが追加されました。

このリソース アカウントは、Skype または Exchange でミーティングに参加できるように認証する場合に Surface Hub で使用されます。 Surface Hub がミーティングで会議室として表示されるように、一意のリソース アカウントを作成できます。 たとえば、リソース アカウントは*会議室 B41/6233* と表示されます。 Surface Hub のリソース アカウント (デバイス アカウントと呼ばれる) は通常、会議室の場所や、他のリソース アカウントのパラメーターをいつ変更するかを構成するのに必要となります。

管理者はデバイスでリソース アカウントを更新する場合、デバイスに関連付けられた現在の Active Directory または Azure Active Directory 資格情報を指定する必要があります。 デバイスでパスワードのローテーションがオンに設定されている場合には、管理者は Azure Active Directory に移動してパスワードを検索する必要があります。

> [!NOTE]
> すべてのフィールドがまとめて送信され、以前に構成されたすべてのフィールドを上書きします。 また、空のフィールドも既存のフィールドを上書きします。

管理者が行える構成は次のとおりです。

- **リソース アカウント**
   - **Active Directory ユーザー**

      Domainname\username、またはユーザー プリンシパル名: user@domainname.com

   - **パスワード**

- **オプションのリソース アカウント パラメーター** (指定されたリソース アカウントを使用して設定する必要があります)

   - **パスワードのローテーション期間**

     アカウントのパスワードは、セキュリティ上の理由から、毎週 Surface Hub によって自動的に更新されます。 これを有効にした後にパラメーターを構成するには、最初に Azure Active Directory のアカウントのパスワードをリセットする必要があります。

   - **SIP (セッション開始プロトコル) アドレス**

     自動検出が失敗した場合にのみ使用されます。

   - **電子メール**

     デバイス アカウントまたはリソース アカウントの電子メール アドレス。

   - **Exchange サーバー**

     自動検出が失敗した場合のみ必要です。

   - **予定表の同期**

     予定表の同期と他の Exchange サーバー サービスが有効かどうかを指定します。 たとえば、ミーティングの同期などです。

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>macOS デバイスでの Office アプリのインストール <!-- 1494311 -->
macOS デバイスで Office アプリをインストールできるようになりました。 この新しい種類のアプリでは、Word、Excel、PowerPoint、Outlook、OneNote をインストールできます。 これらのアプリには Microsoft AutoUpdate (MAU) も付属しており、アプリを安全かつ最新に保つことができます。

### <a name="app-management"></a>アプリ管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>iOS Volume Purchasing Program トークンのライセンスの削除 <!-- 820879 -->
コンソールを使用して、iOS Volume Purchasing Program (VPP) トークンを削除できます。 VPP トークンのインスタンスが重複している場合に、これが必要になることがあります。

### <a name="intune-apps"></a>Intune アプリ

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>アカウントに関するエンド ユーザーへのメッセージング<!--1573558 for 1712-->

ポータル サイトの Web サイト ユーザーによる、テナントへの書き込みアクセスを必要とする操作はブロックされます。 対象ユーザーには、使用アカウントがメンテナンス中であることを示すエラー メッセージが表示されます。 Android、iOS、macOS、Windows 向けのポータル サイト アプリにも、同様の変更がまもなく適用されます。 詳細については、[アプリの UI の新機能](whats-new-app-ui.md)に関するページをご覧ください。



### <a name="role-based-access-control"></a>ロールベースのアクセス制御

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>現在のユーザーという名前の新しいエンティティ コレクションは、現在アクティブなユーザー データに限られています <!-- 1667026 -->

**ユーザー** エンティティ コレクションには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態はデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

これに対し、新しい**現在のユーザー** エンティティ コレクションには、削除されていないユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションには、現在アクティブなユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションの詳細については、「[現在のユーザー エンティティのリファレンス](reports-ref-current-user.md)」をご覧ください。


### <a name="updated-graph-apis----1736360---"></a>Graph API の変更 <!-- 1736360 -->

このリリースでは、Intune のベータ版の Graph API にいくつか変更を加えました。 詳細については、[Graph API の変更ログ](https://developer.microsoft.com/graph/docs/concepts/changelog)のページ (毎月更新) をご覧ください。


## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日の週

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune では Windows Information Protection (WIP) で拒否されたアプリがサポートされる<!-- 1479103 -->
拒否されたアプリを Intune で指定することができます。 アプリが拒否された場合、企業の情報へのアクセスがブロックされます。これは事実上、許可されたアプリ リストの反対です。 詳しくは、[Windows 情報保護の推奨される拒否リスト](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)を参照してください。


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日の週

### <a name="device-enrollment"></a>デバイスの登録

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>登録に関する問題をトラブルシューティングする <!-- 746324 -->

**トラブルシューティング** ワークスペースに、ユーザーの登録に関する問題が表示されるようになりました。 問題に関する詳細と推奨される修復手順は、管理者およびヘルプ デスクのオペレーターが問題をトラブルシューティングするのに役立ちます。 登録に関する特定の問題はキャプチャされず、一部のエラーには推奨される修復方法がない場合があります。

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>グループ割り当て登録制限 <!-- 747598 -->

Intune 管理者は[ユーザー グループに対してカスタムの登録制限として [デバイスの種類] と [デバイスの上限数] を作成できるようになりました](enrollment-restrictions-set.md)。

Intune Azure Portal で、制限タイプごとに最大 25 個のインスタンスを作成できます。作成したインスタンスはユーザー グループに割り当てることができます。 グループに割り当てられた制限は既定の制限をオーバーライドします。

制限タイプのすべてのインスタンスは、厳密に順序付けられた一覧で保守管理されます。 この順序により、競合解決の優先度の値が決まります。 複数の制限インスタンスの影響を受けるユーザーは、優先度の値が最も高いインスタンスによって制限されます。 インスタンスの優先度は、一覧内の別の位置にドラッグすることによって変更できます。

Android For Work 登録メニューから登録制限メニューに Android For Work 設定が移行されたとき、この機能が使えるようになります。 この移行には数日かかる場合があります。11 月リリースのその他の部分に関してアカウントがアップグレードされた後に、登録制限のグループ割り当てが有効になる場合があります。

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>複数のネットワーク デバイス登録サービス (NDES) コネクタのサポート <!-- 1528104 -->

NDES を利用すれば、ドメイン資格情報なしでモバイル デバイスを実行し、Simple Certificate Enrollment Protocol (SCEP) に基づいて証明書を取得できます。
今回の更新で、複数の NDES コネクタがサポートされるようになりました。

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 EEready-->

**注**: 以下の変更は 11 月の更新をもってロールアウトが開始されます。ただし、自分のアカウントでは実行に時間がかかることがあります。 変更が自分のアカウントに適用されると、Office 365 ポータルで確認通知が届きます。 ロールアウト後、管理機能の追加のオプションを使用できるようになります。 ロールアウト中、エンド ユーザーのエクスペリエンスに対する変更はありません。

Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、 > **[Android for Work への登録]**、 > **[Android for Work の登録設定]** でした。)

既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。

個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。

新しい設定を使用する場合、次の点を考慮してください。

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない

新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした

以前にオンボードしている場合、状況は選んだ設定によって変わります。

| Setting | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可済み | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |

いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

### <a name="app-management"></a>アプリ管理

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>インストール保留中の状態を含むように更新されたアプリ インストール レポート<!-- 1249446 -->  

**[モバイル アプリ]** ワークロードの **[アプリ]** 一覧から表示できるアプリ別の **[アプリ インストールの状態]** レポートが、ユーザーとデバイスについて **[インストール保留中]** カウントを表示するようになりました。

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>モバイルの脅威を検出するための iOS 11 アプリ インベントリ API <!-- 1391759 -->

Intune は個人のデバイスと会社所有のデバイスの両方からアプリ インベントリ情報を収集し、Lookout for Work など、MTD (Mobile Threat Detection/モバイル脅威検出) プロバイダーが取得できるようにします。 iOS 11 以降のデバイスを所有するユーザーからアプリ インベントリを収集できます。

**アプリ インベントリ**  
iOS 11 以降を内蔵した会社所有デバイスと個人所有デバイスの両方からのインベントリが MTD サービス プロバイダーに送信されます。 アプリ インベントリのデータ:

 - アプリ ID
 - アプリ バージョン
 - アプリ バージョン (短い形式)
 - アプリ名
 - アプリ バンドル サイズ
 - アプリの動的サイズ
 - アプリの有効性が確認されているかどうか
 - アプリが管理されているかどうか


### <a name="device-management"></a>デバイス管理

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する<!-- 1463747 wnready -->
ハイブリッド MDM から Azure Portal 内の Intune にユーザーとそのデバイスを移動するために、新しいプロセスとツールを用意しました。これにより、次の操作を行うことができます。
- Configuration Manager コンソールから Azure Portal 内の Intune にポリシーとプロファイルをコピーする
- ユーザーのサブセットを Azure Portal 内の Intune に移動し、残りのユーザーをハイブリッド MDM で保持したままにする
- 再登録せずに、Azure Portal 内の Intune にデバイスを移行する

詳しくは、「[ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)」を参照してください。

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>オンプレミスの Exchange Connector の高可用性のサポート  <!-- 676614 -->
Exchange Connector によって、指定の CAS で Exchange への接続が作成された後、コネクタで別の CAS も検出できるようになりました。 メインの CAS が利用できなくなった場合、再度利用可能になるまで、コネクタが別の CAS (ある場合) にフェールオーバーします。 詳細については、「[オンプレミスの Exchange Connector の高可用性のサポート](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)」をご覧ください。

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS デバイスをリモート再起動する (監視モードのみ) <!-- 1424595 -->

デバイス アクションを利用し、監視されている iOS 10.3 以降のデバイスの再起動をトリガーできるようになりました。 デバイス再起動アクションの利用方法については、「[Intune でデバイスをリモートで再起動する](device-restart.md)」を参照してください。

> [!Note]
> このコマンドは、監視されているデバイスと**デバイス ロック** アクセス権を要求します。 デバイスがすぐに再起動します。 パスコードでロックされている iOS デバイスが再起動後に Wi-Fi ネットワークに再び参加することはありません。再起動後、サーバーと通信できないことがあります。

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS のシングル サインオン サポート <!-- 1333645 -->  

iOS ユーザーのためにシングル サインオンを使用できます。 シングル サインオン ペイロードのユーザー資格情報を探すようにプログラミングされている iOS アプリは、このペイロード構成更新で機能します。 UPN と Intune デバイス ID を利用し、プリンシパル名と領域を構成することもできます。 詳しくは、「[Configure Intune for iOS device single sign-on](sso-ios.md)」 (iOS 用 Intune のデバイス シングル サインオンを構成する) を参照してください。

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>個人デバイスの "iPhone を探す" を追加 <!--1427287-->
iOS デバイスのアクティベーション ロックがオンになっているかどうかを表示できるようになりました。 この機能は以前、クラシック ポータルの Intune にありました。


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>管理されている macOS デバイスを Intune でリモート ロックする <!-- 1437691 -->

紛失した macOS デバイスをロックできます。6 桁の回復用 PIN を設定できます。 ロックされているとき、別のデバイス アクションが送信されるまで、**デバイス概要**ブレードにその PIN が表示されます。

詳細については、「[管理されたデバイスを Intune でリモートからロックする](device-remote-lock.md)」を参照してください。

#### <a name="new-scep-profile-details-supported----1559808---"></a>サポートされる新しい SCEP プロファイル詳細 <!-- 1559808 -->

Windows、iOS、macOS、Android プラットフォームで SCEP プロファイルを作成するとき、管理者は追加設定を設定できるようになりました。  管理者は、IMEI、シリアル番号、あるいはサブジェクト名の形式の電子メールなど、一般名を設定できます。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>工場出荷時の設定へのリセット中にデータを保持する <!--1588489 -->
Windows 10 バージョン 1709 以降を工場出荷時の設定にリセットすると、新しい機能が使用できるようになります。 工場出荷時の設定へのリセット中、デバイス登録やプロビジョニングされているその他のデータを保持するかどうかを管理者は指定することができます。

工場出荷時の状態にリセットしても、次のデータが維持されます。
- デバイスに関連付けられているユーザー アカウント
- コンピューターの状態 (ドメイン参加、Azure Active Directory に参加)
- MDM 登録
- OEM でインストールされたアプリ (ストア アプリと Win32 アプリ)
- ユーザー プロファイル
- ユーザー プロファイル以外のユーザー データ
- ユーザー自動ログオン

次のデータは保持されません。
- ユーザー ファイル
- ユーザーがインストールしたアプリ (ストア アプリと Win32 アプリ)
- 初期値ではないデバイス設定

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 更新プログラム リング割り当てが表示される <!-- 1621837 -->
**トラブルシューティング**時、表示しているユーザーに関して、Windows 10 更新プログラム リング割り当てを表示することができます。  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender Advanced Threat Protection の報告頻度設定 <!-- 1455974  -->
Windows Defender Advanced Threat Protection (WDATP) サービスを利用するとき、管理者は管理対象デバイスの報告頻度を管理できます。 新しい **[テレメトリの報告頻度を早める]** オプションを利用すると、WDATP はデータを収集し、さらに頻繁にリスクを評価します。 報告の既定値で速度とパフォーマンスが最適化されます。 報告の頻度を増やすことは、リスクの高いデバイスの場合に有益となります。 この設定は **[デバイス構成]** の **[Windows Defender ATP]** プロファイルにあります。

#### <a name="audit-updates----1412961---"></a>監査更新 <!-- 1412961 -->  
Intune の監査機能により、Intune に関連する変更操作が記録されます。  あらゆる作成操作、更新操作、削除操作、リモート タスク操作が記録され、1 年間保存されます。  Azure Portal では、ワークロード別の監査データを過去 30 日分表示できます。データの絞り込みも可能です。  対応する Graph API により、前年に格納された監査データを取得できます。

監査は **[モニター]** グループの下にあります。 ワークロード別に **[監査ログ]** メニュー項目があります。




## <a name="week-of-november-20-2017"></a>2017 年 11 月 20 日の週

### <a name="app-management"></a>アプリ管理

#### <a name="google-play-protect-support-on-android----908720---"></a>Android の Google Play Protect サポート <!-- 908720 -->

Android Oreo のリリースに伴い、セキュリティで保護されたアプリおよび Android イメージをユーザーや組織が実行できる、Google Play Protect という一連のセキュリティ機能が Google より提供されました。 Intune では、SafetyNet リモート構成証明をはじめとした Google Play Protect の各機能をサポートします。 管理者は、Google Play Protect が構成され正常な状態であることが求められるコンプライアンス ポリシー要件を設定できます。
**[SafetyNet デバイスの構成証明]** 設定では、デバイスが正常な状態であり危険にさらされていないことを確認するために、デバイスを Google サービスに接続する必要があります。 管理者は、インストール済みのアプリが Google Play 開発者サービスによって検証されることを必須にする、Android for Work の構成プロファイル設定を設定することもできます。 条件付きアクセスでは、デバイスが Google Play Protect の要件に準拠していない場合に、ユーザーが企業リソースにアクセスできなくなる可能性があります。

- 「[デバイスのコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)」を参照してください。

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>管理対象アプリから許可されるテキスト プロトコル <!-- 1414050  -->

Intune App SDK によって管理されているアプリは、SMS メッセージを送信できます。

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日の週

### <a name="intune-apps"></a>Intune アプリ
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS 用ポータル サイト アプリ提供開始 <!--1541700-->
macOS での Intune ポータル サイトのエクスペリエンスが更新されました。ユーザーが登録済みのすべてのデバイスで必要となるすべての情報とコンプライアンス通知が明確に表示されるように最適化されました。 また、いったん Intune ポータル サイトをデバイスに展開すると、macOS 用 Microsoft 自動更新から更新プログラムが提供されるようになります。 macOS デバイスから Intune ポータル サイトにログインすることで、新しい macOS 用 Intune ポータル サイトをダウンロードできます。

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner が承認済みアプリのモバイル アプリ管理 (MAM) リストの一部に <!-- 1248473 -->
iOS および Android 用の Microsoft Planner アプリが、承認済みアプリのモバイル アプリ管理 (MAM) の一部となりました。 このアプリは、Azure Portal の Intune App Protection ブレードからすべてのテナントに対して構成できます。
- 詳細については、[承認済みアプリの MAM リスト](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS デバイスでのアプリごとの VPN 要件の更新頻度 <!-- 1547061 -->  
管理者が iOS デバイス上のアプリでアプリごとの VPN 要件を削除できるようになりました。影響を受けるデバイスでは、次回の Intune チェックイン後、通常 15 分以内に反映されます。  

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector 用 System Center Operations Manager 管理パックのサポート <!-- 885457 -->
Exchange Connector 用 System Center Operations Manager (SCOM) 管理パックを Exchange Connector のログ解析に利用できるようになります。 これにより、問題のトラブルシューティングが必要な場合に、別の方法でサービスを監視できるようになります。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日の週

### <a name="device-enrollment"></a>デバイスの登録
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 デバイスの共同管理 <!-- 1243445 -->
共同管理は、従来の管理から最新の管理への橋渡しとなるソリューションであり、段階的なアプローチを使って移行する方向を提示します。 基本的に、共同管理は、Windows 10 デバイスを Configuration Manager と Microsoft Intune で同時に管理すると共に、Active Directory (AD) と Azure Active Directory (Azure AD) に同時に参加させることができるソリューションです。  この構成は、一度にすべてを移行できない組織が適切なペースで時間をかけて最新化するパスを提供します。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>OS のバージョンによる Windows 登録の制限 <!-- 245498 -->
Intune 管理者は、デバイス登録に関して、Windows 10 の最小バージョンと最大バージョンを指定できるようになりました。 これらの制限は **[プラットフォーム構成]** ブレードで設定できます。

Intune では、Windows 8.1 の PC とスマートフォンを引き続き登録できます。 ただし、下限と上限を設定できるのは Windows 10 のバージョンだけです。 8.1 デバイスの登録を許可するには、下限を空のままにします。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot の未割り当てデバイスのアラート <!-- 1631236 -->
**[Microsoft Intune]**、**[デバイス登録]**、**[概要]** ページには、Windows AutoPilot の未割り当てデバイスの新しいアラートがあります。 このアラートでは、AutoPilot プログラムからのデバイスで、AutoPilot Deployment プロファイルが割り当てられていないデバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。 詳細については、「[Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する](https://docs.microsoft.com/intune/enrollment-autopilot)」を参照してください。

### <a name="device-management"></a>デバイス管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>デバイス一覧の [更新] ボタン <!-- 1333581 -->
デバイス一覧は自動的に更新されないため、新しい [更新] ボタンを利用し、一覧に表示されるデバイスを更新できます。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec クラウド証明機関 (CA) のサポート <!-- 1333638 -->    
Intune は Symantec クラウド CA をサポートするようになり、Intune Certificate Connector は Symantec クラウド CA から Intune で管理対象デバイスに PKCS 証明書を発行できます。 Microsoft 証明機関 (CA) で Intune Certificate Connector を既に使っている場合は、Intune Certificate Connector の既存の設定を利用して、Symantec CA のサポートを追加できます。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>デバイス インベントリに追加された新しい項目 <!--1404455 -->
このリリースでは、[登録デバイスによって取得されるインベントリ](device-inventory.md)に次の新しい項目を追加しました。

- Wi-Fi MAC アドレス
- 記憶域の合計容量
- 合計空き容量
- MEID
- 通信事業者


### <a name="app-management"></a>アプリ管理
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>デバイスでの最低限の Android セキュリティ パッチによりアプリへのアクセスを設定する <!-- 1278463 -->   
管理者は、管理されたアカウントの管理対象アプリケーションにアクセスするために、デバイスにインストールする必要がある最低限の Android セキュリティ パッチを定義することができます。

> [!Note]  
> この機能は、Google によって Android 6.0 以降のデバイスについてリリースされたセキュリティ パッチだけを制限します。

#### <a name="app-conditional-launch-support----1193313---"></a>アプリの条件付き起動のサポート <!-- 1193313 -->
IT 管理者は、アプリケーションの起動時にモバイル アプリ管理 (MAM) によって数値の PIN ではなくパスコードを強制する要件を、Azure 管理ポータルで設定できるようになりました。 構成した場合、ユーザーは、MAM 対応のアプリケーションにアクセスする前に、要求された時点で、パスコードを設定および使用する必要があります。 パスコードは、少なくとも 1 つの特殊文字または大文字/小文字アルファベットを含む数値 PIN と定義されます。 Intune の今回のリリースでは、この機能を利用できるのは **iOS のみ**です。 Intune は、数値 PIN に同様の方法でパスコードをサポートし、最小の長さを設定して、文字やシーケンスの繰り返しを許可します。 この機能では、対象のアプリケーションにパスコード設定を適用するのではなく、Intune アプリ SDK とこの機能のコードとを統合するために、アプリケーション (WXP、Outlook、Managed Browser、Yammer など) の参加が必要となります。

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>デバイス インストール状態レポートでの基幹業務アプリのバージョン番号 <!-- 1233999 -->
このリリースでは、デバイス インストール状態レポートに、iOS および Android 用基幹業務アプリのバージョン番号が表示されます。 この情報を使って、アプリのトラブルシューティングや、古いバージョンのアプリを実行しているデバイスの検索を行うことができます。


### <a name="device-configuration"></a>デバイス構成
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>管理者は、デバイス構成プロファイルを使ってデバイスでのファイアウォールの設定を構成できるようになる <!-- 951708 -->   
管理者は、デバイスのファイアウォールを有効にすることができ、ドメイン ネットワーク、プライベート ネットワーク、パブリック ネットワークのさまざまなプロトコルを構成することもできます。  これらのファイアウォールの設定は、"Endpoint Protection" プロファイルで確認できます。

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard は、組織での定義に従って、信頼されていない Web サイトからデバイスを保護する <!-- 958257 -->   
管理者は、Windows Information Protection ワークフローまたはデバイス構成の新しい "ネットワーク境界" プロファイルを使って、"信頼できる" サイトまたは "企業" サイトを定義できます。 64 ビット Windows 10 デバイスの信頼されたネットワーク境界内にないすべてのサイトは、Microsoft Edge で表示された場合、代わりに Hyper-V 仮想コンピューター内のブラウザーで開かれます。

Application Guard は、"Endpoint Protection" プロファイル内のデバイス構成プロファイルで確認できます。 デバイス構成プロファイルでは、管理者は、仮想化されたブラウザーとホスト マシンの相互作用、信頼されないサイトと信頼されるサイト、および仮想化されたブラウザーで生成されたファイルの保存を構成することができます。 デバイスで Application Guard を使うには、最初にネットワーク境界を構成する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise の Windows Defender Application Control は、承認されたアプリのみを信頼するモードを提供する <!-- 1031096 -->    
毎日何千もの悪意あるファイルが作成される状況においては、ウイルス対策の署名ベースの検出を使ってマルウェアに対抗するのでは、新しい攻撃を十分に防ぐことができない可能性があります。 Windows 10 Enterprise の Windows Defender Application Control を使うと、ウイルス対策ソフトウェアや他のセキュリティ ソリューションによってブロックされない限りアプリを信頼するモードから、企業によって承認されたアプリのみをオペレーティング システムが信頼するモードにデバイスの構成を変更できます。 Windows Defender Application Control でアプリに信頼を割り当てます。

Intune を使って、アプリケーション制御ポリシーを "監査のみ" モードまたは強制モードに構成できます。 "監査のみ" モードで実行している場合、アプリはブロックされません。 "監査のみ" モードでは、すべてのイベントがローカル クライアント ログに記録されます。 また、Windows コンポーネントと Microsoft Store アプリの実行のみを許可するか、またはインテリジェント セキュリティ グラフで定義されている評判の良いアプリの実行も許可するかを構成することもできます。

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows 10 用の新しい侵入防止機能セットである Window Defender Exploit Guard <!-- 1063615 -->   
Window Defender Exploit Guard は、アプリケーションが悪用される可能性を減らすカスタム規則を含み、マクロとスクリプトの脅威を防止し、評判が低い IP アドレスへのネットワーク接続を自動的にブロックして、ランサムウェアや不明の脅威からデータを保護できます。 Windows Defender Exploit Guard は、次のコンポーネントで構成されます。

- **攻撃の回避 (ASR)** は、マクロ、スクリプト、メールの脅威を防ぐことができる規則を提供します。
- **フォルダー アクセスの制御**は、保護されているフォルダーのコンテンツへのアクセスを自動的にブロックします。
- **ネットワーク フィルター**は、アプリから評判の悪い IP/ドメインへの発信接続をブロックします。
- **Exploit Protection** は、アプリケーションを悪用から保護するために使うことができるメモリ、制御フロー、およびポリシーの制限を提供します。


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Windows 10 デバイスの Intune で PowerShell スクリプトを管理する <!-- 790537 -->

Intune 管理拡張機能を使用すると、Windows 10 デバイスで実行されている Intune で PowerShell スクリプトをアップロードできます。 この拡張機能は Windows 10 モバイル デバイス管理 (MDM) 機能を補完するもので、最新の管理に簡単に移行できます。 詳細については、「[Windows 10 デバイスの Intune で PowerShell スクリプトを管理する](intune-management-extension.md)」を参照してください。

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 の新しいデバイスの制限設定 <!-- 1308850 -->
-    メッセージング (モバイルのみ) - テストまたは MMS のメッセージを無効化します
-    パスワード - FIPS と、認証用の Windows Hello デバイス セカンダリ デバイスの使用を有効にする設定 
-    ディスプレイ - レガシ アプリの GDI スケーリングをオンまたはオフにする設定

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 キオスク モード デバイスの制限 <!-- 1308872 -->   
Windows 10 デバイスのユーザーをキオスク モードに制限することができます。これは、一連の定義済みアプリにユーザーを制限します。  そのためには、Windows 10 デバイス制限プロファイルを作成し、キオスク設定を設定します。

キオスク モードは、**シングル アプリ** (1 つのアプリだけの実行をユーザーに許可) または**マルチ アプリ** (アプリのセットへのアクセスを許可) の 2 つのモードをサポートします。  ユーザー アカウントとデバイス名を定義します。これらにより、サポートされるアプリが決まります。  ユーザーはログイン時に定義済みのアプリに制限されます。  詳細については、「[AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)」を参照してください。 

キオスク モードには以下が必要です。

- Intune が MDM 機関である必要があります。
- アプリは、ターゲット デバイスに既にインストールされている必要があります。
- デバイスは、[適切にプロビジョニングされている](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)必要があります。

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>ネットワーク境界を作成するための新しいデバイス構成プロファイル <!-- 1311967 -->   
**ネットワーク境界**と呼ばれるデバイス構成プロファイルを作成しました。他のデバイス構成プロファイルと同じ場所にあります。 このプロファイルを使用して、会社のもので信頼できると見なす必要があるオンライン リソースを定義します。 Windows Defender Application Guard や Windows Information Protection などの機能をデバイスで使用するには、"*事前*" にデバイスに対してネットワーク境界を定義する必要があります。 デバイスごとにネットワーク境界を 1 つだけ定義することが重要です。

信頼できるエンタープライズ クラウド リソース、IP アドレス範囲、内部プロキシ サーバーを定義できます。 定義したネットワーク境界は、Windows Defender Application Guard や Windows Information Protection 保護などの他の機能で使うことができます。

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender ウイルス対策用の 2 つの追加設定<!-- 1338409 -->  
**ファイル ブロック レベル**

| | |
|---|---|
| 未構成 | **未構成**は、Windows Defender ウイルス対策の既定のブロック レベルを使用し、正当なファイルが検出されるリスクを高めることなく強力な検出を提供します。 |
| 高 | **高**は、強力なレベルの検出を適用します。
| 高 +  | **高 +** は、高いレベルに加えて、クライアントのパフォーマンスに影響を与える可能性がある保護手段を提供します。
| ゼロ トレランス  | **ゼロ トレランス**は、不明な実行可能ファイルをすべてブロックします。 |

まれですが、**高**に設定すると、一部の正当なファイルが検出される可能性があります。
ファイル ブロック レベルは既定の**未構成**に設定することをお勧めします。

**クラウドによるファイル スキャンの時間延長**  

| | |
|--|--|
| 秒数 (0 - 50) | Windows Defender ウイルス対策がクラウドからの結果の待機中にファイルをブロックする最大時間を指定します。 既定値は 10 秒です。ここで指定した延長時間 (最大 50 秒) は、この 10 秒間に追加されます。 ほとんどの場合、スキャンは最大値よりはるかに短い時間で済みます。 時間を延長すると、クラウドは疑わしいファイルを徹底的に調査できます。 この設定を有効にし、少なくとも 20 秒の追加を指定することをお勧めします。 |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 デバイスに追加された Citrix VPN <!-- 1512457 -->  
Windows 10 デバイス用に Citrix VPN を構成できます。 Windows 10 以降用に VPN を構成するときに、**[基本 VPN]** ブレードの *[接続の種類を選びます]* の一覧で、Citrix VPN を選ぶことができます。

> [!Note]
> Citrix の構成は、iOS および Android 用に存在しました。

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi 接続は iOS で事前共有キーに対応 <!-- 1550823 -->
ユーザーは iOS デバイスで WPA/WPA2 Personal 接続に事前共有キー (PSK) を使用するように Wi-Fi プロファイルを構成できます。 これらのプロファイルは、デバイスが Intune に登録されたとき、ユーザーのデバイスにプッシュされます。

プロファイルがデバイスにプッシュされたとき、次の手順はプロファイル構成によって決まります。  自動的に接続するように設定されている場合、ネットワークが次に必要になったとき、自動的に接続されます。  プロファイルが手動接続になっている場合、ユーザーは接続を手動で開始する必要があります。  

### <a name="intune-apps"></a>Intune アプリ

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>iOS の管理対象アプリ ログにアクセス <!-- 1469920 -->
Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開したあらゆるアプリの管理状態を表示し、管理対象 iOS アプリの問題を解消するためにログを送信できるようになりました。

iOS デバイスの Managed Browser でトラブルシューティング モードを有効にする方法については、「[iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)」を参照してください。

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化<!-- 1417174 -->

iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローを改善しました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 また、セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。 この更新されたワークフローについては、 [アプリ UI ページの新機能](whats-new-app-ui.md)に関するページをご覧ください。

### <a name="monitor-and-troubleshoot"></a>監視とトラブルシューティング

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>ユーザー エンティティにデータ ウェアハウス データ モデルの最新のユーザー データが含まれている<!-- 1544273 -->
Intune データ ウェアハウス データ モデルの最初のバージョンでは、最近の Intune 履歴データのみが含まれていました。 レポートの作成者は、ユーザーの最新の状態をキャプチャできませんでした。 今回の更新プログラムでは、最新のユーザー データを使用して**ユーザー エンティティ**が設定されます。


## <a name="notices"></a>通知

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>変更計画: Microsoft Intune App SDK for Cordova プラグインのサポートでの変更
Intune による [Microsoft Intune App SDK Cordova プラグイン](app-sdk-cordova.md)のサポートは、2018 年 5 月 1 日で終了します。 代わりに Intune アプリ ラッピング ツールを使って、Cordova ベースのアプリの Intune での管理性と可用性の準備をすることをお勧めします。 この変更が有効になると、Microsoft Intune APP SDK for Cordova プラグインは保守されたり更新プログラムを受け取ったりしなくなります。 アプリ開発者はこのプラグインを使えなくなります。 Intune は、Cordova でのアプリ構築のサポートを続ける予定です。 ただし、Microsoft Intune APP SDK for Cordova プラグインを使って作成されたアプリは、Intune での機能が制限されるようになります。 Intune アプリ ラッピング ツールでラップした後は、通常どおりにアプリをエンド ユーザーに展開できます。 Google Play Store にリリースされた Cordova ベースの Android アプリの場合:
- エンド ユーザーは、初めて起動するときに Intune ポリシーを受け取るために資格情報を求められます。
- アプリは、Intune ユーザーが対象のアプリ ストアにリリースされる必要があります ("Contoso App for Intune" など)。 

アプリ ラッピング ツールについては、[iOS 用アプリ ラッピング ツール](app-wrapper-prepare-ios.md)および [Android 用アプリ ラッピング ツール](app-wrapper-prepare-android.md)に関する説明をご覧ください。 問題または質問は、[msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com) にお問い合わせください。 

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>変更の計画: MDM 管理に今すぐ Azure で Intune を使用する <!-- 1227338 -->
1 年以上前、[Azure の Intune のパブリック プレビュー](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)を発表し、その後、6 か月前に Intune の[新しい管理者エクスペリエンスを一般公開](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)しました。 Intune スタンドアロンをご利用の場合、2018 年 4 月 2 日以降、従来の Silverlight コンソールではモバイル デバイス管理 (MDM) を使用できなくなります。 MDM が必要な場合は、代わりに [Azure 上の Intune](https://aka.ms/Intune_on_Azure) を使用できます。 まだ MDM に従来のコンソールを使用している場合は、使用を止め、Azure 上の Intune に慣れてください。 この変更によるエンド ユーザーへの影響はない予定です。 従来の PC 管理は Silverlight に残ります。 この変更とその影響については、[こちら](https://aka.ms/Intune_on_Azure_mdm)を参照してください。


### <a name="plan-for-change-easy-assist-end-of-life----1556480---"></a>予定されている変更: Easy Assist のサービス終了<!-- 1556480 -->
Intune では、PC 管理のリモート アシスタンスに Microsoft Easy Assist を使用しています。 ご存知ないとは思いますが、Microsoft Easy Assist は、2017 年 12 月 31 日にサービスを終了する Office Live Meeting のコンポーネントの 1 つです。 そのため、Intune の Easy Assist サービスも、2017 年 12 月 31 日をもって終了いたします。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android デバイスとは別に Android for Work デバイスを管理する <!-- 1490731 EEready-->    
**注**: 以下の変更は 11 月の更新をもってロールアウトが開始されます。ただし、自分のアカウントでは実行に時間がかかることがあります。 変更が自分のアカウントに適用されると、Office 365 ポータルで確認通知が届きます。 ロールアウト後、管理機能の追加のオプションを使用できるようになります。 ロールアウト中、エンド ユーザーのエクスペリエンスに対する変更はありません。

Intune は、Android プラットフォームに依存することなく、Android for Work デバイスの登録を管理します。 この設定は、**[デバイスの登録]**、 > **[登録制限]**、 > **[デバイスの種類の制限]** で管理されます。 (以前の場所は **[デバイス登録]**、**[Android for Work への登録]**、**[Android for Work の登録設定]** でした。)

既定では、Android for Work デバイス設定は Android デバイスの設定と同じになります。 ただし、Android for Work 設定を変更した後は、同じではなくなります。

個人の Android for Work 登録をブロックした場合、会社の Android デバイスのみを Android for Work として登録できます。

新しい設定を使用する場合、次の点を考慮してください。

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>以前に Android for Work 登録をオンボードしたことがない

新しい Android for Work プラットフォームは、既定の [デバイスの種類の制限] でブロックされます。 この機能をオンボードした後は、デバイスを Android for Work に登録できます。 そのためには、既定値を変更するか、新しい [デバイスの種類の制限] を作成して既定の [デバイスの種類の制限] に代えます。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Android for Work 登録をオンボードした

以前にオンボードしている場合、状況は選んだ設定によって変わります。

| Setting | 既定の [デバイスの種類の制限] の Android for Work の状態 | 注 |
| --- | --- | --- |
| **すべてのデバイスを Android として管理する** | ［ブロック済み］ | すべての Android デバイスを Android for Work なしで登録する必要があります。 |
| **サポートされているデバイスを Android for Work として管理する** | 許可済み | Android for Work 対応のすべての Android デバイスを Android for Work に登録する必要があります。 |
| **これらのグループに所属するユーザーのサポートされているデバイスのみを Android for Work として管理する** | ［ブロック済み］ | 既定値をオーバーライドする別個の [デバイスの種類の制限] ポリシーが作成されました。 このポリシーによって、以前に選択したグループで Android for Work 登録が許可されます。 選択されたグループ内のユーザーには、Android for Work デバイスの登録が引き続き許可されます。 その他すべてのユーザーには、Android for Work の登録が禁止されます。 |

いずれの場合でも、意図した規制が維持されます。 自分の環境で Android for Work のグローバル許可またはグループ別許可を維持するための操作は必要ありません。

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>OS X Mavericks 10.10 と以前のバージョンの macOS のサポートは廃止に <!--1489263, plan for change for 1802-->
2018 年 2 月に OS X Yosemite 10.10 と以前のバージョンの macOS を搭載したデバイスの登録が廃止されることをお知らせします。 Intune は OS X El Capitan 10.11 以降を完全サポートします。

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Graph API での管理対象デバイスに対する新しいパス <!-- 1586728 -->
Graph API のベータ版で管理対象デバイスにアクセスするために使用されるパスが変更されています。 

| | |
|--|--|
| 現在のパス |  https://graph.microsoft.com/beta/managedDevices |
| 新しいパス | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

10 月中は両方のパスを使うことができます。 10 月のサービス リリース後は、新しいパスのみが機能します。  Graph API を使用して管理対象デバイスにアクセスしている場合は、スクリプトとアプリケーションを新しいパスで更新して確認してください。 追加の変更については、毎月の [Graph API 変更ログ](https://developer.microsoft.com/graph/docs/concepts/changelog)でご確認ください。


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 登録シナリオへの直接アクセス <!--951869-->
Intune では、2017 年 1 月以降に作成された Intune アカウントについて、Azure Portal の Enroll Devices ワークロードを使用して、Apple 登録シナリオに直接アクセスできるようになりました。 これまでは、Apple 登録プレビューは Intune クラシック ポータルのリンクからのみアクセスが可能でした。 2017 年 1 月より前に作成された Intune アカウントの場合は、これらの機能が Azure で利用可能になるまでの間、1 回限りの移行が必要です。 移行スケジュールはまだ発表されていませんが、詳細はできる限り早く発表します。 既存のアカウントで Azure Portal にアクセスできない場合は、試用アカウントを作成して、新しいエクスペリエンスをテストすることを強くお勧めします。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure Portal で置き換えられる管理ロール
Intune クラシック ポータル (Silverlight) で使用される既存のモバイル アプリケーション管理 (MAM) の管理ロール (共同作成者、所有者、および読み取り専用) は、Intune Azure Portal の新しいロール ベースの管理制御 (RBAC) の完全なセットで置き換えられます。 Azure Portal に移行すると、管理者をこれらの新しい管理ロールに割り当て直す必要があります。 RBAC と新しいロールの詳細については、[Microsoft Intune のロール ベースのアクセス制御](/intune/role-based-access-control)に関する記事を参照してください。

## <a name="whats-coming"></a>今後の更新情報

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム <!--1412866-->

iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースする予定です。 この更新プログラムは、新しいルック アンド フィール、使いやすさとアクセシビリティの向上を含め、ビジュアル デザインの刷新が特徴です。 現在の iOS ポータル サイト機能はすべて維持されます。

お客様がフィードバックを使用および送信できるように、Apple TestFlight プログラムを使用して iOS 用の更新されたポータル サイト アプリのプレリリース バージョンを提供しています。 TestFlight にアクセスするには、https://aka.ms/intune_ios_cp_testflight にサインアップしてください。

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>Intune の条件付きアクセス ポリシーは、Azure Portal からのみ利用できる<!-- 1737088 -->
Microsoft では、条件付きアクセスを構成および管理する場所を単純化しています。 現在、Intune App Protection (MAM) ブレードと [Microsoft Azure Portal](https://manage.windowsazure.com) のクラシック Azure AD エクスペリエンスから条件付きアクセスを管理できます。 1 月以降は、**[Azure Active Directory]**  >  **[条件付きアクセス]**からのみ [Azure Portal](https://portal.azure.com) のポリシーを構成したり管理したりすることができます。 便宜上、**[Intune]**  >  **[条件付きアクセス]**の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>Intune のデバイス コンプライアンス エンジンを使用した Jamf に登録された macOS デバイスの管理 <!--1592747-->
2018 年初めより、Jamf から Intune に macOS デバイスの状態情報が送信されるようになります。その情報はその後、Intune コンソールで定義されたポリシーへの準拠が評価されます。 条件付きアクセスでは、デバイスのコンプライアンス対応状態や、その他の条件 (場所やユーザー リスクなど) に基づいて、Azure AD に接続されたクラウド アプリケーションやオンプレミス アプリケーション (Office 365 など) にアクセスする macOS デバイスにコンプライアンスを適用します。

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

## <a name="see-also"></a>関連項目
* [Microsoft Intune のブログ](http://go.microsoft.com/fwlink/?LinkID=273882)
* [クラウド プラットフォームのロードマップ](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [ポータル Web サイトの UI の新機能](whats-new-app-ui.md)
* [以前の月の新機能](whats-new-archive.md)
