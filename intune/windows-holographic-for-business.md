---
title: Microsoft Intune - Azure で Windows Holographic デバイスを管理する | Microsoft Docs
description: Windows Holographic for Business を実行しているデバイスで、Microsoft Intune を使用してさまざまな作業を完了できます。たとえば、ポータル サイトを構成したり、コンプライアンス ポリシーを作成したり、OMA-URI 設定をカスタマイズしたり、アプリをデプロイしたり、デバイスをグループに分類したり、デバイスを制限したり、ソフトウェア更新を有効にしたり、条件を設定したり、VPN 設定と Wi-F 設定を構成したり、Hello for Business を使用したりできます。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18f86580fc4c80fade7aeaa9678e9d8edac9a53e
ms.sourcegitcommit: b57be56524ddb5026fab94f7638dc516ed118325
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>Intune を使用して Windows Holographic を実行するデバイスをカスタマイズする

Microsoft Intune は、Windows Holographic for Business 実行する [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/) などのデバイスをサポートします。

Windows Holographic を実行しているデバイスを Microsoft Intune で管理するには、エディションのアップグレード プロファイルを作成する必要があります。 このアップグレード プロファイルによって、Windows Holographic から Windows Holographic for Business にデバイスがアップグレードされます。 Microsoft HoloLens の場合、Commercial Suite を購入してアップグレードに必要なライセンスを入手できます。 詳細については、「[Windows Holographic を実行するデバイスを Windows Holographic for Business にアップグレードする](holographic-upgrade.md)」を参照してください。

Windows Holographic for Business を実行しているデバイスを管理したり、カスタマイズしたりする際、この記事で紹介している操作が役に立ちます。 たとえば、ソフトウェア更新を管理したり、VPN 設定を構成したりできます。

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) は、Windows Holographic for Business を実行するデバイスの管理と制御に役立つ優れたリソースです。 Intune と Azure AD を使用して、次の操作を行うことができます。 

