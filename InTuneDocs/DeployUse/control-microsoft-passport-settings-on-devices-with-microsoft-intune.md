---
title: "デバイスの Windows Hello for Business の設定を制御する | Microsoft Intune"
description: "Active Directory や Azure Active Directory アカウントを使った代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードに置き換わる Windows Hello for Business と Intune を統合する方法について説明します。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3d212869051719b6b1f1d527ee52044420df0c14
ms.openlocfilehash: c2c2774dd85d8ce9c056248f801220e06f17063b


---

# Microsoft Intune を使用してデバイスの Windows Hello for Business の設定を制御する
Windows Hello for Business （旧称 Microsoft Passport for Work） と Microsoft Intune を統合できます。Windows Hello for Business は Active Directory や Azure Active Directory アカウントを使った代替サインイン方法であり、パスワード、スマート カード、または仮想スマート カードに置き換わるものです。

Hello for Business を使用すると、パスワードの代わりに*ユーザー ジェスチャ*を使用してサインインできます。 ユーザー ジェスチャには、単純な暗証番号 (PIN)、Windows Hello などの生体認証、または指紋リーダーなどの外部のデバイスがあります。

Intune と Hello for Business の統合には 2 通りの方法があります。

-   Intune ポリシーを使って、ユーザーがサインインに使用できるジェスチャと使用できないジェスチャを制御できます。

-   Windows Hello for Business のキー格納プロバイダー (KSP) に認証証明書を格納します。 詳細については、「[Secure resource access with certificate profiles in Microsoft Intune ](secure-resource-access-with-certificate-profiles.md)」 (Microsoft Intune の証明書プロファイルでリソースへのアクセスを保護する) を参照してください。

## Windows Hello for Business のポリシーの作成

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** &gt; **[Windows Hello for Business]** を選択して、[Windows Hello for Business] ページを開きます。

    ![[Windows Hello for Business] ページ](../media/passport.png)

2.  次の設定から 1 つ選択してください。
    - **[登録デバイスで Windows Hello for Business を無効にする]**。 Windows Hello for Business を使用しない場合は、この設定を選択します。 画面上の他のすべての設定が使用できなくなります。
    - **[登録デバイスで Windows Hello for Business を有効にする]**。 Windows Hello for Business の設定を構成する場合は、この設定を選択します。
    - **[Not configured]** (未構成)。 Windows Hello for Business の設定の制御に Intune を使用しない場合は、この設定を選択します。 Windows 10 デバイス上の既存の Windows Hello for Business の設定は変更されません。 画面上の他のすべての設定が使用できなくなります。
3.  **[登録デバイスで Windows Hello for Business を有効にする]** を選択した場合は、すべての登録済みの Windows 10 デバイスと Windows 10 モバイル デバイスに適用される必須設定を構成します。
4.  終了したら、**[保存]** を選択します。


## Windows Hello for Business のポリシーの設定

- **[トラステッド プラットフォーム モジュール (TPM) の使用]**。 TPM チップは、追加のデータのセキュリティ層を提供します。<br>次のいずれかの値を選択します。
    - **[必須]** (既定)。 アクセス可能な TPM を装備したデバイスのみが Windows Hello for Business をプロビジョニングできます。
    - **[優先]**。 デバイスは最初に TPM を使用しようとします。 これが使用できない場合、ソフトウェアの暗号化を使用できます。
- **[最小 PIN サイズを必要とする]**/**[最大 PIN サイズを必要とする]**。 サインインをセキュリティで保護するために指定する PIN の最小長と最大長を使用するようにデバイスを構成します。 既定の PIN の長さは 6 文字ですが、最小長を 4 文字にすることができます。 PIN の最大長は 127 文字です。
- **[PIN での小文字の使用を必要とする]**/**[PIN での大文字の使用を必要とする]**/**[Require special characters in PIN]** (PIN での特殊文字の使用を必要とする)。 大文字、小文字、特殊文字を PIN で使用するように要求することで、PIN をより強力にすることができます。 次の中から選択します。
    - **[許可]**。 ユーザーは PIN で文字を使用できますが、使用は必須ではありません。
    - **[必須]**。 ユーザーは PIN に文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。
    - **[許可しない]** (既定)。 ユーザーは、これらの文字を PIN で使用することができません  (これは、この設定を構成していない場合の動作でもあります)。<br>特殊文字には次のものが含まれます。 **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**.
- **[PIN の有効期間 (日)]**。 その期間が経過したらユーザーが PIN を変更する必要がある有効期間を指定することをお勧めします。 既定は 41 日です。
- **[PIN の履歴を保存]**。 以前に使用した PIN の再利用を制限します。 既定では、直近 5 回の PIN を再利用することはできません。
- **[生体認証を許可]**。 Windows Hello for Business の PIN の代わりとして、顔認識や指紋などの生体認証を有効にします。 ユーザーは、生体認証に失敗した場合のために、Work の PIN も設定する必要があります。 次の中から選択します。
    - **[はい]**。 Windows Hello for Business で生体認証が使用可能になります。
    - **[いいえ]**。 Windows Hello for Business で生体認証を利用できません (すべてのアカウントの種類が対象)。
- **[拡張スプーフィング対策が使用可能な場合は使用する]**。 Windows Hello のスプーフィング対策機能 (例: 実際の顔の代わりに写真の顔を検出する) をサポートしているデバイスで、その機能を使用するかどうかを構成します。<br>**[はい]** に設定されている場合、Windows のすべてのユーザーは、サポートされている場合に顔の特徴のスプーフィング対策を使用する必要があります。
- **[電話によるサインインの使用]**。 このオプションが **[はい]** に設定されている場合、ユーザーはデスクトップ コンピューターの認証にポータブル コンパニオン デバイスとして機能するリモートの Passport を使用することができます。 デスクトップ コンピューターは Azure Active Directory に参加している必要があり、コンパニオン デバイスでは Windows Hello for Business の PIN を設定する必要があります。

## 詳細情報
Microsoft Passport について詳しくは、Windows 10 ドキュメントの[こちらのガイド](https://technet.microsoft.com/library/mt589441.aspx)をご覧ください。



<!--HONumber=Sep16_HO1-->


