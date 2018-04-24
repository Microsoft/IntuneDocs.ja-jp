---
title: コンプライアンス ポリシーを展開して監視する
description: このトピックのステップ バイ ステップの指示は、デバイスのコンプライアンス ポリシーを展開して監視するために使用します。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7e3f67411a4eff357102756e785f4cbbff120d23
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Microsoft Intune でデバイスのコンプライアンス ポリシーを展開して監視する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>コンプライアンス ポリシーの展開
[こちらの手順で作成した](create-a-device-compliance-policy-in-microsoft-intune.md)コンプライアンス ポリシーを、組織内のユーザーの 1 つ以上のグループに展開します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。

1.  **[ポリシー]** ワークスペースで、展開するポリシーを選び、**[展開の管理]** を選びます。
![上部に [展開の管理] メニュー オプションが表示されているコンプライアンス ポリシー ページのスクリーンショット](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  **[展開の管理]** ダイアログ ボックスで、ポリシーを展開するグループを 1 つ以上選択し、**[追加]** > **[OK]** の順に選択します。
![[展開の管理] ダイアログ ボックスのスクリーン ショット](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) 既に作成され、Intune と同期している Active Directory グループを使用するか、これらのグループを Intune コンソールで手動で作成します。 ポリシーを展開する方法の詳細については、「[構成ポリシーを展開する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」を参照してください。

**[ポリシー]** ワークスペースの **[概要]** ページに表示されるステータスの概要とアラートを使用すると、注意が必要なポリシーの問題を識別できます。 ステータスの概要は **[ダッシュボード]** ワークスペースにも表示されます。

> [!IMPORTANT]
> コンプライアンス ポリシーを展開していない状態で、Exchange 条件付きアクセス ポリシーを有効にすると、すべての対象デバイスからアクセスできるようになります。

## <a name="monitor-the-compliance-policy"></a>コンプライアンス ポリシーの監視

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>コンプライアンス ポリシーに準拠していないデバイスを表示するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[グループ]** > **[すべてのデバイス]** の順に選択します。

2.  デバイスの一覧内のデバイスの名前をダブルクリックします。

3.  **[ポリシー]** タブを選び、そのデバイスのポリシーの一覧を表示します。

4.  **[フィルター]** ドロップダウン リストから **[コンプライアンス ポリシーに準拠しない]** を選択します。
![フィルター リストのオプション リストを示すスクリーンショット](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>正常性構成証明書レポートを表示するには

1.  [Microsoft Intune の管理コンソール](https://manage.microsoft.com)で、**[レポート]** を選びます。

2.  **[正常性構成証明書レポート - レポートの新規作成]** ページで、Intune によって収集されたすべての Windows 10 正常性構成証明書データを含むレポートを表示できます。 フィルターを使用して、データのサブセットを含むレポートを作成することもできます。 フィルターは、デバイスの種類、オペレーティング システム、またはデータ ポイントのサブセットのみに基づいて設定できます。

## <a name="how-intune-resolves-policy-conflicts"></a>Intune のポリシー競合の解決方法
複数の Intune ポリシーを 1 つのデバイスに適用すると、ポリシーの競合が発生する可能性があります。 ポリシーの設定が重複した場合、Intune では次のルールを使用して競合を解決します。

-   Intune の構成ポリシーと準拠ポリシーの設定が競合している場合は、構成ポリシーの設定よりも準拠ポリシーの設定が優先されます。 構成ポリシーの設定の方が安全性が高い場合でも同様です。

-   複数の準拠ポリシーを展開した場合、Intune ではその中で最も安全なポリシーが使用されます。

## <a name="next-steps"></a>次の手順
条件付きアクセス ポリシーと共にコンプライアンス ポリシーを使用して、組織内のサービスへのアクセスを制御する方法については、「[電子メールと O365 サービスへのアクセスを制限する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)」を参照してください。


### <a name="see-also"></a>関連項目
[Intune でのデバイス コンプライアンス ポリシーの概要](introduction-to-device-compliance-policies-in-microsoft-intune.md)
