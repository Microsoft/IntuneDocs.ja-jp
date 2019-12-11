---
title: JAMF Pro から Intune に送られるデータ
titleSuffix: Microsoft Intune
description: Jamf Pro を統合して Intune で Mac を管理する場合に、Jamf Pro から Microsoft Intune に送られるデータの一覧を確認します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4bf6df44335f3375d58d3c2c11da7cb3f982b3e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502421"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Jamf Pro から Intune に送られるデータ

Intune でエンドユーザーの Mac を管理する目的で [Jamf Pro](https://www.jamf.com) を使用するとき、Jamf Pro によって管理対象 macOS デバイスに関するインベントリ情報がキャプチャされます。 

## <a name="data"></a>データ  
Jamf Pro が Intune と共有するデータの一覧については、「[Appendix:Inventory Information Shared with Microsoft Intune (付録: Microsoft Intune と共有されるインベントリ情報)](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html)」(Jamf Pro 技術ドキュメント) を参照してください。 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>次の手順
Jamf で管理されるデバイスの削除方法については、[Jamf Pro のドキュメント](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)を参照してください。[Jamf サポート](https://www.jamf.com/support/)にサポート チケットを提出して、さらなる支援を受けることもができます。 

