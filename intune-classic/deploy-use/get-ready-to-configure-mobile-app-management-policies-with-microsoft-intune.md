---
title: MAM ポリシーの前提条件
description: このトピックでは、モバイル アプリ管理ポリシーを作成する前にユーザーを設定するための前提条件について説明します。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e6a85e7-e007-41b6-9034-64d77f547b87
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 52cba4de7d19744e1a011071ac6c9bbb168ffb30
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024075"
---
# <a name="get-ready-to-configure-app-protection-policies-in-the-azure-portal"></a>Azure ポータルでアプリ保護ポリシーを構成する準備をする

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

このトピックでは、Azure ポータルでアプリ保護ポリシーを作成する**前に**完了しておく必要がある前提条件と手順について説明します。

Intune アプリ保護ポリシーで会社のデータを守る方法については、[アプリ保護ポリシーを使用したアプリとデータの保護](protect-apps-and-data-with-microsoft-intune.md)に関する記事をご覧ください。

## <a name="what-is-the-azure-portal"></a>Azure ポータルとは?

Azure ポータルはアプリ保護ポリシーを作成するための新しい管理コンソールです。 Azure Portal では、次の MAM シナリオをサポートします。
- Intune に登録されたデバイス
- 別のモバイル デバイス管理 (MDM) ソリューションによって管理されるデバイス
- MDM ソリューションで管理されないデバイス (BYOD)

現在のところ、**Intune 管理者コンソール**と **Azure ポータル**の両方でアプリ保護ポリシーを構成できます。  次の点を考慮します。

* **Azure Portal**  で作成するポリシーは、上記の**すべての MAM シナリオ**でサポートされます。 **Intune 管理者コンソール**は、**Intune で登録し、管理するデバイス**のポリシー作成にのみ対応しています。

* **新しい設定**は **Azure ポータル**にのみ追加できるため、一部のアプリ ポリシー設定は Intune 管理者コンソールに表示されない場合があります。

* Intune 管理コンソールと Azure ポータルの**両方**でアプリ保護ポリシーを作成した場合、**Azure ポータルのポリシーがアプリに適用され、ユーザーにデプロイされます**。
    * Intune 管理コンソールで作成したアプリ保護ポリシーを Azure ポータルにインポートすることはできません。  Azure ポータルでアプリ保護ポリシーを作成し直す必要があります。


* アプリやアプリ構成ポリシーの展開などの、**他のアプリ管理機能**は、現在のところ、**Intune 管理コンソール**でのみ利用できます。


初めて Azure ポータルを使用する場合は、[Azure ポータルの Microsoft Intune アプリ保護ポリシー対応](azure-portal-for-microsoft-intune-mam-policies.md)に関する記事で Azure ポータルの基本をご確認ください。

Intune 管理コンソールでアプリ ポリシーを作成する方法については、[Microsoft Intune コンソールでのアプリ保護ポリシーの構成とデプロイ](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)に関する記事をご覧ください。


##  <a name="supported-platforms"></a>サポートされているプラットフォーム
- iOS 8.1 以降
- Android 4 以降
- Windows 10

>[!NOTE]
>バージョン 1703 より、アプリの保護ポリシーを、MAM に登録シナリオなしで Windows 10 デバイスに対して定義することができます。 詳細については、「[Protect your enterprise data using Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)」 (Windows 情報保護 (WIP) を使用してエンタープライズ データを保護する) を参照してください。

##  <a name="supported-apps"></a>サポートされているアプリ
* **Microsoft アプリ:** これらのアプリには Intune App SDK が組み込まれているので、アプリ保護ポリシーを適用する前に必要な処理はありません。
サポートされている Microsoft アプリの完全な一覧については、Microsoft Intune アプリケーション パートナー ページの [Microsoft Intune モバイル アプリケーション ギャラリー](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)を参照してください。 アプリをクリックし、サポートされるシナリオ、プラットフォーム、アプリのマルチ ID 対応について確認してください。

