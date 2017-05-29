---
title: "アプリをインベントリから削除する | Microsoft Docs"
description: "Intune を使用してアプリを削除またはアンインストールする方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 670e108fc4f672b4900f7cfb4e0127e16a377fa7
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="retire-apps-using-microsoft-intune"></a>Microsoft Intune を使用してアプリをインベントリから削除する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

アプリをインベントリから削除するには、アプリをアンインストールします。 Intune を使用してアプリを展開および管理すると、そのアプリをアンインストールするプロセスは、モバイル デバイスと Windows PC の両方で同じになります。 そのアプリでは、この手順が成功するようにアンインストール処理がサポートされています。

## <a name="uninstall-an-app"></a>アプリをアンインストールする

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、[**アプリ**] &gt; [**アプリ**] の順に選びます。

2.  アンインストールする (既に展開した) アプリを選択し、[**展開の管理**] を選択します。

3.  **[展開アクション]** ページで、 **[承認]** 列の **[アンインストール]** を選択します。

デバイスまたはコンピューターで次にアプリが確認されるときに、そのアプリはアンインストールされます。

### <a name="see-also"></a>関連項目
[Microsoft Intune でアプリを追加する](add-apps.md)

