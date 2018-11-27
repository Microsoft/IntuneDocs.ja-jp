---
title: Microsoft Intune で Windows 10 デバイスをアップグレードするか、S モードを使用する - Azure | Microsoft Docs
description: Microsoft Intune でデバイス プロファイルを作成し、Windows 10 デバイスを別のエディションにアップグレードします。 たとえば、Windows 10 Professional から Windows 10 Enterprise にアップグレードできます。 構成プロファイルを利用し、デバイス上で S モードを有効にしたり、S モードから抜けたりすることもできます。 Windows 10 Pro、N Edition、Education、Cloud、Enterprise、Core、Holographic、Mobile でサポートされるアップグレード パスについても説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eb44647e50e406b9ef5052c576660c9b7eebf6dd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189760"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Intune で構成プロファイルを使用して Windows 10 をアップグレードするか、S モードから切り替える
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune でアップグレード プロファイルを構成し、Windows 10 エディションを実行するデバイスを自動的に別のエディションにアップグレードします。 サポートされるアップグレード パスについても紹介します。

## <a name="before-you-begin"></a>始める前に
デバイスを最新版にアップグレードするには、次の前提条件が必要です。

- ポリシーで対象とするすべてのデバイスにアップデートされたバージョンの Windows をインストールするための有効なプロダクト キー (Windows 10 Desktop エディションの場合)。 マルチ ライセンス認証キー (MAK) またはキー マネジメント サーバー (KMS) キーのどちらかを使用できます。 Windows 10 Mobile エディションと Windows 10 Holographic エディションの場合、ポリシーで対象とするべてのデバイスに更新版の Windows をインストールするためのライセンス情報を含む Microsoft ライセンス ファイルを使用できます。
- ポリシーを割り当てる Windows 10 デバイスが Microsoft Intune に登録されます。 エディションのアップグレード ポリシーは、Intune PC クライアント ソフトウェアを実行する PC で使用できません。

## <a name="supported-upgrade-paths"></a>サポートされるアップグレード パス
Windows 10 エディションのアップグレード プロファイルでサポートされるアップグレード パスを次の表に示します。

| アップグレード前のバージョン | アップグレード後のバージョン |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Windows 10 Pro N エディション | Windows 10 Education N エディション <br/>Windows 10 Enterprise N エディション <br/>Windows 10 Pro Education N エディション | 
| Windows 10 Pro Education | Windows 10 Education | 
| Windows 10 Pro Education N エディション | Windows 10 Education N エディション |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Windows 10 Cloud N エディション | Windows 10 Education N エディション <br/>Windows 10 Enterprise N エディション <br/>Windows 10 Pro N エディション <br/>Windows 10 Pro Education N エディション | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 Enterprise N エディション | Windows 10 Education N エディション | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Windows 10 Core N エディション | Windows 10 Education N エディション <br/>Windows 10 Enterprise N エディション <br/>Windows 10 Pro Education N エディション | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="upgrade-the-edition"></a>エディションをアップグレードする

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。
3. プロファイルの **[名前]** と **[説明]** を入力します。 たとえば、`Windows 10 edition upgrade` のようなものを入力します。
4. **[プラットフォーム]** には、**[Windows 10 以降]** を選択します。
5. **[プロファイルの種類]** には、**[エディションのアップグレード]** を選択します。
6. **[エディションのアップグレード]** プロパティで、次の設定を入力します。

   - **アップグレード後のエディション**: アップグレード後の Windows 10 エディションを選択します。 このポリシーで対象となるデバイスが選択したエディションにアップグレードされます。
   - **プロダクト キー**: Microsoft から受け取ったプロダクト キーを入力します。 プロダクト キーを含むポリシーの作成後、キーは更新できなくなり、セキュリティ上の理由から非表示になります。 プロダクト キーを変更するには、キー全体を再入力します。
   - **ライセンス ファイル**: **[Windows 10 Holographic for Business]** または **[Windows 10 Mobile エディション]** については、**[参照]** を選択し、Microsoft から受け取ったライセンス ファイルを選択します。 このライセンス ファイルには、対象のデバイスをアップグレードするエディションのライセンス情報が含まれています。

7. **[OK]** を選択して変更を保存します。 **[作成]** を選択して、プロファイルを作成します。

## <a name="switch-out-of-s-mode"></a>S モードから抜ける

[Windows 10 S モード](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)はセキュリティとパフォーマンスのために設計されています。 Microsoft Store からのアプリのみをデバイスで実行する場合、S モードを利用し、デバイスをセキュリティで保護できます。 Microsoft Store で利用できないアプリがデバイスで必要な場合、S モードから抜けます。 S モードから抜けるという行為は一方向です。 Windows 10 S モードから一度抜けると、戻ることができません。

次の手順は、Windows 10 (1809 以降) デバイスで S モードを制御するプロファイルを作成する方法です。

1. **Azure Portal** で、[[すべてのサービス]](https://portal.azure.com) を選択し、**[Intune]** をフィルターとして適用して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。
3. プロファイルの **[名前]** と **[説明]** を入力します。 たとえば、`Windows 10 switch off S mode` のようなものを入力します。
4. **[プラットフォーム]** には、**[Windows 10 以降]** を選択します。
5. **[プロファイルの種類]** には、**[エディションのアップグレード]** を選択します。
6. **[モードの切り替え (Windows Insider のみ)]** を選択し、**[S モードから切り替える]** プロパティを設定します。 次のようなオプションがあります。

    - **構成しない**: S モード デバイスは S モードのままになります。 エンドユーザーはデバイスを S モードから抜けさせることができます。
    - **S モードを維持する**: エンド ユーザーはデバイスを S モードから抜けさせることができなくなります。
    - **切り替える**: デバイスを S モードから抜けさせます。

7. **[OK]** を選択して変更を保存します。 **[作成]** を選択して、プロファイルを作成します。

プロファイルが作成され、プロファイルの一覧に表示されます。

## <a name="next-steps"></a>次の手順

グループに[このプロファイルを割り当てます](device-profile-assign.md)。

>[!NOTE]
>後でポリシーの割り当てを削除する場合、デバイス上の Windows のバージョンは元に戻されず、正常に機能を続けます。
