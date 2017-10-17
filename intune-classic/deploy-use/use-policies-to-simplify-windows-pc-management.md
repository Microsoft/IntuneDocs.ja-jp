---
title: "ポリシーを使用して Windows PC 管理を簡略化する"
description: "Windows PC 管理ポリシーと Microsoft Intune Center の設定について説明します。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0afda7e-f4c3-4bcd-b4bf-4304103cf73e
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9d67bf344be7a20853e21cf580939f1156d1a723
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="use-policies-to-simplify-windows-pc-management"></a>ポリシーを使用して Windows PC 管理を簡略化する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune ソフトウェア クライアントを実行することにより Windows デスクトップを PC として管理するには、Intune 管理コンソールの **[コンピューターの管理]** ポリシーにあるポリシーだけを使用できます。 管理コンソールに表示される他のすべてのポリシーは、モバイル デバイス専用です。 **[コンピューターの管理]** のポリシーを使用して、Microsoft Intune Center で設定を構成し、PC の更新を制御し、PC の Windows ファイアウォールを構成できます。

![Windows PC のポリシー テンプレート](../media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>Microsoft Intune Center の管理
ユーザーは、Intune ソフトウェア クライアントを **Microsoft Intune Center** として確認します。 Microsoft Intune Center を使用してユーザーは次の操作を実行できます。

-   ポータル サイトからアプリケーションを取得する。

-   更新プログラムを確認する。

-   Microsoft Intune Endpoint Protection を管理する。

-  リモート アシスタンスを要求する。

Microsoft Intune Center は、管理されているすべてコンピューターにインストールされます。 Intune ポリシーで次の設定を構成でき、各設定は Microsoft Intune Center でユーザーに表示されます。

|ポリシー設定|説明|
|------------------|--------------------|
|**名前**|コンピューターを管理する管理者の名前。<br />最大文字数:40 字|
|**電話番号**|コンピューターを管理する管理者の電話番号。<br />最大文字数:20 字|
|**電子メール アドレス**|コンピューターを管理する管理者の電子メール アドレス。<br />最大文字数:40 字|
|**Web サイト名**|ユーザー向けのサポート Web サイトの名前。<br />最大文字数:40 字|
|**Web サイトの URL**|サポート Web サイトの URL。<br />最大文字数:150 字|
|**メモ**|ユーザーに表示されるメモ。<br />最大文字数:120 字|

Windows PC で構成できるポリシーと設定の詳細については、以下のリソースを参照してください。

- [Microsoft Intune でソフトウェア更新プログラムを使用して Windows PC を最新の状態に保つ](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) - 管理対象コンピューターで Microsoft やサード パーティのソフトウェア更新プログラムを確認し、ダウンロードするように指示するポリシーについて説明しています。 この更新プログラムには、OS のアップグレード (Windows 7 から Windows 10 へのアップグレードまたは Windows 10 のあるバージョンからそれ以降のバージョンへのアップグレード) は含まれません。

- [Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) - スキャンのスケジュール、マルウェアが検出されたときに実行するアクションなどの設定について説明しています。

- [Microsoft Intune で Windows ファイアウォール ポリシーを使用して Windows PC を保護する](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) - 管理対象のコンピューターで Windows ファイアウォール設定の管理を簡易化するポリシーについて説明しています。


### <a name="see-also"></a>関連項目

[Intune ソフトウェア クライアントを使用した一般的な Windows PC 管理タスク](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
