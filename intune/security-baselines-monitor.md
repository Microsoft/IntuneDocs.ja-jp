---
title: Microsoft Intune でセキュリティのベースラインの成功または失敗を確認する - Azure | Microsoft Docs
description: Microsoft Intune MDM でセキュリティのベースラインをユーザーとデバイスに展開するときに、エラー、競合、および成功の状態を確認します。 クライアント ログを使用してトラブルシューティングする方法と Intune のレポート機能について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b853d42efc247f6080cc4ed6ad8b4943b85b3215
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230824"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>Microsoft Intune でセキュリティのベースラインとプロファイルを監視する

セキュリティのベースラインを使用する場合はさまざまな監視オプションがあります。 ユーザーとデバイスに適用されるセキュリティのベースライン プロファイルを監視できます。 また、実際のベースラインと、推奨値と一致する (または一致しない) デバイスを監視することもできます。

この記事では、両方の監視オプションについて手順を追って説明します。

Microsoft Intune のセキュリティのベースライン機能の詳細については、[Intune のセキュリティのベースライン](security-baselines.md)に関するページを参照してください。

## <a name="monitor-the-baseline-and-your-devices"></a>ベースラインとデバイスを監視する

ベースラインを監視すると、Microsoft の推奨事項に基づいて、デバイスのセキュリティ状態に関する分析情報が得られます。

> [!NOTE]
> ベースラインを最初に割り当てた後、レポートが更新されるまでに最大 24 時間かかることがあります。 その後の更新には最大 6 時間かかることがあります。

1. [Azure portal](https://portal.azure.com/) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Intune]** を選択します。
2. **[セキュリティのベースライン (プレビュー)]** を選択し、ベースラインを選択します。
3. **[概要]** のグラフには、選択したベースラインの影響を受けるデバイスの数と、さまざまな状態が表示されます。

    ![デバイスの状態を確認する](./media/security-baselines-monitor/overview.png)

    次の状態を使用できます。

    - **Matches baseline (ベースラインと一致)**:ベースラインのすべての設定は推奨設定と一致しています。
    - **Does not match baseline (ベースラインと一致しない)**:ベースラインの少なくとも 1 つの設定が推奨設定と一致しません。
    - **正しく構成されていません**:少なくとも 1 つの設定が正しく構成されていません。 この状態は、設定が競合、エラー、または保留中の状態にあることを意味します。
    - **適用なし**:少なくとも 1 つの設定が適用可能ではなく、適用されていません。

4. デバイスがある状態の 1 つを選択します。 たとえば、**[正しく構成されていません]** 状態を選択します。

5. その状態を持つすべてのデバイスの一覧が表示されます。 特定のデバイスを選択すると、詳細が表示されます。 

    次の例では、**[デバイスの構成]** を選択し、エラー状態のプロファイルを選択します。

    ![デバイスの状態を確認する](./media/security-baselines-monitor/device-configuration-profile-list.png)

    エラーのプロファイルを選択します。 プロファイル内のすべての設定の一覧と、その状態が表示されます。 ここで、スクロールし、エラーの原因となっている設定を探します。

    ![エラーの原因となっている設定を確認する](./media/security-baselines-monitor/profile-with-error-status.png)

このレポートを使用して、問題の原因となっているプロファイル内の設定を確認します。 また、デバイスに展開されているポリシーとプロファイルの詳細情報も得られます。

> [!NOTE]
> ベースラインでプロパティが **[未構成]** に設定されている場合、その設定は無視され、制限は適用されません。 このプロパティはどのレポートにも表示されません。

## <a name="monitor-the-profile"></a>プロファイルを監視する

プロファイルを監視すると、デバイスの展開状態に関する分析情報が得られますが、ベースラインの推奨事項に基づくセキュリティ状態に関する分析情報は得られません。

1. Intune で **[Security Baselines]\(セキュリティのベースライン\)** を選択し、ベースライン、**[Profiles created]\(作成したプロファイル\)** の順に選択します。

2. プロファイルを選択します。 **[概要]** の画像には、このプロファイルが割り当てられているデバイスとユーザーの数が表示されます。

    ![セキュリティのベースライン プロファイルが割り当てられているデバイスとユーザーの数を確認する](./media/security-baselines-monitor/existing-profile-overview.png)

3. **[管理]** > **[プロパティ]** に、ベースラインのすべての設定の一覧が表示されます。 これらの設定のすべてを変更することもできます。

    ![セキュリティのベースライン プロファイルの設定を確認および更新する](./media/security-baselines-monitor/manage-settings.png)

4. **[監視]** では、個々のデバイスに関するプロファイルの展開状態、各ユーザーの状態、およびベースラインの各設定の状態を確認できます。

    ![セキュリティのベースライン プロファイルのさまざまなモニター オプションを確認する](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>設定ごとの状態を使用したトラブルシューティング

セキュリティのベースラインを展開しましたが、展開状態にエラーが表示されます。 次の手順では、エラーのトラブルシューティングに関するガイダンスをいくつか紹介します。

1. Intune で **[Security Baselines]\(セキュリティのベースライン\)** を選択し、ベースライン、**[Profiles created]\(作成したプロファイル\)** の順に選択します。
2. プロファイルを選択し、**[監視]** > **[設定ごとの状態]** を選択します。
3. この表には、すべての設定と、各設定の状態が表示されます。 **[エラー]** 列または **[競合]** 列を選択して、エラーの原因となっている設定を確認します。

### <a name="mdm-diagnostic-information"></a>MDM の診断情報

これで問題のある設定がわかりました。 次の手順は、この設定がエラーまたは競合を引き起こしている理由を見つけることです。 

Windows 10 デバイスには、組み込みの MDM 診断情報レポートがあります。 このレポートには、既定値、現在の値、ポリシーの一覧、デバイスとユーザーのどちらに展開されているかなどが表示されます。 このレポートを使用すると、設定によって競合やエラーが発生している理由を特定できます。

1. デバイス上で、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の順に移動します。
2. アカウントを選択し、**[情報]** > **[Advanced Diagnostic Report]\(高度な診断レポート\)** > **[レポートの作成]** の順に選択します。
3. **[エクスポート]** を選択し、生成されたファイルを開きます。
4. レポートでは、レポートのさまざまなセクションに含まれるエラーまたは競合の設定を探します。

  たとえば、**[Enrolled configuration sources and target resources]\(登録済みの構成ソースとターゲット リソース\)** セクションや **[Unmanaged policies]\(管理されていないポリシー\)** セクションを調べます。 エラーや競合の原因となっている理由を把握できます。

[[Diagnose MDM failures in Windows 10]\(Windows 10 の MDM エラーを診断する\)](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) を使用すると、この組み込みレポートに関する詳細情報が表示されます。

> [!TIP]
> - 一部の設定には GUID の一覧も表示されます。 任意の設定値について、ローカル レジストリ (regedit) でこの GUID を検索できます。
> - イベント ビューアー ログには、問題のある設定に関するエラー情報もいくつか含まれている場合があります (**[イベント ビューアー]** > **[アプリケーションとサービス ログ]** > **[Microsoft]** > **[Windows]** > **[DeviceManagement-Enterprise-Diagnostics-Provider]** > **[Admin]**)。

## <a name="next-steps"></a>次の手順

[デバイス プロファイルを監視](device-profile-monitor.md)し、[いくつかの一般的な問題と解決策を確認](device-profile-troubleshoot.md)します。
