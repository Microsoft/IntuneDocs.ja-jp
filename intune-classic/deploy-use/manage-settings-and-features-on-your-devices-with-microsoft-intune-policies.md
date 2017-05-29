---
title: "ポリシーを使用してデバイスの設定を管理する | Microsoft Docs"
description: "Intune を使用して、管理する登録デバイスの設定と機能を制御するポリシーを作成して展開します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8f1a4cb3bcab4aee534fc5fb9a1f1a1eb5a6f3a1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="manage-settings-and-features-on-your-devices-with-microsoft-intune-policies"></a>Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune の*ポリシー*は、モバイル デバイスとコンピューターの機能を制御する設定のグループです。 ポリシーは、推奨設定やカスタム設定を含むテンプレートを使用することで作成し、デバイスまたはユーザー グループに展開します。

## <a name="types-of-policies"></a>ポリシーの種類

Intune のポリシーは以下のカテゴリに分類されます。 使用するカテゴリは、ポリシーの作成方法と展開方法に影響があります。


- **構成ポリシー:** デバイスのセキュリティ設定と機能を管理するために一般的に使用されます。 ポリシーの作成方法と展開方法、使用できる設定については、このトピックの情報を参照してください。
- **デバイス コンプライアンス ポリシー:** デバイスが条件付きアクセス ポリシーによって "準拠している" と見なされるために遵守する必要がある規則および設定を定義します。 コンプライアンス ポリシーを使用して、条件付きアクセスとは別に、デバイスのコンプライアンスを監視および修復することもできます。
詳細については、「[Microsoft Intune のデバイス コンプライアンス ポリシー](introduction-to-device-compliance-policies-in-microsoft-intune.md)」を参照してください。
- **条件付きアクセス ポリシー:** 指定する条件に基づいて電子メールおよびその他のサービスをセキュリティで保護できます。
詳細については、「[Microsoft Intune を使用して電子メールおよび O365 サービスへのアクセスを制限する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)」を参照してください。
- **会社のデバイスの登録ポリシー:** 会社のデバイスの登録ポリシーについては、「[Microsoft Intune を使用した iOS および Mac の管理のセットアップ](set-up-ios-and-mac-management-with-microsoft-intune.md)」を参照してください。
- **リソース アクセス ポリシー:** これらのポリシーを使用すると、ユーザーはどこにいても仕事を確実に遂行するために必要なファイルとリソースにアクセスできます。
詳細については、「[Microsoft Intune を使用して、会社のリソースへのアクセスを有効にする](enable-access-to-company-resources-with-microsoft-intune.md)」を参照してください。


Intune ポリシーの一覧については、「[Microsoft Intune policy reference (Microsoft Intune ポリシー リファレンス)](microsoft-intune-policy-reference.md)」を参照してください。

## <a name="create-a-configuration-policy"></a>構成ポリシーを作成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[ポリシー]、** &gt; **[構成ポリシー]** &gt; **[追加]** の順に選択します。

2.  作成するポリシーを選択します。ポリシーの推奨設定 (使用可能な場合。この設定は後で変更できます) を使用するか、独自の設定でカスタム ポリシーを作成するか選びます。

    > [!TIP]
    > 適切なポリシーを選択する方法については、「[Microsoft Intune ポリシー リファレンス](microsoft-intune-policy-reference.md)」を参照してください。

3.  準備ができたら、 **[ポリシーを作成する]** を選択します。

4.  **[ポリシーを作成する]** ページで、ポリシーの名前とオプションの説明を構成します。

