---
title: Microsoft Intune - Azure でエンドポイント保護設定を構成する | Microsoft Docs
description: Microsoft Intune で macOS または Windows 10 デバイス プロファイルを作成するとき、エンドポイント保護設定を作成します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 3/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: add75e252c8d49025ac01832e5fb12afea9ede67
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512952"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Intune でエンドポイント保護設定を追加する

エンドポイント保護では、ファイアウォール、BitLocker、アプリの許可と禁止、Windows Defender、暗号化など、さまざまなセキュリティ機能を制御できます。 デバイス プロファイルを利用し、Microsoft Intune でエンドポイント保護設定を構成できます。

たとえば、macOS ユーザーに Mac App Store からのみアプリのインストールを許可するエンドポイント保護プロファイルを作成できます。 あるいは、Windows 10 デバイスでアプリを実行しているとき、Windows SmartScreen を有効にします。

この記事では、プロファイルを作成する方法を紹介します。 次に、ご利用のデバイスを選択し、利用できる設定の詳細をご覧ください。

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>エンドポイント保護設定を含むデバイス プロファイルを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. エンドポイント保護プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、カスタム設定を適用するデバイス プラットフォームを選択します。 現時点では、デバイスの制限設定に対応している次のいずれかのプラットフォームを選択できます。
   - **macOS**
   - **Windows 10 以降**
6. **[プロファイルの種類]** ドロップダウン リストで、**[Endpoint Protection]** を選択します。 
7. 選択したプラットフォームによって構成できる設定が異なります。 各プラットフォームの詳細な設定については、次のいずれかのトピックを参照してください。
   - [macOS の設定](endpoint-protection-macos.md)
   - [Windows 10 の設定](endpoint-protection-windows-10.md)
8. 完了したら、**[プロファイルの作成]** ページに戻り、**[作成]** をクリックします。

プロファイルが作成され、プロファイルの一覧ページに表示されます。 このプロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順
プロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](device-profile-assign.md)に関するページを参照してください。
