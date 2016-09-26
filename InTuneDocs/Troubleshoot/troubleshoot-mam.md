---
title:
- "モバイル アプリケーション管理に関するトラブルシューティング | Microsoft Intune"
description: 
keywords: 
author: karaman
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: 9cfb3694b2fae919fd0554a6e21b497cdcf19c72
ms.openlocfilehash: f33e8de82ee07bb4571a5bfaff63af72f9086376


---

# モバイル アプリケーション管理に関するトラブルシューティング

モバイル アプリケーション管理に関して問題がある場合は、まずこのトピックを読んでください。 このトピックでは、発生する可能性がある一般的な問題とその解決策が示されています。


**問題:** Azure コンソールからの登録ポリシーのない MAM が、iOS および Android デバイスの Skype for Business アプリに適用されない。

解決方法: 先進認証を使用するように Skype for Business を設定する必要があります。  「[Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)」 (テナントで先進認証を有効にする) の説明に従って、Skype に先進認証を設定してください。

**問題:** 登録ポリシーのない MAM が、すべてのユーザーのすべての (サポートされる Office アプリ)[https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners] に適用されない。
 
解決方法: ユーザーに Intune のライセンスがあることを確認します。  

**問題:** IT 管理者ユーザーが Azure ポータルで MAM ポリシーを構成できない

解決方法: 次のロールには Azure ポータルへのアクセス権があります。

- グローバル管理者: [Office ポータル](http://portal.office.com/)で設定できます。
- 所有者: [Azure ポータル](https://portal.azure.com/)で設定できます。
- 共同作成者: [Azure ポータル](https://portal.azure.com/)で設定できます。

これらのロールの設定については、「[Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)」をご覧ください。 

**問題:** 最近 MAM ポリシーの対象にしたユーザーがアプリ レポートに表示されない。

解決方法: 新しく MAM ポリシーの対象になったユーザーは、対象ユーザーとしてレポートに表示されるまでに最大で 24 時間かかります。 

**問題:** ポリシーの変更または更新が適用されるまでに最大 8 時間かかる。  

解決方法: エンド ユーザーは、いったんアプリをログアウトしてから再びログインすることで、サービスと強制的に同期できます。  

**問題:** MAM ポリシーが Apple DEP デバイスに適用されない

解決方法: Apple Device Enrollment Program (DEP) でユーザー アフィニティを使用していることを確認してください。 DEP でのユーザー認証を必要とするすべてのアプリにはユーザー アフィニティが必要です。
iOS DEP 登録の詳細については、「[会社所有のデバイス登録プログラムによる iOS デバイスの登録](https://docs.microsoft.com/en-us/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)」をご覧ください。


### 関連項目
- [モバイル アプリケーション管理のセットアップの検証](https://docs.microsoft.com/en-us/intune/deploy-use/validate-mobile-application-management)
- [Microsoft Intune でのモバイル アプリ管理ポリシーの作成および展開](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) 





<!--HONumber=Sep16_HO2-->


