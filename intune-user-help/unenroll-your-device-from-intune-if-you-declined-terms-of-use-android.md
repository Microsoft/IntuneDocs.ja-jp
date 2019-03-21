---
title: 利用規約を拒否した場合に管理からデバイスを削除する | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbf35b77c843b4dc084916b2c283b6c66d5f066d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "55849235"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>"利用規約" を拒否した場合に管理からデバイスを削除する

ポータル サイト アプリへのサインインの試行中に利用規約を拒否した場合は、次回以降、ポータル サイト アプリにサインインできなくなるため、デバイスを Intune から削除するときは次の "回避策" の手順を実施する必要があります。

ポータル サイト アプリをアンインストールすると、Intune からそのデバイスも削除されます。 デバイスは会社のリソースにアクセスできなくなります。 管理からデバイスを削除した場合の詳細については、「[Intune からデバイスの登録を解除するとどうなりますか。](what-happens-if-you-unenroll-your-device-from-intune-android.md)」を参照してください。

会社のポータル アプリをアンインストールするには、最初に **[Device administrators]** 設定に進み、**[会社のポータル]** をオフにします。 使用している Android デバイスによっては、手順が多少異なる場合があります。

## <a name="removing-the-device-from-the-company-portal-app"></a>ポータル サイト アプリからデバイスを削除する

Intune からデバイスを削除し、ポータル サイト アプリをアンインストールするには:

1.  **[設定]** &gt; **[セキュリティ &amp; 画面のロック]** &gt;**[デバイス管理者]** の順に進みます。

    この手順は、デバイスの登録を解除したらすぐに実行します。

2.  **[会社のポータル]** の横のチェック ボックスの選択を解除 (オフに) します。

    これで、会社のポータル アプリをアンインストールできます。

## <a name="removing-data-collected-by-the-company-portal-app"></a>ポータル サイト アプリによって収集されたデータを削除する

Android 用のポータル サイト アプリによってお使いのデバイスに格納されているすべてのデータを削除するには:

  - [アプリケーション] でアプリをクリックし、"データの消去" ボタンをクリックし、アプリ データを消去します。
  - フォルダー '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' を削除します。


サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。
