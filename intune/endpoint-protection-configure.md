---
title: Microsoft Intune - Azure でエンドポイント保護設定を構成する | Microsoft Docs
description: Microsoft Intune で macOS または Windows 10 デバイス プロファイルを作成するとき、エンドポイント保護設定を作成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: d0e3e67cd227c5ce8ac2cb42f79bdea1da8e2d75
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375112"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Intune でエンドポイント保護設定を追加する  

Intune でデバイスの構成プロファイルを使用し、次などのデバイスで、共通のエンドポイント保護セキュリティ機能を管理できます。  
- ファイアウォール   
- BitLocker  
- アプリの許可とブロック  
- Windows Defender と暗号化  

たとえば、macOS ユーザーに Mac App Store からのみアプリのインストールを許可するエンドポイント保護プロファイルを作成できます。 あるいは、Windows 10 デバイスでアプリを実行しているとき、Windows SmartScreen を有効にします。  

プロファイルを作成する前に、サポート対象のそれぞれのプラットフォームで Intune が管理できる、エンドポイント保護設定の詳細が記述されている次の記事を確認してください。  
   - [macOS の設定](endpoint-protection-macos.md)  
   - [Windows 10 の設定](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>エンドポイント保護設定を含むデバイス プロファイルを作成する  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。  
3. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。  
4. エンドポイント保護プロファイルの **[名前]** と **[説明]** を入力します。  
5. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイスの制限設定に対応している次のいずれかのプラットフォームを選択できます。  
   - **macOS**  
   - **Windows 10 以降**  
6. **[プロファイルの種類]** ドロップダウン リストで、 **[Endpoint Protection]** を選択します。  
7. 選択したプラットフォームによって構成できる設定が異なります。 次を参照してください。  
   - [macOS の設定](endpoint-protection-macos.md)  
   - [Windows 10 の設定](endpoint-protection-windows-10.md)  

8. 適切な設定を構成したら、 **[プロファイルの作成]** ページで **[作成]** を選択します。  

   プロファイルが作成され、プロファイルの一覧ページに表示されます。 このプロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Windows 10 デバイスのカスタム ファイアウォール規則を追加する  
***カスタム ファイアウォール規則はパブリック プレビュー段階です。***  

Windows 10 のエンドポイント保護規則を含むプロファイルの一部として Windows Defender ファイアウォールを構成する場合は、ファイアウォールのカスタム規則を構成できます。 カスタム規則を使用すると、Windows 10 でサポートされているファイアウォール規則の定義済みセットを拡張できます。  

カスタム ファイアウォール規則を含むプロファイルを計画する場合は、次の情報を考慮してください。これは、プロファイルでファイアウォール規則をグループ化する際に選択する方法に影響する可能性があります。  
- 各プロファイルでは、最大 150 個のファイアウォール規則がサポートされます。 150 個を超える規則を使用する場合は、それぞれ 150 個の規則に限定された、追加のプロファイルを作成します。  
- プロファイルごとに、単一の規則を適用できなかった場合、そのプロファイルのすべての規則が失敗し、デバイスにはどの規則も適用されません。  
- 規則を適用できなかったときは、プロファイル内のすべての規則が失敗として報告されます。 Intune では、失敗した個々の規則を識別することはできません。  

Intune で管理できるファイアウォール規則については、Windows の[ファイアウォール構成サービス プロバイダー]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) (CSP) に関するページで詳しく説明されています。 Intune でサポートされる Windows 10 デバイスのカスタム ファイアウォール設定のリストを確認する場合は、[カスタム ファイアウォール規則](endpoint-protection-windows-10.md#custom-firewall-rules)に関するセクションを参照してください。  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Endpoint Protection プロファイルにカスタム ファイアウォール規則を追加するには  

1. Intune で、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に移動します。  

2. *[プラットフォーム]* では **[Windows 10 以降]** を選択し、 *[プロファイルの種類]* では **[Endpoint protection]** を選択します。  

3. **[Windows Defender ファイアウォール]** を選択して構成ページを開き、 *[ファイアウォール規則]* では **[追加]** を選択し、 **[規則の作成]** ページを開きます。  

4. ファイアウォール規則の設定を指定し、 **[OK]** を選択して保存します。 ドキュメントで利用可能なカスタム ファイアウォール規則のオプションを確認する場合は、[カスタム ファイアウォール規則](endpoint-protection-windows-10.md#custom-firewall-rules)に関するセクションを参照してください。  

5. 規則を保存した後、 *[Windows Defender ファイアウォール]* ページの規則のリストに表示されます。  

6. 規則を変更するには、リストから規則を選択して **[規則の編集]** ページを開きます。  

7. プロファイルから規則を削除するには、その規則の省略記号 **(...)** を選択し、 **[削除]** を選びます。  

8. 規則の表示順序を変更するには、規則リストの上部にある*上矢印、下矢印* アイコンを選択します。  


## <a name="next-steps"></a>次の手順  

プロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。  
