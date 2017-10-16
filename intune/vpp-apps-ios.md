---
title: "iOS のボリューム購入アプリの管理 | Microsoft Docs"
titlesuffix: Azure portal
description: "iOS ストアからボリューム購入したアプリを Intune に同期し、その使用状況を管理および追跡する方法について説明します。\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dc3160d40d4ddabcd0a7d8d5557b07b4086eea7c
ms.sourcegitcommit: 4184db38d1a9a223e680bcb4c9b732f7069bf510
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2017
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Volume Purchase Program で購入した iOS アプリを Microsoft Intune で管理する方法


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

iOS アプリ ストアでは、社内で実行するアプリの複数のライセンスを購入できます。 購入したアプリの複数コピーを追跡する管理オーバーヘッドを削減するのに役立ちます。

Microsoft Intune を使用することで、このプログラムを通じて購入したアプリを管理できます。

- アプリ ストアからライセンス情報を報告する
- 使用しているライセンスの数を追跡記録する
- 自分が所有している以上のアプリのコピーをインストールしないように支援する

ボリューム購入アプリを割り当てるには 2 つの方法があります。

### <a name="device-licensing"></a>デバイス ライセンス

デバイスにアプリを割り当てると、1 つのアプリ ライセンスが使用されて、割り当てたデバイスに関連付けられたままになります。
ボリューム購入アプリをデバイスに割り当てた場合、デバイスのエンド ユーザーは、ストアにアクセスするために Apple ID を指定する必要はありません。 



### <a name="user-licensing"></a>ユーザー ライセンス

ユーザーにアプリを割り当てると、1 つのアプリ ライセンスが使われて、ユーザーに関連付けられます。 ユーザーが所有する複数のデバイスでアプリを実行できます (上限は Apple により制御)。
ボリューム購入アプリをユーザーに割り当てた場合、各エンド ユーザーは、アプリ ストアにアクセスするために一意の有効な Apple ID が必要です。

さらに、Apple ボリューム購入プログラム ストアから購入した本と Intune との間で同期、管理、割り当てを行うことができます。 詳細については、「[Volume Purchase Program で購入した iOS 電子ブックを管理する方法](vpp-ebooks-ios.md)」を参照してください。

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS デバイス用のボリューム購入アプリの管理

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Apple Volume Purchase Program の iOS デバイス用のボリューム購入アプリをサポート

