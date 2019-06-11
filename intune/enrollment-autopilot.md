---
title: Windows Autopilot を使用してデバイスを登録する
titleSuffix: Microsoft Intune
description: Windows Autopilot を使用して Windows 10 デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d58a10e62e4ff65c0c1589fcf948a6704224bc51
ms.sourcegitcommit: a97b6139770719afbd713501f8e50f39636bc202
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402745"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Windows Autopilot を使用して Intune に Windows デバイスを登録する  
Windows Autopilot を使用すると、Intune でのデバイスの登録が簡単になります。 カスタマイズされたオペレーティング システム イメージのビルドおよび維持は、時間のかかるプロセスです。 また、これらのカスタム オペレーティング システム イメージを新しいデバイスに適用し、エンド ユーザーに提供する前に使用の準備を行う場合にも、時間がかかることがあります。 Microsoft Intune と Autopilot を使用すれば、カスタム オペレーティング システム イメージのビルド、維持、および新しいデバイスへの適用を行わなくてもデバイスをエンド ユーザーに提供することができます。 Intune を使用して Autopilot デバイスを管理する場合、デバイスの登録後にポリシー、プロファイル、アプリなどを管理することができます。 利点、シナリオ、および前提条件の概要については、「[Overview of Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)」 (Windows Autopilot の概要) を参照してください。


## <a name="prerequisites"></a>必要条件
- [Intune のサブスクリプション](licenses.md)
- [Windows の自動登録が有効である](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium サブスクリプション](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Intune でのインポート用に CSV を取得する方法

使用方法について詳しくは、PowerShell コマンドレットの説明をご覧ください。

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo/1.3/Content/Get-WindowsAutoPilotInfo.ps1)

## <a name="add-devices"></a>デバイスを追加する

CSV ファイルの情報をインポートすることにより、Windows Autopilot デバイスを追加できます。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]**  >  **[インポート]** の順に選択します。

    ![Windows Autopilot デバイスのスクリーンショット](media/enrollment-autopilot/autopilot-import-device.png)

2. **[Windows AutoPilot デバイスの追加]** で、追加するデバイスを一覧表示する CSV ファイルを参照します。 CSV ファイルでは、デバイスのシリアル番号、Windows 製品 ID (省略可能)、ハードウェア ハッシュ、およびグループ タグ (省略可能) が一覧に示されているはずです。 一覧には最大 500 行を含めることができます。 次に示すヘッダーと行の形式を使用してください: `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag`
    `<serialNumber>,<optionalProductID>,<hardwareHash>,<optionalGroupTag>`

    ![Windows Autopilot デバイスの追加のスクリーンショット](media/enrollment-autopilot/autopilot-import-device2.png)

3. **[インポート]** を選んでデバイス情報のインポートを開始します。 インポートには、数分かかる場合があります。

4. インポートが完了したら、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Windows Autopilot]**  >  **[デバイス]**  >  **[同期]** の順に選択します。同期が進行中であることを示すメッセージが表示されます。 同期されているデバイスの数に応じて、プロセスが完了するまで数分かかる場合があります。

5. ビューを更新して、新しいデバイスを表示します。

## <a name="create-an-autopilot-device-group"></a>Autopilot デバイス グループを作成する

