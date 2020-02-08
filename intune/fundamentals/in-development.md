---
title: 開発中 - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune の開発中の機能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912635"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>Microsoft Intune 用に開発中 - 2020 年 1 月

お客様の準備と計画をサポートするため、このページでは、開発中でまだリリースされていない Intune UI の更新と機能が一覧表示されます。 このページの情報に加えて: 

- 変更前にお客様による対処が必要であると予測される場合は、Office メッセージ センターに補足の投稿が公開されます。
- 機能の運用が始まると、機能の説明はプレビュー版も一般公開版も、このページから[新機能](whats-new.md)に関するページに移行します。
- このページと[新機能](whats-new.md)に関するページは、定期的に更新されます。 適宜確認してください。
- 戦略的な成果物とタイムラインについては、「[Microsoft 365 のロードマップ](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)」を参照してください。

> [!NOTE]
> このページには、将来のリリースでの Intune の機能に関する現在の予測が反映されています。 日付と個々の機能は変更される可能性があります。 このページは、開発中のすべての機能を説明しているわけではありません。

**RSS フィード**:ご自身のフィード リーダーに次の URL をコピーして貼り付けることで、このページが更新されたときにわかるようになります。`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>アプリ管理

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Windows でポータル サイト アプリの通知を表示する<!-- 1808082  -->
Windows デバイス上のポータル サイト アプリを更新し、アプリケーションが閉じている場合でも、ユーザーにトースト通知を表示します。 更新により、インストール状態が [完了] または [失敗] の場合にのみ、利用可能なアプリの通知が表示されます。 ポータル サイト アプリには、必要なアプリケーションの通知は表示されません。 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>ポータル サイト アプリのインストール状態メッセージを表示する<!-- 2514416  -->
ポータル サイト アプリでは、エンド ユーザーに追加のアプリ インストール状態メッセージが表示されます。 新しい Win32 依存関係機能には、次の条件が適用されます。
- アプリをインストールできませんでした。 管理者によって定義された依存関係が満たされませんでした。

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>iOS デバイス上の Microsoft Edge に Web クリップを再ターゲットする<!-- 5455276 -->
iOS デバイス上でピン留めされた Web アプリとして機能する Web クリップを更新する必要があります。 新しく展開された Web クリップを保護されたブラウザーで開く必要がある場合は、Intune Managed Browser ではなく Microsoft Edge で開きます。 既存の Web クリップを再ターゲットして、Managed Browser ではなく Microsoft Edge で開くようにする必要があります。 


<!-- ***********************************************-->
## <a name="device-configuration"></a>デバイスの構成

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS デバイス用の有線ネットワーク デバイス構成プロファイル<!-- 3508686  -->
有線ネットワークを構成する ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームの **[macOS]** > プロファイル タイプの **[ワイヤード (有線) ネットワーク]** ) 新しい macOS デバイス構成プロファイルが使用できるようになります。 この機能を使用して、有線ネットワークを管理する 802.1x プロファイルを作成し、この有線ネットワークを macOS デバイスに展開します。

適用対象:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>IKEv2 VPN 接続を使用する VPN プロファイルでは iOS デバイスで常時接続を使用できる <!-- 1947932 idready -->
iOS デバイスでは、IKEv2 接続を使用する VPN プロファイルを作成することができます ( **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームの **[iOS/iPadOS]** > プロファイル タイプの **[VPN]** )。 今後の更新では、IKEv2 を使用して常時接続を構成することができます。 構成すると、IKEv2 VPN プロファイルは自動的に接続され、VPN に接続されたままになります (またはすぐに再接続されます)。 ネットワーク間を移動したり、デバイスを再起動したりしても、接続されたままになります。

iOS では、常時接続 VPN は IKEv2 プロファイルに限定されます。

現在構成できる IKEv2 設定については、「[Microsoft Intune で iOS デバイス向けの VPN 設定を追加する](../configuration/vpn-settings-ios.md#ikev2-settings)」を参照してください。

適用対象:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>iOS および macOS デバイスで構成プロファイルを作成するときのユーザー インターフェイス エクスペリエンスの向上<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
iOS または macOS デバイス用のプロファイルを作成すると、Endpoint Management 管理センターのエクスペリエンスが更新されます。 この変更は、次のデバイス構成プロファイルに影響します ( **[デバイス]**  >  **[構成プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームの **[iOS]** または **[macOS]** ):

- カスタム: iOS、macOS
- デバイスの機能: iOS、macOS
- デバイスの制限: iOS、macOS
- エンドポイント保護: macOS
- 拡張機能: macOS
- 設定ファイル: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Android Enterprise デバイスで OEMConfig 構成プロファイルを作成するときのユーザー インターフェイス エクスペリエンスの向上<!-- 5568645 idready  -->
Android Enterprise デバイスで OEMConfig プロファイルを作成または編集すると、Endpoint Management 管理センターのエクスペリエンスが更新されます。 更新されたエクスペリエンスによって、構成した設定の概要が表示されます。 この変更は、OEMConfig デバイス構成プロファイルに影響します ( **[デバイス]**  >  **[構成プロファイル]**  >  **[プロファイルの作成]**  >  プラットフォームの **[Android Enterprise]** > プロファイルの種類の **[OEMConfig]** )。

この機能は、以下に適用されます。
- Android エンタープライズ 

<!-- ***********************************************-->
<!--## Device enrollment-->



<!-- ***********************************************-->
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>ロール ベースのアクセス制御

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune ロールのユーザー インターフェイスが変更予定<!--5801612 idready-->
[Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) >  **[テナント管理]**  >  **[ロール]** のユーザー インターフェイスが、ユーザーフレンドリで直感的な設計に変更されます。 このエクスペリエンスでは、現在使用しているのと同じ設定と詳細が提供されます。ただし、新しいエクスペリエンスでは、ウィザードに似たプロセスが採用されています。


<!-- ***********************************************-->
## <a name="security"></a>セキュリティ

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO デバイスでの派生資格情報のサポート<!--4839592-->
Android Enterprise の完全に管理されたデバイスで、派生資格情報を使用できるようになります。 Entrust Datacard、Intercede、および DISA Purebred の派生資格情報を取得するためのサポートが追加されます。 アプリ認証、Wi-Fi、VPN、または S/MIME 署名や、それをサポートするアプリでの暗号化に、派生資格情報を使用できるようになります。 

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new.md)」をご覧ください。