iOS アプリの複数のライセンスを[ビジネス向け Apple Volume Purchase Program](http://www.apple.com/business/vpp/) 経由または[教育向け Apple Volume Purchase Program](http://volume.itunes.apple.com/us/store) 経由で購入します。 このためには、Apple Web サイトから Apple VPP アカウントをセットアップし、Apple VPP トークンを Intune にアップロードする必要があります。  その後、ボリューム購入情報を Intune と同期し、ボリューム購入アプリの使用を追跡することができます。

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>iOS デバイス用の企業間ボリューム購入アプリをサポート

また、サードパーティの開発者も、iTunes Connect に指定されているビジネス メンバーに、認められたボリューム購入プログラムにプライベートでアプリを配布できます。 VPP for Business のメンバーは、Volume Purchase Program App Store にサインインし、アプリを購入できます。 エンド ユーザーが購入した VPP for Business アプリはそのユーザーの Intune テナントに同期されます。

## <a name="before-you-start"></a>アップグレードを開始する前に
開始する前に、Apple から VPP トークンを取得し、それを Intune アカウントにアップロードする必要があります。 さらに、次の条件を理解する必要があります。

* Intune アカウントを使用して複数の Volume Purchase Program トークンを関連付けることができます。
* 以前に異なる製品で VPP トークンを使用していた場合は、Intune で使用するための新しい VPP トークンを生成する必要があります。
* 各トークンは、1 年間有効です。
* 既定では、Intune は 1 日に 2 回、Apple VPP サービスと同期します。 いつでも手動での同期を開始できます。
* Intune で iOS VPP の使用を開始する前に、他のモバイル デバイス管理 (MDM) ベンダーで作成された既存の VPP ユーザー アカウントを削除してください。 Intune では、セキュリティ対策として、そのようなユーザー アカウントは Intune と同期されません。 Intune では、Intune で作成された Apple VPP サービスからのデータのみが同期されます。
* Intune は最大 256 VPP トークンの追加をサポートしています。
* Apple の Device Enrollment Profile (DEP) プログラムは、モバイル デバイス管理 (MDM) 登録を自動化します。 DEP を利用すれば、触れることなく企業のデバイスを構成できます。 Apple の VPP で使用したものと同じプログラム エージェント アカウントを利用し、DEP プログラムに登録できます。 Apple 展開プログラム ID は [Apple 展開プログラム](https://deploy.apple.com) Web サイトに記載されているプログラムに固有であり、iTunes ストアなど、Apple サービスのログインには利用できません。 
* VPP トークンは、一度に 1 つの Intune アカウントでのみ使用できます。 複数の Intune テナントに同じ VPP トークンを再利用することはしないでください。
* ユーザー ライセンス モデルを利用する VPP アプリをユーザーまたは (ユーザー アフィニティのある) デバイスに割り当てるとき、デバイスで Apple の利用規約に同意するときのために、各 Intune ユーザーを一意の Apple ID またはメール アドレスに関連付ける必要があります。 Apple 展開プログラム ID に使用されている Apple ID は使用しないでください。 新しい Intune ユーザーにデバイスを設定するとき、そのユーザーの一意の Apple ID またはメール アドレスで構成する必要があります。 Apple ID またはメール アドレスと Intune ユーザーで一意のペアを形成し、最大 5 台のデバイスで使用できます。

>[!IMPORTANT]
>Intune に VPP トークンをインポートした後、同じトークンを他のデバイス管理ソリューションにインポートすることはできません。 これを行うと、ライセンスの割り当てとユーザー レコードが失われる恐れがあります。

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Apple VPP トークンを取得およびアップロードするには

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
2.  VPP トークンの一覧ブレードで、**[作成]** をクリックします。
4. **[VPP トークンの作成]** ブレードで、次の情報を指定します。
    - **[VPP トークン ファイル]** - サインアップしていない場合は、ビジネス向け Volume Purchase Program または教育向けプログラムにサインアップします。 サインアップした後、アカウントの Apple VPP トークンをダウンロードし、ここで選択します。
    - **アプリの自動更新** - **[オン]** か **[オフ]** を選択し、自動更新を有効/無効にします。 有効にすると、Intune は、デバイスのチェックイン時に Intune サービスを介し、指定されたトークンに対象に購入されたすべてのアプリを更新します。 アプリ ストア内の VPP アプリ更新プログラムを検出し、デバイスのチェックイン時に自動的にデバイスにプッシュします。
4. 終了したら、**[保存]** をクリックします。

トークンがトークンの一覧ブレードに表示されます。

**[今すぐ同期]** を選択すると、いつでも、Apple が保持しているデータと Intune を同期することができます。

> [!NOTE]
> Microsoft Intune は、iTunes ストアに公開されているアプリの情報だけを同期します。 **iOS 用カスタム B2B アプリケーション**には未対応です。 このようなアプリを対象にする場合、アプリ情報は同期されません。

## <a name="to-assign-a-volume-purchased-app"></a>ボリューム購入アプリを割り当てるには

1.  **[Intune]** ブレードの  > [管理]** で、**[モバイル アプリ]**、**[アプリ]** の順に選択します。
2.  アプリの一覧ブレードで、割り当てるアプリを選択し、**[割り当て]** を選択します。
3.  ***アプリの名前***  -  **[割り当て]** ブレードで **[グループの選択]** を選択し、**[グループの選択]** ブレードでアプリを割り当てる Azure AD ユーザーまたはデバイス グループを選択します。
5.  選択したグループごとに、次の設定を選択します。
    - **[種類]** - アプリが **[使用可能]** (エンド ユーザーはポータル サイトからアプリをインストールできます) か、**[必須]** (エンドユーザーのデバイスにアプリが自動的にインストールされ) かを選びます。
    - **[ライセンスの種類]** - **[ユーザー ライセンス]** または **[デバイス ライセンス]** を選びます。
6.  完了したら、**[保存]** を選択します。


>[!NOTE]
>表示されるアプリの一覧はトークンに関連付けられます。 アプリが複数の VPP に関連付けられている場合、複数回表示されます。同じアプリがトークンごとに 1 回です。

## <a name="further-information"></a>詳細情報

ライセンスを再利用するには、割り当てアクションを [アンインストール] に変更する必要があります。 アプリをアンインストールすると、ライセンスは回収されます。 ユーザーに割り当てられたアプリを削除すると、Intune は、そのユーザーに関連付けられているすべてのアプリ ライセンスの回収を試行します。

対象となるデバイスを持つユーザーが初めて VPP アプリをデバイスにインストールしようとすると、Apple Volume Purchase Program に参加するように求められます。 アプリのインストールを実行する前に、このプログラムに参加する必要があります。 Apple Volume Purchase Program への参加招待を行うには、ユーザーが iOS デバイスで iTunes アプリを使用できる必要があります。 iTunes Store アプリを無効にするようにポリシーを設定した場合、VPP アプリのユーザーベース ライセンスは機能しません。 この問題を解決するには、ポリシーを削除して iTunes アプリを許可するか、デバイス ベースのライセンスを使用します。



## <a name="next-steps"></a>次のステップ

アプリの割り当てを監視するのに役立つ情報については、[アプリを監視する方法](apps-monitor.md)に関する記事を参照してください。