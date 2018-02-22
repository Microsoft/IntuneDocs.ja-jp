---
title: "Android for Work について"
description: "Intune は Android for Work を管理し、ユーザーが仕事に Android デバイスを使用するときに追加の管理機能とプライバシーを提供します。"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: d7939a20e9729487ce5824ba3f67cd84ec970032
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="manage-android-for-work-devices-with-intune"></a>Intune で Android for Work デバイスを管理する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work は、仕事用のアプリとデータを含む仕事用プロファイルから個人用アプリとデータを分離する、Android デバイスの機能とサービスのセットです。 Android for Work は、ユーザーが仕事に Android デバイスを使用するときの追加の管理機能とプライバシーを提供します。 Intune を使用すると、アプリと会社のリソースを Android for Work デバイスに展開し、仕事の情報と個人の情報を分けることができます。 展開に成功すると、ユーザーがアクセスするアプリとデータは、デバイス上の Android for Work 環境内にのみ存在します。

## <a name="supported-devices"></a>サポートされるデバイス

Android for Work の管理機能は、新しい Android オペレーティング システムに含まれる機能に依存しています。 現在、Android for Work は、Android 5.0 Lollipop 以降を実行し、仕事用プロファイルをサポートしているデバイスでサポートされています。 Android for Work をサポートしていないデバイスの場合、従来の Android 管理を使用できます。 詳細については、「[Android for Work requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)」(Android for Work の要件) を参照してください。

## <a name="onboarding"></a>オンボード

Android for Work デバイスを登録する前に、いくつかのオンボード手順を完了する必要があります。 この手順で、Intune テナントと Google Play for Work サービス間に接続を確立します。この接続は、Android for Work アプリの配布と管理プロセスに不可欠な要素です。 詳細については、「[Android for Work デバイスの登録を有効にする](/intune-classic/deploy-use/set-up-android-for-work)」を参照してください。

## <a name="work-profile-management"></a>仕事用プロファイルの管理

Intune で Android for Work デバイスを管理する場合、デバイス全体は管理しません。 管理機能は、登録時にデバイスに作成された仕事用プロファイルにのみ影響します。 Intune でデバイスに展開されるすべてのアプリが、仕事用プロファイルにインストールされます。 仕事用プロファイルのアプリ アイコンには、デバイスの個人用アプリから仕事用アプリを区別するためにオレンジ色のブリーフケースが表示されます。 デバイスの Android for Work に含まれないすべての Android アプリとデータは個人用であり、エンド ユーザーが管理します。 ユーザーはデバイスの個人用の側に任意のアプリをインストールできます。一方、管理者は仕事用プロファイルの対象となるアプリと操作を管理および監視できます。

Intune には、Android for Work デバイスで構成できるさまざまな全般設定が組み込まれています。 詳細については、[Android for Work のポリシー設定](android-for-work-policy-settings-in-microsoft-intune.md)を参照してください。

## <a name="app-publishing-and-distribution"></a>アプリの発行と配布

Google Play サービスは、Android for Work アプリの配布と管理に不可欠な要素です。 仕事用プロファイルで Android for Work デバイスに展開されるすべてのアプリは、Google Play サービスから取得できます。 Play ストアでアプリを管理し、展開するには、Google 管理用の会社の管理者資格情報で Google Play の Web サイトにログインします。 アプリの Android の展開を承認し、デバイスの仕事プロファイルに表示させることができます。 これらのアプリは Intune コンソールと同期されます。Intune コンソールでは、Intune を使用してアプリの展開と管理を行うことができます。 組織が開発した基幹業務 (LOB) アプリは、Google の Android アプリ公開コンソールを使用して Play for Work に公開する必要があります。 基幹業務アプリは、Android アプリ公開コンソールで組織にアクセスを限定するように構成する必要があります。

アプリは、ユーザー操作なしでインストールできます。また、ユーザーが**不明なソースからのインストール**を許可する必要もありません。 オプションまたは使用可能なアプリを参照およびインストールする場合、デバイスで Google Play ストアを参照できます。 詳細については、「[Intune を使用してアプリを Android for Work デバイスを展開する方法](/intune-classic/deploy-use/android-for-work-apps)」を参照してください。

## <a name="app-configuration"></a>アプリの構成

