---
title: "Android アプリと MAM ポリシー | Microsoft Docs"
description: "このトピックでは、アプリがモバイル アプリ管理ポリシーを使用して管理されている場合に予想される結果について説明します。"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: aeacfddb3ed42938dd9443e2734222c977436430


---

# <a name="what-to-expect-when-your-android-app-is-managed-by-mam-policies"></a>MAM ポリシーを使用して Android アプリを管理するときの注意点

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、MAM (モバイル アプリケーション管理) ポリシーを使用する場合のアプリのユーザー エクスペリエンスについて説明します。 MAM ポリシーが適用されるのは、仕事でアプリが使用される場合に限られます。たとえば、職場のアカウントを使用してアプリにアクセスしたり、会社の OneDrive 事業拠点に格納されたファイルにアクセスしたりする場合です。
##  <a name="access-apps"></a>アプリにアクセスする

Android デバイス上の MAM ポリシーに関連付けられたすべてのアプリでポータル サイト アプリが必要です。

Intune に登録されていないデバイスの場合は、ポータル サイト アプリをデバイスにインストールする必要があります。 ただし、ユーザーは MAM ポリシーによって管理されるアプリが使用できるようになるまで、ポータル サイト アプリの起動またはサインインを行う必要はありません。

ポータル サイト アプリは、Intune が安全な場所でデータを共有するための手段となります。 そのため、ポータル サイト アプリは、デバイスが Intune に登録されていない場合でも、MAM ポリシーに関連付けられているすべてのアプリの要件となります。


##  <a name="use-apps-with-multi-identity-support"></a>複数の ID に対応しているアプリを使用する

MAM ポリシーは仕事関連でのみ適用されます。 そのため、仕事で使用する場合と個人的に使用する場合でアプリの動作が異なることがあります。

たとえば、ユーザーが職場のデータにアクセスすると、暗証番号 (PIN) を求めるプロンプトが表示されます。 **Outlook アプリ**の場合、ユーザーにはアプリの起動時に、暗証番号 (PIN) の入力を求めるプロンプトが表示されます。 **OneDrive アプリ**の場合、ユーザーが職場のアカウントを入力するとき、PIN の入力が求められます。 Microsoft **Word**、**PowerPoint**、**Excel** の場合、会社の OneDrive for Business 拠点に保存されているドキュメントにユーザーがアクセスするとき、PIN の入力が求められます。

##  <a name="manage-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理

Intune では、MAM ポリシーの展開は、デバイスごとに 1 ユーザー アカウントに限られます。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、MAM ポリシーが適用される最初のユーザーだけです。

  * **Microsoft Word**、**Excel**、および **PowerPoint** では、2 つ目のユーザー アカウントがブロックされることはありませんが、2 つ目のユーザー アカウントが MAM ポリシーの影響を受けることはありません。

  * **OneDrive アプリ**と **Outlook アプリ**では、職場のアカウントは 1 つだけ使用できます。  これらのアプリに複数の職場のアカウントを追加することはできません。  ただし、デバイス上のユーザーを削除して、別のユーザーを追加することはできます。


* MAM ポリシーを展開する前にデバイスに複数の既存のユーザー アカウントがある場合は、MAM ポリシーが展開される最初のアカウントが Intune MAM ポリシーによって管理されます。


次のサンプル シナリオを読んで、複数のユーザー アカウントがどのように処理されるかを深く理解してください。

ユーザー A は、**会社 X** と会社 **会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してMAM ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に** MAM ポリシーを展開しています。MAM ポリシーは、**会社 X** に関連付けられた MAM ポリシーに適用され、会社 Y に関連付けられたアカウントには適用されません。会社 Y に関連付けられたユーザー アカウントを MAM ポリシーで管理する場合は、会社 X に関連付けられたユーザー アカウントを削除する必要があります。
### <a name="add-a-second-account"></a>2 つ目のアカウントを追加する
####  <a name="android"></a>Android
Android デバイスを使用している場合は、既存のアカウントを削除して新しいアカウントを追加する手順を示すブロック メッセージが表示されることがあります。  既存のアカウントを削除するには、**[設定]、[全般]、[アプリケーション マネージャー]、[会社のポータル]** の順に選択します。 **[データのクリア]** を選択します。

![エラー メッセージとアカウントの削除手順のスクリーンショット](../media/AppManagement/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Azure Information Protection アプリでメディア ファイルを表示する
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

## <a name="next-steps"></a>次のステップ
[MAM ポリシーを使用して iOS アプリを管理するときの注意点](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### <a name="see-also"></a>関連項目
[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


