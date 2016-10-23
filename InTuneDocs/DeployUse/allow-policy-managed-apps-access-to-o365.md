---
title: "アプリ ベースの O365 に対する条件付きアクセス | Microsoft Intune"
description: "MAM CA を利用して、O365 サービスに対してアクセス権を持つアプリを制御する方法の概念について説明します。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 64eaba6918c4a5c7ccc39fb8ccfeae729a34ff4c
ms.openlocfilehash: a03faa57f9bf1ec6784f0b1ec2d41d3f4cd88a12


---

# Intune MAM ポリシーをサポートするモバイル アプリケーションのみが Office 365 サービスにアクセスできるポリシーを作成する
[Intune モバイル アプリ管理 (MAM) ポリシー](protect-apps-and-data-with-microsoft-intune.md)を使用すると、Intune の管理対象に登録されているデバイス上の会社のデータを保護できます。 **Intune の監視対象に登録されていない従業員が所有するデバイス**に対して、MAM ポリシーを使用することもできます。  この場合、デバイスを管理しなくても、会社のデータとリソースが保護されていることを確認する必要があります。 MAM の条件付きアクセス (MAM CA) を使用すると、Exchange Online などの Office 365 サービスへのアクセスを、Intune MAM ポリシーをサポートするモバイル アプリのみに許可するポリシーを作成できます。

たとえば、Exchange Online へのアクセスを **Microsoft Outlook アプリ**のみに許可すると、**Exchange Online** からから電子メールを取得するように Intune MAM ポリシーのデータ保護を受けていない **iOS と Android の組み込み電子メール アプリをブロックできます**。

## 必要条件
MAM CA ポリシーを構成する**前に**、**Enterprise Mobility + Security または Azure Active Directory Premium サブスクリプション**を用意する必要があります。また、ユーザーに EMS または Azure AD のライセンスが付与される必要があります。 詳細については、「[Enterprise Mobility pricing page](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing)」 (Enterprise Mobility の価格) ページまたは「[Azure Active Directory の価格](https://azure.microsoft.com/en-us/pricing/details/active-directory/)」ページを参照してください。


## サポートされているアプリ
**Exchange Online**
* Android および iOS 用 Microsoft Outlook

## 他の条件付きアクセスと認証方法との重複
### MAM CA と Azure Active Directory 証明書ベースの認証

MAM CA は、Azure Active Directory (Azure AD) 証明書ベースの認証と併用することはできません。 同時に使用できるのは、いずれかの構成のみです。
### MAM CA とデバイスのコンプライアンスに基づく条件付きアクセス  

[Intune 管理コンソール](https://manage.microsoft.com)または [Azure AD Premium 管理コンソール] (https://manage.windowsazure.com) で[デバイスのコンプライアンスに基づいて条件付きアクセス](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (**デバイス CA**) を構成できます。 デバイス CA を使用する場合、ユーザーが Exchange Online に接続するには、Intune デバイス コンプライアンス ポリシーに準拠している Intune の管理対象デバイス、またはドメインに参加しているコンピューターを使用する必要があります。  ユーザーが、MAM CA とデバイス CA ポリシー両方の対象である 1 つまたは複数のセキュリティ グループに属している場合、ユーザーは次の 2 つの要件のうち 1 つを満たす必要があります。
* サービスへのアクセスに使用されるアプリは、MAM CA でサポートされているモバイル アプリであり、アプリを実行するデバイスには、**iOS Authenticator (iOS デバイスの場合)** または**ポータル サイト アプリ (Android デバイスの場合)** がインストールされている。
* サービスへのアクセスに使用されるデバイスは、**Intune の管理対象で Intune のデバイス コンプライアンス ポリシーに準拠している**か、**ドメインに参加しているコンピューター**である。  わかりやすい例を示します。
  * ユーザーが**ネイティブ iOS 電子メール アプリ**から接続する場合、ネイティブ電子メール アプリは MAM CA でサポートされていないため、**管理対象で準拠しているデバイス**を使用して接続する必要があります。
  * ユーザーが **Windows Home コンピューター**から接続する場合、**デバイス CA ポリシー**が適用されるので、ドメインに参加しているコンピューターを使用する必要があります。


## アプリと MAM CA を使用する場合の結果
MAM CA は、デバイス上に必ずあるブローカー アプリを利用して、承認されたアプリケーションの ID を確認します。
*  **iOS** の場合、**Azure Authenticator アプリ**がブローカー アプリです。
* **Android** の場合、**Intune ポータル サイト アプリ**がブローカー アプリです。 

OneDrive や Outlook など、MAM CA でサポートされているアプリにエンドユーザーが初めてサインインする場合、ブローカー アプリをインストールし、デバイスを Azure AD に登録するように求められます。 Azure AD にデバイスを登録すると (以前は社内参加と呼ばれていました)、トークンの発行先に対してデバイス レコードと証明書が作成されます。  これは **MDM の登録**と**同じではありません**。 適用される管理プロファイルまたはポリシーはありません。また、デバイスのアプリから取得されるインベントリはありません。  ブローカー アプリのインストールとデバイスの登録プロセスは、管理対象アプリを初めて使用する場合にのみ実行されます。


## 次のステップ
[MAM アプリ用の Exchange Online ポリシーを作成する](mam-ca-for-exchange-online.md)

[最新の認証を使用していないアプリをブロックする](block-apps-with-no-modern-authentication.md)

### 関連項目

[MAM ポリシーでアプリ データを保護する](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


