---
title: Android Enterprise フル マネージド デバイスに Intune 登録を設定する
titleSuffix: Microsoft Intune
description: Intune で Android Enterprise フル マネージド デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d8397dea1dca97122aac6716ee3d51295b913538
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885934"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-fully-managed-devices"></a>Android Enterprise フル マネージド デバイスの Intune 登録を設定する 

Android Enterprise フル マネージド デバイスは、1 人のユーザーに関連付けられる会社所有デバイスであり、仕事限定で使用され、私事には使用されません。 管理者はデバイス全体を管理し、次のように、仕事用プロファイルで利用できないポリシー制御を強制できます。
- managed Google Play からのみアプリのインストールを許可する。
- マネージド アプリのアンインストールをブロックする。
- ユーザーがデバイスを工場出荷時の設定にリセットできないようにする、など。

Intune を利用すると、Android Enterprise フル マネージド デバイスなど、会社所有の Android デバイスにアプリや設定を配置できます。 Android Enterprise に関する特定の詳細については、「[Android Enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)」 (Android Enterprise の要件) を参照してください。

## <a name="technical-requirements"></a>技術要件

Android Enterprise フル マネージド デバイスを管理するには、Intune スタンドアロン テナントを用意する必要があります。 フル マネージド デバイスは、従来の Silverlight 管理コンソールでは管理できません。

デバイスを Android Enterprise フル マネージド デバイスとして管理するには、以下の要件を満たす必要があります。

- Android OS バージョン 6.0 以降。
- デバイスは、Google Mobile Services (GMS) に接続できる Android ビルドを実行する必要があります。 デバイスで GMS が利用できて、GMS に接続できる必要があります。

上記の要件が満たされた場合、デバイスの製造元/OEM に制限はありません。

## <a name="set-up-android-enterprise-fully-managed-device-management"></a>Android Enterprise フル マネージド デバイスの管理を設定する

Android Enterprise フル マネージド デバイスの管理を設定するには、次の手順を実行します。

1. モバイル デバイスの管理を準備するには、[MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定する](../fundamentals/mdm-authority-set.md)必要があります。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。
2. [Android Enterprise アカウントに Intune テナント アカウントを接続します](connect-intune-android-enterprise.md)。
3. [会社所有ユーザー デバイスを有効にする](#enable-corporate-owned-user-devices)
4. [フル マネージド デバイスを登録します](#enroll-the-fully-managed-devices)。

### <a name="enable-corporate-owned-user-devices"></a>会社所有ユーザー デバイスを有効にする

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、 **[デバイス]**  >  **[Android]**  >  **[Android の登録]**   >  **[会社が所有する完全に管理されたユーザー デバイス]** の順に選択します。
2. **[会社が所有するユーザー デバイスの登録をユーザーに許可する]** で **[はい]** を選択します。

> [!NOTE]
> *[デバイスは準拠としてマーク済みである必要があります]* コントロールを使用し、**すべてのクラウド アプリ**、**Android** および**ブラウザー**に適用される、Azure AD 条件付きアクセス ポリシーを定義している場合 - このポリシーから **Microsoft Intune** クラウド アプリを除外する必要があります。 これは、Android のセットアップ プロセスで Chrome タブを使用して、登録中にユーザーを認証するためです。 詳細については、「[Azure AD の条件付きアクセスのドキュメント](https://docs.microsoft.com/azure/active-directory/conditional-access/)」を参照してください。

**[はい]** に設定すると、登録トークン (無作為の文字列) と Intune テナントの QR コードが与えられます。 この 1 個の登録トークンは登録するすべてのユーザーに対して有効であり、有効期限はありません。 デバイスの Android OS とバージョンに基づき、トークンと QR コードのいずれかを利用してデバイスを登録できます。

## <a name="enroll-the-fully-managed-devices"></a>フル マネージド デバイスを登録する
これで[フル マネージド デバイスを登録](android-dedicated-devices-fully-managed-enroll.md)できるようになりました。

## <a name="next-steps"></a>次のステップ
- [Android Enterprise フル マネージド デバイス構成ポリシーを追加する](../configuration/device-restrictions-android-for-work.md#device-owner-only)
- [Android Enterprise フル マネージド デバイスのアプリ構成ポリシーを構成する](../apps/app-configuration-policies-use-android.md)

