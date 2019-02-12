---
title: Microsoft Intune での Windows 10 の教育設定 - Azure | Microsoft Docs
description: Windows 10 デバイス用のすべての教育設定を一覧で示します。 テスト アプリでデバイス構成プロファイルにこれらの設定を使用する、ユーザーまたは学生のサインイン方法を選択する、テスト中に画面を監視するなどの機能が Intune にはあります。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae26d35a50ffd2b5b40f262ddebeab8d53d87223
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846691"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Windows 10 デバイス上で Intune を使用してテスト アプリを構成する

この記事では、Windows 10 以降を実行しているデバイス上で構成できる Microsoft Intune 教育のテスト アプリの設定をすべて紹介します。 このアプリを使用すると、学生はデバイスにサインインしてテストを受けることができます。

これらの設定は、デバイスの構成プロファイルに追加した後、Microsoft Intune を使ってデバイスに割り当てたり展開したりします。

[Intune のテスト アプリ](education-settings-configure.md)は、この機能に関する詳細情報を提供しています。

## <a name="before-you-begin"></a>始める前に

[デバイス構成プロファイルを作成します](education-settings-configure.md#create-a-device-profile)。

## <a name="take-a-test-settings"></a>テストの設定

- **アカウントの種類**:ユーザーがテストにサインインする方法を選択します。 次のようなオプションがあります。
  - Azure AD アカウント
  - ドメイン アカウント
  - ローカル アカウント
- **アカウント ユーザー名**:テスト アプリで使用したアカウントのユーザー名を入力します。 次の形式でアカウントを入力できます。
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **評価 URL**:ユーザーに受けさせるテストの URL を入力します。 URL の取得の詳細については、[テストに関するドキュメント](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)を参照してください。
- **画面の監視**:ユーザーがテストを受けている間、画面の動作を監視するには **[許可]** を選択します。 **[未構成]** を選択すると、テスト中に画面を監視できなくなります。
- **テキストの候補**:受験者がテキストの候補を表示できるようにするには、**[許可]** を選択します。 **[未構成]** を選択すると、ユーザーがテストを受けている間、テキストの候補がブロックされます。

## <a name="next-steps"></a>次の手順

プロファイルは作成されましたが、まだ何も実行できない可能性があります。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。
