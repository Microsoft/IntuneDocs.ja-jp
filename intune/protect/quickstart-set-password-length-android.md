---
title: クイック スタート - Android デバイス用のパスワード コンプライアンス ポリシー
titleSuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して Android デバイスに必要なパスワードの長さを設定します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61fdf91d57ce5d187a0c43153f317b0b42c6b46c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409776"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>クイック スタート:Android デバイス用のパスワード コンプライアンス ポリシーを作成する

このクイック スタートでは、Microsoft Intune を使用して、従業員の Android ユーザーに対し、Android デバイスでの情報へのアクセスを許可する前に、特定の長さのパスワードが必要なように設定します。

Intune デバイス コンプライアンス ポリシーでは、準拠しているものと見なされるためにデバイスが満たす必要のあるルールと設定を指定します。 コンプライアンス ポリシーを条件付きアクセスと一緒に使用することにより、会社のリソースへのアクセスを許可または阻止することができます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。

> [!IMPORTANT]
> パスワードの設定だけでなく、従業員を保護する他のシステム セキュリティ設定も考慮する必要があります。 詳しくは、「[システム セキュリティ設定](compliance-policy-create-android-for-work.md)」をご覧ください。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

[全体管理者](../fundamentals/users-add.md#types-of-administrators)または Intune [サービス管理者](../fundamentals/users-add.md#types-of-administrators)として、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成

従業員の Android ユーザーに対し、Android デバイス上の情報へのアクセスを許可する前に、特定の長さのパスワードを入力するよう求めるデバイス コンプライアンス ポリシーを作成します。

1. Intune で、 **[デバイス]**  >  **[コンプライアンス ポリシー]**  >  **[ポリシーの作成]** の順に選択します。

2. 「**Android compliance**」という **[名前]** を追加します。 **[説明]** も追加します。

3. **[プラットフォーム]** に、 **[Android エンタープライズ]** を選択します。

4. **[プロファイルの種類]** には **[仕事用プロファイル]** を選択します。

5. **[設定]**  >  **[システム セキュリティ]** を選択し、Android の **[システム セキュリティ]** ブレードを表示します。

6. **[モバイル デバイスのロック解除にパスワードを必要とする]** で、 **[必要]** を選択します。

7. **[必要なパスワードの種類]** には **[最小数の英数字]** を選択します。

8. **[パスワードの最小文字数]** には「**6**」と入力します。

    ![Microsoft Intune でのグループ作成のスクリーンショット](./media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

9. 終わったら、 **[OK]** 、 **[OK]** 、 **[作成]** の順に選択し、ポリシーを作成します。

ポリシーが正常に作成されると、デバイス コンプライアンス ポリシーの一覧に表示されます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

不要になったら、ポリシーを削除します。 そのためには、コンプライアンス ポリシーを選択して、 **[削除]** をクリックします。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、6 文字以上の長さのパスワードが必要なように、従業員の Android デバイス用のコンプライアンス ポリシーを作成しました。 コンプライアンス ポリシーの作成について詳しくは、「[Intune のデバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: 非準拠デバイスへの通知の送信](../quickstart-send-notification.md)
