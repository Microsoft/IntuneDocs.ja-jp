---
title: Intune で Android デバイスを登録する
titlesuffix: Microsoft Intune
description: Intune で Android デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f03c60c12bfd759c738de50d320787bf4b85f99d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909186"
---
# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 管理者は、次の Android デバイスを管理できます。
- Android デバイス (Samsung KNOX Standard デバイスを含む)
- Android Enterprise デバイス ([Android 仕事用プロファイルのデバイス](#enable-enrollment-of-android-for-work-devices)および Android Kiosk デバイスを含む)

Samsung Knox Standard を実行するデバイスが、Intune によるマルチ ユーザー管理のサポート対象になりました。 つまり、ユーザーは Azure AD 資格情報を使用してデバイスに対してサインインしたりサインアウトしたりすることができます。 使用中かどうかに関係なく、デバイスは中央管理されます。 サインインしたユーザーはアプリにアクセスできるのに加え、適用されるポリシーを受け取ります。 ユーザーがサインアウトすると、すべてのアプリ データがクリアされます。

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](mdm-authority-set.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune では、既定で Android および Samsung Knox Standard デバイスの登録が許可されています。 前提条件を満たした後に、管理者は、[デバイスを登録する方法をユーザーに通知](/intune-user-help/enroll-your-device-in-intune-android.md)する必要があります。

ユーザーが登録した後に、[コンプライアンス ポリシーの割り当て](compliance-policy-create-android.md)、[アプリの管理](app-management.md)など、Intune でのデバイスの管理を開始することができます。

その他のユーザー タスクについては、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](end-user-educate.md)
- [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Android デバイスをブロックする場合や、個人所有の Android デバイスのみの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

## <a name="set-up-android-enterprise-enrollment"></a>Android Enterprise の登録の設定

Android Enterprise は、仕事用のアプリとデータを含む仕事用プロファイルから個人用アプリとデータを分離する、Android デバイスの機能とサービスのセットです。 Android Enterprise デバイス (仕事用プロファイルのデバイスおよび Kiosk デバイスを含む) 

Android Enterprise デバイスの登録をセットアップするには、まず[を Intune に Android Enterprise を接続](connect-intune-android-enterprise.md)します。 この手順を完了すると、次の操作を実行できます。

[Android 仕事用プロファイルの登録の設定](android-work-profile-enroll.md)
[Android Kiosk の登録の設定](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Samsung KNOX デバイス登録時のエンドユーザー エクスペリエンス
Samsung Knox デバイスを登録する場合、次のいくつかの考慮事項があります。
-   ポリシーで PIN が要求されない場合でも、デバイスを登録するには少なくとも 4 桁の PIN が必要です。 デバイスに PIN がない場合、ユーザーに作成を求めるメッセージが表示されます。
-   Workplace Join Certificates (WPJ) に関するユーザーの操作はありません。
-   ユーザーにサービス登録情報とアプリで実行できる内容を示すメッセージが表示されます。
-   ユーザーに Knox 登録情報と Knox で実行できる内容を示すメッセージが表示されます。
-   暗号化ポリシーが適用されている場合、ユーザーはデバイス パスコードの 6 文字の複雑なパスワードを設定する必要があります。
-   会社のリソースへのアクセスのサービスでプッシュされる証明書のインストールをユーザーに求める追加のメッセージは表示されません。
- 一部の古い Knox デバイスでは、会社のリソースへのアクセスで使用される追加の証明書を求めるメッセージがユーザーに表示されます。
- Samsung Mini デバイスで WPJ のインストールに失敗し、"**証明書が見つかりません**" または "**デバイスを登録できません**" などのエラーが表示された場合は、最新の Samsung Firmware Updates をインストールします。
