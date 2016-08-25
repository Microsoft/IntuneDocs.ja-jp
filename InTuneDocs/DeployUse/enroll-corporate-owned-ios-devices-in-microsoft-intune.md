---
title: "企業所有の iOS デバイスの登録 | Microsoft Intune"
description: "Apple Device Enrollment Program (DEP) または Apple Configurator を使用した企業所有の iOS デバイスの登録"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9b7b8f6e5182e228458f5ea75e804a638f1e2a2b
ms.openlocfilehash: ca05e94e72269c11db24b667f1d113c794cd8b23


---

# Microsoft Intune での企業所有の iOS デバイスの登録
Microsoft Intune は、Mac コンピューターで実行される Apple Device Enrollment Program (DEP) または [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) ツールを使用した、企業所有の iOS デバイスの登録をサポートします。

**前提条件:**  [Apple Push Notification サービス証明書](set-up-ios-and-mac-management-with-microsoft-intune.md)

企業登録対象の iOS デバイスは次の 3 つの方法で登録することができます。

-   **Apple Configurator** - 会社の登録プロファイルをエクスポートし、Apple Configurator を実行している Mac にモバイル デバイスを接続することで、iOS デバイスを登録することができます。 Apple Configurator では、2 つの形式の登録がサポートされています。

    - **セットアップ アシスタントを使用した登録** – デバイスを出荷時の設定に戻し、デバイスの新しいユーザーによるセットアップ用に準備します。 この方法では、管理者は、[Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) を実行している Mac コンピューターに iOS デバイスを USB 接続して、登録を事前構成する必要があります。 その後、デバイスがユーザーに渡され、ユーザーがセットアップ アシスタント プロセスを実行し、自分の職場または学校の資格情報でデバイスを構成して登録プロセスを完了します。 [Apple Configurator とセットアップ アシスタントを使用して iOS デバイスを登録する](ios-setup-assistant-enrollment-in-microsoft-intune.md)

    - **直接登録** - デバイスの準備中に使用する Apple Configurator 準拠のファイルを作成します。 登録されるデバイスは出荷時の設定に戻されませんが、ユーザーの関連付け情報は含まれません。 この方法では、管理者は、[Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) を実行している Mac コンピューターに iOS デバイスを USB 接続して、デバイスを登録する必要があります。 [Apple Configurator の直接登録を使用して iOS デバイスを登録する](ios-direct-enrollment-in-microsoft-intune.md)

-   **Device Enrollment Program (DEP)** – Apple の Device Enrollment Program を通して購入された iOS デバイスに登録プロファイルを "無線" で展開します。 ユーザーがデバイスでセットアップ アシスタントを実行すると、デバイスが Intune に登録されます。  DEP を使用して登録したデバイスの場合は、ユーザーが登録を解除することはできません。 [Device Enrollment Program の iOS デバイスを登録する](ios-device-enrollment-program-in-microsoft-intune.md)

## DEP または Apple Configurator で登録されたデバイスでのポータル サイトの使用

ユーザー アフィニティが構成されているデバイスは、会社のポータル アプリをインストールして実行することにより、アプリをダウンロードしてデバイスを管理できるようになります。 デバイスを受け取ったユーザーは、セットアップ アシスタントを完了して会社のポータル アプリをインストールするために、いくつもの追加の手順を完了する必要があります。

ユーザー アフィニティありで企業所有の iOS デバイスを登録するには
1. ユーザーはデバイスの電源をオンすると、セットアップ アシスタントを完了するように求められます。 セットアップ中にユーザーは資格情報を要求されます。 Intune のサブスクリプションに関連付けられている資格情報 (つまり一意の個人名または UPN) を使用する必要があります。

2. セットアップ中にユーザーは Apple ID を要求されます。 デバイスが会社ポータルをインストールできるように、Apple ID を入力する必要があります。 セットアップの完了後に iOS の設定メニューから Apple ID を入力することもできます。

3. セットアップが完了したら、iOS デバイスは App Store から会社のポータル アプリ (たとえば会社のポータル アプリ) をインストールする必要があります。

4. これでユーザーは、デバイスを設定するときに、UPN を使用して会社ポータルにログインできるようになります。

5. ユーザーはログインすると、デバイスを登録するように求められます。 最初の手順はデバイスを指定することです。 既に会社に登録されていてエンドユーザーの Intune アカウントに割り当てられている iOS デバイスの一覧が表示されます。 一致するデバイスを選択します。

  このデバイスがまだ会社に登録されていない場合は、[新しいデバイス] を選択して、標準登録フローを続行します。

6. 次の画面で、ユーザーは新しいデバイスのシリアルを確認する必要があります。 ユーザーは [シリアル番号を確認] リンクをクリックして、設定アプリを開始して、シリアル番号を確認できます。 ユーザーは、シリアル番号の最後の 4 文字を会社ポータル アプリに入力する必要があります。

  この手順では、デバイスが Intune に登録されている会社のデバイスであることが確認されます。 デバイスのシリアル番号が一致しない場合は、間違ったデバイスが選択されています。 前の画面に戻り、別のデバイスを選択します。

7. シリアル番号の確認後に、会社ポータル アプリは会社ポータル Web サイトにリダイレクトします。ユーザーはそこで登録を完了すると、アプリに戻るように求められます。

8. これで登録が完了します。 このデバイスのすべての機能を使用できるようになります。

### ユーザー アフィニティなしの企業所有の管理対象デバイスについて

ユーザー アフィニティなしで構成されているデバイスは、会社のポータルをサポートしませんので、アプリをインストールしないでください。 会社ポータルは、会社の資格情報を持ち、カスタマイズされた企業リソース (電子メールなど) へのアクセスを必要とするユーザー向けです。 ユーザー アフィニティなしで登録されたデバイスは、専用ユーザー サインインのためのデバイスではありません。 キオスク、販売時点管理 (POS)、または共有ユーティリティ デバイスは、ユーザー アフィニティなしで登録されたデバイスの一般的なユース ケースです。 ユーザー アフィニティが必要な場合は、デバイスの登録プロファイルで [ユーザー アフィニティ] が選択されていることを確認してから、デバイスを登録します。 デバイスのアフィニティ ステータスを変更するには、デバイスをインベントリから削除してから再登録する必要があります。



### 関連項目
[Microsoft Intune にデバイスを登録する準備](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


