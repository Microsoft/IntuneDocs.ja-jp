---
title: チュートリアル - EMM とアプリ構成に Intune を使用するように Slack を構成する
titleSuffix: Microsoft Intune
description: このチュートリアルでは、EMM とアプリ構成に Intune を使用するように Slack を構成します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3b01c1444b44e3f5c66fc129f78f321c9c9f5aa
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563397"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>チュートリアル: EMM とアプリ構成に Intune を使用するように Slack を構成する

Slack は、Microsoft Intune と共に使用できるコラボレーション アプリです。   

このチュートリアルでは次のことを行います。
> [!div class="checklist"]
> - Slack Enterprise Grid 上で Enterprise Mobility Management (EMM) プロバイダーとして Intune を設定します。 Grid プランのワークスペースへのアクセスを Intune マネージド デバイスに制限することができます。
> - iOS 上の Slack for EMM アプリと Android 仕事用プロファイル デバイス用 Slack アプリを管理するためのアプリ構成ポリシーを作成します。
> - Intune デバイス コンプライアンス ポリシーを作成して、Android および iOS デバイスが準拠済みと見なされるために満たす必要のある条件を設定します。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件
このチュートリアルでは、次のサブスクリプションのあるテスト テナントが必要です。
- Azure Active Directory Premium ([無料試用版](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune サブスクリプション ([無料試用版](../fundamentals/free-trial-sign-up.md))

また、[Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-) プランも必要です。

## <a name="configure-your-slack-enterprise-grid-plan"></a>Slack Enterprise Grid プランを構成する
[Slack の指示](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm)に従って Slack Enterprise Grid プランに対して EMM を有効にして、Grid プランの ID プロバイダー (IDP) として [Azure Active Directory に接続](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする
グローバル管理者または Intune サービス管理者として [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="set-up-slack-for-emm-on-ios-devices"></a>iOS デバイス上で Slack for EMM を設定する
iOS アプリの Slack for EMM を Intune テナントに追加し、組織の iOS ユーザーが EMM プロバイダーとして Intune を使用して Slack にアクセスできるようにするアプリ構成ポリシーを作成します。

### <a name="add-slack-for-emm-to-intune"></a>Intune に Slack for EMM を追加する
Intune でマネージド iOS アプリとして Slack for EMM を追加し、Slack ユーザーを割り当てます。 アプリはプラットフォーム固有なので、Android デバイス上の Slack ユーザーには別の Intune アプリを追加する必要があります。
1. Intune で、 **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** を選択します。
2. [アプリの種類] で、 **[ストア アプリ - iOS]** を選択します。
3. **[アプリ ストアを検索します]** を選びます。 検索語句「Slack for EMM」を入力してアプリを選択します。
4. **[アプリ情報]** を選択し、必要に応じて変更を構成します。
5. **[追加]** を選択します。
6. 検索バーに「Slack for EMM」と入力し、先ほど追加したアプリを選択します。
7. [管理] から **[割り当て]** を選択します。
8. **[グループの追加]** を選択します。 EMM for Slack を有効にしたときに影響を受ける対象として選択したユーザーに応じて、 **[割り当ての種類]** で次を選択することができます。
    - [All members (including guests)]\(すべてのメンバー (ゲストを含む)\) を選択した場合は **[登録済みデバイスで使用可能]** 、または
    - [All members (excluding guests)]\(すべてのメンバー (ゲストを除く)\) または [省略可能] を選択した場合は **[登録の有無にかかわらず使用可能]** 。
9. **[組み込まれたグループ]** を選択し、[すべてのユーザーがこのアプリを使用できるようにします] で **[はい]** を選択します。
10. **[OK]** をクリックし、再度 **[OK]** をクリックします。
11. **[Save]** (保存) をクリックします。

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Slack for EMM のアプリ構成ポリシーを追加する
Slack for EMM iOS のアプリ構成ポリシーを追加する マネージド デバイスのアプリ構成ポリシーはプラットフォーム固有なので、Android デバイス上の Slack ユーザーには別のポリシーを追加する必要があります。
1. Intune で、 **[アプリ]**  >  **[アプリ構成ポリシー]**  >  **[追加]** を選択します。
2. [名前] に「Slack app configuration policy test」と入力します。
3. [デバイス登録の種類] で **[マネージド デバイス]** を選択します。
4. [プラットフォーム] で **[iOS]** を選択します。
5. **[関連アプリ]** を選択します。
6. 検索バーに「Slack for EMM」と入力し、アプリを選択します。
7. **[OK]** をクリックし、 **[構成設定]** を選択します。 
8. **[OK]** を選択し、 **[追加]** を選択します。
9. 検索バーに「Slack app configuration policy test」と入力して、先ほど追加したポリシーを選択します。
10. [管理] から **[割り当て]** を選択します。
11. [割り当て先] で、 **[すべてのユーザーとすべてのデバイス]** を選択します。
12. **[Save]** (保存) をクリックします。

### <a name="optional-create-an-ios-device-compliance-policy"></a>(省略可能) iOS デバイスのコンプライアンス ポリシーを作成する
Intune デバイス コンプライアンス ポリシーを設定して、デバイスが準拠済みと見なされるために満たす必要のある条件を設定します。 このチュートリアルでは、iOS デバイス用のデバイス コンプライアンス ポリシーを作成します。 コンプライアンス ポリシーはプラットフォーム固有なので、Android デバイス上の Slack ユーザーには別のポリシーを作成する必要があります。
1. Intune で、 **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]** の順に選択します。
2. [名前] に「iOS compliance policy test」と入力します。
3. [説明] に「iOS compliance policy test」と入力します。
4. [プラットフォーム] で **[iOS]** を選択します。
5. **[デバイスの正常性]** を選択します。 [脱獄されたデバイス] の隣の **[ブロックする]** を選択して、 **[OK]** を選択します。
6. **[システム セキュリティ]** を選択して、[パスワード] の設定を入力します。 このチュートリアルでは、次の推奨設定を選択します。
    - [モバイル デバイスのロック解除にパスワードを必要とする] で、 **[必要]** を選択します。
    - [単純なパスワード] で、 **[ブロックする]** を選択します。
    - [パスワードの最小文字数] に、「4」と入力します。
    - [必要なパスワードの種類] で、 **[英数字]** を選択します。
    - [画面ロック後にパスワードが要求されるまでの最長時間 (分)] で、 **[即時]** を選択します。
    - [パスワードの有効期限 (日数)] に、「41」と入力します。
    - [再使用を禁止するパスワード世代数] に、「5」と入力します。
7. **[OK]** を選択し、 **[OK]** をもう一度選択します。
8. **[作成]** をクリックします。

## <a name="set-up-slack-on-android-work-profile-devices"></a>Android 仕事用プロファイル デバイス上で Slack を設定する
Slack マネージド Google Play アプリを Intune テナントに追加し、組織の Android ユーザーが EMM プロバイダーとして Intune を使用して Slack にアクセスできるようにするアプリ構成ポリシーを作成します。

### <a name="add-slack-to-intune"></a>Slack を Intune に追加する
Intune でマネージド Google Play アプリとして Slack を追加し、Slack ユーザーを割り当てます。 アプリはプラットフォーム固有なので、iOS デバイス上の Slack ユーザーには別の Intune アプリを追加する必要があります。
1. Intune で、 **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** を選択します。
2. [アプリの種類] で **[ストア アプリ - マネージド Google Play]** を選択します。
3. **[マネージド Google Play - 承認]** を選択します。 検索語句「Slack for EMM」を入力してアプリを選択します。
4. **[承認]** を選択します。
5. 検索バーに「Slack」と入力し、先ほど追加したアプリを選択します。
6. [管理] から **[割り当て]** を選択します。
7. **[グループの追加]** を選択します。 EMM for Slack を有効にしたときに影響を受ける対象として選択したユーザーに応じて、 **[割り当ての種類]** で次を選択することができます。
    - [All members (including guests)]\(すべてのメンバー (ゲストを含む)\) を選択した場合は **[登録済みデバイスで使用可能]** 、または
    - [All members (excluding guests)]\(すべてのメンバー (ゲストを除く)\) または [省略可能] を選択した場合は **[登録の有無にかかわらず使用可能]** 。
8. [組み込まれたグループ] を選択し、[すべてのユーザーがこのアプリを使用できるようにします] で **[はい]** を選択します。
9. **[OK]** をクリックし、再度 **[OK]** をクリックします。
10. **[Save]** (保存) をクリックします。

### <a name="add-an-app-configuration-policy-for-slack"></a>Slack のアプリ構成ポリシーを追加する
Slack のアプリ構成ポリシーを追加します。 マネージド デバイスのアプリ構成ポリシーはプラットフォーム固有なので、iOS デバイス上の Slack ユーザーには別のポリシーを追加する必要があります。
1. Intune で、 **[アプリ]**  >  **[アプリ構成ポリシー]**  >  **[追加]** を選択します。
2. [名前] に「Slack app configuration policy test」と入力します。
3. [デバイス登録の種類] で **[マネージド デバイス]** を選択します。
4. [プラットフォーム] で、 **[Android]** を選択します。
5. **[関連アプリ]** を選択します。
6. 検索バーに「Slack」と入力し、アプリを選択します。
7. **[OK]** を選択し、 **[構成設定]** を選択します。
    - 構成キーとその値については、[Slack の AppConfig Web ページ](https://www.appconfig.org/company/slack/) の「Technical (技術)」タブにあるドキュメントを参照してください。
8. **[OK]** をクリックし、 **[追加]** を選択します。
9. 検索バーに「Slack app configuration policy test」と入力して、先ほど追加したポリシーを選択します。
10. [管理] から **[割り当て]** を選択します。
11. [割り当て先] で、 **[すべてのユーザーとすべてのデバイス]** を選択します。
12. **[Save]** (保存) をクリックします。

### <a name="optional-create-an-android-device-compliance-policy"></a>(省略可能) Android デバイスのコンプライアンス ポリシーを作成する
Intune デバイス コンプライアンス ポリシーを設定して、デバイスが準拠済みと見なされるために満たす必要のある条件を設定します。 このチュートリアルでは、Android デバイス用のデバイス コンプライアンス ポリシーを作成します。 コンプライアンス ポリシーはプラットフォーム固有なので、iOS デバイス上の Slack ユーザーには別のポリシーを作成する必要があります。
1. Intune で、 **[デバイスのポリシー準拠]**  >  **[ポリシー]**  >  **[ポリシーの作成]** の順に選択します。
2. [名前] に「Android compliance policy test」と入力します。
3. [説明] に「Android compliance policy test」と入力します。
4. [プラットフォーム] で、 **[Android エンタープライズ]** を選択します。
5. [プロファイルの種類] で、 **[仕事用プロファイル]** を選択します。
6. **[デバイスの正常性]** を選択します。 [ルート化されたデバイス] の隣の **[ブロックする]** を選択して、 **[OK]** を選択します。
7. **[システム セキュリティ]** を選択して、 **[パスワード]** の設定を入力します。 このチュートリアルでは、次の推奨設定を選択します。
    - [モバイル デバイスのロック解除にパスワードを必要とする] で、 **[必要]** を選択します。
    - [必要なパスワードの種類] の **[最小数の英数字]** を選択します。
    - [パスワードの最小文字数] に、「4」と入力します。
    - [画面ロック後にパスワードが要求されるまでの最長時間 (分)] で、 **[15 分]** を選択します。
    - [パスワードの有効期限 (日数)] に、「41」と入力します。
    - [再使用を禁止するパスワード世代数] に、「5」と入力します。
8. **[OK]** をクリックし、再度 **[OK]** をクリックします。
9. **[作成]** をクリックします。

## <a name="launch-slack"></a>Slack を起動する

先ほど作成したポリシーでは、いずれかのワークスペースにサインインを試行した iOS または Android の仕事用プロファイル デバイスを Intune に登録する必要があります。 このシナリオをテストするには、Intune に登録された iOS デバイス上で Slack for EMM を起動するか、Intune に登録された Android 仕事用プロファイル デバイスで Slack を起動してみます。 

## <a name="next-steps"></a>次の手順

このチュートリアルの内容:
- Slack Enterprise Grid 上で Enterprise Mobility Management (EMM) プロバイダーとして Intune を設定しました。 
- iOS 上の Slack for EMM アプリと Android 仕事用プロファイル デバイス用 Slack アプリを管理するためのアプリ構成ポリシーを作成しました。
- Intune デバイス コンプライアンス ポリシーを作成して、Android および iOS デバイスが準拠済みと見なされるために満たす必要のある条件を設定しました。

アプリ構成ポリシーの詳細については、「[Microsoft Intune 用アプリ構成ポリシー](app-configuration-policies-overview.md)」を参照してください。 デバイス コンプライアンス ポリシーの詳細については、「[Intune を使用して組織内のリソースへのアクセスを許可するように、デバイス上でルールを設定する](../protect/device-compliance-get-started.md)」を参照してください。
