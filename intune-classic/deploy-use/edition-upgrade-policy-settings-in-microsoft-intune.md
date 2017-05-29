---
title: "Windows エディションのアップグレード ポリシー設定 | Microsoft Docs"
description: "Intune を使用して Windows 10 デバイスを別のバージョンに自動的にアップグレードする方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 81061f032ef2079695f45e54e99cbb6479252bed
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Microsoft Intune のエディションのアップグレード ポリシー設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune の**エディションのアップグレード ポリシー**を使用して、次に挙げる Windows 10 のバージョンのいずれかを実行するデバイスを自動的に別のエディションにアップグレードできます。
* [Windows] 10 Desktop
* Windows 10 Holographic
* [Windows] 10 Mobile

次のアップグレード パスがサポートされます。
- Windows 10 Pro から Windows 10 Enterprise へのアップグレード パス
- Windows 10 Home から Windows 10 Education へのアップグレード パス
- Windows 10 Mobile から Windows 10 Mobile Enterprise へのアップグレード パス
- Windows 10 Holographic Pro から Windows 10 Holographic Enterprise へのアップグレード パス

## <a name="before-you-start"></a>アップグレードを開始する前に
デバイスを最新バージョンにアップグレードし始める前に、次のいずれかを用意する必要があります。
* ポリシーで対象とするすべてのデバイスに新しいバージョンの Windows をインストールするための有効なプロダクト キー (Windows 10 Desktop エディションの場合)。 マルチ ライセンス認証キー (MAK) またはキー マネジメント サーバー (KMS) キーのどちらかを使用できます。
**または、**ポリシーで対象とするすべてのデバイスに新しいバージョンの Windows をインストールするためのライセンス情報を含む、Microsoft からのライセンス ファイル (Windows 10 Mobile エディションと Windows 10 Holographic エディションの場合)。
* 対象とする Windows 10 デバイスが Microsoft Intune に登録されている必要があります。 エディションのアップグレード ポリシーは、Intune PC クライアント ソフトウェアを実行する PC で使用できません。

## <a name="edition-upgrade-policy-settings"></a>エディションのアップグレード ポリシー設定

|設定の名前|説明|
|-|-|
|**名前**|エディションのアップグレード ポリシーの名前を入力します。|
|**説明**|必要に応じて、Intune コンソールでの識別に役立つポリシーの説明を入力します。
|**アップグレード後のエディション**|対象とするデバイスのアップグレード後の Windows 10 Desktop、Windows 10 Holographic、または Windows 10 Mobile のバージョンをドロップダウン リストから選びます。
|**プロダクト キー**|Microsoft から取得した、対象とするすべての Windows 10 デスクトップ デバイスをアップグレードするために使用できるプロダクト キーを指定します。<br>プロダクト キーを含むポリシーを作成した後でプロダクト キーを編集することはできません。 これは、セキュリティ上の理由からキーが隠されるためです。 プロダクト キーを変更するには、キー全体を再入力する必要があります。
|**ライセンス ファイル**|**[参照]** を選択し、Microsoft から取得した、対象とするデバイスのアップグレード後の Windows Holographic、または Windows 10 Mobile エディション用のライセンス情報を含むライセンス ファイルを選択します。

### <a name="see-also"></a>関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

