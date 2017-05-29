---
title: "ビジネス向け Windows ストアからのアプリの管理 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure プレビュー: ビジネス向け Windows ストアから取得したアプリを同期して Intune に取り込み、そのアプリを割り当てて追跡します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: b1a76e9f30e3587157d4b3085b1b3ce2abe0b37c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>ビジネス向け Windows ストアから購入したアプリを Microsoft Intune で管理する方法

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


[ビジネス向け Windows ストア](https://www.microsoft.com/business-store)では、組織用のアプリを見つけて、個別または大量購入することができます。 Microsoft Intune にストアを接続することで、Intune ポータルからボリューム購入アプリを管理することができます。 たとえば、
* ストアから購入したアプリの一覧を Intune に同期することができます。
* 同期されているアプリは Intune 管理コンソールに表示され、他のアプリと同様に割り当てることができます。
* 使用可能なライセンス数、および Intune 管理コンソールで使用中のライセンス数を追跡することができます。
* 使用可能なライセンス数が不足している場合、Intune はアプリの割り当てとインストールをブロックします。

## <a name="before-you-start"></a>アップグレードを開始する前に
ビジネス向け Windows ストアからアプリを同期して割り当てる前に、以下のことを確認してください。
* 組織のモバイル デバイス管理機関として Intune を構成する必要があります。
* ビジネス向け Windows ストアのアカウントにサインアップする必要があります。
* Intune に Windows ビジネス ストア アカウントを関連付けた後で別のアカウントに変更することはできません。
* Intune に対して、ストアから購入したアプリを手動で追加したり、削除したりすることはできません。 ビジネス向け Windows ストアとの同期のみが可能です。
* Intune は、ビジネス向け Windows ストアから購入したオンライン ライセンスされたアプリのみを同期します。
* この機能を使用するには、デバイスが Active Directory Domain Services またはワークプレースに参加している必要があります。
* 登録デバイスは、1511 リリースの Windows 10 以降を使用している必要があります。

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Intune にビジネス向け Windows ストア アカウントを関連付ける
Intune コンソールで同期を有効にする前に、以下の手順に従って、Intune を管理ツールとして使用するようにストア アカウントを構成する必要があります。
1. Intune へのサインインに使用したものと同じテナント アカウントを使用して、ビジネス ストアにサインインしていることを確認します。
2. ビジネス ストアで、**[設定]** > **[管理ツール]** の順に選択します。
3. [管理ツール] ページで、**[管理ツールの追加]** を選択し、**[Microsoft Intune]** を選択します。

> [!NOTE]
> ビジネス向け Windows ストアのアプリを割り当てるために複数の管理ツールを使用する場合、これまでは、ビジネス向け Windows ストアにはそのうちの 1 つしか関連付けることはできませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。

これで、作業を続行し、Intune コンソールで同期を設定することができます。

## <a name="configure-synchronization"></a>同期を構成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[モバイル アプリ]** を選択します。
1. **[モバイル アプリ]** ブレードで、**[セットアップ]** > **[ビジネス用の Windows ストア]** の順に選択します。
2. **[有効にする]** をクリックします。
3. ビジネス向け Windows ストアにまだサインアップしていない場合は、前に詳しく説明したように、サインアップ用のリンクをクリックしてサインアップし、アカウントを関連付けます。
5. **[言語]** ドロップダウン リストで、Intune ポータルで表示するビジネス向け Windows ストアのアプリに使用する言語を選択します。 アプリは、どの言語を使用して表示するかに関係なく、使用可能なエンド ユーザーの言語でインストールされます。
6. **[同期]** をクリックして、Windows ストアから購入したアプリを Intune に取り込みます。

## <a name="synchronize-apps"></a>アプリを同期する

1. **[モバイル アプリ]** ワークロードで、**[セットアップ]** > **[ビジネス用の Windows ストア]** の順に選択します。
2. **[同期]** をクリックして、Windows ストアから購入したアプリを Intune に取り込みます。

## <a name="assign-apps"></a>アプリを割り当てる

他の Intune アプリを割り当てる場合と同じように、ストアからアプリを割り当てます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](apps-deploy.md)」を参照してください。 ただし、**[すべてのアプリ]** ページからではなく、**[ライセンスされたアプリ]** ページからアプリを割り当てます。

ビジネス向け Windows ストア アプリを割り当てると、アプリをインストールする各ユーザーによってライセンスが使用されます。 割り当てられたアプリに対して使用可能なライセンスをすべて使用すると、それ以上コピーを割り当てることはできません。 以下のいずれかの操作を実行する必要があります。
* 一部のデバイスからアプリをアンインストールする。
* 現在の割り当ての範囲を絞り、十分なライセンスがあるユーザーのみを対象にする。
* ビジネス向け Windows ストアからアプリのコピーをさらに購入する。

> [!Important]
> 割り当てられたアプリは、最初にデバイスを登録したユーザーのみが利用できます。 他のユーザーは、そのアプリにアクセスすることができません。

