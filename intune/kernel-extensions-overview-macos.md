---
title: MacOS に Microsoft Intune - Azure でのカーネルの拡張機能のデバイス プロファイルを作成 |Microsoft Docs
titleSuffix: ''
description: 追加またはを macOS デバイス プロファイルを作成し、ユーザー オーバーライドを許可するには、Microsoft Intune でのチームの識別子、およびバンドルとチームの識別子の追加のカーネルの拡張機能を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403907"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Intune で macOS カーネルの拡張機能を追加します。

MacOS デバイスでは、カーネル レベルで機能を追加できます。 これらの機能は、通常のプログラムにアクセスできないように、その OS のパーツにアクセスします。 組織には、特定のニーズやアプリ、デバイスの機能、およびなどでは使用できない要件があります。 

デバイス上の負荷を常に許可されるカーネルの拡張機能を追加するには、「カーネルの拡張機能」を追加 (KEXT)、Microsoft Intune で、デバイスにこれらの拡張機能を展開するとします。

たとえば、悪意のあるコンテンツには、デバイスをスキャンするウイルス検出プログラムがあるとします。 このウィルス対策プログラムのカーネルの拡張機能として Intune で許可されているカーネル拡張機能を追加することができます。 次に、「割り当てる」拡張機能を macOS デバイスにします。

この機能により、管理者は、カーネルの拡張機能をオーバーライドし、チームの識別子を追加、Intune での特定のカーネルの拡張機能の追加を許可できます。

この機能は、以下に適用されます。

- macOS 10.13.2 以降

この機能を使用するには、デバイスがある必要があります。

- Apple の Device Enrollment Program (DEP) を使用して Intune に登録します。 [MacOS デバイスを自動的に登録](device-enrollment-program-enroll-macos.md)の詳細。

  または

- 「承認されたユーザーの登録」に、Intune に登録されている (Apple の用語)。 [MacOS High Sierra でカーネルの拡張機能への変更に備える](https://support.apple.com/en-us/HT208019)(Apple の web サイトを開きます) の詳細が。

Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後は、そのプロファイルをお客様の組織内の macOS デバイスにプッシュまたは展開できます。

この記事では、カーネルの拡張機能を使用して、Intune でデバイス構成プロファイルを作成する方法を示します。

> [!TIP]
> カーネルの拡張機能の詳細については、次を参照してください。[カーネル拡張機能の概要](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)(Apple の web サイトを開きます)。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- 符号なしのレガシー カーネルの拡張機能を追加できます。
- 必ず、適切なチーム識別子を入力し、バンドルのカーネルの拡張機能の ID。 Intune では、入力した値を検証しません。 誤った情報を入力すると、デバイスで、拡張機能は機能しません。

> [!NOTE]
> Apple は、署名と証明のすべてのソフトウェアに関する情報をリリースしました。 MacOS 10.14.5 でと、新しいカーネルを Intune で展開された拡張機能は、Apple の証明のポリシーを順守する必要はありません。
>
> この証明ポリシーや更新プログラムの変更については、次のリソースを参照してください。
>
>  - [配布する前に、アプリを notarizing](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (Apple の web サイトを開きます) 
>  - [MacOS High Sierra でカーネルの拡張機能への変更に備える](https://support.apple.com/en-us/HT208019)(Apple の web サイトを開きます)

## <a name="create-the-profile"></a>プロファイルの作成

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
    - **説明**: プロファイルの説明を入力します この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[macOS]** を選択します
    - **プロファイルの種類**: 選択**拡張**します。
    - **[設定]** : 構成する設定内容を入力します。 すべての設定の一覧とその実行内容については、以下を参照してください。

        - [macOS](kernel-extensions-settings-macos.md)

4. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、一覧に表示されます。 必ず[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)してください。

## <a name="next-steps"></a>次の手順

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
