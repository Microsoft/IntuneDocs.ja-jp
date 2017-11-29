---
title: "Intune で Google Play Protect コンプライアンスを有効にする"
titleSuffix: Azure portal
description: "Android デバイス用のコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法について説明します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d610bc338c1bcf81ed3bc71f1357e001914c5877
ms.sourcegitcommit: 71e6e80b7370024624ce2e5fad1ca5b372975748
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>デバイスのコンプライアンス ポリシーを作成して Google Play Protect を有効にする方法

Android プラットフォーム用に新しいコンプライアンス ポリシーを作成して、Google Play Protect (GPP) コンプライアンスをチェックすることができます。

これらの設定を必要とするコンプライアンス ポリシーは、Android ユーザーまたはデバイスのグループを対象にすることができます。 デバイスでこれらの設定が有効になっていない場合は、コンプライアンスの対象にはなりません。

## <a name="create-a-compliance-policy"></a>コンプライアンス ポリシーの作成

1. Azure ポータルにサインインします。 **[その他のサービス]** > **[監視 + 管理]** + **[Intune]** の順に選択します。
2. **[グループの管理]** で **[デバイスのポリシー準拠]** を選択します。 
3. **[ポリシー]**、**[ポリシーを作成する]** を選択します。
4. **[ポリシー名]** と **[説明]** を入力します。
5. [プラットフォーム] に **[Android]** を選択します。
6. **[設定]** > **[デバイスの正常性]** を選択します。
7. **[Google Play Protect]** 設定を構成します。
8. [Google Play Protect] 設定が完了したら、**[セキュリティ]** および **[デバイスのプロパティ]** 設定を指定します。 終了したら、**[OK]** を選択します。

## <a name="configure-the-google-play-protect-settings"></a>Google Play Protect 設定を構成する

 - **Google Play 開発者サービスが構成されています**  
   Google Play 開発者サービス アプリがインストールされ、有効になっている必要があります。 Google Play 開発者サービスはセキュリティ更新プログラムを許可し、Google の認定デバイスの多くのセキュリティ機能に対してベースレベルの依存関係となっています。
 - **最新のセキュリティ プロバイダー**  
   最新のセキュリティ プロバイダーが既知の脆弱性からデバイスを保護できるようになっている必要があります。
 - **アプリの脅威のスキャン**  
   Android の **[アプリの確認]** 機能が有効になっている必要があります。
    > [!Note]  
    > 従来の Android プラットフォームでは、この機能はコンプライアンス設定です。 Intune では、デバイス レベルでこの設定が有効になっているかどうかのみを確認できます。 作業プロファイルがあるデバイス (従来の Android for Work) では、この設定は構成ポリシー設定として存在しています。 これにより、管理者はデバイスの設定を有効にできます。

    企業で、Android 作業プロファイルを使用する場合は、登録されているデバイスに対して **[アプリの脅威のスキャン]** を有効にできます。 デバイス プロファイルを作成し、システム セキュリティ設定を要求します。 詳細については、「[Microsoft Intune での Android for Work デバイスの制限設定](device-restrictions-android-for-work.md)」をご覧ください。

 - **SafetyNet デバイスの構成証明**  
   満たす必要がある SafetyNet デバイス構成証明の整合性のレベルを設定します。 レベルには、**[未構成]**、**[Check basic integrity]\(基本的な整合性のチェック\)**、**[Check basic integrity & certified devices]\(基本的な整合性と認定デバイスのチェック\)** があります。




## <a name="next-steps"></a>次のステップ

Intune のデバイス コンプライアンス ポリシーの詳細については、「[Intune のデバイス コンプライアンス ポリシーの概要](device-compliance-get-started.md)」をご覧ください。