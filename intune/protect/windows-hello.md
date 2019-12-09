---
title: Windows Hello for Business と Microsoft Intune の統合
titleSuffix: Microsoft Intune
description: マネージド デバイスで Windows Hello for Business の使用を制御するポリシーを作成する方法について説明します。"
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 7ce6def40c6c0fff3a28f884c458220283979234
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465771"
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Windows Hello for Business と Microsoft Intune の統合  

Windows Hello for Business (旧称 Microsoft passport for Work) と Microsoft Intune を統合することができます。

 Hello for Business は、Active Directory や Azure Active Directory アカウントを使った代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードに取って代わります。 これを使用すると、パスワードの代わりに*ユーザー ジェスチャ*を使用してサインインできます。 ユーザー ジェスチャには、暗証番号 (PIN)、Windows Hello などの生体認証、または指紋リーダーなどの外部のデバイスがあります。

Intune と Hello for Business の統合には 2 通りの方法があります。

- Intune ポリシーは **[デバイスの登録]** で作成できます。 このポリシーの対象は組織全体 (テナント全体) となります。 Windows AutoPilot out-of-box-experience (OOBE) をサポートしており、デバイスが登録されたときに適用されます。 
- ID 保護プロファイルは **[デバイス構成]** で作成できます。 このプロファイルの対象は割り当てられたユーザーとデバイスであり、チェックイン時に適用されます。 

この記事を利用し、組織全体を対象とする既定の Windows Hello for Business ポリシーを作成します。 一部のユーザー グループとデバイス グループに適用される ID 保護プロファイルを作成するには、[ID 保護プロファイルを構成する](identity-protection-configure.md)方法に関するページを参照してください。  

<!--- - You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Anniversary Update バージョンより前の Windows 10 のデスクトップおよびモバイルでは、リソースの認証に使用可能な 2 つの異なる PIN を設定することができました。
> - **デバイス PIN**: デバイスのロック解除とクラウド リソースへの接続に使用できました。
> - **勤務先 PIN**: ユーザーの個人用デバイス (BYOD) 上の Azure AD リソースへのアクセスに使用されていました。
> 
> Anniversary Update では、これら 2 つの PIN が 1 つのデバイス PIN にまとめられました。
> デバイス PIN の制御用に設定済みの Intune の構成ポリシー、さらに構成済みの Windows Hello for Business ポリシーの両方により、この新しい PIN の値が設定されるようになりました。
> 両方の種類のポリシーをデバイス PIN の制御用に設定している場合、Windows Hello for Business が Windows 10 デスクトップおよびモバイル デバイスの両方に適用されます。
> ポリシーの競合を解消して PIN ポリシーが適切に適用されるようにするために、構成ポリシーの設定に合わせて Windows Hello for Business ポリシーを更新し、ユーザーにポータル サイト アプリでデバイスを同期するように伝えてください。



## <a name="create-a-windows-hello-for-business-policy"></a>Windows Hello for Business のポリシーの作成

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431 ) にサインインします。

2. **[デバイス]** > 登録** > **[デバイスの登録]**  >  **[Windows の登録]**  >  **[Windows Hello for Business]** の順に移動します。 [Windows Hello for Business] ウィンドウが開きます。

3. **[Windows Hello for Business の構成]** を次のオプションから選択します。

    - **Disabled**。 Windows Hello for Business を使用しない場合は、この設定を選択します。 無効にした場合、プロビジョニングが必須の可能性がある Azure Active Directory に参加した携帯電話以外では、ユーザーは Windows Hello for Business をプロビジョニングできません。
    - **Enabled**。 Windows Hello for Business の設定を構成する場合は、この設定を選択します。  *Enabled* を選択した場合、Windows Hello の追加設定が表示されます。
    - **[Not configured]** (未構成)。 Windows Hello for Business の設定の制御に Intune を使用しない場合は、この設定を選択します。 Windows 10 デバイス上の既存の Windows Hello for Business の設定は変更されません。 ウィンドウ上の他のすべての設定が使用できなくなります。

