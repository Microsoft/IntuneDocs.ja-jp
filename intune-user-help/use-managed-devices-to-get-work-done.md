---
title: マネージド デバイスを使用して作業する | Microsoft Docs
description: デバイスを Intune による管理対象として登録することの意味を理解します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883864"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>職場または学校のリソースにアクセスするためにデバイスを登録する
デバイスを登録し、電子メールとアプリにアクセスできるようにするには、Intune ポータルサイトアプリまたは Microsoft Intune アプリのいずれかをインストールする必要があります。 登録すると、組織が構成した基本的な管理ポリシー (パスワード、PIN、暗号化など) がデバイスに適用されます。 デバイス設定がすべての組織の要件を満たしたら、実質的にどこからでも作業情報に安全にアクセスできます。  

ポータルサイトアプリと Microsoft Intune アプリは、デバイスの設定が組織のポリシーと一致するようにして、登録されているデバイスの安全を維持します。 

ポータル サイト アプリでは次も行えます。  
* 個人情報と勤務先情報を別々に保管します。  
* を使用すると、関連する職場や学校のアプリを簡単に検索してインストールできます。   

## <a name="get-the-apps"></a>アプリを入手する
ポータル サイトを取得するには:

- プラットフォーム固有のアプリストアからポータルサイトアプリをインストールします。 場合によっては、ポータルサイトアプリが組織によってインストールされます。  
- ブラウザーからアプリにアクセスするには、[ポータルサイト web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)にアクセスします。  

Microsoft Intune アプリを使用する必要がある場合は、組織によってインストールされます。  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>ユーザーが登録した場合に会社が確認できる情報
デバイスが登録されると、組織のサポート担当者は、作業に関連する情報のみを表示できます。 ユーザーの個人情報を確認することはできません。 職場で使用するために個人のデバイスを登録している場合は、[表示できることとできないことを正確に説明して](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)ください。  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>アプリと Web サイトの違い
ポータルサイトアプリは、Windows 10、iOS、macOS、および Android デバイスで使用できます。 デバイスのプラットフォームとシームレスに統合されます。 Web サイト バージョンには任意のデバイスからアクセスでき、使用しているデバイスに関係なく同じ共通のエクスペリエンスが提供されます。 

Microsoft Intune アプリは、企業所有の Android デバイス用です。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>ポータルサイトで登録できるデバイスの種類
- iOS (iPhone や iPad など) および macOS (MacBook や iMac など) を使用する Apple デバイス
- Android デバイス
- Windows デバイス
  - Windows 10 Mobile
  - [Windows] 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Microsoft Intune アプリに登録できるデバイスの種類  
組織がアプリで使用するように設定した企業所有の Android デバイスを登録できます。 このアプリでは、Android 6.0 以降がサポートされています。 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>ポータル サイトからコンピューターまたはデバイスを削除できますか。
ポータル サイトのコンピューターまたはデバイスは、削除またはリセットできます。 **削除**と**リセット**には違いがあります。

ポータル サイトからコンピューターまたはデバイスを削除すると、そのデバイスは Intune から登録解除されます。 登録が解除されると、そのデバイスからポータル サイトにはアクセスできなくなります。また、一部の会社データがデバイスから削除される場合があります。 ポータルサイトからデバイスを削除する方法については、次のリンクを参照してください。  

- [Android デバイスの登録解除](unenroll-your-device-from-intune-android.md)
- [iOS デバイスの登録解除](unenroll-your-device-from-intune-ios.md)
- [macOS デバイスの登録解除](unenroll-your-device-from-intune-macos.md)
- [Windows デバイスの登録解除](unenroll-your-device-from-intune-windows.md)

コンピューターまたはデバイスをリセットすると、ポータル サイトによって、そのコンピューターまたはデバイスの製造元の既定の設定へのリセットが試みられます。 デバイスをリセットすると、デバイスから会社と個人のデータがすべて削除されます。 デバイスを紛失した場合、ポータル サイトの Web サイトからリモートでリセットすることもできます。  

デバイスをリセットする方法については、[ポータルサイト web サイトからデバイスをリセット](reset-erase-your-device-cpwebsite.md)する方法に関するページを参照してください。  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Microsoft Intune アプリからコンピューターまたはデバイスを削除できますか。
いいえ。 Microsoft Intune アプリから会社所有のデバイスを削除する方法はありません。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>ポータルサイトまたは Microsoft Intune アプリにデバイスが表示されない場合はどうすればよいですか。
デバイスを表示するには、ポータル サイトに追加する必要があります。 管理者から推奨されたポータル サイトを開き、ご利用のデバイス向けの手順に従ってください。 会社が所有および管理しているデバイスは表示されません。

Microsoft Intune アプリを使用している場合は、現在使用しているデバイスのみが表示されます。 その他の登録済みデバイスは、アプリでは表示されません。  

## <a name="where-else-can-i-go-for-help"></a>サポートを受けられるその他の場所  
一般的な問題と質問のトラブルシューティングを行うには、次のプラットフォーム固有のドキュメントを確認してください。  

- [Android デバイスに関する一般的な問題を解決する](check-compliance-on-your-device-android.md)  
- [iOS デバイスに関する一般的な問題を解決する](troubleshoot-your-device-ios.md)
- [macOS デバイスに関する一般的な問題を解決する](troubleshoot-your-device-macos.md)
- [Windows デバイスに関する一般的な問題を解決する](troubleshoot-your-device-windows.md)

サポート担当者に連絡することもできます。 ポータルサイトおよび Microsoft Intune アプリには、連絡先情報を一覧表示し、問題を報告する方法を示すヘルプとサポートページが用意されています。 連絡先情報は、お客様の組織の[ポータルサイト web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)でもご利用いただけます。  

## <a name="next-steps"></a>次の手順  

デバイスのプラットフォームに固有の、登録からのヘルプを取得します。  

- [Android デバイスを使用する](using-your-android-device-with-intune.md)
- [iOS デバイスを使用する](using-your-ios-device-with-intune.md)
- [macOS デバイスを使用する](using-your-macos-device-with-intune.md)
- [Windows デバイスを使用する](using-your-windows-device-with-intune.md)
- [ポータル Web サイトを使用する](using-the-intune-company-portal-website.md)


