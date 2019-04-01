---
title: Microsoft Intune での Windows Hello for Business の設定 - Azure | Microsoft Docs
description: Windows 10 デバイス上の Microsoft Intune で Windows Hello for Business を使用および構成するための ID 保護プロファイル内のすべての PIN、生体認証、およびスプーフィング防止の設定の一覧を示します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 308a730737612f39863160952409ab92670f9153
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069172"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Intune で Windows Hello for Business を有効にするための Windows 10 デバイス設定

この記事では、Windows 10 デバイス上の Intune で制御できる Windows Hello for Business の設定の一覧を示して説明します。 Intune 管理者は構成して、モバイル デバイス管理 (MDM) ソリューションの一部としてこれらの設定を Windows 10 デバイスに割り当てます。 

これらの設定に関する追加情報を見つけることができます[構成 Windows こんにちは for Business のポリシー設定](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)、WIndows こんにちはのドキュメント。


Intune の Windows Hello for Business プロファイルの詳細については、[ID 保護の構成](identity-protection-configure.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[構成プロファイルを作成します](identity-protection-configure.md#create-the-device-profile)。

## <a name="windows-hello-for-business"></a>Windows Hello for Business

- **Windows こんにちは for Business 構成**: この機能を使用して、その設定を設定して、次のように選択します。**を有効にする**します。
- **[PIN の長さの最小値]**: デバイス上で許可する PIN の長さの最小値を入力します。 PIN の長さの既定値は 6 文字です。 PIN の長さの最小値は 4 文字です。
- **[PIN の長さの最大値]**: デバイス上で許可する PIN の長さの最大値を入力します。 PIN の長さの既定値は 6 文字です。 PIN の最大長は 127 文字です。  
- **[PIN での小文字の使用]**: エンド ユーザーに小文字を含めるように要求することで、より強力な PIN を強制できます。 次のようなオプションがあります。

  - **許可されていません**(既定値): ユーザーが PIN で小文字の使用をブロックします。 この動作は、設定が構成されていない場合にも発生します。
  - **[許可]**: ユーザーが PIN に小文字を使用することは許可しますが、必須ではありません。
  - **[必須]**: ユーザーは PIN に小文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

- **[PIN での大文字の使用]**: エンド ユーザーに大文字を含めるように要求することで、より強力な PIN を強制できます。 次のようなオプションがあります。

  - **許可されていません**(既定値): ユーザーが PIN に大文字を使用します。 この動作は、設定が構成されていない場合にも発生します。
  - **[許可]**: ユーザーが PIN に大文字を使用することは許可しますが、必須ではありません。
  - **[必須]**: ユーザーは PIN に大文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

- **[PIN での特殊文字の使用]**: エンド ユーザーに特殊文字を含めるように要求することで、より強力な PIN を強制できます。 次のようなオプションがあります。

  - **許可されていません**(既定値): ユーザーが PIN に特殊文字を使用します。 この動作は、設定が構成されていない場合にも発生します。
    特殊文字には、`! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~` が含まれます
  - **[許可]**: ユーザーが PIN に大文字を使用することは許可しますが、必須ではありません。
  - **[必須]**: ユーザーは PIN に大文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

- **[PIN の有効期間 (日)]**: その期間が経過したらユーザーが PIN を変更する必要がある有効期間を指定することをお勧めします。 既定は 41 日です。

- **PIN の履歴を保存**: 以前に使用した Pin の再利用を制限します。 既定では、直近 5 回の PIN を再利用することはできません。  
- **[Enable PIN recovery]\(PIN の回復を有効にします\)**: Windows Hello for Business の PIN の回復サービスを使用して、ユーザーが自分の PIN を変更することを許可します。

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **[トラステッド プラットフォーム モジュール (TPM) を使用する]**: TPM チップでは、追加のデータのセキュリティ層を提供します。 次のいずれかの値を選択します。  
  - **[有効にする]**: アクセス可能な TPM を装備したデバイスのみが Windows Hello for Business をプロビジョニングできます。
  - **[未構成]**: 使用可能な TPM がない場合も、すべてのデバイスで Windows Hello for Business をプロビジョニングすることができます。 デバイスでは、まず TPM を使用しようとしますが、利用できない場合は、デバイスでソフトウェアの暗号化を使用できます。  

- **[生体認証を許可する]**: Windows Hello for Business の PIN の代わりとして、顔認識や指紋などの生体認証を有効にします。 ユーザーは、生体認証に失敗した場合のために、Work の PIN も設定する必要があります。 次の中から選択します。

  - **[有効にする]**: Windows Hello for Business で生体認証が使用可能になります。
  - **[未構成]** (既定値): Windows Hello for Business で生体認証を利用できません (すべてのアカウントの種類が対象)。

- **拡張スプーフィング対策を使用可能な場合を使用して、**: サポートされているデバイスで Windows こんにちはの機能を使用の場合、スプーフィング対策を選択します。 たとえば、実際の顔ではなく顔の写真を検出します。

  - **[有効にする]**: Windows のすべてのユーザーは、サポートされている場合に顔の特徴のスプーフィング対策を使用する必要があります。  
  - **構成されていない**(既定値): Windows は、デバイス上のなりすまし対策の構成を優先します。

- **[オンプレミスのリソースの証明書]**: 

  - **[有効にする]**: オンプレミスのリソースを認証するために、Windows Hello for Business で証明書を使用することを許可します。
  - **[未構成]** (既定値): オンプレミスのリソースを認証するために、Windows Hello for Business で証明書を使用できないようにします。 デバイスでの既定の動作を使用する代わりに、*キー信頼オンプレミス認証*します。 詳細については、次を参照してください。 [、オンプレミスの認証用のユーザーの証明書](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication)Windows Hello のドキュメント。  
## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
