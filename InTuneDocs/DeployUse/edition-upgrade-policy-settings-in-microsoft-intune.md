---
title: "Windows エディションのアップグレード ポリシー設定 | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8e911193075d2a621ef94f2917b2126501ea2100
ms.openlocfilehash: e468ff102b45bf0c23fd76d8d15c44978861ae8a


---

# Microsoft Intune のエディションのアップグレード ポリシー設定
Microsoft Intune の**エディションのアップグレード ポリシー**を使用して、次に挙げる Windows 10 のバージョンのいずれかを実行するデバイスを自動的に新しいエディションにアップグレードできます。
* [Windows] 10 Desktop
* Windows 10 Holographic

## アップグレードを開始する前に
デバイスを最新バージョンにアップグレードし始める前に、次のいずれかを用意する必要があります。
* ポリシーで対象とするすべてのデバイスに新しいバージョンの Windows をインストールするための有効なプロダクト キー (Windows 10 Desktop エディションの場合)。
* ポリシーで対象とするすべてのデバイスに新しいバージョンの Windows をインストールするためのライセンス情報を含む、Microsoft からのライセンス ファイル (Windows 10 Mobile エディションと Windows 10 Holographic エディションの場合)。
* 対象とする Windows 10 デバイスが Microsoft Intune に登録されている必要があります。

## エディションのアップグレード ポリシー設定

|設定の名前|説明|
|-|-|
|**名前**|エディションのアップグレード ポリシーの名前を入力します。|
|**説明**|必要に応じて、Intune コンソールでの識別に役立つポリシーの説明を入力します。
|**アップグレード後のエディション**|対象とするデバイスのアップグレード後の Windows 10 Desktop、Windows 10 Holographic、または Windows 10 Mobile のバージョンをドロップダウン リストから選びます。
|**プロダクト キー**|Microsoft から取得した、対象とするすべての Windows 10 デスクトップ デバイスをアップグレードするために使用できるプロダクト キーを指定します。<br>プロダクト キーを含むポリシーを作成した後でプロダクト キーを編集することはできません。 これは、セキュリティ上の理由からキーが隠されるためです。 プロダクト キーを変更するには、キー全体を再入力する必要があります。
|**ライセンス ファイル**|**[参照]** をクリックし、Microsoft から取得した、対象とするデバイスのアップグレード後の Windows Holographic、または Windows 10 Mobile エディション用のライセンス情報を含むライセンス ファイルを選択します。

### 関連項目
[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


<!--HONumber=Jun16_HO4-->


