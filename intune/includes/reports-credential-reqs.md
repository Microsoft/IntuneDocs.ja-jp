---
ms.openlocfilehash: 015e50d24149a6b6242eda86d5f3d62489e9955d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61511331"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Azure AD と Intune の資格情報の要件

認証と承認は、Azure AD の資格情報と Intune のロールベースのアクセス制御 (RBAC) に基づいています。 すべての全体管理者およびテナントの Intune サービス管理者は、既定でデータ ウェアハウスに対するアクセス権を持っています。 Intune ロールを使用して、他のユーザーにアクセス権を付与するには、**Intune データ ウェアハウス** リソースへのアクセス権を付与します。

Intune データ ウェアハウス (API を含む) にアクセスするための要件は次のとおりです。

  -  ユーザーは次のいずれかである必要があります
      -  Azure AD 全体管理者
      -  Intune サービス管理者
      -  **Intune データ ウェアハウス** リソースへのロールベース アクセス権を持つユーザー
      -  [アプリケーションのみの認証](../data-warehouse-app-only-auth.md)を使用するユーザーなしの認証 
