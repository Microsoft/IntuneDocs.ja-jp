---
title: Android ユーザーがアプリを入手する方法
description: エンド ユーザーが Android アプリを入手する方法
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 960c440372613fed2c92ce00c604d97e1f122e8f
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71239833"
---
# <a name="how-your-android-users-get-their-apps"></a>Android ユーザーがアプリを入手する方法

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

この記事は、Microsoft Intune を通して配布されたアプリを Android エンド ユーザーがどこでどのように取得するかについて理解するのに役立ちます。 この情報はデバイスの種類 (Android ネイティブ デバイスや Samsung Knox Standard デバイス) によって異なる可能性があります。

## <a name="native-non-samsung-knox-standard-android-devices"></a>ネイティブ (Samsung KNOX Standard 以外) Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 通知が表示されます。この通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。 | ユーザーがポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示されます。 ここでインストールを始めます。|
| Required apps      | ユーザーには、アプリをインストールする必要があることを示す通知が表示されます。この通知を非表示にすることはできません。 通知をタップしてインストールを開始します。 インストールが成功すると、通知は表示されなくなります。    | ユーザーには、アプリをインストールする必要があることを示す通知が表示されます。この通知を非表示にすることはできません。 ユーザーが通知をタップすると、Play ストアのアプリのページが表示されます。 ここでインストールを始めます。 インストールが成功すると、通知は表示されなくなります。 |

[LOB アプリ](lob-apps-android.md)をインストールするには、エンド ユーザーは、不明なソースからのインストールを許可する必要があります。 通常、この設定は 2 つの異なる場所に表示されます。

* **Android 7.1.2 以前**: **[設定]**  >  **[セキュリティ]**  >  **[不明なソース]**
* **Android 8.0 以降**: **[設定]**  >  **[Apps & notifications]\(アプリと通知\)**  >  **[Special app access]\(特別なアプリ アクセス\)**  >  **[Install unknown apps]\(不明なアプリのインストール\)**  >  **[ポータル サイト]**  >  **[Allow from this source]\(このソースからは許可する\)**

許可が必要になった場合、ポータル サイト アプリがエンド ユーザーに通知し、該当する設定画面まで直接誘導します。 

## <a name="samsung-knox-standard-android-devices"></a>Samsung KNOX Standard Android デバイス

| アプリの種類 | 基幹業務 (LOB) アプリ | Play ストア アプリ  |
| ------------- |-------------| -----|
| Available apps      | ポータル サイトで **[インストール]** をタップします。 アプリがインストールされます。ユーザーによる操作は不要です。 | ユーザーがポータル サイトでアプリをタップすると、Play ストアでアプリのページが表示されます。 ここでインストールを始めます。|
| Required apps      | アプリがインストールされます。ユーザーによる操作は不要です。    | ユーザーには、アプリをインストールする必要があることを示す通知が表示されます。この通知を非表示にすることはできません。 ユーザーが通知をタップすると、Play ストアのアプリのページが表示されます。 ここでインストールを始めます。 インストールが成功すると、通知は表示されなくなります。 |

アプリは、以下に示すように管理することも管理外にすることも可能です。 アプリを管理するプロセスは、すべての種類の Android デバイスで共通です。

**マネージド アプリ** - これらのアプリはポリシーによって管理されます。 Intune で "ラップ" されているか、Intune App SDK でビルドされています。 These apps can be managed by Intune, and application policies can be applied to them.

**アンマネージド アプリ** - これらのアプリはポリシーによって管理されません。 Intune によってラップされていないか、Intune App SDK を組み込まれていません。 これらのアプリにアプリケーション ポリシーを適用することはできません。

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Zebra Mobility Extensions を含む Zebra デバイス

Intune では、Zebra Mobility Extensions (MX) ツールキットを使用して、デバイス管理者によって管理されている Zebra デバイスにアプリがサイレント インストールされます。 この機能を使用すると、ユーザーの介入なしに、Zebra デバイス上のアプリを展開および更新することができます。 デバイスの MX のバージョンが 4.2 またはそれ以前の場合、アプリはサイレント インストールされません。 詳細については、Zebra の Web サイトの「[MX の完全な機能のマトリックス](http://techdocs.zebra.com/mx/compatibility/)」を参照してください。

Zebra デバイスに展開された LOB アプリは、パブリックな場所からデバイスにインストールされる必要があります。 .apk アプリ パッケージには、デバイス上のパブリック ストレージにもアクセスできる他のアプリやサービスでアクセスできる場合があります。 通常、このアクセスは、アプリのダウンロードが完了してからインストールが開始されるまでの短い期間です。 この期間に、タイミング攻撃を受ける可能性があります。 たとえば、この期間中に .apk パッケージが変更される場合があります。 Intune では、.apk がパブリック ストレージに存在する時間が最小限に抑えられ、署名されていないアプリのインストールは許可されません。 セキュリティ リスクを最小限に抑えるため、アップロードする .apk ファイルに機密情報が含まれていないことを確認してください。

## <a name="see-also"></a>関連項目

[Microsoft Intune でアプリを追加する](apps-add.md)

[iOS ユーザーがアプリを入手する方法](end-user-apps-ios.md)

[Windows ユーザーがアプリを入手する方法](end-user-apps-windows.md)
