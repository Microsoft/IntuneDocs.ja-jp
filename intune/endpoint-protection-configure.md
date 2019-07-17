---
title: Microsoft Intune - Azure でエンドポイント保護設定を構成する | Microsoft Docs
description: Microsoft Intune で macOS または Windows 10 デバイス プロファイルを作成するとき、エンドポイント保護設定を作成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 1a5cd898545bae51395352d5cf1e7b1ee9bd22dd
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883241"
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


## <a name="next-steps"></a>次の手順  

プロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。
