---
title: "企業所有の iOS デバイスの登録 | Microsoft Intune"
description: "Apple Device Enrollment Program (DEP) または Apple Configurator を使用した企業所有の iOS デバイスの登録"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 00ca6ea06aa63646d6ede6337f8e70d1ab956c5f
ms.openlocfilehash: cfc97f4ed931a5c7dc5b38eafd0a2d081bc30975


---

# <a name="enroll-corporate-owned-ios-devices-in-microsoft-intune"></a>Microsoft Intune での企業所有の iOS デバイスの登録
Microsoft Intune は、Mac コンピューターで実行される Apple Device Enrollment Program (DEP) または [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) ツールによる、企業所有の iOS デバイスの登録をサポートします。

**前提条件:** [Apple Push Notification サービス証明書](set-up-ios-and-mac-management-with-microsoft-intune.md)が必要です。

企業登録対象の iOS デバイスは、Apple Configurator、DEP、またはポータル サイトを使用して登録することができます。

## <a name="use-apple-configurator"></a>Apple Configurator を使用する場合

会社の登録プロファイルをエクスポートし、Apple Configurator を実行している Mac にモバイル デバイスを接続することで、iOS デバイスを登録できます。 Apple Configurator では、2 つの形式の登録がサポートされています。

- **セットアップ アシスタントを使用した登録**: デバイスを出荷時の設定に戻し、デバイスの新しいユーザーがセットアップできるようにします。 この方法では、管理者は [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) を実行している Mac コンピューターに iOS デバイスを USB で接続して、登録を事前構成する必要があります。 その後、デバイスをユーザーに配布し、ユーザーがセットアップ アシスタント プロセスを実行します。 このプロセスで、デバイスを職場または学校の資格情報で構成し、登録プロセスを完了します。 詳しくは、[Apple Configurator とセットアップ アシスタントを使用した iOS デバイスの登録](ios-setup-assistant-enrollment-in-microsoft-intune.md)に関するページを参照してください。

- **直接登録** - デバイスの準備で使用する Apple Configurator 準拠ファイルを作成します。 登録対象デバイスは出荷時の設定に戻されませんが、ユーザーの関連付け情報は含まれません。 この方法では、管理者は [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) を実行している Mac コンピューターに iOS デバイスを USB で接続して、デバイスを登録する必要があります。 詳しくは、[Apple Configurator の直接登録を使用した iOS デバイスの登録](ios-direct-enrollment-in-microsoft-intune.md)に関するページを参照してください。

## <a name="use-the-device-enrollment-program-dep"></a>Device Enrollment Program (DEP) のサポートを使用する場合
DEP では、DEP を通じて購入したデバイスに "無線で" 登録プロファイルが展開されます。 ユーザーがデバイスでセットアップ アシスタントを実行すると、デバイスが Intune に登録されます。  DEP を使用して登録したデバイスの場合は、ユーザーが登録を解除することはできません。 詳しくは、[Device Enrollment Program による iOS デバイスの登録](ios-device-enrollment-program-in-microsoft-intune.md)に関するページを参照してください。

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>DEP または Apple Configurator で登録されたデバイスでのポータル サイトの使用

ユーザー アフィニティが構成されたデバイスでは、ポータル サイト アプリをインストールして実行し、アプリをダウンロードしてデバイスを管理できます。 ユーザーは、デバイスを受け取った後、セットアップ アシスタントを完了してポータル サイト アプリをインストールするために、いくつもの追加の手順を完了する必要があります。

以下をサポートするには、ユーザー アフィニティが必要です。
  - モバイル アプリケーション管理 (MAM) アプリ
  - 電子メールと会社データへの条件付きアクセス
  - ポータル サイト アプリ

**ユーザー アフィニティありで企業所有 iOS デバイスを登録する方法**
1. ユーザーは、デバイスの電源をオンにすると、セットアップ アシスタントを完了するように求められます。 セットアップ中にユーザーは資格情報を要求されます。 Intune のサブスクリプションに関連付けられている資格情報 (つまり一意の個人名または UPN) を使用する必要があります。

2. セットアップ中にユーザーは Apple ID を要求されます。 デバイスでポータル サイトをインストールできるように、Apple ID を入力する必要があります。 この ID は、セットアップの完了後に iOS の設定メニューから入力することもできます。

3. セットアップが完了したら、iOS デバイスで App Store からポータル サイト アプリをインストールする必要があります。

4. これでユーザーは、デバイスを設定するときに使用した UPN を使用して、ポータル サイトにサインインできるようになります。

5. ユーザーはログインすると、デバイスを登録するように求められます。 最初の手順は、デバイスを指定することです。 アプリには、ユーザーの Intune アカウントに割り当てられている企業登録済みの iOS デバイスの一覧が表示されます。 一致するデバイスを選択する必要があります。

  ユーザーのデバイスがまだ企業登録済みでない場合は、**[新しいデバイス]** を選択して標準の登録フローを行う必要があります。

6. 次の画面で、ユーザーは、新しいデバイスのシリアル番号を確認する必要があります。 シリアル番号は、**[シリアル番号を確認]** リンクをタップして設定アプリを起動すると確認できます。 その後、ポータル サイト アプリにシリアル番号の最後の 4 文字を入力する必要があります。

  この手順では、デバイスが Intune に登録されている会社のデバイスであることが確認されます。 デバイスのシリアル番号が一致しない場合は、間違ったデバイスが選択されています。 その場合は、前の画面に戻って、別のデバイスを選択する必要があります。

7. シリアル番号が確認されると、ポータル サイト アプリはポータル サイトの Web サイトにリダイレクトされ、登録の最終処理が行われます。 Web サイトでは、ユーザーにアプリに戻るように促すメッセージが表示されます。

8. これで登録が完了します。 これで、このデバイスのすべての機能を使用できるようになります。

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>ユーザー アフィニティなしの企業所有の管理対象デバイスについて

ユーザー アフィニティなしで構成されているデバイスではポータル サイトはサポートされません。そのようなデバイスにはポータル サイト アプリをインストールしないでください。 会社ポータルは、会社の資格情報を持ち、カスタマイズされた企業リソース (電子メールなど) へのアクセスを必要とするユーザー向けです。 ユーザー アフィニティなしで登録されたデバイスは、専用ユーザー サインインのためのデバイスではありません。 ユーザー アフィニティなしで登録されているデバイスの一般的な使用例としては、キオスクや販売時点管理 (POS)、共有ユーティリティのデバイスがあります。

ユーザー アフィニティが必要な場合は、デバイスを登録する前に、デバイスの登録プロファイルで **[ユーザー アフィニティ]** が選択されていることを確認してください。 デバイスのアフィニティの状態を変更するには、デバイスをインベントリから削除してから再登録する必要があります。



### <a name="see-also"></a>関連項目
[Microsoft Intune でデバイスを登録するための前提条件](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO3-->


