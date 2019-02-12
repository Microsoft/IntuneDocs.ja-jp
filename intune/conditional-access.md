---
title: Microsoft Intune での条件付きアクセス | Microsoft Intune
description: 会社のリソースにアクセスするためにユーザー、デバイス、アプリが満たす必要のある条件を Microsoft Intune で定義する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a540d47d9b4418f7cf613fa401e92463d74a17fa
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838565"
---
# <a name="whats-conditional-access"></a>条件付きアクセスとは

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

条件付きアクセスとは、自分のメールや会社のリソースに接続することが許可されたデバイスやアプリを制御する手段です。 このトピックでは、デバイスベースやアプリベースの条件付きアクセスと、Intune で条件付きアクセスを利用する一般的なシナリオについて説明します。

Enterprise Mobility + Security (EMS) 条件付きアクセスはスタンドアロン製品ではありませんが、EMS の一部であるすべてのサービスと製品にかかわるソリューションです。 細かいアクセス制御を提供することで会社のデータをセキュリティで保護し、任意の場所と任意のデバイスで最適な仕事ができるエクスペリエンスをユーザーに提供します。

場所、デバイス、ユーザーの状態、アプリケーションの機密度に基づいて、会社のデータへのアクセスを制限する条件を定義できます。

> [!NOTE] 
> 条件付きアクセスは、その機能を[Office 365 サービス](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/)にも拡張しています。

![条件付きアクセスのアーキテクチャ ダイアグラム](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Intune での条件付きアクセス

条件付きアクセスは、Azure Active Directory Premium ライセンスに含まれる Azure Active Directory の機能です。 Intune は、モバイル デバイス コンプライアンスとモバイル アプリ管理をソリューションに加えて、この機能を強化します。 

![EMS 使用時の Intune と条件付きアクセス](./media/intune-with-ca-1.png)

Intune での条件付きアクセスの使用方法

-   **デバイスに基づく条件付きアクセス**

    -   Exchange On-Premises の条件付きアクセス

    -   ネットワーク アクセス制御に基づいた条件付きアクセス

    -   デバイスのリスクに基づいた条件付きアクセス

    -   Windows PC の条件付きアクセス

        -   企業所有

        -   Bring Your Own Device (BYOD)

-   **アプリベースの条件付きアクセス**

## <a name="next-steps"></a>次の手順

[Intune での条件付きアクセスの一般的な使用方法](conditional-access-intune-common-ways-use.md)