1. [Azure portal の Intune](https://aka.ms/intuneportal) で、 **[グループ]**  >  **[新しいグループ]** の順に選択します。
2. **[グループ]** ブレードで、次の手順を実行します。
    1. **[グループの種類]** で、 **[セキュリティ]** を選択します。
    2. **[グループ名]** と **[グループ テキスト]** を入力します。
    3. **[メンバーシップの種類]** に、 **[割り当て済み]** または **[動的デバイス]** のどちらかを選択します。
3. 前の手順の **[メンバーシップの種類]** で **[割り当て済み]** を選択した場合は、 **[グループ]** ブレードで **[メンバー]** を選択して Autopilot のデバイスをグループに追加します。
    まだ登録されていない Autopilot デバイスの場合、デバイスのシリアル番号が名前です。
4. 上の **[メンバーシップの種類]** で **[動的デバイス]** を選択した場合は、 **[グループ]** ブレードで **[動的なデバイス メンバー]** を選択し、 **[高度なルール]** ボックスに次のいずれかのコードを入力します。
    - Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`」と入力します
    - Intune のグループ タグ フィールドは、Azure AD デバイス上の OrderID 属性にマップされます。 特定のグループ タグ (OrderID) を使って Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `」と入力する必要があります
    - 特定の注文書 ID の Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`」と入力します
    
    **[高度なルール]** にコードを追加したら、 **[保存]** を選択します。
5. **[作成]** を選択します。  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot Deployment プロファイルを作成する
Autopilot Deployment プロファイルは、Autopilot デバイスを構成する場合に使用されます。
1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Deployment mode]\(展開プロファイル\)**  >  **[プロファイルの作成]** の順に選択します。
2. **[基本]** ページ上で、 **[名前]** と省略可能な **[説明]** に入力します。

    ![基本ページのスクリーンショット](media/enrollment-autopilot/create-profile-basics.png)

3. 割り当てられたグループ内のデバイスのすべてが自動的に Autopilot に変換されるようにする場合は、 **[すべての対象デバイスを Autopilot に変換する]** を **[はい]** に設定します。 割り当てられたグループ内の Autopilot 以外のデバイスはすべて Autopilot 展開サービスに登録されます。 登録が処理されるまで 48 時間待ちます。 デバイスが登録解除されリセットされると、Autopilot によってそのデバイスが登録されます。 この方法でデバイスを登録すると、このオプションを無効にしてもプロファイルの割り当てを削除しても、Autopilot 展開サービスからデバイスは削除されません。 [デバイスを直接削除](enrollment-autopilot.md#delete-autopilot-devices)する必要があります。
4. **[次へ]** を選択します。
5. **[Out-of-box experience (OOBE)]** ページ上の **[配置モード]** で、次の 2 つのオプションのいずれかを選択します。
    - **[ユーザー ドリブン]** : このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられます。 デバイスを登録するには、ユーザーの資格情報が必要です。
    - **[自己展開 (プレビュー)]** : (Windows 10 バージョン 1809 以降が必要) このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられません。 デバイスを登録するのに、ユーザーの資格情報は必要ありません。

    ![OOBE ページのスクリーンショット](media/enrollment-autopilot/create-profile-outofbox.png)

6. **[Join to Azure AD as]\(Azure AD への参加状況\)** ボックスに、 **[Azure AD 参加済み]** を選択します。
7. 次のオプションを構成します。
    - **[使用許諾契約書 (EULA)]** : (Windows 10、バージョン 1709 以降) EULA をユーザーに表示するかどうかを選択します。
    - **[プライバシーの設定]** : プライバシーの設定をユーザーに表示するかどうかを選択します。
    >[!IMPORTANT]
    >Windows 10 バージョン 1903 デバイス以降に Autopilot をデプロイする場合、診断データの既定は [フル] に自動設定されます。 詳しくは、[Windows 診断データ](https://docs.microsoft.com/en-us/windows/privacy/windows-diagnostic-data)に関するページをご覧ください <br>
    
    - **[アカウントの変更オプションを非表示にする] (Windows 10 バージョン 1809 以降が必要)** : **[非表示]** を選択すると、会社のサインイン ページとドメイン エラー ページにアカウント変更オプションが表示されなくなります。 これらのオプションでは、[Azure Active Directory で会社のブランドを構成する](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)必要があります。
    - **[ユーザー アカウントの種類]** : ユーザーのアカウントの種類を選択します (**管理者**ユーザーまたは**標準**ユーザー)。
    - **White Glove OOBE を許可する** : **[はい]** を選択して、White Glove のサポートを許可します。
    - **デバイス名のテンプレートを適用する**: **[はい]** を選択すると、登録中にデバイスに名前を付けるときに使用するテンプレートが作成されます。 名前を 15 文字以下にする必要があります。また、文字、数字、ハイフンを含めることができます。 数字だけで名前を作ることはできません。 [%SERIAL% マクロ](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を使用し、ハードウェア固有のシリアル番号を追加します。 または、[%RAND:x% マクロ](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を使用して、数字のランダム文字列を追加します。x は追加する桁数です。 
    - **[言語 (リージョン)]** \*: デバイスで使用する言語を選択します。 このオプションは、 **[配置モード]** に **[自己展開]** を選択した場合のみ使用できます。
    - **[キーボードを自動的に構成する]** \*: **[言語 (リージョン)]** を選択している場合は、 **[はい]** を選択してキーボード選択ページをスキップします。 このオプションは、 **[配置モード]** に **[自己展開]** を選択した場合のみ使用できます。
8. **[次へ]** を選択します。
9. **[スコープ タグ]** ページ上で、このプロファイルに適用するスコープ タグをオプションで追加します。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](scope-tags.md)に関するページをご覧ください。
10. **[次へ]** を選択します。
11. **[割り当て]** ページで、 **[割り当て先]** として **[選択したグループ]** を選択します。

    ![割り当てページのスクリーンショット](media/enrollment-autopilot/create-profile-assignments.png)

12. **[含めるグループを選択]** を選択し、このプロファイルに含めるグループを選択します。
13. いずれかのグループを除外する場合は、 **[含めないグループを選択]** を選択して、除外するグループを選びます。
14. **[次へ]** を選択します。
15. **[確認および作成]** ページで、 **[作成]** を選択してプロファイルを作成します。

    ![確認ページのスクリーンショット](media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune は、割り当てられているグループ内の新しいデバイスを定期的に確認し、これらのデバイスにプロファイルを割り当てるプロセスを開始します。 このプロセスの完了には数分かかることがあります。 デバイスをデプロイする前に、このプロセスが完了したことを確認します。  この確認は、 **[デバイスの登録]** > **[Windows の登録]** > **[デバイス]** で行うことができます。ここで、プロファイルの状態が "未割り当て" から "割り当て中" に変わり、最後に "割り当て済み" になります。

## <a name="edit-an-autopilot-deployment-profile"></a>Autopilot Deployment プロファイルを編集する
Autopilot Deployment プロファイルを作成したら、その展開プロファイルの特定の部分を編集することができます。   

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]** を選択します。
2. **[Windows の登録]** の **[Windows Autopilot]** セクションで、 **[Deployment Profiles]\(展開プロファイル\)** を選択します。
3. 編集するプロファイルを選択します。
4. 左側の **[プロパティ]** をクリックして、デプロイ プロファイルの名前または説明を変更します。 変更したら、 **[保存]** をクリックします。
5. **[設定]** をクリックして、OOBE 設定を変更します。 変更したら、 **[保存]** をクリックします。

> [!NOTE]
> プロファイルの変更は、そのプロファイルに割り当てられているデバイスに適用されます。 ただし、更新されたプロファイルは、デバイスがリセットされ、再登録されるまで、Intune に既に登録されているデバイスには適用されません。

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows Autopilot の未割り当てデバイスのアラート  <!-- 163236 -->  

アラートには、Autopilot Deployment プロファイルを備えていない Autopilot プログラム デバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows Autopilot デバイスの完全な一覧とそれらに関する詳細が表示されます。


未割り当てデバイスのアラートを表示するには、[Azure Portal の Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[概要]**  >  **[Unassigned devices]\(未割り当てのデバイス\)** の順に選択します。  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>特定の Autopilot デバイスにユーザーを割り当てる

特定の Autopilot デバイスにユーザーを割り当てることができます。 この割り当てにより、Windows のセットアップ中、[社名](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)サインイン ページに Azure Active Directory からユーザーが事前入力されます。 カスタムの挨拶の名前を設定することもできます。 それによって、データが事前入力されることも、Windows サインインが変更されることもありません。 ライセンスが与えられた Intune ユーザーのみ、この方法で割り当てることができます。

前提条件:Azure Active Directory ポータル サイトが構成されていること。Windows 10 バージョン 1809 以降。

1. [Azure Portal の Intune](https://aka.ms/intuneportal) で、 **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]** の順に選択し、デバイスを選択して **[ユーザーの割り当て]** を選択します。

    ![ユーザー割り当てのスクリーンショット](media/enrollment-autopilot/assign-user.png)

2. Intune の使用ライセンスが与えられている Azure ユーザーを選択し、 **[選択]** を選択します。

    ![ユーザー選択のスクリーンショット](media/enrollment-autopilot/select-user.png)

3. **[ユーザー フレンドリ名]** ボックスにわかりやすい名前を入力するか、既定値をそのまま選択します。 この文字列は Windows セットアップ中、ユーザーがサインインしたときに表示されるフレンドリ名です。

    ![フレンドリ名のスクリーンショット](media/enrollment-autopilot/friendly-name.png)

4. **[OK]** を選択します。


## <a name="delete-autopilot-devices"></a>Autopilot デバイスを削除する

Intune に登録されていない Windows Autopilot デバイスは削除することができます。

- **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]** で Windows Autopilot からデバイスを削除します。 削除するデバイスを選んで、 **[削除]** を選択します。 Windows Autopilot デバイスの削除は、完了までに数分かかる場合があります。

テナントからデバイスを完全に削除するには、Intune デバイス、Azure Active Directory デバイス、および Windows Autopilot デバイスの各レコードを削除する必要があります。 これはすべて Intune から実行できます。

1. デバイスが Intune に登録されている場合、最初に[それらを Intune の [すべてのデバイス] ブレードから削除する](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)必要があります。

2. **[デバイス]**  >  **[Azure AD デバイス]** で Azure Active Directory デバイスのデバイスを削除します。

3. **[デバイスの登録]**  >  **[Windows の登録]**  >  **[デバイス]** で Windows Autopilot からデバイスを削除します。 削除するデバイスを選んで、 **[削除]** を選択します。 Windows Autopilot デバイスの削除は、完了までに数分かかる場合があります。

## <a name="using-autopilot-in-other-portals"></a>他のポータルでの Autopilot の使用
モバイル デバイス管理に関心がない場合は、他のポータルで Autopilot を使用できます。 他のポータルの使用はオプションですが、ご利用の Autopilot Deployment を管理する場合には Intune のみを使用することをお勧めします。 Intune と別のポータルを使用する場合、Intune では以下の操作を行うことはできません。  

- Intune で作成されたが、別のポータルで編集されたプロファイルの変更を表示する
- 別のポータルで作成されたプロファイルを同期する
- 別のポータルで行われたプロファイル割り当ての変更を表示する
- 別のポータルで行われたプロファイル割り当てを同期する
- 別のポータルで行われたデバイス一覧への変更を表示する

## <a name="windows-autopilot-for-existing-devices"></a>既存のデバイス向けの Windows Autopilot

Configuration Manager で[既存のデバイス向け Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) を使用することにより登録を行う場合は、correlator ID で Windows デバイスをグループ化することができます。 correlator ID は、Autopilot 構成ファイルのパラメーターです。 [Azure AD デバイス属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) は等しい "OfflineAutopilotprofile-\<correlator ID\>" に自動的に設定されます。 これにより、enrollmentprofileName 属性を使用して correlator ID に基づく任意の Azure AD 動的グループを作成することができます。

>[!WARNING] 
> correlator ID は Intune 内にあらかじめリストされていないので、デバイスで必要な correlator ID がレポートされる場合があります。 ユーザーが Autopilot または Apple DEP プロファイル名と一致する correlator ID を作成した場合、デバイスは enrollmentProfileName 属性に基づいて任意の動的 Azure AD デバイス グループに追加されます。 この競合を避けるには:
> - 常に enrollmentProfileName 値 "*全体*" と照合する動的グループ ルールを作成します。
> - Autopilot または Apple DEP プロファイルには "OfflineAutopilotprofile-" で始まる名前を決して付けないでください。

## <a name="next-steps"></a>次の手順
登録済み Windows 10 デバイス用に Windows Autopilot を構成したら、これらのデバイスを管理する方法を学習します。 詳細については、「[Microsoft Intune デバイスの管理とは](https://docs.microsoft.com/intune/device-management)」をご覧ください。
