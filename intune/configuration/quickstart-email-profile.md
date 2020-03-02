---
title: クイック スタート - iOS/iPadOS デバイス用の電子メール デバイス プロファイルを作成する
titleSuffix: Microsoft Intune
description: iOS/iPadOS デバイスが会社の電子メールに安全に接続できるように、Microsoft Intune を使用して電子メール デバイス プロファイルを作成する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af2576c44e0486dbd859a56896db3b7d0ffc6cff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511070"
---
# <a name="quickstart-create-an-email-device-profile-for-iosipados"></a>クイック スタート:iOS/iPadOS 用の電子メール デバイス プロファイルを作成する

このクイック スタートでは、iOS/iPadOS デバイス用の電子メール デバイス プロファイルを作成する方法を確認します。 このプロファイルでは、iOS/iPadOS デバイス上の組み込みの電子メール アプリが会社の電子メールに接続するために必要な設定を指定します。 電子メール デバイス プロファイルは、デバイス間で設定を標準化するのに役立ちます。これにより、エンドユーザーは自分自身では何も設定する必要なく、個人のデバイスで会社の電子メールにアクセスできます。 電子メールの保護をさらに強化するには、電子メール プロファイルを使用してデバイスが準拠しているかどうかを判断し、準拠しているデバイスのみが電子メールにアクセスできるように、条件付きアクセスを設定します。 電子メール プロファイルの詳細については、「[Microsoft Intune で電子メールの設定を構成する方法](email-settings-configure.md)」を参照してください。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

全体管理者または Intune サービス管理者として、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="create-an-iosipados-email-profile"></a>iOS/iPadOS 電子メール プロファイルを作成する

1. **[デバイス]**  >  **[構成プロファイル]**  >  **[プロファイルの作成]** の順に選択します。

   ![Intune で iOS/iPadOS 用の電子メール プロファイルを作成する](./media/quickstart-email-profile/ios-create-profile.png)

2. **[名前]** に、新しいプロファイルのわかりやすい名前を入力します。 この例では、「**iOS で職場の電子メールが必要**」と入力します。
3. 次のプロファイル情報を入力します。
    - **[説明]** に、「**職場の電子メールを使用する iOS/iPadOS デバイスが必要**」と入力とします。
    - **[プラットフォーム]** で **[iOS/iPadOS]** を選択します。
    - **[プロファイルの種類]** で、 **[電子メール]** を選択します。

        ![Intune で、iOS/iPadOS デバイスで使用するための電子メール プロファイルを作成する](./media/quickstart-email-profile/ios-email-profile-name.png)

4. **[設定]** を選択し、次の設定を入力します (その他の設定は既定値のままにします)。
   - **[電子メール サーバー]** :このクイック スタートでは、「**outlook.office365.com**」と入力します。 この設定では、iOS/iPadOS のメール アプリが電子メールへの接続に使用する電子メール サーバーの Exchange の場所 (URL) を指定します。
   - **[アカウント名]** :**会社の電子メール**を入力します。
   - **[AAD からのユーザー名の属性]** :Intune が Azure Active Directory (Azure AD) から取得する名前。 Intune では、この名前を使用してこのプロファイルのユーザー名を動的に生成します。 このクイック スタートでは、プロファイルのユーザー名として **[ユーザー プリンシパル名]** (たとえば、user1@contoso.com) を使用すると仮定します。
   - **[AAD からのメール アドレス属性]** :この設定は、Exchange へのサインインに使用する Azure AD からの電子メール アドレスです。 このクイック スタートでは、 **[ユーザー プリンシパル名]** を選択します。
   - **[認証方法]** :このクイック スタートでは、 **[ユーザー名とパスワード]** を選択します (Intune に証明書を既に設定している場合は、 **[証明書]** を選択することもできます)。

        ![iOS/iPadOS で使用するための電子メール プロファイルを作成する](./media/quickstart-email-profile/ios-email-profile.png)

5. **[OK]**  >  **[作成]** を選択します。 プロファイルの一覧に、ダッシュボードが表示された状態で新しいプロファイルが表示されます。これにより、プロファイルが iOS/iPadOS デバイスおよび iOS/iPadOS ユーザーにどのように割り当てられているかを監視できます。
6. **[割り当て]** を選択します。
7. **[含める]** タブを選択し、 **[すべてのユーザー] と [すべてのデバイス]** を選択します。 
8. **[保存]** を選択します。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

追加のチュートリアルまたはテスト用に作成したプロファイルを使用しない場合は、ここで削除できます。

1. Intune で **[デバイス構成]** を選択し、 **[プロファイル]** を選択します。
2. 作成したテスト プロファイル "**iOS/iPadOS で職場の電子メールが必要**" を選択します。
3. プロファイルの隣にある省略記号 ( **...** ) を選択し、 **[削除]** を選択します。

## <a name="next-steps"></a>次のステップ

このクイック スタートでは、iOS/iPadOS デバイス用の電子メール プロファイルを作成しました。 ここで、このプロファイルを使用して、プロファイルと一致しないすべての iOS/iPadOS デバイスを非準拠としてマークするコンプライアンス ポリシーを作成することで、iOS/iPadOS デバイスが準拠しているかどうかを判断することができます。 保護をさらに強化するには、非準拠の iOS/iPadOS デバイスが電子メールにアクセスできないようブロックする条件付きアクセス ポリシーを作成します。 デバイス コンプライアンス ポリシーの詳細については、[Intune でのデバイス コンプライアンス ポリシーの概要](../protect/device-compliance-get-started.md)に関するページを参照してください。

> [!div class="nextstepaction"]
> [チュートリアル:マネージド デバイス上で Exchange Online の電子メールを保護する](../tutorial-protect-email-on-enrolled-devices.md)
