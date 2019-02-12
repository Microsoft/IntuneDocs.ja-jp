---
title: クイック スタート - iOS 用の電子メール デバイス プロファイルを作成する
titlesuffix: Microsoft Intune
description: iOS デバイスが会社の電子メールに安全に接続できるように、Microsoft Intune を使用して電子メール デバイス プロファイルを作成する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fbe3371d86d02247922c87680605c9ea3a1f4df
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845841"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>クイック スタート:iOS 用の電子メール デバイス プロファイルを作成する

このクイック スタートでは、iOS デバイス用の電子メール デバイス プロファイルを作成する方法を確認します。 このプロファイルでは、iOS デバイス上の組み込みの電子メール アプリが会社の電子メールに接続するために必要な設定を指定します。 電子メール デバイス プロファイルは、デバイス間で設定を標準化するのに役立ちます。これにより、エンドユーザーは自分自身では何も設定する必要なく、個人のデバイスで会社の電子メールにアクセスできます。 電子メールの保護をさらに強化するには、電子メール プロファイルを使用してデバイスが準拠しているかどうかを判断し、準拠しているデバイスのみが電子メールにアクセスできるように、条件付きアクセスを設定します。 電子メール プロファイルの詳細については、「[Microsoft Intune で電子メールの設定を構成する方法](email-settings-configure.md)」を参照してください。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。 Intune には、Azure portal で **[すべてのサービス]** > **[Intune]** を選択してアクセスします。

## <a name="create-an-ios-email-profile"></a>iOS 電子メール プロファイルを作成する
1. Intune で **[デバイス構成]** を選択し、**[プロファイル]** を選択します。
2. **[プロファイルの作成]** を選択します。
   
   ![iOS 用の電子メール プロファイルを作成する](media/quickstart-email-profile/ios-create-profile.png)

3. **[名前]** に、新しいプロファイルのわかりやすい名前を入力します。 この例では、「**iOS で職場の電子メールが必要**」と入力します。
4. 次のプロファイル情報を入力します。
   - **[説明]** に、「**職場の電子メールを使用する iOS デバイスが必要**」と入力とします。
   - **[プラットフォーム]** で **[iOS]** を選択します。
   - **[プロファイルの種類]** で、**[電子メール]** を選択します。
    
     ![iOS で使用するための電子メール プロファイルを作成する](media/quickstart-email-profile/ios-email-profile-name.png)

5. **[設定]** を選択し、次の設定を入力します (その他の設定は既定値のままにします)。
   - **[電子メール サーバー]**:このクイック スタートでは、「**outlook.office365.com**」と入力します。 この設定では、iOS のメール アプリが電子メールへの接続に使用する電子メール サーバーの Exchange の場所 (URL) を指定します。
   - **[アカウント名]**:**会社の電子メール**を入力します。
   - **[AAD からのユーザー名の属性]**:Intune が Azure Active Directory (Azure AD) から取得する名前。 Intune では、この名前を使用してこのプロファイルのユーザー名を動的に生成します。 このクイック スタートでは、プロファイルのユーザー名として **[ユーザー プリンシパル名]** (たとえば、user1@contoso.com) を使用すると仮定します。
   - **[AAD からのメール アドレス属性]**:この設定は、Exchange へのサインインに使用する Azure AD からの電子メール アドレスです。 このクイック スタートでは、**[ユーザー プリンシパル名]** を選択します。
   - **[認証方法]**:このクイック スタートでは、**[ユーザー名とパスワード]** を選択します (Intune に証明書を既に設定している場合は、**[証明書]** を選択することもできます)。
    
     ![iOS で使用する電子メール プロファイルを作成する](media/quickstart-email-profile/ios-email-profile.png)

6. **[OK]** を選択します。
7. **[作成]** を選択します。 プロファイルの一覧に、ダッシュボードが表示された状態で新しいプロファイルが表示されます。これにより、プロファイルが iOS デバイスおよび iOS ユーザーにどのように割り当てられているかを監視できます。
8. **[割り当て]** を選択します。
9. **[含める]** タブを選択し、**[すべてのユーザー] と [すべてのデバイス]** を選択します。 
10. **[保存]** を選択します。

## <a name="clean-up-resources"></a>リソースをクリーンアップする
追加のチュートリアルまたはテスト用に作成したプロファイルを使用しない場合は、ここで削除できます。
1. Intune で **[デバイス構成]** を選択し、**[プロファイル]** を選択します。
2. 作成したテスト プロファイル "**iOS で職場の電子メールが必要**" を選択します。
3. プロファイルの隣にある省略記号 (**...**) を選択し、**[削除]** を選択します。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、iOS デバイス用の電子メール プロファイルを作成しました。 ここで、このプロファイルを使用して、プロファイルと一致しないすべての iOS デバイスを非準拠としてマークするコンプライアンス ポリシーを作成することで、iOS デバイスが準拠しているかどうかを判断することができます。 保護をさらに強化するには、非準拠の iOS デバイスが電子メールにアクセスできないようブロックする条件付きアクセス ポリシーを作成します。 デバイス コンプライアンス ポリシーの詳細については、[Intune でのデバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)に関するページを参照してください。

> [!div class="nextstepaction"]
> [チュートリアル: マネージド デバイス上で Exchange Online の電子メールを保護する](tutorial-protect-email-on-enrolled-devices.md)
