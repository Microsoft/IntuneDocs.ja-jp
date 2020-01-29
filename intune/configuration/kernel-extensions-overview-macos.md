---
title: Microsoft Intune を使用して macOS カーネル拡張機能デバイス プロファイルを作成する - Azure | Microsoft Docs
titleSuffix: ''
description: macOS デバイス プロファイルを追加または作成した後、カーネル拡張機能を構成して、Microsoft Intune でのユーザーによるオーバーライド、チーム識別子の追加、バンドルとチーム識別子を許可します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1075054f3812e8c40f38e705a440c46ba09fdd0e
ms.sourcegitcommit: 11cbd2a9d90dea20f6dc1f54f0a6acbeec3a71d6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146771"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Intune で macOS カーネル拡張機能を追加する

macOS デバイスでは、カーネル レベルで機能を追加できます。 これらの機能では、通常のプログラムがアクセスできない OS の部分にアクセスします。 組織には、アプリやデバイスの機能などでは利用できない特定のニーズや要件がある場合があります。 

デバイスでの読み込みが常に許可されているカーネル拡張機能を追加するには、Microsoft Intune で "カーネル拡張機能" (KEXT) を追加した後、これらの拡張機能をデバイスに展開します。

たとえば、デバイスで悪意のあるコンテンツをスキャンするウイルス スキャン プログラムがあるとします。 このウイルス スキャン プログラムのカーネル拡張機能を、Intune で許可されるカーネル拡張機能として追加できます。 次に、拡張機能を macOS デバイスに "割り当て" ます。

この機能を使用すると、管理者は、ユーザーが Intune でカーネル拡張機能をオーバーライドしたり、チーム識別子を追加したり、特定のカーネル拡張機能を追加したりすることを許可できます。

この機能は、以下に適用されます。

- macOS 10.13.2 以降

この機能を使用するには、次のようなデバイスが必要です。

- Apple の Device Enrollment Program (DEP) を使用して Intune に登録されている。 詳細については、[macOS デバイスの自動登録](../enrollment/device-enrollment-program-enroll-macos.md)に関する記事を参照してください。

  または

- "ユーザー承認済みの登録" (Apple の用語) を使用して Intune に登録されている。 詳細については、「[macOS High Sierra のカーネル機能拡張の変更点について準備を進める](https://support.apple.com/en-us/HT208019)」 (Apple の Web サイトが開きます) を参照してください。

Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後は、そのプロファイルをお客様の組織内の macOS デバイスにプッシュまたは展開できます。

この記事では、Intune でカーネル拡張機能を使用してデバイス構成プロファイルを作成する方法について説明します。

> [!TIP]
> カーネル拡張機能の詳細については、「[kernel extension overview](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)」(カーネル拡張機能の概要) (Apple の Web サイトが開きます) を参照してください。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- 未署名のレガシ カーネル拡張機能を追加できます。
- カーネル拡張機能の正しいチーム識別子とバンドル ID を入力してください。 Intune では、入力した値は検証されません。 間違った情報を入力すると、デバイス上の拡張機能は機能しません。 チーム識別子の長さは、英数字で厳密に 10 文字です。 

> [!NOTE]
> Apple から、すべてのソフトウェアの署名と公証 (Notarization) に関する情報が公開されています。 macOS 10.14.5 以降では、Intune を使用して展開されたカーネル拡張機能は、Apple の公証ポリシーを満たしている必要はありません。
>
> この公証ポリシー、および更新または変更の詳細については、次のリソースを参照してください。
>
> - [配布の前にアプリを公証する](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (Apple の Web サイトが開きます) 
> - [macOS High Sierra のカーネル機能拡張の変更点について準備を進める](https://support.apple.com/en-us/HT208019) (Apple の Web サイトが開きます)

## <a name="create-the-profile"></a>プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**:新しいプロファイルのわかりやすい名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[macOS]** を選択します
    - **プロファイルの種類**: **[拡張機能]** を選択します。
    - **設定**:構成が必要な設定を入力します。 すべての設定の一覧とその実行内容については、以下を参照してください。

        - [macOS](kernel-extensions-settings-macos.md)

4. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、一覧に表示されます。 必ず[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](../device-profile-monitor.md)してください。

## <a name="next-steps"></a>次のステップ

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](../device-profile-monitor.md)します。