4. 前の手順で **[有効]** を選択した場合は、すべての登録済みの Windows 10 デバイスと Windows 10 モバイル デバイスに適用される必須設定を構成します。 これらの設定を構成した後、 **[保存]** を選択します。

   - **[トラステッド プラットフォーム モジュール (TPM) の使用]** :

     TPM チップは、追加のデータのセキュリティ層を提供します。 次のいずれかの値を選択します。

     - **[必須]** (既定)。 アクセス可能な TPM を装備したデバイスのみが Windows Hello for Business をプロビジョニングできます。
     - **[優先]** 。 デバイスは最初に TPM を使用しようとします。 このオプションが使用できない場合、ソフトウェアの暗号化を使用できます。

   - **[PIN の長さの最小値]** **[PIN の長さの最大値]** :

     サインインをセキュリティで保護するために指定する PIN の最小長と最大長を使用するようにデバイスを構成します。 既定の PIN の長さは 6 文字ですが、最小長を 4 文字にすることができます。 PIN の最大長は 127 文字です。

   - **[PIN での小文字の使用]** 、 **[PIN での大文字の使用]** 、および **[PIN での特殊文字の使用]** 。

     大文字、小文字、特殊文字を PIN で使用するように要求することで、PIN をより強力にすることができます。 それぞれに対して、次のいずれかを選択します。

     - **[許可]** 。 ユーザーは PIN で文字を使用できますが、使用は必須ではありません。

     - **[必須]** 。 ユーザーは PIN に文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

     - **[許可しない]** (既定)。 ユーザーは、これらの文字を PIN で使用することができません (これは、この設定を構成していない場合の動作でもあります)。

       特殊文字には次のものが含まれます。 **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **[PIN の有効期間 (日)]** :

     その期間が経過したらユーザーが PIN を変更する必要がある有効期間を指定することをお勧めします。 既定は 41 日です。

   - **[PIN の履歴を保存]** :

     以前に使用した PIN の再利用を制限します。 既定では、直近 5 回の PIN を再利用することはできません。

   - **[生体認証を許可する]** :

     Windows Hello for Business の PIN の代わりとして、顔認識や指紋などの生体認証を有効にします。 ユーザーは、生体認証に失敗した場合のために、Work の PIN も設定する必要があります。 次の中から選択します。

     - **[はい]** 。 Windows Hello for Business で生体認証が使用可能になります。
     - **[いいえ]** 。 Windows Hello for Business で生体認証を利用できません (すべてのアカウントの種類が対象)。

   - **[使用可能な場合は、高度なスプーフィング対策を使用する]** :

     サポートされるデバイス上で Windows Hello のスプーフィング対策機能を使用するかどうかを構成します。 たとえば、実際の顔ではなく顔の写真を検出します。

     **[はい]** に設定されている場合、Windows のすべてのユーザーは、サポートされている場合に顔の特徴のスプーフィング対策を使用する必要があります。

   - **[電話によるサインインの許可]** :

     このオプションが **[はい]** に設定されている場合、ユーザーはデスクトップ コンピューターの認証にポータブル コンパニオン デバイスとして機能するリモートの Passport を使用することができます。 デスクトップ コンピューターは Azure Active Directory に参加している必要があり、コンパニオン デバイスでは Windows Hello for Business の PIN を設定する必要があります。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business のサポート

Windows Holographic for Business では、Windows Hello for Business の以下の設定がサポートされます。

- トラステッド プラットフォーム モジュール (TPM) の使用
- PIN の最小長
- PIN の最大長
- PIN での小文字
- PIN での大文字
- PIN での特殊文字
- PIN の有効期間 (日)
- PIN の履歴を保存

## <a name="next-steps"></a>次の手順

Windows Hello for Business の詳細については、Windows 10 ドキュメント内の[ガイド](https://technet.microsoft.com/library/mt589441.aspx)を参照してください。
