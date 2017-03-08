---
title: "デバイスに必要な証明書がない | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 207297601634f390051a6345b96bf09e1d031747
ms.openlocfilehash: 6b37cede797f965b82c067b274517277d8597939
ms.lasthandoff: 01/12/2017

---


# <a name="your-device-is-missing-a-required-certificate"></a>デバイスに必要な証明書がない

## <a name="whats-a-certificate"></a>証明書について

[暗号化](https://technet.microsoft.com/en-us/library/cc962030.aspx)は、情報にセキュリティ保護を提供する技術です。 従来、暗号化は、コード化されたメッセージを渡して[通信の機密性が保たれるようにする](https://technet.microsoft.com/en-us/library/cc962019.aspx)ために使用されてきました。 最も単純な形式の暗号化では、文字を置き換えるか入れ替えることで、コード化されたメッセージを読み取り不可能にするか、スクランブル化するか、隠しています。 デコード キー、つまり_証明書_を持つユーザーのみが、コード化されたメッセージを元の読み取り可能な形式に変換できます。 Android デバイスでは、Intune で証明書を使用して、デバイスと組織のリソース (電子メールやドキュメントなど) 間の無線通信が安全に行われるようにします。

## <a name="fixing-certificate-issues"></a>証明書の問題の修正

Android デバイスが Intune に登録されておらず、IT 管理者が必要とする特定の証明書がない場合は、ポータル サイト アプリにサインインすることはできません。 サインインしようとすると、次のメッセージが表示されます。

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

まず実行すべき手順は、[デバイスに通常プレインストールされている証明書が不足](your-device-is-missing-a-preinstalled-certificate-android.md)しているかどうかを確認することです。

この手順で解決しない場合、IT 管理者から、[追加のセキュリティのために 2 番目の証明書をインストールするよう要求される](your-device-is-missing-an-IT-required-certificate-android.md)ことがあります。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

