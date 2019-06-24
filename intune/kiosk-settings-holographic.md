---
title: Microsoft Intune での Windows Holographic for Business 用のキオスク設定 - Azure | Microsoft Docs
description: Microsoft Intune でシングル アプリおよびマルチ アプリ キオスクとして Windows Holographic for Business デバイスを構成し、スタート メニューのカスタマイズ、アプリの追加、タスク バーの表示、および Web ブラウザーの構成を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d6366034af09acdbecdc0cb0e670f6d57766b35
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197523"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Intune でキオスクとして実行するための Windows Holographic for Business デバイスの設定

Windows Holographic for Business デバイスでは、シングル アプリ キオスク モード、またはマルチ アプリ キオスク モードで実行するようにこれらのデバイスを構成することができます。 一部の機能は、Windows Holographic for Business ではサポートされていません。

この記事では、Windows Holographic for Business デバイス上で制御できるさまざまな設定について説明します。 モバイル デバイス管理 (MDM) ソリューションの一部として、これらの設定を使用して、Windows Holographic for Business デバイスをキオスク モードで実行するように構成します。

Intune 管理者は、デバイスに対してこれらの設定を作成し、割り当てることができます。

Intune での Windows キオスク機能の詳細については、[キオスク設定の構成](kiosk-settings.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[プロファイルを作成します](kiosk-settings.md#create-the-profile)。

## <a name="single-full-screen-app-kiosks"></a>シングル全画面表示アプリ キオスク

シングル アプリ キオスク モードを選択するときには、次の設定を入力します。

- **[ユーザーのログオンの種類]** : **[ローカル ユーザー アカウント]** を選択して、(デバイスの) ローカル ユーザー アカウントか、キオスク アプリに関連付けられている Microsoft アカウント (MSA) を入力します。 **[自動ログオン]** というユーザー アカウントの種類は、Windows Holographic for Business ではサポートされていません。

- **[アプリケーションの種類]** : **[ストア アプリ]** を選択します。

- **[App to run in kiosk mode]\(キオスク モードで動作するアプリ\)** : **[Add a store app]\(ストア アプリを追加\)** を選択し、一覧からアプリを選択します。

    アプリが何も表示されない場合は、 [クライアント アプリ](apps-add.md)ごとの手順を使用して追加してください。

    **[OK]** を選択して変更を保存します。

## <a name="multi-app-kiosks"></a>マルチ アプリ キオスク

このモードのアプリはスタート メニューから使用できます。 ユーザーはこれらのアプリのみを開くことができます。 マルチ アプリ キオスク モードを選択するときには、次の設定を入力します。

- **[Target Windows 10 in S mode devices]\(S モードのデバイスで Windows 10 を対象にする\)** : **[いいえ]** を選択します。 S モードは、Windows Holographic for Business ではサポートされていません。

- **[ユーザーのログオンの種類]** : 追加したアプリを使用できる 1 つ以上のユーザー アカウントを追加します。 次のようなオプションがあります。 

  - **[自動ログオン]** : Windows Holographic for Business ではサポートされていません。
  - **[ローカル ユーザー アカウント]** : (デバイスの) ローカル ユーザー アカウントを**追加**します。 入力したアカウントは、キオスクへのサインインに使用されます。
  - **[Azure AD user or group (Windows 10, version 1803 and later)]\(Azure AD のユーザーまたはグループ (Windows 10、バージョン 1803 以降)\)** : デバイスにサインインするには、ユーザーの資格情報が必要です。 一覧から Azure AD のユーザーまたはグループを選択するには、 **[追加]** を選択します。 複数のユーザーおよびグループを選択することができます。 **[選択]** を選んで変更を保存します。
  - **[HoloLens の訪問者]** : 訪問者のアカウントはゲスト アカウントであり、「[共有 PC モードの概念](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)」の説明のとおり、ユーザーの資格情報や認証は必要ありません。

- **[アプリケーション]** : キオスク デバイスで実行するアプリを追加します。 複数のアプリを追加することができます。

  - **ストア アプリの追加**: 追加またはとして Intune に配置した既存のアプリを選択します。[クライアント アプリ](apps-add.md)、LOB アプリを含むです。 表示されているすべてのアプリを持っていない場合は多くの Intune サポートしている[アプリの種類](apps-add.md)した[を Intune に追加](store-apps-windows.md)します。
  - **[Add Win32 app]\(Win32 アプリの追加\)** : Windows Holographic for Business ではサポートされていません。
  - **[Add by AUMID]\(AUMID による追加\)** : このオプションを使用して、受信トレイ Windows アプリを追加します。 次のプロパティを入力します。 

    - **[アプリケーション名]** : 必須です。 アプリケーションの名前を入力します。
    - **[アプリケーション ユーザー モデル ID (AUMID)]** : 必須です。 Windows アプリのアプリケーション ユーザー モデル ID (AUMID) を入力します。 この ID を取得する場合は、「[Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)」 (インストール済みアプリのアプリケーション ユーザー モデル ID を見つける) を参照してください。
    - **[タイルのサイズ]** : 必須です。 小、中、全体、大の、アプリ タイルのサイズを選択します。

- **[キオスク ブラウザーの設定]** : Windows Holographic for Business ではサポートされていません。

- **[Use alternative Start layout]\(スタート画面の別のレイアウトを使用する\)** : **[はい]** を選択して、アプリの順序を含む、アプリをスタート メニューに表示する方法を説明する XML ファイルを入力します。 [スタート] メニューでさらにカスタマイズが必要な場合は、このオプションを使用します。 [[スタート画面のレイアウトのカスタマイズとエクスポート]](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) ではいくつかのガイダンスが提供され、Windows Holographic for Business デバイス用の特定の XML ファイルが含まれます。

- **[Windows タスク バー]** : Windows Holographic for Business ではサポートされていません。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Android](device-restrictions-android.md#kiosk)、[Android エンタープライズ](device-restrictions-android-for-work.md#dedicated-device-settings)、および [Windows 10 以降](kiosk-settings-windows.md)のデバイス用にキオスク プロファイルを作成することもできます。
