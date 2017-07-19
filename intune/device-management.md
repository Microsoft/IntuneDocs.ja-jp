---
title: "Intune を使用してデバイスを管理する"
titleSuffix: Intune on Azure
description: "Intune で管理するデバイスを確認し、そのデバイスで各種操作を実行する方法について説明します。\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune デバイスの管理とは


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[デバイス]** ワークロードでは、管理対象のデバイスについての情報が得られ、そのデバイスでリモート タスクを実行できます。 このワークロードにアクセスするには、以下の手順に従います。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。

次のアクションを実行できるようになります。

- [デバイス インベントリを表示する](device-inventory.md)
- 以下のリモート デバイス アクションを実行します。
    - [会社データの削除](device-company-data-remove.md) 
    - [出荷時の設定に戻す](device-factory-reset.md)
    - [リモート ロック](device-remote-lock.md)
    - [パスコードのリセット](device-passcode-reset.md)
    - [アクティブ化ロックのバイパス](device-activation-lock-bypass.md)
    - [新しく開始](device-fresh-start.md)
    - [紛失モード](device-lost-mode.md)
    - [デバイスを検索する](device-locate.md)
    - [再起動](device-restart.md)
    - [Windows 10 の PIN のリセット](device-windows-pin-reset.md)
    - [Android のリモート コントロール](device-profile-android-teamviewer.md)


## <a name="support-for-each-device-action"></a>各デバイスのアクションのサポート

次の表は、各アクションによってサポートされているデバイス プラットフォームをまとめたものです。

|||||||
|-|-|-|-|-|-|
|デバイスのアクション|Windows|Windows Phone|iOS|macOS|Android|
|**会社データの削除**|Yes|○|○|○|Yes|
|**出荷時の設定に戻す**|Windows 8.1 以降 (EAS で管理されていないデバイス)|○|○|いいえ|Android for Work はサポートされていません|
|**削除**|○|○|○|○|Yes|
|**リモート ロック**|いいえ|Windows Phone 8.1 以降|Yes|いいえ|○|
|**パスコードのリセット**|いいえ|Windows Phone 8.1 から Azure AD に参加していない Windows 10 Creators Update まで、Windows 10 Creators Update 以降 - すべて|Yes|いいえ|Android 7 より前、Android for Work は非サポート|
|**新しいパスコード** (Windows 10 デバイスの場合)|いいえ|Windows 10 Creators Update 以降 (Azure AD に参加)|いいえ|いいえ|Android for Work はサポートされていません|
|**アクティブ化ロックのバイパス**|いいえ|いいえ|会社所有デバイスのみ|いいえ|いいえ|
|**紛失モード**|いいえ|いいえ|iOS 9.3 以降、監督下、会社所有|いいえ|いいえ|
|**デバイスを検索する**|いいえ|いいえ|紛失モードの iOS 9.3 以降、監督下、会社所有|いいえ|いいえ|
|**現在のユーザーのログアウト**|いいえ|いいえ|iOS 9.3 以降 (共有 iPad デバイスのみ)|いいえ|いいえ|
|**再起動**|Windows 8.1 以降|Windows Phone 8.1 以降|いいえ|いいえ|いいえ|
|**新しく開始**|Windows 10 Creators Update 以降|いいえ|いいえ|いいえ|いいえ|
|**新しいリモート アシスタンス セッション**|いいえ|いいえ|いいえ|[いいえ]|Yes|
|**ユーザーの削除**|いいえ|いいえ|iOS 9.3 以降 (共有 iPad デバイスのみ)|いいえ|いいえ|

## <a name="next-steps"></a>次のステップ

- 管理しているデバイスで実行されているアクションの状態を確認するには、**[デバイス アクション]** を選びます。 
![デバイス アクションの監視](./media/monitor-device-actions.png)