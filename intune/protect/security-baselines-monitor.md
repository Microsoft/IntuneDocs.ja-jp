---
title: Microsoft Intune でセキュリティのベースラインの成功または失敗を確認する - Azure | Microsoft Docs
description: Microsoft Intune MDM でセキュリティのベースラインをユーザーとデバイスに展開するときに、エラー、競合、成功の状態を確認します。 クライアント ログを使用してトラブルシューティングする方法と Intune のレポート機能について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b7f14e939e7241cd34c01d73e9af822dea7acdc
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410093"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Microsoft Intune でセキュリティのベースラインとプロファイルを監視する

Intune からは、セキュリティ ベースラインを監視するためのオプションがいくつか与えられます。 ユーザーとデバイスに適用されるセキュリティのベースライン プロファイルを監視できます。 また、実際のベースラインと、推奨値と一致する (または一致しない) デバイスを監視することもできます。

この記事では、両方の監視オプションについて手順を追って説明します。

Microsoft Intune のセキュリティのベースライン機能の詳細については、[Intune のセキュリティのベースライン](../security-baselines.md)に関するページを参照してください。

## <a name="monitor-the-baseline-and-your-devices"></a>ベースラインとデバイスを監視する

ベースラインを監視すると、Microsoft の推奨事項に基づいて、デバイスのセキュリティ状態に関する分析情報が得られます。 このような分析情報は、Intune コンソールのセキュリティ ベースラインの [概要] ウィンドウから表示できます。  最初にベースラインを割り当ててからデータが表示されるまで最大 24 時間かかります。 その後の変更は、表示されるまで最大 6 時間かかります。

ベースラインとデバイスの監視データを表示するには、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。 次に、 **[エンドポイント セキュリティ]**  >  **[セキュリティ ベースライン]** の順に選択して、ベースラインを選択し、 **[概要]** ウィンドウを表示します。

**[概要]** ウィンドウには、状態を監視する方法が 2 つあります。

- **デバイス** ビュー - ベースラインの状態カテゴリ別デバイス数の概要。
- **カテゴリ別**ビュー - ベースラインに各カテゴリを表示し、ベースライン カテゴリ別に、状態グループごとのデバイスの割合を表示するビュー。

各デバイスは次のいずれかの状態によって表されます。これらの状態は、*デバイス* ビューと*カテゴリ別*ビューの両方で使用されます。

- **Matches baseline (ベースラインと一致)** - ベースラインのすべての設定は推奨設定と一致しています。
- **Does not match baseline (ベースラインと一致しない)** - ベースラインの少なくとも 1 つの設定が推奨設定と一致しません。
- **正しく構成されていません** - 少なくとも 1 つの設定が正しく構成されていません。 この状態は、設定が競合、エラー、または保留中の状態にあることを意味します。
- **適用なし** - 少なくとも 1 つの設定が適用可能ではなく、適用されていません。

### <a name="device-view"></a>デバイス ビュー

[概要] ウィンドウには、ベースラインの特定の状態になっているデバイスの数がグラフによる概要で表示されます。下は「**Security baseline posture for assigned Windows 10 devices**」のまとめです。

![デバイスの状態を確認する](./media/security-baselines-monitor/overview.png)

1 台のデバイスにベースラインのさまざまなカテゴリからさまざまな状態が与えられるとき、そのデバイスは 1 つの状態で表されます。 デバイスを表す状態は次の優先順位で取得されます。**正しく構成されていません**、**ベースラインと一致しない**、**適用なし**、**ベースラインと一致**。

たとえば、あるデバイスに "*正しく構成されていません*" として分類される設定が与えられているとき、他にも "*ベースラインと一致しない*" として分類される設定が与えられている場合、そのデバイスは "*正しく構成されていません*" として分類されます。

グラフをクリックすると詳細が表示されます。さまざまな状態が与えられたデバイスが一覧表示されます。 その一覧から個々のデバイスを選択すると、個々のデバイスの詳細を表示できます。 次に例を示します。

- **[デバイスの構成]** を選択し、状態がエラーになっているプロファイルを選択します。

  ![プロファイルの状態を表示する](./media/security-baselines-monitor/device-configuration-profile-list.png)

- エラーのプロファイルを選択します。 プロファイル内のすべての設定の一覧と、その状態が表示されます。 ここで、スクロールし、エラーの原因となっている設定を探します。

  ![エラーの原因となっている設定を確認する](./media/security-baselines-monitor/profile-with-error-status.png)

このレポートを使用して、問題の原因となっているプロファイル内の設定を確認します。 また、デバイスに展開されているポリシーとプロファイルの詳細情報も得られます。

> [!NOTE]
> ベースラインでプロパティが **[未構成]** に設定されている場合、その設定は無視され、制限は適用されません。 このプロパティはどのレポートにも表示されません。

