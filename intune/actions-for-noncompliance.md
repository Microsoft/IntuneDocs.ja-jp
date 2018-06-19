---
title: Microsoft Intune でのコンプライアンス違反メッセージとアクション - Azure | Microsoft Docs
description: コンプライアンス違反デバイスに送信するメール通知を作成します。 準拠するまでの猶予期間の追加や、デバイスが準拠するまでアクセスをブロックするスケジュールの作成など、デバイスがコンプライアンス違反としてマークされた後のアクションを追加します。 これらの作業は、Azure で Microsoft Intune を使って行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e8603ca59b46937b1529e710a8bc83aec5dd4d6
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
ms.locfileid: "32017959"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>コンプライアンス違反デバイスに対する自動メール送信とアクションの追加 - Intune

時間順のアクションを構成する**コンプライアンス違反に対するアクション**機能があります。 これらのアクションは、コンプライアンス ポリシーを満たしていないデバイスに適用されます。 

## <a name="overview"></a>概要
既定では、Intune は、準拠していないデバイスを検出すると、直ちにコンプライアンス違反としてマークします。 その後、Azure Active Directory (AD) の[条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)がデバイスをブロックします。 デバイスがコンプライアンスに違反している場合、**コンプライアンス違反に対するアクション**を使って対処方法を柔軟に決定することもできます。 たとえば、デバイスをすぐにブロックしないで、ユーザーにコンプライアンスに対応するための猶予時間を与えたりすることができます。

アクションには 2 つの種類があります。

- **メールでエンド ユーザーに通知する**: エンド ユーザーに送信する前に、メール通知をカスタマイズすることができます。 受信者、件名、メッセージ本文のほか、会社のロゴ、連絡先情報をカスタマイズできます。

    さらに、メール通知にはコンプライアンス違反デバイスについての詳細が含まれます。

- **デバイスにコンプライアンス違反のマークを付ける**: デバイスをコンプライアンス違反としてマークするまでのスケジュール (日数) を作成できます。 このアクションが即時有効になるように構成することも、コンプライアンス対応にするまでの猶予期間を設定することもできます。

## <a name="before-you-begin"></a>始める前に

- コンプライアンス違反に対するアクションを設定するには、少なくとも 1 つのデバイス コンプライアンス ポリシーが必要です。 デバイス コンプライアンス ポリシーの作成については、以下のプラットフォームをご覧ください。

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- デバイス コンプライアンス ポリシーを使ってデバイスを企業リソースからブロックする場合は、Azure AD の条件付きアクセスを設定する必要があります。 詳しくは、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」をご覧ください。

- 通知メッセージ テンプレートを作成する必要があります。 ユーザーにメールを送信するには、このテンプレートを使って、コンプライアン違反に対するアクションを作成します。

## <a name="create-a-notification-message-template"></a>通知メッセージ テンプレートを作成する

1. ご自分の Intune 資格情報で [Azure Portal](https://portal.azure.com) にサインインします。 
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイスのポリシー準拠]** を選択してから、**[通知]** を選択します。 
4. **[通知の作成]** を選択し、次の情報を入力します。

   - 名前
   - サブジェクト
   - メッセージ
   - 電子メール ヘッダー – 会社のロゴを含める
   - 電子メール フッター – 会社名を含める
   - 電子メール フッター – 連絡先情報を含める

   ![Intune でのコンプライアンス準拠通知メッセージの例](./media/actionsfornoncompliance-1.PNG)

情報の追加が完了したら、**[作成]** を選択します。 通知メッセージ テンプレートが使用できるようになります。

> [!NOTE]
> また、以前に作成した通知テンプレートを編集することもできます。

## <a name="add-actions-for-noncompliance"></a>コンプライアンス違反に対するアクションを追加する

既定では、Intune がコンプライアンス違反のアクションを自動的に作成します。 デバイスがコンプライアンス ポリシーを満たしていない場合、このアクションがデバイスをコンプライアンス違反としてマークします。 デバイスがコンプライアンス違反としてマークされるまでの期間をカスタマイズできます。 このアクションを削除することはできません。

アクションを追加できるのは、新しいコンプライアンス ポリシーを作成するとき、または既存のコンプライアンス ポリシーを更新するときです。 

1. [Azure Portal](https://portal.azure.com) で **[Microsoft Intune]** を開き、**[デバイスのポリシー準拠]** を選択します。
2. **[ポリシー]** を選択し、ポリシーのいずれかを選択して、**[プロパティ]** を選択します。 

  ポリシーがまだない場合は、 [Android](compliance-policy-create-android.md)、[iOS](compliance-policy-create-ios.md)、[Windows](compliance-policy-create-windows.md)、または他のプラットフォーム用のポリシーを作成します。
  
  > [!NOTE]
  > JAMF デバイスと、デバイス グループを対象とするデバイスは、現時点ではコンプライアンス アクションを受け取ることができません。

3. **[コンプライアンス非対応に対するアクション]** を選択し、**[追加]** を選択してアクションのパラメーターを入力します。 以前に作成したメッセージ テンプレートの選択、新しい受信者の追加、猶予期間のスケジュールの更新を行うことができます。 スケジュールで日数 (0 - 365) を入力して、条件付きアクセス ポリシーを強制的に適用することができます。 日数を **0** にすると、条件付きアクセスは**すぐに**企業リソースへのアクセスをブロックします。

4. 完了したら、**[追加]** > **[OK]** の順に選択して変更を保存します。

## <a name="next-steps"></a>次の手順
レポートを実行して、デバイスのコンプライアンス アクティビティを監視します。 詳しくは、[Intune でデバイス コンプライアンスを監視する方法](device-compliance-monitor.md)に関するページをご覧ください。
