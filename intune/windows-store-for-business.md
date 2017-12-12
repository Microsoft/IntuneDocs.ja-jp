---
title: "ビジネス向け Microsoft ストア アプリの管理"
titlesuffix: Azure portal
description: "ビジネス向け Microsoft ストアから取得したアプリを同期して Intune に取り込み、そのアプリを割り当てて追跡します。\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecb5a310e8b869deb493bc5554029d641ba419c3
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>ビジネス向け Microsoft ストアから購入したアプリを Microsoft Intune で管理する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


[ビジネス向け Microsoft ストア](https://www.microsoft.com/business-store)では、組織用のアプリを見つけて、個別または大量に購入することができます。 Microsoft Intune にストアを接続することで、Azure Portal からボリューム購入アプリを管理することができます。 たとえば、
* ストアから購入したアプリの一覧を Intune に同期することができます。
* 同期されているアプリは Intune 管理コンソールに表示され、他のアプリと同様に割り当てることができます。
* 使用可能なライセンス数、および Intune 管理コンソールで使用中のライセンス数を追跡することができます。
* 使用可能なライセンス数が不足している場合、Intune はアプリの割り当てとインストールをブロックします。
* ユーザーが企業を退社したとき、または管理者がユーザーとユーザー デバイスを削除したときに、ビジネス向け Windows ストアによって管理されているアプリはライセンスを自動的に取り消します。

## <a name="before-you-start"></a>アップグレードを開始する前に

ビジネス向け Microsoft ストアのアプリを同期して割り当てる前に、以下のことを確認してください。

- 組織のモバイル デバイス管理機関として Intune を構成します。
- ビジネス向け Microsoft ストアのアカウントにサインアップする必要があります。
- Intune に Windows ビジネス ストア アカウントを関連付けた後で別のアカウントに変更することはできません。
- Intune に対して、ストアから購入したアプリを手動で追加したり、削除したりすることはできません。 ビジネス向け Microsoft ストアとの同期のみが可能です。
- Intune は、ビジネス向け Microsoft ストアから購入したオンラインおよびオフラインのライセンスされたアプリを同期します。
- Intune には、無料のオフライン アプリのみを同期することができます。
- この機能を使用するには、デバイスが Active Directory Domain Services またはワークプレースに参加している必要があります。
- 登録デバイスは、1511 リリースの Windows 10 以降を使用している必要があります。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Intune にビジネス向け Microsoft ストア アカウントを関連付ける
Intune コンソールで同期を有効にする前に、以下の手順に従って、Intune を管理ツールとして使用するようにストア アカウントを構成する必要があります。
1. Intune へのサインインに使用したものと同じテナント アカウントを使用して、ビジネス ストアにサインインしていることを確認します。
2. ビジネス ストアで、**[設定]** > **[管理ツール]** の順に選択します。
3. [管理ツール] ページで、**[管理ツールの追加]** を選択し、**[Microsoft Intune]** を選択します。

> [!NOTE]
> これまでは、アプリを割り当てるための管理ツールをビジネス向け Microsoft ストアに 1 つしか関連付けることができませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。

これで、作業を続行し、Intune コンソールで同期を設定することができます。

## <a name="configure-synchronization"></a>同期を構成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
1. **[モバイル アプリ]** ブレードで、**[セットアップ]** > **[ビジネス向け Microsoft ストア]** の順に選択します。
2. **[有効にする]** をクリックします。
3. ビジネス向け Microsoft ストアにまだサインアップしていない場合は、前に詳しく説明したように、サインアップ用のリンクをクリックしてサインアップし、アカウントを関連付けます。
5. **[言語]** ドロップダウン リストで、Azure Portal で表示するビジネス向け Microsoft ストアのアプリに使用する言語を選択します。 アプリは、どの言語を使用して表示するかに関係なく、使用可能なエンド ユーザーの言語でインストールされます。
6. **[同期]** をクリックして、Microsoft ストアから購入したアプリを Intune に取り込みます。

## <a name="synchronize-apps"></a>アプリを同期する

1. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[ビジネス向け Microsoft ストア]** の順に選択します。
2. **[同期]** をクリックして、Microsoft ストアから購入したアプリを Intune に取り込みます。

## <a name="assign-apps"></a>アプリを割り当てる

他の Intune アプリを割り当てる場合と同じように、ストアからアプリを割り当てます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](apps-deploy.md)」を参照してください。 ただし、**[すべてのアプリ]** ページからではなく、**[ライセンスされたアプリ]** ページからアプリを割り当てます。

オフライン アプリの対象は、ユーザー グループ、デバイス グループ、またはユーザーとデバイスのグループとすることができます。
オフライン アプリは、デバイス上の特定のユーザーまたはデバイス上のすべてのユーザーに対してインストールできます。 


ビジネス向け Microsoft ストア アプリを割り当てると、アプリをインストールする各ユーザーによってライセンスが使用されます。 割り当てられたアプリに対して使用可能なライセンスをすべて使用すると、それ以上コピーを割り当てることはできません。 次の操作のいずれかを選択します。
* 一部のデバイスからアプリをアンインストールする。
* 現在の割り当ての範囲を絞り、十分なライセンスがあるユーザーのみを対象にする。
* ビジネス向け Microsoft ストアからアプリのコピーをさらに購入する。


