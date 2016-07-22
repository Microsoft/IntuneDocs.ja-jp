---
title: "Microsoft Intune での企業所有の iOS デバイスの登録 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 48359b44bec9ac3e1c9510debc01d2cf8abf6d2b


---

# Microsoft Intune での企業所有の iOS デバイスの登録
Microsoft Intune は、Mac コンピューターで実行される Apple Device Enrollment Program (DEP) または [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) ツールを使用した、企業所有の iOS デバイスの登録をサポートします。

企業登録対象の iOS デバイスは次の 3 つの方法で登録することができます。

-   **セットアップ アシスタントを使用した登録** – デバイスを出荷時の設定に戻し、デバイスの新しいユーザーによるセットアップ用に準備します。 この方法では、管理者は、Apple Configurator を実行している Mac コンピューターに iOS デバイスを USB 接続して、登録を事前構成する必要があります。 その後、デバイスがユーザーに渡され、ユーザーがセットアップ アシスタント プロセスを実行し、自分の職場または学校の資格情報でデバイスを構成して登録プロセスを完了します。 [Apple Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](ios-setup-assistant-enrollment-in-microsoft-intune.md)

-   **直接登録** - デバイスの準備中に使用する Apple Configurator 準拠のファイルを作成します。 登録されるデバイスは出荷時の設定に戻されませんが、ユーザーの関連付け情報は含まれません。 この方法では、管理者は、Apple Configurator を実行している Mac コンピューターに iOS デバイスを USB 接続して、デバイスを登録する必要があります。 [Apple Configurator の直接登録を使用して iOS デバイスを登録する](ios-direct-enrollment-in-microsoft-intune.md)

-   **Device Enrollment Program (DEP)** – Apple の Device Enrollment Program を通して購入された iOS デバイスに登録プロファイルを "無線" で展開します。 ユーザーがデバイスでセットアップ アシスタントを実行すると、デバイスが Intune に登録されます。  DEP を使用して登録したデバイスの場合は、ユーザーが登録を解除することはできません。 [Device Enrollment Program の iOS デバイスを登録する](ios-device-enrollment-program-in-microsoft-intune.md)




### 関連項目
[Microsoft Intune にデバイスを登録する準備](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


