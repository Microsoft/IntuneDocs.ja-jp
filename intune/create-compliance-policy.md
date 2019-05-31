---
title: Microsoft Intune - Azure のデバイス コンプライアンス ポリシー | Microsoft Docs
description: デバイス コンプライアンス ポリシーの使用の開始、状態と重大度レベルの概要、InGracePeriod 状態の使用、条件付きアクセスの使用、割り当てポリシーなしのデバイスの処理、Microsoft Intune の Azure portal とクラシック ポータルのコンプライアンスの違い
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da0aa98774f25bf290391225c6ccae56a3859c22
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570417"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Microsoft Intune でコンプライアンス ポリシーを作成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune を使用して組織のリソースを保護する場合、デバイスのコンプライアンス ポリシーは重要な機能です。 Intune では、最低限の OS バージョンなど、デバイスがコンプライアンス準拠と見なされるために満たす必要がある規則と設定を作成できます。 デバイスが準拠していない場合は、[条件付きアクセス](conditional-access.md)を使用してデータとリソースへのアクセスをブロックできます。

また、コンプライアンス非準拠の場合は、通知メールをユーザーに送信するなどの対応を実行できます。 コンプライアンス ポリシーの役割と使用方法の概要については、[デバイスのコンプライアンスの概要](device-compliance-get-started.md)に関するページを参照してください。

この記事の内容:

- コンプライアンス ポリシーを作成する前提条件と手順を示します。
- ユーザーおよびデバイス グループにポリシーを割り当てる方法を示します。
- ポリシーを "フィルター処理" するためのスコープのタグ、準拠していないデバイスに対して実行できる手順など、追加の機能について説明します。
- デバイスでポリシーの更新を受信した際のチェックインの更新サイクル時間を示します。

## <a name="before-you-begin"></a>始める前に

デバイス コンプライアンス ポリシーを使う場合、次のことを確認します。

