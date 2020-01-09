---
title: Microsoft Intune でポリシーを使用してデバイスの機能を制限する - Azure | Microsoft Docs
description: デバイス プロファイルを追加して、Microsoft Intune で Android、macOS、iOS、iPadOS、Windows Phone、および Windows 10 の各デバイスの機能を制限します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c86252030a4baf957077cd889386bb8016554f1
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206569"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune でデバイスの制限設定を構成する



Intune には、管理者が Android、iOS、macOS、および Windows の各デバイスを制御するのに役立つデバイス制限ポリシーが含まれています。 これらの制限を使用して、組織のリソースを保護するための幅広い設定と機能を制御できます。 たとえば、管理者には次の機能があります。

- デバイス カメラを許可またはブロックする
- Google Play、アプリ ストア、ドキュメントの表示、およびゲームへのアクセスを制御する
- 組み込みアプリをブロックするか、許可または禁止するアプリの一覧を作成する
- クラウドとストレージ アカウントへのファイルのバックアップを許可または禁止する
- パスワードの最小文字数を設定し、単純なパスワードをブロックする

これらの機能は Intune で使用できます。また、管理者が構成できます。 Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後、そのプロファイルをお客様の組織のデバイスにプッシュまたは展開できます。

この記事では、デバイス制限プロファイルの作成方法について説明します。 さまざまなプラットフォームで使用できるすべての設定を確認することもできます。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**:ポリシーのわかりやすい名前を入力します。 後で簡単に識別できるよう、ポリシーに名前を付けます。 たとえば、適切なポリシー名は **iOS:デバイスのカメラをブロックする**です。
    - **説明**:ポリシーの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** :デバイスのプラットフォームを選択します。 次のようなオプションがあります。  

        - **Android**
        - **Android エンタープライズ**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 以降**
        - **Windows 10 以降**

    - **[プロファイルの種類]** : **[デバイスの制限]** を選択します。

        Surface Hub などの Windows 10 Team デバイス用のデバイスの制限プロファイルを作成するには、 **[デバイスの制限 (Windows 10 Team)]** を選択します。

4. 選択したプラットフォームによって構成できる設定が異なります。 詳細な設定については、お使いのプラットフォームを選択してください。

    - [Android の設定](../device-restrictions-android.md)
    - [Android エンタープライズの設定](../device-restrictions-android-for-work.md)
    - [iOS/iPadOS の設定](device-restrictions-ios.md)
    - [macOS の設定](device-restrictions-macos.md)
    - [Windows Phone 8.1 の設定](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 の設定](device-restrictions-windows-10.md)
    - [Windows 10 Team の設定](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business の設定](device-restrictions-windows-holographic.md)

5. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、プロファイル一覧に表示されます。

## <a name="next-steps"></a>次のステップ

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](../device-profile-monitor.md)します。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
