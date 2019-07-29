---
title: プラットフォームでサポートされている暗号化方法を使用して Microsoft Intune でデバイスを暗号化する
titleSuffix: Microsoft Intune
description: BitLocker や FileVault などの組み込みの暗号化方式を使用してデバイスを暗号化し、Intune ポータル内からそれらの暗号化されたデバイスの回復キーを管理します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 57b459efa5b423f1c73a0d6b7b9172f71f4c86d3
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375163"
---
# <a name="use-device-encryption-with-intune"></a>Intune でデバイスの暗号化を使用する  

Intune を使用して、デバイス上のデータを保護する組み込みディスクまたはドライブ暗号化デバイスを管理します。  

エンドポイント保護のためのデバイス構成プロファイルの一部として、ディスクの暗号化を構成します。 Intune によって、次のプラットフォームと暗号化テクノロジがサポートされています。  
- macOS:FileVault   
- Windows 10 以降:BitLocker  

Intune では、管理されているすべてのデバイスのデバイスの暗号化ステータスに関する詳細を表示する、組み込みの[暗号化レポート](encryption-monitor.md)も用意されています。  

## <a name="filevault-encryption-for-macos"></a>MacOS 用 FileVault 暗号化  

Intune を使用して、macOS を実行するデバイスで FileVault のディスク暗号化を構成します。 次に、Intune の暗号化レポートを使用して、これらのデバイスの暗号化の詳細を表示し、FileVault で暗号化されたデバイスの回復キーを管理します。  

FileVault は、macOS に含まれるディスク全体の暗号化プログラムです。 Intune を使用して、**macOS 10.13 以降**を実行するデバイスで FileVault を構成することができます。  

FileVault を構成するには、macOS プラットフォームのエンドポイント保護用の[デバイス構成プロファイル](device-profile-create.md)を作成します。 FileVault 設定は、macOS エンドポイント保護で使用可能な設定カテゴリの 1 つです。  

FileVault を使用してデバイスを暗号化するポリシーを作成すると、そのポリシーは 2 段階でデバイスに適用されます。 まず、Intune が回復キーを取得してバックアップできるようにデバイスが準備されます。 これはエスクローと呼ばれます。 キーがエスクローされると、ディスクの暗号化が開始されます。

![FileVault の設定](./media/encrypt-devices/filevault-settings.png)

Intune で管理できる FileVault 設定の詳細については、macOS エンドポイント保護設定に関する Intune の記事の「[FileVault](endpoint-protection-macos.md#filevault)」を参照してください。  

### <a name="how-to-configure-macos-filevault"></a>macOS FileVault を構成する方法 

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインして、 **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に移動します。  

2. 次のオプションを設定します。  

   - プラットフォーム: macOS  
   - プロファイルの種類:Endpoint Protection  

3. **[設定]**  >  **[FileVault]** の順に選択します。  

4. *FileVault* で **[有効]** を選択します。  

5. *[回復キーの種類]* には、**個人用キー**のみがサポートされています。  

   自分のデバイスの回復キーを取得する方法について、エンド ユーザーを支援するガイドにメッセージを追加することを検討してください。 この情報は、個人用回復キーの交換の設定を使用するときに、デバイスの新しい回復キーを定期的に自動生成することができるため、エンド ユーザーにとって役立ちます。  

   次に例を示します。紛失した、または最近交換した回復キーを取得するには、任意のデバイスから Intune ポータル Web サイトにサインインします。 ポータルで、 *[デバイス]* に移動し、FileVault が有効になっているデバイスを選択し、 *[回復キーを取得する]* を選択します。 現在の回復キーが表示されます。  

6. ビジネス ニーズに合わせて残りの設定を構成し、 **[OK]** を選択します。  

   > [!NOTE]
   > FileVault のサポートは、7 月のリリースのロールアウトが完了するまでの数日間、制限されます。 ロールアウトが完了するまで、FileVault を構成する場合は、 *[サインアウトするまで FileVault を延期する]* を **[有効]** に設定する必要があります。  

7. 追加設定の構成を完了したら、プロファイルを保存します。  

### <a name="manage-filevault"></a>FileVault の管理  

Intune で FileVault を使用して macOS デバイスを暗号化すると、Intune の[暗号化レポート](encryption-monitor.md)を表示したときに、FileVault 回復キーを表示して管理できます。  

## <a name="bitlocker-encryption-for-windows-10"></a>Windows 10 の BitLocker 暗号化  

Intune を使用して、Windows 10 を実行するデバイスで BitLocker ドライブ暗号化を構成します。 次に、Intune の暗号化レポートを使用して、これらのデバイスの暗号化の詳細を表示します。 Azure Active Directory (Azure AD) で見られるように、お使いのデバイスから BitLocker の重要な情報にアクセスすることもできます。  

BitLocker は、**Windows 10 以降**を実行しているデバイスで使用できます。  

Windows 10 以降のプラットフォームのエンドポイント保護用の[デバイス構成プロファイル](device-profile-create.md)を作成するときに、BitLocker を構成します。 BitLocker 設定は、Windows 10 エンドポイント保護の Windows 暗号化設定カテゴリに含まれています。    

![BitLocker 設定](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>Windows 10 BitLocker を構成する方法  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、[デバイスの構成]、[プロファイル]、[プロファイルの作成] の順に移動します。  

2. 次のオプションを設定します。  
   - プラットフォーム:Windows 10 以降  
   - プロファイルの種類:Endpoint Protection  

3. **[設定]**  >  **[Windows 暗号化]** の順に選択します。

4. ビジネス ニーズに合わせて BitLocker の設定を構成し、 **[OK]** を選択します。  

5. 追加設定の構成を完了したら、プロファイルを保存します。  

### <a name="manage-bitlocker"></a>BitLocker の管理  

Intune で BitLocker を使用して Windows 10 デバイスを暗号化すると、Intune の[暗号化レポート](encryption-monitor.md)を表示したときに、BitLocker 回復キーを表示して取得できます。  

## <a name="next-steps"></a>次の手順  

[デバイス コンプライアンス](compliance-policy-create-windows.md) ポリシーの作成  

暗号化レポートを使用して、次の管理を行います。  
- [BitLocker 回復キー](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 回復キー](encryption-monitor.md#filevault-recovery-keys)

Intune で構成できる次の暗号化設定を確認します。  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
