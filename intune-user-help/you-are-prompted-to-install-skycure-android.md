---
title: "Android デバイスに Symantec Endpoint Protection Mobile をインストールする必要がある | Microsoft Docs"
description: "Android デバイスに SEP Mobile をインストールする方法を説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 09/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 627cd171-6e1b-439e-809a-2e6f007c4b3d
searchScope:
- User help
ROBOTS: 
ms.custom: intune-enduser
ms.openlocfilehash: 040b7bad4b62acffa5dad1606d5beb81efc56b68
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="install-symantec-endpoint-protection-mobile-on-your-android-device"></a>Android デバイスに Symantec Endpoint Protection Mobile をインストールする

作業内容にアクセスする前に、潜在的なセキュリティ脅威を検出してデバイスを保護することができる、Symantec Endpoint Protection (SEP) Mobile アプリをインストールするように会社から求められます。

インストールで問題が発生する場合、このトピックの終わりに示すトラブルシューティングの手順を試してください。

## <a name="what-you-need-to-do"></a>必要事項

1. 画面の一番上から下にドラッグして通知バーを開き、**[Required application – Install Skycure from Play Store]\(必要なアプリケーション – Skycure を Play ストアからインストール)** をタップします。 ポータル サイト アプリの __[Compliance Details]\(ポリシー準拠状況の詳細)__ でも確認することができます。

2. Play ストアの SEP Mobile のインストール ページが表示されます。 SEP Mobile をインストールし、**[同意する]** をタップして SEP Mobile がデバイスにアクセスすることを許可します。

3. SEP Mobile を開いて、**[VERIFY]\(確認)** をタップします。

4. **[Azure Active Directory でサインインする]** をタップし、職場または学校の電子メールやファイルへのアクセスに使用しているアカウントを入力します。

5. 職場または学校の電子メールやファイルへのアクセスに使用するアカウントを選択してから **[アカウントの追加]** をタップします。

6. **[同意する]** をタップして SEP Mobile による自分のアカウントでのサインインと自分のプロフィールの読み取りを許可します。

7. SEP Mobile がこのデバイスをどのように保護するかを確認してから **[OK]** をタップします。 少しして SEP Mobile のセットアップが完了すると、デバイス上のセキュリティの脅威を探す処理を開始します。

8. SEP Mobile がこのデバイス上のセキュリティの脅威を探す処理をただちに開始します。

  * SEP Mobile によってこのデバイスでセキュリティ上の脅威が見つかった場合は、問題を解決する手順が表示されます。

  * 脅威が検出されない場合は、3 つの脅威の種類はすべて緑色で表示されます。

    * ポータル サイトの **[デバイスの詳細]** 画面には、このデバイスが会社のセキュリティ要件に準拠している状態であることが表示されます。

    ![このデバイスはポリシーに準拠している状態になりました](./media/mtd-device-now-compliant-android.png)

## <a name="if-the-installation-doesnt-work"></a>インストールが機能しない場合

ユーザーが制御できない技術的な問題によりインストールが失敗する場合があります。 このような場合は、SEP Mobile を [Play ストアから手動で](https://play.google.com/store/apps/details?id=com.skycure.skycure)インストールします。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