* **社内で構築した基幹業務アプリ:** アプリ保護ポリシーを適用する前に、Intune App SDK を含めるようにアプリを準備する必要があります。

  * Intune で管理されているデバイスについては、「[Decide how to prepare apps for MAM](/intune/apps-prepare-mobile-application-management)」 (MAM 用にアプリを準備する方法を決める) を参照してください。

  * 従業員が所有するデバイスなど管理対象ではないデバイスや、別のモバイル デバイス管理ソリューションで管理されているデバイスの場合は、「[Microsoft Intune に登録されていないデバイスの基幹業務アプリとデータを保護する](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)」を参照してください。

## <a name="prerequisites"></a>必要条件

- **Microsoft Intune サブスクリプション**。 アプリ保護ポリシーが適用されているアプリを入手するには、Intune ライセンスが必要です。
  デバイスを管理するために現在 Intune を使用している場合、既に Intune サブスクリプションを所有していることになります。 Enterprise Mobility Suite (EMS) ライセンスを購入している場合も、Intune サブスクリプションを所有しています。 MAM 機能を調べるために Intune を試してみる場合は、試用アカウントを [Microsoft Intune Web ページ](https://www.microsoft.com/server-cloud/products/microsoft-intune/)から取得できます。

  自分が Intune サブスクリプションを所有しているかどうかを確認するには、Office ポータルの**課金情報**のページをご覧ください。  サブスクリプションを所有している場合は、Intune が **Active** になっているはずです。

- **Office 365 サブスクリプション**。これは、以下で必要となります。

  - 複数の ID をサポートするアプリにアプリ保護ポリシーを適用する。

  - SharePoint Online および Exchange Online 作業アカウントを作成する。 Exchange On-Premises と SharePoint On-Premises はサポートされていません。

- **Skype for Business Online の先進認証の設定**。 詳細については、「[Enable modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)」 (先進認証の有効化) をご覧ください。


- ユーザーを作成するための Azure Active Directory (Azure AD)。 Azure AD では、ユーザーがアプリを開いて作業用の資格情報を入力するときに、ユーザーを認証します。

    > [!NOTE]
    > ユーザー グループは Azure AD で設定する必要があります。 Azure ポータルで Intune ユーザー グループを利用してアプリ保護ポリシーをデプロイすることはできません。

### <a name="create-users-and-assign-microsoft-intune-licenses"></a>ユーザーの作成と Microsoft Intune ライセンスの割り当て

1.  管理者資格情報で [Office ポータル](https://portal.office.com)にサインインします。

2.  [Intune の評価ガイド](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune)の、**Intune の 30 日間評価版の完了手順**のセクションにある説明に従ってユーザーを追加して、Intune ライセンスを割り当てます。 ユーザーが Office ポータル、Azure AD ポータル、Azure ポータルにアクセスできるようにするには、**全体管理者ロール**をユーザーに割り当てます。

5.  アプリ保護ポリシーは、Azure Active Directory のユーザー グループにデプロイされます。 アプリ保護ポリシーのユーザー グループを作成するには、「[評価版のサブスクリプションのユーザーとデバイスを編成するグループを作成する](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3)」の「**ユーザー グループを作成する**」セクションの説明にあるようにユーザー グループを作成します。

### <a name="assign-roles-to-non-global-admin-users"></a>グローバル管理者でないユーザーにロールを割り当てる

全体管理者には [Azure ポータル](https://portal.azure.com)へのアクセス権があります。  グローバル管理者ではないユーザーもポリシーを構成して他のモバイル アプリ管理タスクを実行できるようにする場合は、「[Azure サブスクリプション リソースへのアクセスをロールの割り当てによって管理する](https://azure.microsoft.com/documentation/articles/role-based-access-control-configure/)」の記事をご確認ください。

## <a name="next-steps"></a>次の手順
[Microsoft Intune でのアプリ保護ポリシーの作成とデプロイ](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
