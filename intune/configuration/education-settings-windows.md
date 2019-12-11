---
title: Microsoft Intune での Windows 10 の教育設定 - Azure | Microsoft Docs
description: Windows 10 デバイス用のすべての教育設定を一覧で示します。 テスト アプリでデバイス構成プロファイルにこれらの設定を使用する、ユーザーまたは学生のサインイン方法を選択する、テスト中に画面を監視するなどの機能が Intune にはあります。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d89f512c06dcfbf6f6ddaba5e17ac9ca6f0becf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506797"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Windows 10 デバイス上で Intune を使用してテスト アプリを構成する

Take a Test app を使用すると、教室の Windows 10 デバイスでオンラインテストを安全に管理できます。 テストアプリをセットアップするには、Intune でデバイス構成プロファイルを作成し、セキュリティで保護された評価の設定を構成する必要があります。 この記事では、テストアプリを作成するために必要な設定について説明します。 

プロファイルを構成したら、それを割り当てて学生にデプロイします。 

[Intune のテスト アプリ](education-settings-configure.md)は、この機能に関する詳細情報を提供しています。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](education-settings-configure.md#create-a-device-profile)。

## <a name="take-a-test-settings"></a>テストの設定
デバイス構成プロファイルを作成したら、 **[プロファイルの種類]** にアクセスし、 **[セキュリティで保護された評価 (教育)]** を選択します。 次のようなテストアプリの設定を確認できます。 


- **[アカウントの種類]** : ユーザーがテストにサインインする方法を選択します。 次のようなオプションがあります。
  - Azure AD アカウント
  - ドメイン アカウント
  - ローカル アカウント
  - ローカルゲストアカウント: Windows 10 バージョン1903以降を実行しているデバイスでのみ使用できます。    
- **アカウント ユーザー名**: テスト アプリで使用するアカウントのユーザー名を入力します。 次の形式でアカウントを入力できます。
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **アカウント名**: ローカルの guest アカウントの種類を設定するには、[テストアプリの作成] で使用するアカウントの名前を入力します。 アカウント名は、サインイン画面にタイルとして表示されます。 学生は、タイルをクリックしてテストを開始します。  
- **評価 URL**: ユーザーに受けさせるテストの URL を入力します。 URL の取得の詳細については、[テストに関するドキュメント](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)を参照してください。
- **プリンター接続**: **[必須]** を選択すると、プリンターに接続されているデバイスからのテストアプリへのアクセスのみが許可されます。 また、この設定により、アプリの [印刷] ボタンを受け手で使用できるようになります。 **未構成の場合**、学生は、プリンターに接続されていないデバイスからアプリにアクセスできます。  
- **画面の監視**: ユーザーがテストを受けている間、画面の動作を監視するには **[許可]** を選択します。 **[未構成]** を選択すると、テスト中に画面を監視できなくなります。
- **テキストの候補**: 受験者がテキストの候補を表示できるようにするには、 **[許可]** を選択します。 **[未構成]** を選択すると、ユーザーがテストを受けている間、テキストの候補がブロックされます。

## <a name="next-steps"></a>次の手順

必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。
