---
title: "Microsoft Intune でのモバイル デバイス管理を評価する | Microsoft Docs"
description: "Intune 無料試用版での MDM を評価します。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e0eb48c5bb2e0158d7b780af1c16139f10602c4e
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>Microsoft Intune でのモバイル デバイス管理を評価する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

この評価ガイドでは、Intune でモバイル デバイス管理がどのように行われるかを説明します。 次のことを行います。
- Intune で管理するデバイスを登録します。
- ユーザーとデバイスを整理するグループを作成します。
- デバイス管理ポリシーを作成してグループに展開します。
- 登録されているデバイスを使用するユーザーがデバイスにインストールできるように、アプリを公開します。
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>前提条件
このガイドでは、評価版が評価目的のみに使用されること、サブスクライブするときにクリーンな環境から始めることを前提としています。

評価版の開始を簡単にするために、Intune だけを利用するとても単純な環境を構築しています。また、Intune がモバイル デバイス管理機関になるものと想定しています。 ただし、ガイド全体を通して、もっと知りたい場合のために、より技術的なコンテンツも紹介します。

評価版ではサブスクリプション版と同じ機能が与えられます。唯一の違いは、評価版の場合、ユーザー アカウントが 100 個に制限されていることです。

## <a name="whats-not-covered"></a>このガイドには記載されていない内容
|関心がある内容 |参照先 |
|------------------------|----------|
|非テスト環境での MDM | [はじめに](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune) |
|Intune と System Center Configuration Manager での MDM | [ハイブリッド モバイル デバイス管理](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management) |

上記のガイドは運用環境への Intune のセットアップに関するものなので、評価ガイドより手順は長く、より多くの事柄を決定する必要があります。

Intune について短時間で理解できるよう、最初に評価ガイドを読んでから、他のガイドに進むことをお勧めします。

