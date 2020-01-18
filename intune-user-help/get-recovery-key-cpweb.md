---
title: Intune ポータルサイト web サイトから macOS デバイスの回復キーを取得する
description: 登録済みの管理された macOS デバイスの回復キーを表示します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 1e7831712b4c07d015aa0f587ff6ba6183940897
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855238"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>MacOS デバイスの回復キーを取得する

ポータルサイトの web サイトを使用して、ロックされた macOS デバイスの回復キーを取得します。 デバイスのパスワードを忘れた場合は、別のデバイスからポータルサイトにサインインして、キーを取得することができます。  

## <a name="get-recovery-key-from-company-portal-website"></a>ポータルサイト web サイトから回復キーを取得する

このオプションは、FileVault を使用して組織で暗号化されたデバイスで使用できます。 個人で暗号化したデバイスでは使用できません。

1. 任意のデバイスで、[ポータルサイトの web サイト](https://portal.manage.microsoft.com)にサインインし、[**デバイス** **] > メニュー**ボタンを選択します。  
2. 暗号化された macOS デバイスを選択します。  
3. **[回復キーを取得する]** を選択します。  

    ![[回復キーの取得] セクションを強調表示してポータルサイト web サイトのスクリーンショット。](./media/1907-recovery2-cpweb-intune.PNG)  

4. 回復キーが表示されます。

    ![回復キーが表示されているポータルサイト web サイトのスクリーンショット。](./media/1907-recovery-cpweb-intune.PNG)  

    セキュリティ上の理由から、キーは5分後に消去されます。 キーを再度表示するには、 **[回復キーの取得]** を選択します。

キーが見つからず、デバイスが適切に暗号化されている場合は、組織のサポート担当者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>IOS 用ポータルサイトアプリから回復キーを取得する

IOS 用ポータルサイトアプリを使用して、個人の回復キー (FileVault キー) を取得できます。 個人用回復キーを持つデバイスは、Intune に登録され、Intune 経由で FileVault を使用して暗号化する必要があります。 このオプションは、個人が暗号化したデバイスでは使用できません。 

ポータルサイトアプリを使用して、Safari web ビューを開き、個人の回復キーを取得することができます。 

1. ポータル サイトを開きます。
2. **[回復キーの取得]** をクリックします。

    ![回復キーが表示されている iOS 用ポータルサイトアプリのスクリーンショット](./media/get-recovery-key-cpweb-02.png)  

Safari web ビューでポータルサイト web サイトが開き、キーが表示されます。 

## <a name="it-pro-support"></a>IT プロフェッショナルサポート

IT サポート担当者であり、macOS デバイスの FileVault 暗号化を構成して管理する場合は、「 [Intune でデバイスの暗号化を使用](/intune/protect/encrypt-devices)する」を参照してください。

## <a name="next-steps"></a>次のステップ

ポータルサイトの web サイトから他に何ができるかを確認してください。 アクションの一覧については[、「Intune ポータルサイト web サイトの使用](using-the-intune-company-portal-website.md)」を参照してください。  

サポートが必要な場合は、 IT サポート担当者にお問い合わせください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。  
