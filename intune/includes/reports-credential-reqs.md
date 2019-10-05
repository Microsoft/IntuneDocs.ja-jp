---
ms.openlocfilehash: 8483ed3d4198e228bdaaf4723b2c9c0dca9cecfc
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830506"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Azure AD と Intune の資格情報の要件

認証と承認は、Azure AD の資格情報と Intune のロールベースのアクセス制御 (RBAC) に基づいています。 すべての全体管理者およびテナントの Intune サービス管理者は、既定でデータ ウェアハウスに対するアクセス権を持っています。 Intune ロールを使用して、他のユーザーにアクセス権を付与するには、**Intune データ ウェアハウス** リソースへのアクセス権を付与します。

Intune データ ウェアハウス (API を含む) にアクセスするための要件は次のとおりです。

- ユーザーは次のいずれかである必要があります
  - Azure AD 全体管理者
  - Intune サービス管理者
  - **Intune データ ウェアハウス** リソースへのロールベース アクセス権を持つユーザー
  - [アプリケーションのみの認証](../developer/data-warehouse-app-only-auth.md)を使用するユーザーなしの認証 
