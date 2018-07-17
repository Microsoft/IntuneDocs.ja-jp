---
title: Microsoft Intune で Android 仕事用プロファイルのデバイスを管理する
titlesuffix: ''
description: Microsoft Intune は Android 仕事用プロファイルのデバイスを管理し、ユーザーが仕事に Android デバイスを使用するときに追加の管理機能とプライバシーを提供します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9c3184ff01252d2f53b5bfcce286df3424da23c2
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909169"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Intune で Android 仕事用プロファイルのデバイスを管理する

Android Enterprise は、仕事用のアプリとデータから個人用アプリとデータを分離する、機能とサービスのセットです。 Android Enterprise は、ユーザーが仕事に Android デバイスを使用するときの追加の管理機能とプライバシーを提供します。 

## <a name="supported-devices"></a>サポートされるデバイス

Android Enterprise の管理機能は、新しい Android オペレーティング システムに含まれる機能に依存しています。 Android Enterprise をサポートしていないデバイスの場合、従来の Android 管理を使用できます。 詳細については、「[Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)」(Android Enterprise の要件) を参照してください。

## <a name="onboarding"></a>オンボード

Android 仕事用プロファイルのデバイスを登録する前に、いくつかのオンボード手順を完了する必要があります。 次の手順では、Intune テナントと Google Play for Work サービス間の接続を確立します。 詳細については、「[Enable enrollment of Android work profile devices](android-work-profile-enroll.md)」(Android 仕事用プロファイルのデバイスの登録を有効にする) を参照してください。

## <a name="work-profile-management"></a>仕事用プロファイルの管理

Intune で Android 仕事用プロファイルのデバイスを管理する場合、デバイス全体は管理しません。 管理機能は、登録時にデバイスに作成された仕事用プロファイルにのみ影響します。 Intune でデバイスに展開されるすべてのアプリが、仕事用プロファイルにインストールされます。 仕事用プロファイルのアプリ アイコンは、デバイス上の個人用アプリと区別されます。 デバイスの Android Enterprise に含まれないすべての Android アプリとデータは個人用であり、エンド ユーザーが管理します。 ユーザーは、デバイスの個人用の側に任意のアプリをインストールできます。 管理者は、仕事用プロファイルの対象となるアプリケーションと操作を管理および監視できます。

Intune には、Android 仕事用プロファイルのデバイスで構成できるさまざまな全般設定が組み込まれています。 詳細については、「[Android work profile device policy settings](compliance-policy-create-android-for-work.md)」(Android 仕事用プロファイルのデバイスのポリシーの設定) を参照してください。

## <a name="app-publishing-and-distribution"></a>アプリの発行と配布

Google Play for Work サービスは、Android Enterprise アプリの配布と管理に不可欠な要素です。 仕事用プロファイルで Android 仕事用プロファイルのデバイスに展開されるすべてのアプリは、Managed Google Play サービスから取得できます。 Play ストアでアプリを管理し、展開するには、Google 管理用の会社の管理者資格情報で Google Play の Web サイトにサインインします。 アプリの Android Enterprise の展開を承認し、デバイスの仕事プロファイルに表示させることができます。 これらのアプリは Intune コンソールと同期されます。Intune コンソールでは、Intune を使用してアプリの展開と管理を行うことができます。 組織が開発した基幹業務 (LOB) アプリは、Google の Android アプリ公開コンソールを使用して Managed Google Play に公開する必要があります。 基幹業務アプリは、Android アプリ公開コンソールで組織にアクセスを限定するように構成する必要があります。

アプリは、ユーザー操作なしでインストールできます。また、ユーザーが**不明なソースからのインストール**を許可する必要もありません。 オプションまたは使用可能なアプリを参照およびインストールする場合、デバイスで Google Play ストアを参照できます。 詳細については、「[Intune を使用してアプリを Android for Work デバイスに割り当てる](apps-add-android-for-work.md)」を参照してください。

## <a name="app-configuration"></a>アプリの構成

Android Enterprise には、アプリの構成値を、そのアプリをサポートするアプリに展開するインフラストラクチャがあります。 仕事用アプリの構成値を指定することで、ユーザーが初めてそのアプリを起動するときに構成値を正しく設定することができます。 アプリ構成をサポートするには、管理されている構成値をサポートする Android アプリをアプリ開発者が作成する必要があります。 そうすると、Intune を使用して、構成設定を指定および適用できるようになります。 詳細については、「[管理対象の Android デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-android.md)」を参照してください。

