---
title: Microsoft Intune での暗号化レポートと BitLocker キー
titleSuffix: Microsoft Intune
description: Microsoft Intune ポータルでは、ご利用のデバイス暗号化の状態に関するレポートを表示すると共に、BitLocker 回復キーにアクセスできます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 52b92483ddafadf460911caaa472825a0bc0a20f
ms.sourcegitcommit: b4483c8476a209de83102e8993d8074dbb323493
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527220"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>BitLocker とデバイスの暗号化を監視する  
Intune には、ご利用の Windows 10 デバイスの暗号化の状態を識別するための一元的な場所が用意されているため、Intune を使用すれば、Azure Active Directory (Azure AD) 内で BitLocker の重要な情報が検出されたら、ご自分のデバイスからアクセスできます。  

- [暗号化レポート (パブリック プレビュー)](#encryption-report) では、デバイスの暗号化の状態と準備に関する詳細が提供されます。 レポートの詳細は、保護するデバイスの暗号化が正常に行われるのを妨げている問題を特定するのに役立ちます。  
- Intune ポータル内から、ご利用のデバイスのキー ID や回復キーなど、[BitLocker の詳細を表示する (パブリック プレビュー)](#bitlocker-recovery-keys)。  

## <a name="encryption-report"></a>レポートの暗号化
暗号化レポート (パブリック プレビュー) を使用して、ご利用の Windows 10 デバイスの暗号化の状態に関する詳細を確認できます。  

レポートを検索するには、[Intune](https://aka.ms/intuneportal) にサインインし、 **[デバイス構成]** に進み、次に *[監視]* で、 **[暗号化レポート (プレビュー)]** を選択します。  

### <a name="prerequisites"></a>前提条件:
暗号化レポートに表示されるためには、デバイス上で Windows のバージョン 1607 以降を実行している必要があります。  

### <a name="report-details"></a>レポートの詳細
レポートには、ご利用の Windows 10 デバイス対する **[デバイス名]** と、それらの各デバイスの次のような大まかな詳細が表示されます。  
- **OS バージョン** – Windows のバージョン。  
- **TPM バージョン** – デバイス上のトラステッド プラットフォーム モジュール (TPM) チップのバージョン。  
- **暗号化の準備** – BitLocker 暗号化をサポートするための、デバイスの準備に関する評価。 デバイスは次のように識別される可能性があります。
  - **準備完了**:デバイスの暗号化は MDM ポリシーを使用して行うことができます。このポリシーでは、TPM を保持していること、次に示す Windows 10 のバージョンおよび SKU の要件を満たしていることがデバイスに求められます。
    - Business、Enterprise、Education のバージョン 1703 以降
    - Pro のバージョン 1809 以降  
  
    詳細については、Windows ドキュメントの [BitLocker 構成サービス プロバイダー (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)に関するページを参照してください。  

  - **準備中**: デバイスは暗号化のすべての機能を備えていませんが、それでもデバイスでは暗号化がサポートされています。 たとえば、デバイスの暗号化は、ユーザーが手動で行ったり、TMP なしでの暗号化を許可するように設定できるグループ ポリシーを介して行ったりする場合があります。
  - **適用なし**:このデバイスを分類するための十分な情報がありません。  

- **暗号化の状態** – OS ドライブが暗号化されているかどうか。  


### <a name="device-encryption-status"></a>デバイスの暗号化の状態
デバイスを選択すると、Intune によって **[デバイスの暗号化の状態]** ウィンドウが表示されます。

このウィンドウでは、次のような詳細が表示されます。  
- **デバイス名** – 確認しているデバイスの名前。  
- **暗号化の準備** - BitLocker 暗号化をサポートするための、デバイスの準備に関する評価。 デバイスに TPM が不足していることからデバイスの暗号化の準備が "*準備中*" であっても、デバイスの暗号化の状態は "*暗号化*" となる可能性があります (詳細については、前のセクションの「暗号化の準備」を参照してください)。
- **暗号化の状態** - OS ドライブが暗号化されているかどうか。  
- **プロファイル** – このデバイスに適用され、次のプロファイルの種類と設定が含まれる "*デバイス構成*" プロファイルの一覧。  
  - プロファイルの種類 = *Endpoint protection*  
  - [設定] > [Windows 暗号化] > [デバイスの暗号化] = *必須*  

  この一覧は、プロファイルの状態の概要で問題が示されている場合、個々のポリシーを検索して確認を行う際に役立つことがあります。  

- **プロファイルの状態に関する概要** – このデバイスに適用されるプロファイルの概要。 概要では、すべての該当するプロファイルの間で最も好ましくない状況が示されます。 たとえば、1 つのプロファイルによってエラーが発生している場合、プロファイルの状態の概要には "*エラー*" が表示されます。  
- **状態の詳細** – デバイスの暗号化の状態についての詳細情報。 
  > [!NOTE]  
  > Intune では、*Windows 10 の 2019 年 4 月の更新プログラム*以降を実行しているデバイスに対してのみ "*状態の詳細*" が表示されます。
  
  このフィールドには、検出できる各該当エラーの情報が表示されます。 この情報を使用することで、デバイスがどうして暗号化準備完了の状態にならないのかを把握できます。  

  Intune から報告される状態の詳細の例を次に示します。  

   - BitLocker ポリシーによって、ユーザーは BitLocker ドライブ暗号化ウィザードを起動して OS ボリュームの暗号化を開始することに同意を求められていますが、ユーザーが同意しませんでした。  
   - OS ボリュームの暗号化の方法が、BitLocker ポリシーと一致していません。  
   - BitLocker ポリシーによって、TPM 保護機能を使用して OS ボリュームを保護するように求められていますが、TPM が使用されていません。  
   - BitLocker ポリシーによって、OS ボリューム用の保護機能として TPM のみを使用するように求められていますが、TPM 保護が使用されていません。  
   - BitLocker ポリシーによって、OS ボリューム用の保護機能として TPM + PIN 保護を使用するように求められていますが、TPM + PIN 保護機能が使用されていません。  
   - BitLocker ポリシーによって、OS ボリューム用の保護機能として TPM + 起動キー保護を使用するように求められていますが、TPM + 起動キー保護機能が使用されていません。  
   - BitLocker ポリシーによって、OS ボリューム用の保護機能として TPM + PIN + 起動キー保護を使用するように求められていますが、TPM + PIN + 起動キー保護機能が使用されていません。  
   - OS ボリュームは保護されていません。  
   - 回復キーのバックアップが失敗しました。  
   - 固定ドライブが保護されていません。  
   - 固定ドライブの暗号化の方法が、BitLocker ポリシーと一致していません。  
   - ドライブを暗号化する場合、BitLocker ポリシーによって、ユーザーが管理者としてサインインする必要がある、または、デバイスが Azure AD に参加している場合は、AllowStandardUserEncryption ポリシーを 1 に設定する必要がある、のいずれかが求められています。  
   - Windows 回復環境 (WinRE) が構成されていません。  
   - TPM が BitLocker で使用できません。原因として、それが存在していない、それがレジストリ内で利用できなくなっている、または OS がリムーバブル ドライブ上にあることが挙げられます。  
   - TPM が BitLocker で使用する準備ができていません。  
   - 回復キーのバックアップに必要なネットワークが使用できません。  

## <a name="bitlocker-recovery-keys"></a>BitLocker 回復キー
パブリック プレビューとして Intune では BitLocker 用の Azure AD ブレードにアクセスできます。これにより、Intune ポータル内から、ご利用の Windows 10 デバイス用の BitLocker キー ID および回復キーを確認できます。  アクセスできるようになるには、デバイスのキーが Azure AD にエスクローされている必要があります。 
1. [Intune](https://aka.ms/intuneportal) にサインインし、 **[デバイス]** に移動してから、 *[管理]* で、 **[すべてのデバイス]** を選択します。
2. 一覧からデバイスを選択して、 *[監視]* で、 **[回復キー – プレビュー]** を選択します。  
  
キーが Azure AD で利用できる場合は、次の情報を入手できます。
- BitLocker キー ID
- BitLocker 回復キー
- ドライブの種類  

キーが Azure AD 内に存在していない場合、Intune によって "*このデバイスの BitLocker キーが見つかりません*" が表示されます。  

BitLocker の情報については、[BitLocker 構成サービス プロバイダー](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP) に関するページを参照してください。 BitLocker CSP は、Windows 10 の場合、バージョン 1703 以降で、Windows 10 Pro の場合、バージョン 1809 以降でサポートされています。 

## <a name="next-steps"></a>次の手順
Windows 10 デバイスで BitLocker および暗号化を構成するために、[デバイス コンプライアンス](compliance-policy-create-windows.md) ポリシーを作成します。
