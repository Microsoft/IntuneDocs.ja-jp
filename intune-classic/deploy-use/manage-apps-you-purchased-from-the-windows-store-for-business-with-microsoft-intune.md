---
title: "ビジネス向け Microsoft ストア アプリの管理"
description: "Intune コンソールからボリューム購入したアプリを管理および展開する場合に、Microsoft Intune をビジネス向け Microsoft ストアに接続する"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d73fca5dfb5b9890e28c15438527bd540a2a9853
ms.sourcegitcommit: 1c71fff769ca0097faf46fc2b58b953ff28386e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2017
---
# <a name="manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>ビジネス向け Microsoft ストアから購入したアプリを Microsoft Intune で管理する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[ビジネス向け Microsoft ストア](https://www.microsoft.com/business-store)では、組織用のアプリを見つけて、個別または大量に購入することができます。 Microsoft Intune にストアを接続することで、Intune コンソールから大量購入アプリを管理することができます。 たとえば、
* ストアから購入したアプリの一覧を Intune に同期することができます。
* 同期されているアプリは Intune 管理コンソールに表示され、他のアプリと同様に展開することができます。
* 使用可能なライセンス数、および Intune 管理コンソールで使用中のライセンス数を追跡することができます。
* 使用可能なライセンス数が不足している場合、Intune はアプリの展開とインストールをブロックします。

## <a name="before-you-start"></a>開始する前に
ビジネス向け Microsoft ストアからアプリを同期して展開する前に、以下のことを確認してください。
* 組織のモバイル デバイス管理機関として Intune を構成する必要があります。 詳細については、「[Intune でデバイスを登録するための前提条件](prerequisites-for-enrollment.md)」を参照してください。
* ビジネス向け Microsoft ストアのアカウントにサインアップする必要があります。
* Intune に Windows ビジネス ストア アカウントを関連付けた後で別のアカウントに変更することはできません。
* Intune に対して、ストアから購入したアプリを手動で追加したり、削除したりすることはできません。 ビジネス向け Microsoft ストアとの同期のみが可能です。
* Intune は、ビジネス向け Microsoft ストアから購入したオンライン ライセンスされたアプリのみを同期します。
* この機能を使用するには、デバイスが Active Directory Domain Services またはワークプレースに参加している必要があります。
* 登録デバイスは、1511 リリースの Windows 10 を使用している必要があります。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Intune にビジネス向け Microsoft ストア アカウントを関連付ける
Intune コンソールで同期を有効にする前に、以下の手順に従って、Intune を管理ツールとして使用するようにストア アカウントを構成する必要があります。
1. Intune へのサインインに使用したものと同じテナント アカウントを使用して、ビジネス ストアにサインインしていることを確認します。
2. ビジネス ストアで、**[設定]** > **[管理ツール]** の順に選択します。
3. [管理ツール] ページで、**[管理ツールの追加]** を選択し、**[Microsoft Intune]** を選択します。

> [!NOTE]
> ビジネス向け Microsoft ストアのアプリを展開するために複数の管理ツールを使用する場合、これまでは、ビジネス向け Microsoft ストアにはそのうちの 1 つしか関連付けることができませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。

これで、作業を続行し、Intune コンソールで同期を設定することができます。

## <a name="configure-synchronization"></a>同期を構成する

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理者]** を選択します。
2. **[管理]** ワークスペースで、**[モバイル デバイス管理]** > **[Windows]** の順に展開し、**[ビジネス向けストア]** を選択します。
3. **[ビジネス向け Microsoft ストア]** ページで、以下の操作を行います。
 * ビジネス向け Microsoft ストアにまだサインアップしていない場合は、サインアップ用のリンクをクリックしてサインアップを行います。
 * サインアップしたら、**[同期の構成]** を選択します。
4. **[ビジネス向け Microsoft ストア アプリの同期の構成]** ダイアログ ボックスで、**[ビジネス向け Microsoft ストアの同期を有効にする]** を選択します。
5. **[言語]** ドロップダウン リストで、Intune コンソールで表示するビジネス向け Microsoft ストアのアプリに使用する言語を選択します。 アプリは、どの言語を使用して表示するかに関係なく、使用可能なエンド ユーザーの言語でインストールされます。
6. **[OK]** をクリックします。

## <a name="synchronize-apps"></a>アプリを同期する

1. **[ビジネス向け Microsoft ストア]** ページで、**[今すぐ同期]** を選択し、ストアから購入したアプリと Intune を同期します。
2. **[アプリ]** ワークスペースで、**[アプリ]** > **[ボリューム購入アプリ]** の順に選択し、展開可能なアプリを表示して、購入したアプリが正しくインポートされたことを確認します。 このノードのアプリは、所有しているライセンスの合計数と、使用可能なライセンスの数と共に表示されます。
たとえば、ビジネス向け Microsoft ストアから会社のポータル アプリ (オンライン ライセンス) を購入し、Intune コンソールに同期してから、それを必要な Windows 10 デバイスに必要なアプリとして展開できます。 


## <a name="deploy-apps"></a>アプリの展開

他の Intune アプリを展開する場合と同じように、ストアからアプリを展開します。 詳細については、「[Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md)」 (Microsoft Intune でアプリを展開する) を参照してください。
ビジネス向け Microsoft ストア アプリを展開すると、アプリをインストールする各ユーザーによってライセンスが使用されます。 展開されたアプリに対して使用可能なライセンスをすべて使用すると、それ以上コピーを展開することはできません。 以下のいずれかの操作を実行する必要があります。
* 一部のデバイスからアプリをアンインストールする。
* 現在の展開の範囲を絞り、十分なライセンスがあるユーザーのみを対象にする。
* ビジネス向け Microsoft ストアからアプリのコピーをさらに購入する。

> [!Important]
> 展開されたアプリは、最初にデバイスを登録したユーザーのみが利用できます。 他のユーザーは、そのアプリにアクセスすることができません。


### <a name="see-also"></a>関連項目
[Microsoft Intune でモバイル デバイスのアプリを追加する](add-apps-for-mobile-devices-in-microsoft-intune.md)
