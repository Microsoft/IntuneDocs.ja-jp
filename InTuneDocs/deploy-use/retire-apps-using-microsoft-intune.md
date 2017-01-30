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
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: d0c24549c4805da87c74247253905a96d6290969


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



<!--HONumber=Dec16_HO5-->


