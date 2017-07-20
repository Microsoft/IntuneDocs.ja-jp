---
title: "Microsoft Intune で BYOD を有効にする"
description: 
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: vlpetros
ms.suite: ems
ms.openlocfilehash: 880b83a63eefe13a96ab8838c7092c185aa32cd0
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2017
---
# <a name="enable-byod-with-intune"></a>Intune で BYOD を有効にする

このトピックでは、組織で "Bring your own device" (BYOD) ソリューションを有効にするための Intune のセットアップに関する概要ワークフローを示します。 タスクは、3 つのプロセスと方法に関するトピックへのリンクにまとめられています。

ワークフローは、次の 3 つのプロセスに分かれます。 組織の要件に合わせて各プロセスの諸側面を調整できます。

-   「**[デバイスを登録してコンプライアンスを確認する](#enroll-devices-and-check-for-compliance)**」では、ユーザーが個人のデバイスを Intune による管理に登録できるようにする方法について説明します。 Intune は、iOS、macOS、Android、および Windows のデバイスを管理します。 このセクションでは、デバイスにポリシーを展開し、セキュリティの基本要件を満たしていることを確認する方法も説明します。

- 「**[会社のリソースにアクセスできるようにする](#provide-access-to-company-resources)**」では、IT 部門としてユーザーが会社のリソースに簡単かつ安全にアクセスできるようにする方法を説明します。 これを行うには、管理対象デバイスにアクセス プロファイルを展開します。 このセクションでは、Intune でのボリューム購入アプリの展開を管理する方法も説明します。

-   「**[会社のデータを保護する](#protect-company-data)**」では、会社のリソースに対する条件付きアクセスを提供し、データの損失を防ぎ、使わなくなったデバイス、紛失したデバイス、盗まれたデバイスから会社のアプリとデータを削除する方法を説明します。

[![Microsoft Intune で BYOD を有効にするための概要ワークフロー図](./media/workflow-diagram-for-byod.png)](./media/workflow-diagram-for-byod.png)

<!--- > <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup> --->

## <a name="before-you-begin"></a>始める前に
ユーザーがデバイスを登録する前にまず、Intune サービス自体を準備する必要があります。 そのためには、[ライセンスをユーザーに割り当て](licenses-assign.md)て、[モバイル デバイス管理機関を設定](mdm-authority-set.md)します。

その間に、[ポータル サイトをカスタマイズする](company-portal-customize.md)ことも必要です。 会社のブランドを追加し、サポート情報をユーザーに提供します。 これにより、ユーザーのための信頼できる登録およびサポートのエクスペリエンスが作成されます。

## <a name="enroll-devices-and-check-for-compliance"></a>デバイスを登録してコンプライアンスを確認する

Intune サービスを準備した後は、管理するさまざまなデバイス種類のさまざまな登録要件を満たす必要があります。 デバイスを管理対象として登録する手順は簡単ですが、デバイスの種類によって若干の違いがあります。

-   **iOS および Mac デバイス** iPad、iPhone、または macOS デバイスを登録するには、[Apple Push Notification Service (APNs) 証明書を取得する](apple-mdm-push-certificate-get.md)必要があります。 [APNs の証明書を Intune にアップロード](/intune-user-help/enroll-your-device-in-intune-ios)すると、会社のポータルのアプリを使用して [iOS デバイスを登録](/intune-user-help/enroll-your-device-in-intune-macos)したり、会社のポータルの Web サイトを使用して macOS デバイスを登録したりできます。

-   **Android デバイス** Android デバイスは、事前準備の必要なく Intune サービスに登録できます。 ユーザーは、Google Play からポータル サイト アプリを入手して、管理対象として [Android デバイスを登録](/intune-user-help/enroll-your-device-in-intune-android.md)できます。

-   **Windows Phone および PC** Windows デバイスを簡単に登録するには、[登録サーバーに DNS エイリアスを設定](windows-enroll.md#enable-windows-enrollment-without-azure-ad-premium)します。 それ以外の場合、ユーザーは職場または学校のアカウントを追加して [Windows デバイスを登録](/intune-user-help/enroll-your-w10-phone-or-w10-pc-windows)します。

  - Azure AD Premium がある場合は、[自動登録を有効にする](windows-enroll.md)ことで、ユーザーが Windows デバイスをより簡単に登録できるようにすることができます。 ユーザーが個人デバイスを登録するために職場または学校アカウントを追加すると、この機能がデバイスを Intune に自動的に登録します。 また、組織の Azure AD に参加している会社所有デバイスでも機能します。


### <a name="make-sure-that-managed-devices-meet-basic-security-requirements"></a>管理対象のデバイスが基本的なセキュリティ要件を満たしていることを確認する

ユーザーがデバイスを管理対象として登録したら、IT チームは会社のアプリおよびデータへのアクセスに使用されているデバイスが、基本的なセキュリティ要件を満たしていることを確認する必要があります。 これらのルールには、PIN を使用するデバイスへのアクセスと、デバイスに格納されているデータの暗号化に関するものが含まれる場合があります。 このような一連のルールは、[コンプライアンス ポリシー](device-compliance.md)と呼ばれます。

ユーザーに[コンプライアンス ポリシーを展開する](device-compliance-get-started.md)と、Intune で管理されているデバイスはすべて、BYOD ポリシーの一部として定義した基本的なセキュリティ要件を満たしているかどうかについて確認されます。 デバイスのポリシー コンプライアンスの評価が終了すると、その結果が Intune に報告されます。 場合によっては、ユーザーは PIN やデバイスの暗号化などの設定の修正を求められる場合があります。 それ以外の場合、ポータル サイト アプリは単に、ポリシーを満たしていない設定をユーザーに通知します。

## <a name="provide-access-to-company-resources"></a>会社のリソースへのアクセスを提供する

多くの従業員は、自分のモバイル デバイスから、まず会社の電子メールやドキュメントにアクセスしたいと考えます。 また、その際は、複雑な手順を踏んだり、ヘルプ デスクに問い合わせたりすることなく済ませたいと考えます。 Intune では、モバイル デバイスにプレインストールされたネイティブ メール アプリの[メール設定を簡単に作成して展開する](conditional-access-intune-common-ways-use.md)ことができます。
<!--- this was old link: (https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune). check with Andre--->

> [!NOTE]
> Intune では、Google Play ストアにある Gmail および Nine Work 電子メール アプリに対する Android for Work 電子メール プロファイル構成をサポートします。

また、Intune では、オフサイトで働いているユーザーによるオンプレミスの会社データへのアクセスを制御および保護することもできます。 Intune の [Wi-Fi](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune)、[VPN](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune#create-a-vpn-profile)、メールのプロファイルを使うと、ユーザーはどこにいても仕事を遂行するために必要なファイルとリソースにアクセスできます。 Azure Active Directory アプリケーション プロキシと条件付きアクセスを使用して、会社の Web アプリケーションとオンプレミスでホストされるサービスに対しても安全にアクセスして保護することができます。

### <a name="manage-volume-purchased-apps"></a>ボリューム購入アプリを管理する
Intune では、次のことが簡単にできます。
* アプリ ストアからボリューム ライセンス情報をインポートする
* 使ったライセンス数を追跡する
* 所有している以上のアプリのコピーをユーザーがインストールできないようにする
* [ストア アプリを管理対象デバイスに配信する](apps-deploy.md)
* ポータル サイト Web サイトを使ってアプリの対象を管理されていないデバイスにする

Intune では、iOS アプリ ストアとビジネス向け Windows ストアからボリューム購入したアプリを管理して展開することもできます。 これは、ボリューム購入したアプリを追跡するための管理オーバーヘッドを削減するのに役立ちます。

> [!TIP]
> [Azure AD Connect でシングル サインオン (SSO) を構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)ことができます。 SSO を使うと、ユーザーはオンプレミスで使っているドメイン ユーザー名とパスワードでアプリにサインインできます。 また、Azure Active Directory アプリケーション プロキシを使用して、[オンプレミスでホストされている Web アプリにインターネットベースのアクセスを提供](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)できます。

-   [iOS デバイス用のボリューム購入アプリの管理](vpp-apps-ios.md)。 iOS アプリの複数のライセンスを購入するには、[Apple Volume Purchase Program for Business](http://www.apple.com/business/vpp/) を利用します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンを Intune にアップロードする必要があります。 その後、ボリューム購入情報を Intune と同期し、ボリューム購入アプリの使用を追跡することができます。

-   [ビジネス向け Windows ストアから購入したアプリの管理](windows-store-for-business.md)。 [ビジネス向け Windows ストア](https://www.microsoft.com/business-store)では、組織用のアプリを見つけて、個別または大量購入することができます。 Intune にストアを接続することで、Intune ポータルからボリューム購入アプリを管理することができます。

## <a name="protect-company-data"></a>会社のデータを保護する

Intune は、複数のテクノロジ層を介して会社のデータを保護します。 ID 層では、条件付きアクセスがサービスへのアクセスを保護します。 条件付きアクセスは、管理された準拠デバイスのみに、会社リソースへのアクセスを許可します。 クライアント アプリケーション層では、モバイル アプリケーション管理 (MAM) がデータの損失を保護します。  アプリ保護ポリシーは、保護されていないアプリまたは保存場所にデータが移動されるのを防ぎます。 また、これらのポリシーでは、デバイスの紛失または盗難が発生したときに会社のデータをワイプすることもできます。

### <a name="enforce-conditional-access-to-company-resources"></a>会社リソースに対する条件付きアクセスを適用する

コンプライアンス ポリシーと[条件付きアクセス ポリシー](device-compliance.md)を組み合わせて、BYOD ポリシーが要求する基本的なセキュリティ要件をデバイスが満たしているかどうかを確認できます。 デバイスが要件を満たしていない場合、ルールが適用されて、デバイスがポリシーの要件を満たすまでアクセスが拒否されます。 これにより、管理対象でポリシー要件を満たしたデバイスだけが Exchange ([Exchange On-premises](exchange-connector-install.md) または [Exchange Online](conditional-access-exchange-create.md))、SharePoint Online、Skype for Business Online のようなサービスから、会社のデータにアクセスできるようになります。
<!---first link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)
third link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune). check with Andre--->

> [!IMPORTANT]
> コンプライアンスを検証するコンプライアンス ポリシーがないと、条件付きアクセス ポリシーは機能しません。

### <a name="prevent-data-loss-of-company-data-with-application-protection-policies"></a>アプリケーション保護ポリシーで会社のデータの損失を防止する

Intune のアプリケーション保護ポリシーでは、デバイスの登録の有無に関係なくデータへのアクセス方法を選択できます。 この多用途性により、ユーザーが Intune に自分のデバイスを登録していない場合でも会社のデータを保護することができ、ユーザーは会社のデータに安全にアクセスできます。

[Intune のアプリ保護ポリシー](app-protection-policies.md)を使用すると、ユーザーが iOS および Android デバイスでアクセスする会社のデータを保護できます。 これらのアプリレベル ポリシーを使うと、デバイス自体が Intune で管理されていなくても、従業員が会社のデータをどのように使用および共有するかを制御できます。

[Windows 情報保護 (WIP) ポリシー](app-protection-policies-configure-windows-10.md)を使用すれば、管理対象の Windows 10 デバイスにも適用できます。 これらのポリシーは、従業員のエクスペリエンスを妨げることなく動作します。 ネットワーク環境や他のアプリを変更する必要はありません。

### <a name="wipe-company-data-while-leaving-personal-data-intact"></a>個人データを保持しながら会社のデータを削除する

仕事でデバイスを使用しなくなった場合、別の用途に使用することになった場合、または単に紛失してしまった場合、デバイスから会社のアプリやデータを削除する必要があります。 これは、Intune の選択的ワイプまたは完全なワイプ機能を使って行います。 ユーザーは、デバイスが Intune に登録されている場合、Intune ポータル サイトからリモートで個人所有デバイスをワイプすることもできます。

[フル ワイプ](devices-wipe.md)は、デバイスを工場出荷時の既定設定に戻し、ユーザーのデータと設定を削除します。 [選択的ワイプ](devices-wipe.md#selective-wipe)は、デバイスから会社のデータのみを削除し、ユーザーの個人データはそのまま残します。

一度開始されると、デバイスを管理対象から削除する選択的なワイプのプロセスが即座に開始されます。 プロセスが完了すると、会社のすべてのデータは削除され、Intune の管理コンソールからデバイス名は削除されます。 これでデバイスの管理ライフサイクルは終了します。
