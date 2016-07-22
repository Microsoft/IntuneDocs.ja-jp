---
title: "デバイスで Microsoft Passport の設定を制御する | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 42e21b802fb605c98f688485c3b77703b3950e94
ms.openlocfilehash: bdf7dfda3814ad6c6c00f5c133027175a95fb5e2


---

# Microsoft Intune を使ってデバイスで Microsoft Passport の設定を制御する
Microsoft Intune により、**Microsoft Passport for Work** を統合できます。これは Active Directory や Azure Active Directory アカウントを使った代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードに置き換わります。

Passport を使用すると、パスワードの代わりに**ユーザー ジェスチャ**を使用してログインできます。 ユーザー ジェスチャには、単純な暗証番号 (PIN)、Windows Hello などの生体認証、または指紋リーダーなどの外部のデバイスがあります。

Intune は、2 つの方法で Passport for Work と統合できます。

-   Intune ポリシーを使って、ユーザーがログインに使用できるジェスチャと使用できないジェスチャを制御できます。

-   Passport for Work のキー格納プロバイダー (KSP) に認証証明書を格納できます。 詳細については、「[Secure resource access with certificate profiles in Microsoft Intune ](secure-resource-access-with-certificate-profiles.md)」 (Microsoft Intune の証明書プロファイルでリソースへのアクセスを保護する) を参照してください。

## Passport for Work ポリシーを作成するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** &gt; **[Passport for Work]** をクリックして、次の [Passport for Work] ページを開きます。

    ![[Passport for Work] ページ](../media/passport.png)

2.  次の設定から 1 つ選択してください。
    - **登録デバイスで Passport for Work を無効にする** - Windows 10 デバイスで Passport for Work を使用しない場合は、この設定を選択します。 画面上の他のすべての設定が無効になります。
    - **登録デバイスで Passport for Work を有効にする** - すべての Windows 10 デバイスで Passport for Work 設定を構成する場合は、この設定を選択します。
    - **未構成** - Intune で Passport for Work 設定を制御しない場合は、この設定を選択します。 Windows 10 デバイス上の既存の Passport for Work 設定が変更されることはありません。 画面上の他のすべての設定が無効になります。
3.  **[登録デバイスで Passport for Work を有効にする]** を選択した場合は、すべての登録済みの Windows 10 デバイスと Windows 10 モバイル デバイスに適用される必須設定を構成します。
3.  操作が完了したら、**[保存]** をクリックします。

## Passport for Work: PIN 設定

  
- **PIN の最小長**/**PIN の最大長** - サインインをセキュリティで保護するために指定する PIN の最小長と最大長を使用するようにデバイスを構成します。 既定の PIN の長さは 6 文字ですが、最小長を 4 文字にすることができます。 PIN の最大長は 127 文字です。
- **PIN に小文字が必要**/**PIN に大文字が必要**/**PIN に特殊文字が必要** - さらに、大文字、小文字、特殊文字を PIN で使用するように要求することで、PIN をより強力にすることができます。 次の中から選択します。
    - **許可** - ユーザーは PIN で文字を使用できますが、使用は必須ではありません。
    - **必須** -ユーザーは PIN に文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。
    - **使用不可** (既定) - ユーザーは、これらの文字を PIN で使用することができません (これは、この設定を構成していない場合の動作でもあります)。
    > [!TIP]
    > 特殊文字には次のものが含まれます。 **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **PIN の有効期間 (日)** - その期間が経過したらエンドユーザーが PIN を変更する必要がある有効期間を指定することをお勧めします。 既定は 41 日です。 
- **PIN の履歴を保存** - この設定を使用すると、以前に使用した PIN の再利用を制限できます。 既定では過去 5 回の PIN を再利用することはできません。


## Passport for Work: その他の設定

- **トラステッド プラットフォーム モジュール (TPM) の使用** - トラステッド プラットフォーム モジュール (TPM) チップは、追加のデータのセキュリティ層を提供します。<br>次のいずれかの値を選択します。
    - **必須** (既定) - アクセス可能な TPM を装備したデバイスのみが Passport for Work をプロビジョニングできます。
    - **優先** - デバイスは最初に TPM を使用しようとします。 これが使用できない場合、ソフトウェアの暗号化を使用できます。
- **生体認証を許可** - Passport for Work の PIN の代わりとして、顔認識や指紋などの生体認証を有効にします。 ユーザーは、生体認証に失敗した場合のために、Work の PIN も設定する必要があります。 次の中から選択します。
    - **はい** - Passport for Work で生体認証が可能になります。
    - **いいえ** - Passport for Work で生体認証を利用できません (すべてのアカウントの種類が対象)。
- **拡張スプーフィング対策が使用可能な場合は使用する** - Windows Hello のスプーフィング対策機能 (例: 実際の顔の代わりに写真の顔を検出する) をサポートしているデバイスで、その機能を使用するかどうかを構成します。<br>**[はい]** に設定されている場合、Windows のすべてのユーザーは、サポートされている場合に顔の特徴のスプーフィング対策を使用する必要があります。
- **リモートの Passport を使用する** - このオプションが **[はい]** に設定されている場合、ユーザーはデスクトップ コンピューターの認証にポータブル コンパニオン デバイスとして機能するリモートの Passport を使用することができます。 デスクトップ コンピューターは Azure Active Directory に参加している必要があり、コンパニオン デバイスは、Passport for Work の PIN を使用して設定されている必要があります。

## 詳細情報
Microsoft Passport について詳しくは、Windows 10 ドキュメントの[こちらのガイド](https://technet.microsoft.com/library/mt589441.aspx)をご覧ください。





<!--HONumber=Jun16_HO4-->


