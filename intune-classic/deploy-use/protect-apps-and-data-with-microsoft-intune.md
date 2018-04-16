---
title: "アプリとデータを保護する"
description: "このトピックでは、さまざまな Intune の機能と、会社のアプリとデータを保護するために使用可能な機能について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2a05444c757b8e99ca0b897acfcd6238d960aeb2
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="protect-apps-and-data-with-microsoft-intune"></a>Microsoft Intune でアプリとデータを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune は、複数のテクノロジ層を介して会社のデータを保護します。 ID 層では、条件付きアクセスによりサービスへのアクセスを保護します。管理対象のデバイスが条件を満たした場合にのみアクセスが許可されます。 クライアント アプリケーション層では、モバイル アプリ管理 (MAM) がデータ紛失を防止します。保護されていないアプリや記憶域にデータを移動する行為を禁止し、デバイスをなくしたり、盗難に遭ったりした場合、データを消去します。 これらの 2 つの保護層は合わせて使用し、データをセキュリティで保護し、モバイルの生産性を維持することが推奨されます。

会社のデータを保護するための最初の重要な手順は、条件付きアクセスを導入することです。 そのために、データ アクセスに使用されるデバイスで強力なパスワードや暗号化などのセキュリティ保護を利用し、脱獄されないようにします。 Intune では、条件を設定できます。その条件をデバイスが満たさないと、会社の電子メールやデータにアクセスできません。

[条件付きアクセス](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)は、Intune で設定できる次の 2 つの種類のポリシーによって決定されます。
- [コンプライアンス ポリシー](introduction-to-device-compliance-policies-in-microsoft-intune.md)を利用し、デバイスのコンプライアンス対応状態を判断します。 このポリシーは、次のような設定と条件を評価します。
  - PIN とパスワード: ルールを作成してデバイスのロック解除にパスワードを要求したり、パスワードの要件を複雑にしたり、他のパスワード設定を要求したりできます。
  - 暗号化: 暗号化されているデバイスへのアクセスを制限できます。
  - デバイスが脱獄またはルート化されていない: Intune は、登録済みのデバイスが脱獄されているかどうかを検出できます。 そのようなデバイスからのアクセスをブロックするポリシーを設定できます。
- Exchange Online や SharePoint Online などの特定のサービスに[条件付きアクセス ポリシー](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)を構成します。 各サービスに、これらのポリシーが適用されるユーザーのグループを定義することができます。 たとえば、財務部門のすべてのユーザーに、登録済みの準拠デバイスから会社の電子メールへのアクセスのみを許可することができます。

会社のリソースに対するアクセスをセキュリティで保護することは、会社のデータ保護の最初の手順に過ぎません。 デバイスでデータにアクセスした後も、引き続きデータを保護する機能が必要です。 これでデータを他の場所にコピー、移動、保存したり、共有したりできます。 Intune には次のような一連のルールを作成することでデータ移動を制限する機能があり、この問題を解決します。
- コピーと貼り付けを禁止します。あるいは、仕事以外でのデータ転送を禁止します。
- 個人のクラウドの記憶域にバックアップすることと "名前を付けて保存する" ことを防止することを禁止します。
- PIN/パスコードまたは会社の資格情報を要求し、アプリのアクセスをセキュリティで保護します。
- Web リンクはすべて Intune Managed Browser 内で開きます。

これらの一連のルールは[モバイル アプリ管理 (MAM) ポリシー](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)と呼ばれています。 MAM ポリシーはアプリに適用できます。アプリを実行しているデバイスを自分が管理しているかどうかは関係ありません。  

**Intune に登録されている**デバイスや、**他のサード パーティ MDM (モバイル デバイス管理) により登録され、管理されている**デバイス、社員所有のデバイスなどの **MDM ソリューションに登録されていない**デバイスに MAM ポリシーを適用し、会社のデータを保護できます。

アプリと MAM ポリシーを関連付けるには、アプリに Microsoft Intune App ソフトウェア開発キット (SDK) を組み込む必要があります。あるいは、アプリ ラッピング ツールを使用できます。

Microsoft Office アプリのようなアプリには、Intune アプリ SDK が組み込まれています。 Microsoft Intune アプリケーション パートナー ページの [Microsoft Intune モバイル アプリケーション ギャラリー](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)で、サポートされているアプリの完全な一覧を参照できます。 アプリを選択し、サポートされるシナリオ、プラットフォーム、アプリのマルチ ID 対応を確認してください。

[特注の基幹業務アプリ](/intune/apps-prepare-mobile-application-management)で MAM ポリシーを使用することもできます。

データ移動を制限するだけでなく、デバイスをなくしたり、盗難に遭ったりした場合、あるいは、ユーザーが退職した場合、[会社のデータを選択消去](wipe-managed-company-app-data-with-microsoft-intune.md)し、個人データだけを残すことができます。
