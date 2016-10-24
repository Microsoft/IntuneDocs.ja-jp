---
title: "アプリとデータの保護 | Microsoft Intune"
description: "このトピックでは、さまざまな Intune の機能と、会社のアプリとデータを保護するために使用可能な機能について説明します。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dd7a51b5ba176c8c7b593d2d7a3e5cfabd72a1e6
ms.openlocfilehash: 77ce4cca5f85f1847e599a6151411bfc12afbc8b


---

# Microsoft Intune でアプリとデータを保護する


Intune は、複数のテクノロジ層を介して会社のデータを保護します。  ID 層では、条件付きアクセスによりサービスへのアクセスを保護します。管理対象のデバイスが条件を満たした場合にのみアクセスが許可されます。  クライアント アプリケーション層では、モバイル アプリ管理 (MAM) がデータ紛失を防止します。保護されていないアプリや記憶域にデータを異動する行為を禁止し、デバイスをなくしたり、盗難に遭ったりした場合、データを消去します。  データをセキュリティで保護し、モバイルの生産性を維持するために、これらの 2 つの保護層は合わせて使用してください。

会社のデータを保護するための最初の重要な手順は、条件付きアクセスを導入し、データ アクセスに使用されるデバイスで強力なパスワードや暗号化などのセキュリティ保護を利用し、脱獄されないようにすることです。 Microsoft Intune では、条件を設定できます。その条件をデバイスが満たさないと、会社の電子メールやデータにアクセスできません。

[条件付きアクセス](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)は、Intune で設定できる次の 2 つの種類のポリシーによって決定されます。
- [コンプライアンス ポリシー](introduction-to-device-compliance-policies-in-microsoft-intune.md)は、デバイスのコンプライアンス対応状態を判断します。 このポリシーは、次のような設定と条件を評価します。
  - PIN とパスワード: デバイスのロックを解除する前にパスワードを要求するルール、パスワードの複雑さ、その他のパスワードの設定を作成できます。
  - 暗号化: 暗号化されているデバイスへのアクセスを制限できます。
  - デバイスが脱獄またはルート化されていない: Intune は、登録済みのデバイスが脱獄されているかどうかを検出できます。さらに、そのようなデバイスからのアクセスをブロックするポリシーを設定できます。
- [条件付きアクセス ポリシー](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)は、Exchange Online や SharePoint Online などの特定のサービスで構成します。 各サービスに、これらのポリシーが適用されるユーザーのグループを定義することができます。 たとえば、財務部門のすべてのユーザーに、登録済みの準拠デバイスから会社の電子メールへのアクセスのみを許可することができます。

会社のリソースに対するアクセスをセキュリティで保護することは、会社のデータ保護の最初の手順に過ぎません。 デバイスでデータにアクセスした後も、引き続きデータを保護する機能が必要です。 これでデータを他の場所にコピー、移動、保存したり、共有したりできます。 Intune には次のような一連のルールを作成することでデータ移動を制限する機能があり、この問題を解決します。
- コピーと貼り付けを禁止します。あるいは、作業コンテキスト外のデータ転送を禁止します。
- 個人のクラウド ストレージへのバックアップを禁止します。名前を付けて保存することを禁止します。
- PIN/パスコードまたは会社の資格情報を要求し、アプリのアクセスをセキュリティで保護します。
- Web リンクはすべて Intune Managed Browser 内で開きます。

これらの一連のルールは[モバイル アプリ管理 (MAM) ポリシー](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)と呼ばれています。  MAM ポリシーは、場合によっては自分で管理できないデバイスで実行されているアプリに適用できます。  

**Intune に登録されている**デバイスや、**他のサード パーティー MDM により登録され、管理されている**デバイス、社員所有のデバイスなどの **MDM ソリューションに登録されていない**デバイスに MAM ポリシーを適用し、会社のデータを保護できます。

アプリと MAM ポリシーを関連付けるには、アプリに Microsoft Intune App ソフトウェア開発キット (SDK) を組み込むか、アプリでアプリ ラッピング ツールを使用する必要があります。

Microsoft Office アプリのようなアプリには、アプリ SDK が組み込まれています。 サポートされているアプリの完全リストは、Microsoft Intune アプリケーション パートナー ページの [Microsoft Intune モバイル アプリケーション ギャラリー](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)にあります。 アプリを選択し、サポートされるシナリオ、プラットフォーム、アプリのマルチ ID 対応を確認してください。

[特注の基幹業務アプリ](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)で MAM ポリシーを使用することもできます。

データ移動を制限するだけでなく、デバイスをなくしたり、盗難に遭ったりした場合、あるいは、ユーザーが退職した場合、[会社のデータを選択消去](wipe-managed-company-app-data-with-microsoft-intune.md)し、個人データだけを残すことができます。



<!--HONumber=Oct16_HO3-->


