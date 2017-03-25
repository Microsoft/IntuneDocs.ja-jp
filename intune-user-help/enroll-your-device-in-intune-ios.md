---
title: "Intune に iOS デバイスを登録する | Microsoft Docs"
description: "Intune に iOS デバイスを登録する方法について説明します"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: af3313e6ba5cbf9184aaaa9b197f7a3b2b9d4c3e
ms.lasthandoff: 03/13/2017


---


# <a name="enroll-your-ios-device-in-intune"></a>Intune に iOS デバイスを登録する

職場または学校が Microsoft Intune を使用している場合は、お使いの iOS デバイスを登録して、会社の電子メール、ファイル、またその他のリソースにアクセスできます。 デバイスを登録すると、IT 部門が職場や学校のリソースを管理してそれらの安全性を保持する一方で、ユーザーは好みのデバイスを使用して作業を進めることができます。 登録の詳細については、「[ポータル サイト アプリをインストールし、Intune にデバイスを登録するとどうなるか](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)」を参照してください。

<iframe src="https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

> [!NOTE]
> MacBook Pro や iMac などの macOS デバイスを実際に登録してみる場合は、[代わりにこちらの説明をご覧ください](enroll-your-device-in-intune-macos.md)。

**開始する前に:**

- この手順を開始した後に、登録が完了したことを確認します。 通常、数分以上一時停止するとプロセスが停止し、再起動が必要になります。
- 何らかの理由で登録に失敗した場合、ポータル サイト アプリに戻って、やり直す必要があります。
- Wi-Fi が機能していることを確認します。 Wi-Fi が機能していない場合、登録は失敗します。
- デバイスで Safari をブロックしている場合はブロックを解除します。 登録には Safari を使用する必要があります。


**iOS デバイスを登録するには:**

1.  「[Intune ポータル サイト アプリをインストールしてサインインする](install-and-sign-in-to-the-intune-company-portal-app-ios.md)」に記載の手順に従います。

2. **[会社アクセスのセットアップ]** ページで、**[開始]** をタップします。

    ![ios-enroll-comp-access-setup-begin](./media/ios-enroll-1a-comp-access-setup.png)

3. **[デバイスを登録する理由]** 画面で、デバイスを登録すると可能になる操作についての説明を確認した後、**[続行]** をタップします。

    ![ios-enroll-why-enroll](./media/ios-enroll-1b-why-enroll.png)

> [!NOTE]
> 黄色い三角形は、エラーが既に発生していることを意味するものではありません。 これらのアイコンは、登録プロセスに完了する必要のある手順があることを示します。

4. IT 管理者がユーザーの登録デバイスに関して確認できる情報と確認できない情報について確認し、**[続行]** をタップします。

    ![ios-enroll-what-it-can-see](./media/ios-enroll-1c-we-care-privacy.png)

5.  **[次に行うこと]** 画面で、登録中に行う内容を確認し、**[登録]** をタップします。

     ![ios-enroll-what-comes-next](./media/ios-enroll-1d-what-comes-next.png)

6.  **[プロファイルのインストール]** 画面で、**[インストール]** をタップし、入力を求められたらパスコードを入力します。

    ![ios-enroll-install-profile](./media/ios-enroll-2-mgt-profile-install.png)

7.  **[インストール]** をタップします。

    ![ios-enroll-tap-install](./media/ios-enroll-3-mgt-profile-install-2.png)    

8.  **[インストール]** をタップすると、警告を読んだことになります。

       ![ios-enroll-tap-install-after-warning](./media/ios-enroll-4-warning.png)

9.  **[信頼]** をタップします。

       ![ios-enroll-tap-trust](./media/ios-enroll-5-trust.png)

10.  プロファイルのインストールが完了したことを示す画面に変わったら、**[完了]** をタップします。

     ![ios-enroll-tap-done](./media/ios-enroll-6-done.png)

    “デバイス登録中” というメッセージが画面に表示されます。

11.  ポータル サイトでページを開くことを確認するメッセージが表示されたら、**[開く]** をタップします。

    ![ios-enroll-open-comp-portal](./media/ios-enroll-7-open-cp.png)

12. **[会社アクセスのセットアップ]** 画面で、**[続行]** をタップします。 IT 管理者が別のセキュリティ要件 (パスワードの設定など) をセットアップしている場合は、画面の指示に従って、すべてのコンプライアンス要件に対応します。[会社アクセスのセットアップ] 画面に戻った後、**[続行]** をタップします。

    ![ios-enroll-comp-access-tap-continue](./media/ios-enroll-8-comp-access-setup-compliance.png)

13. **[完了]** をタップします。

    ![ios-enroll-tap-done](./media/ios-enroll-9-comp-access-setup-complete.png)

これでデバイスが Intune に登録され、ポータル サイト アプリに戻ります。

> [!Note]
> 組織で通信費管理ソフトウェアを使用している場合は、デバイスの登録を完了する前にいくつかの追加手順を実行します。 詳細については、[こちら](enroll-your-device-with-telecom-expense-management-ios.md)を参照してください。

サポートが必要な場合は、 IT 管理者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

