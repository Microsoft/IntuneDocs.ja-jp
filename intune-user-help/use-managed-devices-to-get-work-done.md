---
title: デバイス登録とは | Microsoft Docs
description: ポータルサイトと Microsoft Intune アプリを使用してデバイスを登録する意味を理解します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/13/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca1776915d50858c28b43a49faa7c737c825c67d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72501860"
---
# <a name="what-is-device-enrollment"></a>デバイス登録とは
デバイスから職場または学校のリソースにアクセスするには、デバイスを Intune ポータルサイトアプリまたは Microsoft Intune アプリに登録する必要があります。 

デバイスの登録時:

* お使いのデバイスは組織に登録されています。 この手順により、組織の電子メール、アプリ、および Wi-fi にアクセスする権限が与えられます。 
* 組織のデバイス管理ポリシーがデバイスに適用されます。 ポリシーには、デバイスのパスワードや暗号化などの要件を含めることができます。 これらの要件の目的は、デバイスと組織のデータを承認されていないアクセスから保護することです。

組織の要件に合わせてデバイスの設定を更新すると、登録が完了します。 職場または学校のアカウントには、事実上どこからでも安全にサインインできます。  

この記事では、アプリを入手する方法、サポートされているデバイス、デバイスを削除またはリセットする方法など、登録に関する他の側面について説明します。  

## <a name="company-portal-and-microsoft-intune-app"></a>ポータルサイトと Microsoft Intune アプリ

ポータルサイトと Microsoft Intune アプリによって、ポリシーや変更の設定が通知されるため、職場または学校へのアクセス権を失うことなくアクションを実行できます。 

ポータルサイトアプリでは個人情報と作業情報を別々に保持するため、生産性を維持し、集中することができます。 また、職場や学校のアプリを利用できるようになるため、作業に関連するものを見つけてインストールすることができます。  

### <a name="get-company-portal"></a>ポータル サイトの取得

場合によっては、組織がデバイスにポータルサイトアプリをインストールすることがあります。 アプリは、Microsoft Store、App Store、Google Play ストアなどのアプリストアからインストールすることもできます。 Web ブラウザーからアプリにアクセスするには、職場または学校のアカウントを使用して[ポータルサイト web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)にサインインします。  

### <a name="get-microsoft-intune-app"></a>Microsoft Intune アプリの取得

Microsoft Intune アプリを使用する必要がある場合は、組織によってデバイスにインストールされます。  

## <a name="whats-the-difference-between-the-apps-and-the-website"></a>アプリと Web サイトの違い
ポータルサイトアプリは、Windows 10、iOS、macOS、および Android デバイスで使用できます。 デバイスのプラットフォームとシームレスに統合されます。 Web サイト バージョンには任意のデバイスからアクセスでき、使用しているデバイスに関係なく同じ共通のエクスペリエンスが提供されます。 

Microsoft Intune アプリは、企業所有の Android デバイス用であり、web サイトはありません。  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>ポータルサイトで登録できるデバイスの種類
ポータルサイトを使用して、次のデバイスを登録できます。  

- Windows デバイス
  - Windows 10 Mobile
  - [Windows] 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1
- Apple デバイス
    - iOS
    - macOS
- Android デバイス


## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Microsoft Intune アプリに登録できるデバイスの種類  
組織がアプリで使用するように設定した企業所有の Android デバイスを登録できます。 このアプリでは、Android 6.0 以降がサポートされています。 

## <a name="can-you-remove-a-device-from-the-company-portal"></a>ポータル サイトからデバイスを削除できますか
ポータルサイトからデバイスを削除またはリセットできます。 **削除**と**リセット**には違いがあります。

デバイスの削除中に、によってデバイスの登録と登録解除がポータルサイトされます。 そのデバイスはポータルサイトにアクセスできなくなります。 職場または学校のデータも削除される可能性があります。 

デバイスのリセットでは、ポータル サイトによって、コンピューターまたはデバイスの製造元の既定の設定へのリセットが試みられます。 すべての職場または学校のデータとすべての個人データがデバイスから削除されます。 リセットは、デバイスを紛失した場合などに便利です。 ポータルサイト web サイトからリモートでリセットできます。  

## <a name="can-you-remove-a-device-from-the-microsoft-intune-app"></a>Microsoft Intune アプリからデバイスを削除できますか。
いいえ。 Microsoft Intune アプリから会社所有のデバイスを削除する方法はありません。  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>ポータルサイトまたは Microsoft Intune アプリにデバイスが表示されない場合はどうすればよいですか。
ポータルサイトにデバイスを表示するには、まず登録する必要があります。 登録後もすべてのデバイスが表示されない場合は、ポータルサイトを使用してアクセスを同期または確認してください。 お客様の会社によって所有および管理されているデバイスは、表示されません。

Microsoft Intune アプリでは、現在使用しているデバイスのみが表示されます。 その他の登録済みデバイスは、アプリでは表示されません。  

## <a name="where-else-can-i-go-for-help"></a>サポートを受けられるその他の場所  
一般的な問題のトラブルシューティングについては、次のプラットフォーム固有のドキュメントをご覧ください。  

- [Android デバイスに関する一般的な問題を解決する](check-compliance-on-your-device-android.md)  
- [iOS デバイスに関する一般的な問題を解決する](troubleshoot-your-device-ios.md)
- [macOS デバイスに関する一般的な問題を解決する](troubleshoot-your-device-macos.md)
- [Windows デバイスに関する一般的な問題を解決する](troubleshoot-your-device-windows.md)

IT サポート担当者に問い合わせることもできます。 ポータルサイトおよび Microsoft Intune アプリには、連絡先情報を一覧表示し、問題を報告する方法を示すヘルプとサポートページが用意されています。 連絡先情報は、お客様の組織の[ポータルサイト web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)でもご利用いただけます。  

## <a name="next-steps"></a>次の手順  

職場または学校アカウントにアクセスする準備ができたら、組織の指示に従ってデバイスを登録します。 次の記事で、詳細な登録ガイダンスを参照することもできます。

* [Windows 10 デバイスを登録する](enroll-windows-10-device.md)
* [Android デバイスを登録する](enroll-device-android-company-portal.md)
* [Android 仕事用プロファイルを使用して登録する](enroll-device-android-work-profile.md)
* [Microsoft Intune アプリを使用して登録する](enroll-device-android-microsoft-intune-app.md)
* [iOS デバイスを登録する](enroll-your-device-in-intune-ios.md)
* [組織で提供される iOS デバイスを登録する](enroll-your-device-dep-ios.md)
* [macOS デバイスを登録する](enroll-your-device-in-intune-macos-cp.md)
* [組織で提供される macOS デバイスを登録する](enroll-company-device-macos.md)


