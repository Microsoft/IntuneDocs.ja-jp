---
title: Microsoft Intune でデバイスを表示する - Azure | Microsoft Docs
description: デバイスの詳細を表示します。たとえば、オペレーティング システム、記憶域、製造元、モデルなどです。 Azure で Microsoft Intune を使用して、インストールされているアプリのリストを取得したり、コンプライアンス ポリシーを確認したり、TeamViewer をセットアップしたりします。 管理するデバイスのインベントリを表示する作業と似ています。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eaaf3e9807a8eab66c24f4d1bb3c3c5ea9f4cfe0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="see-device-details-in-intune"></a>Intune でデバイスの詳細を確認する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**[デバイス]** 機能を使用すると、ハードウェアやインストールされているアプリなど、管理するデバイスの詳細を表示できます。 

この記事では、Azure Portal ですべてのデバイスと、それらのプロパティを表示する方法を示します。

## <a name="view-your-device-details"></a>デバイスの詳細を表示する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]** を選択します。 [デバイス] には、いくつかのオプションがあります。

   - **[概要]**: 登録したデバイスと、各デバイスで実行されているオペレーティング システムについての情報を取得します。
   - **[管理]**: 管理対象のすべてのデバイスのリストを表示するには、**[すべてのデバイス]** または **[Azure AD デバイス]** を選択します。
    デバイスの一覧でいずれかを選択します。 この手順により、<*デバイス名*>  の **[概要]** が開きます。ここで次のいずれかを選択できます。
     - **[概要]**: デバイス名、所有者、デバイスが Bring-Your-Own-Device (BYOD) であるかどうか、チェックインされた日時などの詳細情報が表示されます。
     - **[ハードウェア]**: 記憶域の空き容量、モデル、製造元など、デバイスについてのさらに詳細な情報が表示されます。
     - **[検出されたアプリ]**: Intune でデバイスにインストールされていると判断されたすべてのアプリのリストが表示されます。
     - **[デバイスのポリシー準拠]**: デバイスに割り当てられているすべてのコンプライアンス ポリシーの状態が表示されます。
     - **[デバイス構成]**: デバイスに割り当てられているすべてのデバイス構成ポリシーのコンプライアンス対応状態が表示されます。
   - **[監視]**: **[デバイス アクション]** を選択すると、管理対象のデバイスで実行されたアクションのリストと、その現在の状態が表示されます。 **[監査ログ]** には、さまざまなタスクの状態が表示されます。
   - **[セットアップ]** > **[TeamViewer Connector]**: TeamViewer ソフトウェアを使用して、デバイスのリモート管理を構成します。 詳細については、「[Intune 管理対象の Android デバイスにリモート アシスタンスを提供する](device-profile-android-teamviewer.md)」を参照してください。

Intune は会社所有のデバイスでのみアプリの一覧を収集します。 個人用のデバイス上のアプリは確認されません。 Windows 10 の PC の場合、会社所有のデバイスの最新のアプリのみが収集されます。 Intune では、デバイス上の Win32 アプリに関する情報を収集しません。 デバイスで使用される通信事業者によっては、一部のアプリが収集されない場合があります。

## <a name="next-steps"></a>次の手順
Intune で[デバイスを管理](device-management.md)するために他に行えることを確認します。