## <a name="prerequisites-for-this-evaluation"></a>この評価の前提条件
- Internet Explorer 10 以降
- Intune ユーザーがポータル サイトをどのように使用してデバイスを登録および管理するかを確認するためのテストに使用するデバイス。 このガイドでは、iPad および Android フォンを使用しています。
- iPad または他の iOS デバイスを管理するには、[Apple Push Notification Service の証明書](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)が必要です。
- [Intune 評価版サブスクリプション](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>MDM 機関を設定する
Intune によるモバイル デバイス管理に必要な最初の手順は、**モバイル デバイス管理 (MDM) 機関**を設定することです。

Intune スタンドアロンを使用している場合 (このガイドで想定されていること)、または Enterprise Mobility + Security (EMS) の一部として Intune を使用している場合は、Intune をモバイル デバイス管理機関として設定する必要があります。 つまり、組織内のモバイル デバイスの管理に使用するサービスとして Intune を指定します。

System Center Configuration Manager で Intune を使用してモバイル デバイスを管理する場合は、モバイル デバイス管理機関として Intune または Configuration Manager のどちらを使用するかを決定する必要があります。 現在ではいったん行った設定を変更するのはとても困難であるため、これは運用環境での重要な決定事項です。ただし、これについてはこの評価ガイドでは説明しません。 MDM 機関として Intune または Configuration Manager のいずれかを設定する場合の影響の詳細については、「[Choose between standalone Intune and hybrid mobile device management](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)」 (スタンドアロンの Intune またはハイブリッド モバイル デバイス管理の選択) を参照してください。

このガイドでは、試用版で Intune を MDM 機関として設定します。運用環境で試用版を使用しない限り、この設定による運用環境への影響はありません。

1. [Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理]** &gt; **[モバイル デバイス管理]** の順に選択します。
2. **[タスク]** の一覧で、**[Set MDM Authority]** (MDM 機関の設定) を選択します。 **[MDM 機関の設定]** ダイアログ ボックスが開きます。 <!---screen shot--->
3. Intune によって、Intune を MDM 機関にすることを確認するよう求められます。 Intune を使用してモバイル デバイスを管理するには、チェック ボックスをオンにして **[はい]** を選択します。

## <a name="enroll-your-test-devices-into-intune"></a>Intune にテスト デバイスを登録する

このガイドでは Android フォンと Apple iPad を登録しますが、[Intune でのデバイス登録の詳細](#Learn-more-about-device-enrollment)へのリンクがこのセクションの最後にあります。
### <a name="android"></a>Android
[Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) で Microsoft が提供する **Intune ポータル サイト**をインストールし、無料試用版にサインアップするときに[作成した Intune のユーザー資格情報](sign-up-for-30-day-trial-microsoft-intune.md#add-users)でサインインします。

### <a name="ios"></a>iOS
ユーザーが iOS デバイスを登録する前に、デバイスを管理するように Intune をセットアップしておく必要があります。

1. **証明書署名要求を取得する**<br/>
管理アカウントで Intune にログオンし、**[管理]** > **[モバイル デバイス管理]** > **[iOS および Mac OS X]** > **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書要求のダウンロード]** を選択します。 証明書署名要求 (.csr) ファイルをローカルに保存します。 .csr ファイルは、Apple Push Certificates Portal からの信頼関係証明書を要求するために使用します。 <!--- screen shot--->
2.    **Apple Push Notification サービス証明書を取得する**<BR/>
[Apple Push Certificates Portal](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2) に移動します。会社の Apple ID でサインインし、.csr ファイルを使用して APNs 証明書を作成します。 Apple Push Certificate Portal で **[Upload]** (アップロード) を選択すると、APNs に使用できない .json ファイルを受け取ります。 ダウンロードが完了したら、Apple Push Certificates Portal に戻り、[Certificates for Third-Party Servers]\(サード パーティのサーバーの証明書) で、**[Download]** (ダウンロード) を選択します。<br/>
APNs (.pem) 証明書をダウンロードして、ファイルをローカルに保存します。 この Apple ID は、後で APNs 証明書を更新するときにも使用する必要があります。
3.    **APNs 証明書を Intune に追加する**<BR/>
Microsoft Intune 管理コンソールで、**[管理]** > **[モバイル デバイス管理]** > **[iOS および Mac OS X]** > **[APNs 証明書のアップロード]** の順に移動して、**[APNs 証明書のアップロード]** を選択します。 証明書 (.pem) ファイルに移動し、**[開く]** を選択して、Apple ID を入力します。 この APNs 証明書を使用して、 Intune はモバイル デバイスを登録し、登録したモバイル デバイスにポリシーを適用して iOS デバイスを管理できます。
4.    **デバイスを登録して会社のリソースへのアクセスを取得する方法をユーザーに知らせる**<br/>
エンドユーザー用の登録手順については、「[Intune に iOS デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)」および「[Intune に Mac OS X デバイスを登録する](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-mac-os-x)」を参照してください。 登録プロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見られないデータについての説明が行われます。


### <a name="learn-more-about-device-enrollment"></a>デバイス登録の詳細

Intune は次のデバイス プラットフォームをサポートします。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

デバイス管理を有効にするための要件は、管理対象のプラットフォームによって異なります。
- **Android** モバイル デバイスは、ユーザーが、Google Play から入手できる[ポータル サイト アプリを使用して登録](/intune-classic/deploy-use/set-up-android-management-with-microsoft-intune)できます。 Intune での追加構成は不要です。
- [**iOS および Mac OS X** のセットアップ要件]/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [**Windows Phone** のセットアップ要件]/intune-classic/deploy-use/set-up-windows-phone-management-with-microsoft-intune)

<!--- ## Verify enrollment--->
<!--- START HERE

### iOS and Mac OS X
Install the **Microsoft Intune Company Portal** app from Microsoft Corporation available in the App Store and sign in with Intune user credentials added above. View **Enrolled devices** to add your device.



### Windows Phone 8.1
Users install the **Company Portal** app from Microsoft Corporation, available in the Windows Phone store, and sign in with the Intune user credentials added above.  View **Enrolled devices** to add your device.

## Install the previously deployed app
Open the Company Portal on the mobile device, choose **Apps**, and then install **Microsoft Skype**.--->



## <a name="next-steps"></a>次のステップ
[ユーザーとデバイスを編成するグループを作成する](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)

