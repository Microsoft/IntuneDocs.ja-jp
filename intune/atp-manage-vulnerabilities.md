---
title: Intune を使用して、Microsoft Defender ATP によって検出された脆弱性を修復する - Azure | Microsoft Docs
description: Intune コンソール内で Microsoft Defender Advanced Threat Protection (ATP) の一部である脅威と脆弱性の管理からセキュリティ タスクを管理する方法を説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6f6f319b5c38f290f3cdb6d4a04528f3b227212
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65733393"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Intune を使用して Microsoft Defender ATP によって検出された脆弱性を修復する  

Intune と Microsoft Defender Advanced Threat Protection (ATP) を統合すると、ATP の脅威と脆弱性の管理 (TVM) を利用でき、Intune を使って TVM によって検出されたエンドポイントの脆弱性を修復できます。 この統合により、環境全体で修復の応答時間を向上させることができるリスク ベースのアプローチが、脆弱性の検出と優先順位付けに組み込まれます。  

[脅威と脆弱性の管理](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt)は、[Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) の一部です。  

## <a name="how-integration-works"></a>統合のしくみ  

Intune を Microsoft Defender Advanced Threat Protection に接続すると、ATP はマネージド デバイスから脅威と脆弱性の詳細を受け取るようになります。  

Windows Defender Security Center コンソールで、ATP セキュリティ管理者はエンドポイントの脆弱性に関するデータを確認します。 その後、管理者は脆弱性のあるデバイスに要修復のフラグを設定するセキュリティ タスクをシングル クリックで作成します。 セキュリティ タスクはすぐに Intune コンソールに渡され、そこで Intune 管理者はそれらを表示できます。 セキュリティ タスクでは、脆弱性の種類、優先度、状態、および脆弱性修復手順が示されます。 Intune 管理者は、タスクの同意または拒否を選択します。  

タスクに同意したら、Intune 管理者はセキュリティ タスクの一部として提供されたガイダンスを使って、Intune で脆弱性を修復します。  

修復のための一般的なアクションは次のとおりです。  
- アプリケーションが実行されないように**ブロック**します  
- オペレーティング システムの更新プログラムを**展開**して、脆弱性を軽減します。  
- レジストリの値を**変更**します。  
- 構成を**無効**または**有効**にして、脆弱性に影響を与えます。  
- 提供する適切な推奨事項がない場合は、**注意が必要です**によって管理者は脅威に対する警告を受けます。  

ワークフローの例:  
- Microsoft Defender ATP で Contoso Media Player v4 という名前のアプリに対する脆弱性が検出され、管理者はそのアプリを更新するセキュリティ タスクを作成します。 Contoso Media Player は、Intune で展開されたアンマネージド アプリです。  

  Intune コンソールには、このセキュリティ タスクが保留中という状態で表示されます。  
  ![Intune コンソールでセキュリティ タスクの一覧を表示する](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- Intune 管理者は、セキュリティ タスクを選択してタスクについての詳細を表示します。  管理者が **[同意する]** を選択すると、Intune および ATP の状態が *[同意済み]* に更新されます。  
  ![セキュリティ タスクを同意または拒否する](./media/atp-manage-vulnerabilities/temp-accept-task.png) 
 
- その後、管理者は、提供されたガイダンスに基づいてタスクを修復します。  ガイダンスは、必要な修復の種類によって異なります。 利用できる場合、修復ガイダンスには、Intune で構成に関連するウィンドウを開くリンクが含まれます。 

  この例の Media Player はマネージド アプリではないため、Intune で提供できるのはテキストでの説明のみです。 アプリがマネージドであった場合、Intune では更新バージョンをダウンロードする手順を提供でき、更新されたファイルを展開に追加できるようにアプリの展開を開くためのリンクが提供されます。 

- 修復が完了した後、Intune 管理者はセキュリティ タスクを開き、**[タスクの完了]** を選択します。  Intune と ATP で修復の状態が更新され、セキュリティ管理者は脆弱性の状態が変更されたことを確認します。  

## <a name="prerequisites"></a>必要条件  

**サブスクリプション**:   
- Microsoft Intune  
- Microsoft Defender Advanced Threat Protection ([無料試用版にサインアップ](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink))  

**ATP 用の Intune の構成**:   
- Microsoft Defender ATP でサービス間の接続を構成します。  
- ATP によって評価されるリスクがあるデバイスに、プロファイルの種類を **Microsoft Defender ATP (Windows 10 Desktop)** にしてデバイス コンプライアンス ポリシーを展開します。
  ATP で動作するように Intune を設定する方法については、[Intune の条件付きアクセスでの Microsoft Defender ATP に対するコンプライアンスの適用](https://docs.microsoft.com/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune)に関する記事をご覧ください。  

## <a name="work-with-security-tasks"></a>セキュリティ タスクを処理する  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、**[デバイスのセキュリティ]** > **[セキュリティ タスク]** に移動します。  
2. 一覧からタスクを選択してリソース ウィンドウを開き、そのセキュリティ タスクに対する追加の詳細を表示します。  
3. セキュリティ タスクのリソース ウィンドウを表示している間に、追加のリンクを選択できます。  
   - [マネージド アプリ] - 脆弱であるアプリケーションが表示されます。 その脆弱性が複数のアプリに適用されるときは、アプリのフィルター処理された一覧が表示されます。  
   - [デバイス] - "*脆弱性のあるデバイス*" の一覧が表示されます。そこから、リンクを介してそのデバイスでの脆弱性に関するさらに詳細なエントリに移動できます。  
   - [要求元] - リンクを使って、このセキュリティ タスクを送信した管理者にメールを送ります。  
   - [メモ] - セキュリティ タスクを開くときに、要求元によって送信されたカスタム メッセージを読みます。  
4. **[同意する]** または **[拒否]** を選択して、計画されているアクションについて ATP に通知を送信します。 タスクを同意または拒否するときは、メモを ATP に送信できます。  

5. タスクに同意した後、セキュリティ タスクを再び開き (閉じてあった場合)、修復の詳細に従って脆弱性を修復します。  セキュリティ タスクの詳細で ATP によって提供される指示は、関係する脆弱性によって異なります。  

   可能な場合、修復手順には Intune コンソールで関連する構成オブジェクトを開くリンクが含まれます。  

6. 修復手順を完了した後、セキュリティ タスクを開き、**[タスクの完了]** を選択します。  このアクションにより、Intune と ATP の両方でセキュリティ タスクの状態が更新されます。  

修復が成功した後、修復されたデバイスからの新しい情報に基づき、ATP のリスク エクスポージャ スコアが下がる場合があります。 

## <a name="next-steps"></a>次の手順
Intune と [Microsoft Defender ATP](https://docs.microsoft.com/intune/advanced-threat-protection) についてさらに詳しく学習する  
Intune の [Mobile Threat Defense](https://docs.microsoft.com/intune/mobile-threat-defense) について確認する  
Microsoft Defender ATP で[脅威と脆弱性の管理ダッシュボード](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights)について確認する
