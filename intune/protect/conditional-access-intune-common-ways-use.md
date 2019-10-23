---
title: 条件付きアクセスのシナリオ
titleSuffix: Microsoft Intune
description: デバイスベースおよびアプリベースの条件付きアクセスで、Intune の条件付きアクセスが一般的にどのように使用されるかについて説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 00743e020fc9d42970dca5efa130908a53c6c5bf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504593"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Intune での条件付きアクセスの一般的な使用方法

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Intune での条件付きアクセスには、デバイス ベースの条件付きアクセスとアプリ ベースの条件付きアクセスの 2 種類があります。 組織の条件付きアクセス コンプライアンスを進めるために関連するコンプライアンス ポリシーを構成する必要があります。 条件付きアクセスは、一般的に Exchange へのアクセスの許可またはブロック、ネットワークへのアクセスの制御、Mobile Threat Defense ソリューションとの統合などを行うために使用されます。
 
この記事は、Intune のモバイル "*デバイス*" のコンプライアンス機能と Intune のモバイル "*アプリケーション*" 管理 (MAM) 機能の使用方法を理解するのに役立ちます。 

> [!NOTE]
> 条件付きアクセスは、Azure Active Directory Premium ライセンスに含まれる Azure Active Directory の機能です。 Intune は、モバイル デバイス コンプライアンスとモバイル アプリ管理をソリューションに加えて、この機能を強化します。 *Intune* からアクセスされる条件付きアクセス ノードは、*Azure AD* からアクセスされるノードと同じです。  

## <a name="device-based-conditional-access"></a>デバイスベースの条件付きアクセス

Intune と Azure Active Directory が連携することで、マネージド デバイスと準拠デバイスのみが電子メール、Office 365 サービス、サービスとしてのソフトウェア (SaaS) アプリ、および[オンプレミス アプリ](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)にアクセスできるようになります。 また、ドメインに参加しているコンピューターまたは Intune に登録されているモバイル デバイスのみが Office 365 サービスにアクセスできるように、Azure Active Directory 内にポリシーを設定できます。

Intune には、デバイスのコンプライアンス対応状態を評価する、デバイス コンプライアンス ポリシーの機能があります。 コンプライアンス対応状態は Azure Active Directory に報告され、ユーザーが会社のリソースにアクセスしようとしたときに、Azure Active Directory で作成された条件付きアクセスのポリシーを適用するために使用されます。

Exchange Online や他の Office 365 製品のデバイスベースの条件付きアクセス ポリシーは、[Azure portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune) で構成します。  

- Azure Active Directory で条件付きアクセスを使用するサポートされるブラウザーについては、[こちら](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)を参照してください。

- Intune のデバイス コンプライアンスの詳細については、[こちら](device-compliance-get-started.md)を参照してください。

- Azure Active Directory の条件付きアクセスでサポートされるブラウザーについては、[こちら](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers)を参照してください。

> [!NOTE]
> Android デバイスでは、SharePoint Online に対するデバイスベースのアクセスまたは Exchange Online に対するブラウザーベースのアクセスが有効な場合、ユーザーは登録されたデバイスで次のように **[ブラウザー アクセスを有効にする]** オプションを有効にする必要があります。
> 1. **ポータル サイト アプリ**を起動します。
> 2. トリプル ドット (...) またはハードウェアのメニュー ボタンから、 **[設定]** ページに移動します。
> 3. **[ブラウザー アクセスを有効にする]** ボタンを押します。 
> 4. Chrome ブラウザーで Office 365 からサインアウトして、Chrome を再起動します。

### <a name="conditional-access-based-on-network-access-control"></a>ネットワーク アクセス制御に基づいた条件付きアクセス

Intune は Cisco ISE、Aruba Clear Pass、Citrix NetScaler などのパートナーと統合され、Intune 登録とデバイスのコンプライアンス対応状態に基づいたアクセス制御が提供されます。

