---
title: GCC High 環境と DoD 環境用のアプリ
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用して、GCC High 環境と DoD 環境に関連するアプリについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a6c430ab15c40166e8c3afbccd6fcc7c2c5976d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72507256"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Intune を使用して GCC High 環境および DoD 環境でアプリを展開する 

Microsoft Intune は、テナント管理者がワークフォースにアプリを配布するために使用できます。 ワークフォースは会社の従業員で、アプリのユーザーです。 GCC High 環境または DoD 環境で Intune から展開できるアプリには多くの種類があります。 管理者が、カスタム作成された、サード パーティ ベンダーによって作成された、または[ビジネス向け Microsoft Store](https://businessstore.microsoft.com/store) からダウンロードしたオフライン アプリとして、GCC High または DoD の対象ユーザー向けに Windows アプリをアップロードして配布する必要がある場合には、管理者はそれを[基幹業務アプリ](apps-add.md#app-types-in-microsoft-intune)として配布することを選択できます。  

> [!NOTE]
> 商用環境では、テナント管理者は自社のビジネス向けストアと Intune を同期させることができますが、GCC High 環境と DoD 環境では、このサービスは利用できません。 このような状況では、管理者は Intune にアプリを直接アップロードして展開する必要があります。  

## <a name="add-line-of-business-apps-using-intune"></a>Intune を使用して基幹業務アプリを追加する 

Intune を使用して、GCC High 環境または DoD 環境向けに基幹業務アプリを追加するには、[Windows LOB アプリ](lob-apps-windows.md)の指示に従って行うことができます。 ビジネス向け Microsoft Store からポータル サイトを最初に展開することもできます。 ポータル サイトの使用を選択した場合は、ポータル サイトを手動でインストールして展開できます。 詳細については、「[Microsoft Intune ポータル サイト アプリを構成する方法](company-portal-app.md)」を参照してください。 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Intune を使用してビジネス向けストアからオフライン アプリを配布する  

ビジネス向け Microsoft Store から[オフライン ライセンス付きアプリのダウンロード](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app)をする必要がある場合は、次の手順を実行してアプリケーションをダウンロードします。 

1. [ビジネス向けストア](https://businessstore.microsoft.com/)にサインインします。
2. **[管理]**  >  **[設定]** の順に選択します。
3. **[Shopping Experience]\(ショッピング体験\)** の **[Show offline apps]\(オフライン アプリの表示\)** を **[オン]** に設定します。

アプリの購入時にオフライン バージョンが利用可能な場合は、ライセンスの種類をオフラインに変更することもできます。 アプリを取得した後で、[ビジネス向けストア](https://businessstore.microsoft.com/)で **[管理]**  >  **[Products & Services]\(製品およびサービス\)** を選択してアプリを管理できます。 さらに、アプリとその依存関係をダウンロードすることができます。 次に、Intune を使用してユーザーにこのダウンロードしたアプリ (とその依存関係) を展開できます。  

## <a name="syncing-intune-to-the-store-for-business"></a>Intune をビジネス向けストアと同期させる 

商用 (非政府) 環境では、管理者は Intune をビジネス向け Microsoft Store と同期させることができます。 この機能は政府機関の環境では使用できません。 商用環境での Intune と政府機関の環境での Intune の違いについて詳しくは、「[米国政府機関サービス向け Enterprise Mobility + Security の説明](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)」を参照してください。  

Intune をビジネス向け Microsoft ストアのアカウントに同期するには、「[ビジネス向け Microsoft ストアから購入したアプリを Microsoft Intune で管理する方法](windows-store-for-business.md)」を参照してください。  

## <a name="compliance"></a>コンプライアンス 

これらのサービスが適切に使用されているかを評価するときは、アプリのプライバシーとコンプライアンスのステートメントを確認し、それらを自身の組織のコンプライアンス、セキュリティ、プライバシーの要件と比較します。   

## <a name="next-steps"></a>次の手順

アプリの展開と割り当てに関する詳細については、「[Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)」を参照してください。

 
