---
title: "Apple Configurator と直接登録を使用して iOS デバイスを登録する"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: Apple Configurator で、直接登録を使用して会社が所有している iOS デバイスを登録する方法について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b464a07e701797d39b7f9f50d1854a9a2682ac8e
ms.openlocfilehash: 3208e964f2676ebcc1e54e29f039c4965c20238f
ms.lasthandoff: 03/01/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>Apple Configurator と直接登録を使用して iOS デバイスを登録する 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune は、Mac コンピューターで実行される [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) を使用した、企業所有の iOS デバイスの登録をサポートします。 このプロセスはデバイスを工場出荷時の設定に戻さず、定義済みのポリシーでデバイスを登録します。 この方法は、**ユーザー アフィニティなし**のデバイス向けであり、iOS デバイスを Mac コンピューターに USB で接続して、会社の登録をセットアップする必要があります。

>[!NOTE]
>この登録方法は、[デバイス登録マネージャー](enroll-devices-using-device-enrollment-manager.md)の方法と同時に使用することはできません。

iOS デバイスを直接登録する場合は、デバイスのシリアル番号を取得しなくてもデバイスを登録することができます。 登録時に Intune がデバイス名をキャプチャする前に、デバイスを識別するための名前を指定することもできます。 会社のポータル アプリは、直接登録されているデバイスではサポートされていません。 このガイドでは、Mac コンピューターで Apple Configurator 2.0 を使用していることを想定しています。

iOS デバイスの他の登録方法については、[Intune での iOS デバイスの登録方法の選択](choose-ios-enrollment-method.md)に関するページを参照してください。


## <a name="prerequisites"></a>必要条件

iOS デバイスの登録を設定する前に、以下の前提条件を満たしている必要があります。

- [ドメインを構成する](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [MDM 機関を設定する](set-mdm-authority.md)
- [グループの作成](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [ポータル サイト アプリを構成する](/intune-azure/manage-apps/company-portal-app)
- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)でユーザー ライセンスを割り当てる
- [Apple MDM プッシュ証明書を取得する](get-an-apple-mdm-push-certificate.md)
- iOS デバイスに物理的にアクセスできることを確認する
- デバイスのシリアル番号を確認する ([iOS のシリアル番号の確認方法](https://support.apple.com//HT204308)に関するページを参照してください)
- USB 接続ケーブルを手元に置いておく。
- Mac PC に [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) をインストールしておく

## <a name="create-an-apple-configurator-profile-for-devices"></a>デバイスの Apple Configurator プロファイルを作成する

デバイス登録プロファイルで、デバイスのグループに適用する設定を定義します。 以下の手順は、Apple Configurator を使用して登録される iOS デバイス用のデバイス登録プロファイルを作成する方法を示しています。

1. Azure Portal で、**[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。

2. [Intune] ブレードで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。

3. **[Apple Configurator 登録設定の管理]** で **[AC プロファイル]** を選択します。

4. **[Apple Configurator の登録プロファイル]** ブレードで、**[作成]** を選択します。

5. **[登録プロファイルの作成]** ブレードで、プロファイルの名前と説明を入力します。

6. **[ユーザー アフィニティ]** で **[ユーザー アフィニティなしで登録する]** を選択して、デバイスがユーザーと関連付けられていないことを確認します。 このデバイス関連付け情報を使用すると、ローカルのユーザー データにアクセスしなくてもタスクを実行できます。 ユーザー アフィリエーションが必要なアプリ (基幹業務アプリのインストールに使用されるポータル サイト アプリを含む) は機能しません。

7. **[作成]** を選択してプロファイルを保存します。

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>プロファイルを .mobileconfig として iOS デバイスにエクスポートする

1. **[プロファイルのエクスポート]** ブレードで、登録プロファイルを [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) にダウンロードして、接続された iOS デバイスに管理プロファイルとして直接プッシュします。 この方法では、デバイスの工場出荷時の設定へのリセットは行われません。

2. 次の手順に従って、Apple Configurator を使用してデバイスを準備します。

   a. Mac コンピューターで Apple Configurator 2.0 を開きます。

   b. iOS デバイスを USB ケーブルで Mac コンピューターに接続します。 デバイスの検出時にそのデバイス用に開かれた写真、iTunes、その他のアプリを閉じます。

   c. Apple Configurator で、接続された iOS デバイスを選択し、**[追加]** ボタンを選択します。 デバイスに追加できるオプションがドロップダウン リストに表示されます。 **[プロファイル]** を選択します。

   d. ファイル ピッカーを使用して、Intune からエクスポートした .mobileconfig ファイルを選択し、**[追加]** を選択します。 プロファイルがデバイスに追加されます。 デバイスが "監督解除済み" の場合は、インストール時にデバイスの承認が必要になります。

3. 次の手順を使用して、iOS デバイスにプロファイルをインストールします。 デバイスでセットアップ アシスタントが既に完了し、使用する準備ができている必要があります。 登録のためにアプリの展開が必要な場合は、アプリの展開時に Apple ID で App Store にサインインする必要があるため、デバイスに Apple ID が設定されている必要があります。

   a. iOS デバイスのロックを解除します。

   b. **[管理プロファイル]** の **[プロファイルのインストール]** ダイアログ ボックスで、**[インストール]** を選択します。

   c. 必要に応じて、デバイスのパスコードまたは Apple ID を入力します。

   d. **[警告]** を受け入れ、**[インストール]** を選択します。

   e. **[リモート警告]** を受け入れ、**[信頼]** を選択します。

   f. **[インストール完了]** ボックスでプロファイルがインストール済みであることを確認したら、**[完了]** を選択します。

4. iOS デバイスで、**[設定]** を開き、**[全般]** > **[デバイス管理]** > **[管理プロファイル]** に移動します。 プロファイルのインストールが一覧に表示されていることを確認し、iOS のポリシー制限とインストールされているアプリを確認します。 ポリシー制限とアプリがデバイスに表示されるまでに、最大 10 分かかることがあります。

5. デバイスを配布します。 これで、iOS デバイスが Intune に登録され、管理対象になりました。

