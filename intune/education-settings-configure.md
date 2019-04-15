---
title: Microsoft Intune で教育設定を追加または構成する - Azure | Microsoft Docs
description: Windows 10 以降のデバイス上の Microsoft Intune では、デバイス構成プロファイル内にテスト アプリを使用します。 [教育] 設定を使用して構成プロファイルを作成して、テスト アプリの URL の入力、ユーザーのサインイン方法の選択、テスト中の画面の監視、テスト中のテキスト候補の許可または禁止を行います。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/10/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efa990e12416c292d9446428165e4bff99c7eca2
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57393215"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Windows 10 デバイス上の Microsoft Intune でテスト アプリを使用する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune の [教育] プロファイルは、デバイス上でテストや試験を受ける学生向けに設計されています。 この機能には、**テスト** アプリと、テスト URL の追加、エンドユーザーによるテストへのサインイン方法の選択などの設定が含まれています。 この機能は次のプラットフォームをサポートしています。

- Windows 10 以降

ユーザーがサインインすると、テスト アプリが自動的に開き、入力したテストが表示されます。 テスト中は他のアプリをデバイス上で実行できません。 テスト アプリの詳細については、「[Windows 10 でテストを受ける](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)」を参照してください。

この記事では、Microsoft Intune でデバイス構成プロファイルを作成する手順を説明します。 また、Windows 10 デバイスに使用できる教育設定について読み、学習するための情報も含まれています。

## <a name="create-a-device-profile"></a>デバイス プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**Microsoft Intune** を選びます。
2. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **[名前]**:新しいプロファイルのわかりやすい名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]**:**[Windows 10 以降]** を選択します。
    - **[プロファイル]**:**[教育プロファイル]** を選択します。

4. 構成が必要な設定を入力します。

    - [Windows 10 以降](education-settings-windows.md)

5. **[OK]** > **[作成]** を選択して変更を保存します。

設定を入力してプロファイルを作成すると、プロファイルの一覧に自分のプロファイルが表示されます。 次に、[このプロファイルをいくつかのグループに割り当てます](device-profile-assign.md)。

## <a name="next-steps"></a>次の手順

[Windows 10 の教育設定](education-settings-windows.md)の一覧とその説明を参照してください。

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
