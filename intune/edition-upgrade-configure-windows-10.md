---
title: Windows 10 デバイス上でのアップグレードまたは S モードの使用 - Microsoft Intune - Azure | Microsoft Docs
description: Windows 10 デバイスを別のエディションにアップグレードする場合や S モードを有効にする場合に Microsoft Intune を使用します。 管理者はデバイス構成プロファイルを使用して、Windows 10 Professional の Windows 10 Enterprise へのアップグレード、S モードの有効化、S モードからの切り替えを行うことができます。 Windows 10 Pro、N Edition、Education、Cloud、Enterprise、Core、Holographic、Mobile については、サポートされるアップグレード パスを参照してください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3eea1d1f100515b29dfda3b2297005f61e05ea23
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831617"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Microsoft Intune を使用しているデバイス上での Windows 10 エディションのアップグレードまたは S モードの有効化

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

モバイル デバイス管理 (MDM) ソリューションの一部として、Windows 10 デバイスをアップグレードすることができます。 たとえば、Windows 10 Professional デバイスを Windows 10 Enterprise にアップグレードすることができます。 また、S モバイルを有効にして、デバイスで Microsoft Store のアプリのみを実行するようにします。

[Windows 10 S モード](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)はセキュリティとパフォーマンスのために設計されています。 Microsoft Store からのアプリのみをデバイスで実行する場合、S モードを利用し、デバイスをセキュリティで保護できます。 Microsoft Store で入手できないアプリをデバイスで使用する場合は、S モードから切り替えます。 S モードから切り替える操作は一方向です。 Windows 10 S モードから切り替えると、戻ることができません。

この機能は、以下に適用されます。

- Windows 10 以降
- S モードの場合は Windows 10 1809 以降
- Windows Holographic for Business

これらの機能は Intune で使用できます。また、管理者が構成できます。 Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後は、そのプロファイルをお客様の組織内の Windows 10 デバイスにプッシュまたは展開できます。 プロファイルを展開すると、Intune によって自動的にデバイスがアップグレードされるか、S モードが有効になります。

この記事では、サポートされているアップグレード パスの一覧を示し、デバイス構成プロファイルの作成方法を説明します。 また、[Windows 10](edition-upgrade-windows-settings.md) で使用できるすべてのアップグレードと S モード設定についても紹介します。

> [!NOTE]
> 後でポリシーの割り当てを削除しても、デバイス上の Windows のバージョンは元に戻りません。 デバイスは引き続き正常に動作します。

## <a name="prerequisites"></a>必要条件

デバイスをアップグレードする前に、次の前提条件が満たされていることを確認します。

- ポリシーで対象とするすべてのデバイスにアップデートされたバージョンの Windows をインストールするための有効なプロダクト キー (Windows 10 Desktop エディションの場合)。 マルチ ライセンス認証キー (MAK) またはキー マネジメント サーバー (KMS) キーのどちらかを使用できます。
- Windows 10 Mobile エディションと Windows 10 Holographic エディションの場合は、Microsoft ライセンス ファイルを使用できます。 このライセンス ファイルには、ポリシーで対象としているすべてのデバイス上に更新されたエディションをインストールするためのライセンス情報が含まれています。
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

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **[名前]**:新しいプロファイルのわかりやすい名前を入力します。 たとえば、`Windows 10 edition upgrade profile` や `Windows 10 switch off S mode` などを入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]**:プラットフォームを選択します。  

        - **Windows 10 以降**

    - **[プロファイルの種類]**:**[エディションのアップグレード]** を選択します。
    - **設定**:構成が必要な設定を入力します。 すべての設定の一覧とその実行内容については、以下を参照してください。

        - [Windows 10 のアップグレードと S モード](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. **[OK]** > **[作成]** を選択して変更を保存します。 

プロファイルが作成され、一覧に表示されます。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

## <a name="next-steps"></a>次の手順

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

[Windows 10](edition-upgrade-windows-settings.md) デバイスと [Windows Holographic for Business](holographic-upgrade.md) デバイスのアップグレードと S モード設定を確認します。
