---
title: "GPO と Intune ポリシーの競合を解決する"
description: "グループ ポリシーと Intune 構成ポリシーの競合を解決する方法について説明します。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f6d12dd886fe475161e767e63177313a729e170d
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>グループ ポリシー オブジェクト (GPO) と Microsoft Intune ポリシーの競合を解決する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune は、Windows PC の設定を管理するためにポリシーを使用します。 たとえば、ポリシーを使用して、PC の Windows ファイアウォールに関する設定を制御できます。 多くの Intune 設定は、Windows グループ ポリシーで構成する設定と似ています。 ただし、この 2 つの設定が互いに競合することがあります。

競合が発生した場合、PC がドメインにサインインできない場合を除き、ドメインレベルのグループ ポリシーの方が Intune ポリシーより優先されます。 ドメインにログオンできない場合は、Intune ポリシーがクライアント PC に適用されます。

## <a name="what-to-do-if-you-are-using-group-policy"></a>グループ ポリシーを使用する場合の操作
適用するポリシーがグループ ポリシーの管理対象かどうかを確認してください。 競合を回避するために、次の方法の 1 つまたは複数を使用できます。

-   グループ ポリシー設定が適用されない Active Directory 組織単位 (OU) に PC を移動してから、Intune クライアントをインストールします。 また、Intune に登録されている PC を含む OU にグループ ポリシー設定を適用しない場合は、その OU へのグループ ポリシーの継承をブロックすることもできます。

-   セキュリティ グループ フィルターを使用して、Intune で管理されていない PC のみに GPO を制限します。

-   Intune ポリシーと競合するグループ ポリシー オブジェクトを無効にするか削除します。

Active Directory と Windows グループ ポリシーの詳細については、Windows Server のマニュアルを参照してください。

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>既存の GPO をフィルターして Intune ポリシーとの競合を回避する方法
Intune ポリシーと設定が競合するグループ ポリシー オブジェクト (GPO) を見つけたら、セキュリティ グループ フィルターを使用して、Intune で管理しない PC のみにこれらの GPO が適用されるようにします。

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


GPO は、グループ ポリシー管理コンソールで、選択した GPO の **[セキュリティ フィルター処理]** に指定されているセキュリティ グループのみに適用できます。 既定では、GPO は *[認証されたユーザー]* に適用されます。

-   **[Active Directory ユーザーとコンピューター]** スナップインで、Intune で管理しないコンピューターとユーザー アカウントを含む新しいセキュリティ グループを作成します。 このグループに *Not In Microsoft Intune* などの名前を設定します。

-   グループ ポリシー管理コンソールで、選択した GPO の **[委任]** タブを開き、新しいセキュリティ グループを右クリックして、適切な**読み取り**アクセス許可と**グループ ポリシーの適用**アクセス許可をセキュリティ グループ内のユーザーとコンピューターの両方に委任できます。 (**グループ ポリシーの適用** アクセス許可は **[詳細設定]** ダイアログ ボックスで使用できます)。

-   次に、選択した GPO に新しいセキュリティ グループ フィルターを適用し、既定の **[認証されたユーザー]** フィルターを解除します。

新しいセキュリティ グループは、Intune サービス変更の登録として保持する必要があります。

### <a name="see-also"></a>関連項目
[Microsoft Intune を使用して Windows PC を管理する](manage-windows-pcs-with-microsoft-intune.md)
