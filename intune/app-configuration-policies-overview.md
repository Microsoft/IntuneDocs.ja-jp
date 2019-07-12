---
title: Microsoft Intune 用アプリ構成ポリシー
titleSuffix: ''
description: Microsoft Intune の iOS または Android デバイスでアプリ構成ポリシーを使用する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10dad24ee41f63dcc304d95e9b733f7de3f1b71a
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2019
ms.locfileid: "67649023"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Microsoft Intune 用アプリ構成ポリシー

Microsoft Intune のアプリ構成ポリシーを使用して、iOS または Android アプリの構成を設定できます。 これらの構成設定では、アプリの構成と管理に対する業界の標準的なアプローチを使用して、アプリをカスタマイズできます。 構成ポリシー設定は、アプリがポリシーをチェックするとき (通常はアプリの初回実行時) に使用されます。

含める割り当てと除外する割り当ての組み合わせを使って、ユーザーとデバイスのグループにアプリ構成ポリシーを割り当てることができます。 アプリ構成ポリシーを追加すると、アプリ構成ポリシーの割り当てを設定できます。 ポリシーの割り当てを設定するときに、ポリシーを適用するユーザーのグループを含めたり、除外したりできます。 含めるグループを選ぶとき、含める特定のグループを選ぶか、組み込みグループを選ぶことができます。 組み込みグループには、**すべてのユーザー**、**すべてのデバイス**、**すべてのユーザーとすべてのデバイス**が含まれます。

たとえば、アプリ構成設定では、次の詳細のいずれかを指定する必要があります。

- カスタム ポート番号
- 言語の設定
- セキュリティ設定
- 会社のロゴなどのブランドの設定

ユーザーが代わりにこれらの設定を入力した場合、誤って入力する可能性があり、それによってヘルプ デスクの負荷が増加し、新しいアプリの採用が遅くなる可能性もあります。

アプリ構成ポリシーを使用すると、ユーザーがアプリを実行する前に、ユーザーに割り当てられるポリシーに構成設定を割り当てることができるため、アプリ設定の問題を排除するのに役立ちます。 設定が自動的に指定されるため、ユーザーの操作は不要です。

構成設定は、アプリがチェックするたびに使用されます。 通常、アプリはユーザーがアプリを初めて実行するときに構成設定を確認します。

Intune でアプリ構成を使用する方法には 2 つの選択肢があります。
 - **マネージド デバイス**: デバイスは、Intune で MDM (モバイル デバイス管理) プロバイダーとして管理されます。
 - **マネージド アプリ**: アプリはデバイスの登録なしで管理されます。

> [!NOTE]
> Microsoft Intune 管理者は、マネージド デバイス上の Microsoft Office アプリケーションにどのユーザー アカウントを追加するかを制御することができます。 許可されている組織ユーザー アカウントのみにアクセスを制限したり、登録済みデバイス上の個人アカウントをブロックしたりできます。 サポートされているアプリケーションがアプリの構成を処理し、未承認のアカウントを削除してブロックします。

## <a name="apps-that-support-app-configuration"></a>アプリ構成をサポートするアプリ

### <a name="managed-devices"></a>マネージド デバイス
サポートするアプリにアプリ構成ポリシーを使用できます。 Intune でアプリ構成をサポートするには、[Appconfig Community](https://www.appconfig.org/members) による定義に従って、アプリ構成の使用をサポートするようにアプリが記述されている必要があります。 詳細については、アプリのベンダーに問い合わせてください。

### <a name="managed-apps"></a>Managed apps
Intune App SDK をアプリに組み込むか、アプリの開発後にラップして、基幹業務アプリを準備することができます。 iOS と Android の両方で使用可能な Intune App SDK では、Intune アプリ保護構成ポリシーに対してアプリを有効にすることができます。 アプリの開発者が必要なコード変更が最小限に抑えられます。 詳細については、「[Intune App SDK の概要](app-sdk.md)」を参照してください。

## <a name="graph-api-support-for-app-configuration"></a>Graph API のアプリ構成のサポート

アプリ構成タスクは、Graph API でも実行することができます。 詳細については、[Graph API のリファレンスの MAM を対象とした構成](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

### <a name="managed-devices"></a>マネージド デバイス

 - iOS デバイスでアプリ構成を使用する方法について学びます。  「[管理対象の iOS デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-ios.md)」をご覧ください。
 - Android デバイスにアプリ構成を使用する方法について学びます。  「[管理対象の Android デバイス用アプリ構成ポリシーを追加する](app-configuration-policies-use-android.md)」を参照してください。

### <a name="managed-apps"></a>Managed apps

 - 管理対象アプリにアプリ構成を使用する方法について学びます。 「[デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する](app-configuration-policies-managed-app.md)」を参照してください。
