---
title: "Android アプリと MAM ポリシー | Microsoft Intune"
description: "このトピックでは、アプリがモバイル アプリ管理ポリシーを使用して管理されている場合に予想される結果について説明します。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 546b909737b4ea34bd747880fe8ed2d366c6b18a


---

# MAM ポリシーを使用して Android アプリを管理するときの注意点
このトピックでは、MAM ポリシーを使用する場合のアプリのユーザー エクスペリエンスについて説明します。 モバイル アプリケーション管理 (MAM) ポリシーが適用されるのは、作業アカウントを使用してアプリにアクセスしたり、会社の OneDrive 事業拠点に格納されたファイルにアクセスしたりするなどのワーク コンテキストでアプリが使用される場合に限定されます。
##  アプリへのアクセス

Android デバイス上の MAM ポリシーに関連付けられたすべてのアプリでポータル サイト アプリが必要です。

Intune に登録されていないデバイスの場合は、ポータル サイト アプリをデバイスにインストールする必要があります。 ただし、ユーザーは MAM ポリシーによって管理されるアプリが使用できるようになるまで、ポータル サイト アプリの起動またはサインインを行う必要はありません。
ポータル サイト アプリは、セキュリティで保護された場所にあるデータを Intune で共有するための手段となります。したがって、このアプリは、デバイスが Intune に登録されていない場合でも必要です。


##  複数の ID を使用するアプリのサポート

MAM ポリシーはアプリがワーク コンテキストで使用されている場合にのみ適用されます。そのため、ワーク コンテキストとパーソナル コンテキストでは、アプリの動作に違いが見られることがあります。

複数の ID をサポートするアプリに対しては、Intune は、エンドユーザーがアプリをワーク コンテキストで使用している場合にのみ MAM ポリシーを適用します。  たとえば、エンドユーザーが職場のデータにアクセスすると、暗証番号 (PIN) を求めるプロンプトが表示されます。  **Outlook アプリ** の場合、エンドユーザーにはアプリの起動時に、暗証番号 (PIN) の入力を求めるプロンプトが表示されます。 **OneDrive アプリ** の場合は、エンドユーザーが作業アカウントを入力すると、同様のプロンプトが表示されます。  Microsoft **Word**、**PowerPoint*、**Excel** の場合は、エンドユーザーが会社の OneDrive for Business 拠点に保存されたドキュメントにアクセスすると、同様のプロンプトが表示されます。
##  デバイスのユーザー アカウントの管理

Intune では、MAM ポリシーをデバイスごとに 1 つのユーザー アカウントのみに展開することをサポートします。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、MAM ポリシーが適用される最初のユーザーだけです。

  * **Microsoft Word**、**Excel**、および **PowerPoint** では、2 つ目のユーザー アカウントがブロックされることはありませんが、2 つ目のユーザー アカウントが MAM ポリシーの影響を受けることはありません。

  * **OneDrive アプリと Outlook アプリ**では、作業アカウントは 1 つだけ使用できます。  作業アカウントを複数追加しようとしても、これらのアプリでブロックされます。  ただし、デバイス上のユーザーを削除して、別のユーザーを追加することはできます。


* MAM ポリシーを展開する前にデバイスに複数の既存のユーザー アカウントがある場合は、MAM ポリシーが展開される最初のアカウントが Intune MAM ポリシーによって管理されます。


次のサンプル シナリオを読んで、複数のユーザー アカウントがどのように処理されるかを深く理解してください。

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してMAM ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に** MAM ポリシーを展開しています。MAM ポリシーは、**会社 X** に関連付けられた MAM ポリシーに適用され、会社 Y に関連付けられたアカウントには適用されません。会社 Y に関連付けられたユーザー アカウントを MAM ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除する必要があります。
### 2 つ目のアカウントの追加
####  Android
Android デバイスを使用している場合は、既存のアカウントを削除して新しいアカウントを追加する手順を示すブロック メッセージが表示されることがあります。  既存のアカウントを削除するには、**[設定] &gt; [全般] &gt; [アプリケーション マネージャー] &gt; [会社のポータル] の順に選択し、[データのクリア] を選びます**。

![エラー メッセージとアカウントの削除手順のスクリーンショット](../media/AppManagement/Android_SwitchUser.png)

##  Azure Information Protection アプリ (旧称: Rights Management 共有アプリ) でメディア ファイルを表示する
Android デバイスで会社の AV、PDF、および画像ファイルを表示するには、[Azure Information Protection アプリ](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)を使用します。

このアプリは、Google Play ストアからダウンロードします。  

次のファイルの種類がサポートされます。

* **音声:** AAC LC、HE-AACv1 (AAC+)、HE-AACv2 (enhanced AAC+)、AAC ELD (enhanced low delay AAC)、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **ビデオ:** H.263、H.264 AVC、MPEG-4 SP、VP8。
* **画像:** jpg、pjpg、png、ppng、bmp、pbmp、gif、pgif、jpeg、pjpeg。
* **ドキュメント:** PDF、PPDF

------------
|**pfile**|**text**|
|----|----|
|pfile は、保護するファイル向けの汎用的な "ラッパー" 形式です。暗号化されたコンテンツと Azure Information Protection ライセンスをカプセル化し、任意のファイルの種類を保護できます。|XML、CSV などのテキスト ファイルは、保護されているときでもアプリで開いて表示できます。 ファイルの種類: txt、ptxt、csv、pcsv、log、plog、xml、pxml。|
---------------
## 次のステップ
[MAM ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### 関連項目
[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


