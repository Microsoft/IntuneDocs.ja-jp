---
title: Intune の Android デバイスの暗号化 |Microsoft Docs
description: Intune で必要な場合に、Android デバイスの暗号化を有効にする手順
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545251"
---
# <a name="encrypting-your-android-device"></a>Android デバイスの暗号化

デバイスの暗号化保護ファイルとフォルダーを不正アクセスからデバイスが紛失または盗難にあった場合します。 デバイスの暗号化を有効にすると、正しいパスワードまたは pin でのユーザーのみは同じデバイスにサインインすることができます。 

学校または会社のリソースにアクセスする前に、組織は、Android デバイスを暗号化する必要があります。 既定では、一部の新しい Android デバイスで暗号化ボックスの。  

## <a name="turn-on-encryption"></a>暗号化を有効にします。

ポータル サイトまたは Microsoft Intune のアプリ、デバイスの暗号化を求め、られる場合は、次の手順を完了します。 

> [!Note]
> Huawei、Vivo および OPPO から特定の Android デバイスを暗号化することはできません。 詳細については、[こちら](your-device-appears-encrypted-but-cp-says-otherwise-android.md)を参照してください。  

1. デバイスの画面のロックを設定します。  
    」を参照します。 **[設定]**  >  **[ロック画面とセキュリティ]**  >  **[Screen lock type]\(画面のロックの種類\)** に移動します。  
    b. いずれかを選択**PIN**、**パスワード**、または**パターン**します。  
    c. 画面のロックを構成するのには、画面の指示に従います。  

2. 戻り**ロック画面とセキュリティ**選択**安全な起動**します。
3. 選択**デバイスをオンに PIN を必要と** > **OK**します。
4. 確認し、デバイスの暗号化、PIN を入力します。
5. ポータル サイトまたは Microsoft Intune のアプリを開きます。
    * ポータル サイトのユーザー: デバイスを選択し、 **[デバイス設定の確認]** をタップします。 
    * Microsoft Intune のユーザー: ページの更新プログラムまで待機する必要がありますが、するときに準拠している暗号化の状態を変更する必要があります。  

Android 4.4 以降を実行しているデバイスがない、 **Secure startup**オプション。 その場合は、デバイスを暗号化するには、次の手順を完了します。

1. 移動して**設定** > **セキュリティ** > **デバイスを暗号化**します。 Android デバイスで画面に表示されるラベルは異なります。 表示されない場合、**デバイスの暗号化**オプションで確認してください。
    * **記憶域** > **ストレージの暗号化**
    * **記憶域** > **ロック画面とセキュリティ** > **他のセキュリティ設定** 

2. 画面の指示に従います。 暗号化中、デバイスが何度か再起動する可能性があります。
3. ポータル サイトまたは Microsoft Intune のアプリを開きます。
    * ポータル サイトのユーザー: デバイスを選択し、 **[デバイス設定の確認]** をタップします。  
    * Microsoft Intune のユーザー: ページの更新プログラムまで待機する必要がありますが、するときに準拠している暗号化の状態を変更する必要があります。

## <a name="troubleshoot"></a>トラブルシューティング  
**問題**: デバイスが既に暗号化されていると

- 暗号化ボタンが無効です。
- 暗号化が必要であるというメッセージが引き続き表示されます。
- ポータル サイトまたは Microsoft Intune のアプリを使用しようとするときにエラーが発生します。

**対処方法**

- デバイスが課金され、接続されていることを確認します。  
- デバイスで PIN やパスワードが設定されていることを確認します。  

サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。  
