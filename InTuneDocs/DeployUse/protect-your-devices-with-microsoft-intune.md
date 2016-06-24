---
# required metadata

title: デバイスを保護する | Microsoft Intune
description:
keywords:
author: Robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune でデバイスを保護する
デバイスを Intune の管理対象にしたら、無許可のアクセスやその他の脅威に対して保護されていることを確認します。 その目的に役立つ Intune の機能をいくつか示します。

> [!TIP]
> このトピックでは、デバイスのセキュリティ保護に役立つ Intune の機能の一部のみを紹介します。 たとえば、Intune ポリシーを使用すれば、パスワードの構成、暗号化設定、ハードウェア機能 (Bluetooth やデバイス カメラなど) など、さまざまなセキュリティ設定をデバイスで構成できます。 これらの設定の詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

## ユーザーがデバイスからロックアウトされるときにパスコードをリセットする
モバイル デバイス上の会社のデータを保護するには、まず、デバイスを使用するためのパスコードが必要になるため、場合によっては、[パスコードをリセットする](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)か、従業員がパスコードをリセットできるようにする必要があります。そのためには、パスコードを削除するか、リモートで一時パスコードを設定します。 デバイスをなくしたか、盗難に遭った場合、[デバイスをリモート ロック](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)することもできます。

## Windows デバイスに保護層を追加する
[多要素認証 (MFA)](protect-windows-devices-with-multi-factor-authentication.md) は、ネットワーク上の Windows デバイスと Windows Phone デバイスのユーザーを認証するより安全な方法です。  MFA を使用すると、ユーザーは、ユーザー名とパスワード以外に、電話やテキスト メッセージを使用して本人であることを証明する必要があります。

## Windows デバイスで Microsoft Passport の設定を制御する
Intune では、[Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) を統合できます。これは Active Directory または Azure Active Directory アカウントを使った Windows 10 以降の代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードの代わりに使用されます。

## Intune クライアントで管理されている Windows PC を保護する
Intune は引き続き、ユーザーは登録しないが、Intune コンピューター クライアント ソフトウェアで管理する Windows PC のセキュリティ ポリシーをサポートします。 これらのポリシーで Windows PC をセキュリティ保護する方法については、「[Use policies to help protect Windows PCs that run the Intune client software](policies-to-protect-windows-pcs-in-microsoft-intune.md)」 (Intune クライアント ソフトウェアを搭載した Windows PC の保護に有用なポリシーを使用する) を参照してください。


<!--HONumber=May16_HO2-->


