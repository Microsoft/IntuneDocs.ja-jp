---
title: クイック スタート - Microsoft Intune に Windows 10 デスクトップ デバイスを登録する
description: クイック スタート - Intune ポータル サイトを使用して Windows 10 デスクトップ デバイスを Microsoft Intune に登録します。
services: microsoft-intune
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 12/05/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: c04dc3169fbf6a60d0c4d7db8358092909e90240
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841822"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>クイック スタート:Windows 10 デバイスを登録する

このクイック スタートでは、最初に Intune ユーザーのロールで、Microsoft Intune に Windows 10 デバイスを登録します。 次に、Intune に戻って、登録したデバイスを確認します。

デバイスを Microsoft Intune に登録すると、Windows 10 デバイスが組織のセキュリティで保護されているデータ (電子メール、ファイル、その他のリソースなど) にアクセスできるようになります。 対象は Windows 10 Desktop と Windows 10 Mobile デバイスの両方です。 デバイスを登録すると、ユーザーと組織の両方にとってこのアクセスを保護し、職場のデータと個人のデータを分けることができます。

> [!TIP]
> 「[ポータル サイト アプリをインストールし、Intune に Windows デバイスを登録するとどうなりますか](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows)」と「[デバイスを Intune に登録した場合に IT 管理者が確認できるもの](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)」を参照してください。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件

- Microsoft Intune サブスクリプション - [無料試用版アカウントにサインアップします](free-trial-sign-up.md)
- このクイック スタートを最後まで行うには、[Intune で自動登録を設定する](quickstart-setup-auto-enrollment.md)手順を完了する必要があります。

## <a name="confirm-your-windows-10-desktop-version"></a>Windows 10 デスクトップのバージョンを確認する

Windows 10 デスクトップを登録する前に、インストールされている Windows のバージョンを確認する必要があります。

1. Windows の **[スタート]** アイコンを右クリックして、**[設定]** を選択し、Windows 設定オプションを表示します。

   ![Windows の設定 - システムのスクリーンショット](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. **[システム]** > **[バージョン情報]** を選択します。 

   ![システム設定のスクリーンショット](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > **検索バー**に「PC 情報」と入力し、**[PC 情報]** を選択してもかまいません。

3. **[設定]** ウィンドウに、PC の **[Windows の仕様]** 一覧が表示されます。 一覧の **[バージョン]** を確認します。

4. Windows 10 の **[バージョン]** が **1607 以降**であることを確認します。

    > [!IMPORTANT]
    > このクイック スタートの手順は Windows 10 バージョン **1607 以降**に対するものです。バージョンが **1511 以前**の場合は、[こちらの手順](/intune-user-help/enroll-your-w10-device-your-account)に従ってください。

## <a name="enroll-windows-10-desktop"></a>Windows 10 デスクトップを登録する

1. Windows の [設定] に戻り、**[アカウント]** を選択します。

   ![システム設定 - アカウントのスクリーンショット](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. **[職場または学校にアクセスする]** > **[接続]** の順に選択します。

    ![[職場または学校にアクセスする] アカウントの選択](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. 職場または学校アカウントで Intune にサインインし、**[次へ]** を選択します。 「ユーザーを作成してライセンスを割り当てる」クイック スタートに従った場合、作成したユーザー アカウントでサインインすることができます。

    > [!NOTE]
    > ".onmicrosoft.com" を設定した場合、ユーザー アカウントのアドレスの一部が **.onmicrosoft.com** になります。 

   ![職場または学校アカウントを入力する](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    会社または学校がデバイスを登録していることを示すメッセージが表示されます。

4. 「**準備が完了しました!**」という画面が表示されたら、 **[完了]** を選択します。 以上で完了です。

5. Windows デスクトップの **[職場または学校にアクセスする]** 設定の一部として、追加したアカウントが表示されます。

   ![新しく追加したアカウントのスクリーンショット](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    前の手順を実行しても職場または学校の電子メール アカウントとファイルにまだアクセスできない場合は、「[[職場または学校にアクセスする] が表示されている場合のトラブルシューティング手順](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)」に従ってください。

## <a name="confirm-your-device-enrollment-in-intune"></a>Intune でのデバイス登録を確認する

1. グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。
2. **[デバイス]** を選択して、Intune に登録されたデバイスを表示します。
3. Intune に追加したデバイスが登録されていることを確認します。

   ![Intune に登録されたデバイスのスクリーンショット](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>リソースをクリーンアップする

Windows デバイスの登録を解除するには、「[管理から Windows デバイスを削除する](/intune-user-help/unenroll-your-device-from-intune-windows)」をご覧ください。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Windows 10 デバイスを Intune に登録する方法を説明しました。 すべてのプラットフォーム全体にデバイスを登録する他の方法について学習することができます。 Intune でのデバイスの使用について詳しくは、「[マネージド デバイスを使用して作業する](/intune-user-help/use-managed-devices-to-get-work-done)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート:Android デバイスに必要なパスワードの長さを設定する](quickstart-set-password-length-android.md)
