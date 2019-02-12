---
title: Microsoft Intune での Windows 10 のアップグレードと S モードの設定 - Azure | Microsoft Docs
description: デバイス上の Windows 10 エディションをアップグレードするときのすべての設定一覧とその実行内容や、Microsoft Intune のデバイス構成プロファイルを使用してデバイス上で S モードを有効にする方法について説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 24f763cf3231bd76a01870d889cb7637f2f36532
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849677"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Intune でエディションのアップグレードや S モードの有効化に使用する Windows 10 (以降の) デバイス設定

Microsoft Intune には、デバイスの管理と保護に役立つ多くの設定が含まれています。 この記事では、Windows 10 デバイス上でのエディションのアップグレードや S モードの有効化に使用する設定について説明します。 このような設定は、デバイスにプッシュまたは展開される Intune のアップグレード構成プロファイルに作成されます。

モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、Windows 10 デバイスのエディションと S モードのオプションを制御します。

この機能の詳細については、[Windows 10 エディションのアップグレードまたは S モードの有効化](edition-upgrade-configure-windows-10.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[プロファイルを作成します](edition-upgrade-configure-windows-10.md#create-the-profile)。

## <a name="edition-upgrade"></a>エディションのアップグレード

- **アップグレード後のエディション**:アップグレード後の Windows 10 エディションを選択します。 このポリシーで対象となるデバイスが選択したエディションにアップグレードされます。
- **プロダクト キー**:Microsoft から受け取ったプロダクト キーを入力します。 プロダクト キーを含むポリシーの作成後、キーは更新できなくなり、セキュリティ上の理由から非表示になります。 プロダクト キーを変更するには、キー全体を再入力します。
- **ライセンス ファイル**:**[Windows 10 Holographic for Business]** または **[Windows 10 Mobile エディション]** については、**[参照]** を選択し、Microsoft から受け取ったライセンス ファイルを選択します。 このライセンス ファイルには、デバイスをアップグレードするエディションのライセンス情報が含まれています。

## <a name="mode-switch"></a>モード切り替え

- **No configuration (構成なし)**:S モード デバイスは S モードのままです。 エンドユーザーはデバイスを S モードから抜けさせることができます。
- **S モードのままにする**:エンド ユーザーはデバイスを S モードから抜けさせることができなくなります。
- **切り替え**:デバイスを S モードから切り替えます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も実行できない可能性があります。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

[Windows Holographic for Business](holographic-upgrade.md) デバイス用にエディションのアップグレード プロファイルを作成することもできます。
