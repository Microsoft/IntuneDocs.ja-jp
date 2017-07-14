---
title: "アプリ保護ポリシー付きの Android アプリ"
description: "このトピックでは、アプリ保護ポリシーを使用してアプリを管理するときの注意点について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 030e17a9f28a9476c82e89d4dd26151a2d3cb953
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2017
---
# アプリ保護ポリシーを使用して Android アプリを管理するときの注意点
<a id="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

このトピックでは、アプリ保護ポリシーを使用する場合のアプリのユーザー エクスペリエンスについて説明します。 アプリ保護ポリシーが適用されるのは、仕事でアプリが使用される場合に限られます。たとえば、職場のアカウントを使用してアプリにアクセスしたり、会社の OneDrive 事業拠点に格納されたファイルにアクセスしたりする場合です。
##  アプリにアクセスする
<a id="access-apps" class="xliff"></a>

Android デバイス上のアプリ保護ポリシーに関連付けられたすべてのアプリでポータル サイト アプリが必要です。

Intune に登録されていないデバイスの場合は、ポータル サイト アプリをデバイスにインストールする必要があります。 ただし、ユーザーはアプリ保護ポリシーによって管理されるアプリが使用できるようになるまで、ポータル サイト アプリの起動またはサインインを行う必要はありません。

ポータル サイト アプリは、Intune が安全な場所でデータを共有するための手段となります。 そのため、ポータル サイト アプリは、デバイスが Intune に登録されていない場合でも、アプリ保護ポリシーに関連付けられているすべてのアプリの要件となります。


##  複数の ID に対応しているアプリを使用する
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

アプリ保護ポリシーは仕事関連でのみ適用されます。 そのため、仕事で使用する場合と個人的に使用する場合でアプリの動作が異なることがあります。

たとえば、ユーザーが職場のデータにアクセスすると、暗証番号 (PIN) を求めるプロンプトが表示されます。 **Outlook アプリ**の場合、ユーザーにはアプリの起動時に、暗証番号 (PIN) の入力を求めるプロンプトが表示されます。 **OneDrive アプリ**の場合、ユーザーが職場のアカウントを入力するとき、PIN の入力が求められます。 Microsoft **Word**、**PowerPoint**、**Excel** の場合、会社の OneDrive for Business 拠点に保存されているドキュメントにユーザーがアクセスするとき、PIN の入力が求められます。

##  デバイスのユーザー アカウントの管理
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

Intune では、アプリ保護ポリシーの展開は、デバイスごとに 1 ユーザー アカウントに限られます。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、アプリ保護ポリシーが適用される最初のユーザーのみです。

  * **Microsoft Word**、**Excel**、**PowerPoint** では、2 つ目のユーザー アカウントがブロックされることはありませんが、2 つ目のユーザー アカウントがアプリ保護ポリシーの影響を受けることはありません。

  * **OneDrive アプリ**と **Outlook アプリ**では、職場のアカウントは 1 つだけ使用できます。  これらのアプリに複数の職場のアカウントを追加することはできません。  ただし、デバイス上のユーザーを削除して、別のユーザーを追加することはできます。


* アプリ保護ポリシーを展開する前にデバイスに複数の既存のユーザー アカウントがある場合は、アプリ保護ポリシーが展開される最初のアカウントが Intune アプリ保護ポリシーによって管理されます。


次のサンプル シナリオを読んで、複数のユーザー アカウントがどのように処理されるかを深く理解してください。

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してアプリ保護ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に**アプリ保護ポリシーを展開しています。アプリ保護ポリシーは、**会社 X** に関連付けられたアプリ保護ポリシーに適用され、会社 Y に関連付けられたアカウントには適用されません。会社 Y に関連付けられたユーザー アカウントをアプリ保護ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除する必要があります。
### 2 つ目のアカウントを追加する
<a id="add-a-second-account" class="xliff"></a>
####  Android
<a id="android" class="xliff"></a>
Android デバイスを使用している場合は、既存のアカウントを削除して新しいアカウントを追加する手順を示すブロック メッセージが表示されることがあります。  既存のアカウントを削除するには、**[設定]、[全般]、[アプリケーション マネージャー]、[会社のポータル]** の順に選択します。 **[データのクリア]** を選択します。

![エラー メッセージとアカウントの削除手順のスクリーンショット](./media/Android_SwitchUser.png)

##  Azure Information Protection アプリでメディア ファイルを表示する
<a id="view-media-files-with-the-azure-information-protection-app" class="xliff"></a>
Android デバイスで会社の AV、PDF、画像ファイルを表示するには、[Azure Information Protection アプリ](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (以前の Rights Management 共有アプリ) を使用します。

このアプリは、Google Play ストアからダウンロードします。  

次のファイルの種類がサポートされます。

* **音声:** AAC LC、HE-AACv1 (AAC+)、HE-AACv2 (enhanced AAC+)、AAC ELD (enhanced low delay AAC)、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE
* **ビデオ:** H.263、H.264 AVC、MPEG-4 SP、VP8
* **画像:** .jpg、.pjpg、.png、.ppng、.bmp、.pbmp、.gif、.pgif、.jpeg、.pjpeg
* **ドキュメント:** PDF、PPDF


|**pfile**|**テキスト**|
|----|----|
|pfile は、保護するファイル向けの汎用的な "ラッパー" 形式です。暗号化されたコンテンツと Azure Information Protection ライセンスをカプセル化します。 任意のファイルの種類を保護できます。|XML、CSV などのテキスト ファイルは、保護されているときでもアプリで開いて表示できます。 ファイルの種類: .txt、.ptxt、.csv、.pcsv、.log、.plog、.xml、.pxml。|

## 次のステップ
<a id="next-steps" class="xliff"></a>
[アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点](end-user-mam-apps-ios.md)
