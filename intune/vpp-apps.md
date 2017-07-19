---
title: "Intune によるボリューム購入アプリとブックの管理"
titleSuffix: Intune on Azure
description: "Intune を使用して、ストアからのボリューム購入アプリとブックの使用状況を管理および監視する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 85b07f57-661a-4bc8-87d2-7b446d5cf4d6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e8f938e81740d1bb08e0e9995cab94329c2fe5e7
ms.sourcegitcommit: c9b3a95bf529b6cb2a2bdacbc49127dfa0c233e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2017
---
# <a name="manage-volume-purchased-apps-and-books-with-microsoft-intune"></a>Microsoft Intune によるボリューム購入アプリとブックの管理

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>概要

一部のアプリ ストアでは、社内で使用するアプリやブックの複数のライセンスを購入できます。 ライセンスの一括購入は、購入したアプリとブックの複数コピーを追跡する管理オーバーヘッドを削減するのに役立ちます。

Microsoft Intune を使用することで、このようなプログラムを通じて購入したアプリとブックを管理できます。 ストアからライセンス情報をインポートし、使用したライセンスの数を追跡できます。 このプロセスにより、所有している数より多くのアプリまたはブックのコピーがインストールされないようにできます。

## <a name="which-types-of-apps-and-books-can-you-manage"></a>管理できるアプリとブックの種類

Intune では、iOS ストアからボリューム購入したアプリとブックを管理し、ビジネス向け Windows ストアからボリューム購入したアプリを管理できます。 各ストアからライセンスを購入したアプリを管理する方法については、次のトピックのいずれかをご覧ください。

- [iOS のボリューム購入アプリの管理](vpp-apps-ios.md)
- [ビジネス用 Windows ストアからボリューム購入したアプリの管理](windows-store-for-business.md)
- [Volume Purchase Program で購入した iOS 電子ブックを Microsoft Intune で管理する方法](vpp-ebooks-ios.md)
