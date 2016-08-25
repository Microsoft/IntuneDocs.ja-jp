---
title: "デバイスが最小限のセキュリティ パッチを満たしていない | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: angrobe
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b3e5994c-d215-4c72-8915-349bd0b2504d
ROBOTS: noindex,nofollow
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 9405fdf219a1882cbfa2326c22325545ecec5080


---

# デバイスが最小限のセキュリティ パッチを満たしていない

"最低限の Android セキュリティ パッチが構成されていません" というメッセージが表示される場合、最低限のセキュリティ パッチ以降をインストールする必要があります。 IT 管理者は、Android デバイス上の会社のデータを保護するために、このインストールを必須にしています。

現在のセキュリティ パッチ レベルの場所は、使用している Android デバイスの種類によって異なります。 Samsung Knox デバイスか、他の種類の Android デバイスかを確認する必要があります。 Samsung Knox デバイスかどうかを確認するには、**[Settings]** > **[About phone]** を選択します。 "Knox" という単語が表示されない場合、使用しているデバイスは Samsung Knox ではありません。

**デバイスの最新のソフトウェア バージョンを確認するには:**

- Samsung Knox 以外のデバイス: **[Settings]** > **[About]** > **[Software information]** > **[More]** に移動し、**[Android security patch level]** を確認します。 メニュー名と場所は、Android デバイスによって異なる場合があります。

- Samsung Knox デバイス: **[Settings]** > **[About phone]** > **[Security software version]** に移動します。

**必要なセキュリティ パッチをインストールするには:**

- Samsung Knox 以外のデバイス: **[Settings]** > **[About]** > **[Software updates]** に移動します。

- Samsung Knox デバイス: **[Settings]** > **[System updates]** > **[Check for new system update]** に移動します。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

### 関連項目
[Android デバイスを Intune で使用する](using-your-android-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


