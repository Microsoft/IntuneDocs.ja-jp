---
title: Microsoft Intune での条件付きアクセス
titleSuffix: Microsoft Intune
description: 会社のリソースにアクセスするためにユーザー、デバイス、アプリが満たす必要のある条件を Microsoft Intune で定義する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188273"
---
# <a name="learn-about-conditional-access-and-intune"></a>条件付きアクセスと Intune について説明します

条件付きアクセスを使用すると、自分のメールや会社のリソースに接続できるデバイスやアプリを制御できます。 

Enterprise Mobility + Security (EMS) は、スタンドアロン製品ではありません。 これは、EMS の一部であるすべてのサービスと製品にかかわるソリューションです。 条件付きアクセスにより、会社のデータをセキュリティで保護するためのきめ細かいアクセスの制御を提供すると同時に、任意の場所と任意のデバイスで最適な仕事ができるエクスペリエンスをユーザーに提供します。

場所、デバイス、ユーザーの状態、アプリケーションの機密度に基づいて、会社のデータへのアクセスを制限する条件を定義できます。

> [!NOTE]
> 条件付きアクセスは、その機能を[Office 365 サービス](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access)にも拡張しています。

![条件付きアクセスの図](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Intune で条件付きアクセスを使用する

条件付きアクセスは、Azure Active Directory Premium ライセンスに含まれる Azure Active Directory の機能です。 Intune は、モバイル デバイス コンプライアンスとモバイル アプリ管理をソリューションに加えて、この機能を強化します。 

![EMS 使用時の Intune と条件付きアクセス](./media/conditional-access/intune-with-ca-1.png)

Intune での条件付きアクセスの使用方法:

- **デバイスベースの条件付きアクセス**

  - Exchange On-Premises の条件付きアクセス

  - ネットワーク アクセス制御に基づく条件付きアクセス

  - デバイスのリスクに基づく条件付きアクセス

  - Windows PC の条件付きアクセス

    - 企業所有

    - Bring Your Own Device (BYOD)

- **アプリベースの条件付きアクセス**

## <a name="next-steps"></a>次の手順

[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)
