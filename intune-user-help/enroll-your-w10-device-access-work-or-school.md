---
title: Intune に Windows 10 デバイスを登録する | Microsoft Docs
description: Intune に Windows 10, バージョン1607 以降のデバイスを登録する
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 21332f5441d6b2318a8739feb0457021cb7e442b
ms.sourcegitcommit: 8117444cfdddf6d9bdbc4ac715af8d88e72f411d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48260219"
---
# <a name="enroll-your-windows-10-device-in-intune"></a>Intune に Windows 10 デバイスを登録する

> [!NOTE]
> Windows 10 はあらゆる種類のデバイスで動作します。 デスクトップ、スマートフォン、タブレットのいずれを使用している場合でも、このページの画像とは少し違う部分があるかもしれませんが、手順は同じです。

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]

1. **[スタート]** メニューに移動します。

   - **Windows 10 デスクトップ** デバイスを使用している場合は、**[スタート] メニュー**に移動します。
   - **Windows 10 Mobile** デバイスを使用している場合は、**[スタート]** 画面に移動し、スワイプして **[すべてのアプリ]** リストを表示します。

2. 検索バーで「設定」を検索して、Windows の **[設定]** アプリを開きます。

3. **[アカウント]** > **[職場または学校にアクセスする]** > **[接続]** の順に選択します。

    ![[職場または学校にアクセスする] アカウントの選択](./media/w10-enroll-rs1-connect-to-work-or-school.png)

4. 職場または学校の電子メール アドレスを入力し、**[次へ]** を選択します。

   ![職場または学校のアカウントを入力します。](./media/w10-enroll-rs1-set-up-work-or-school-account.png)

5. 職場または学校のアカウントで Intune にサインインします。

    ![職場または学校のアカウントを追加する](./media/w10-enroll-rs1-enter-your-credentials.png)

    会社または学校がデバイスを登録していることを示すメッセージが表示されます。

6. 「**準備が完了しました!**」という画面が表示されたら、 **[閉じる]** を選択します。 以上で完了です。

   !["準備が完了しました" という画面で [閉じる] を 選択する](./media/w10-enroll-rs1-youre-all-set.png)

7. 接続が適切なことを再確認する場合は、**[設定]** に戻ります。すると、職場または学校のアカウントが表示されます。

    ![接続が正しくセットアップされたことを確認する](./media/w10-enroll-rs1-validate-successful-enrollment.png)

前の手順を実行しても職場または学校の電子メール アカウントとファイルにまだアクセスできない場合は、「[[職場または学校にアクセスする] が表示されている場合のトラブルシューティング手順](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)」に従ってください。
