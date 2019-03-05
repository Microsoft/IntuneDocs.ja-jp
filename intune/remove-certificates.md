---
title: Microsoft Intune で SCEP または PKCS 証明書を削除する - Azure | Microsoft Docs
titleSuffix: ''
description: 管理者は "ワイプ" アクションまたは "インベントリからの削除" アクションを利用し、Microsoft Intune から証明書を削除できます。 デバイスの登録解除やコンプライアンス ポリシーの削除など、一部のシナリオでは証明書が自動的に削除されます。 Intune ライセンスが失われたり、削除されたりしたときなど、証明書が自動的にデバイスに残るシナリオもあります。 Android、Android エンタープライズ、iOS、macOS、Windows デバイス用のさまざまな方法をご確認ください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 977e7006d39ae76516d5b06019e463d1018aaa79
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229260"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Microsoft Intune で SCEP 証明書と PKCS 証明書を削除する

Microsoft Intune では、Simple Certificate Enrollment Protocol (SCEP) 証明書と Public Key Cryptography Standards (PKCS) 証明書をデバイスに追加できます。 これらの証明書は、デバイスから[ワイプ](devices-wipe.md#wipe)したり、[インベントリから削除](devices-wipe.md#retire)したりするときにも削除できます。 

証明書が自動的に削除されるシナリオや、証明書がデバイスに残るシナリオもあります。 この記事では、一般的なシナリオと、PKCS 証明書と SCEP 証明書への影響を紹介します。

> [!NOTE]
> オンプレミスの Active Directory または Azure Active Directory (Azure AD) から削除されるユーザーの証明書を削除して取り消すには、次の手順を順番に実行します。
>
> 1. ユーザーのデバイスをワイプします (または、インベントリから削除します)。
> 2. オンプレミスの Active Directory または Azure AD からユーザーを削除します。

## <a name="windows-devices"></a>Windows デバイス

#### <a name="scep-certificates"></a>SCEP 証明書

SCEP 証明書は次の場合に取り消され、*その上*、削除されます。

- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。
- Azure AD グループからデバイスが削除される。
- 証明書プロファイルがグループ割り当てから削除される。

SCEP 証明書は次の場合に取り消されます。
- 管理者が SCEP プロファイルを変更または更新する。

ルート証明書は次の場合に削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

SCEP 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。

#### <a name="pkcs-certificates"></a>PKCS 証明書

PKCS 証明書は次の場合に取り消され、*その上*、削除されます。

- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

ルート証明書は次の場合に削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

PKCS 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。
- 管理者が PKCS プロファイルを変更または更新する。
- 証明書プロファイルがグループ割り当てから削除される。


## <a name="ios-devices"></a>iOS デバイス

#### <a name="scep-certificates"></a>SCEP 証明書

SCEP 証明書は次の場合に取り消され、*その上*、削除されます。

- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。
- Azure AD グループからデバイスが削除される。
- 証明書プロファイルがグループ割り当てから削除される。

SCEP 証明書は次の場合に取り消されます。
- 管理者が SCEP プロファイルを変更または更新する。

ルート証明書は次の場合に削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

SCEP 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。

#### <a name="pkcs-certificates"></a>PKCS 証明書

PKCS 証明書は次の場合に取り消され、*その上*、削除されます。

- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

PKCS 証明書は次の場合に削除されます。
- 証明書プロファイルがグループ割り当てから削除される。
  
ルート証明書は次の場合に削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

PKCS 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。
- 管理者が PKCS プロファイルを変更または更新する。

## <a name="android-knox-devices"></a>Android KNOX デバイス

#### <a name="scep-certificates"></a>SCEP 証明書

SCEP 証明書は次の場合に取り消され、*その上*、削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。

SCEP 証明書は次の場合に取り消されます。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。
- Azure AD グループからデバイスが削除される。
- 証明書プロファイルがグループ割り当てから削除される。
- 管理者が Azure AD からユーザーまたはグループを削除する。
- 管理者が SCEP プロファイルを変更または更新する。

ルート証明書は次の場合に削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

SCEP 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。

#### <a name="pkcs-certificates"></a>PKCS 証明書

PKCS 証明書は次の場合に取り消され、*その上*、削除されます。

- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

ルート証明書は次の場合に削除されます。
- ユーザーの登録が解除される。
- 管理者が[ワイプ](devices-wipe.md#wipe) アクションを実行する。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。

PKCS 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。
- 管理者が PKCS プロファイルを変更または更新する。
- 証明書プロファイルがグループ割り当てから削除される。
  
  
> [!NOTE]
> Android for Work デバイスは、上記のシナリオで検証されていません。 Android の従来のデバイス (Samsung 以外のすべての、仕事用プロファイル以外のデバイス) では証明書の削除が無効です。 

## <a name="macos-certificates"></a>macOS 証明書

#### <a name="scep-certificates"></a>SCEP 証明書

SCEP 証明書は次の場合に取り消され、*その上*、削除されます。
- ユーザーの登録が解除される。
- 管理者が[インベントリからの削除](devices-wipe.md#retire)アクションを実行する。
- Azure AD グループからデバイスが削除される。
- 証明書プロファイルがグループ割り当てから削除される。

SCEP 証明書は次の場合に取り消されます。
- 管理者が SCEP プロファイルを変更または更新する。

SCEP 証明書は次の場合にデバイスに*残ります* (証明書は取り消されず、削除されません)。
- エンドユーザーが Intune ライセンスを失う。
- 管理者が Intune ライセンスを取り消す。
- 管理者が Azure AD からユーザーまたはグループを削除する。

> [!NOTE]
> [ワイプ](devices-wipe.md#wipe) アクションを使用して macOS デバイスを工場出荷時の状態にリセットすることはできません。

#### <a name="pkcs-certificates"></a>PKCS 証明書

PKCS 証明書は macOS ではサポートされていません。

