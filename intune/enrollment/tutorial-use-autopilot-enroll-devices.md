---
title: チュートリアル - Autopilot を使用して Intune にデバイスを登録する
titleSuffix: Microsoft Intune
description: このチュートリアルでは、Intune にデバイスを登録するように Windows Autopilot を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc781ea72b54468b21fb70e60e334f1c8d8832ea
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547945"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>チュートリアル: Autopilot を使用して Intune に Windows デバイスを登録する

Windows Autopilot を使用すると、デバイスの登録が簡単になります。 Microsoft Intune と Autopilot を使用すれば、カスタム オペレーティング システム イメージのビルド、維持、および適用を行わなくてもデバイスをエンド ユーザーに提供することができます。

このチュートリアルでは、次の方法について説明します。
> [!div class="checklist"]
> * デバイスを Intune に追加する
> * Autopilot デバイス グループを作成する
> * Autopilot Deployment プロファイルを作成する
> * Autopilot Deployment プロファイルをデバイス グループに割り当てる
> * Windows デバイスをユーザーに配布する

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

Autopilot の利点、シナリオ、および前提条件の概要については、「[Windows Autopilot の概要](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)」をご覧ください。


## <a name="prerequisites"></a>必要条件
- [Windows 自動登録を設定する](../quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium サブスクリプション](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>デバイスを追加する

Windows Autopilot の設定で最初にやることは、Intune への Windows デバイスの追加です。 行う必要があるのは、CSV ファイルを作成し、Intune にインポートするだけです。

1. 任意のテキスト エディターで、Windows デバイスを示すコンマ区切り値 (CSV) のリストを作成します。 次の形式を使用します。
    
    "*シリアル番号*", "*Windows 製品 ID*", "*ハードウェア ハッシュ*", "*オプション グループ タグ*"
    
    最初の 3 つの項目は必要ですが、グループ タグ (以前の "注文 ID") は省略可能です。

2. CSV ファイルを保存します。

3. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]**  >  **[インポート]** の下) を選択します。

    ![Windows Autopilot デバイスのスクリーンショット](./media/enrollment-autopilot/autopilot-import-device.png)

4. **[Windows AutoPilot デバイスの追加]** で、保存した CSV ファイルを参照します。

    ![Windows Autopilot デバイスの追加のスクリーンショット](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. **[インポート]** を選んでデバイス情報のインポートを開始します。 インポートには、数分かかる場合があります。

4. インポートが完了したら、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]**  >  **[同期]** の下) を選択します。同期が進行中であることを示すメッセージが表示されます。 同期するデバイスの数によっては、プロセスが完了するまで数分かかる場合があります。

5. ビューを更新して、新しいデバイスを表示します。

## <a name="create-an-autopilot-device-group"></a>Autopilot デバイス グループを作成する

次に、デバイス グループを作成し、読み込んだ Autopilot デバイスをそこに格納します。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[グループ]** を選択し、 **[新しいグループ]** を選択します。
2. **[グループ]** ブレードで、次の手順を実行します。
    1. **[グループの種類]** で、 **[セキュリティ]** を選択します。
    2. **[グループ名]** に、「*Autopilot Group*」と入力します。 **[グループの説明]** に「*Test group for Autopilot devices*」と入力します。
    3. **[メンバーシップの種類]** で、 **[割り当て済み]** を選択します。
3. **[グループ]** ブレードで **[メンバー]** を選択し、Autopilot デバイスをグループに追加します。 まだ登録されていない Autopilot デバイスの場合、デバイスのシリアル番号が名前です。
4. **[作成]** を選択します。  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot Deployment プロファイルを作成する

デバイス グループを作成した後は、Autopilot デバイスを構成できるように、展開プロファイルを作成する必要があります。

1. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デプロイ プロファイル]**  >  **[プロファイルの作成]** を選択します。
2. **[基本]** ページで、 **[名前]** に「*Autopilot Profile*」と入力します。 **[説明]** に「*Test profile for Autopilot devices*」と入力します。
3. **[すべての対象デバイスを Autopilot に変換する]** を **[はい]** に設定します。 この設定により、リスト内のすべてのデバイスが確実に Autopilot 展開サービスに登録されます。 登録が処理されるまで 48 時間待ちます。
4. **[次へ]** を選択します。
5. **[Out-of-box experience (OOBE)]** ページの **[配置モード]** で、 **[ユーザー ドリブン]** を選択します。 このプロファイルのデバイスは、デバイスを登録しているユーザーに関連付けられます。 デバイスを登録するには、ユーザーの資格情報が必要です。
6. **[Join to Azure AD as]\(Azure AD への参加状況\)** ボックスに、 **[Azure AD 参加済み]** を選択します。
7. 以下のオプションを構成し、他は既定値の設定のままにします。
    - **[使用許諾契約書 (EULA)]** : **非表示**
    - **[プライバシーの設定]** : **表示**
    - **[ユーザー アカウントの種類]** : **標準**
8. **[次へ]** を選択します。
9. **[割り当て]** ページで、 **[割り当て先]** として **[選択したグループ]** を選択します。
10. **[含めるグループを選択]** を選択して、**Autopilot Group** を選択します。
11. **[次へ]** を選択します。
12. **[確認および作成]** ページで、 **[作成]** を選択してプロファイルを作成します。

## <a name="distribute-devices-to-users"></a>デバイスをユーザーに配布する

これで、ユーザーに Windows デバイスを配布できます。 ユーザーが初めてサインインするとき、Autopilot システムは自動的にデバイスを登録して構成します。 

## <a name="clean-up-resources"></a>リソースをクリーンアップする

Autopilot デバイスを使用しなくなった場合は、それらを削除できます。

1. デバイスが Intune に登録されている場合、最初に [Azure Active Directory ポータルから削除する](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)必要があります。

2. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[Windows]**  >  **[Windows の登録]**  >  **[デバイス]** ( **[Windows Autopilot Deployment プログラム]** の下) を選択します。

3. 削除するデバイスを選んで、 **[削除]** を選択します。

4. **[はい]** を選んで削除を確認します。 削除には数分かかることがあります。

## <a name="next-steps"></a>次の手順

Windows Autopilot で使用できる他のオプションについての詳細を確認できます。

> [!div class="nextstepaction"]
> [Autopilot の登録に関する詳細な記事](enrollment-autopilot.md)


