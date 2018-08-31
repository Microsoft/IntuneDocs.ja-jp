---
title: Windows AutoPilot を使用してデバイスを登録する
titleSuffix: Microsoft Intune
description: Windows AutoPilot を使用して Windows 10 デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: b3c374e4ce6baeab8cc6fde3f6c45c63c48e34dd
ms.sourcegitcommit: d99def6e4ceb44f3e7ca10fe7cdd7f222cf814c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "42903077"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Windows AutoPilot を使用して Windows デバイスを登録する
Windows AutoPilot により、デバイスのプロビジョニングが簡略化されます。 カスタマイズされたオペレーティング システム イメージのビルドおよび維持は、時間のかかるプロセスです。 また、これらのカスタム オペレーティング システム イメージを新しいデバイスに適用し、エンド ユーザーに提供する前に使用の準備を行う場合にも、時間がかかることがあります。 Microsoft Intune と AutoPilot を使用すれば、カスタム オペレーティング システム イメージのビルド、維持、および新しいデバイスへの適用を行わなくてもデバイスをエンド ユーザーに提供することができます。 Intune を使用して AutoPilot デバイスを管理する場合、デバイスの登録後にポリシー、プロファイル、アプリなどを管理することができます。 利点、シナリオ、および前提条件の概要については、「[Overview of Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)」 (Windows AutoPilot の概要) を参照してください。

## <a name="prerequisites"></a>必要条件
- [Windows の自動登録が有効である](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium サブスクリプション](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>デバイスを追加する

CSV ファイルの情報をインポートすることにより、Windows AutoPilot デバイスを追加できます。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Windows の登録]** > **[デバイス]** > **[インポート]** の順に選択します。

    ![Windows AutoPilot デバイスのスクリーンショット](media/enrollment-autopilot/autopilot-import-device.png)

2. **[Windows AutoPilot デバイスの追加]** で、追加するデバイスを一覧表示する CSV ファイルを参照します。 ファイルには、デバイスのシリアル番号、Windows 製品 ID、ハードウェア ハッシュ、および省略可能な注文 ID が含まれているはずです。

    ![Windows AutoPilot デバイスの追加のスクリーンショット](media/enrollment-autopilot/autopilot-import-device2.png)

3. **[インポート]** を選んでデバイス情報のインポートを開始します。 インポートには、数分かかる場合があります。

4. インポートが完了したら、**[デバイスの登録]** > **[Windows の登録]** > **[Windows AutoPilot]** > **[デバイス]** > **[同期]** の順に選択します。同期が進行中であることを示すメッセージが表示されます。 同期されているデバイスの数に応じて、プロセスが完了するまで数分かかる場合があります。

5. ビューを更新して、新しいデバイスを表示します。

## <a name="create-an-autopilot-device-group"></a>AutoPilot デバイス グループを作成する

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[グループ]** を選択します。
2. **[グループ]** ブレードで、次の手順を実行します。
    1. **[グループの種類]** で、**[セキュリティ]** を選択します。
    2. **[グループ名]** と **[グループ テキスト]** を入力します。
    3. **[メンバーシップの種類]** に、**[割り当て済み]** または **[動的デバイス]** のどちらかを選択します。
3. 前の手順の **[メンバーシップの種類]** で **[割り当て済み]** を選択した場合は、**[グループ]** ブレードで **[メンバー]** を選択して AutoPilot のデバイスをグループに追加します。
    まだ登録されていない AutoPilot デバイスの場合、デバイスのシリアル番号が名前です。
