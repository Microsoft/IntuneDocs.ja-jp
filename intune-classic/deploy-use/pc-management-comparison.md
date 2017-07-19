---
title: "Windows PC 管理オプションの比較"
description: "Apple Device Enrollment Program (DEP) または Apple Configurator を使用した会社所有の iOS デバイスの登録"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 560ce922fa58e759157358c6b7348fe0388ce408
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Windows PC のコンピューターとしての管理とモバイル デバイスとしての管理の比較

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

組織では Microsoft Intune を使用して、モバイル デバイス管理 (MDM) によりモバイル デバイスとして、または Intune ソフトウェア クライアントによりコンピューターとして、Windows PC を管理できます。  Microsoft では、可能な場合は常に MDM 管理ソリューションを使用することをお勧めします。 これらのオプションの相違点を理解するために、次の表で 2 つの管理オプションを比較しています。

|**機能やシナリオ** |**コンピューターとしての Windows**<br>Intune ソフトウェア クライアント | **モバイル デバイスとしての Windows**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**オペレーティング システム** |Windows 10、Windows 8+、Windows 7、Windows Vista | Windows 10+ |
|**Intune ポータルのサポート** |[Silverlight コンソール](https://manage.microsoft.com)|[Azure Portal](https://portal.azure.com) |
|**条件付きアクセス**|利用不可|利用可能 <br>[条件付きアクセスとは](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**一括登録**|利用不可|利用可能 <br>[Windows デバイスの一括登録](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**デバイス プロファイル**|利用不可|利用可能 <br>[Microsoft Intune のデバイス プロファイルとは](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**エージェントレスの登録**|利用不可 |利用可能<br>[Windows デバイスの登録](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**ソフトウェア更新管理**| Windows の更新プログラムと Microsoft アプリの更新プログラム<br>[ソフトウェア更新プログラムを使用して Windows PC を最新の状態に保つ](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Windows 10 と Microsoft アプリの更新プログラム用のビジネス向け Microsoft ストア<br> [ビジネス設定向けの Windows Update の構成](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**ソフトウェア ライセンスの管理**|利用可能 <br>[Windows PC ソフトウェアのライセンス契約を管理する](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|ビジネス向け Microsoft ストア (.appx アプリのみ)<br>[ビジネス向け Windows ストアから購入したアプリを管理する](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**インベントリ**|利用可能 <br>[Windows PC のハードウェアとソフトウェアのインベントリを表示する](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|利用可能 <br>[アプリ情報を監視する方法](https://docs.microsoft.com/intune/apps-monitor)<br>[デバイス管理とは](https://docs.microsoft.com/intune/device-management)|
|**Windows ファイアウォールのポリシー**|利用可能 <br>[Windows ファイアウォール ポリシーを使用して Windows PC を保護する](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |利用不可|
|**マルウェア対策**|Endpoint Protection<br>[Endpoint Protection を使用した Windows PC の保護](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Windows Defender の設定](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**リモート アシスタンス** |TeamViewer<br>[Windows PC のリモート アシスタンス要求と提供](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|利用不可 |
|**アプリの展開** | ビジネス向け Microsoft ストアでは使用できません。<br>.exe、.appx、マルチファイル .msi のみ<br>[Intune ソフトウェア クライアントを実行している Windows PC にアプリを追加する](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Microsoft ストア アプリと基幹業務アプリに使用可能<br>[Windows ストア アプリを追加する方法](https://docs.microsoft.com/intune-azure/manage-apps/windows-store-app)<br>Microsoft アプリ展開と Win32 アプリが近日公開予定 |
|**アプリ保護**|利用不可|利用可能 <br>[アプリ保護ポリシーとは](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows PC 管理の利点
最新のモバイル デバイス管理での Windows PC 管理には、次の利点があります。
- **スケーラビリティ** - MDM 管理は Intune クラウド管理とともに拡張します。 Intune ソフトウェア クライアントの制限は、PC 7,000 台までです。
- **簡単** - ダウンロード済みのソフトウェア クライアントに依存せず、オペレーティング システムに含まれる最新の管理機能を使用します。
- **整合性** - お使いの Windows PC は組織内の他のすべてのモバイル デバイスと同様に管理されます。
<!-- - **Cloud optimization** - -->
