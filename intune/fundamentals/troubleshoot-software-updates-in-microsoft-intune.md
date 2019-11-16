---
title: Microsoft Intune のソフトウェア更新プログラムのトラブルシューティング - Azure | Microsoft Docs
description: Microsoft Intune でのソフトウェア更新に関する問題を解決します。
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7da927754971fb66a5d8442d0cdf18e0ebfbcd4a
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059077"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Microsoft Intune でのソフトウェア更新のトラブルシューティング

Microsoft Intune でのソフトウェア更新に関する問題を解決するために役立ちます。 エラー コードと説明の一覧を確認するには、[Microsoft Intune のソフトウェア更新エージェントのエラー コード](../protect/software-update-agent-error-codes.md)に関する記事を参照してください。

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>置き換えられる更新プログラムが多数ある Windows 7 デバイスから Intune への報告が停止する

Microsoft Intune クライアントでは、次下の現象が 1 つ以上発生することがあります。

- デバイスから Intune への報告が突然停止する。  
- デバイスの CPU 使用率が高くなる。
- Intune 経由でアプリケーションをインストールすると、インストールが遅くなる。
- Microsoft Intune Center に "`An error occurred while updating your computer. Error found: Code 0x800705b4`" というエラーが表示される。
- [Intune 管理コンソール] > [グループ] > [すべてのデバイス] > [状態] に "`One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`" と表示される。

この問題は、置き換えられた更新プログラム (更新プログラムが別の更新プログラムに置き換えられる) が長期間拒否されていない場合に発生することがあります。 Windows がアプリケーションのインストールなどの特定の処理を行う際、置き換えられた更新プログラムと置き換え後の更新プログラムを正しく関連付けるために、置き換えられた更新プログラムを順番にすべてチェックします。 置き換えられた更新プログラムが多くなりすぎると、このチェック処理に負荷と時間がかかるため、CPU 使用率が高くなる場合があります。 Windows 7 では置き換えられた更新プログラムが大量に提供されているため、この問題は主に Windows 7 デバイスに影響します。 新しいオペレーティング システムには置き換えられた更新プログラムがそれほど多くないため、この問題の影響はあまりない可能性があります。

**解決方法**

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[ソフトウェア更新プログラム]** を選択します。
3. 影響を受けているクライアントにインストールされている Windows 7 またはアプリケーション (Microsoft Office など) に適用される置き換えられた更新プログラムをすべて拒否します。
4. 影響を受けているクライアントを再起動します。

Windows 7 を実行している場合は、[3050265 Windows Update Client for Windows 7: June 2015](https://support.microsoft.com/kb/3050265) の更新プログラムがインストールされていることを確認します。

## <a name="next-steps"></a>次の手順

[Microsoft からサポート](get-support.md)を受けるか、[コミュニティ フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)を使用します。