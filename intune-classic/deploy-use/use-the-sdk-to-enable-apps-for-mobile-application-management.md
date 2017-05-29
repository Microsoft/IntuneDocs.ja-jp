---
title: "SDK を使用して MAM のアプリを有効にする |Microsoft Docs"
description: "このトピックでは、Intune APP SDK を使用する必要がある理由について概説します。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 26b00081-7c05-4969-ace1-0585e44d5cd2
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ec4e2f966fa8c24505ce1fa74a59c95908273bd1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="use-the-sdk-to-enable-apps-for-mobile-application-management"></a>Use the SDK to enable apps for mobile application management (アプリでモバイル アプリケーション管理を実行できるよう SDK を使用する)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

iOS または Android アプリの特定の機能を Intune で管理できるようにするには、Microsoft Intune App SDK を使用します。 Intune での管理に向けた対応化が済んだら、アプリにポリシーを展開することができます。 それらの機能をポリシーから使用することによって、会社のデータが保護されます。 SDK で実装できる保護には、次のようなものがあります。

-   会社のドキュメントをクラウドにコピーすることを禁止する。

-   デバイスに保存するデータの暗号化をアプリに強制する

-   管理対象ブラウザーの使用を強制する

-   会社のデータをアプリから遠隔消去する

SDK を使用するためにはアプリのソース コードを書きかえる必要がありますが、SDK の大半の機能は、アプリの動作を変更せずに実装できます。

SDK の概要については、「[概要](/intune-classic/develop/intune-app-sdk-get-started)」を参照してください。

### <a name="see-also"></a>関連項目
[Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)