ユーザーは、使用しているデバイスが管理され、Intune デバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、会社の Wi-Fi や VPN リソースへのアクセスを許可または拒否されます。

- NAC と Intune の統合について詳しくは、[こちら](network-access-control-integrate.md)をご覧ください。

### <a name="conditional-access-based-on-device-risk"></a>デバイスのリスクに基づいた条件付きアクセス

Intune は、モバイル デバイス上のマルウェア、トロイの木馬、およびその他の脅威を検出するためのセキュリティ ソリューションを提供する Mobile Threat Defense ベンダーと提携しました。

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune と Mobile Threat Defense の統合のしくみ

モバイル デバイスに Mobile Threat Defense エージェントがインストールされている場合、モバイル デバイスで脅威が検出されると、コンプライアンス対応状態のメッセージがエージェントから Intune に返されます。

Intune と Mobile Threat Defense の統合は、デバイスのリスクに基づいた条件付きアクセスの決定において重要な役割を果たします。

- Intune Mobile Threat Defense について詳しくは、[こちら](mobile-threat-defense.md)をご覧ください。

### <a name="conditional-access-for-windows-pcs"></a>Windows PC の条件付きアクセス

PC の条件付きアクセスでは、モバイル デバイスで利用できる機能と同様の機能が提供されます。 Intune で PC を管理する場合に条件付きアクセスを使用する方法について説明します。

#### <a name="corporate-owned"></a>企業所有

- **オンプレミス AD ドメインへの参加:** この方法は、AD のグループ ポリシーや System Center Configuration Manager を使用して PC を管理している現在のやり方におおむね満足している組織でよく使用されます。

- **Azure AD ドメインへの参加と Intune の管理:** このシナリオは、クラウドファーストにすることを望んでいる (つまり、主にクラウド サービスを使用し、オンプレミスのインフラストラクチャの使用を減らすことを目標としている) 組織や、クラウドのみを使用する (オンプレミスのインフラストラクチャがない) 組織向けです。 Azure AD への参加はハイブリッド環境で適切に機能し、クラウドとオンプレミスのアプリとリソースの両方にアクセスできるようにします。 Azure AD に参加したデバイスは Intune に登録されます。会社のリソースにアクセスするときに、これを条件付きアクセスの基準として使用できます。

- **AD ドメインへの参加と System Center Configuration Manager:** 現在のブランチでは、System Center Configuration Manager は、ドメインに参加している PC となるのに加え、次の特定のコンプライアンス基準を評価できる条件付きアクセス機能を提供します。

  - PC が暗号化されているか。

  - マルウェア対策がインストールされているか。 PC は最新の状態か。

  - デバイスが脱獄またはルート化されているか。

#### <a name="bring-your-own-device-byod"></a>Bring Your Own Device (BYOD)

- **Workplace Join と Intune 管理:** この場合、ユーザーは個人のデバイスを参加させて、会社のリソースやサービスにアクセスできます。 Workplace Join を使用してデバイスを Intune MDM に登録し、デバイスレベルのポリシーを受け取ることができます。これは、条件付きアクセスの基準を評価する別のオプションです。

