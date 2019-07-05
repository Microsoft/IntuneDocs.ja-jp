---
title: Windows デバイスの Intune 登録方法
titleSuffix: Microsoft Intune
description: Windows デバイスを Intune に登録するさまざまな方法について学習します
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: b8b1c47e4a2eb46bb8f7190ede351ed77a1bfef4
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494493"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Windows デバイスの Intune 登録方法

Intune でデバイスを管理するには、まず、デバイスを Intune サービスに登録する必要があります。 個人所有デバイスと会社所有デバイスの両方を、Intune 管理用に登録することができます。 

デバイスを Intune に登録する方法には、次の 2 つがあります。
- ユーザーが Windows PC を自己登録できる 
- 管理者が、ユーザーの介入なしの自動登録を強制するようにポリシーを構成できる

## <a name="user-self-enrollment-in-intune"></a>Intune のユーザーの自己登録

ユーザーは、以下の方法のいずれかを使用して、Windows デバイスを自己登録することができます。

- [Bring Your Own Device (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device):ユーザーは、デバイスの **[設定]** から**職場と学校**のアカウントを接続するよう選択して、個人所有デバイスを登録します。 このプロセスでは、次のことを行います。
    - Azure Active Directory にデバイスを登録して、メールなどの企業リソースにアクセスできるようにする。
    - デバイスを個人所有デバイス (BYOD) として、Intune に登録する。
管理者が自動登録 (Azure AD Premium サブスクリプションで利用可能) を構成している場合、ユーザーが資格情報を入力する必要があるのは 1 回のみとなります。 それ以外の場合、MDM の登録のみで個別に登録し、資格情報を再入力する必要があります。  
- **MDM の登録のみ**では、ユーザーは、既存のワークグループ、Active Directory、または Azure Active Directory に参加済みの PC を Intune に登録することができます。 ユーザーは、既存の Windows PC で [設定] から登録します。 この方法は、デバイスが Azure Active Directory に登録されないため、お勧めできません。 条件付きアクセスなどの機能も使用できません。
- [Azure Active Directory (Azure AD) に参加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) - デバイスを Azure Active Directory に参加させ、ユーザーが Azure AD 資格情報を使用して、Windows にサインインできるようにします。 自動登録が有効になっている場合、デバイスは Intune に自動的に登録されます。 自動登録の利点は、ユーザーの単一ステップ プロセスです。 それ以外の場合、MDM の登録のみで個別に登録し、資格情報を再入力する必要があります。 ユーザーは、[設定] からまたは最初の Windows OOBE 時に、この方法で登録します。 デバイスは、Intune で会社所有デバイスとしてマークされます。
- [Autopilot](enrollment-autopilot.md) - Azure AD 参加を自動化し、新しい企業所有デバイスを Intune に登録します。 この方法では、Out-of-Box Experience が簡略化され、カスタム オペレーティング システム イメージをデバイスに適用する必要がなくなります。 管理者は、Intune を使用して Autopilot デバイスを管理する場合、ポリシー、プロファイル、アプリなどを登録後に管理することができます。  Autopilot の展開の種類には次の 4 種類があります。[自己展開モード](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (キオスク、デジタル信号、または共有デバイスの場合)、[ユーザー駆動型モード](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (従来のユーザーの場合)、[ホワイト グローブ] (https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) (パートナーまたは IT スタッフは Windows 10 PC が完全に構成されビジネスに即応できるように、それを事前プロビジョニングすることができる)、[既存のデバイス向け Autopilot] (https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) (最新バージョンの Windows 10 をご利用の既存のデバイスに簡単に展開できる)。

## <a name="administrator-based-enrollment-in-intune"></a>Intune の管理者ベースの登録

管理者は、ユーザーの介入を必要としない、次の登録方法を設定できます。

- [Hybrid Azure AD Join](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) では、管理者は、ハイブリッド Azure AD 参加済みのデバイスを自動的に登録するように Active Directory グループ ポリシーを構成できます。 
- [Configuration Manager の共同管理](https://docs.microsoft.com/sccm/comanage/overview)では、管理者は、既存の Configuration Manager マネージド デバイスを Intune に登録して、Intune と Configuration Manager の 2 つの利点を得ることができます。 
- [デバイス登録マネージャー](device-enrollment-manager-enroll.md) (DEM) は特別なサービス アカウントです。 DEM アカウントには、許可されているユーザーが複数の会社所有デバイスを登録して管理できるようにするアクセス許可があります。 この種のデバイスは、POS アプリやユーティリティ アプリなどには適していますが、電子メールや会社のリソースにアクセスする必要があるユーザーには適していません。 この方法では、条件付きアクセスなどの機能の使用が許可されません。 
- [一括登録](windows-bulk-enroll.md)では、許可されているユーザーは、数多くの新しい企業所有デバイスを Azure Active Directory と Intune に参加させることができます。 Windows Configuration Designer (WCD) アプリでプロビジョニング パッケージを作成します。 その後、既存の Windows PC からまたは最初の Windows OOBE エクスペリエンス時に USB メディアを使用して、プロビジョニング パッケージをインストールし、デバイスを Intune に自動的に登録します。 この方法では、条件付きアクセスの使用が許可されません。 
- [Windows IoT Core デバイスの登録](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment)を行うには、Windows IoT Core ダッシュボードを使用してデバイスを準備してから、Windows Configuration Designer を使用してプロビジョニング パッケージを作成します。 次に、初回起動時に SD カード メディアを使用して、プロビジョニング パッケージをインストールしてデバイスを Intune に自動登録します。

## <a name="next-steps"></a>次の手順

[Windows の登録方法の機能について学習する](enrollment-method-capab.md)
