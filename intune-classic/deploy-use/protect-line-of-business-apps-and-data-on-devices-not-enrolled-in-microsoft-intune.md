---
title: "登録されていないデバイスで LOB アプリを保護する"
description: "このトピックでは、データの損失を防ぐことができるモバイル アプリケーション管理ポリシーを適用できるように、カスタム基幹業務アプリを準備する方法について説明します。"
keywords: 
author: mattbriggs
ms.author: mabriggs
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0fbc7ae1937aff60e8e494df06ee2c30e2fe8855
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="protect-line-of-business-apps-and-data-on-devices-that-are-not-enrolled-in-microsoft-intune"></a>Microsoft Intune に登録されていないデバイスの基幹業務アプリとデータを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

モバイル アプリケーション管理 (MAM) ポリシーでは、会社のデータを保護するために、会社データが漏洩する可能性があるアクションを制限し、アプリ PIN などのデータ アクセス要件を強制することができます。 MAM ポリシーを iOS または Android の基幹業務アプリに適用するには、最初に Microsoft Intune アプリ ラッピング ツールを使用してアプリをラップする必要があります。 アプリ ラッピングは、モバイル アプリを何も変更することなく管理レイヤーを適用するプロセスで、モバイル アプリはユーザーに配布されます。  

このトピックでは、**従業員が所有している管理外のデバイス**からアクセスするアプリと、**サード パーティ製のモバイル デバイス管理 (MDM) ソリューション**で管理されているデバイスに MAM ポリシーを適用する手順を説明します。  **Intune MDM に登録されているデバイス**で実行されている基幹業務アプリを準備するには、「[Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](/intune/apps-prepare-mobile-application-management)」をご覧ください。


##  <a name="step-1-prepare-the-app"></a>手順 1: アプリを準備する

MAM ポリシーをアプリに適用する前に、まず Microsoft Intune アプリ ラッピング ツール ([iOS](/intune/app-wrapper-prepare-ios) 用、[Android](/intune/app-wrapper-prepare-android) 用) を使用してアプリをラップする必要があります。あるいは、[Intune アプリ SDK](/intune/app-sdk) を利用し、Intune アプリ保護機能を手動で統合します。

アプリ ラッピング ツールと SDK の比較については、「[Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](/intune/apps-prepare-mobile-application-management)」を参照してください。

## <a name="step-2-add-the-app"></a>手順 2: アプリを追加する

MAM ポリシーと基幹業務アプリを関連付けるには、次の手順を使用して Intune のサブスクリプションとテナントにアプリの詳細を追加する必要があります。

1. [Azure Portal](https://portal.azure.com/) で **[Intune モバイル アプリケーション管理]**、**[設定]** に進み、**[基幹業務アプリ]** を選択します。

   ![基幹業務オプションを示す [設定] ブレードのスクリーン ショット](../media/mam-azure-portal-lob-on-settings.png)

2. **[基幹業務アプリ]** ブレードで、**[カスタム アプリの追加]** を選択します。

   ![[カスタム アプリの追加] ボタンが上部に示された [基幹業務アプリ] ブレードのスクリーンショット](../media/mam-azure-portal-add-lob-app-action.png)
3. アプリの名前、[アプリ ID] フィールドにバンドル ID、プラットフォーム (iOS または Android) を指定します。

   ![[カスタム アプリの追加] ブレードのスクリーン ショット](../media/mam-azure-portal-add-app-details.png)

   この手順で、アプリは一意のものとして一覧表示されます。 アプリは、次の手順で説明するように、テナントの MAM ポリシーの対象アプリの一覧にも表示されるようになります。

## <a name="step-3-apply-mam-policies"></a>手順 3: MAM ポリシーを適用する
サービスにアプリのメタデータがアップロードされると、アプリはアプリ一覧に表示されます。 [新しいポリシーまたは既存のポリシーを作成し](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)、手順 2. で追加した基幹業務アプリに適用できます。

>[!IMPORTANT]
>ラップされたアプリを使用するユーザーに対して、MAM ポリシーを指定する必要があります。  このポリシーを展開されていないユーザーは、アプリを使用できません。


  ![新しい基幹業務アプリが示された [対象アプリ] 一覧が示されたブレードのスクリーンショット](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>手順 4: アプリを配布する
アプリはユーザーに、次の方法で配布できます。
* デバイスがサード パーティ製の MDM ソリューションに登録されている場合、MDM ソリューションを介してアプリを配布できます。
* デバイスが MDM ソリューションで管理されていない場合には、カスタム ソリューションが必要です。 ユーザーは自分のデバイスにアプリをダウンロードしてインストールする必要があります。

## <a name="change-the-metadata"></a>メタデータを変更する
アプリ名、バンドル ID などのアプリの詳細を変更する必要がある場合、[アプリを削除し](#remove-apps)、それに新しいメタデータを[追加](#step-2-add-the-app)する必要があります。

##  <a name="remove-apps"></a>アプリを削除する
アプリの一覧から基幹業務アプリを削除できます。 これを行うと、アプリは一覧から削除され、MAM ポリシーとの関連付けが削除されますが、ユーザーのデバイスからアプリが削除されたり、アンインストールされたりすることはありません。  

1. [Azure Portal](https://portal.azure.com/) の **[Intune モバイル アプリケーション管理]**、**[設定]** に進みます。 **[設定]** ブレードで、**[基幹業務]** を選択し、既存のアプリの一覧を開きます。  
2. 削除するアプリを選択し、**(...) のコンテキスト** メニューを選択します。

   ![省略記号がある基幹業務アプリのブレードのスクリーンショット](../media/mam-azure-portal-lob-context-menu.png)
3. **[アプリケーションの削除]** を選択しアプリを削除します。

   ![[アプリケーションの削除] オプションがある基幹業務ブレードのスクリーンショット](../media/mam-azure-portal-delete-app.png)

   これによって、基幹業務アプリの一覧と MAM ポリシーの対象アプリ一覧からアプリは削除されます。
