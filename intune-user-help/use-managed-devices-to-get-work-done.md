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
ms.openlocfilehash: 2c0d3484311d044842daf6718b306d45fc93edf2
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545941"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>職場または学校のリソースにアクセスするためのデバイスを登録します。
デバイスを登録し、電子メールおよびアプリへのアクセス、Intune ポータル サイト アプリまたは Microsoft Intune のアプリをインストールする必要があります。 登録すると、パスワード、PIN、および暗号化など、組織が構成される基本的な管理ポリシーがデバイスに適用されます。 デバイスの設定を使用して、すべての組織の要件を満たしていると事実上どこから職場の情報を安全にアクセスできます。  

ポータル サイトと Microsoft Intune のアプリでは、デバイスの設定が、組織のポリシーと一致することを確認してセキュリティで保護された登録済みデバイスを保持します。 

ポータル サイト アプリでは次も行えます。  
* 独立した、個人と職場の情報を保持します。  
* 検索して関連する作業と学校のアプリをインストールできるようになります。   

## <a name="get-the-apps"></a>アプリを入手する
ポータル サイトを取得するには:

- プラットフォーム固有のアプリ ストアからポータル サイト アプリをインストールします。 場合によっては、組織がポータル サイト アプリをインストールします。  
- 移動して、[ポータル サイト web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)ブラウザーから、アプリにアクセスします。  

場合は、Microsoft Intune のアプリを使用する必要がありますが、組織はインストールします。  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>ユーザーが登録した場合に会社が確認できる情報
デバイスの登録後、組織のサポート スタッフは作業に関連する情報をのみ参照できます。 ユーザーの個人情報を確認することはできません。 場合は、職場で使用される個人のデバイスを登録する[について正確に把握でき、見なすことはできません](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)します。  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>アプリと Web サイトの違い
ポータル サイト アプリでは、Windows 10、iOS、macOS、Android デバイスおよび使用できます。 これは、デバイスのそれぞれのプラットフォームとシームレスに統合します。 Web サイト バージョンには任意のデバイスからアクセスでき、使用しているデバイスに関係なく同じ共通のエクスペリエンスが提供されます。 

Microsoft Intune のアプリは、企業所有の Android デバイス用です。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>ポータル サイトでは、デバイスの種類を登録できますか。
- iOS (iPhone や iPad など) および macOS (MacBook や iMac など) を使用する Apple デバイス
- Android デバイス
- Windows デバイス
    - Windows 10 Mobile
    - [Windows] 10 Desktop
    - Windows Phone 8.1
    - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Microsoft Intune のアプリでは、デバイスの種類を登録できますか。  
アプリで使用する組織がセットアップされている企業所有の Android デバイスを登録することができます。 アプリには、Android 6.0 以降がサポートしています。 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>ポータル サイトからコンピューターまたはデバイスを削除できますか。
ポータル サイトのコンピューターまたはデバイスは、削除またはリセットできます。 **削除**と**リセット**には違いがあります。

ポータル サイトからコンピューターまたはデバイスを削除すると、そのデバイスは Intune から登録解除されます。 登録が解除されると、そのデバイスからポータル サイトにはアクセスできなくなります。また、一部の会社データがデバイスから削除される場合があります。 ポータル サイトからデバイスを削除する方法については、次のリンクを参照してください。  

- [Android デバイスの登録解除](unenroll-your-device-from-intune-android.md)
- [iOS デバイスの登録解除](unenroll-your-device-from-intune-ios.md)
- [macOS デバイスの登録解除](unenroll-your-device-from-intune-macos.md)
- [Windows デバイスの登録解除](unenroll-your-device-from-intune-windows.md)

コンピューターまたはデバイスをリセットすると、ポータル サイトによって、そのコンピューターまたはデバイスの製造元の既定の設定へのリセットが試みられます。 デバイスをリセットすると、デバイスから会社と個人のデータがすべて削除されます。 デバイスを紛失した場合、ポータル サイトの Web サイトからリモートでリセットすることもできます。  

デバイスをリセットする方法については、次を参照してください。[ポータル サイト web サイトからデバイスをリセット](reset-erase-your-device-cpwebsite.md)します。  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>できます削除するコンピューターまたはデバイスを Microsoft Intune のアプリからでしょうか。
いいえ、Microsoft Intune のアプリから会社所有のデバイスを削除するための方法はありません。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>場合、ポータル サイトまたは Microsoft Intune のアプリでデバイスを表示することはできませんか。
デバイスを表示するには、ポータル サイトに追加する必要があります。 管理者から推奨されたポータル サイトを開き、ご利用のデバイス向けの手順に従ってください。 会社が所有および管理しているデバイスは表示されません。

Microsoft Intune のアプリを使用している場合は、現在使用しているデバイスのみ表示されます。 その他の登録済みデバイスは、アプリで表示されません。  

## <a name="where-else-can-i-go-for-help"></a>サポートを受けられるその他の場所  
一般的な問題と質問をトラブルシューティングするには、これらのプラットフォームに固有のドキュメントをご覧ください。  

- [Android デバイスに関する一般的な問題を解決する](check-compliance-on-your-device-android.md)  
- [iOS デバイスに関する一般的な問題を解決する](troubleshoot-your-device-ios.md)
- [macOS デバイスに関する一般的な問題を解決する](troubleshoot-your-device-macos.md)
- [Windows デバイスに関する一般的な問題を解決する](troubleshoot-your-device-windows.md)

サポート担当者に連絡することができますも。 ポータル サイトと Microsoft Intune アプリ ヘルプを提供し、連絡先情報や問題を報告する方法を示すページをサポートしています。 連絡先情報は、大きな組織で使用できるも[ポータル サイト web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)します。  

## <a name="next-steps"></a>次の手順  

以降では、デバイスのプラットフォームに固有の登録、ヘルプを取得するには。  

- [Android デバイスを使用する](using-your-android-device-with-intune.md)
- [iOS デバイスを使用する](using-your-ios-device-with-intune.md)
- [macOS デバイスを使用する](using-your-macos-device-with-intune.md)
- [Windows デバイスを使用する](using-your-windows-device-with-intune.md)
- [ポータル Web サイトを使用する](using-the-intune-company-portal-website.md)


