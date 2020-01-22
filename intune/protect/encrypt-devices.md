---
title: プラットフォームでサポートされている暗号化方法を使用してデバイスを暗号化する
titleSuffix: Microsoft Intune
description: BitLocker や FileVault などの組み込みの暗号化方式を使用してデバイスを暗号化し、Intune ポータル内からそれらの暗号化されたデバイスの回復キーを管理します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5209ce7fba30a156de055503751104f9090d49d7
ms.sourcegitcommit: e7052114324b80d0503b107c934bb90b8eb29704
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75756008"
---
# <a name="use-device-encryption-with-intune"></a>Intune でデバイスの暗号化を使用する

Intune を使用して、デバイス上のデータを保護する組み込みディスクまたはドライブ暗号化デバイスを管理します。

エンドポイント保護のためのデバイス構成プロファイルの一部として、ディスクの暗号化を構成します。 Intune によって、次のプラットフォームと暗号化テクノロジがサポートされています。

- macOS:FileVault
- Windows 10 以降:BitLocker

Intune では、管理されているすべてのデバイスのデバイスの暗号化ステータスに関する詳細を表示する、組み込みの[暗号化レポート](encryption-monitor.md)も用意されています。

## <a name="filevault-encryption-for-macos"></a>MacOS 用 FileVault 暗号化

Intune を使用して、macOS を実行するデバイスで FileVault のディスク暗号化を構成します。 次に、Intune の暗号化レポートを使用して、これらのデバイスの暗号化の詳細を表示し、FileVault で暗号化されたデバイスの回復キーを管理します。

デバイス上で FileVault を機能させるためには、ユーザー承認済みのデバイス登録が必要であることに注意してください。 登録がユーザー承認済みであると見なされるためには、そのユーザーがシステム環境設定から手動で管理プロファイルを承認する必要があります。 

FileVault は、macOS に含まれるディスク全体の暗号化プログラムです。 Intune を使用して、**macOS 10.13 以降**を実行するデバイスで FileVault を構成することができます。

FileVault を構成するには、macOS プラットフォームのエンドポイント保護用の[デバイス構成プロファイル](../configuration/device-profile-create.md)を作成します。 FileVault 設定は、macOS エンドポイント保護で使用可能な設定カテゴリの 1 つです。

FileVault を使用してデバイスを暗号化するポリシーを作成すると、そのポリシーは 2 段階でデバイスに適用されます。 まず、Intune が回復キーを取得してバックアップできるようにデバイスが準備されます。 これはエスクローと呼ばれます。 キーがエスクローされると、ディスクの暗号化が開始されます。

![FileVault の設定](./media/encrypt-devices/filevault-settings.png)

