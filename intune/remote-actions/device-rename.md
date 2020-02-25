---
title: Microsoft Intune を使ってデバイスの名前を変更する - Azure | Microsoft Docs
description: Microsoft Intune を使ってデバイスの名前を変更します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11b339a3e94e60db43e8237d9f3d2c729b48a57d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413610"
---
# <a name="rename-a-device-in-intune"></a>Intune 上でデバイスの名前を変更する

**デバイス名の変更**アクションによって、Intune に登録されているデバイスの名前を変更できます。 デバイスの名前は、Intune 内とデバイス上で変更されます。

次の種類のデバイス名を変更できます。
- 企業所有の Windows 
- 監視下にある iOS/iPadOS
- 企業所有の MacOS 10

この機能では、ハイブリッド Azure AD Windows デバイスの名前変更は現在サポートされていません。

## <a name="rename-a-device"></a>デバイスの名前を変更する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[デバイス]**  >  **[すべてのデバイス]** > デバイスの選択 > **[その他]**  >  **[デバイスの名前を変更]** の順に選択します。
4. **[デバイスの名前を変更]** ブレードで、テキスト ボックスに新しい名前を入力します。 文字、数字、ハイフンを使用できます。 名前には、少なくとも 1 つの文字またはハイフンを含める必要があります。
5. 名前の変更後、デバイスを再起動する場合、 **[名前を変更したら再起動する]** の横の **[はい]** を選択します。
6. **[名前の変更]** を選択します。

## <a name="windows-device-rename-rules"></a>Windows デバイスの名前の変更規則
Windows デバイスの名前を変更する場合、次の規則に従って新しい名前を指定する必要があります。
- 15 文字以下 (後続の NULL を除き、63 バイト以下にする必要があります)
- null または空の文字列にしない
- 許可される ASCII: 文字 (a-z、A-Z)、数字 (0-9)、ハイフン
- 許可される Unicode: 文字数 >= 0x80、有効な UTF8 であることが必須、IDN マッピング可能であることが必須 (つまり、RtlIdnToNameprepUnicode は合格です。RFC 3492 参照)
- 名前は数字だけにすることができない
- 名前にスペースを使用できない
- 許可されていない文字: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>次のステップ

**[名前の変更]** デバイス アクションの状態を表示するには、デバイスの **[概要]** ページを確認します。
