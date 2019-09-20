---
title: Intune でのデータ収集
description: Intune で個人データがどのように収集されるかを学習します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08066c0742ad4ad02f907e55cc84eb65068c9b99
ms.sourcegitcommit: c9725ddae6c0f82a491de27c87f240254d32716b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70986418"
---
# <a name="data-collection-in-intune"></a>Intune でのデータ収集

ユーザーが Intune を使用して会社や個人のデバイスを登録すると、Intune で一部の個人データが収集および共有されます。 Intune では、次のソースから個人データが収集されます。

- Azure portal で管理者の Intune の使用。
- エンド ユーザーのデバイス (Intune 管理の登録時と使用中)。
- (管理者の指示による) サード パーティ サービスでの顧客アカウント。
- 診断、パフォーマンス、使用状況の情報。

Intune では、これらのソースから、[識別済み](#identified-data)、[匿名化済み](#pseudonymized-data)、[集計済み](#aggregated-data)の 3 つのカテゴリに分類される情報が収集されます。

> [!NOTE]
> Microsoft では、いかなる理由でも、Microsoft のサービスによって収集されたデータを第三者に販売することはありません。

## <a name="identified-data"></a>識別済みデータ

Intune によって収集されるほとんどの個人データは、識別済みデータです。 このデータは、ユーザー、デバイス、またはアプリケーションに関連付けられていて、管理の性質上、必要不可欠です。 識別済みデータは、ユーザーのデバイスとアプリケーションを管理し、Intune サービスをプロビジョニングするために使用されます。

Intune によって収集される識別済みデータには、次のようなものが含まれます。 

- ユーザー情報
  - 所有者名またはユーザーの表示名 (AzureUserID で識別される Azure に登録されているユーザーの名前)
  - ユーザー プリンシパル名または電子メール アドレス
  - サード パーティのユーザー識別子 (AppleID など)
- ハードウェア インベントリ情報
  - デバイス名
  - 製造元
  - オペレーティング システム
  - シリアル番号
  - IMEI 番号
  - IP アドレス
  - Wi-Fi MacAddress
  - ICCID
  - 電話番号
- 次のアクティビティに関するデータを含む、監査ログ情報
  - コンピューターの
  - 作成
  - 更新 (編集)
  - 削除
  - 割り当てる
  - リモート タスク
- サポート情報
  - 連絡先情報 (名前、電話番号、電子メール アドレス)
  - Microsoft のサポート、製品、またはカスタマー エクスペリエンスのチーム メンバーとの電子メールによるディスカッション
- アクセス制御情報 (Intune では、このデータを使用して、[ロールベースのアクセス制御](role-based-access-control.md)のような機能を通じて、管理者ロールや機能へのアクセスを管理します)。
  - 静的認証子 (顧客のパスワード)
  - 証明書のプライバシー キー 
- 管理者とアカウント情報
  - 管理者ユーザーの姓と名
  - 管理者ユーザー名
  - UPN (電子メール)
  - 電話番号
  - アカウント所有者の電子メール アドレス
  - 顧客の各 IT 管理者の Active Directory ID
  - 顧客への課金に対する支払いデータ
  - サブスクリプション キー
- 次のようなアプリケーション インベントリ
  - アプリ名
  - のバージョン
  - アプリ ID
  - サイズ
  - インストール場所
  - アプリケーション インベントリ データは、管理者が企業所有のデバイスとしてマークした場合、または準拠しているアプリの機能がオンになっている場合にのみ収集されます。  
- 顧客のサード パーティ テナント ID (Apple ID など)。 

## <a name="pseudonymized-data"></a>匿名化済みデータ

匿名化済みデータは、一意識別子に関連付けられています。この識別子は、通常、システムで生成される値で、それだけでは個人を特定することはできませんが、エンタープライズ サービスをユーザーに提供するために使用されます。 

Intune によって収集される匿名化済みデータには、次のようなものが含まれます。 

- ユーザーまたはデバイスに関連付けられた診断、パフォーマンス、使用状況データ
  - 機能の使用回数
  - 機能に提供されるコマンド
  - サービスの応答時間
  - インストールとその他のプロセスの成功率
  - Intune ポータル サイト アプリのエラー
  - ユーザー識別子とデバイス識別子
  - 参照、相関関係、管理のための識別子 
- デバイスまたはユーザーに関連付けられていないデバイス データ (このデータがデバイスまたはユーザーに関連付けられている場合、Intune では識別済みデータとして扱われます)
  - Intune デバイス ID
  - Azure Active Directory デバイス ID
  - Intune デバイス管理 ID
  - テナント ID
  - アカウント ID
  - EAS デバイス ID
  - プラットフォーム固有の ID
  - iOS デバイス用の AppleID
  - Mac デバイスの MAC アドレス
  - Windows デバイスの Windows ID
- マネージド アプリケーション情報
  - マネージド アプリケーション ID
  - マネージド アプリケーション デバイス タグ
  - Intune デバイス管理 ID
  - Azure Active Directory デバイス ID
  - 暗号化キー

## <a name="aggregated-data"></a>集計済みデータ

集計済みデータは、Intune サービスのプロビジョニングと向上に使用されます。 

Intune によって収集される集計済みデータには、次のようなものが含まれます。 

- すべての Intune テナントからの管理者の使用状況データ (たとえば、管理コンソールとのやり取りで選択された管理コントロール)
- テナント アカウント情報 (このデータは、Intune ブレードから入手できます)
  - 登録したデバイスまたはユーザーの数
  - 識別されたデバイス プラットフォームの数  
  - インストールされているデバイスの数
  - installedDeviceCount: アプリケーションがインストールされているデバイスの数。
  - notApplicableDeviceCount: アプリケーションが適用できないデバイスの数。
  - notInstalledDeviceCount: アプリケーションは適用できるがインストールされていないデバイスの数。
  - pendingInstallDeviceCount: アプリケーションは適用できるがインストールが保留中のデバイスの数。

## <a name="next-steps"></a>次の手順

Intune が個人データを[格納と処理](privacy-data-store-process.md)および[共有](privacy-data-secure-share.md)する方法について確認します。 
