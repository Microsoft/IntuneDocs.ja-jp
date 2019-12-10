---
title: ビジネス向け Microsoft Store の VPP アプリを管理する
titleSuffix: Microsoft Intune
description: ビジネス向け Microsoft Store のアプリを Intune に同期する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c1627ba89ad50b2053187a20fee6cbc7a9064e8
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74562492"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>ビジネス向け Microsoft Store のボリューム購入アプリを Microsoft Intune で管理する方法

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[ビジネス向け Microsoft ストア](https://www.microsoft.com/business-store)では、組織用のアプリを見つけて、個別または大量に購入することができます。 Microsoft Intune にストアを接続することで、Azure Portal からボリューム購入アプリを管理することができます。 次に例を示します。
* ストアから購入した (または無料の) アプリの一覧を Intune に同期することができます。
* 同期されているアプリは Intune 管理コンソールに表示され、他のアプリと同様に割り当てることができます。
* オンラインとオフラインの両方のライセンス アプリが Intune に同期されます。 ポータルでは、アプリ名に "オンライン" または "オフライン" が付加されます。
* 使用可能なライセンス数、および Intune 管理コンソールで使用中のライセンス数を追跡することができます。
* 使用可能なライセンス数が不足している場合、Intune はアプリの割り当てとインストールをブロックします。
* ユーザーが企業を退社したとき、または管理者がユーザーとユーザー デバイスを削除したときに、ビジネス向け Microsoft ストアによって管理されているアプリはライセンスを自動的に取り消します。

## <a name="before-you-start"></a>開始する前に

ビジネス向け Microsoft ストアのアプリを同期して割り当てる前に、以下のことを確認してください。

- 組織のモバイル デバイス管理機関として Intune を構成します。
- ビジネス向け Microsoft ストアのアカウントにサインアップする必要があります。
- Intune に Microsoft ビジネス ストア アカウントを関連付けた後で別のアカウントに変更することはできません。
- Intune に対して、ストアから購入したアプリを手動で追加したり、削除したりすることはできません。 ビジネス向け Microsoft ストアとの同期のみが可能です。
- ビジネス向け Microsoft ストアから購入したオンラインおよびオフラインのライセンスされたアプリは Intune ポータルと同期されます。 その後、これらのアプリをデバイス グループまたはユーザー グループに展開できます。 
- オンライン アプリのインストールはストアによって管理されます。
- 無料のオフライン アプリも Intune と同期することができます。 これらのアプリは、ストアからではなく Intune でインストールします。
- この機能を使用するには、デバイスが Active Directory Domain Services またはワークプレースに参加している必要があります。
- 登録デバイスは、1511 リリースの Windows 10 以降を使用している必要があります。

さらに、ビジネス向け Microsoft ストアから同期された関連するセットとオフラインのライセンスされたアプリは、UI の単一のアプリ エントリに統合されるようになります。 個々のパッケージの展開の詳細は、すべて単一のエントリに移行されます。 Azure portal で関連するセットを表示するには、 **[アプリ]** ウィンドウから **[アプリ ライセンス]** を選びます。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Intune にビジネス向け Microsoft ストア アカウントを関連付ける
Intune コンソールで同期を有効にする前に、以下の手順に従って、Intune を管理ツールとして使用するようにストア アカウントを構成する必要があります。
1. Intune へのサインインに使用したものと同じテナント アカウントを使用して、[ビジネス向け Microsoft Store](https://www.microsoft.com/business-store) にサインインしていることを確認します。
2. ビジネス ストアで、 **[管理]** タブを選択し、 **[設定]** を選択して、 **[配布]** タブを選択します。
3. モバイル デバイス管理ツールとして特に **Microsoft Intune** を使用できない場合は、 **[Add management tool]\(管理ツールの追加\)** を選択し、 **[Microsoft Intune]** を追加します。 モバイル デバイス管理ツールとして **Microsoft Intune** をアクティブにしていない場合は、 **[Microsoft Intune]** の横にある **[アクティブ化]** をクリックします。 **[Microsoft Intune Enrollment]\(Microsoft Intune 登録\)** ではなく **[Microsoft Intune]** を有効にする必要があります。

> [!NOTE]
> これまでは、アプリを割り当てるための管理ツールをビジネス向け Microsoft ストアに 1 つしか関連付けることができませんでした。 これからは、複数のツール (Intune や Configuration Manager など) をストアに関連付けることができます。 

これで、作業を続行し、Intune コンソールで同期を設定することができます。

## <a name="configure-synchronization"></a>同期を構成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[テナント管理]**  >  **[コネクタとトークン]**  >  **[Microsoft Store for Business]** を選択します。
3. **[有効にする]** をクリックします。
4. ビジネス向け Microsoft ストアにまだサインアップしていない場合は、前に詳しく説明したように、サインアップ用のリンクをクリックしてサインアップし、アカウントを関連付けます。
5. **[言語]** ドロップダウン リストで、Azure Portal で表示するビジネス向け Microsoft ストアのアプリに使用する言語を選択します。 アプリは、どの言語を使用して表示するかに関係なく、使用可能なエンド ユーザーの言語でインストールされます。
6. **[同期]** をクリックして、Microsoft ストアから購入したアプリを Intune に取り込みます。

## <a name="synchronize-apps"></a>アプリを同期する

1. **[テナント管理]**  >  **[コネクタとトークン]**  >  **[Microsoft Store for Business]** を選択します。
2. **[同期]** をクリックして、Microsoft ストアから購入したアプリを Intune に取り込みます。

> [!NOTE]
> アプリ パッケージが暗号化されたアプリは現在サポートされていないため、Intune と同期されません。

## <a name="assign-apps"></a>アプリを割り当てる

他の Intune アプリを割り当てる場合と同じように、ストアからアプリを割り当てます。 詳細については、「[How to assign apps to groups with Microsoft Intune (Microsoft Intune を使ってアプリをグループに割り当てる方法)](apps-deploy.md)」を参照してください。 

オフライン アプリの対象は、ユーザー グループ、デバイス グループ、またはユーザーとデバイスのグループとすることができます。
オフライン アプリは、デバイス上の特定のユーザーまたはデバイス上のすべてのユーザーに対してインストールできます。 


ビジネス向け Microsoft ストア アプリを割り当てると、アプリをインストールする各ユーザーによってライセンスが使用されます。 割り当てられたアプリに対して使用可能なライセンスをすべて使用すると、それ以上コピーを割り当てることはできません。 次の操作のいずれかを選択します。
* 一部のデバイスからアプリをアンインストールする。
* 現在の割り当ての範囲を絞り、十分なライセンスがあるユーザーのみを対象にする。
* ビジネス向け Microsoft ストアからアプリのコピーをさらに購入する。

## <a name="remove-apps"></a>アプリを削除する

Microsoft Store から同期されているビジネス用アプリを削除するには、Microsoft Store for Business にログインし、アプリに返金する必要があります。 アプリが無料かどうかに関係なく、このプロセスは同じです。 無料アプリの場合、ストアからは $0 が返金されます。 無料アプリの返金の例を次に示します。 

![アプリ削除詳細のスクリーンショット](./media/windows-store-for-business/microsoft-store-for-business-01.png)

> [!NOTE]
> プライベート ストアでアプリの表示を削除すると、Intune はアプリを同期できなくなります。 アプリを完全に削除するには、アプリを返金する必要があります。

## <a name="next-steps"></a>次の手順

- [Microsoft Intune によるボリューム購入アプリとブックの管理](../vpp-apps.md)
