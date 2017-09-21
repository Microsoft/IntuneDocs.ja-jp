---
title: "Azure での Intune の機能の移動先"
titlesuffix: Azure portal
description: "Azure Portal で Intune の機能がどこにあるかを確認できます。"
keywords: 
author: dagerrit
ms.author: dagerrit
manager: angrobe
ms.date: 03/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41b358f48412585ec40e369225b4263012bfd2f8
ms.sourcegitcommit: b8987b8dfb009ea55678d7f640ac5f18a6ab167e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2017
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Azure での Intune の機能の移動先
Intune から Azure Portal に移行する際に、いくつかのタスクがより論理的に整理されました。 しかし、このような改善を行えば、新しい構成を学ばなければなりません。 このリファレンス ガイドは、従来のポータルを使用した Intune の知識があり、Intune で行われていた内容を Azure Portal ではどのように実行されるのかについて関心があるユーザーに向けて作成しました。 この記事でお探しの機能が記載されていない場合は、今後更新できるように記事の最後にコメントを残してください。
## <a name="quick-reference-guide"></a>クイック リファレンス ガイド
|機能 |従来のポータルでのパス|Azure Portal の Intune でのパス|
|------------|---------------|---------------|
|Device Enrollment Program (DEP) [iOS のみ]|[管理] > [モバイル デバイス管理] > [iOS] > [Device Enrollment Program]|[[デバイスの登録] > [Apple の登録] > [Enrollment Program トークン]](#where-did-apple-dep-go) |
|Device Enrollment Program (DEP) [iOS のみ]| [管理] > [モバイル デバイス管理] > [iOS および Mac OS X] > [Device Enrollment Program] |[[デバイスの登録] > [Apple の登録] > [Enrollment Program Serial Numbers]\(Enrollment Program シリアル番号\)](#where-did-apple-dep-go) |
|登録ルール |[管理] > [モバイル デバイス管理] > [登録ルール]|[[デバイスの登録] > [登録制限]](#where-did-enrollment-rules-go) |
|iOS シリアル番号別のグループ |[グループ] > [すべてのデバイス] > [会社の事前登録済みデバイス] > [iOS シリアル番号を使用]|[[デバイスの登録] > [Apple の登録] > [Enrollment Program Serial Numbers]\(Enrollment Program シリアル番号\)](#where-did-corporate-pre-enrolled-devices-go) |
|iOS シリアル番号別のグループ |[グループ] > [すべてのデバイス] > [会社の事前登録済みデバイス] > [iOS シリアル番号を使用]| [[デバイスの登録] > [Apple の登録] > [AC Serial numbers]\(AC シリアル番号\)](#where-did-corporate-pre-enrolled-devices-go)|
|IMEI 別のグループ (すべてのプラットフォーム)| [グループ] > [すべてのデバイス] > [会社の事前登録済みデバイス] > [By IMEI]\(IMEI を使用\) (すべてのプラットフォーム) | [[デバイスの登録] > [業務用デバイスの ID]](#by-imei-all-platforms)|
| 業務用デバイスの登録プロファイル| [ポリシー] > [業務用デバイスの登録] | [[デバイスの登録] > [Apple の登録] > [Enrollment Program プロファイル]](#where-did-corporate-pre-enrolled-devices-go) |
| 業務用デバイスの登録プロファイル | [ポリシー] > [業務用デバイスの登録] | [[デバイスの登録] > [Apple の登録] > [AC プロファイル]](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | [管理] > [モバイル デバイス管理] > [Android for Work] | [デバイスの登録] > [Android for Work への登録] |
| 使用条件 | [ポリシー] > [使用条件] | [デバイスの登録] > [使用条件] |


## <a name="where-do-i-manage-groups"></a>グループを管理する場所
Azure Portal の Intune では、[Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) を使用してグループを管理します。

## <a name="where-did-enrollment-rules-go"></a>登録ルールの移動先
従来のポータルでは、モバイルおよび最新の Windows/macOS デバイスの MDM の登録に適用されるルールを次のようにして設定できました。

![従来のモバイル デバイスの登録ルールの画像](./media/01-classic-rules.png)

これらのルールは例外なくすべてのユーザーの Intune アカウントに適用されました。 Azure Portal では、これらのルールは [デバイスの種類の制限] と [デバイス数の制限] という 2 つのポリシーの種類に表示されます。

![Azure のモバイル デバイス登録制限の画像](./media/02-azure-enroll-restrictions.png)

既定の [デバイスの上限数の制限] は、従来のポータルの [デバイス登録制限] に対応します。

![Azure のデバイス数の制限の画像](./media/03-azure-device-limit.png)

既定の [デバイスの種類の制限] は、従来のポータルの [プラットフォームの制限] に対応します。

![Azure のデバイスの種類の制限の画像](./media/04-azure-platform-restrictions.png)

個人所有のデバイスを許可またはブロックする機能を、[デバイスの種類の制限] の [プラットフォーム構成] で管理できるようになりました。

![Azure の個人用デバイスのブロック設定の画像](./media/05-azure-personal-block.png)

新しい制限の機能は、Azure Portal のみに追加されます。

## <a name="where-did-apple-dep-go"></a>Apple DEP の移動先
従来のポータルでは、Intune が Apple のデバイス登録プログラムと統合されるように設定し、Apple サービスとの同期を手動で要求できました。

![従来の DEP トークンの画像](./media/06-classic-dep-token.png)

Azure Portal でも、Intune クラシックと同じ手順で Apple のデバイス登録プログラムを設定します。

![Azure の DEP トークンの画像](./media/07-azure-dep-token.png)

ただし、従来のポータルの **[同期]** オプションが、シリアル番号管理のワークフローに移動しています。手動による同期の結果がここに表示されるためです。

![Azure の DEP 同期の画像](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>会社の事前登録済みデバイスの移動先
### <a name="by-ios-serial-number"></a>iOS シリアル番号を使用
従来のポータルでは、Apple デバイス登録プログラム (DEP) と Apple Configurator ツールを使用して iOS デバイスを登録できます。 どちらの方法でも、シリアル番号を使用したデバイスの事前登録が可能で、この登録によって特別な業務用デバイスの登録プロファイルが割り当てられます。 登録の前に、**[会社の事前登録済みデバイス] の [iOS シリアル番号を使用]** のデバイス グループから登録プロファイルの割り当てを管理できます。

![従来の Apple シリアル番号の画像](./media/09-classic-apple-serials.png)

これには、Apple DEP と Configurator で登録されたシリアル番号が 1 つの一覧に表示されています。 プロファイルの割り当て (DEP プロファイルから AC シリアル番号、およびその逆) の不一致を減らすため、Azure Portal ではシリアル番号を 2 つの一覧に分割しました。

**DEP のシリアル番号**
![Azure DEP のシリアル番号の画像](./media/10-azure-dep-serials.png)

**Apple Configurator のシリアル番号**
![Azure Apple Configurator のシリアル番号の画像](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>IMEI (すべてのプラットフォーム) を使用

従来のポータルでは、デバイスの IMEI 番号を事前に一覧表示することで、デバイスを Intune に登録する際に業務用としてマークすることができました。

![IMEI 番号の従来の一覧の画像](./media/12-classic-corp-imei.png)

Azure Portal では、コンマ区切り値 (CSV) ファイルを使用して同じ IMEI を [業務用デバイスの ID] 一覧にアップロードする必要があります。 新しいポータルでは、IMEI 番号の手動での入力はサポートされません。

![IMEI 番号の Azure の一覧の画像](./media/13-azure-corp-imei.png)

Azure Portal の Intune では IMEI 以外の種類の ID も今後サポートされることになっていますが、現在は事前表示用の IMEI 番号のみが許可されています。

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>業務用デバイスの登録プロファイルの移動先
Apple のデバイス登録プログラムまたは Apple Configurator ツールを使用して iOS デバイスを登録するには、デバイスに割り当てられる業務用デバイスの登録プロファイルを指定する必要があります。 従来のポータルでは、これらのプロファイルの作成と管理は同じ一覧にありました。

![従来のデバイスの登録プロファイルの画像](./media/14-classic-corp-profiles.png)

この一覧には Apple のデバイス登録プログラムでの使用が有効なプロファイル (**DEP が [On (オン)]**) と、Apple Configurator ツールでの使用のみが有効なプロファイル (**DEP が [Off (オフ)]**) が表示されています。

2 つのプロファイルを混同し、割り当て (DEP プロファイルから Configurator デバイス、およびその逆) が一致しない可能性を少なくするため、(Apple のデバイス登録プログラムと Apple スクール マネージャーの両方をサポートする) 登録プログラムのプロファイルと、Apple Configurator プロファイルの作成と管理を分けました。

**DEP プロファイル**
![Azure の DEP プロファイルの画像](./media/15-azure-dep-profiles.png)

**Apple Configurator のプロファイル**
![Azure の Apple Configurator プロファイルの画像](./media/16-azure-ac-profiles.png)