- 以下のサブスクリプションを使用します。

  - Intune
  - 条件付きアクセスを使用する場合は、Azure Active Directory (AD) Premium Edition が必要です。 「[Azure Active Directory の価格](https://azure.microsoft.com/pricing/details/active-directory/)」には、さまざまなエディションで入手できる機能を一覧表示しています。 Intune のコンプライアンスには、Azure AD は必要ありません。

- サポートされているプラットフォームを使用します。

  - Android
  - Android エンタープライズ
  - iOS
  - macOS (プレビュー)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8。1

- Intune にデバイスを登録します (コンプライアンスの状態を確認するために必要です)。

- 1 人のユーザーにデバイスを登録するか、またはプライマリ ユーザーなしで登録します。 複数のユーザーに登録されたデバイスはサポートされていません。

## <a name="create-the-policy"></a>ポリシーを作成する

1. [Azure portal](https://portal.azure.com) で、 **[すべてのサービス]** を選択し、**Intune** でフィルター処理して、 **[Intune]** を選択します。
2. **[デバイスのポリシー準拠]** を選択します。 次のオプションがあります。

    - **概要**:準拠しているデバイス、評価されていないデバイスなど、デバイスの概要と数を示します。 ポリシーと、ポリシーの個々の設定も一覧表示します。 「[Intune デバイスのコンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)」では、いくつかの有用な情報を提供しています。
    - **管理**:デバイス ポリシーを作成したり、非準拠のデバイスに[通知](quickstart-send-notification.md)を送信したり、[ネットワーク フェンシング](use-network-locations.md)を有効化したりします。
    - **監視**:デバイスのコンプライアンス状態と、設定およびポリシー レベルでのコンプライアンス状態を確認します。 「[Intune デバイスのコンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)」は、優れたリソースです。 また、ログを参照し、デバイスの脅威エージェントの状態を確認します。
    - **セットアップ**:[組み込みのコンプライアンス ポリシー](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)を使用したり、[Windows Defender Advanced Threat Protection (ATP)](advanced-threat-protection.md) を有効にしたり、[Mobile Threat Defense コネクタ](mobile-threat-defense.md)を追加したり、[Jamf](conditional-access-integrate-jamf.md) を使用したりします。

3. **[ポリシー]**  >  **[ポリシーの作成]** を選択します。 次のプロパティを入力します。

    - **名前**: ポリシーのわかりやすい名前を入力します。 後で簡単に識別できるよう、ポリシーに名前を付けます。 たとえば、適切なポリシー名は、**iOS 脱獄したデバイスを非準拠としてマークする**などです。
    - **説明**:ポリシーの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** :デバイスのプラットフォームを選択します。 次のようなオプションがあります。  

       - **Android**
       - **Android エンタープライズ**
       - **Android**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 以降**
       - **Windows 10 以降**

    - **設定**:次の記事では、プラットフォームの種類ごとの設定を一覧表示して説明します。

        - [Android](compliance-policy-create-android.md)
        - [Android エンタープライズ](compliance-policy-create-android-for-work.md)
        - [Android](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1、Windows 8.1 以降](compliance-policy-create-windows-8-1.md)
        - [Windows 10 以降](compliance-policy-create-windows.md)

4. 完了したら、 **[OK]**  >  **[作成]** の順に選択して変更を保存します。 ポリシーが作成され、一覧に表示されます。 次に、グループにポリシーを割り当てます。

## <a name="assign-user-groups"></a>ユーザー グループを割り当てる

ポリシーが作成されたら、次の手順として、グループにポリシーを割り当てます。

1. 作成したポリシーを選択します。 既存のポリシーは、 **[デバイスのポリシー準拠]**  >  **[ポリシー]** で確認できます。
2. ポリシーを選択し、 **[割り当て]** を選択します。 Azure Active Directory (AD) のセキュリティ グループは、含めることも除外することもできます。
3. **[選択したグループ]** を選択すると、Azure AD セキュリティ グループが表示されます。 このポリシーで適用するユーザー グループを選択し、 **[保存]** を選択してユーザーにポリシーを展開します。

ユーザーにポリシーが適用されました。 ポリシーの対象となっているユーザーが使用しているデバイスに対して、コンプライアンスに関する評価が行われます。

### <a name="evaluate-how-many-users-are-targeted"></a>対象となるユーザー数を評価する

ポリシーを割り当てるときに、影響を受けるユーザー数を**評価**することもできます。 この機能によってユーザーが計算されます。デバイスは計算されません。

1. Intune で、 **[デバイスのポリシー準拠]**  >  **[ポリシー]** を選択します。
2. ポリシーを選択し、 **[割り当て]**  >  **[評価]** を選択します。 このポリシーの対象となるユーザー数を示すメッセージが表示されます。

**[評価]** ボタンが灰色表示されている場合は、ポリシーが 1 つまたは複数のグループに割り当てられていることを確認してください。

## <a name="actions-for-noncompliance"></a>コンプライアンス非対応に対するアクション

コンプライアンス ポリシーに違反するデバイスについて、自動的に適用されるアクションのシーケンスを追加できます。 デバイスを非対応としてマークするスケジュールを更新することができます (たとえば、1 日後)。 デバイスが非対応になったとき、ユーザーにメールを送信する 2 つ目のアクションを構成することもできます。

ユーザーへの通知メールの作成など、詳細については、[非対応デバイスに対するアクションの追加](actions-for-noncompliance.md)に関するページを参照してください。

たとえば、[場所] 機能を使用して、コンプライアンス ポリシー内に場所を追加するとします。 少なくとも 1 つの場所を選択すると、コンプライアンス非対応に対する既定のアクションが適用されます。 選択した場所にデバイスが接続されていない場合、そのデバイスはすぐに非対応と見なされます。 ユーザーには猶予期間 (たとえば、1 日) を与えることができます。

## <a name="scope-tags"></a>スコープのタグ

スコープのタグは、営業、人事、US-NC の全従業員など、特定のグループにポリシーを割り当てて、フィルター処理するのに最適な方法です。 設定を追加したら、コンプライアンス ポリシーにスコープのタグを追加することもできます。 [スコープのタグを使用したポリシーのフィルター処理](scope-tags.md)に関するページは、優れたリソースです。

## <a name="refresh-cycle-times"></a>サイクル時間の更新

コンプライアンスを確認するときに、Intune では構成プロファイルとして同じ更新サイクルが使われます。 通常、時間は次のとおりです。

| プラットフォーム | 更新サイクル|
| --- | --- |
| iOS | 6 時間ごと |
| macOS | 6 時間ごと |
| Android | 8 時間ごと |
| デバイスとして登録された Windows 10 PC | 8 時間ごと |
| Windows Phone | 8 時間ごと |
| Windows 8.1 | 8 時間ごと |

登録してすぐのデバイスでは、次のようにコンプライアンス チェックインの実行頻度が高くなります。

| プラットフォーム | 頻度 |
| --- | --- |
| iOS | 6 時間まで 15 分ごと、その後 6 時間ごと |  
| macOS | 6 時間まで 15 分ごと、その後 6 時間ごと | 
| Android | 15 分まで 3 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと | 
| デバイスとして登録された Windows 10 PC | 30 分まで 3 分ごと、その後 8 時間ごと | 
| Windows Phone | 15 分まで 5 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと | 
| Windows 8.1 | 15 分まで 5 分ごと、その後の 2 時間は 15 分ごと、その後 8 時間ごと | 

ユーザーはいつでもポータル サイト アプリを起動し、デバイスを同期して、ポリシーをすぐに確認できます。

### <a name="assign-an-ingraceperiod-status"></a>InGracePeriod 状態を割り当てる

コンプライアンス ポリシーの InGracePeriod 状態は値の 1 つです。 この値は、デバイスの猶予期間、およびそのコンプライアンス ポリシーのデバイスの実際の状態の組み合わせによって決まります。

具体的には、デバイスに割り当てられているコンプライアンス ポリシーが NonCompliant 状態になっている場合、次のようになります。

- デバイスに猶予期間が割り当てられていない場合、コンプライアンス ポリシーの割り当て済みの値は NonCompliant です。
- デバイスに割り当てられている猶予期間が期限切れになっている場合、コンプライアンス ポリシーの割り当て済みの値は NonCompliant です。
- デバイスに将来の猶予期間が割り当てられている場合、コンプライアンス ポリシーの割り当て済みの値は InGracePeriod です。

次の表はこれらの点をまとめたものです。

|実際のコンプライアンス状態|割り当てられた猶予期間の値|有効なコンプライアンス状態|
|---------|---------|---------|
|NonCompliant |猶予期間が割り当てられていない |NonCompliant |
|NonCompliant |昨日の日付|NonCompliant|
|NonCompliant |明日の日付|InGracePeriod|

デバイスのコンプライアンス ポリシーの監視の詳細については、「[Intune デバイス コンプライアンス対応ポリシーの監視](compliance-policy-monitor.md)」を参照してください。

### <a name="assign-a-resulting-compliance-policy-status"></a>コンプライアンス ポリシーの結果の状態を割り当てる

デバイスに複数のコンプライアンス ポリシーがあり、デバイスの 2 つ以上の割り当て済みコンプライアンス ポリシーが異なるコンプライアンス状態になっている場合、1 つの結果のコンプライアンス状態が割り当てられます。 この割り当ては、各コンプライアンス状態に割り当てられている概念的な重大度レベルを基にしています。 各コンプライアンス状態には、次の重大度レベルがあります。

|状態  |重大度  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|準拠|3|
|InGracePeriod|4|
|NonCompliant|5|
|エラー|6|

デバイスに複数のコンプライアンス ポリシーがある場合、すべてのポリシーの最も高い重大度がそのデバイスに割り当てられます。

たとえば、デバイスに 3 つのコンプライアンス ポリシーが割り当てられていて、1 つが不明状態 (重大度 = 1)、1 つが準拠状態 (重大度 = 3)、1 つが InGracePeriod 状態 (重要度 = 4) であるとします。 この中で重大度レベルが最も高いのは、InGracePeriod 状態です。 したがって、3 つのポリシーすべてのコンプライアンス状態が InGracePeriod となります。

## <a name="next-steps"></a>次の手順

[ポリシーを監視します](compliance-policy-monitor.md)。