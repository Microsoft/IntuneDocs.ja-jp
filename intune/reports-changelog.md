---
title: Intune データ ウェアハウスの変更ログ
titlesuffix: Microsoft Intune
description: このトピックには、Microsoft Intune データ ウェアハウス API の変更の一覧が記載されています。
keywords: Intune データ ウェアハウス
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 0f39b0cb758c8c62da2e76ef8eaff07264ff3f3a
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642763"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Intune データ ウェアハウス API の変更ログ

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

常に Intune データ ウェアハウスの最新の更新プログラムをインストールしてください。

## <a name="1808"></a>1808
_リリース日: 2018 年 8 月_

### <a name="v10-collections"></a>v1.0 コレクション  

クエリ パラメーター `api-version=v1.0` を設定することにより、Intune データ ウェアハウスの v1.0 バージョンを使用できるようになりました。 Data Warehouse 内のコレクションに対する更新は本質的に追加であり、既存のシナリオが使用できなくなることはありません。

### <a name="enrollment-failure-collection-released-to-beta"></a>ベータ版にリリースされた Enrollment Failure コレクション

新しい `Enrollment Failure` コレクションが、ベータ版にリリースされました。 このコレクションを使用して、最も一般的なエラーを表示することにより、登録の進行状況がわかります。 


## <a name="1805"></a>1805
_2018 年 5 月リリース_

### <a name="correction-to-device-count-in-devices-collection"></a>**Devices** コレクションのデバイス数の修正 

**Devices** コレクションが修正されました。この修正により、`isDeleted` 属性でフィルター処理される合計デバイス数が少なくなることがあります この減少は修正の結果であり、エラーではありません。 **Devices** コレクションの詳細については、「[デバイス エンティティの参照](reports-ref-devices.md)」を参照してください。 


## <a name="1801"></a>1801
_2018 年 1 月リリース_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Intune データ ウェアハウス アプリケーションのみの認証 <!-- 1867540 -->

Azure Active Directory (Azure AD) を使用してアプリケーションを設定し、Intune データ ウェアハウスに対する認証を実行できます。 詳細については、「[Intune データ ウェアハウス アプリケーションのみの認証](data-warehouse-app-only-auth.md)」を参照してください。

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Azure AD と Intune の資格情報の要件 <!-- 2077525 -->

- Intune データ ウェアハウス (API を含む) にアクセスするときに、Intune ライセンスをユーザーに割り当てる必要がなくなりました。
- Intune のロール名は**レポート**から **Intune データ ウェアハウス**に変更されました。 

    詳細については、「[Azure AD と Intune の資格情報の要件](reports-api-url.md#azure-ad-and-intune-credential-requirements)」を参照してください。

### <a name="odata-query-options----2077711---"></a>OData クエリのオプション <!-- 2077711 -->

OData クエリ パラメーターとして <code>$select</code> を使用できます。 現在のバージョンは、OData クエリ パラメーター <code>$filter</code>、<code>$orderby</code>、<code>$select</code>、<code>$skip</code>、および <code>$top</code> をサポートしています。 詳細については、「[OData クエリのオプション](reports-api-url.md#odata-query-options)」を参照してください。

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>データ ウェアハウス データ モデルの新しいエンティティ <!-- 2077804 -->

 - エンティティ [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus) が追加されました。 **MobileAppDeviceUserInstallStatus** は、特定のデバイスとユーザーのモバイル アプリのインストール状態を表します。
 - エンティティ [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) が追加されました。 **MobileAppInstallState** エンティティは、デバイス、ユーザー、またはその両方を含むグループに割り当てられた後のモバイル アプリケーションのインストール状態を表します。 

## <a name="1710"></a>1710
_リリース日: 2017 年 11 月_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>現在のユーザーという名前の新しいエンティティ コレクションは、現在アクティブなユーザー データに限られています <!-- 1544273 -->

**ユーザー** エンティティ コレクションには、社内のすべての Azure Active Directory (Azure AD) ユーザーと割り当てられているライセンスが表示されます。 これらのレコードには、ユーザーが削除されている場合でも、データ コレクション期間中のユーザーの状態が含まれます。 たとえば、ユーザーが Intune に追加され、過去 1 か月の過程で削除されたとします。 このユーザーがレポートの時点では存在しない一方で、ユーザーと状態はデータに存在します。 データ内のユーザーの履歴における存在の期間を示すレポートを作成できます。

これに対し、新しい**現在のユーザー** エンティティ コレクションには、削除されていないユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションには、現在アクティブなユーザーのみが含まれています。 **現在のユーザー** エンティティ コレクションの詳細については、「[現在のユーザー エンティティのリファレンス](reports-ref-current-user.md)」をご覧ください。

## <a name="1709"></a>1709
_リリース日: 2017 年 10 月_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune データ ウェアハウスのデータ モデルに追加されたユーザー デバイス関連付けエンティティ コレクション <!-- 1187917 -->

ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。 このデータ モデルは、OData エンドポイントを使うか、カスタム クライアントを開発すると、[Data Warehouse Intune]\(データ ウェアハウス Intune\) ページから取得した Power BI ファイル (PBIX) を使ってアクセスできます。 詳細については、「[ユーザー デバイスの関連付け](reports-ref-user-device.md)」をご覧ください。

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>データ ウェアハウス データ モデルの新しいエンティティ <!-- 1479526 --><!-- -->

 - [**UserDeviceAssociation**](reports-ref-user-device.md) というエンティティが追加されました。 **UserDeviceAssociation** には、組織内のユーザー デバイスの関連付けが含まれています。 ユーザーとデバイスのエンティティ コレクションを関連付けるユーザー デバイス関連付け情報を使って、レポートやデータの視覚エフェクトを作成できるようになりました。  
 - [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) というエンティティが追加されました。 **IntuneManagementExtension** には、バージョンやインストール状態などの情報を追跡するモバイル デバイスのエンティティが含まれます。

## <a name="next-steps"></a>次の手順
 - [週ごとにまとめた Intune の新機能](whats-new.md)を参照してください。 今後の変更、サービスに関する重要なお知らせ、過去のリリースに関する情報も確認できます。
 - [Microsoft Intune のブログ](https://go.microsoft.com/fwlink/?LinkID=273882)を参照してください。
