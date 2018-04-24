---
title: Microsoft Intune でデバイスを保護する
description: 不正アクセスなどの脅威からのデバイス保護に Intune が役立つ方法のいくつかについて説明します。
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ea1cc3bc2d662a0d74c87fb5616f3626d580a7e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="protect-devices-with-microsoft-intune"></a>Microsoft Intune でデバイスを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune では、管理するデバイスを保護するための機能とそれらのデバイスに格納されたデータをセットで提供します。 このトピックではこれらの機能の基本とその詳細を説明します。

## <a name="general-ways-to-protect-all-devices"></a>すべてのデバイスを保護する一般的な方法

### <a name="device-configuration"></a>デバイス構成
Intune [構成ポリシー](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)は、さまざまな設定と機能を制御することでデバイスを保護および構成する際に役立ちます。 次に例を示します。
- カメラや Bluetooth などのデバイス上のハードウェア機能の使用を制限できます。
- 準拠アプリと非準拠アプリを構成できます。 非準拠アプリがインストールされている場合に警告します (一部のプラットフォームでは、インストールを実際にブロックできます)。

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>ユーザーがデバイスからロックアウトされるときにパスコードをリセットする
モバイル デバイス上の会社のデータを保護するには、まず、デバイスを使用するためのパスコードが必要になるため、場合によっては、[パスコードをリセットする](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)か、従業員がパスコードをリセットできるようにする必要があります。そのためには、パスコードを削除するか、リモートで一時パスコードを設定します。 デバイスをなくしたか、盗難に遭った場合、[デバイスをリモート ロック](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)することもできます。

### <a name="retire-devices-and-remove-data"></a>デバイスを削除して、データを削除する
デバイスを [Intune 管理対象から削除](retire-devices-from-microsoft-intune-management.md)する必要がある場合に (ユーザーが退職する、またはデバイスが紛失や盗難にあった場合など)、そのデバイスからデータを削除します。 Intune は、企業データの安全を確保するさまざまな方法を提供します。

### <a name="require-devices-to-be-compliant"></a>準拠デバイスである必要がある
Intune は [デバイス コンプライアンス ポリシー](introduction-to-device-compliance-policies-in-microsoft-intune.md) を特徴としているため、指定する規則に準拠していないデバイスを評価 (場合によっては修復) できます。 たとえば、脱獄している iOS デバイスや、デバイスが暗号化されているかどうか、または正常性証明書サービスによって Windows 10 デバイスを正常と報告するかどうかについて報告できます。

### <a name="protect-apps-and-the-data-they-use"></a>アプリと使用しているデータを保護する
Intune では、アプリとそのデータを保護するのに役立つ機能を提供します。 たとえば、モバイル アプリケーション管理 (MAM) ポリシーが、保護されているアプリからデータをバックアップされないようにし、他のアプリへのコピーや貼り付けを制限し、アプリへのアクセスに暗証番号 (PIN) を要求します。 アプリの保護の詳細については、「[Microsoft Intune でアプリとデータを保護する](protect-apps-and-data-with-microsoft-intune.md)」をご覧ください。

### <a name="add-an-additional-layer-of-protection-to-devices"></a>デバイスに保護層を追加する
[多要素認証 (MFA)](multi-factor-authentication-azure-active-directory.md) は、ネットワーク上のデバイスのユーザーを認証するより安全な方法です。  MFA を使用すると、ユーザーは、ユーザー名とパスワード以外に、電話やテキスト メッセージを使用して本人であることを証明する必要があります。

## <a name="further-capabilities-for-windows-devices"></a>Windows デバイスの他の機能

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Windows デバイスで Windows Hello for Business の設定を制御する
Intune は、[Windows Hello for Business](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (旧 Microsoft Passport) と統合でき、パスワード、スマート カード、または仮想スマート カードの代わりに Active Directory または Azure Active Directory アカウントを使った Windows 10 以降の代替サインイン方法です。

## <a name="further-capabilities-for-ios-devices"></a>iOS デバイスの他の機能

### <a name="bypass-activation-lock-on-ios-devices"></a>iOS デバイスのアクティブ化ロックをバイパスする
アクティブ化ロックは、デバイスを消去または再アクティブ化する前に、Apple ID とパスワードの入力を要求することでユーザー デバイスを保護するのに役立つ機能です。 ただし、これが問題につながる場合があります。たとえば、ユーザーがロックを解除しないまま会社を退職した場合です。 [iOS のアクティベーション ロックのバイパス](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md)は、監視下 iOS デバイスのロックを解除して、デバイスを再割り当てしたり、消去したりできるようにする機能です。



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>Intune クライアントで管理されている Windows PC を保護する
Intune は引き続き、ユーザーは登録しないが、Intune コンピューター クライアント ソフトウェアで管理する Windows PC のセキュリティ ポリシーをサポートします。 これらのポリシーで Windows PC をセキュリティ保護する方法については、「[Use policies to help protect Windows PCs that run the Intune client software (Intune クライアント ソフトウェアを搭載した Windows PC の保護に有用なポリシーを使用する)](policies-to-protect-windows-pcs-in-microsoft-intune.md)」を参照してください。