## <a name="email-configuration"></a>電子メールの構成

Android Enterprise には、iOS で提供されているような既定の電子メール アプリまたはネイティブの電子メール プロファイル オブジェクトはありません。 その代わり、サポートする電子メール アプリにアプリ構成設定を適用することで、電子メール構成を設定できます。 Play ストアにある Gmail と Nine Work は、Android Enterprise アプリ構成による構成をサポートする 2 つの Exchange ActiveSync (EAS) クライアント アプリです。

Gmail アプリと Nine Work アプリを仕事用のアプリとして管理する場合、Intune には構成テンプレートがあります。 アプリ構成プロファイルをサポートするその他の電子メール アプリは、モバイル アプリ構成ポリシーを使用して構成することができます。

Android 仕事用プロファイルのデバイスで Exchange ActiveSync の条件付きアクセスを使用している場合、Gmail または Nine Work 電子メール アプリの使用を検討してください。 Android アプリ用 Microsoft Outlook、または ADAL 経由の新しい認証方法を使用する他の電子メール アプリもサポートされます。 詳細については、「[Microsoft Intune で電子メールの設定を構成する方法](email-settings-configure.md)」を参照してください。

## <a name="app-protection-policies"></a>アプリ保護ポリシー

適用されているアプリ保護ポリシーは、仕事用プロファイルと個人用プロファイルで完全にサポートされています。 Android アプリ公開コンソール (https://play.google.com/apps/publish) で基幹業務アプリを公開できます。 このコンソールには、アプリを組織にのみ制限するオプションもあります。 詳細については、「[Intune で Android for Work デバイス用のデバイス コンプライアンス ポリシーを追加する](compliance-policy-create-android-for-work.md)」を参照してください。 アプリ保護ポリシーについて詳しくは、「[アプリ保護ポリシーとは](app-protection-policy.md)」を参照してください。

## <a name="vpn-profiles"></a>VPN プロファイル

VPN のサポートは、Android VPN プロファイルに似ています。 Android Enterprise 管理では同じ VPN プロバイダーと基本構成オプションを使用できますが、次の 2 つの違いがあります。

-  **仕事用プロファイル対象の VPN** - VPN 接続は、仕事用プロファイルに展開されるアプリのみが対象です。 Android Enterprise で管理されるアプリのみが VPN 接続を使用できます。 デバイス上の個人用のアプリは、管理対象の VPN 接続を使用できません。 詳細については、「[Android enterprise VPN settings](vpn-settings-android.md#android-work-profile-device-vpn-settings)」(Android Enterprise の VPN 設定) を参照してください。

-  **アプリ固有の VPN** – VPN プロバイダーがサポートしている場合は、Intune でアプリ固有の VPN を構成できます。
    - アプリ固有の VPN の構成
    - Android Enterprise アプリの構成プロファイルを介してアプリごとの VPN を構成する機能です。
    詳細については、「[Microsoft Intune のカスタム プロファイルを使って、Android デバイス用にアプリごとの VPN プロファイルを作成する](android-pulse-secure-per-app-vpn.md)」を参照してください。

## <a name="certificate-profiles"></a>証明書プロファイル

Android 管理で使用できるものと同じ証明書プロファイルの構成オプションが、Android 仕事用プロファイルのデバイスで使用できます。 Android Enterprise には、強化された証明書管理 API があります。 強化された証明書管理には、次の機能があります。

-  ユーザーにとって、証明書の展開が自動的かつシームレスに実行されます。
-  デバイスが Intune のインベントリから削除され、仕事用プロファイルが削除されるときに、展開された証明書が削除されます。
-  IT 部門が管理サービスを介して証明書を展開し、構成したことをユーザーに伝えるメッセージ処理が改善されます。

詳細については、「[Microsoft Intune でデバイスの証明書プロファイルを構成する](certificates-configure.md)」を参照してください。

## <a name="wi-fi-profiles"></a>Wi-Fi プロファイル

デバイスが Intune のインベントリから削除され、仕事用プロファイルが削除されると、Android Enterprise が管理する Wi-Fi プロファイルが削除されます。 詳細については、「[Microsoft Intune で Wi-Fi の設定を構成する方法](wi-fi-settings-configure.md)」を参照してください。

## <a name="next-steps"></a>次の手順
- [Android デバイスを登録する](android-enroll.md)
- [Intune で Android 仕事用プロファイルのデバイスにアプリを割り当てる](apps-add-android-for-work.md)