5.  必要なポリシー設定を構成して、**[ポリシーの保存]** を選択します。

    ポリシー設定の詳細については、次の一覧から使用するポリシーの種類を選択してください。

    - [iOS デバイス向けの設定](ios-policy-settings-in-microsoft-intune.md)
    - [Android デバイス向けの設定](android-policy-settings-in-microsoft-intune.md)
    - [Android for Work デバイス向けの設定](android-for-work-policy-settings-in-microsoft-intune.md)
    - [Windows 8 および Windows 8.1 デバイス向けの設定](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Windows Phone 8.1 デバイス向けの設定](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Windows 10 デスクトップおよびモバイル デバイス向けの設定](windows-10-policy-settings-in-microsoft-intune.md)
    - [Windows チーム デバイス向けの設定](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Windows エディション アップグレード向けの設定](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Mac OS X デバイスの設定](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Exchange ActiveSync 向けの設定](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [使用条件ポリシー向けの設定](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [モバイル デバイス (レガシ) 向けの全般設定](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  確認ダイアログ ボックスで、**[はい]** を選択してポリシーをすぐに展開するか、**[いいえ]** を選択して展開せずにポリシーを作成します。

**[ポリシー]** ワークスペースの各種ポリシーについてのセクションを参照し、新しいポリシーを表示して編集します。

推奨設定を使用するポリシーを作成する場合、新しいポリシーの名前は、テンプレート名と、日付、時刻の組み合わせになります。 ポリシーを編集するときに、名前は、編集した時間と日付で更新されます。

ポリシーを作成したら、通常 1 つ以上のユーザー グループまたはデバイスにポリシーを展開します。

> [!TIP]
> すべての種類のポリシーを展開するわけではありません。 たとえば、モバイル アプリケーション管理 (MAM) ポリシーは展開されません。 代わりに、この種類のポリシーはアプリに関連付けられ、このアプリが展開されます。

## <a name="deploy-a-configuration-policy"></a>構成ポリシーを展開する

1.  **[ポリシー]** ワークスペースで、展開するポリシーを選び、**[展開の管理]** を選びます。

2.  **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。

    -   ポリシーを展開するには、ポリシーを展開する対象となる 1 つ以上のグループを選択して、**[追加]** &gt; **[OK]** の順に選択します。

    -   ポリシーを展開せずにダイアログ ボックスを閉じるには、**[キャンセル]** を選択します。

展開済みポリシーを選択すると、ポリシー一覧の下部に展開についての詳細が表示されます。

## <a name="manage-policies"></a>ポリシーの管理

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com/)で、**[ポリシー]** を選択し、管理するポリシーを参照して選択します。

2.  次のアクションのいずれかを選択します。

- **編集** - 選択したポリシーのプロパティを開き、変更できます。
- **削除** - 選択したポリシーを削除します。<br>ポリシーを削除すると、展開先のすべてのグループから削除されます。
- **展開の管理** - ポリシーを展開するグループを選択し、**[追加]** を選択します。


## <a name="frequently-asked-questions-about-intune-policies"></a>Intune ポリシーについてよく寄せられる質問

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-deployed"></a>モバイル デバイスが展開後にポリシーまたはアプリを取得するのにどれくらいの時間がかかりますか。
ポリシーまたはアプリが展開されると、Intune はデバイスに対して、Intune サービスにチェックインする必要があることをすぐに通知し始めます。 これにかかる時間は通常 5 分未満です。

最初の通知が送信された後、デバイスがチェックインしてポリシーを取得しない場合、Intune はさらに 3 回試行します。  デバイスがオフライン (たとえば、デバイスの電源がオフである、ネットワークに接続されていない) の場合、通知を受信していない可能性があります。 この場合、デバイスは次回のスケジュールされた Intune サービスへのチェックインでポリシーを取得することになります。チェックイン頻度は次のとおりです。

- iOS と Mac OS X: 6 時間ごと
- Android: 8 時間ごと
- Windows Phone: 8 時間ごと
- デバイスとして登録された Windows 8.1 および Windows 10 PC: 8 時間ごと

登録してすぐのデバイスでは、チェックイン頻度が高くなります。頻度は次のとおりです。

- iOS と Mac OS X: 6 時間まで 15 分ごと、その後 6 時間ごと
- Android: 15 分まで 3 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと
- Windows Phone: 15 分まで 5 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと
- デバイスとして登録された Windows PC: 30 分まで 3 分ごと、その後 8 時間ごと

また、ユーザーはポータル サイト アプリを起動し、デバイスを同期して、いつでもすぐにポリシーを確認できます。

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>どのような操作を行うと Intune は通知をデバイスにすぐに送信しますか。
デバイスは、チェックインを指示する通知を受け取ったとき、または定期的にスケジュールされたチェックイン時に Intune にチェックインします。  ワイプ、ロック、パスコードのリセット、アプリの展開、プロファイルの展開 (Wi-Fi、VPN、メールなど)、ポリシーの展開などの操作で具体的にデバイスまたはユーザーを対象とする場合、Intune は、デバイスが Intune サービスにチェックインしてこれらの更新プログラムを受信するよう指示する通知をすぐに開始します。

ポータル サイトの連絡先情報の修正など、他の変更ではデバイスへの通知はすぐに行われません。

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>複数のポリシーが同じユーザーまたはデバイスに展開される場合、どの設定が適用されるのかどうすればわかりますか。
2 つ以上のポリシーが同じユーザーまたはデバイスに展開される場合、適用される設定の評価は個々の設定レベルで行われます。

-   コンプライアンス ポリシー設定は常に構成ポリシー設定よりも優先されます。

-   異なるコンプライアンス ポリシーの同じ設定について評価する場合、最も制限の厳しいコンプライアンス ポリシー設定が適用されます。

-   構成ポリシーの設定が別の構成ポリシーの設定と競合する場合、Intune コンソールにその競合が表示されます。 このような競合は手動で解決する必要があります。

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>モバイル アプリケーション管理ポリシーが互いに競合する場合はどうなりますか。 どのポリシーがアプリに適用されますか。
競合している値は、(リセットする前の PIN の試行で使用するような) 番号入力フィールドを除き、MAM ポリシーで使用可能な最も制限の厳しい設定になっています。  番号入力フィールドは、推奨設定のオプションを使用することでコンソールで MAM ポリシーを作成した場合と同じ値に設定されます。

競合は、2 つのポリシー設定が同じ場合に発生します。  たとえば、コピー/貼り付けの設定以外は同じ MAM ポリシーを 2 つ構成したとします。  この場合、コピー/貼り付けの設定は最も厳しい値になりますが、残りの設定は構成したとおりに適用されます。

1 つのポリシーをアプリに展開し、このポリシーが有効になった後、2 つ目のポリシーを展開すると、2 つ目のポリシーは競合の状態になりますが、最初のポリシーは優先され、適用されたままになります。 両方を同時に適用する (優先されるポリシーがない) 場合は、両方が競合の状態になります。 競合する設定は、最も制限の厳しい値に設定されます。

### <a name="what-happens-when-ios-custom-policies-conflict"></a>iOS カスタム ポリシーが競合するとどうなりますか。
Intune は Apple 構成ファイルのペイロードまたはカスタム Open Mobile Alliance Uniform Resource Identifier (OMA-URI) ポリシーを評価しません。 配信メカニズムとしてのみ機能します。

カスタム ポリシーを展開するときは、構成した設定がコンプライアンス、構成、または他のカスタム ポリシーと競合していないことを確認してください。 設定が競合しているカスタム ポリシーの場合、設定が適用される順序はランダムになります。

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>ポリシーが削除された場合または適用できなくなった場合はどうなりますか。
ポリシーを削除した場合やポリシーを展開したグループからデバイスを削除した場合は、次のリストに従ってポリシーと設定がデバイスから削除されます。

#### <a name="enrolled-devices"></a>[登録済みデバイス]

- Wi-Fi、VPN、証明書、電子メールのプロファイル: これらのプロファイルは、すべてのサポートされる登録デバイスから削除されます。
- その他のすべてのポリシーの種類:
    - **Windows および Android デバイス**: 設定はデバイスから削除されません。
    - **Windows Phone 8.1 デバイス**: 次の設定が削除されます。
        - モバイル デバイスのロックを解除するパスワードを要求する
        - 単純なパスワードを許可する
        - 最小のパスワードの長さ
        - 必要なパスワードの種類
        - パスワードの有効期限 (日)
        - パスワードの履歴を記憶する
        - デバイスをワイプするまでの連続サインイン エラーの数
        - パスワードが必要になるまでの非アクティブ状態の時間 (分)
        - 必要なパスワードの種類 - 文字セットの最小数
        - カメラを許可する
        - モバイル デバイスの暗号化を要求する
        - リムーバブル記憶域を許可する
        - Web ブラウザーを許可する
        - アプリケーション ストアを許可する
        - 画面のキャプチャを許可する
        - 位置情報を許可する
        - Microsoft アカウントを許可する
        - コピーと貼り付けを許可する
        - Wi-Fi テザリングを許可する
        - 無料 Wi-Fi スポットへの自動接続を許可する
        - Wi-Fi スポットの報告を許可する
        - 工場出荷時のリセットを許可する
        - Bluetooth を許可する
        - NFC を許可する
        - Wi-Fi を許可する

    - **iOS**: 次を除き、すべての設定が削除されます。
        - 音声通話ローミングを許可する
        - データ ローミングを許可する
        - ローミング中の自動同期を許可する

#### <a name="windows-pcs-running-the-intune-client-software"></a>Intune クライアント ソフトウェアを実行している Windows PC

- **Endpoint Protection 設定**: 設定は、推奨値に復元されます。 例外は、**[Microsoft Active Protection Service に参加する]** の設定だけで、既定値は **[いいえ]** です。 詳細については、「[Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)」を参照してください。
- **ソフトウェアの更新プログラムの設定**: 設定は、オペレーティング システムの既定の状態にリセットされます。 詳細については、「[Microsoft Intune でソフトウェア更新プログラムを使用して Windows PC を最新の状態に保つ](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)」を参照してください。
- **Microsoft Intune Center の設定**: ポリシーで構成されたサポートの連絡先情報は、すべてコンピューターから削除されます。
- **Windows ファイアウォールの設定**: 設定は、コンピューターのオペレーティング システムの既定にリセットされます。 詳細については、「[Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)」を参照してください。


### <a name="how-can-i-refresh-the-policies-on-a-device-to-ensure-that-they-are-current-applies-to-windows-pcs-running-the-intune-client-software-only"></a>どうしたらデバイスのポリシーを更新して最新の状態に保つことができますか (Intune クライアント ソフトウェアを実行している Windows PC にのみ適用されます)。

1.  任意のデバイス グループで、ポリシーを更新するデバイスを選択して、**[リモート タスク]** &gt; **[ポリシーの更新]** の順に選択します。
2.  Intune 管理コンソールの右下にある **[リモート タスク]** を選択し、タスクの状態を確認します。

### <a name="where-can-i-find-help-troubleshooting-policies"></a>ポリシーのトラブルシューティングのヘルプはどこにありますか?

「[Microsoft Intune のポリシーのトラブルシューティング](/intune-classic/troubleshoot/troubleshoot-policies-in-microsoft-intune)」をご覧ください。

