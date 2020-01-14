---
title: Windows Autopilot を使用してデバイスを登録する
titleSuffix: Microsoft Intune
description: Windows Autopilot を使用して Windows 10 デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd320dddeb7717461188bdb701044bf060e7d75e
ms.sourcegitcommit: 0d9e1452fcf5f15a80230838f80a427b9951cdb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2019
ms.locfileid: "75324884"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Windows Autopilot を使用して Intune に Windows デバイスを登録する  
Windows Autopilot を使用すると、Intune でのデバイスの登録が簡単になります。 カスタマイズされたオペレーティング システム イメージのビルドおよび維持は、時間のかかるプロセスです。 また、これらのカスタム オペレーティング システム イメージを新しいデバイスに適用し、エンド ユーザーに提供する前に使用の準備を行う場合にも、時間がかかることがあります。 Microsoft Intune と Autopilot を使用すれば、カスタム オペレーティング システム イメージのビルド、維持、および新しいデバイスへの適用を行わなくてもデバイスをエンド ユーザーに提供することができます。 Intune を使用して Autopilot デバイスを管理する場合、デバイスの登録後にポリシー、プロファイル、アプリなどを管理することができます。 利点、シナリオ、および前提条件の概要については、「[Overview of Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)」 (Windows Autopilot の概要) を参照してください。

Autopilot の展開の種類には次の 4 種類があります。
- [自己展開モード](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying)は、キオスク、デジタル サイネージ、または共有デバイス向けです。
- [ホワイト グローブ](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove)では、パートナーまたは IT スタッフが、完全に構成されビジネスに即応できるように Windows 10 PC を事前プロビジョニングできます。[既存のデバイス向け Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) では、最新バージョンの Windows 10 をご利用の既存のデバイスに簡単に展開できます。
- [ユーザー駆動モード](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)は従来のユーザー向けです。 


## <a name="prerequisites"></a>[前提条件]
- [Intune のサブスクリプション](../fundamentals/licenses.md)
- [Windows の自動登録が有効である](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium サブスクリプション](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Intune でのインポート用に CSV を取得する方法

詳細については、PowerShell コマンドレットの説明をご覧ください。

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>デバイスを追加する

CSV ファイルの情報をインポートすることにより、Windows Autopilot デバイスを追加できます。

1. [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下)  >  **[インポート]** を選択します。

    ![Windows Autopilot デバイスのスクリーンショット](./media/enrollment-autopilot/autopilot-import-device.png)

2. **[Windows AutoPilot デバイスの追加]** で、追加するデバイスを一覧表示する CSV ファイルを参照します。 CSV ファイルでは、シリアル番号、Windows 製品 ID、ハードウェア ハッシュ、オプションのグループ タグ、オプションの割り当てユーザーが一覧に示されているはずです。 一覧には最大 500 行を含めることができます。 デバイスの情報を取得する方法については、「[Windows Autopilot へのデバイスの追加](https://docs.microsoft.com/windows/deployment/windows-autopilot/add-devices#device-identification)」を参照してください。 次に示すヘッダーと行の形式を使用してください:

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Windows Autopilot デバイスの追加のスクリーンショット](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > CSV のアップロードを使ってユーザーを割り当てる場合は、必ず有効な UPN を割り当てるようにしてください。 無効な UPN (正しくないユーザー名) を割り当てた場合、その無効な割り当てを削除するまで、デバイスにアクセスできなくなる可能性があります。 CSV のアップロード中に **Assigned User** の列に対して実行される検証は、ドメイン名が有効であることの確認のみです。 Microsoft では、個々の UPN の検証を実行して、既存のユーザーまたは適切なユーザーが割り当てられていることを確認することはできません。

3. **[インポート]** を選んでデバイス情報のインポートを開始します。 インポートには、数分かかる場合があります。

4. インポートが完了したら、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]**  >  **[同期]** の下) を選択します。同期が進行中であることを示すメッセージが表示されます。 同期されているデバイスの数に応じて、プロセスが完了するまで数分かかる場合があります。

5. ビューを更新して、新しいデバイスを表示します。

## <a name="create-an-autopilot-device-group"></a>Autopilot デバイス グループを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[グループ]** を選択し、 **[新しいグループ]** を選択します。
2. **[グループ]** ブレードで、次の手順を実行します。
    1. **[グループの種類]** で、 **[セキュリティ]** を選択します。
    2. **[グループ名]** と **[グループ テキスト]** を入力します。
    3. **[メンバーシップの種類]** に、 **[割り当て済み]** または **[動的デバイス]** のどちらかを選択します。
3. 前の手順の **[メンバーシップの種類]** で **[割り当て済み]** を選択した場合は、 **[グループ]** ブレードで **[メンバー]** を選択して Autopilot のデバイスをグループに追加します。
    まだ登録されていない Autopilot デバイスの場合、デバイスのシリアル番号が名前です。