Azure Active Directory のデバイス管理の詳細については、[こちら](https://docs.microsoft.com/azure/active-directory/devices/overview)を参照してください。

## <a name="app-based-conditional-access"></a>アプリベースの条件付きアクセス

Intune と Azure Active Directory が連携することで、管理対象アプリのみが会社の電子メールやその他の Office 365 サービスにアクセスできるようになります。

- Intune を使用したアプリ ベースの条件付きアクセスについて詳しくは、[こちら](app-based-conditional-access-intune.md)をご覧ください。

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Exchange On-Premises での Intune 条件付きアクセス

条件付きアクセスを使用すると、デバイス コンプライアンス ポリシーと登録状態に基づいて、**Exchange On-Premises** へのアクセスを許可またはブロックすることができます。 条件付きアクセスをデバイス コンプライアンス ポリシーと組み合わせて使用した場合は、準拠デバイスのみが Exchange On-Premises へのアクセスを許可されます。

条件付きアクセスの詳細設定を構成して、次のような細かい制御を行うことができます。

- 特定のプラットフォームを許可またはブロックする。

- Intune で管理されていないデバイスを即時ブロックする。

デバイス コンプライアンスと条件付きアクセス ポリシーが適用されると、Exchange On-Premises へのアクセスで使用されるデバイスがチェックされます。

デバイスが条件を満たしていない場合、エンド ユーザーは、デバイス非準拠の原因である問題を修正するためのデバイス登録プロセスを提示されます。

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange On-Premises の条件付きアクセスのしくみ

Exchange On-Premises の条件付きアクセスの動作は、Azure の条件付きアクセス ベースのポリシーとは異なります。 Intune Exchange On-premises コネクタをインストールして、Exchange サーバーと直接対話します。 Intune Exchange Connector は Exchange サーバーに存在するすべての Exchange Active Sync (EAS) レコードを収集するため、Intune はこれらの EAS レコードを取得して、Intune デバイス レコードにマップすることができます。 これらのレコードはデバイスに登録され、Intune によって認識されます。 このプロセスにより、電子メールへのアクセスが許可またはブロックされます。

EAS レコードが新しいために Intune で認識されない場合、電子メールへのアクセスをブロックすることを Exchange サーバーに指示するコマンドレットが Intune によって発行されます。 このプロセスのしくみの詳細を次に示します。

![Exchange On-premises と条件付きアクセス (CA) のフローチャート](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. ユーザーは、Exchange On-premises 2010 SP1 以降でホストされている会社の電子メールにアクセスしようとしています。

2. デバイスが Intune で管理されていない場合、電子メールへのアクセスがブロックされます。 Intune によって、EAS クライアントにブロック通知が送信されます。

3. EAS がブロック通知を受信し、該当デバイスを検疫に移動して、検疫メールを送信します。このメールには、ユーザーがデバイスを登録するためのリンクを含む修復手順が記載されています。

4. Workplace Join プロセスが発生します。これは、Intune でデバイスを管理する最初の手順です。

5. デバイスが Intune に登録されます。

6. Intune により EAS レコードとデバイス レコードがマップされ、デバイスのコンプライアンス対応状態が保存されます。

7. Azure AD Device Registration プロセスにより EAS クライアント ID が登録され、Intune デバイス レコードと EAS クライアント ID の間のリレーションシップが作成されます。

8. Azure AD Device Registration により、デバイスの状態に関する情報が保存されます。

9. ユーザーが条件付きアクセス ポリシーを満たしている場合、Intune によって Intune Exchange Connector を介して、メールボックスの同期を許可するコマンドレットが発行されます。

10. Exchange サーバーが EAS クライアントに通知を送信し、ユーザーは電子メールにアクセスできるようになります。


#### <a name="whats-the-intune-role"></a>Intune ロールとは

Intune はデバイスの状態を評価し、管理します。

#### <a name="whats-the-exchange-server-role"></a>Exchange サーバー ロールとは

Exchange サーバーでは、デバイスを検疫に移動するための API とインフラストラクチャを提供しています。

> [!IMPORTANT]
> デバイスのコンプライアンスを評価できるようにするために、デバイスを使用するユーザーにコンプライアンス プロファイルと Intune ライセンスを割り当てる必要がある点に注意してください。 コンプライアンス ポリシーがユーザーに展開されていない場合、デバイスは準拠したものと見なされ、アクセス制限は適用されません。

## <a name="next-steps"></a>次の手順

[Azure Active Directory で条件付きアクセスを構成する方法](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[アプリベースの条件付きアクセス ポリシーを設定する](app-based-conditional-access-intune-create.md)

[Intune で On-Premises Exchange Connector をインストールする方法](exchange-connector-install.md)

[Exchange On-Premises の条件付きアクセス ポリシーを作成する方法](conditional-access-exchange-create.md)
