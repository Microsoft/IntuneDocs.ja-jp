---
# required metadata

title: Volume Purchase Program で購入した iOS アプリを管理する | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Volume Purchase Program で購入した iOS アプリを Microsoft Intune を使って管理する
一部のアプリ ストアでは、社内で実行するアプリの複数のライセンスを購入できます。 これは、購入したアプリの複数コピーを追跡する管理オーバーヘッドを削減するのに役立ちます。

Microsoft Intune では、このようなプログラムを通じて購入したアプリを管理するために、アプリ ストアからライセンス情報をインポートし、使用したライセンスの数を追跡し、所有しているより多くのアプリをインストールできないようにします。

> [!Important]
> 現在、Intune は、デバイスではなくユーザーに iOS VPP アプリ ライセンスを割り当てます。 そのため、エンド ユーザーは、アプリをインストールするために Apple ID パスワードを入力する必要があります。

## iOS デバイス用のボリューム購入アプリの管理
iOS アプリの複数のライセンスを購入するには、[Apple Volume Purchase Program for Business (VPP)](http://www.apple.com/business/vpp/) を利用します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンを Intune にセットアップします。  その後、ボリューム購入情報を Intune と同期し、ボリューム購入アプリの使用を追跡することができます。

## 開始する前に
開始する前に、Apple から VPP トークンを取得し、これを Intune アカウントにアップロードする必要があります。 さらに、次の点を理解する必要があります。

* 各組織には、VPP アカウントとトークンが 1 つだけあります。
* いったん Apple VPP アカウントを Intune に関連付けると、その後、異なるアカウントに関連付けることができなくなります。 そのため、使用するアカウントの詳細を複数のユーザーが持っていることが非常に重要です。
* 以前に異なる製品で VPP トークンを使用していた場合は、Intune で使用するための新しい VPP トークンを生成する必要があります。
* 各トークンは、1 年間有効です。
* 既定では、Intune は 1 日に 2 回、Apple VPP サービスと同期します。 ただし、いつでも手動で同期することができます。
* Intune に VPP トークンをインポートした後、同じトークンを他のデバイス管理ソリューションにインポートすることはできません。 これを行うと、ライセンスの割り当てとユーザー レコードが失われる恐れがあります。
* Intune で iOS VPP の使用を開始する前に、他の MDM ベンダーで作成された既存の VPP ユーザー アカウントを削除してください。 Intune は、セキュリティ対策として、そのようなユーザー アカウントを Intune と同期しません。 Intune は、Intune によって作成された Apple VPP サービスからのデータのみを同期します。 
* Device Enrollment Protocol (DEP) を使って登録されたデバイスに iOS VPP アプリを展開することはできません。

## Apple VPP トークンを取得およびアップロードするには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理者]** &gt; **[iOS および Mac OS X]**、**[Volume Purchase Program]** の順に選択します。

2.  もしまだであれば、**[Apple VPP アカウント]** リンクを選択して、Volume Purchase Program for Business にサインアップします。 サインアップして、アカウントの Apple VPP トークンをダウンロードします。

3.  Intune コンソールの **[Apple Volume Purchase Program (VPP) の管理]** ページで、**[VPP トークンのアップロード]** を選択します。

4.  **[VPP トークンのアップロード]** ダイアログ ボックスで、VPP トークンの名前と Apple ID を入力または貼り付けて、**[アップロード]** を選択します。

5.  警告ダイアログ ボックスで、後で異なる VPP アカウントに変更できないことを理解していることを示すチェック ボックスをオンにして、**[はい]** を選択します。

**[Volume Purchase Program]** ページに、Apple VPP トークンに関する情報として、最終更新時刻や有効期限、Intune との最終同期時刻などが表示されます。

**[今すぐ同期]** を選択すると、いつでも、Apple が保持しているデータと Intune を同期することができます。

## ボリューム購入アプリを展開するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[アプリ]**、**[管理されているソフトウェア]** &gt; **[ボリューム購入されたアプリ]** の順に選択します。 この一覧には、Apple VPP サービスから同期されたアプリがすべて表示されます。

2.  展開するアプリを選択し、**[展開の管理]** を選択して、「[Microsoft Intune でアプリを展開する](deploy-apps-in-microsoft-intune.md)」トピックの手順に従って、アプリのアップロード、作成、展開を完了します。

アプリを **[必須]** インストールとしてデプロイすると、アプリをインストールする各ユーザーによってライセンスが使用されます。

ライセンスを再利用するには、展開アクションを **[アンインストール]** に変更する必要があります。 アプリがアンインストールされた後、ライセンスが再利用されます。

対象となるデバイスを持つユーザーが初めて VPP アプリをインストールしようとすると、Apple Volume Purchase Program に参加するように求められます。 アプリのインストールを実行する前に、このプログラムに参加する必要があります。

> [!TIP] **[VPP 使用条件の状態]** 列を見ると、アプリが展開された各ユーザーの同意状態がわかります。

ライセンスが 1 つもない場合、展開は失敗します。

## Apple VPP アプリを監視するには
どの VPP アプリが展開されているか、ライセンスがいくつ使われているかを監視するには、**[アプリ]** ワークスペースで、**[管理されているソフトウェア]** &gt; **[ボリューム購入されたアプリ]** ノードを使います。

> [!TIP] アプリの **[フィルター]** を使って、各アプリのインストールの状態を調べることもできます。

### 関連項目
[Deploy apps in Microsoft Intune (Microsoft Intune でアプリを展開する)](deploy-apps-in-microsoft-intune.md)



<!--HONumber=Jun16_HO2-->


