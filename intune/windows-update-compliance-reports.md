---
title: Microsoft Intune で Windows Updates 用の Update Compliance レポートを使用する | Microsoft Docs
description: OMS Update Compliance を使用して、Intune で展開する Windows Updates のレポート データを表示します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2b236d01cb5ffcf5a26e71ac0a9b65bb586dcb1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039666"
---
# <a name="intune-compliance-reports-for-updates"></a>更新プログラムに関する Intune コンプライアンス レポート
Intune を使用して Windows 10 デバイスに Windows の更新プログラムを展開する場合は、Intune を使用するか、または Microsoft Operations Management Suite (OMS) の一部であり、*Update Compliance* と呼ばれる無料のソリューションを使用することで、更新プログラムのコンプライアンスについて詳細を表示できます。

## <a name="use-intune"></a>Intune を使用する
構成済みの Windows 10 更新プログラム リングの展開状態に関するポリシー レポートを確認するには:  
1. [Azure ポータル](https://portal.azure.com/)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[ソフトウェア更新プログラム]** > **[概要]** の順に選択します。 割り当てたすべての更新プログラム リングの状態に関する一般的な情報を表示することができます。
4. 次のレポートのいずれかを開きます。  

   **すべての展開リングの場合**:
   1. **[ソフトウェア更新プログラム]** > **[Windows 10 更新プログラムのリング]** の順に移動します。
   2. **[監視] セクション**で、**[更新プログラムごとのリングの展開の状態]** を選択します。  

   **特定の展開リングの場合**:  

   1. **[ソフトウェア更新プログラム]** > **[Windows 10 更新プログラムのリング]** で、確認する展開リングを選択します。  
   2. **[監視]** セクションで、更新プログラム リングの詳細情報を表示するレポートを以下から選択します。  
      - **デバイスの状態**  
      - **ユーザーの状態**  

## <a name="use-update-compliance"></a>Update Compliance を使用する
Windows 10 更新プログラム ロールアウトを監視するには、Windows Analytics ソリューションである [Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) を使用します。 Update Compliance は、Azure portal を介して提供され、[前提条件](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites)を満たすデバイスでは無料で使用できます。  

このソリューションを使用する場合は、更新プログラムのコンプライアンス対応を報告する任意の Intune マネージド Windows 10 デバイスに商用 ID を展開します。  

Intune コンソールで、カスタム ポリシーの OMA-URI 設定を使用して商用 ID を構成します。 詳しくは、「[Microsoft Intune での Windows 10 デバイス向けの Intune ポリシー設定](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)」を参照してください。  

商用 ID を構成するための OMA-URI (大文字と小文字を区別する) パスは、*./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID* です。  

たとえば、**[OMA-URI 設定の追加または編集]** で次の値を使用できます。
- **設定名**:Windows Analytics の商用 ID
- **設定の説明**:Windows Analytics ソリューションの商用 ID を構成
- **OMA-URI** (大文字と小文字を区別): .*./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **データ型**:String
- **値**: \<OMS ワークスペースの Windows 利用統計情報に示された GUID を使用>
 
> [!NOTE]  
> MS DM サーバーに関する詳細については、「[DMClient 構成サービス プロバイダー (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)」を参照してください。

## <a name="next-steps"></a>次の手順
[Intune でのソフトウェア更新プログラムの管理](windows-update-for-business-configure.md)

