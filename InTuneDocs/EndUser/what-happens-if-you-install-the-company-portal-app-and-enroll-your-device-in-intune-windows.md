---
title: "Windows 用ポータル サイト アプリをインストールする | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 0e6b7ae1794ff0857dfb203eb3c67d7ba494bd8e
ms.openlocfilehash: bde2ccc0c170a85e926357d54fcf4ffe6ee50fd9
ms.lasthandoff: 02/21/2017


---


# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>ポータル サイト アプリをインストールし、Intune に Windows デバイスを登録するとどうなりますか。

ポータル サイト アプリをインストールして、Windows または Windows Phone デバイスを登録する場合、デバイスを IT 管理者が管理して、会社または学校のデータを保護することができるようになります。 このトピックでは、Windows 10 より前のデバイスの動作について説明します。 Windows 10 デバイスについては、[関連項目](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md)を参照してください。

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>登録後にすべての Windows デバイスでできるようになること
Intune に Windows または Windows Phone デバイスを登録すると、次のことができます。

-   会社のネットワークにアクセスし、電子メールや仕事用のファイルにアクセスする。

-   ポータル Web サイトから会社のアプリを取得する。 (__注__: Windows 7 と Windows Vista の場合は、ポータル Web サイトからしか会社用アプリを取得できません。)

-   会社または学校用の電子メール アカウントを自動的にセットアップする。

-   携帯電話の紛失や盗難にあった場合、電話を工場出荷時設定にリセットする。

デバイスを登録すると、IT 管理者に以下のようなアクセス許可が付与されます。

-   デバイスを製造元の既定設定にリセットする。 この操作は、デバイスの紛失時または盗難時に役立ちます。

-   会社に関連するファイルとビジネス アプリケーションのみを削除する。 *個人データや設定は削除されません。*

-   IT 管理者は、ユーザーが個人的にインストールしたソフトウェアを含め、デバイスにインストールされているすべてのソフトウェアを確認できます。

-   会社のデータを保護できるように、デバイスのパスワードや暗証番号 (PIN) の入力を求めるなどの要件をデバイスに設定してください。 IT 管理者は、パスワードの試行回数の制限、または試行回数を超えた場合のデバイスのロックなども設定できます。

-   デバイスの紛失または盗難時に会社のデータを保護するため、デバイスのデータを暗号化する必要があります。

-   条項に同意する必要があります。

-   会社に関連するデータの撮影を禁止する。

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>登録後にすべての Windows PC でできるようになること

-  コンピューターにソフトウェアがインストールされ、IT 管理者がそのコンピューターを管理できるようになり、ユーザーがアプリケーションやサポート情報などの会社のリソースを入手できるようになります。 このソフトウェアは、IT 管理者によって自動更新に設定される可能性があります。

-  コンピューターには、Intune Endpoint Protection がインストールされている可能性があります。 このソフトウェアは、ウイルスとマルウェアが存在しないかをチェックします。

-  IT 管理者は、ユーザー コンピューターのハード ドライブにあるデータを収集または削除することができます。

-  IT 管理者は、コンピューターにアプリケーションと更新プログラムをインストールすることができます。

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>デバイスの登録後&8; 時間ごとに生じる動作

登録済みのデバイスは、約&8; 時間ごとに以下のことを行います。

-   IT 管理者が許可したポリシーまたはアプリケーションの更新プログラムをダウンロードする。

-   ハードウェアのインベントリの更新情報を送信する。

-   会社のアプリのインベントリの更新情報を送信する。

ご質問がございましたら、IT 管理者に問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

