---
title: Microsoft Intune の Windows および Holographic デバイスのキオスク設定 - Azure | Microsoft Docs
description: Microsoft Intune でシングル アプリおよびマルチ アプリ キオスクとして Windows 10 (以降) および Windows Holographic for Business デバイスを構成し、スタート メニューのカスタマイズ、アプリの追加、タスク バーの表示、および Web ブラウザーの構成を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e80bbbb87df88acc24a64a1bb0d977c91c970bb3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57394423"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Intune を使用して専用キオスクとして実行するための Windows 10 および Windows Holographic for Business デバイスの設定

Windows 10 デバイスで Intune を使用して、専用デバイスとも呼ばれるキオスクとしてデバイスを実行します。 キオスク モードのデバイスでは、1 つのアプリも、複数のアプリも実行できます。 スタート メニューの表示とカスタマイズ、Win32 アプリを含むさまざまなアプリの追加、特定のホーム ページの Web ブラウザーへの追加などを行うことができます。 

この機能は、次を実行しているデバイスに適用されます。

- Windows 10 以降
- Windows Holographic for Business

Intune では、デバイスごとに 1 つのキオスク プロファイルをサポートします。 1 台のデバイスに複数のキオスク プロファイルが必要な場合は、[カスタム OMA-URI](custom-settings-windows-10.md) を使用することができます。

Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 このような機能をプロファイルに追加したら、その設定を組織内のグループにプッシュまたは展開します。

この記事では、デバイス構成プロファイルを作成する方法について説明します。 すべての設定の一覧とその実行内容については、[Windows 10 のキオスク設定](kiosk-settings-windows.md)と [Windows Holographic for Business のキオスク設定](kiosk-settings-holographic.md)に関するページを参照してください。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Azure portal](https://portal.azure.com) で、**[すべてのサービス]** を選択し、**Intune** でフィルター処理して、**[Microsoft Intune]** を選びます。
2. **[デバイス構成]**、**[プロファイル]**、**[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

   - **[名前]**:新しいプロファイルのわかりやすい名前を入力します。
   - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
   - **[プラットフォーム]**:**[Windows 10 以降]** を選択します。
   - **[プロファイルの種類]**:**[キオスク]** を選択します。

4. **[設定]** の **[キオスク モード]** を選択します。 **[キオスク モード]** では、ポリシーによってサポートされるキオスク モードの種類を識別します。 次のオプションがあります。

    - **[未構成]** (既定):このポリシーでは、キオスク モードが有効になりません。
    - **[シングル アプリ、全画面表示キオスク]**:デバイスは単一ユーザー アカウントとして実行され、1 つのストア アプリに制限されます。 したがって、ユーザーがサインインすると、特定のアプリが起動します。 また、このモードでは、ユーザーによる新しいアプリを開く操作や、実行中のアプリを変更する操作が制限されます。
    - **[マルチ アプリ キオスク]**:デバイスはアプリケーション ユーザー モデル ID (AUMID) を使用して複数のストア アプリ、Win32 アプリ、または受信トレイの Windows アプリを実行します。 デバイスでは追加されているアプリだけを利用できます。

        マルチ アプリ キオスク (または固定目的デバイス) の利点は、ユーザーがアクセスできるのは必要なアプリだけなので、わかりやすいエクスペリエンスがユーザーに提供されることです。 また、必要のないアプリはビューから削除されます。

    すべての設定の一覧とその実行内容については、以下を参照してください。
      - [Windows 10 のキオスク設定](kiosk-settings-windows.md)
      - [Windows Holographic for Business のキオスク設定](kiosk-settings-holographic.md)

5. 完了したら、**[OK]** > **[作成]** を選択して変更を保存します。 

プロファイルが作成され、プロファイル一覧に表示されます。 次に、プロファイルを[割り当てます](device-profile-assign.md)。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

次のプラットフォームを実行するデバイス用のキオスク プロファイルを作成できます。
- [Android](device-restrictions-android.md#kiosk)
- [Android エンタープライズ](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 以降](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
