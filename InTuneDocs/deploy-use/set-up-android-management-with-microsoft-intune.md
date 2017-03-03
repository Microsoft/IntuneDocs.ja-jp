---
title: "Android の管理をセットアップする | Microsoft Docs"
description: "Microsoft Intune を使用して Android および KNOX Standard デバイスのモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 8e2588e2bb0537877f0164bc996fa973f25ea4dd


---

# <a name="set-up-android-device-management"></a>Android デバイスの管理をセットアップする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 管理者は、ポータル サイトから Samsung Knox Standard デバイスなどの Android デバイスの管理を有効にできます。 ユーザーが、Google Play から入手できるポータル サイト アプリを使用してデバイスを登録できます。

既定では、Android デバイスを Intune に登録することができます。 Android デバイスの登録をブロックするには、管理者資格情報を使用して [Microsoft Intune 管理ポータル](http://manage.microsoft.com)にサインインします。 **[管理]** > **[モバイル デバイス管理]** > **[登録ルール]** の順に選択し、**[Android デバイスを許可する]** チェック ボックスをオフにします。

1.  **Intune をセットアップする**<br>
    **Microsoft Intune** を[モバイル デバイス管理機関に設定](prerequisites-for-enrollment.md#step-2-set-mdm-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2.  **Android の登録が有効になる**<br>
    Android モバイル デバイスの登録を有効にするために、Intune コンソールで追加の構成を行う必要はありません。

3.  **デバイスを登録して会社のリソースへのアクセスを取得する方法をユーザーに知らせる**

    エンドユーザー用の登録手順については、「[Intune に Android デバイスを登録する](../enduser/enroll-your-device-in-intune-android.md)」を参照してください。 登録プロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見られないデータについての説明が行われます。

    その他のエンドユーザー タスクの詳細については、次の記事を参照してください。
  - [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](how-to-educate-your-end-users-about-microsoft-intune.md)
  - [Android デバイス向けエンド ユーザー ガイダンス](../enduser/using-your-android-device-with-intune.md)

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



<!--HONumber=Feb17_HO3-->


