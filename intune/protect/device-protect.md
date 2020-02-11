---
title: Microsoft Intune でデバイスを保護する
titleSuffix: Microsoft Intune
description: 不正アクセスなどの脅威からのデバイス保護に Intune が役立つ方法のいくつかについて説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: conceptual
ms.subservice: protect
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c18b6bcc8ec6e8d78862c0368c920fd3d79ce2b5
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755580"
---
# <a name="protect-devices-with-microsoft-intune"></a>Microsoft Intune でデバイスを保護する

Microsoft Intune を使用すると、管理するデバイスと、そのデバイスに格納されたデータを保護することができます。

## <a name="device-configuration"></a>デバイスの構成
Intune の[構成ポリシー](../configuration/device-profiles.md)は、さまざまな設定や機能を制御してデバイスを保護したり構成したりするのに役立ちます。 次に例を示します。

- カメラや Bluetooth などのデバイス上のハードウェア機能の使用を制限できます。
- 準拠アプリと非準拠アプリを構成できます。 非準拠アプリがインストールされる場合、アラートが表示されます (一部のプラットフォームでは、インストールを実際にブロックできます)。

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>ユーザーがデバイスからロックアウトされるときにパスコードをリセットする
モバイル デバイス上の会社のデータを保護するには、まず、デバイスを使用するためのパスコードが必要になるため、場合によっては、[パスコードをリセットする](../remote-actions/device-passcode-reset.md)か、従業員がパスコードをリセットできるようにする必要があります。そのためには、パスコードを削除するか、リモートで一時パスコードを設定します。 デバイスの紛失や盗難が発生した場合は、[デバイスをリモート ロック](../remote-actions/device-remote-lock.md)することもできます。

## <a name="retire-devices-and-remove-data"></a>デバイスを削除して、データを削除する
デバイスを [Intune 管理対象から削除](../remote-actions/devices-wipe.md)する必要がある場合 (ユーザーが退職する場合や、デバイスが紛失や盗難にあった場合など)、そのデバイスからデータを削除することが望まれます。 Intune では、企業データの安全を確保するための、さまざまな方法が用意されています。

## <a name="require-devices-to-be-compliant"></a>準拠デバイスである必要がある
Intune は [デバイス コンプライアンス ポリシー](device-compliance-get-started.md) の機能を備えています。これにより、指定する規則に準拠していないデバイスを評価 (場合によっては修復) することができます。 たとえば、次のことに関するレポートを取得できます。
- 脱獄された iOS デバイス
- 暗号化されたデバイス、または暗号化されていないデバイス
- Windows 10 デバイスの正常性 (正常性構成証明サービスによって決定される)。

## <a name="protect-apps-and-the-data-they-use"></a>アプリと使用しているデータを保護する
Intune では、アプリとそのデータを保護するのに役立つ機能を提供します。 たとえば、モバイル アプリケーション管理 (MAM) ポリシーでは、次のことが可能です。
- 保護されているアプリからのデータのバックアップを回避する
- 他のアプリへのコピーや貼り付けを制限する
- アプリにアクセスするための PIN を要求する、など。詳細については、「[Microsoft Intune でアプリとデータを保護する](../apps/app-protection-policy.md)」をご覧ください。

## <a name="add-an-additional-layer-of-protection-to-devices"></a>デバイスに保護層を追加する
[多要素認証 (MFA)](../enrollment/multi-factor-authentication.md) は、ネットワーク上のデバイスのユーザーを認証するより安全な方法です。  MFA を使用すると、ユーザーは、ユーザー名とパスワード以外に、電話やテキスト メッセージを使用して本人であることを証明する必要があります。

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Windows デバイスで Windows Hello for Business の設定を制御する
Intune は [Windows Hello for Business](windows-hello.md) と統合することができます。これは、パスワード、スマート カード、仮想スマート カードの代わりに Active Directory または Azure Active Directory アカウントを使用する、Windows 10 以降に向けた代替サインイン方法です。

## <a name="disable-activation-lock-on-ios-devices"></a>iOS デバイスのアクティブ化ロックを無効にする
アクティベーション ロックはユーザーのデバイスの保護に役立つ機能です。 この機能を使用すると、ユーザーはデバイスを消去したり再アクティブ化したりする前に、各自の Apple ID とパスワードを入力する必要があります。 ただし、この機能が問題を引き起こす場合もあります。ユーザーがロックを解除しないまま会社を退職した場合などです。 [iOS のアクティベーション ロックの無効化](../remote-actions/device-activation-lock-disable.md)は、監視下 iOS デバイスのロックを解除して、デバイスを再割り当てしたり、消去したりできるようにする機能です。

## <a name="next-steps"></a>次のステップ

[Mobile Threat Defense](mobile-threat-defense.md) について学習します
