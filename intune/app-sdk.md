---
title: Intune App SDK の利点
titleSuffix: Microsoft Intune
description: Intune アプリ SDK は、iOS プラットフォームと Android プラットフォームの両方で利用でき、Microsoft Intune を使ったモバイル アプリ管理機能が有効になります。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a8722f5cef29dfec8b0d3eabcc6eeac0a188456
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582880"
---
# <a name="microsoft-intune-app-sdk-overview"></a>Microsoft Intune App SDK の概要
iOS と Android の両方で使用可能な Intune App SDK によって、ご使用のアプリで Intune [アプリ保護ポリシー](app-protection-policy.md)をサポートできるようにします。 アプリにアプリ保護ポリシーを適用すると、そのアプリを Intune で管理できるようになり、マネージド アプリとして Intune で認識されるようになります。 SDK では、アプリの開発者が必要なコード変更が最小限に抑えられます。 SDK の機能の多くは、アプリの動作を変更せずに利用できます。 エンド ユーザーと IT 管理者のエクスペリエンスを向上させるために、SDK の API を利用してアプリの動作をカスタマイズし、アプリ側の処理が必要な機能をサポートします。

ご利用のアプリで Intune アプリ保護ポリシーをサポートできるようにすると、IT 管理者はそのポリシーを展開し、アプリ内の会社データを保護することができます。

## <a name="app-protection-features"></a>アプリ保護機能

SDK で有効にできる Intune アプリ保護機能の例を以下に示します。

### <a name="control-users-ability-to-move-corporate-files"></a>ユーザーに会社のファイルの移動を許すかどうかを制御
IT 管理者は、アプリ内の職場または学校のデータを移動できる場所を制御できます。 たとえば、アプリで会社のデータをクラウドにバックアップできないようにするポリシーを展開できます。

### <a name="configure-clipboard-restrictions"></a>クリップボードの制限の構成
IT 管理者は、Intune の管理対象アプリにおけるクリップボードの動作を構成できます。 たとえば、エンド ユーザーがアプリからデータを切り取るかコピーして、管理されていない個人アプリに貼り付けられないようにするポリシーを展開できます。

### <a name="enforce-encryption-on-saved-data"></a>保存データへの暗号化の適用
IT 管理者は、アプリによってデバイスに保存されたデータを確実に暗号化するポリシーを適用できます。

### <a name="remotely-wipe-corporate-data"></a>会社のデータのリモート ワイプ
IT 管理者は、Intune で管理されたアプリから会社のデータをリモートでワイプできます。 これは ID ベースの機能で、エンドユーザーの社内 ID に関連付けられたファイルのみが削除されます。 この機能を実行するには、アプリによる処理が必要です。 アプリは、ワイプする必要のある ID を、ユーザー設定を基に指定できます。 指定されたユーザー設定がアプリにない場合、既定の動作では、アプリケーションのディレクトリがワイプされ、エンド ユーザーにアクセスが削除されたことが通知されます。

### <a name="enforce-the-use-of-a-managed-browser"></a>管理対象ブラウザーの使用を強制
IT 管理者は、アプリ内の Web リンクを開くときに、[Intune Managed Browser アプリ](app-configuration-managed-browser.md)の使用を強制することができます。 この機能により、企業環境で表示されるリンクが Intune で管理されたアプリのドメイン内に維持されることが保証されます。

### <a name="enforce-a-pin-policy"></a>暗証番号 (PIN) ポリシーの適用
IT 管理者は、エンド ユーザーがアプリ内の企業データにアクセスする前に PIN の入力を求めることができます。 これにより、アプリを使用するユーザーが、職場または学校のアカウントで最初にサインインしたユーザーであることが保証されます。 エンド ユーザーが自分の PIN を構成するときに、Intune App SDK は Azure Active Directory を使用して、エンド ユーザーの資格情報を登録されている Intune アカウントに照らして確認します。

