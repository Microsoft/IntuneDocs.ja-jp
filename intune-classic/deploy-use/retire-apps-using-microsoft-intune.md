---
title: "アプリをインベントリから削除する"
description: "Intune を使用してアプリを削除またはアンインストールする方法について説明します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6fbf0805-1144-4e08-bafd-4f181d932bf2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 15e90a2fea2ec3b4f020a0e14c40da2cb65aecab
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
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
