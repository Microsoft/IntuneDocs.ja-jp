---
title: Intune で Android デバイスを登録する
titleSuffix: Microsoft Intune
description: Intune で Android デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 363a7d0ef32aee0c21c6e5cecbd55cc3087f4613
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568675"
---
# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 管理者は、次の Android デバイスを管理できます。
- Android デバイス (Samsung KNOX Standard デバイスを含む)
- Android Enterprise デバイスには次のものが含まれます。
    - **Android Enterprise 仕事用プロファイル デバイス**:会社のデータにアクセスする権限が与えられた個人用デバイス。 管理者は職場のアカウント、アプリ、データにアクセスできます。 デバイスに入っている個人のデータは仕事のデータから分離され、個人の設定やデータが管理者に操作されることはありません。 
    - **Android Enterprise 専用デバイス**:デジタル サイネージ、チケット印刷、在庫管理など、会社が所有する単回使用デバイス。 管理者はデバイスの使用を厳しく管理し、限られたアプリと Web リンクのみ許可します。 また、ユーザーがデバイスに他のアプリを追加したり、他の操作を行ったりできないようになっています。
    - **Android Enterprise のフル マネージド デバイス**:仕事のためにのみ使用し、私事には使用しない会社所有の単一ユーザー デバイス。 管理者はデバイス全体を管理し、仕事用プロファイルで利用できないポリシー制御を強制できます。 

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](mdm-authority-set.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune では、既定で Android および Samsung Knox Standard デバイスの登録が許可されています。 前提条件を満たした後に、管理者は、[デバイスを登録する方法をユーザーに通知](/intune-user-help/enroll-your-device-in-intune-android)する必要があります。

ユーザーが登録した後に、[コンプライアンス ポリシーの割り当て](compliance-policy-create-android.md)、[アプリの管理](app-management.md)など、Intune でのデバイスの管理を開始することができます。

その他のユーザー タスクについては、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](end-user-educate.md)
- [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Android デバイスをブロックする場合や、個人所有の Android デバイスのみの登録をブロックする場合は、「[Set device type restrictions](enrollment-restrictions-set.md)」 (デバイスの種類の制限を設定する) を参照してください。

## <a name="set-up-android-enterprise-enrollment"></a>Android Enterprise の登録を設定する

Android Enterprise には、最新のセキュリティで保護された機能をユーザーに提供する一連の登録オプションがあります。 Android Enterprise 登録オプションには、仕事用プロファイル、フル マネージド デバイス、専用デバイスがあります。

- [Android Enterprise の仕事用プロファイルの登録を設定する](android-work-profile-enroll.md)
- [Android Enterprise の専用デバイスの登録を設定する](android-kiosk-enroll.md)
- [Android Enterprise のフル マネージドの登録を設定する](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Samsung KNOX デバイス登録時のエンドユーザー エクスペリエンス

Samsung Knox Standard デバイスが Intune によるマルチ ユーザー管理のサポート対象になりました。 つまり、ユーザーは Azure AD 資格情報を使用してデバイスに対してサインインしたりサインアウトしたりすることができます。 使用中かどうかに関係なく、デバイスは中央管理されます。 サインインしたユーザーはアプリにアクセスできるのに加え、適用されるポリシーを受け取ります。 ユーザーがサインアウトすると、すべてのアプリ データが消去されます。

Samsung Knox デバイスを登録する場合、次のいくつかの考慮事項があります。
-   ポリシーで PIN が要求されない場合でも、デバイスを登録するには少なくとも 4 桁の PIN が必要です。 デバイスに PIN がない場合、ユーザーに作成を求めるメッセージが表示されます。
-   Workplace Join Certificates (WPJ) に関するユーザーの操作はありません。
-   ユーザーにサービス登録情報とアプリで実行できる内容を示すメッセージが表示されます。
-   ユーザーに Knox 登録情報と Knox で実行できる内容を示すメッセージが表示されます。
-   暗号化ポリシーが適用されている場合、ユーザーはデバイス パスコードの 6 文字の複雑なパスワードを設定する必要があります。
-   会社のリソースへのアクセスのサービスでプッシュされる証明書のインストールをユーザーに求める追加のメッセージは表示されません。
- 一部の古い Knox デバイスでは、会社のリソースへのアクセスで使用される追加の証明書を求めるメッセージがユーザーに表示されます。
- Samsung Mini デバイスで WPJ のインストールに失敗し、"**証明書が見つかりません**" または "**デバイスを登録できません**" などのエラーが表示された場合は、最新の Samsung Firmware Updates をインストールします。

## <a name="next-steps"></a>次の手順

- [Android Enterprise の仕事用プロファイルの登録を設定する](android-work-profile-enroll.md)
- [Android Enterprise の専用デバイスの登録を設定する](android-kiosk-enroll.md)
- [Android Enterprise のフル マネージドの登録を設定する](android-fully-managed-enroll.md)
