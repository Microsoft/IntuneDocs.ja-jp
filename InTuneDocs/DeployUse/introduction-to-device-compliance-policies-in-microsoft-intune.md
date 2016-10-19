---
title: "デバイス コンプライアンス ポリシー | Microsoft Intune"
description: "このトピックでは、デバイス コンプライアンス ポリシーの内容とその仕組みに関して、理解しておくべき概念について説明します。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 550fbbf94f46eee23e77ebf7f9177148882f28e2
ms.openlocfilehash: a853eb4de5528b3ca219ca844a9df4f3b5ad9224


---

# Microsoft Intune のデバイス コンプライアンス ポリシー
## コンプライアンス ポリシーとは
会社のデータを保護するため、会社のアプリやデータにアクセスするために使用するデバイスが、デバイスにアクセスする場合の PIN の使用や、デバイスに格納されるデータの暗号化などの特定のルールに準拠していることを確認する必要があります。 このような一連のルールは、コンプライアンス ポリシーと呼ばれます。

## コンプライアンス ポリシーの使用方法
コンプライアンス ポリシーは、コンプライアンス ポリシー ルールに準拠しているデバイスにのみ電子メールや他のサービスへのアクセスを許可する条件付きアクセス ポリシーと一緒に使用できます。 2 つのポリシーを組み合わせて使用する方法については、「[restrict access to email and O365 services (電子メールと O365 サービスへのアクセスの制限)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)」の記事を参照してください。

また、条件付きアクセスと独立してコンプライアンス ポリシーを使用することもできます。 単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数、脱獄またはルート化されたデバイスに関するレポートを必要とすることがあります。 ただし、単独で使用した場合、会社のリソースへのアクセス制限が設定されません。

コンプライアンス ポリシーをユーザーに展開します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。
ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでの時間の詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)」を参照してください。

次の表は、コンプライアンス ポリシーによってサポートされているデバイスの種類と、ポリシーが条件付きアクセス ポリシーと共に使用される場合に非準拠設定がどのように管理されるかを示した一覧です。

-----------------------------

|ポリシー設定| Windows 8.1 以降| Windows Phone 8.1 以降| iOS 8.0 以降|Android 4.0 以降<br/>Samsung KNOX Standard 4.0 以降|
|-----|----|----|----|----|
|**PIN またはパスワードの構成** |修復|修復|修復|検疫済み|
|**デバイスの暗号化**|該当なし|修復|修復 (PIN の設定による)|検疫済み|
|**脱獄または root 化されたデバイス**|該当なし|該当なし|検疫済み (設定ではありません)|検疫済み (設定ではありません)|
|**電子メールのプロファイル**|該当なし|該当なし|検疫済み|該当なし|
|**最小 OS バージョン**|検疫済み|検疫済み|検疫済み|検疫済み|
|**最大 OS バージョン**|検疫済み| 検疫済み| 検疫済み| 検疫済み|
|**Windows 正常性構成証明書**|Windows 10 および Windows 10 Mobile は検疫されます。<br /><br />Windows 8.1 には設定を適用できません。|N/A|該当なし|該当なし|

------------------------------

**修復** = デバイスのオペレーティング システムによってコンプライアンスが適用されます (たとえば、ユーザーが PIN の設定を求められます)。  設定が非準拠となる場合はありません。

**検疫済み** = デバイスのオペレーティング システムはコンプライアンスを適用しません (たとえば、Android デバイスはユーザーにデバイスの暗号化を求めません)。 デバイスが準拠していない場合、次のアクションが行われます。

-   ユーザーが条件付きアクセス ポリシーの対象となる場合は、デバイスがブロックされます。

-   ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## 次のステップ
[デバイス コンプライアンス ポリシーの作成](create-a-device-compliance-policy-in-microsoft-intune.md)

[デバイス コンプライアンス ポリシーの展開と監視](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### 関連項目
[Restrict access to email and O365 services (電子メールと O365 サービスへのアクセスの制限)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Sep16_HO4-->


