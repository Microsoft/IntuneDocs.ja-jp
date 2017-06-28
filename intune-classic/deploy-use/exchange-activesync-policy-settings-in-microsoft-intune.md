---
title: "Exchange ActiveSync ポリシー設定"
description: "Intune Exchange ActiveSync ポリシーを使用して、Exchange ActiveSync で管理されているデバイスのさまざまな機能を制御できる設定を構成します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 6bbb0cd7ca87a3c6cc352cbdd6dd2b61a9c5e36c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/08/2017


---

# <a name="exchange-activesync-policy-settings-in-microsoft-intune"></a>Microsoft Intune の Exchange ActiveSync ポリシー設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune **Exchange ActiveSync** ポリシーを使用して、Exchange ActiveSync で管理されているデバイスのさまざまな機能を制御する設定を構成します。


## <a name="password-settings"></a>パスワードの設定

|設定の名前|説明
|----------------|---|
|**モバイル デバイスのロックを解除するパスワードを要求する**|パスワードを使用してデバイスをロックする必要があるかどうかを指定します <br>(Windows RT を実行するデバイスには適用されません)。|
|**必要なパスワードの種類**|数値のみや英数字など、必要なパスワードの種類を指定します。|
|**最小のパスワードの長さ**|デバイスのパスワードに必要な最小文字数を指定します。|
|**単純なパスワードを許可する**|"0000" や "1234" などの単純なパスワードを使えるようにするかどうかを指定します。|
|**デバイスをワイプするまでの連続サインイン エラーの数**|間違ったパスワードをユーザーが何回入力すると、そのデバイスをワイプするかを指定します。|
|**パスワードの有効期限 (日)**|デバイスのパスワードの変更が必要になるまでの日数を指定します。
|**パスワードの履歴を記憶する**|以前に使用されていたパスワードの使用を許可しないかどうかを指定します。|
|**パスワードの履歴を保存する** - **前のパスワードを再利用できないようにする**|再び使用できない以前に使用していたパスワードの数を指定します。|
|**パスワードが必要になるまでの非アクティブ状態の時間 (分)**|デバイスがどれだけの時間アイドル状態であると、画面がロックされるかを指定します。

## <a name="encryption-settings"></a>暗号化の設定

|設定の名前|説明|
|----------------|---|
|**モバイル デバイスの暗号化を要求する**<sup>1</sup>|サポートされている場合にデバイス上のデータの暗号化を要求します。<br><br>Windows Phone 8 デバイスの場合、これを **[はい]**に設定する必要があります。<br /><br />iOS デバイスでの暗号化を有効にするには、**[モバイル デバイスのロック解除にパスワードを必要とする]** 設定を有効にします。|
|**メモリ カードの暗号化を必要とする**|(サポートされているデバイス上で) SD カードなどの外部ストレージに保存されたデータの暗号化を要求します。
<sup>1</sup> Windows 8.1 が実行されているデバイスの追加情報

-   Windows 8.1 搭載デバイスで暗号化を適用する場合は、[Windows の 2014 年 12 月付け MDM クライアント更新プログラム](https://support.microsoft.com/kb/3013816)を各デバイスにインストールする必要があります。

-   Windows 8.1 デバイスに対してこの設定を有効にすると、デバイスのすべてのユーザーに Microsoft アカウントが必要になります。

-   Windows 8.1 デバイスで暗号化を機能させる場合は、デバイスが Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) ハードウェア認定要件を満たしている必要があります。

-   Windows 8.1 デバイスで暗号化を適用すると、回復キーは、ユーザーの Microsoft アカウントからのみアクセスできるようになり、ユーザーの OneDrive アカウントからアクセスされます。 ユーザーの代わりにこのキーを回復することはできません。

## <a name="email-settings"></a>電子メールの設定

|設定の名前|説明
|----------------|---|
|**ユーザーが電子メールの添付ファイルをダウンロードできるようにする**|電子メールの添付ファイルをデバイスにダウンロードできるようにするかどうかを指定します。|
|**電子メールを同期する期間**|受信した電子メールをデバイスと同期する日数を指定します。
|**Exchange ActiveSync を完全にサポートしていないモバイル デバイスによる Exchange との同期を許可する**|1 つまたは複数の Exchange ActiveSync 設定をサポートしないデバイスで Exchange へのアクセスを許可するかどうかを指定します。

## <a name="browser-settings"></a>ブラウザー設定

|設定の名前|説明
|----------------|---|
|**Web ブラウザーを許可する**|デバイスの Web ブラウザーを使用できるようにするかどうかを指定します <br>(Windows RT または Windows Phone では使用できません)。

## <a name="hardware-settings"></a>ハードウェア設定

|設定の名前|説明
|----------------|---|
|**カメラを許可する**|デバイスのカメラを使用できるようにするかどうかを指定します。<br>(Windows RT または Windows Phone では使用できません)。



### <a name="see-also"></a>関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

