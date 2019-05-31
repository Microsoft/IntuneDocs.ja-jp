---
title: Microsoft Intune ライセンスを割り当てる
description: Intune に登録できるようにライセンスをユーザーに割り当てる
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14d5e01577100e0a66cfcf6ce935289a1dc26fab
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57459902"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Intune にデバイスを登録できるようにライセンスをユーザーに割り当てる

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

ユーザーを手動で追加する場合も、オンプレミスの Active Directory から同期する場合も、まず各ユーザーに Intune のライセンスを割り当ててから、Intune にデバイスを登録する必要があります。 ライセンスのリストについては、「[Licenses that include Intune](licenses.md)」 (Intune が含まれているライセンス) を参照してください。

## <a name="assign-an-intune-license-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターで、Intune のライセンスを割り当てる

[Microsoft 365 管理センター](http://go.microsoft.com/fwlink/p/?LinkId=698854)を使用して、手動でクラウドベースのユーザーを追加し、クラウドベースのユーザー アカウントと、オンプレミスの Active Directory から Azure AD に同期されているアカウントの両方にライセンスを割り当てることができます。

1. テナント管理者の資格情報を使用して [Microsoft 365 管理センター](http://go.microsoft.com/fwlink/p/?LinkId=698854)にサインインした後、 **[ユーザー]**  >  **[アクティブ ユーザー]** の順に選択します。

2. Intune ユーザー ライセンスを割り当てるユーザー アカウントを選択し、 **[製品ライセンス]**  >  **[編集]** の順に選択します。

3. **Intune** または **Enterprise Mobility + Security** を **[オン]** に切り替えて、 **[保存]** を選択します。

   ![Microsoft 365 管理センターの [製品ライセンス] セクションのスクリーンショット](./media/office-assign-license.png)

4. ユーザー アカウントが、サービスを使用してデバイスを管理に登録するために必要なアクセス許可を持つようになります。

> [!NOTE]
> デバイスを登録すると、管理コンソールにユーザーが表示されます。 また、編集するユーザーのグループを一度に選択して、選択したすべてのユーザーに対してライセンスを追加したり交換することができます。

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Azure Active Directory を使用して Intune のライセンスを割り当てる

Azure Active Directory を使用してユーザーに Intune ライセンスを割り当てることもできます。 詳しくは、[Azure Active Directory でのユーザーへのライセンスの割り当て](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal)に関するページをご覧ください。 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>School Data Sync を使って Intune for Education のユーザーにライセンスを割り当てる
教育組織の場合、School Data Sync (SDS) を使用して Intune for Education のライセンスを同期されたユーザーに割り当てることができます。 SDS プロファイルを設定するときに、Intune for Education のチェック ボックスをオンにするだけです。  

![SDS プロファイル設定のスクリーンショット](./media/i4e-sds-profile-setup-setting.png)

Intune for Education のライセンスを割り当てるときは、Intune A Direct のライセンスも割り当てられることを確認してください。

![製品ライセンス セットアップのスクリーンショット](./media/i4e-set-licenses.png)

SDS について詳しくは、「[School Data Sync と Classroom の概要](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)」をご覧ください。

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>ユーザー ライセンスとデバイス ライセンスがサービスへのアクセスに与える影響
* ユーザー ソフトウェア ライセンスが割り当てられた各**ユーザー**は、オンライン サービスと関連するソフトウェア (System Center ソフトウェアを含む) にアクセスしてそれらを使用し、複数のアプリケーションと最大 15 台のデバイスを管理できます。
* ユーザー ライセンスとは別にあらゆるデバイス用のライセンスを購入できます。 デバイス ライセンスはデバイスに割り当てる必要はありません。 オンライン サービスと関連ソフトウェア (System Center ソフトウェアを含む) にアクセスして使用する各デバイスに、デバイス ライセンスが必要です。
* デバイスが 2 人以上のユーザーによって使用される場合は、各デバイスにデバイス ソフトウェア ライセンス、またはすべてのユーザーにユーザー ソフトウェア ライセンスが必要です。

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>購入したライセンスの種類について

Intune の購入方法により、サブスクリプション情報が決まります。

- Enterprise Agreement を通じて Intune を購入された場合は、ボリューム ライセンス ポータルの **[サブスクリプション]** で、ご自分のサブスクリプション情報を見つけることができます。
- クラウド ソリューション プロバイダーを通じて Intune を購入された場合は、販売店に確認してください。
- CC # または請求書で Intune を購入された場合、ライセンスはユーザー ベースになります。




## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>PowerShell を使用して、EMS ユーザー ライセンスを選択的に管理する
Microsoft Enterprise Mobility + Security (旧 Enterprise Mobility Suite) を使用している組織には、EMS パッケージの Azure Active Directory Premium または Intune サービスのみを必要とするユーザーがいる可能性があります。 [Azure Active Directory PowerShell コマンドレット](https://msdn.microsoft.com/library/jj151815.aspx)を使用して、いずれかのサービスまたはサービスのサブセットを割り当てることができます。

EMS サービスのユーザー ライセンスを選択的に割り当てるには、[Azure Active Directory Module for Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) がインストールされているコンピューターで管理者として PowerShell を開きます。 PowerShell は、ローカル コンピューターまたは ADFS サーバーにインストールできます。

目的のサービス プランにのみ適用される新しいライセンス SKU 定義を作成する必要があります。 これを行うには、適用しないプランを無効にします。 たとえば、Intune ライセンスを割り当てないライセンス SKU 定義を作成できます。 利用できるサービスの一覧を確認するには、次のコマンドを入力します。

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

次のコマンドを実行すると、Intune サービス プランを除外できます。 同じメソッドを使用して、セキュリティ グループ全体に展開することや、より詳細なフィルターを使用することができます。

**例 1**<br>
コマンド ラインで、新しいユーザーを作成し、ライセンスに含まれる Intune を有効にせずに EMS ライセンスを割り当てます。

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


次のコマンドで確認します。

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**例 2**<br>
ライセンスが既に割り当てられているユーザーに対して、EMS ライセンスに含まれる Intune を無効にします。

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

次のコマンドで確認します。

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)
