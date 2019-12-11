---
title: Intune で Android デバイスを登録する
titleSuffix: Microsoft Intune
description: Intune で Android デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff005ddded4178801e7e334f604280ef4408aaff
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505667"
---
# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 管理者は、次の方法で Android デバイスを登録できます。
- Android Enterprise (最新のセキュリティで保護された機能をユーザーに提供する一連の登録オプションがあります)。
    - [**Android Enterprise 仕事用プロファイル**](android-work-profile-enroll.md):会社のデータにアクセスする権限が与えられた個人用デバイス用です。 管理者は職場のアカウント、アプリ、データにアクセスできます。 デバイスに入っている個人のデータは仕事のデータから分離され、個人の設定やデータが管理者に操作されることはありません。 
    - [**Android Enterprise 専用**](android-kiosk-enroll.md):デジタル サイネージ、チケット印刷、在庫管理など、会社が所有する単一用途のデバイス用です。 管理者はデバイスの使用を厳しく管理し、限られたアプリと Web リンクのみ許可します。 また、ユーザーがデバイスに他のアプリを追加したり、他の操作を行ったりできないようになっています。
    - [**Android Enterprise フル マネージド**](android-fully-managed-enroll.md):仕事のためにのみ使用し、私事には使用しない会社所有の単一ユーザー デバイス用です。 管理者はデバイス全体を管理し、仕事用プロファイルで利用できないポリシー制御を強制できます。 
- [**Android デバイス管理者**](android-enroll-device-administrator.md) (Samsung KNOX Standard デバイスと [Zebra デバイス](../configuration/android-zebra-mx-overview.md)を含みます)。 

## <a name="prerequisites"></a>必要条件

モバイル デバイスの管理を準備するには、MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](../fundamentals/mdm-authority-set.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。

Zebra Technologies 製のデバイスの場合、特定のデバイスの機能に応じて、ポータル サイトの追加のアクセス許可を付与しなければならない場合があります。 詳細については、[Zebra デバイス上のモビリティの拡張機能](../configuration/android-zebra-mx-overview.md)に関するページを参照してください。

Samsung KNOX Standard デバイスの場合は、[追加の前提条件](android-samsung-knox-mobile-enroll.md)があります。

## <a name="next-steps"></a>次の手順

- [Android Enterprise の仕事用プロファイルの登録を設定する](android-work-profile-enroll.md)
- [Android Enterprise の専用デバイスの登録を設定する](android-kiosk-enroll.md)
- [Android Enterprise のフル マネージドの登録を設定する](android-fully-managed-enroll.md)
- [Android デバイス管理者登録を設定する](android-enroll-device-administrator.md)

