---
title: "Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する"
description: "Windows AutoPilot Deployment プログラムを使用して、新しい Windows 10 デバイスを登録する方法について説明します。"
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 736eda24e355024e2abadd57206c0f0423e6d4b4
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="enroll-windows-devices-using-windows-autopilot-deployment-program"></a>Windows AutoPilot Deployment プログラムを使用して Windows デバイスを登録する
Windows AutoPilot Deployment プログラムにより、デバイスのプロビジョニングが簡略化されます。 現在、カスタマイズされたオペレーティング システム イメージのビルドおよび維持には多くの時間がかかります。 また、これらのカスタム オペレーティング システム イメージを新しいデバイスに適用し、エンド ユーザーに提供する前に使用の準備を行う場合にも多くの時間を費やすことがあります。 Microsoft Intune と AutoPilot を使用すれば、カスタム オペレーティング システム イメージのビルド、維持、および新しいデバイスへの適用を行わなくてもデバイスをエンド ユーザーに提供することができます。 Intune を使用して AutoPilot デバイスを管理する場合、デバイスの登録後にポリシー、プロファイル、アプリなどを管理することができます。 利点、シナリオ、および前提条件の概要については、「[Overview of Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot)」 (Windows AutoPilot の概要) を参照してください。

## <a name="prerequisites"></a>必要条件
- [組織へのデバイスの登録が必要](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot#registering-devices-to-your-organization)
- [Windows の自動登録が有効である](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium サブスクリプション](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>デバイスを同期する
登録済みデバイスを Intune と同期して、構成できるようにします。

1. [Azure](https://portal.azure.com/) にサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
4. **[Windows の登録]** ブレードの **[Windows AutoPilot Deployment プログラム]** セクションで、**[デバイス]** を選択します。
5. **[同期]** をクリックして、登録済みデバイスをインポートします。 同期が進行中であることを示すメッセージが表示されます。
6. ビューを更新して、新しいデバイスを表示します。 同期されているデバイスの数に応じて、プロセスが完了するまで数分かかる場合があります。  

## <a name="create-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを作成する
AutoPilot Deployment プロファイルは、AutoPilot デバイスを構成する場合に使用されます。
1. [Azure](https://portal.azure.com/) にサインインします。 
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
4. **[Windows の登録]** ブレードの **[Windows AutoPilot Deployment プログラム]** セクションで、**[デプロイ プロファイル]** を選択します。
5. **[プロファイルの作成]** をクリックして、名前と説明 (オプション) を選択します。 
6. **[結合の種類]** では、**[Azure AD 参加済み]** を選択します。
7. **[Out-of-box experience (OOBE)]** では、次のオプションを構成して **[OK]** をクリックします。 
   - **プライバシーの設定**: プライバシーの設定をユーザーに表示するかどうかを選択します。 
   - **使用許諾契約書 (EULA)**: EULA をユーザーに表示するかどうかを選択します。
   - **ユーザー アカウントの種類**: ユーザーのアカウントの種類を**管理者**ユーザーと**標準**ユーザーのどちらにするかを選択します。

     > [!Note]    
     > この設定は、グローバル管理者アカウントや会社の管理者アカウントには適用されません。 これらのアカウントは、Azure AD のすべての管理機能にアクセスできるため、標準ユーザーにすることはできません。
8. **[作成]** をクリックして、プロファイルを作成します。 これで、AutoPilot Deployment プロファイルをデバイスに割り当てられるようになりました。
     
> [!Note]    
> 次の設定は、すべての AutoPilot Deployment プロファイルで構成されます。
> - [Skip Cortana, OneDrive, and OEM registration setup pages]\(Cortana、OneDrive、および OEM の登録セットアップ ページのスキップ\)
> - [Automatically set up for work or school]\(職場または学校の自動セットアップ\)
> - [Sign in experience with company or school brand]\(職場または学校のブランドを使用するサインイン エクスペリエンス\)    

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows AutoPilot の未割り当てデバイスのアラート <!-- 163236 -->
Windows AutoPilot の未割り当てデバイスのアラートを表示し、AutoPilot プログラムからのデバイスで、AutoPilot 展開プロファイルが割り当てられていないデバイスの数を確認できます。 アラート内の情報を利用してプロファイルを作成し、未割り当てデバイスに割り当てます。 アラートをクリックすると、Windows AutoPilot の完全一覧とそれらに関する詳細が表示されます。 
1. [Azure](https://portal.azure.com/) にサインインします。 
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
4. **[概要]** を選択し、アラートを表示します。 アラートをクリックすると、AutoPilot デバイスの一覧が表示されます。  

## <a name="assign-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを割り当てる
AutoPilot Deployment プロファイルを作成したら、それを選択したデバイスに割り当てることができます。

1. [Azure](https://portal.azure.com/) にサインインします。 
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
4. **[Windows の登録]** ブレードの **[Windows AutoPilot Deployment プログラム]** セクションで、**[デバイス]** を選択します。
5. デプロイ プロファイルを割り当てるデバイスを選択します。 **[状態]** 列をフィルターすることで、割り当てられているプロファイルのないデバイスを簡単に見つけることができます。 
6. **[プロファイルの割り当て]** をクリックし、AutoPilot Deployment プロファイルを選択してから **[割り当て]** をクリックします。 割り当てが進行中であることを示すメッセージが表示されます。
7. ビューを更新し、プロファイルがデバイスに割り当てられていることを確認します。 選択したデバイスの数に応じて、プロセスが完了するまで数分かかる場合があります。 

> [!Note]
> 新しいプロファイルがデバイスに割り当てられます。 ただし、デバイスがリセットされ、再登録されるまで、Intune に既に登録されているデバイスにはプロファイルは適用されません。

### <a name="assign-a-different-autopilot-deployment-profile"></a>別の AutoPilot Deployment プロファイルを割り当てる
AutoPilot Deployment プロファイルをデバイスに割り当てた後で、別のプロファイルを割り当てる場合は、新しいプロファイルをデバイスに割り当てます。  

## <a name="edit-an-autopilot-deployment-profile"></a>AutoPilot Deployment プロファイルを編集する 
AutoPilot Deployment プロファイルを作成したら、デプロイ プロファイルの特定の部分を編集することができます。   
1. [Azure](https://portal.azure.com/) にサインインします。 
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
4. **[Windows の登録]** ブレードの **[Windows AutoPilot Deployment プログラム]** セクションで、**[デプロイ プロファイル]** を選択します。 
5. 編集するプロファイルを選択します。 
6. 左側の **[プロパティ]** をクリックして、デプロイ プロファイルの名前または説明を変更します。 変更したら、**[保存]** をクリックします。 
7. **[設定]** をクリックして、OOBE 設定を変更します。 変更したら、**[保存]** をクリックします。 

> [!NOTE]
> 更新されたプロファイルがデバイスに割り当てられます。 ただし、更新されたプロファイルは、デバイスがリセットされ、再登録されるまで、Intune に既に登録されているデバイスには適用されません。 

## <a name="using-autopilot-in-other-portals"></a>他のポータルでの AutoPilot の使用
モバイル デバイス管理が不要な場合は、ビジネス向け Microsoft ストアなどで AutoPilot を使用できます。 他のポータルの使用はオプションですが、AutoPilot Deployment を管理する場合には Intune のみを使用することをお勧めします。 Intune と別のポータルを使用する場合、Intune では以下の操作を行うことはできません。
- Intune で作成されたが、別のポータルで編集されたプロファイルの変更を表示する
- 別のポータルで作成されたプロファイルを同期する
- 別のポータルで行われたプロファイル割り当ての変更を表示する
- 別のポータルで行われたプロファイル割り当てを同期する

## <a name="next-steps"></a>次のステップ
登録済み Windows 10 デバイス用に Windows AutoPilot を構成したら、これらのデバイスを管理する方法を学習します。 詳細については、「[Microsoft Intune デバイスの管理とは](https://docs.microsoft.com/intune/device-management)」を参照してください。