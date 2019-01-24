---
title: Android エンタープライズ アカウントに Intune アカウントを接続する
titlesuffix: Microsoft Intune
description: Android エンタープライズ アカウントに Intune アカウントを接続する方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 698bc4e7e2d2cf8ece1b1c17b091a91c76a7d178
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386889"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Android エンタープライズ アカウントに Intune アカウントを接続する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[Android 仕事用プロファイル デバイス](android-work-profile-enroll.md)、[Android フル マネージド デバイス](android-fully-managed-enroll.md)、[Android 専用デバイス](android-kiosk-enroll.md)をサポートするには、Intune テナント アカウントを Android エンタープライズ アカウントに接続する必要があります。  

> [!NOTE]
> Google ドメインと Microsoft ドメインの間の相互作用のため、この手順では、ブラウザー設定の調整が必要な場合があります。  "portal.azure.com" と "play.google.com" がブラウザーの同じセキュリティ ゾーンにあることを確認してください。

1. **Microsoft Intune** を[モバイル デバイス管理機関](mdm-authority-set.md)に設定し、モバイル デバイス管理の準備をします (この作業をまだ行っていない場合)。
2. [Azure Portal の Intune](https://aka.ms/intuneportal) にサインインして、**[デバイスの登録]** > **[Android の登録]** > **[managed Google Play]** を選択します。  カスタム Intune 管理者ロールを使用している場合、このアクセスには組織の読み取りと更新のアクセス許可が必要です。
   
   ![Android エンタープライズの登録画面](./media/android-work-bind.png)

3. **[同意する]** を選択して、Microsoft が[ユーザーとデバイスの情報を Google に送信](data-intune-sends-to-google.md)できるようにします。 
   
4. **[Launch Google to connect now]\(Google を起動して今すぐ接続する\)** を選択して、managed Google Play の Web サイトを開きます。 ブラウザーの新しいタブで Web サイトが開きます。
  
5. Google のサインイン ページで、このテナントのすべての Android エンタープライズ管理タスクに関連付ける Google アカウントを入力します。 これは、会社の IT 管理者が Google Play コンソールでアプリを管理および公開するときに共有する Google アカウントです。 既存の Google アカウントを使用するか、新しい Google アカウントを作成できます。 選択したアカウントを G-Suite ドメインと関連付けることはできません。
    
    > [!Note]
    > Microsoft Edge ブラウザーを使用している場合は、右上隅の **[サインイン]** をクリックして、Google アカウントにサインインします。

6. **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、**Microsoft Intune** と表示されます。

7. Android の使用条件に同意し、**[確認]** を選択します。 要求が処理されます。

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Android エンタープライズ管理者アカウントの接続を解除する

Android エンタープライズの登録と管理を無効にすることもできます。 無効にするには、登録したすべての Android 仕事用プロファイル デバイスをまずインベントリから削除する必要があります。 次に Intune 管理コンソールで **[切断]** を選択します。登録済みのすべての Android 仕事用プロファイル デバイスとキオスク デバイスが登録から削除されます。 また、Android エンタープライズ アカウントと Intune 間のリレーションシップも削除されます。

1. Intune 管理者として [Azure Portal](https://portal.azure.com) で **[すべてのサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
2. **[デバイスの登録]** > **[Android の登録]** > **[managed Google Play]** > **[切断]** の順に選択します。
3. **[はい]** を選択して、Intune からすべての Android エンタープライズ デバイスを切断し、登録を解除します。

## <a name="next-steps"></a>次の手順

Android エンタープライズ アカウントに接続したら、[Android 仕事用プロファイル デバイスの設定](android-work-profile-enroll.md)と、[Android キオスク デバイスの設定](android-kiosk-enroll.md)ができます。
