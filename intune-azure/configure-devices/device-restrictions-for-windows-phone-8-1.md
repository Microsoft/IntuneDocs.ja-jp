---
title: "Windows Phone 8.1 向けの Intune デバイスの制限設定 | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Windows Phone 8.1 デバイスのデバイス設定と機能を制御するために使用できる Intune 設定について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d42714-49ca-43b3-b080-2e67a4268198
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 32bc9adb88803385c26894e8a70513a4adc55b27
ms.lasthandoff: 02/16/2017


---

# <a name="windows-phone-81-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune での Windows Phone 8.1 デバイスの制限設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>全般
-     **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
-     **[カメラ]** - デバイスのカメラを許可またはブロックします。
-     **[コピー/貼り付け]** - デバイスでコピー/貼り付け機能を許可またはブロックします。
-     **[リムーバブル記憶域]** - リムーバブル記憶域 (SD カードなど) の使用をデバイスに許可します。
-     **[位置情報]** - デバイスで位置情報を使用できるようにします。
-     **[Microsoft アカウント]** - ユーザーが Microsoft アカウントをデバイスにリンクすることを許可またはブロックします。
-     **[画面キャプチャ]** - ユーザーが画面のコンテンツを画像ファイルとしてキャプチャできるようにします。
-     **[診断データの送信]** - デバイスが Microsoft に診断情報を送信できるようにします。
-     **[カスタム メール アカウントの同期]** - Microsoft 以外の電子メール アカウントにデバイスが接続できるようにします。

## <a name="password"></a>パスワード
-     **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
-     **[パスワードが必要です]** - エンド ユーザーがデバイスにアクセスする際にパスワードの入力を要求します。
    -     **[必要なパスワードの種類]** - 英数字や数字のみなど、必要なパスワードの種類を指定します。
    -     **[パスワードの最小文字数]** - パスワードに必要な最小文字数を指定します。
    -     **[単純なパスワード]** - "0000" や "1234" などの単純なパスワードを使用できることを指定します。
    -     **[デバイスがワイプされるまでのサインイン失敗回数]** - 間違ったパスワードをユーザーが何回入力すると、そのデバイスをワイプするかを指定します。
    -     **[画面がロックされるまでの非アクティブな最長時間 (分)]** - デバイスのアイドル状態が許容される時間を指定します。この時間を超えると、画面は自動的にロックされます。
    -     **[パスワードの有効期限 (日数)]** - デバイスのパスワードの変更が必要になるまでの日数を指定します。
    -     **[Prevent reuse of previous passwords (前のパスワードを再利用できないようにする)]** - 過去に使用されたパスワードの記憶件数を指定します。
-     **[暗号化]** - サポートされているモバイル デバイス上のデータの暗号化を要求します。

## <a name="app-store"></a>アプリ ストア
-     **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
-     **[アプリ ストア]** - デバイスからアプリ ストアへの接続をユーザーに許可します。

## <a name="restricted-apps"></a>制限付きアプリ

-     **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。

制限付きアプリの一覧では、次の一覧のいずれかを構成できます。

**[ブロックされたアプリケーション]** の一覧 - ユーザーによるインストールと実行が許可されていないアプリ (Intune で管理されていない) アプリを一覧表示します。
**[許可されたアプリ]** の一覧 - ユーザーによるインストールが許可されているアプリを一覧表示します。 管理対象アプリは Intune で自動的に許可されます。

この一覧を構成するには、**[追加]** をクリックし、任意の名前、アプリの発行元 (省略可能)、アプリ ストアでのアプリの URL を指定します。

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>ストアにおけるアプリの URL を指定する方法

許可されるアプリおよびブロックされるアプリの一覧でアプリの URL を指定するには、次の形式を使用します。

[Windows Phone ストア](https://www.microsoft.com/store/apps/windows-phone)のページで、使用するアプリを検索します。

アプリのページを開き、URL をクリップボードにコピーします。 許可されているアプリまたはブロックされているアプリの一覧で、これを URL として使用できます。

例: ストアで Skype アプリを検索します。 **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51** という URL を使用します。



### <a name="additional-options"></a>追加オプション

**[インポート]** をクリックして "<*アプリ URL*>, <*アプリ名*>, <*アプリの発行元*>" 形式の csv ファイルから一覧に値を設定したり、**[エクスポート]** をクリックして、制限付きアプリの一覧の内容を含む csv ファイルを同じ形式で作成したりすることもできます。


## <a name="browser"></a>ブラウザー
-     **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
-     **[Web ブラウザー]** - デバイス上の組み込みの Web ブラウザーを許可またはブロックします。

## <a name="cellular-and-connectivity"></a>携帯ネットワークと接続性
-     **[Apply all settings to Windows Phone 8.1 only (すべての設定を Windows Phone 8.1 のみに適用する)]** - これは、クラシック Intune ポータルで構成できる設定です。 Azure Portal では、この設定は変更できません。 これを **[構成済み]** に設定すると、すべての設定が Windows Phone 8.1 デバイスのみに適用されるようになります。 **[未構成]** に設定されている場合、これらの設定は Windows 10 Mobile デバイスにも適用されます。
-     **[Wi-Fi]** - デバイスの Wi-Fi 機能を有効または無効にします。
-     **[Wi-Fi テザリング]** - デバイスで Wi-Fi テザリングを使用できるようにします。
-     **[自動的に Wi-Fi ホットスポットに接続します]** - 無料の Wi-Fi ホットスポットに自動的に接続し、使用条件に自動的に同意することをデバイスに許可します。
-     **[Wi-Fi ホットスポットのレポート]** - ユーザーが近くにある接続を検出するのに役立つ、Wi-Fi 接続に関する情報を送信します。
-     **[NFC]** - 近距離無線通信をサポートするデバイスでこの機能を使用する操作を有効または無効にします。
-     **[Bluetooth]** - デバイスの Bluetooth 機能を有効または無効にします。

