---
title: "Intune での条件付きアクセス"
titlesuffix: Azure portal
description: "Intune での条件付きアクセスの一般的な使用方法"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d3509dbf1bc0b415803bb003c342f5b5df69e235
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="common-ways-to-use-conditional-access-with-intune"></a>Intune での条件付きアクセスの一般的な使用方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

組織における条件付きアクセスのコンプライアンスを推進するには、Intune モバイル デバイス コンプライアンス ポリシーと Intune モバイル アプリケーション管理 (MAM) の機能を構成する必要があります。 Intune での条件付きアクセスの一般的な使用方法について説明します。

## <a name="device-based-conditional-access"></a>デバイス ベースの条件付きアクセス

Intune と Azure Active Directory が連携することで、管理されたデバイスと準拠デバイスのみが電子メール、Office 365 サービス、サービスとしてのソフトウェア (SaaS) アプリ、および[オンプレミス アプリ](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)にアクセスできるようになります。 また、Azure Active Directory では、ドメインに参加しているコンピューターや、Intune に登録されているモバイル デバイスのみが Office 365 サービスにアクセスできるようにするポリシーを設定できます。

Intune には、デバイスのコンプライアンス対応状態を評価する、デバイス コンプライアンス ポリシーの機能があります。 コンプライアンス対応状態は Azure Active Directory に報告され、ユーザーが会社のリソースにアクセスしようとしたときに、Azure Active Directory で作成された条件付きアクセスのポリシーを適用するために使用されます。

[新しい Azure Portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)では、Exchange Online や他の Office 365 製品のデバイス ベースの条件付きアクセス ポリシーが Azure Portal で構成されるようになります。

-   Azure Active Directory の条件付きアクセスについて詳しくは、[こちら](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)をご覧ください。

-   Intune のデバイス コンプライアンスについて詳しくは、[こちら](device-compliance.md)をご覧ください。

-   Intune で条件付きアクセスを使用した、電子メール、Office 365、およびその他のサービスの保護について詳しくは、[こちら](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)をご覧ください。

### <a name="conditional-access-for-exchange-on-premises"></a>Exchange On-Premises の条件付きアクセス

条件付きアクセスを使用すると、デバイス コンプライアンス ポリシーと登録状態に基づいて、**Exchange On-Premises** へのアクセスを許可またはブロックすることができます。 条件付きアクセスをデバイス コンプライアンス ポリシーと組み合わせて使用した場合は、準拠デバイスのみが Exchange On-Premises へのアクセスを許可されます。

条件付きアクセスの詳細設定を構成して、次のような細かい制御を行うことができます。

-   特定のプラットフォームを許可またはブロックする。

-   Intune で管理されていないデバイスを即時ブロックする。

デバイス コンプライアンスと条件付きアクセス ポリシーが適用されると、Exchange On-Premises へのアクセスで使用されるデバイスがチェックされます。

デバイスが条件を満たしていない場合、エンド ユーザーは、デバイス非準拠の原因である問題を修正するためのデバイス登録プロセスを提示されます。

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange On-Premises の条件付きアクセスのしくみ

Intune Exchange Connector は Exchange サーバーに存在するすべての Exchange Active Sync (EAS) レコードを収集するため、Intune はこれらの EAS レコードを取得して、Intune デバイス レコードにマップすることができます。 これらのレコードはデバイスに登録され、Intune によって認識されます。 このプロセスにより、電子メールへのアクセスが許可またはブロックされます。

EAS レコードが新しいために Intune が認識しない場合、Intune は電子メールへのアクセスをブロックするコマンドレットを発行します。 次の図で、このプロセスのしくみについて詳しく説明します。

![Exchange On-premises と条件付きアクセス (CA) のフローチャート](./media/ca-intune-common-ways-1.png)

1.  ユーザーは、Exchange On-premises 2010 SP1 以降でホストされている会社の電子メールにアクセスしようとしています。

2.  デバイスが Intune で管理されていない場合は、電子メールへのアクセスがブロックされます。 Intune は、EAS クライアントにブロック通知を送信します。

3.  EAS はブロック通知を受信し、該当デバイスを検疫に移動して、検疫メールを送信します。このメールには、ユーザーがデバイスを登録するためのリンクを含む修復手順が記載されています。

4.  Workplace Join プロセスが発生します。これは、Intune でデバイスを管理する最初の手順です。

5.  デバイスが Intune に登録されます。

6.  Intune により EAS レコードとデバイス レコードがマップされ、デバイスのコンプライアンス対応状態が保存されます。

7.  Azure AD Device Registration プロセスにより EAS クライアント ID が登録され、Intune デバイス レコードと EAS クライアント ID の間のリレーションシップが作成されます。

8.  Azure AD Device Registration により、デバイスの状態に関する情報が保存されます。

9.  ユーザーが条件付きアクセス ポリシーを満たしている場合、Intune は Intune Exchange Connector を介して、メールボックスの同期を許可するコマンドレットを発行します。

