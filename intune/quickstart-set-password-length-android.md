---
title: クイック スタート - Android デバイスに必要なパスワードの長さを設定する
titlesuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して Android デバイスに必要なパスワードの長さを設定します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395286"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>クイック スタート: Android デバイスに必要なパスワードの長さを設定する

このクイック スタートでは、Microsoft Intune を使用して、従業員の Android ユーザーに対し、Android デバイスでの情報へのアクセスを許可する前に、特定の長さのパスワードが必要なように設定します。 

> [!IMPORTANT]
> パスワードの設定だけでなく、従業員を保護する他のシステム セキュリティ設定も考慮する必要があります。 詳しくは、「[システム セキュリティ設定](compliance-policy-create-android-for-work.md#system-security-settings)」をご覧ください。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune には、Azure portal で **[すべてのサービス]** > **[Intune]** を選択してアクセスします。 Intune は **[監視 + 管理]** セクションにあります。

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成
1. **Microsoft Intune** ブレードを開いたら、**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** の順に選択します。
2. 「**Android compliance**」という **[名前]** を追加します。 **[説明]** も追加します。
3. **[プラットフォーム]** で、**[Android]** を選択します。 
4. **[設定]** > **[システム セキュリティ]** を選択し、Android の **[システム セキュリティ]** ブレードを表示します。
5. **[パスワード]** セクションで、**[モバイル デバイスのロック解除にパスワードを必要とする]** の横の **[必要]** をクリックします。
6. **[パスワードの最小文字数]** に「**6**」と入力します。  

    ![Microsoft Intune でのグループ作成のスクリーンショット](./media/quickstart-set-password-length-android-01.png)

7. 完了したら、**[OK]** をクリックして **[システム セキュリティ]** ブレードを閉じます。 
8. **[OK]** をクリックして、**[Android コンプライアンス ポリシー]** ブレードを閉じます。 
9. **[作成]** をクリックして、ポリシーを作成します。

ポリシーが正常に作成されると、**[デバイスのポリシー準拠 - ポリシー]** の一覧に表示されます。 

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、6 文字以上の長さのパスワードが必要なように、従業員の Android デバイス用のコンプライアンス ポリシーを作成しました。

> [!div class="nextstepaction"]
> [自動登録を設定する](quickstart-setup-auto-enrollment.md)