- **[Azure Active Directory に参加しているデバイスの設定](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup)**: Azure Active Directory (AD) では、Windows Holographic for Business を実行するデバイスを含む、職場所有の Windows 10 デバイスを追加することができます。 この機能を利用して、Azure AD でデバイスを制御することができます。 ユーザーがセキュリティとコンプライアンスの標準を満たすデバイスから会社のリソースにアクセスしていることを確認できます。

  詳細については、「[Azure Active Directory のデバイス管理の概要](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」を参照してください。

- **[Windows デバイスの一括登録](windows-bulk-enroll.md)**: Azure Active Directory (AD) と Intune に多数の新しい Windows デバイスを参加させることができます。 この機能は一括登録と呼ばれ、プロビジョニング パッケージを使用します。 これらのパッケージでは、Windows Holographic for Business を実行するデバイスを Azure AD テナントに参加させ、Intune に登録します。

## <a name="company-portal"></a>[ポータル サイト]
**[ポータル サイト アプリを構成する](company-portal-app.md)**

Intune には、ポータル サイトが含まれています。このサイトでユーザーは会社のデータにアクセスしたり、デバイスを登録したり、アプリをインストールしたり、IT 部署に連絡したりします。 Windows Holographic for Business を実行しているデバイスに合わせてポータル サイト アプリをカスタマイズできます。

## <a name="compliance-policy"></a>コンプライアンス ポリシー
**[デバイス コンプライアンス ポリシーの作成](compliance-policy-create-windows.md)**

コンプライアンス ポリシーは、デバイスで準拠する必要があるルールや設定です。 このようなポリシーと条件付きアクセスを利用し、非準拠のデバイスが会社のリソースにアクセスするのを阻止できます。 Intune では、Windows Holographic for Business を実行しているデバイスのアクセスを許可したり、禁止したりするためのコンプライアンス ポリシーを作成できます。 たとえば、Bitlocker を有効にすることを要求するポリシーを作成できます。

**[コンプライアンス ポリシーの概要](device-compliance-get-started.md)** に関するページも参照してください。

## <a name="deploy-and-manage-apps"></a>アプリの展開と管理
**[Intune にアプリを追加する](apps-add.md)**

Intune を使用し、Windows Holographic for Business を実行しているデバイスにアプリを追加できます。 アプリは次のようなさまざまな方法でデプロイできます。

- [Microsoft Store のアプリを追加する](store-apps-windows.md)
- [自分で開発したアプリを追加する](lob-apps-windows.md)
- [アプリをグループに割り当てる](apps-deploy.md)

Microsoft Intune では、Windows Holographic for Business を実行している Microsoft HoloLens デバイスにユニバーサル Windows アプリを展開することができます。 アプリ パッケージは、Intune Azure Portal で直接アップロードするか、またはビジネス向け Microsoft ストアから展開することができます。 関連する領域の詳細については、次を参照してください。
- Intune Azure Portal を使用して基幹業務 (LOB) アプリを展開するには、[Windows の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法](lob-apps-windows.md)に関するページを参照してください。
- ビジネス向け Microsoft ストアを使用してアプリを展開するには、「[ビジネス向け Microsoft ストアから購入したアプリを Microsoft Intune で管理する方法](windows-store-for-business.md)」を参照してください。 
- Microsoft Intune でのアプリの管理については、[Microsoft Intune アプリの管理](app-management.md)に関するページを参照してください。
- Microsoft HoloLens 用アプリの開発の詳細については、「[Microsoft HoloLens のための複合現実アプリ](https://www.microsoft.com/hololens/apps)」を参照してください。 

> [!NOTE]
> Windows 10 Holographic for Business 1607 を実行している HoloLens デバイスでは、ビジネス向け Microsoft ストアからのオンライン ライセンス アプリをサポートしていません。 詳細については、「[HoloLens へのアプリのインストール](https://docs.microsoft.com/en-us/hololens/hololens-install-apps)」を参照してください。

## <a name="device-actions"></a>デバイス アクション
Intune にはいくつかの組み込みアクションがあります。これにより、IT 管理者は、デバイス上でローカルに、あるいは Azure Portal の Intune を使用してリモートで、さまざまなタスクを実行できます。 ユーザーは、Intune に登録済みの個人所有デバイスに Intune ポータル サイトからリモート コマンドを発行することもできます。

Windows Holographic for Business を実行するデバイスを使用する場合、次のアクションを使用できます。 

- **[出荷時の設定にリセット](devices-wipe.md#factory-reset)**: **[出荷時の設定にリセット]** アクションでは、Intune からデバイスを削除し、デバイスを出荷時の既定設定に復元します。 デバイスを新しいユーザーに割り当てる前に、あるいはデバイスの紛失時や盗難時に、このアクションを使用します。

- **[会社データを削除する](devices-wipe.md#remove-company-data)**: **[会社データを削除する]** アクションでは、Intune からデバイスを削除し、管理対象のアプリ データ、設定、Intune で割り当てられている電子メール プロファイルを削除します。 ユーザーの個人データはデバイスに保持されます。

- **[デバイスを同期して最新のポリシーと操作を取得する](device-sync.md)**: **[同期]** アクションでは、デバイスが Intune ですぐにチェックインするよう強制します。 デバイスは、チェックインするとすぐに、割り当てられているポリシーまたは保留中のアクションを受け取ります。 この機能は、次のスケジュールされたチェックインを待つことなく、割り当てられたポリシーの検証およびトラブルシューティングに役立ちます。

「**[Microsoft Intune デバイスの管理とは](device-management.md)**」は、Azure Portal を使用するデバイスの管理について学習する際に役立つリソースです。 

## <a name="device-categories-and-groups"></a>デバイスのカテゴリとグループ
**[デバイスをグループに分類する](device-group-mapping.md)**

Intune を使用してデバイスのカテゴリを作成し、営業、経理、人事など、自分で作成したカテゴリに基づいてデバイスをグループに自動追加できます。 このようにカテゴリを利用することで、Windows Holographic for Business を実行しているデバイスの管理が簡単になります。

## <a name="device-configuration-profiles"></a>デバイスの構成プロファイル 
**[構成プロファイルの概要](device-profiles.md)と[独自のプロファイルの作成](device-profile-create.md)**

Intune には、組織内のさまざまなデバイスで有効または無効にできる設定と機能が含まれています。 これらの設定と機能は、プロファイルを使用して管理されます。 たとえば、Cortana を有効にするプロファイルや、Windows Holographic for Business を実行しているデバイスで Windows Defender SmartScreen を使用するプロファイルを作成できます。

プロファイルでは、OMA-URI を使用し、一部の設定をカスタマイズしたり、デバイス制限を作成したり、VPN (仮想プライベート ネットワーク) や Wi-Fi を構成したりできます。

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[カスタム デバイス設定](custom-settings-windows-holographic.md)

OMA-URI (Open Mobile Alliance Uniform Resource Identifier) 設定を構成するために、Intune でカスタム プロファイルを作成できます。 OMA-URI 設定を利用し、Windows Holographic for Business のさまざまな機能を制御できます。たとえば、VPN を有効にしたり、Microsoft Update の更新プログラムを確認したりできます。

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[デバイスの制限](device-restrictions-windows-holographic.md)

デバイスの制限では、デバイスのさまざまな設定や機能を制御できます。たとえば、パスワードを要求したり、[Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps) からアプリをインストールしたり、Bluetooth を有効にしたりできます。 このような制限は Intune プロファイルで作成されます。 このプロファイルは、Windows Holographic for Business を実行している複数のデバイスに適用できます。

#### <a name="configure-vpnvpn-settings-configuremd"></a>[VPN を構成する](vpn-settings-configure.md)

仮想プライベート ネットワーク (VPN) を使用すると、会社のユーザーが社内ネットワークにリモート アクセスする際にセキュリティで保護することができます。 Intune では、Windows Holographic for Business を実行しているデバイスに固有の設定が含まれる VPN プロファイルを作成できます。 たとえば、すべての Windows Holographic for Business デバイスが接続の種類に Citrix VPN を利用するように VPN プロファイルを作成できます。

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Wi-Fi を構成する](wi-fi-settings-configure.md)

Intune で Wi-Fi プロファイルを作成し、お使いの Windows Holographic for Business デバイスに無線ネットワーク設定を割り当てることもできます。 Wi-Fi プロファイルを割り当てると、エンド ユーザーはネットワークを構成しなくても企業のネットワークにアクセスできます。 たとえば、お使いの Windows Holographic for Business デバイス専用の Wi-Fi ネットワークを作成できます。

## <a name="software-updates"></a>ソフトウェア更新プログラム
**[ソフトウェア更新プログラムの管理](windows-update-for-business-configure.md)**

Intune には、Windows 10 デバイス用に、更新プログラム リングと呼ばれている機能があります。 更新プログラム リングには、更新プログラムのインストール方法を決定する一連の設定が含まれています。 たとえば、更新プログラムをインストールするためのメンテナンス期間を作成したり、更新プログラムのインストール後に再起動を選択したりできます。 更新プログラム リングは、Windows Holographic for Business を実行している複数のデバイスに適用できます。

## <a name="terms-and-conditions"></a>Intune の登録および会社アクセスに関する使用条件
**[ユーザー アクセスに関する会社の使用条件を設定する](terms-and-conditions-create.md)**

ユーザーがデバイスを登録したり、会社のアプリにアクセスしたりする前に、会社の使用条件に同意するように要求できます。 Intune では、ポータル サイトに使用条件を表示する方法を定義できます。また、Windows Holographic for Business を実行しているデバイスに使用条件を割り当てることができます。

## <a name="windows-hello-for-business"></a>Windows Hello for Business
**[Windows Hello for Business を使用する](windows-hello.md)**

Hello for Business は、Azure Active Directory アカウントを使った代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードに取って代わります。 Hello for Business を利用すれば、お使いの Windows Holographic for Business デバイスは、自分で最小長を設定した PIN でサインインできます。