Intune で管理できる FileVault 設定の詳細については、macOS エンドポイント保護設定に関する Intune の記事の「[FileVault](endpoint-protection-macos.md#filevault)」を参照してください。

### <a name="how-to-configure-macos-filevault"></a>macOS FileVault を構成する方法

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。

3. 次のオプションを設定します。

   - プラットフォーム: macOS
   - プロファイルの種類:エンドポイント保護

4. **[設定]**  >  **[FileVault]** の順に選択します。

5. *FileVault* で **[有効]** を選択します。

6. *[回復キーの種類]* には、**個人用キー**のみがサポートされています。

   自分のデバイスの回復キーを取得する方法について、エンド ユーザーを支援するガイドにメッセージを追加することを検討してください。 この情報は、個人用回復キーの交換の設定を使用するときに、デバイスの新しい回復キーを定期的に自動生成することができるため、エンド ユーザーにとって役立ちます。

   次に例を示します。紛失した、または最近交換した回復キーを取得するには、任意のデバイスから Intune ポータル Web サイトにサインインします。 ポータルで、 *[デバイス]* に移動し、FileVault が有効になっているデバイスを選択し、 *[回復キーを取得する]* を選択します。 現在の回復キーが表示されます。

7. ご自身のビジネス ニーズに合うよう残りの [FileVault 設定](endpoint-protection-macos.md#filevault)を構成した後、 **[OK]** を選択します。

  8. 追加設定の構成を完了したら、プロファイルを保存します。  

### <a name="manage-filevault"></a>FileVault の管理

Intune で FileVault を使用して macOS デバイスを暗号化すると、Intune の[暗号化レポート](encryption-monitor.md)を表示したときに、FileVault 回復キーを表示して管理できます。

Intune で FileVault を使って macOS デバイスを暗号化した後は、任意のデバイス上の Web ポータル サイトから、そのデバイスの個人用回復キーを表示できます。 Web ポータル サイトで、暗号化された macOS デバイスを選択した後、リモート デバイス アクションとして [回復キーを取得する] を選択します。

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>MEM 暗号化 macOS デバイスから個人用回復キーを取得する

エンド ユーザーは、iOS ポータル サイト アプリを使用して個人用回復キー (FileVault キー) を取得できます。 個人用回復キーを持つデバイスは、Intune に登録され、Intune により FileVault を使用して暗号化されている必要があります。 エンド ユーザーは、iOS ポータル サイト アプリを使用して、FileVault 個人用回復キーを含む Web ページを開くことができます。 また、 **[デバイス]**  > "*暗号化されて登録された macOS デバイス*" >  **[回復キーの取得]** を選択することで、Intune から回復キーを取得することもできます。 

## <a name="bitlocker-encryption-for-windows-10"></a>Windows 10 の BitLocker 暗号化

Intune を使用して、Windows 10 を実行するデバイスで BitLocker ドライブ暗号化を構成します。 次に、Intune の暗号化レポートを使用して、これらのデバイスの暗号化の詳細を表示します。 Azure Active Directory (Azure AD) で見られるように、お使いのデバイスから BitLocker の重要な情報にアクセスすることもできます。

BitLocker は、**Windows 10 以降**を実行しているデバイスで使用できます。

Windows 10 以降のプラットフォームのエンドポイント保護用の[デバイス構成プロファイル](../configuration/device-profile-create.md)を作成するときに、BitLocker を構成します。 BitLocker 設定は、Windows 10 エンドポイント保護の Windows 暗号化設定カテゴリに含まれています。

![BitLocker 設定](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Windows 10 BitLocker を構成する方法

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。

3. 次のオプションを設定します。

   - プラットフォーム:Windows 10 以降
   - プロファイルの種類:エンドポイント保護

4. **[設定]**  >  **[Windows 暗号化]** の順に選択します。

5. ビジネス ニーズに合わせて BitLocker の設定を構成し、 **[OK]** を選択します。

6. 追加設定の構成を完了したら、プロファイルを保存します。

### <a name="manage-bitlocker"></a>BitLocker の管理

Intune で BitLocker を使用して Windows 10 デバイスを暗号化すると、Intune の[暗号化レポート](encryption-monitor.md)を表示したときに、BitLocker 回復キーを表示して取得できます。

### <a name="rotate-bitlocker-recovery-keys"></a>BitLocker 回復キーを交換する

Intune デバイス アクションを使用することで、Windows 10 バージョン 1909 以降を実行するデバイスの BitLocker 回復キーをリモートで交換できます。

#### <a name="prerequisites"></a>[前提条件]

BitLocker 回復キーの交換をサポートするには、デバイスで次の前提条件を満たしている必要があります。

- デバイスで Windows 10 バージョン 1909 以降を実行している必要があります。

- Azure AD 参加デバイスと Hybrid 参加デバイスで、キーの交換のサポートを有効にしておく必要があります。

  - **クライアント主導の回復パスワードの交換**

  この設定は、Windows 10 Endpoint Protection のデバイス構成ポリシーの一部として *[Windows 暗号化]* にあります。
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>BitLocker 回復キーを交換するには

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]**  >  **[すべてのデバイス]** の順に選択します。

3. 管理するデバイスの一覧で、デバイスを選択して、 **[詳細]** を選択し、 **[BitLocker キーの交換]** デバイス リモート アクションを選択します。

## <a name="next-steps"></a>次のステップ

[デバイス コンプライアンス](compliance-policy-create-windows.md) ポリシーを作成します。

暗号化レポートを使用して、次の管理を行います。

- [BitLocker 回復キー](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 回復キー](encryption-monitor.md#filevault-recovery-keys)

Intune で構成できる次の暗号化設定を確認します。

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
