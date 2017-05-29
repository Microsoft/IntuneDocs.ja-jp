---
title: "Android の管理をセットアップする | Microsoft Docs"
description: "Microsoft Intune を使用して Android および KNOX Standard デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4042a22ecfbab7970ea4b3dab8ee6a82b0da5f78
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-android-device-management"></a>Android デバイスの管理をセットアップする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 管理者は、ポータル サイトから Samsung Knox Standard デバイスなどの Android デバイスの管理を有効にできます。 ユーザーが、Google Play から入手できるポータル サイト アプリを使用してデバイスを登録できます。

既定では、Android デバイスを Intune に登録することができます。 Android デバイスの登録をブロックするには、管理者資格情報を使用して [Microsoft Intune 管理ポータル](https://manage.microsoft.com)にサインインします。 **[管理]** > **[モバイル デバイス管理]** > **[登録ルール]** の順に選択し、**[Android デバイスを許可する]** チェック ボックスをオフにします。

1.  **Intune をセットアップする**<br>
    **Microsoft Intune** を[モバイル デバイス管理機関に設定](prerequisites-for-enrollment.md#step-2-set-mdm-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **Android の登録が有効になる**<br>
    Android モバイル デバイスの登録を有効にするために、Intune コンソールで追加の構成を行う必要はありません。

3.  **デバイスを登録して会社のリソースへのアクセスを取得する方法をユーザーに知らせる**

    エンドユーザー用の登録手順については、「[Intune に Android デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)」を参照してください。 登録プロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見られないデータについての説明が行われます。

    その他のエンドユーザー タスクの詳細については、次の記事を参照してください。
  - [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](how-to-educate-your-end-users-about-microsoft-intune.md)
  - [Android デバイス向けエンド ユーザー ガイダンス](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

中国には Google Play ストアがないので、Android デバイスは中国のアプリ マーケットプレースからポータル サイトを入手する必要があります。 Android 用ポータル サイト アプリは、以下のストアでダウンロードできます。
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

Android 用ポータル サイト アプリは、Google Play 開発者サービスを使って Microsoft Intune サービスと通信します。 中国では Google Play 開発者サービスをまだ利用できないので、次のタスクには最大 8 時間かかることがあります。 

|Intune 管理コンソール| Android 用 Intune ポータル サイト アプリ |Intune ポータル サイト Web サイト|   
|---|---|---|
|フル ワイプ| リモート デバイスの削除| デバイスの削除 (ローカルおよびリモート)|
|選択的ワイプ| デバイスのリセット| デバイスのリセット|
|新規アプリまたは更新アプリの展開| 使用可能な基幹業務アプリのインストール| デバイスのパスコードのリセット|
|リモート ロック|||
|パスコードのリセット|||

### <a name="see-also"></a>関連項目
[Microsoft Intune でデバイスを登録するための前提条件](prerequisites-for-enrollment.md)

