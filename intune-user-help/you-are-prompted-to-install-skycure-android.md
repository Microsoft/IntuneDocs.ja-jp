---
title: "Android デバイスで Skycure をインストールする必要がある | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 627cd171-6e1b-439e-809a-2e6f007c4b3d
searchScope: User help
ROBOTS: 
ms.custom: intune-enduser
ms.openlocfilehash: 531963056c4e488865b1c51b76e6b9ce97fe2eb8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="you-need-to-install-skycure-on-your-android-device"></a>Android デバイスで Skycure をインストールする必要がある

作業内容にアクセスする前に、IT 管理者から潜在的なセキュリティ脅威を検出してデバイスを保護することができる、Skycure アプリをインストールするように求められます。

インストールで問題が発生する場合、このトピックの終わりに示すトラブルシューティングの手順を試してください。

**必要な操作**

1. 画面の一番上から下にドラッグして通知バーを開き、**[Required application – Install Skycure from Play Store]\(必要なアプリケーション – Skycure を Play ストアからインストール)** をタップします。 ポータル サイト アプリの __[Compliance Details]\(ポリシー準拠状況の詳細)__ でも確認することができます。

  ![Android デバイスの [Compliance Details](ポリシー準拠状況の詳細) ページ。 このデバイスは準拠した状態ではなく、ポータル サイト ページの下部に、デバイスはモバイル リスク ポリシーを満たしていないため、Skycure を開いて問題を解決する必要があることを示すメッセージが表示されます。](./media/skycure-resolves-compliance-android.png)

2. Play ストアの Skycure のインストール ページが表示されます。 Skycure をインストールし、**[同意する]** をタップして Skycure がデバイスにアクセスすることを許可します。

3. Skycure を開いて、**[VERIFY]\(確認)** をタップします。

4. [**Azure Active Directory でサインインする**] をタップし、職場または学校の電子メールやファイルへのアクセスに使用しているアカウントを入力します。

5. 職場または学校の電子メールやファイルへのアクセスに使用するアカウントを選択してから [**アカウントの追加**] をタップします。

6. **[同意する]** をタップして Skycure による自分のアカウントでのサインインと自分のプロフィールの読み取りを許可します。

7. Skycure がこのデバイスをどのように保護するかを確認してから **[OK]** をタップします。 少しして Skycure のセットアップが完了すると、デバイス上のセキュリティの脅威を探す処理を開始します。

  Skycure がこのデバイス上のセキュリティの脅威を探す処理をただちに開始します。

  ![Skycure によってデバイス上のセキュリティの脅威が分析されます。](./media/skycure-scan-in-progress-android.png)

  Skycure によってこのデバイスでセキュリティ上の脅威が見つかった場合は、問題を解決する手順が表示されます。

  ![セキュリティ上の脅威を検出しました。](./media/skycure-found-a-threat-android.png)

  脅威が検出されない場合は、3 つの脅威の種類はすべて緑色で表示されます。

    ポータル サイトの **[デバイスの詳細]** 画面には、このデバイスが会社のセキュリティ要件に準拠している状態であることが表示されます。

    ![このデバイスはポリシーに準拠している状態になりました](./media/mtd-device-now-compliant-android.png)

**インストールが機能しない場合**

ユーザーが制御できない技術的な問題によりインストールが失敗する場合があります。 このような場合は、Skycure を [Play ストアから手動で](https://play.google.com/store/apps/details?id=com.skycure.skycure)インストールします。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。
