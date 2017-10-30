<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Azure AD と Intune の資格情報の要件

認証と承認は、Azure AD の資格情報と Intune のロールベースのアクセス制御 (RBAC) に基づいています。 すべての全体管理者およびテナントの Intune サービス管理者は、既定でデータ ウェアハウスに対するアクセス権を持っています。 Intune ロールを使用して、他のユーザーにアクセス権を付与するには、**レポート リソース**へのアクセス権を付与します。

Intune データ ウェアハウス (API を含む) にアクセスするための要件は次のとおりです。

  -  Intune ライセンスをユーザーに割り当てる必要があります
  -  ユーザーは次のいずれかである必要があります
      -  Azure AD 全体管理者
      -  Intune サービス管理者
      -  **レポート** リソースに対してロールベースのアクセス権を持つユーザー