4. 上の **[メンバーシップの種類]** で **[動的デバイス]** を選択した場合は、 **[グループ]** ブレードで **[動的なデバイス メンバー]** を選択し、 **[高度なルール]** ボックスに次のいずれかのコードを入力します。 これらのルールは Autopilot デバイスでのみ処理される属性を対象としているため、Autopilot デバイスのみが収集されます。 Autopilot 以外の属性に基づいてグループを作成すると、グループに含まれるデバイスが実際に Autopilot に登録されることは保証されません。
    - Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`」と入力します
    - Intune のグループ タグ フィールドは、Azure AD デバイス上の OrderID 属性にマップされます。 特定のグループ タグ (Azure AD デバイス の OrderID) を持つすべての Autopilot デバイスが含まれるグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`」と入力する必要があります
    - 特定の注文書 ID の Autopilot デバイスをすべて含むグループを作成する場合は、「`(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`」と入力します
    
    **[高度なルール]** にコードを追加したら、 **[保存]** を選択します。
5. **[作成]** を選択します。  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot Deployment プロファイルを作成する
Autopilot Deployment プロファイルは、Autopilot デバイスを構成する場合に使用されます。 テナントごとに最大 350 個のプロファイルを作成できます。
1. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デプロイ プロファイル]**  >  **[プロファイルの作成]** を選択します。
2. **[基本]** ページ上で、 **[名前]** と省略可能な **[説明]** に入力します。

    ![基本ページのスクリーンショット](./media/enrollment-autopilot/create-profile-basics.png)

