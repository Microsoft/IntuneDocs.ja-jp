---
title: クイック スタート - Android デバイス用のパスワード コンプライアンス ポリシーを作成する
titlesuffix: Microsoft Intune
description: このクイック スタートでは、Microsoft Intune を使用して Android デバイスに必要なパスワードの長さを設定します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62ae0c7b9a00c3e07bb49261ca1a20bd5ef5db15
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57397271"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>クイック スタート:Android デバイス用のパスワード コンプライアンス ポリシーを作成する

このクイック スタートでは、Microsoft Intune を使用して、従業員の Android ユーザーに対し、Android デバイスでの情報へのアクセスを許可する前に、特定の長さのパスワードが必要なように設定します。 

Intune デバイス コンプライアンス ポリシーでは、準拠しているものと見なされるためにデバイスが満たす必要のあるルールと設定を指定します。 コンプライアンス ポリシーを条件付きアクセスと一緒に使用することにより、会社のリソースへのアクセスを許可または阻止することができます。 コンプライアンス違反に対して、デバイス レポートを取得したり、是正措置を取ったりすることもできます。

> [!IMPORTANT]
> パスワードの設定だけでなく、従業員を保護する他のシステム セキュリティ設定も考慮する必要があります。 詳しくは、「[システム セキュリティ設定](compliance-policy-create-android-for-work.md#system-security-settings)」をご覧ください。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。 

## <a name="create-a-device-compliance-policy"></a>デバイス コンプライアンス ポリシーの作成

このクイック スタートでは、Intune を使用して、従業員の Android ユーザーに対し、Android デバイスでの情報へのアクセスを許可する前に、特定の長さのパスワードが必要なように設定します。

1. Intune で、**[デバイスのポリシー準拠]** > **[ポリシー]** > **[ポリシーの作成]** の順に選択します。
2. 「**Android compliance**」という **[名前]** を追加します。 **[説明]** も追加します。
3. **[プラットフォーム]** で、**[Android]** を選択します。 
4. **[設定]** > **[システム セキュリティ]** を選択し、Android の **[システム セキュリティ]** ブレードを表示します。
5. **[モバイル デバイスのロック解除にパスワードを必要とする]** の **[必要]** をクリックします。
6. **[パスワードの最小文字数]** に「**6**」と入力します。 

    ![Microsoft Intune でのグループ作成のスクリーンショット](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. 終わったら、**[OK]** > **[OK]** > **[作成]** の順にクリックして、ポリシーを作成します。

ポリシーが正常に作成されると、デバイス コンプライアンス ポリシーの一覧に表示されます。 

## <a name="clean-up-resources"></a>リソースをクリーンアップする

不要になったら、ポリシーを削除します。 そのためには、コンプライアンス ポリシーを選択して、**[削除]** をクリックします。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Intune を使用して、6 文字以上の長さのパスワードが必要なように、従業員の Android デバイス用のコンプライアンス ポリシーを作成しました。 コンプライアンス ポリシーの作成について詳しくは、「[Intune のデバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)」をご覧ください。

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: 非準拠デバイスへの通知の送信](quickstart-send-notification.md)
