---
title: Microsoft Intune での Windows Hello for Business の設定 - Azure | Microsoft Docs
description: Windows 10 デバイス上の Microsoft Intune で Windows Hello for Business を使用および構成するための ID 保護プロファイル内のすべての PIN、生体認証、およびスプーフィング防止の設定の一覧を示します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: f1727e22f7fdab2ef3971667f9a60c70ee7b3702
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732712"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Intune で Windows Hello for Business を有効にするための Windows 10 デバイス設定

この記事では、Windows 10 デバイス上の Intune で制御できる Windows Hello for Business の設定の一覧を示して説明します。 Intune 管理者として、モバイル デバイス管理 (MDM) ソリューションの一環としてこれらの設定を構成し、Windows 10 デバイスに割り当てます。 

これらの設定に関する追加情報については、Windows Hello ドキュメント内の「[Windows Hello for Business のポリシー設定の構成](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings)」をご覧ください。


Intune の Windows Hello for Business プロファイルの詳細については、[ID 保護の構成](identity-protection-configure.md)に関するページを参照してください。

## <a name="before-you-begin"></a>始める前に

[構成プロファイルを作成します](identity-protection-configure.md#create-the-device-profile)。

## <a name="windows-hello-for-business"></a>Windows Hello for Business
- **[Windows Hello for Business の構成]** :
  - **[未構成]** - Windows Hello for Business の設定の制御に Intune を使用しない場合は、この設定を選択します。 Windows 10 デバイス上の既存の Windows Hello for Business の設定は変更されません。 ウィンドウ上の他のすべての設定が使用できなくなります。

  - **[無効]** - Windows Hello for Business を使用しない場合は、この設定を選択します。 画面上の他のすべての設定が使用できなくなります。
  - **[有効]** - Windows Hello for Business の設定を構成する場合は、この設定を選択します。  
  
  **既定値**: 未構成

  [*有効*] に設定すると、次の設定を使用できます。

  - **[PIN の長さの最小値]**  
    サインインをセキュリティで保護するために、デバイスの PIN の最小長を指定します。 Windows デバイスの既定値は6文字ですが、この設定では最低 4 ~ 127 文字を適用できます。 

    **既定値**: *[未構成]*

  - **[PIN の長さの最大値]**  
  サインインをセキュリティで保護するために、デバイスの PIN の最大長を指定します。 Windows デバイスの既定値は6文字ですが、この設定では最低 4 ~ 127 文字を適用できます。  

    **既定値**: *[未構成]*  

  - **[PIN での小文字の使用]**  
    エンド ユーザーに小文字を含めるように要求することで、より強力な PIN を強制できます。 次のようなオプションがあります。

    - **[許可しない]** - ユーザーが PIN に小文字を使用できないようにします。 この動作は、設定が構成されていない場合にも発生します。
    - **[許可]** - ユーザーが PIN に小文字を使用することは許可しますが、必須ではありません。
    - **[必須]** - ユーザーは PIN に小文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

  - **[PIN での大文字の使用]**  
    エンド ユーザーに大文字を含めるように要求することで、より強力な PIN を強制できます。 次のようなオプションがあります。

    - **[許可しない]** - ユーザーが PIN に大文字を使用できないようにします。 この動作は、設定が構成されていない場合にも発生します。
    - **[許可]** - ユーザーが PIN に大文字を使用することは許可しますが、必須ではありません。
    - **[必須]** - ユーザーは PIN に大文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

  - **[PIN での特殊文字の使用]**  
    エンド ユーザーに特殊文字を含めるように要求することで、より強力な PIN を強制できます。 特殊文字には、`! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~` が含まれます  

    次のようなオプションがあります。
    - **[許可しない]** - ユーザーが PIN に特殊文字を使用できないようにします。 この動作は、設定が構成されていない場合にも発生します。
    - **[許可]** - ユーザーが PIN に大文字を使用することは許可しますが、必須ではありません。
    - **[必須]** - ユーザーは PIN に大文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

    **既定値**: 許可されていません

  - **[PIN の有効期間 (日)]**  
    その期間が経過したらユーザーが PIN を変更する必要がある有効期間を指定することをお勧めします。 Windows デバイスの既定値は41日です。

    **既定値**: 未構成

  - **[PIN の履歴を保存]**  
    以前に使用した PIN の再利用を制限します。 Windows デバイスは、既定では、最後の5つの Pin の再利用を防止するために使用されます。  

    **既定値**: 未構成  

  - **[PIN の回復を有効にします]**    
    ユーザーが Windows Hello for Business の PIN 回復サービスを使用できるようにします。 
    
    - **有効**-pin 回復シークレットはデバイスに保存され、ユーザーは必要に応じて pin を変更できます。  
    - **Disabled** -回復シークレットが作成または保存されません。

    **既定値**: 未構成

  - **[トラステッド プラットフォーム モジュール (TPM) の使用]**    
    TPM チップは、追加のデータのセキュリティ層を提供します。  

    - **[有効]** - アクセス可能な TPM を装備したデバイスのみが Windows Hello for Business をプロビジョニングできます。
    - **[未構成]** - デバイスは最初に TPM を使用しようとします。 これが使用できない場合、ソフトウェアの暗号化を使用できます。
    
    **既定値**: 未構成

  - **[生体認証を許可する]**  
     Windows Hello for Business の PIN の代わりとして、顔認識や指紋などの生体認証を有効にします。 ユーザーは、生体認証に失敗した場合のために、Work の PIN も設定する必要があります。 次の中から選択します。

    - **[有効にする]** - Windows Hello for Business で生体認証が使用可能になります。
    - **[未構成]** - Windows Hello for Business で生体認証を利用できません (すべてのアカウントの種類が対象)。

    **既定値**: 未構成

  - **[使用可能な場合は、高度なスプーフィング対策を使用する]**  
    Windows Hello のスプーフィング対策機能 (例: 実際の顔の代わりに写真の顔を検出する) をサポートしているデバイスで、その機能を使用するかどうかを構成します。  
    - **[有効にする]** - Windows のすべてのユーザーは、サポートされている場合に顔の特徴のスプーフィング対策を使用する必要があります。
    - **[未構成]** - Windows では、デバイス上のスプーフィング対策の構成を優先します。

    **既定値**: 未構成

  - **[オンプレミスのリソースの証明書]**  

    - **[有効にする]** - オンプレミスのリソースを認証するために、Windows Hello for Business で証明書を使用することを許可します。
    - **[未構成]** - オンプレミスのリソースを認証するために、Windows Hello for Business で証明書を使用できないようにします。 代わりに、デバイスでは、*キー信頼オンプレミス認証*の既定動作が使用されます。 詳細については、Windows Hello ドキュメントの「[オンプレミスの認証に証明書を使用する](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication)」を参照してください。  

  **既定値**: 未構成

- **サインインにセキュリティキーを使用する**  
  この設定は、Windows 10 バージョン1903以降を実行しているデバイスで使用できます。 サインインに Windows Hello セキュリティキーを使用するためのサポートを管理するために使用します。  

  - **有効**-ユーザーは、このポリシーの対象となる pc のログオン資格情報として Windows Hello セキュリティキーを使用できます。 
  - **無効**-セキュリティキーは無効になっており、ユーザーはそれらを使用して pc にサインインすることはできません。   

  **既定値**: 未構成

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](../configuration/device-profile-assign.md)、[その状態を監視](../configuration/device-profile-monitor.md)します。
