---
title: Windows PC 管理オプションの比較
titlesuffix: Microsoft Intune
description: Apple Device Enrollment Program (DEP) または Apple Configurator を使用した会社所有の iOS デバイスの登録
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c70dbee01c546f73052b8741ce339c7bfe92fc7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461143"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Windows PC のコンピューターとしての管理とモバイル デバイスとしての管理の比較

[!INCLUDE [classic-portal](includes/classic-portal.md)]

組織では Microsoft Intune を使用して、モバイル デバイス管理 (MDM) によりモバイル デバイスとして、または Intune ソフトウェア クライアントによりコンピューターとして、Windows PC を管理できます。  Microsoft では、可能な場合は常に MDM 管理ソリューションを使用することをお勧めします。 これらのオプションの相違点を理解するために、次の表で 2 つの管理オプションを比較しています。

|**機能やシナリオ** |**コンピューターとしての Windows**<br>Intune ソフトウェア クライアント | **モバイル デバイスとしての Windows**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**オペレーティング システム** |Windows 10、Windows 8+、Windows 7、Windows Vista | Windows 10+ |
|**Intune ポータルのサポート** |[Silverlight コンソール](https://manage.microsoft.com)|[Azure Portal](https://portal.azure.com) |
|**条件付きアクセス**|利用不可|利用可能 <br>[条件付きアクセスとは](conditional-access.md)|
|**一括登録**|利用不可|利用可能 <br>[Windows デバイスの一括登録](windows-bulk-enroll.md)|
|**デバイス プロファイル**|利用不可|利用可能 <br>[Microsoft Intune のデバイス プロファイルとは](device-profiles.md)|
|**エージェントレスの登録**|利用不可 |利用可能<br>[Windows デバイスの登録](windows-enroll.md)|
|**ソフトウェア更新管理**| Windows の更新プログラムと Microsoft アプリの更新プログラム<br>[ソフトウェア更新プログラムを使用して Windows PC を最新の状態に保つ](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Windows 10 と Microsoft アプリの更新プログラム用のビジネス向け Microsoft ストア<br> [ビジネス設定向けの Windows Update の構成](windows-update-for-business-configure.md) |
|**ソフトウェア ライセンスの管理**|利用可能 <br>[Windows PC ソフトウェアのライセンス契約を管理する](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|ビジネス向け Microsoft ストア (.appx アプリのみ)<br>[ビジネス向け Microsoft ストアから購入したアプリの管理](windows-store-for-business.md)|
|**インベントリ**|利用可能 <br>[Windows PC のハードウェアとソフトウェアのインベントリを表示する](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|利用可能 <br>[アプリ情報を監視する方法](apps-monitor.md)<br>[デバイス管理とは](device-management.md)|
|**Windows ファイアウォールのポリシー**|利用可能 <br>[Windows ファイアウォール ポリシーを使用して Windows PC を保護する](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |利用可能 <br>[Windows Defender ファイアウォール](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**マルウェア対策**|Endpoint Protection<br>[Endpoint Protection を使用した Windows PC の保護](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[Windows Defender を有効にする](advanced-threat-protection.md)|
|**リモート アシスタンス** |TeamViewer<br>[Windows PC のリモート アシスタンス要求と提供](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [TeamViewer を使用して、Intune デバイスをリモートで管理する](device-profile-android-teamviewer.md) |
|**アプリの展開** | ビジネス向け Microsoft ストアでは使用できません。<br>.exe、.appx、マルチファイル .msi のみ<br>[Intune ソフトウェア クライアントを実行している Windows PC にアプリを追加する](add-apps-for-windows-pcs-in-microsoft-intune.md)|Microsoft ストア アプリと基幹業務アプリに使用可能<br>[Windows ストア アプリを追加する方法](store-apps-windows.md)<br>[Windows の基幹業務 (LOB) アプリを Microsoft Intune に追加する方法](lob-apps-windows.md)|
|**アプリ保護**|利用不可|利用可能 <br>[アプリ保護ポリシーとは](app-protection-policy.md)|
|**正常性構成証明書**|利用不可|利用可能|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows PC 管理の利点
最新のモバイル デバイス管理での Windows PC 管理には、次の利点があります。
- **スケーラビリティ** - MDM 管理は Intune クラウド管理とともに拡張します。 Intune ソフトウェア クライアントの制限は、PC 7,000 台までです。
- **簡単** - ダウンロード済みのソフトウェア クライアントに依存せず、オペレーティング システムに含まれる最新の管理機能を使用します。
- **整合性** - お使いの Windows PC は組織内の他のすべてのモバイル デバイスと同様に管理されます。
<!-- - **Cloud optimization** - -->
