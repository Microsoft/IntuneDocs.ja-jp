---
title: Microsoft Intune で SCEP または PKCS 証明書を削除する - Azure | Microsoft Docs
titleSuffix: ''
description: 管理者は "ワイプ" アクションまたは "インベントリからの削除" アクションを利用し、Microsoft Intune から証明書を削除できます。 デバイスの登録解除やコンプライアンス ポリシーの削除など、一部のシナリオでは証明書が自動的に削除されます。 Intune ライセンスが失われたり、削除されたりしたときなど、証明書が自動的にデバイスに残るシナリオもあります。 Android、Android エンタープライズ、iOS、macOS、Windows デバイス用のさまざまな方法をご確認ください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d4287322fd494c97cf24feb8cc16435a4405f2af
ms.sourcegitcommit: 7a649a5995600fb91817643e20a5565caedbb8f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50150109"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Microsoft Intune で SCEP 証明書と PKCS 証明書を削除する

Microsoft Intune で SCEP 証明書と PKCS 証明書をデバイスに追加できます。 これらの証明書は、デバイスから[ワイプ](devices-wipe.md#wipe)したり、[インベントリから削除](devices-wipe.md#retire)したりするときにも削除できます。 証明書が自動的に削除されるシナリオや、証明書がデバイスに残るシナリオもあります。

この記事では、一般的なシナリオと、PKCS 証明書と SCEP 証明書への影響を紹介します。

> [!NOTE]
> Active Directory (AD) または Azure AD から削除されるユーザー用の証明書を削除したり、取り消すには、次の手順を実行します。
>
>    1. ユーザーのデバイスをワイプする (または、インベントリから削除する)
>    2. AD または Azure AD からユーザーを削除する

## <a name="windows-devices"></a>Windows デバイス

#### <a name="scep-certificates"></a>SCEP 証明書

- SCEP 証明書は次の場合に取り消され、*その上*、削除されます。

  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する
  - デバイスが Azure Active Directory (AD) グループから削除される
  - コンプライアンス ポリシーがグループ割り当てから削除される
  - コンプライアンス プロファイルがグループ割り当てから削除される

- SCEP 証明書は次の場合に取り消されます。
  - 管理者が SCEP プロファイルを変更または更新する

- ルート証明書は次の場合に削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する
  - コンプライアンス ポリシーがグループ割り当てから削除される

- SCEP 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する

#### <a name="pkcs-certificates"></a>PKCS 証明書

- PKCS 証明書は次の場合に取り消され、*その上*、削除されます。

  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- ルート証明書は次の場合に削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- PKCS 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する
  - 管理者が PKCS プロファイルを変更または更新する
  - コンプライアンス プロファイルがグループ割り当てから削除される
  - コンプライアンス ポリシーがグループ割り当てから削除される 


## <a name="ios-devices"></a>iOS デバイス

#### <a name="scep-certificates"></a>SCEP 証明書

- SCEP 証明書は次の場合に取り消され、*その上*、削除されます。

  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する
  - デバイスが Azure Active Directory (AD) グループから削除される
  - コンプライアンス ポリシーがグループ割り当てから削除される
  - コンプライアンス プロファイルがグループ割り当てから削除される

- SCEP 証明書は次の場合に取り消されます。
  - 管理者が SCEP プロファイルを変更または更新する

- ルート証明書は次の場合に削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する
  - コンプライアンス ポリシーがグループ割り当てから削除される

- SCEP 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する

#### <a name="pkcs-certificates"></a>PKCS 証明書

- PKCS 証明書は次の場合に取り消され、*その上*、削除されます。

  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- PKCS 証明書は次の場合に削除されます。
  - コンプライアンス ポリシーがグループ割り当てから削除される
  - コンプライアンス プロファイルがグループ割り当てから削除される
  
- ルート証明書は次の場合に削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- PKCS 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する
  - 管理者が PKCS プロファイルを変更または更新する

## <a name="android--android-enterprise-devices"></a>Android デバイスと Android Enterprise デバイス

#### <a name="scep-certificates"></a>SCEP 証明書

- SCEP 証明書は次の場合に取り消され、*その上*、削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する

- SCEP 証明書は次の場合に取り消されます。
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する
  - デバイスが Azure Active Directory (AD) グループから削除される
  - コンプライアンス ポリシーがグループ割り当てから削除される
  - コンプライアンス プロファイルがグループ割り当てから削除される
  - 管理者が Azure Active Directory (AD) からユーザーまたはグループを削除する
  - 管理者が SCEP プロファイルを変更または更新する

- ルート証明書は次の場合に削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- SCEP 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する

#### <a name="pkcs-certificates"></a>PKCS 証明書

- PKCS 証明書は次の場合に取り消され、*その上*、削除されます。

  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- ルート証明書は次の場合に削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する

- PKCS 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する
  - 管理者が PKCS プロファイルを変更または更新する
  - コンプライアンス プロファイルがグループ割り当てから削除される
  - コンプライアンス ポリシーがグループ割り当てから削除される 

## <a name="macos-certificates"></a>macOS 証明書

#### <a name="scep-certificates"></a>SCEP 証明書

- SCEP 証明書は次の場合に取り消され、*その上*、削除されます。
  - エンドユーザーの登録が解除される
  - 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する
  - デバイスが Azure Active Directory (AD) グループから削除される
  - コンプライアンス ポリシーがグループ割り当てから削除される
  - コンプライアンス プロファイルがグループ割り当てから削除される

- SCEP 証明書は次の場合に取り消されます。
  - 管理者が SCEP プロファイルを変更または更新する

- SCEP 証明書は次の場合にデバイスに**残ります** (証明書は取り消されず、削除されません)。
  - エンドユーザーが Intune ライセンスを失う
  - 管理者が Intune ライセンスを取り消す
  - 管理者が Azure AD からユーザーまたはグループを削除する

> [!NOTE]
> [ワイプ](devices-wipe.md#wipe) アクションを使用して macOS デバイスを工場出荷時の状態にリセットすることはできません。

#### <a name="pkcs-certificates"></a>PKCS 証明書

PKCS 証明書は macOS ではサポートされていません。

