---
title: モバイル デバイス管理機関の設定
titlesuffix: Microsoft Intune
description: Intune でモバイル デバイス管理機関を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce6464cc6aa67636743479e69ad2b55c9b102ed9
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2018
---
# <a name="set-the-mobile-device-management-authority"></a>モバイル デバイス管理機関の設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

可能な構成は以下のとおりです。

- **Intune スタンドアロン** - Azure Portal を利用して構成する、クラウドのみの管理。 Intune で提供される機能がすべて含まれます。 [Intune コンソールで MDM 機関を設定](#set-mdm-authority-to-intune)します。

- **Intune ハイブリッド** - Intune クラウド ソリューションと System Center Configuration Manager の統合。 Configuration Manager コンソールを使用して Intune を構成します。 [Configuration Manager で MDM 機関を設定](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)します。

- **Office 365 のモバイル デバイス管理** - Office 365 と Intune クラウド ソリューションの統合。 Office 365 管理センターから Intune を構成します。 Intune スタンドアロンで利用できる機能の一部が含まれます。 Office 365 管理センターで MDM 機関を設定します。

>[!IMPORTANT]    
Configuration Manager 1610 以降のバージョンと Microsoft Intune バージョン 1705 では、MDM 機関の変更にあたって Microsoft サポートに問い合わせる必要はありません。また、既存の管理されたデバイスの登録を解除して再登録する必要もありません。 詳細については、「[不適切な MDM 機関の設定を選択した場合の対処方法](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting)」を参照してください。

## <a name="set-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
2. オレンジのバナーを選択し、**[モバイル デバイス管理機関]** 設定を開きます。
3. **[モバイル デバイス管理機関]** で、次の選択肢から MDM 機関を選択します。
  - **Intune MDM 機関**
  - **Configuration Manager MDM 機関**
  - **なし**

  ![Intune のモバイル デバイス管理機関設定画面のスクリーンショット](media/set-mdm-auth.png)

  MDM 機関が Intune に正しく設定されたことを示すメッセージが表示されます。

## <a name="enable-device-enrollment"></a>デバイスの登録を可能にする

Intune が MDM 機関として設定されると、ユーザーは個人所有デバイスを登録し、メールなどのリソースにアクセスできます。それには、ポータル サイトをインストールするか (iOS と Android)、仕事の資格情報を追加するか (Windows)、会社のポータル Web サイトにアクセスします (iOS、Android、macOS)。

登録を有効に、または簡単にするために、各種プラットフォームで次のような要件があります。
- **iOS** - (必須) [Apple MDM プッシュ証明書を取得し](apple-mdm-push-certificate-get.md)、[会社所有 iOS デバイスの登録を有効にします](ios-enroll.md) (任意)。
- **Android** - (任意) [Android の仕事用プロファイルを有効にします](android-enroll.md)。
- **Windows** - (任意) [自動登録](windows-enroll.md)または[一括登録](windows-bulk-enroll.md)を有効にします。
- **macOS** - (必須) [Apple MDM プッシュ証明書を取得します](apple-mdm-push-certificate-get.md)。


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。
