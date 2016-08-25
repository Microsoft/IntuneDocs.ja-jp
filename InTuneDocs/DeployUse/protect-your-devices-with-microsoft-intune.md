---
title: "デバイスを保護する | Microsoft Intune"
description: "不正アクセスなどの脅威からのデバイス保護に Intune が役立つ方法のいくつかについて説明します。"
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c999a852b68762002ac94269e27ecbf46c8f9999
ms.openlocfilehash: 3318590eaedc6f0e96fb463dc016d5786eeb38fb


---

# Microsoft Intune でデバイスを保護する
デバイスを Intune の管理対象にした後は、無許可のアクセスやその他の脅威に対して保護されていることを確認します。 その目的に役立つ Intune の機能をいくつか示します。

> [!TIP]
> このトピックでは、デバイスのセキュリティ保護に役立つ Intune の機能の一部のみを紹介します。 たとえば、Intune ポリシーを使用すれば、パスワードの構成、暗号化設定、ハードウェア機能 (Bluetooth やデバイス カメラなど) など、さまざまなセキュリティ設定をデバイスで構成できます。 これらの設定の詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

## ユーザーがデバイスからロックアウトされるときにパスコードをリセットする
モバイル デバイス上の会社のデータを保護する最初のステップは、デバイスの使用に対してパスコードを要求することです。 場合によっては、管理者は[パスコードをリセット](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)するか、従業員によるパスコードのリセットを支援する必要があります。そのためには、パスコードを削除するか、リモートで一時パスコードを設定します。 デバイスをなくしたか、盗難に遭った場合、[デバイスをリモート ロック](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)することもできます。

## Windows デバイスに保護層を追加する
[多要素認証 (MFA)](protect-windows-devices-with-multi-factor-authentication.md) は、ネットワーク上の Windows デバイスと Windows Phone デバイスのユーザーを認証するより安全な方法です。 MFA を使用すると、ユーザーは、ユーザー名とパスワード以外に、電話やテキスト メッセージを使用して本人であることを証明する必要があります。

## Windows デバイスで Microsoft Passport の設定を制御する
Intune は、[Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) と統合できます。 これは、Windows 10 以降に対する代替サインイン方法です。 Microsoft Passport for Work は、Active Directory アカウントまたは Azure Active Directory アカウントを使って、パスワード、スマート カード、または仮想スマート カードを置き換えます。

## iOS デバイスのアクティブ化ロックをバイパスする
アクティブ化ロックは、デバイスを消去または再アクティブ化する前に、Apple ID とパスワードの入力を要求することでユーザー デバイスを保護するのに役立つ機能です。 ただし、これが問題につながる場合があります。たとえば、ユーザーがロックを解除しないまま会社を退職した場合です。 [iOS のアクティベーション ロックのバイパス](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)は、監視下 iOS デバイスのロックを解除して、デバイスを再割り当てしたり、消去したりできるようにする機能です。

## Intune クライアントで管理されている Windows PC を保護する
Intune は引き続き、ユーザーは登録しないが、Intune コンピューター クライアント ソフトウェアで管理する Windows PC のセキュリティ ポリシーをサポートします。 これらのポリシーで Windows PC をセキュリティ保護する方法については、「[Use policies to help protect Windows PCs that run the Intune client software (Intune クライアント ソフトウェアを搭載した Windows PC の保護に有用なポリシーを使用する)](policies-to-protect-windows-pcs-in-microsoft-intune.md)」を参照してください。



<!--HONumber=Aug16_HO2-->


