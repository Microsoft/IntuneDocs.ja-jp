---
title: アプリ保護ポリシー付きの Android アプリ
titlesuffix: Microsoft Intune
description: 保護ポリシー付きの Android アプリでできることについて説明します。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16cef0b3e72c2e7815aada1c45c0e312b84931ab
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31833019"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>アプリ保護ポリシーを使用して Android アプリを管理するときの注意点 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

アプリ保護ポリシー付きの Android アプリでできることについて説明します。 アプリ保護ポリシーは、アプリが作業コンテキストで使用されている場合にのみ適用されます。 たとえば、仕事用アカウントを使用してアプリにアクセスするときや、会社の OneDrive の保存先に格納されているファイルにアクセスするときです。
##  <a name="accessing-apps"></a>アプリへのアクセス

アプリ保護ポリシーを持つ Android デバイス上のすべてのアプリでポータル サイト アプリが必要です。

Intune に登録されていないすべてのデバイスにポータル サイトをインストールします。 ユーザーは、アプリ保護ポリシー付きのアプリを使用するために、ポータル サイト アプリにサインインする必要はありません。
ポータル サイト アプリを使用すると、安全な場所でデータを共有することができます。 そのため、未登録のデバイスにもこれが必要です。


##  <a name="using-apps-with-multi-identity-support"></a>複数の ID を使用するアプリのサポート

アプリ保護ポリシーは、ユーザーが作業に関連するデータにアクセスしようとした場合にのみ有効になります。  ユーザーが個人的に使用するためにアプリにアクセスする場合には、異なる動作になる場合があります。

アプリの中には、複数の ID をサポートしているものもあります。 この場合、Intune ではユーザーが作業データにアクセスするときにのみ、アプリ保護ポリシーが適用されます。  たとえば、ユーザーに PIN プロンプトが表示されるとします。  **Outlook アプリ**では、ユーザーがアプリを起動したときにプロンプトが表示されます。 **OneDrive アプリ** では、ユーザーが作業アカウントを入力するときに、プロンプトが表示されます。  Microsoft **Word**、**PowerPoint**、**Excel** では、ユーザーが会社の OneDrive のドキュメントにアクセスしたときに、プロンプトが表示されます。
##  <a name="managing-user-accounts-on-the-device"></a>デバイスのユーザー アカウントの管理

Intune では、アプリ保護ポリシーをデバイスごとに 1 つのユーザー アカウントに展開することがサポートされます。

* 2 つ目のユーザーがデバイスでブロックされるかどうかは、使用中のアプリによって決まります。 ただし、どの場合でも、ポリシーの影響を受けるのは、アプリ保護ポリシーが適用される最初のユーザーのみです。

  * **Microsoft Word**、**Excel**、**PowerPoint** は、追加のユーザー アカウントへのアクセスをブロックしません。 ただし、ユーザー アカウントは、アプリ保護ポリシーの影響を受けません。

  * **OneDrive アプリと Outlook アプリ**では、作業アカウントは 1 つだけ使用できます。  作業アカウントを複数追加しようとしても、これらのアプリでブロックされます。  ただし、デバイスからユーザーを削除し、デバイスに別のユーザーを追加することができます。


* アプリ保護ポリシーが展開される前に、デバイスに複数のユーザー アカウントが存在していることがあります。 この場合、アプリ保護ポリシーが展開される最初のアカウントは、Intune アプリ保護ポリシーによって管理されます。


Intune が複数のユーザー アカウントを処理する方法については、次のサンプル シナリオをご覧ください。

ユーザー A は、**会社 X** と**会社 Y** という 2 つの会社で働いています。ユーザー A は各会社の作業アカウントを持っており、どちらの会社も Intune を使用してアプリ保護ポリシーを展開しています。 **会社 X** は、**会社 Y** の**前に**アプリ保護ポリシーを展開しています。アプリ保護ポリシーは、**会社 X** に関連付けられたアカウントに適用されますが、会社 Y に関連付けられたアカウントには適用されません。会社 Y のユーザー アカウントをアプリ保護ポリシーで管理するには、ユーザー A が、会社 X のユーザー アカウントを削除する必要があります。
### <a name="adding-a-second-account"></a>2 つ目のアカウントの追加
####  <a name="android"></a>Android
既存のアカウントを削除して新しいアカウントを追加するためのプロンプトが表示される場合があります。  既存のアカウントを削除するには、**[設定] &gt; [全般] &gt; [アプリケーション マネージャー] &gt; [会社のポータル] の順に選択します。次に [データのクリア] を選択します。**

![エラー メッセージとアカウントの削除手順のスクリーンショット](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Azure Information Protection アプリ (旧称: Rights Management 共有アプリ) でメディア ファイルを表示する
Android デバイスで会社の AV、PDF、および画像ファイルを表示するには、[Azure Information Protection アプリ](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)を使用します。

このアプリは、Google Play ストアからダウンロードします。  

次のファイルの種類がサポートされます。

* **音声:** AAC LC、HE-AACv1 (AAC+)、HE-AACv2 (enhanced AAC+)、AAC ELD (enhanced low delay AAC)、AMR-NB、AMR-WB、FLAC、MP3、MIDI、Ogg Vorbis、PCM/WAVE。
* **ビデオ:** H.263、H.264 AVC、MPEG-4 SP、VP8。
* **画像:** jpg、pjpg、png、ppng、bmp、pbmp、gif、pgif、jpeg、pjpeg。
* **ドキュメント:** PDF、PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>テキスト</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pfile は、保護されたファイルの一般的な "ラッパー" 形式です。 暗号化されたコンテンツと、Azure Information Protection のライセンスをカプセル化します。 任意のファイルの種類を保護できます。 | XML、CSV などのテキスト ファイルは、保護されているときでもアプリで開いて表示できます。 ファイルの種類: txt、ptxt、csv、pcsv、log、plog、xml、pxml。 |

---------------
## <a name="next-steps"></a>次のステップ
[アプリ保護ポリシーを使用して iOS アプリを管理するときの注意点](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>関連項目
[Microsoft Intune でのアプリ保護ポリシーの作成と展開](app-protection-policies.md)
