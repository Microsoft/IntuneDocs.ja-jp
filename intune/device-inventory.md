---
title: Microsoft Intune - Azure でデバイスの詳細を表示する | Microsoft Docs
description: デバイスの詳細を表示します。たとえば、オペレーティング システム、記憶域、製造元、モデルなどです。 Azure で Microsoft Intune を使用して、インストールされているアプリのリストを取得したり、コンプライアンス ポリシーを確認したり、TeamViewer をセットアップしたりします。 管理するデバイスのインベントリを表示する作業と似ています。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a40b855d1dbaeece1dc91648866285c0a01fb338
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="see-device-details-in-intune"></a>Intune でデバイスの詳細を確認する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**[デバイス]** 機能を使用すると、ハードウェアやインストールされているアプリなど、管理するデバイスの詳細を表示できます。

この記事では、Azure Portal ですべてのデバイスと、それらのプロパティを表示する方法を示します。

## <a name="view-the-device-details"></a>デバイスの詳細を表示する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]** > **[すべてのデバイス]** を選択します。次に、一覧表示されているデバイスのいずれかを選択して、その詳細を開きます。

   - **[概要]** にはデバイス名が表示され、デバイスが BYOD (Bring-Your-Own-Device ) であるかどうかや、いつチェックインされたかなど、デバイスの主なプロパティがいくつか一覧表示されます。 **[詳細]** を選択して、次の操作も行います。
     - 会社データの削除
     - デバイスの削除
     - デバイスのリモート ロック
     - 消去
     - リモート アシスタンス セッションの開始
   - **[プロパティ]** を使用して、[作成するデバイス カテゴリ](device-group-mapping.md)を割り当て、デバイスの所有権を個人のデバイス、または会社のデバイスに変更します。
   - **[ハードウェア]** にはデバイスに関する多くの詳細が含まれます。たとえば、デバイス ID、オペレーティング システムとバージョン、記憶域スペース、モデルと製造元、条件付きアクセスの設定などの詳細です。
   - **[検出されたアプリ]** には、Intune でデバイスにインストールされていると判断されたすべてのアプリと、アプリのバージョンが一覧表示されます。 アプリの一覧を .csv ファイルに**エクスポートする**こともできます。
   - **[デバイスのポリシー準拠]** には、割り当てられているコンプライアンス ポリシーがすべて一覧表示され、デバイスがポリシーに準拠しているかどうかが示されます。
   - **[デバイス構成]** には、デバイスに割り当てられているデバイス構成ポリシーがすべて表示され、ポリシーが成功したか失敗したかが示されます。

Intune は会社所有のデバイスでのみアプリの一覧を収集します。 個人用のデバイス上のアプリは確認されません。 Windows 10 の PC の場合、会社所有のデバイスの最新のアプリのみが収集されます。 Intune では、デバイス上の Win32 アプリに関する情報を収集しません。 デバイスで使用される通信事業者によっては、一部のアプリが収集されない場合があります。

## <a name="next-steps"></a>次の手順
Intune で[デバイスを管理](device-management.md)するために他に行えることを確認します。