---
title: Microsoft Intune を使用して macOS カーネル拡張機能デバイスプロファイルを作成する-Azure |Microsoft Docs
titleSuffix: ''
description: MacOS デバイスプロファイルを追加または作成し、ユーザーの上書き、チーム識別子の追加、および Microsoft Intune でのバンドルとチーム識別子を許可するようにカーネル拡張を構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e69f1b11833da0906aaf831f8bb82b04241e442f
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755175"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Intune で macOS カーネル拡張機能を追加する

MacOS デバイスでは、カーネルレベルで機能を追加できます。 これらの機能は、通常のプログラムがアクセスできない OS の部分にアクセスします。 組織には、アプリやデバイスの機能などでは利用できない特定のニーズや要件がある場合があります。 

デバイスでの読み込みが常に許可されているカーネル拡張機能を追加するには、Microsoft Intune で "カーネル拡張機能" (KEXT) を追加し、これらの拡張機能をデバイスに展開します。

たとえば、悪意のあるコンテンツがないかデバイスをスキャンするウイルススキャンプログラムがあるとします。 このウイルス検索プログラムのカーネル拡張機能は、Intune で許可されているカーネル拡張機能として追加できます。 次に、拡張機能を macOS デバイスに "割り当て" ます。

この機能を使用すると、管理者は、ユーザーがカーネル拡張機能をオーバーライドしたり、チーム識別子を追加したり、Intune で特定のカーネル拡張機能を追加したりできるようになります。

この機能は、以下に適用されます。

- macOS 10.13.2 以降

この機能を使用するには、デバイスが次のようになっている必要があります。

- Apple の Device Enrollment Program (DEP) を使用して Intune に登録されます。 [MacOS デバイスを自動的に登録](../enrollment/device-enrollment-program-enroll-macos.md)する方法についてはこちらを参照してください。

  または

- "ユーザーが承認した登録" (Apple の用語) を使用して Intune に登録されます。 [MacOS High でカーネル拡張機能の変更を準備する](https://support.apple.com/en-us/HT208019)(Apple の web サイトを開く) 詳細については、こちらを参照してください。

Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 これらの機能をプロファイルに追加した後は、そのプロファイルをお客様の組織内の macOS デバイスにプッシュまたは展開できます。

この記事では、Intune でカーネル拡張機能を使用してデバイス構成プロファイルを作成する方法について説明します。

> [!TIP]
> カーネル拡張機能の詳細については、「[カーネル拡張機能の概要](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)」 (Apple の web サイトを開きます) を参照してください。

## <a name="what-you-need-to-know"></a>知っておく必要がある情報

- 未署名のレガシカーネル拡張機能を追加できます。
- カーネル拡張機能の正しいチーム識別子とバンドル ID を入力してください。 Intune では、入力した値は検証されません。 間違った情報を入力すると、デバイス上の拡張機能は機能しません。

> [!NOTE]
> Apple は、すべてのソフトウェアの署名と notarization 関する情報を公開しました。 MacOS 10.14.5 以降では、Intune を使用して展開されたカーネル拡張機能は、Apple の notarization ポリシーを満たしている必要はありません。
>
> この notarization ポリシー、および更新または変更の詳細については、次のリソースを参照してください。
>
> - [配布前にアプリ](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)を表示する (Apple の web サイトを開く) 
> - [MacOS High でカーネル拡張機能の変更を準備する](https://support.apple.com/en-us/HT208019)(Apple の web サイトを開く)

## <a name="create-the-profile"></a>プロファイルの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]**  >  **[構成プロファイル]**  >  **[プロファイルの作成]** を選択します。
3. 次のプロパティを入力します。

    - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
    - **説明**: プロファイルの説明を入力します この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[macOS]** を選択します
    - **プロファイルの種類**: **[拡張機能]** を選択します。
    - **[設定]** : 構成する設定内容を入力します。 すべての設定の一覧とその実行内容については、以下を参照してください。

        - [macOS](kernel-extensions-settings-macos.md)

4. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、一覧に表示されます。 必ず[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](../device-profile-monitor.md)してください。

## <a name="next-steps"></a>次の手順

プロファイルが作成されると、割り当てることができます。 次に、[プロファイルを割り当て](../device-profile-assign.md)、[その状態を監視](../device-profile-monitor.md)します。
