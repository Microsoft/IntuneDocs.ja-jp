---
title: "Intune を使用した iOS および macOS デバイス向けの AirPrint 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Intune を使用して、iOS デバイスと macOS デバイスを AirPrint 対応プリンターに自動接続する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: a0f60cad9a5e679c83572375c3dd83bc7aeebd93
ms.lasthandoff: 04/19/2017


---

# <a name="airprint-settings-for-ios-and-macos-devices"></a>iOS および macOS デバイス向けの AirPrint 設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

これらの設定を利用し、ネットワーク上の AirPrint 対応プリンターに自動接続するように iOS デバイスまたは macOS デバイスを構成します。 始めるにはプリンターの IP アドレスとリソース パスを用意する必要があります。

## <a name="find-airprint-printer-information"></a>AirPrint プリンター情報を調べる

iOS デバイス ユーザーが既知の AirPrint プリンターに印刷できるようにするには、この手順を実行して AirPrint 情報を AirPrint ペイロードに追加します。

1. Airprint プリンターと同じローカル ネットワーク (サブネット) に接続している Mac で、(**/アプリケーション/ユーティリティ** フォルダから) ターミナルを開きます。
2. ターミナルで「**ippfind**」と入力し、Enter キーを押します。
3. コマンドによって返されたプリンター情報をメモします (例: **ipp://myprinter.local.:631/ipp/port1**)。 この情報の最初の部分がプリンター名で、後の部分がリソース パスです。
4. ターミナルで「**ping myprinter.local**」と入力し、Enter キーを押します。
5. コマンドによって返された IP アドレス情報をメモします (例: **PING myprinter.local (10.50.25.21)**)。
6. 最後に、この IP アドレスとリソース パスを AirPrint ペイロード設定で使用します。 上記の例では、IP アドレスは **10.50.25.21**、リソース パスは **/ipp/port1** になります。

## <a name="configure-an-airprint-profile"></a>AirPrint プロファイルを構成する

1. **[デバイス機能]** ブレードで **[AirPrint]** を選択します。
2. **[AirPrint]** ブレードで、AirPrint の出力先を追加するには、**IP アドレス**と**リソース パス**を入力して、**[追加]** をクリックします。
3. 必要な数の出力先を追加します。 終了したら **[OK]** を選択します。

コンマ区切り値 (.csv) ファイルからプリンターの一覧をインポートしたり、一覧をエクスポートすることもできます。

