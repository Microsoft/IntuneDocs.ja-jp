---
title: managed Google Play アカウントに Intune アカウントを接続する
titleSuffix: Microsoft Intune
description: managed Google Play アカウントに Intune アカウントを接続する方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2c6463ddce7d04168e1929414faf441ae415837
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563842"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>managed Google Play アカウントに Intune アカウントを接続する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[Android Enterprise 仕事用プロファイル デバイス](android-work-profile-enroll.md)、[Android Enterprise フル マネージド デバイス](android-fully-managed-enroll.md)、[Android 専用デバイス](android-kiosk-enroll.md)をサポートするには、Intune テナント アカウントを managed Google Play アカウントに接続する必要があります。  

Android Enterprise 管理をより簡単に構成して使用できるように、Google Play に接続する際に、Intune では 4 つの一般的な Android Enterprise 関連アプリが Intune 管理コンソールに自動的に追加されます。 4 つの Android Enterprise アプリは次のとおりです。

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise フル マネージド シナリオで使用されます。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 2 要素認証を使用している場合のアカウントへのサインインを支援します。
- **[Intune ポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - アプリ保護ポリシー (APP) と Android Enterprise 仕事用プロファイルのシナリオで使用されます。
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Android Enterprise 専用またはキオスクのシナリオで使用されます。

> [!NOTE]
> Google ドメインと Microsoft ドメインの間の相互作用のため、この手順では、ブラウザー設定の調整が必要な場合があります。  "portal.azure.com" と "play.google.com" がブラウザーの同じセキュリティ ゾーンにあることを確認してください。

1. **Microsoft Intune** を[モバイル デバイス管理機関](../fundamentals/mdm-authority-set.md)に設定し、モバイル デバイス管理の準備をします (この作業をまだ行っていない場合)。
2. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、 **[デバイス]**  >  **[Android]**  >  **[Android の登録]**  >  **[マネージド Google Play]** の順に選択します。  カスタム Intune 管理者ロールを使用している場合、このアクセスには組織の読み取りと更新のアクセス許可が必要です。
   
   ![Android エンタープライズの登録画面](./media/connect-intune-android-enterprise/android-work-bind.png)

3. **[同意する]** を選択して、Microsoft が[ユーザーとデバイスの情報を Google に送信](../protect/data-intune-sends-to-google.md)できるようにします。 
   
4. **[Launch Google to connect now]\(Google を起動して今すぐ接続する\)** を選択して、managed Google Play の Web サイトを開きます。 ブラウザーの新しいタブで Web サイトが開きます。
  
5. Google のサインイン ページで、このテナントのすべての Android Enterprise 管理タスクに関連付ける Google アカウントを入力します。 これは、会社の IT 管理者が Google Play コンソールでアプリを管理および公開するときに共有する Google アカウントです。 既存の Google アカウントを使用するか、新しい Google アカウントを作成できます。 選択したアカウントを G-Suite ドメインと関連付けることはできません。
    
    > [!Note]
    > Microsoft Edge ブラウザーを使用している場合は、右上隅の **[サインイン]** をクリックして、Google アカウントにサインインします。

6. **[組織名]** に会社名を入力します。 **エンタープライズ モビリティ管理 (EMM) プロバイダー**の場合、**Microsoft Intune** と表示されます。

7. Android の使用条件に同意し、 **[確認]** を選択します。 要求が処理されます。

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Android Enterprise 管理者アカウントの接続を解除する

Android Enterprise の登録と管理を無効にすることができます。 これを行うには、まず、登録済みの Android Enterprise デバイス (仕事用プロファイル デバイス、専用デバイス、フル マネージド デバイスが含まれます) をインベントリから削除する必要があります。 次に、Intune 管理コンソールで **[切断]** を選択します。登録済みのすべての Android Enterprise 仕事用プロファイル デバイス、専用デバイス、およびフル マネージド デバイスが登録から削除されます。 また、managed Google Play アカウントと Intune 間のリレーションシップも削除されます。

1. Intune 管理者として [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]**  >  **[Android]**  >  **[Android の登録]**  >  **[マネージド Google Play]**  >  **[切断]** の順に選択します。
3. **[はい]** を選択して、Intune からすべての Android エンタープライズ デバイスを切断し、登録を解除します。

## <a name="next-steps"></a>次の手順

マネージド Google Play アカウントに接続したら、[Android Enterprise 仕事用プロファイル デバイスの設定](android-work-profile-enroll.md)、[Android Enterprise 専用デバイスの設定](android-kiosk-enroll.md)、および [Android Enterprise フル マネージド デバイスの設定](android-kiosk-enroll.md)を実行できます。