### <a name="per-category-view"></a>カテゴリ別ビュー

[概要] ウィンドウには、ベースラインのカテゴリ別グラフが表示されます。下は「**Security baseline posture by category**」のまとめです  このビューには、ベースラインからの各カテゴリが表示され、各カテゴリの特定の状態分類に属するデバイスの割合が表示されます。

![状態のカテゴリ別ビュー](./media/security-baselines-monitor/monitor-baseline-per-category.png)

**[ベースラインと一致]** の状態は、カテゴリに対して 100% のデバイスがその状態を報告するまで表示されません。

カテゴリ別ビューは列ごとに並べ替えることができます。その際、列の一番上にある上下の矢印アイコンを選択します。

## <a name="monitor-the-profile"></a>プロファイルを監視する

プロファイルを監視すると、デバイスの展開状態に関する分析情報が得られますが、ベースラインの推奨事項に基づくセキュリティ状態に関する分析情報は得られません。

1. Intune で **[Security Baselines]\(セキュリティのベースライン\)** を選択し、ベースライン、 **[Profiles created]\(作成したプロファイル\)** の順に選択します。

2. プロファイルを選択します。 **[概要]** の画像には、このプロファイルが割り当てられているデバイスとユーザーの数が表示されます。

   ![セキュリティのベースライン プロファイルが割り当てられているデバイスとユーザーの数を確認する](./media/security-baselines-monitor/existing-profile-overview.png)

3. **[管理]**  >  **[プロパティ]** に、ベースラインのすべての設定の一覧が表示されます。 これらの設定のすべてを変更することもできます。

   ![セキュリティのベースライン プロファイルの設定を確認および更新する](./media/security-baselines-monitor/manage-settings.png)

4. **[監視]** では、個々のデバイスに関するプロファイルの展開状態、各ユーザーの状態、およびベースラインの各設定の状態を確認できます。

   ![セキュリティのベースライン プロファイルのさまざまなモニター オプションを確認する](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>設定ごとの状態を使用したトラブルシューティング

セキュリティのベースラインを展開しましたが、展開状態にエラーが表示されます。 次の手順では、エラーのトラブルシューティングに関するガイダンスをいくつか紹介します。

1. Intune で **[Security Baselines]\(セキュリティのベースライン\)** を選択し、ベースライン、 **[Profiles created]\(作成したプロファイル\)** の順に選択します。

2. プロファイルを選択し、 **[監視]**  >  **[設定ごとの状態]** を選択します。

3. この表には、すべての設定と、各設定の状態が表示されます。 **[エラー]** 列または **[競合]** 列を選択して、エラーの原因となっている設定を確認します。

### <a name="mdm-diagnostic-information"></a>MDM の診断情報

これで問題のある設定がわかりました。 次の手順は、この設定がエラーまたは競合を引き起こしている理由を見つけることです。

Windows 10 デバイスには、組み込みの MDM 診断情報レポートがあります。 このレポートには、既定値、現在の値、ポリシーの一覧、デバイスとユーザーのどちらに展開されているかなどが表示されます。 このレポートを使用すると、設定によって競合やエラーが発生している理由を特定できます。

1. デバイス上で、 **[設定]**  >  **[アカウント]**  >  **[職場または学校にアクセスする]** の順に移動します。

2. アカウントを選択し、 **[情報]**  >  **[Advanced Diagnostic Report]\(高度な診断レポート\)**  >  **[レポートの作成]** の順に選択します。

3. **[エクスポート]** を選択し、生成されたファイルを開きます。

4. レポートでは、レポートのさまざまなセクションに含まれるエラーまたは競合の設定を探します。

  たとえば、 **[Enrolled configuration sources and target resources]\(登録済みの構成ソースとターゲット リソース\)** セクションや **[Unmanaged policies]\(管理されていないポリシー\)** セクションを調べます。 エラーや競合の原因となっている理由を把握できます。

[[Diagnose MDM failures in Windows 10]\(Windows 10 の MDM エラーを診断する\)](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) を使用すると、この組み込みレポートに関する詳細情報が表示されます。

> [!TIP]
> - 一部の設定には GUID の一覧も表示されます。 任意の設定値について、ローカル レジストリ (regedit) でこの GUID を検索できます。
> - イベント ビューアー ログには、問題のある設定に関するエラー情報もいくつか含まれている場合があります ( **[イベント ビューアー]**  >  **[アプリケーションとサービス ログ]**  >  **[Microsoft]**  >  **[Windows]**  >  **[DeviceManagement-Enterprise-Diagnostics-Provider]**  >  **[Admin]** )。

## <a name="next-steps"></a>次の手順

[デバイス プロファイルを監視](../configuration/device-profile-monitor.md)し、[いくつかの一般的な問題と解決策を確認](../configuration/device-profile-troubleshoot.md)します。