### <a name="require-users-to-sign-in-with-a-work-or-school-account-for-app-access"></a>ユーザーはアプリにアクセスするために職場または学校のアカウントでサインインする必要がある
IT 管理者は、アプリへのアクセスに、職場または学校のアカウントを使用してサインインすることをユーザーに求めることができます。 Intune App SDK は Azure Active Directory を使用してシングル サインオン エクスペリエンスを提供します。1 回入力した資格情報が、それ以降のログインで再利用されます。 Azure Active Directory とフェデレーションしている ID 管理ソリューションの認証もサポートしています。

### <a name="check-device-health-and-compliance"></a>デバイスのヘルスとコンプライアンスの確認
エンド ユーザーがアプリにアクセスする前に、IT 管理者は、デバイスのヘルスと Intune ポリシーに対するコンプライアンスを確認できます。 iOS では、このポリシーにより、デバイスがジェイルブレイクされているかどうかを確認できます。 Android では、このポリシーにより、デバイスがルート化されているかどうかを確認できます。

### <a name="support-multi-identity"></a>複数 ID のサポート
複数 ID のサポートは、ポリシーで管理された (会社) アカウントと、管理されていない (個人) アカウントとが 1 つのアプリに共存できるようにする SDK の機能です。

たとえば、多くのユーザーは、iOS 用および Android 用の Office モバイル アプリで、会社と個人の両方のメール アカウントを構成しています。 ユーザーが会社のアカウントでデータにアクセスする場合、IT 管理者はアプリ保護ポリシーが確実に適用されるようにする必要があります。 一方、ユーザーが個人用のメール アカウントにアクセスする場合、データは IT 管理者の管理下にありません。 Intune App SDK では、アプリの会社 ID **のみ**をアプリ保護ポリシーの対象として、これを実現します。

複数 ID 機能は、個人と職場の両方のアカウントをサポートするストア アプリを使用することで組織が直面しているデータ保護の問題を解決するのに役立ちます。
 
### <a name="app-protection-without-device-enrollment"></a>デバイス登録が不要なアプリの保護

>[!IMPORTANT]
>デバイス登録のない Intune アプリ保護は、Intune App ラッピング ツール、Intune App SDK for Android、Intune App SDK for iOS、Intune App SDK Xamarin バインディングで利用できます。

個人用デバイスを使用するユーザーの多くは、モバイル デバイス管理 (MDM) プロバイダーを使用して自分の個人用デバイスを登録せずに、会社のデータにアクセスしたいと考えます。 MDM 登録にはデバイスのグローバル制御が必要になるため、多くの場合、ユーザーは自分の個人用デバイスの制御を会社に任せることをためらいます。

デバイス登録が不要なアプリの保護を使用すると、Microsoft Intune サービスでアプリ保護ポリシーを直接アプリに展開することができ、ポリシーの展開でデバイス管理チャネルに依存する必要がなくなります。

### <a name="on-demand-application-vpn-connections-with-citrix-mvpn"></a>Citrix mVPN でのオンデマンドのアプリケーション VPN 接続 
Citrix XenMobile MDX と Microsoft Intune を組み合わせ、デバイスとアプリを管理することができます。 この組み合わせにより、Citrix の mVPN テクノロジを使用し、Intune アプリの保護ポリシーでアプリを管理できるようになります。 Citrix は、iOS と Android 用の Intune App SDK、および iOS と Android 用の Intune アプリ ラッピング ツール(citrix フラグを含む) に統合されています。
 
Citrix MDX の詳細については、「[About the MDX Toolkit](https://docs.citrix.com/en-us/mdx-toolkit/10/about-mdx-toolkit.html)」 (MDX ツールキットについて)、「[Citrix MDX app wrapper for iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html)」 (iOS 用の Citrix MDX アプリ ラッパー) および「[Citrix MDX app wrapper for Android](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-android.html)」 (Android 用の Citrix MDX アプリ ラッパー) を参照してください。

## <a name="next-steps"></a>次の手順

- [Microsoft Intune アプリ SDK の概要](app-sdk-get-started.md)