Android for Work には、アプリの構成値を、そのアプリをサポートするアプリに展開するインフラストラクチャがあります。 仕事用アプリの構成値を指定することで、ユーザーが初めてそのアプリを起動するときに構成値を正しく設定することができます。 アプリ構成をサポートするには、管理されている構成値をサポートする Android アプリをアプリ開発者が作成する必要があります。 そうすると、Intune を使用して、構成設定を指定および適用できるようになります。 詳細については、「[Android for Work app configuration settings](afw-app-configuration-policy.md)」(Android for Work アプリの構成設定) を参照してください。

## <a name="email-configuration"></a>電子メールの構成

Android には、iOS で提供されているような既定の電子メール アプリまたはネイティブの電子メール プロファイル オブジェクトはありません。 その代わり、サポートする電子メール アプリにアプリ構成設定を適用することで、電子メール構成を設定できます。 Play ストアにある Gmail と Nine Work は、Android for Work アプリ構成による構成をサポートする 2 つの Exchange ActiveSync (EAS) クライアント アプリです。

Gmail アプリと Nine Work アプリを仕事用のアプリとして管理する場合、Intune には構成テンプレートがあります。 アプリ構成プロファイルをサポートするその他の電子メール アプリは、モバイル アプリ構成ポリシーを使用して構成することができます。

Android for Work デバイスで Exchange ActiveSync の条件付きアクセスを使用している場合、Gmail または Nine Work 電子メール アプリを使用する必要があります。 Android アプリ用 Microsoft Outlook、または ADAL 経由の新しい認証方法を使用する他の電子メール アプリもサポートされます。 詳細については、「[Microsoft Intune で電子メール プロファイルを使用して会社の電子メールへのアクセスを構成にする](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)」を参照してください。

## <a name="app-protection-policies"></a>アプリ保護ポリシー

適用されているアプリ保護ポリシーは、仕事用プロファイルと個人用プロファイルで完全にサポートされています。 Android アプリ公開コンソール (https://play.google.com/apps/publish) で基幹業務アプリを公開できます。 このコンソールには、アプリを組織にのみ制限するオプションもあります。 詳細については、[Android for Work のコンプライアンス ポリシー設定](afw-compliance-policy-settings-in-microsoft-intune.md)を参照してください。 アプリ保護ポリシーの一般情報については、[アプリ ポリシー](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)に関するページをご覧ください。

## <a name="vpn-profiles"></a>VPN プロファイル

VPN のサポートは、Android VPN プロファイルに似ています。 Android 管理では同じ VPN プロバイダーと基本構成オプションを使用できますが、次の 2 つの違いがあります。

-  **仕事用プロファイル対象の VPN** - VPN 接続は、仕事用プロファイルに展開されるアプリのみが対象です。 Android for Work で管理されるアプリのみが VPN 接続を使用できます。 デバイス上の個人用のアプリは、管理対象の VPN 接続を使用できません。

-  **アプリ固有の VPN** - VPN プロバイダーがアプリ固有の VPN の構成をサポートし、Android for Work アプリ構成プロファイルを介してアプリごとの VPN を構成する互換性がある場合、Intune でアプリ固有の VPN を構成できます。 この機能をサポートしているかどうかについては、VPN プロバイダーに問い合わせてください。 詳細については、[VPN 接続プロファイル](vpn-connections-in-microsoft-intune.md)に関するページを参照してください。

## <a name="certificate-profiles"></a>証明書プロファイル

Android 管理で使用できるものと同じ証明書プロファイルの構成オプションが、Android for Work デバイスで使用できます。 Android for Work には、強化された証明書管理 API があります。 強化された証明書管理には、次の機能があります。

- ユーザーにとって、証明書の展開が自動的かつシームレスに実行されます。
-  デバイスが Intune のインベントリから削除され、仕事用プロファイルが削除されるときに、展開された証明書が完全に削除されます。
-  IT 部門が管理サービスを介して証明書を展開し、構成したことをユーザーに伝えるメッセージ処理が改善されます。

詳細については、「[Microsoft Intune の証明書プロファイルでリソースへのアクセスを保護する](secure-resource-access-with-certificate-profiles.md)」を参照してください。

## <a name="wi-fi-profiles"></a>Wi-Fi プロファイル

デバイスが Intune のインベントリから削除され、仕事用プロファイルが削除されると、Android for Work が管理する Wi-Fi プロファイルが削除されます。 詳細については、「[デバイスを構成すると、会社の Wi-Fi ネットワークに接続できます](wi-fi-connections-in-microsoft-intune.md)」を参照してください。

## <a name="next-steps"></a>次の手順
[Android for Work の登録を有効にする](/intune-classic/deploy-use/set-up-android-for-work)

[Android for Work 用アプリの展開](/intune-classic/deploy-use/android-for-work-apps)