3. 割り当てられたグループ内のデバイスのすべてが自動的に Autopilot に変換されるようにする場合は、 **[すべての対象デバイスを Autopilot に変換する]** を **[はい]** に設定します。 割り当てられたグループ内にある会社所有の Autopilot 以外のデバイスは、すべて Autopilot デプロイ サービスに登録されます。 個人所有のデバイスは、Autopilot に変換されません。 登録が処理されるまで 48 時間待ちます。 デバイスが登録解除されリセットされると、Autopilot によってそのデバイスが登録されます。 この方法でデバイスを登録すると、このオプションを無効にしてもプロファイルの割り当てを削除しても、Autopilot 展開サービスからデバイスは削除されません。 [デバイスを直接削除](enrollment-autopilot.md#delete-autopilot-devices)する必要があります。
4. **[次へ]** を選択します。
5. **[Out-of-box experience (OOBE)]** ページ上の **[配置モード]** で、次の 2 つのオプションのいずれかを選択します。
    - **[ユーザー ドリブン]** : このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられます。 デバイスを登録するには、ユーザーの資格情報が必要です。
    - **[自己展開 (プレビュー)]** : (Windows 10 バージョン 1809 以降が必要) このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられません。 デバイスを登録するのに、ユーザーの資格情報は必要ありません。 デバイスにユーザーが関連付けられていない場合、ユーザーベースのコンプライアンス ポリシーは適用されません。 自己展開モードを使用する場合、そのデバイスを対象とするコンプライアンス ポリシーのみが適用されます。

    ![OOBE ページのスクリーンショット](./media/enrollment-autopilot/create-profile-outofbox.png)

6. **[Join to Azure AD as]\(Azure AD への参加状況\)** ボックスに、 **[Azure AD 参加済み]** を選択します。
7. 次のオプションを構成します。
    - **[使用許諾契約書 (EULA)]** : (Windows 10、バージョン 1709 以降) EULA をユーザーに表示するかどうかを選択します。
    - **[プライバシーの設定]** : プライバシーの設定をユーザーに表示するかどうかを選択します。
    >[!IMPORTANT]
    >診断データ設定の既定値は Windows のバージョンによって異なります。 Windows 10 バージョン 1903 を実行しているデバイスの場合、Out-of-Box Experience 中、既定値は [完全] に設定されます。 詳しくは、[Windows 診断データ](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data)に関するページをご覧ください <br>
    
    - **[アカウントの変更オプションを非表示にする] (Windows 10 バージョン 1809 以降が必要)** : **[非表示]** を選択すると、会社のサインイン ページとドメイン エラー ページにアカウント変更オプションが表示されなくなります。 これらのオプションでは、[Azure Active Directory で会社のブランドを構成する](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)必要があります。
    - **[ユーザー アカウントの種類]** : ユーザーのアカウントの種類を選択します (**管理者**ユーザーまたは**標準**ユーザー)。 デバイスを参加させるユーザーをローカル管理グループに追加することで、それらのユーザーをローカル管理者にすることができます。 ユーザーをデバイスの既定の管理者にすることはできません。
    - **[White Glove OOBE を許可する]** (Windows 10 バージョン 1903 以降が必要、[追加の物理的要件](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): **[はい]** を選択して、White Glove のサポートを許可します。
    - **[デバイス名のテンプレートを適用する]** (Windows 10 バージョン 1809 以降と [Azure AD の結合の種類] が必要) **[はい]** を選択すると、登録中にデバイスに名前を付けるときに使用するテンプレートが作成されます。 名前を 15 文字以下にする必要があります。また、文字、数字、ハイフンを含めることができます。 数字だけで名前を作ることはできません。 [%SERIAL% マクロ](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を使用し、ハードウェア固有のシリアル番号を追加します。 または、[%RAND:x% マクロ](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)を使用して、数字のランダム文字列を追加します。x は追加する桁数です。 [ドメイン参加プロファイル](windows-autopilot-hybrid.md#create-and-assign-a-domain-join-profile)には、ハイブリッド デバイスのプレフィックスのみを指定できます。 
    - **[言語 (リージョン)]** \*: デバイスで使用する言語を選択します。 このオプションは、 **[配置モード]** に **[自己展開]** を選択した場合のみ使用できます。
    - **[キーボードを自動的に構成する]** \*: **[言語 (リージョン)]** を選択している場合は、 **[はい]** を選択してキーボード選択ページをスキップします。 このオプションは、 **[配置モード]** に **[自己展開]** を選択した場合のみ使用できます。
8. **[次へ]** を選択します。
9. **[スコープ タグ]** ページ上で、このプロファイルに適用するスコープ タグをオプションで追加します。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページをご覧ください。
10. **[次へ]** を選択します。
11. **[割り当て]** ページで、 **[割り当て先]** として **[選択したグループ]** を選択します。

    ![割り当てページのスクリーンショット](./media/enrollment-autopilot/create-profile-assignments.png)

12. **[含めるグループを選択]** を選択し、このプロファイルに含めるグループを選択します。
13. いずれかのグループを除外する場合は、 **[含めないグループを選択]** を選択して、除外するグループを選びます。
14. **[次へ]** を選択します。
15. **[確認および作成]** ページで、 **[作成]** を選択してプロファイルを作成します。

    ![確認ページのスクリーンショット](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune は、割り当てられているグループ内の新しいデバイスを定期的に確認し、これらのデバイスにプロファイルを割り当てるプロセスを開始します。 このプロセスの完了には数分かかることがあります。 デバイスをデプロイする前に、このプロセスが完了したことを確認します。  この確認は、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下) で行うことができます。ここで、プロファイルの状態が "未割り当て" から "割り当て中" に変わり、最後に "割り当て済み" になります。

## <a name="edit-an-autopilot-deployment-profile"></a>Autopilot Deployment プロファイルを編集する
Autopilot Deployment プロファイルを作成したら、そのデプロイ プロファイルの特定の部分を編集することができます。   

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デプロイ プロファイル]** を選択します。
2. 編集するプロファイルを選択します。
3. 左側の **[プロパティ]** を選択して、デプロイ プロファイルの名前または説明を変更します。 変更したら、 **[保存]** をクリックします。
5. **[設定]** をクリックして、OOBE 設定を変更します。 変更したら、 **[保存]** をクリックします。

> [!NOTE]
> プロファイルの変更は、そのプロファイルに割り当てられているデバイスに適用されます。 ただし、更新されたプロファイルは、デバイスがリセットされ、再登録されるまで、Intune に既に登録されているデバイスには適用されません。

## <a name="edit-autopilot-device-attributes"></a>オートパイロット デバイス属性の編集
オートパイロット デバイスをアップロードしたら、デバイスの特定の属性を編集できます。

1. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下) を選択します。
2. 編集するデバイスを選択します。
3. 画面の右側のウィンドウで、デバイス名、グループ タグ、またはユーザー フレンドリ名 (ユーザーを割り当てている場合) を編集できます。
4. **[保存]** を選択します。

> [!NOTE]
> デバイス名はすべてのデバイスに対して構成できますが、Hybrid Azure AD 参加済みデプロイでは無視されます。 デバイス名は、Hybrid Azure AD デバイスのドメイン参加プロファイルから引き続き取得されます。

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows Autopilot の未割り当てデバイスのアラート  <!-- 163236 -->  

アラートには、Autopilot Deployment プロファイルを備えていない Autopilot プログラム デバイスの数が示されます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows Autopilot デバイスの完全な一覧とそれらに関する詳細が表示されます。

未割り当てデバイスのアラートを表示するには、[Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[概要]**  >  **[登録のアラート]**  >  **[割り当てられていないデバイス]** を選択します。  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>特定の Autopilot デバイスにユーザーを割り当てる

特定の Autopilot デバイスにユーザーを割り当てることができます。 この割り当てにより、Windows のセットアップ中、[社名](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)サインイン ページに Azure Active Directory からユーザーが事前入力されます。 カスタムの挨拶の名前を設定することもできます。 それによって、データが事前入力されることも、Windows サインインが変更されることもありません。 ライセンスが与えられた Intune ユーザーのみ、この方法で割り当てることができます。

必要条件:Azure Active Directory ポータル サイトが構成されていること。Windows 10 バージョン 1809 以降。

1. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下でデバイスを選択して **[ユーザーの割り当て]** の下) を選択します。

    ![ユーザー割り当てのスクリーンショット](./media/enrollment-autopilot/assign-user.png)

2. Intune の使用ライセンスが与えられている Azure ユーザーを選択し、 **[選択]** を選択します。

    ![ユーザー選択のスクリーンショット](./media/enrollment-autopilot/select-user.png)

3. **[ユーザー フレンドリ名]** ボックスにわかりやすい名前を入力するか、既定値をそのまま選択します。 この文字列は Windows セットアップ中、ユーザーがサインインしたときに表示されるフレンドリ名です。

    ![フレンドリ名のスクリーンショット](./media/enrollment-autopilot/friendly-name.png)

4. **[OK]** を選択します。

## <a name="autopilot-deployments-report"></a>Autopilot 展開レポート
Windows Autopilot によって展開された各デバイスについての詳細を見ることができます。
レポートを表示するには、[Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にアクセスし、 **[デバイス]**  >  **[監視]**  >  **[Autopilot Deployment]** を選択します。
データは、展開後 30 日間使用できます。


## <a name="delete-autopilot-devices"></a>Autopilot デバイスを削除する

Intune に登録されていない Windows Autopilot デバイスは削除することができます。

- **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下) で、Windows オートパイロットからデバイスを削除します。 削除するデバイスを選んで、 **[削除]** を選択します。 Windows Autopilot デバイスの削除は、完了までに数分かかる場合があります。

テナントからデバイスを完全に削除するには、Intune デバイス、Azure Active Directory デバイス、および Windows Autopilot デバイスの各レコードを削除する必要があります。 これはすべて Intune から実行できます。

1. デバイスが Intune に登録されている場合、最初に[それらを Intune の [すべてのデバイス] ブレードから削除する](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)必要があります。

2. **[デバイス]**  >  **[Azure AD デバイス]** で Azure Active Directory デバイスのデバイスを削除します。

3. **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下) で、Windows オートパイロットからデバイスを削除します。 削除するデバイスを選んで、 **[削除]** を選択します。 Windows Autopilot デバイスの削除は、完了までに数分かかる場合があります。

## <a name="using-autopilot-in-other-portals"></a>他のポータルでの Autopilot の使用
モバイル デバイス管理に関心がない場合は、他のポータルで Autopilot を使用できます。 他のポータルの使用はオプションですが、ご利用の Autopilot Deployment を管理する場合には Intune のみを使用することをお勧めします。 Intune と別のポータルを使用する場合、Intune では以下の操作を行うことはできません。  

- Intune で作成されたが、別のポータルで編集されたプロファイルの変更を表示する
- 別のポータルで作成されたプロファイルを同期する
- 別のポータルで行われたプロファイル割り当ての変更を表示する
- 別のポータルで行われたプロファイル割り当てを同期する
- 別のポータルで行われたデバイス一覧への変更を表示する

## <a name="windows-autopilot-for-existing-devices"></a>既存のデバイス向け Windows Autopilot

Configuration Manager で[既存のデバイス向け Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) を使用することにより登録を行う場合は、correlator ID で Windows デバイスをグループ化することができます。 correlator ID は、Autopilot 構成ファイルのパラメーターです。 [Azure AD デバイス属性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) は等しい "OfflineAutopilotprofile-\<correlator ID\>" に自動的に設定されます。 これにより、enrollmentprofileName 属性を使用して correlator ID に基づく任意の Azure AD 動的グループを作成することができます。

>[!WARNING] 
> correlator ID は Intune 内にあらかじめリストされていないので、デバイスで必要な correlator ID がレポートされる場合があります。 ユーザーが Autopilot または Apple DEP プロファイル名と一致する correlator ID を作成した場合、デバイスは enrollmentProfileName 属性に基づいて任意の動的 Azure AD デバイス グループに追加されます。 この競合を避けるには:
> - 常に enrollmentProfileName 値 "*全体*" と照合する動的グループ ルールを作成します。
> - Autopilot または Apple DEP プロファイルには "OfflineAutopilotprofile-" で始まる名前を決して付けないでください。

## <a name="next-steps"></a>次のステップ
登録済み Windows 10 デバイス用に Windows Autopilot を構成したら、これらのデバイスを管理する方法を学習します。 詳細については、「[Microsoft Intune デバイスの管理とは](../remote-actions/device-management.md)」をご覧ください。
