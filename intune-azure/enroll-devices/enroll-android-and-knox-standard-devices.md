---
title: "Intune に Android デバイスを登録する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune Azure プレビューで Android デバイスを登録する方法について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>Android デバイスの登録

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune 管理者は、ポータル サイトから Samsung Knox Standard デバイスなどの Android デバイスの管理を有効にできます。 ユーザーが、Google Play から入手できるポータル サイト アプリを使用してデバイスを登録できます。

## <a name="prerequisite"></a>前提条件

モバイル デバイスの管理を準備するには、MDM 機関を **Microsoft Intune** に設定する必要があります。 手順については、[MDM 機関の設定](set-mdm-authority.md)に関するページを参照してください。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。したがって、これは既に設定されている可能性があります。 

## <a name="set-up-android-enrollment"></a>Android の登録を設定する

Intune は、既定で Android および Samsung Knox Standard デバイスの登録を許可するように設定されています。 

Android デバイスの登録を許可またはブロックする設定を確認するには、Azure Portal の [Intune] ブレードに移動し、**[登録]** > **[登録の制限]** の順に選択します。 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>デバイスを登録して会社のリソースにアクセスする方法をユーザーに知らせる

エンドユーザー用の登録手順については、「[Intune に Android デバイスを登録する](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)」を参照してください。 登録プロセスでは、登録により可能になる操作、および IT 管理者が見ることのできるデバイス上のデータと見られないデータについての説明が行われます。

その他のエンドユーザー タスクの詳細については、次の記事を参照してください。

- [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Android デバイスを Intune で使用する](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