10. Exchange サーバーが EAS クライアントに通知を送信し、ユーザーは電子メールにアクセスできるようになります。

#### <a name="whats-the-intune-role"></a>Intune ロールとは

Intune はデバイスの状態を評価し、管理します。

#### <a name="whats-the-exchange-server-role"></a>Exchange サーバー ロールとは

Exchange サーバーは、デバイスを検疫に移動するための API とインフラストラクチャを提供します。

> [!IMPORTANT]
> デバイスのコンプライアンスを評価するために、デバイスを使用するユーザーにコンプライアンス プロファイルを割り当てる必要がある点に注意してください。 コンプライアンス ポリシーがユーザーに展開されていない場合、デバイスは準拠したものと見なされ、アクセス制限は適用されません。

### <a name="conditional-access-based-on-network-access-control"></a>ネットワーク アクセス制御に基づいた条件付きアクセス

Cisco ISE、Aruba Clear Pass、Citrix NetScaler などのパートナーと統合された Intune は、Intune 登録とデバイスのコンプライアンス対応状態に基づいたアクセス制御を提供します。

ユーザーが会社の Wi-Fi や VPN リソースにアクセスしようとすると、デバイスが管理されているか、Intune デバイス コンプライアンス ポリシーに準拠しているかどうかに基づいて、アクセスが許可または拒否されます。

-   NAC と Intune の統合について詳しくは、[こちら](network-access-control-integrate.md)をご覧ください。

### <a name="conditional-access-based-on-device-risk"></a>デバイスのリスクに基づいた条件付きアクセス

Intune は、モバイル デバイス上のマルウェア、トロイの木馬、およびその他の脅威を検出するためのセキュリティ ソリューションを提供する Mobile Threat Defense ベンダーと提携しました。

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune と Mobile Threat Defense の統合のしくみ

モバイル デバイスに Mobile Threat Defense エージェントがインストールされると、モバイル デバイスで脅威が検出されたかどうかに関するコンプライアンス対応状態のメッセージが、エージェントから Intune に返信されます。

Intune と Mobile Threat Defense の統合は、デバイスのリスクに基づいた条件付きアクセスの決定において重要な役割を果たします。

-   Intune Mobile Threat Defense について詳しくは、[こちら](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense)をご覧ください。

### <a name="conditional-access-for-windows-pcs"></a>Windows PC の条件付きアクセス

PC の条件付きアクセスでは、モバイル デバイスで利用できる機能と同様の機能が提供されます。 Intune で PC を管理する場合に条件付きアクセスを使用する方法について説明します。

#### <a name="corporate-owned"></a>企業所有

-   **オンプレミス AD ドメインへの参加:** AD のグループ ポリシーや System Center Configuration Manager を使用して PC をすでに管理しているという事実に満足している組織にとって、これはもっとも一般的な条件付きアクセスの展開オプションです。

-   **Azure AD ドメインへの参加と Intune の管理:** このシナリオは、Choose Your Own Device (CYOD) と、ローミング ラップトップを会社のネットワークにほとんど接続しないシナリオを対象にしています。 デバイスは Azure AD に参加し、Intune に登録されます。これにより、オンプレミス AD とドメイン コントローラーへの依存が排除されます。 会社のリソースにアクセスする場合は、これを条件付きアクセスの基準として使用できます。

-   **AD ドメインへの参加と System Center Configuration Manager:** 現在のブランチでは、System Center Configuration Manager は、ドメインに参加している PC とするのに加え、次の特定のコンプライアンス基準を評価できる条件付きアクセスの機能を提供します。

    -   PC が暗号化されているか。

    -   マルウェアがインストールされているか。 PC は最新の状態か。

    -   デバイスが脱獄またはルート化されているか。

#### <a name="bring-your-own-device-byod"></a>Bring Your Own Device (BYOD)

-   **Workplace Join と Intune 管理:** この場合、ユーザーは個人のデバイスを参加させて、会社のリソースやサービスにアクセスできます。 Workplace Join を使用し、デバイスを Intune に登録して、デバイスレベルのポリシーを受け取ることができます。これは、条件付きアクセスの基準を評価する別のオプションでもあります。

## <a name="app-based-conditional-access"></a>アプリベースの条件付きアクセス

Intune と Azure Active Directory が連携することで、管理対象アプリのみが会社の電子メールやその他の Office 365 サービスにアクセスできるようになります。

-   Intune を使用したアプリ ベースの条件付きアクセスについて詳しくは、[こちら](app-based-conditional-access-intune.md)をご覧ください。

## <a name="next-steps"></a>次のステップ

[Azure Active Directory で条件付きアクセスを構成する方法](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Intune で On-Premises Exchange Connector をインストールする方法](https://docs.microsoft.com/intune/exchange-connector-install)

[Exchange On-Premises の条件付きアクセス ポリシーを作成する方法](conditional-access-exchange-create.md)