4. 上の **[メンバーシップの種類]** で **[動的デバイス]** を選択した場合は、**[グループ]** ブレードで **[動的なデバイス メンバー]** を選択し、**[高度なルール]** ボックスに次のいずれかのコードを入力します。
    - AutoPilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`」と入力します
    - 特定の注文 ID の AutoPilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `」と入力します
    - 特定の注文書 ID の AutoPilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`」と入力します
    
    **[高度なルール]** にコードを追加したら、**[保存]** を選択します。
5. **[作成]** を選択します。



## <a name="create-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを作成する
AutoPilot Deployment プロファイルは、AutoPilot デバイスを構成する場合に使用されます。
1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment mode]\(展開プロファイル\)** > **[プロファイルの作成]** の順に選択します。
2. **名前**と、必要に応じて**説明**を入力します。
3. **[配置モード]** には、次の 2 つのオプションのどちらかを選択します。
    - **[ユーザー ドリブン]**: このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられます。 デバイスをプロビジョニングするには、ユーザーの資格情報が必要です。
    - **[自己展開 (プレビュー)]**: (Windows 10 Insider Preview ビルド 17672 またはそれ以降) このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられません。 デバイスのプロビジョニングに、ユーザーの資格情報は不要です。
4. **[Join to Azure AD as]\(Azure AD への参加状況\)** ボックスに、**[Azure AD 参加済み]** を選択します。
5. **[Out-of-box experience (OOBE)]** を選択し、次のオプションを構成して **[保存]** を選択します。
    - **言語 (リージョン)**\*: デバイスで使用する言語を選択します。 このオプションは、**[配置モード]** に **[自己展開]** を選択した場合のみ使用できます。
    - **キーボードを自動的に構成する**\*: **[言語 (リージョン)]** を選択している場合は、キーボード選択のページをスキップしてください。 このオプションは、**[配置モード]** に **[自己展開]** を選択した場合のみ使用できます。
    - **[使用許諾契約書 (EULA)]**: (Windows 10、バージョン 1709 またはそれ以降) EULA をユーザーに表示するかどうかを選択します。
    - **[プライバシーの設定]**: プライバシーの設定をユーザーに表示するかどうかを選択します。
    - **[ユーザー アカウントの種類]**: ユーザーのアカウントの種類を**管理者**ユーザーと**標準**ユーザーのどちらにするかを選択します。 

6. **[作成]** を選択して、プロファイルを作成します。 これで、AutoPilot Deployment プロファイルをデバイスに割り当てられるようになりました。

* **[言語 (リージョン)]** も **[キーボードを自動的に構成する]** も、**[配置モード]** に **[自己展開 (プレビュー)]** を選択した場合にのみ使用できます (Windows 10 Insider Preview ビルド 17672 またはそれ以降)。


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>AutoPilot Deployment プロファイルをデバイス グループに割り当てる

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Windows の登録]** > **[Deployment profile]\(展開プロファイル\)** でプロファイルを選択します。
2. 特定のプロファイルのブレードで、**[割り当て]** を選択します。 
3. **[グループの選択]** を選択し、**[グループの選択]** ブレードでプロファイルを割り当てるグループを選択して、**[選択]** をクリックします。

## <a name="edit-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを編集する
AutoPilot Deployment プロファイルを作成したら、デプロイ プロファイルの特定の部分を編集することができます。   

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** を選択します。
2. **[Windows の登録]** の **[Windows AutoPilot]** セクションで、**[Deployment Profiles]\(展開プロファイル\)** を選択します。
3. 編集するプロファイルを選択します。
4. 左側の **[プロパティ]** をクリックして、デプロイ プロファイルの名前または説明を変更します。 変更したら、**[保存]** をクリックします。
5. **[設定]** をクリックして、OOBE 設定を変更します。 変更したら、**[保存]** をクリックします。

> [!NOTE]
> プロファイルの変更は、そのプロファイルに割り当てられているデバイスに適用されます。 ただし、更新されたプロファイルは、デバイスがリセットされ、再登録されるまで、Intune に既に登録されているデバイスには適用されません。

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows AutoPilot の未割り当てデバイスのアラート <!-- 163236 -->
AutoPilot プログラムからのデバイスで、AutoPilot Deployment プロファイルが割り当てられていないデバイスの数を示すアラートを表示することができます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。

未割り当てデバイスのアラートを表示するには、[Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[概要]** > **[Unassigned devices]\(未割り当てのデバイス\)** の順に選択します。  

## <a name="delete-autopilot-devices"></a>AutoPilot デバイスを削除する

登録されていない Windows AutoPilot デバイスは削除することができます。

1. デバイスが Intune に登録されている場合、最初に [Azure Active Directory ポータルから削除する](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)必要があります。

2. [Azure Portal の Intune](https://aka.ms/intuneportal) で、**[デバイスの登録]** > **[Windows の登録]** > **[デバイス]** の順に選びます。

3. **[Windows AutoPilot デバイス]** で、削除するデバイスを選んでから、**[削除]** を選びます。

4. **[はい]** を選んで削除を確認します。 削除には数分かかることがあります。

## <a name="using-autopilot-in-other-portals"></a>他のポータルでの AutoPilot の使用
モバイル デバイス管理が不要な場合は、ビジネス向け Microsoft ストアなどで AutoPilot を使用できます。 他のポータルの使用はオプションですが、AutoPilot Deployment を管理する場合には Intune のみを使用することをお勧めします。 Intune と別のポータルを使用する場合、Intune では以下の操作を行うことはできません。
- Intune で作成されたが、別のポータルで編集されたプロファイルの変更を表示する
- 別のポータルで作成されたプロファイルを同期する
- 別のポータルで行われたプロファイル割り当ての変更を表示する
- 別のポータルで行われたプロファイル割り当てを同期する
- 別のポータルで行われたデバイス一覧への変更を表示する

## <a name="next-steps"></a>次の手順
登録済み Windows 10 デバイス用に Windows AutoPilot を構成したら、これらのデバイスを管理する方法を学習します。 詳細については、「[Microsoft Intune デバイスの管理とは](https://docs.microsoft.com/intune/device-management)」をご覧ください。
