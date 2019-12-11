---
title: Intune の Android デバイスを暗号化する |Microsoft Docs
description: Intune で必要なときに Android デバイスの暗号化を有効にする手順
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2965d6a017d92bd4535a29a2257c0cac5e6deaf
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506362"
---
# <a name="encrypting-your-android-device"></a>Android デバイスの暗号化

デバイスの暗号化は、デバイスが紛失または盗難にあった場合に、ファイルとフォルダーを不正アクセスから保護します。 デバイスの暗号化を有効にすると、正しいパスワードまたは pin を持つユーザーのみがデバイスにサインインできるようになります。 

学校や職場のリソースにアクセスする前に、組織で Android デバイスの暗号化が必要になる場合があります。 既定では、いくつかの新しい Android デバイスが既定で暗号化されています。  

## <a name="turn-on-encryption"></a>暗号化を有効にする

ポータルサイトまたは Microsoft Intune アプリからデバイスを暗号化するように求めるメッセージが表示された場合は、次の手順を実行します。 

> [!Note]
> Huawei、Vivo、OPPO からの特定の Android デバイスは暗号化できません。 詳細については、[こちら](your-device-appears-encrypted-but-cp-says-otherwise-android.md)を参照してください。  

1. デバイスの画面ロックを設定します。  
    」を参照します。 **[設定]**  >  **[ロック画面とセキュリティ]**  >  **[Screen lock type]\(画面のロックの種類\)** に移動します。  
    b. **PIN**、**パスワード**、または**パターン**のいずれかを選択します。  
    c. 画面の指示に従って画面のロックを構成します。  

2. **ロック画面とセキュリティ**に戻り、[セキュリティ**で保護されたスタートアップ**] を選択します。
3. **[デバイスの電源をオンにするときに PIN を必要とする]** を選択 > **OK**。
4. PIN を入力して、デバイスを確認し、暗号化します。
5. ポータルサイトまたは Microsoft Intune アプリを開きます。
    * ポータル サイトのユーザー: デバイスを選択し、 **[デバイス設定の確認]** をタップします。 
    * Microsoft Intune ユーザー: ページが更新されるまで待つ必要がありますが、その場合は、暗号化の状態が [対応] に変更されます。  

Android 4.4 以前を実行しているデバイスには、 **Secure startup**オプションがない可能性があります。 その場合は、次の手順を実行してデバイスを暗号化します。

1. **[設定]** [**セキュリティ** > **暗号化デバイス**] の > にアクセスします。 スクリーンラベルは、Android デバイスによって異なります。 **[デバイスの暗号化]** オプションが表示されない場合は、次のチェックボックスをオンにします。
    * **Storage** > **ストレージの暗号化**
    * **ストレージ** > **ロック画面とセキュリティ** > **その他のセキュリティ設定** 

2. 画面の指示に従います。 暗号化中、デバイスが何度か再起動する可能性があります。
3. ポータルサイトまたは Microsoft Intune アプリを開きます。
    * ポータル サイトのユーザー: デバイスを選択し、 **[デバイス設定の確認]** をタップします。  
    * Microsoft Intune ユーザー: ページが更新されるまで待つ必要がありますが、その場合は、暗号化の状態が [対応] に変更されます。

## <a name="troubleshoot"></a>トラブルシューティング  
**問題**: デバイスが既に暗号化されています。

- 暗号化ボタンが無効です。
- 暗号化が必要であるというメッセージが引き続き表示されます。
- ポータルサイトまたは Microsoft Intune アプリを使用しようとすると、エラーが発生します。

**対処方法**

- デバイスが課金され、接続されていることを確認します。  
- デバイスで PIN やパスワードが設定されていることを確認します。  

サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。  
