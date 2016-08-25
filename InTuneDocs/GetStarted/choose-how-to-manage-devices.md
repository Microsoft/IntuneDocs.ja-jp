---
title: "デバイスを管理する方法を選択する | Microsoft Intune"
description: "デバイスを登録および管理するさまざまな方法について説明します。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c329bd08aaf72ae2acaa03dcb12c911d84b46b4e
ms.openlocfilehash: cfd9df3814d0d306a254a5566155a91ce5d0ca16


---

# デバイスを管理する方法を選択する
Intune では、サービスにデバイスを*登録*することによって、さまざまなデバイスを管理できます。 その後、ユーザーは*ポータル サイト*を使用して、デバイスの登録、アプリの参照とインストール、デバイスが会社のポリシーに準拠していることの確認、IT サポートへの連絡など、さまざまな操作を実行できます。

## モバイル デバイスを管理する方法
Intune では、次のデバイス プラットフォームを管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

> [!NOTE]
> サポート対象バージョンより前のバージョンの iOS を実行するデバイスを登録した場合、そのデバイスの登録は解除されません。 機能がそのバージョンの iOS をサポートしていることをドキュメントで確認してください。

一般に "Bring Your Own Device (BYOD)" として知られる方法を使い、Intune でユーザーのデバイスを管理できます。 会社がユーザーに選択可能なリストを提供する "Choose Your Own Device (CYOD)" として知られるシナリオを含む、会社所有のデバイスも管理できます。

### デバイスを登録して管理する
iOS、Android、Windows Phone などのモバイル デバイス オペレーティング システムの場合、デバイスの登録は必須です。 デバイスを登録する方法は、組織のニーズによって異なります。

|登録の種類|BYOD|CYOD|マネージャー アカウントを持つ共有デバイス|ユーザー アカウントを持たない共有デバイス|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**説明**|Microsoft Intune を使用して登録した個人のデバイス|1 人のユーザーが使用する企業所有のデバイス|多くのユーザーによって共有されるマネージャー アカウントを使用して管理される企業所有のデバイス|多くのユーザーによって使用される企業所有のユーザーのないデバイス。|
|**デバイスのユーザー**|Owner|割り当てられているユーザー|ユーザー固有のアカウントはありません|特定のユーザーはいない|
|**登録するユーザー**|Owner|管理者|デバイス マネージャー|すべてのユーザー|
|**登録解除するユーザー**|所有者または管理者|プラットフォーム |管理者またはユーザー|管理者またはユーザー|
|**リセット可能なユーザー**|所有者または管理者|管理者|管理者|管理者|

その他のガイダンスについては、「[モバイル デバイスの登録方法の選択](/intune/get-started/choose-how-to-enroll-devices1)」を参照してください。

> [!NOTE]
> デバイスを登録することによって可能になるすべての機能の一覧については、「[Mobile device management capabilities](mobile-device-management-capabilities-in-microsoft-intune.md)」 (モバイル デバイス管理機能) を参照してください。

## Windows PC を管理する方法
Intune では、Intune コンピューター クライアントを使用して、Windows Vista 以降の Windows PC を管理できます。 ただし、Windows PC の場合は、デバイスを登録するか、Intune PC クライアント ソフトウェアをインストールするかを選択できます。クライアント ソフトウェアには、デバイスを登録した場合には使用できない機能がいくつかありますが、 ほとんどのシナリオでは、Intune を使用して Windows デバイスを登録します。そうすることで、コンピューター クライアントよりも多くの機能を利用できます。

以下に該当する場合は、Intune コンピューター クライアントを使用することを検討してください。

- Microsoft Intune コンピューター クライアントの機能のいずれかを使用して Windows PC を管理する
- 登録に対応していないオペレーティング システムを実行している Windows PC を管理する

> [!NOTE]
> Intune コンピューター クライアントをサポート対象の Windows PC にインストールすることで可能になるすべての機能の一覧については、「[Windows PC management capabilities](windows-pc-management-capabilities-in-microsoft-intune.md)」 (Windows PC 管理機能) を参照してください。

## Exchange ActiveSync による管理
Exchange ActiveSync を使用してデバイスを管理することもできます。 そのためには、On-Premises Connector をインストールするか、組み込みの Service to Service Connector を使用して Exchange Server に接続します。

On-Premises Connector をインストールするためのハードウェアおよびソフトウェアの要件の詳細については、「[On-Premises Connector の要件](/intune/deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connector)」を参照してください。

On-Premises Connector または Service to Service Connector と Exchange を併用する方法については、「[Mobile device management with Exchange ActiveSync and Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)」 (Exchange ActiveSync および Microsoft Intune を使用したモバイル デバイス管理) を参照してください。



## 次のステップ
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を使用してデバイスを登録することで利用可能になる機能の一部を把握しました。 次は[デバイスを登録する](/intune/deploy-use/enroll-devices-in-microsoft-intune)準備をする必要があります。 デバイスを登録すると、このトピックで紹介したすべての機能を利用できるようになります。 <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->



<!--HONumber=Aug16_HO3-->


