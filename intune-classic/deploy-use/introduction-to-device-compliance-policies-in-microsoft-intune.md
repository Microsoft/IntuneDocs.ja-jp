---
title: "デバイス コンプライアンス ポリシー"
description: "このトピックでは、デバイス コンプライアンス ポリシーの内容とそのしくみについて説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bcdad361dba7ee006bf2e2cffac7f1024c5e6dc6
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2017
---
# <a name="device-compliance-policies-in-microsoft-intune"></a>Microsoft Intune のデバイス コンプライアンス ポリシー

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>コンプライアンス ポリシーとは
会社のデータを容易に保護できるようにするには、会社のアプリとデータへのアクセスに使用されるデバイスが特定のルールに準拠していることを確認する必要があります。 これらのルールには、PIN を使用するデバイスへのアクセスと、デバイスに格納されているデータの暗号化に関するものが含まれる場合があります。 このような一連のルールは、コンプライアンス ポリシーと呼ばれます。

## <a name="how-should-i-use-compliance-policies"></a>コンプライアンス ポリシーの使用方法
コンプライアンス ポリシーは、コンプライアンス ポリシー ルールに準拠しているデバイスにのみ電子メールや他のサービスへのアクセスを許可する条件付きアクセス ポリシーと一緒に使用できます。 2 つのポリシーを組み合わせて使用する方法については、「[電子メールと O365 サービスへのアクセスを制限する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)」の記事を参照してください。

また、条件付きアクセスと独立してコンプライアンス ポリシーを使用することもできます。 コンプライアンス ポリシーを単独で使用した場合、対象のデバイスが評価され、コンプライアンス ステータスを含めて報告されます。 たとえば、暗号化されていないデバイスの数、脱獄またはルート化されたデバイスに関するレポートを必要とすることがあります。 ただし、コンプライアンス ポリシーを単独で使用した場合、会社のリソースへのアクセス制限が設定されません。

コンプライアンス ポリシーをユーザーに展開します。 コンプライアンス ポリシーがユーザーに展開されると、ユーザーのデバイスのコンプライアンスがチェックされます。
ポリシーの展開後にモバイル デバイスがポリシーを取得できるようになるまでの時間の詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)」を参照してください。

次の表に、コンプライアンス ポリシーでサポートされるデバイスの種類をリストします。 この表では、条件付きアクセス ポリシーとコンプライアンス ポリシーを使用する場合に非準拠設定をどのように管理するかについても説明しています。

-----------------------------

|ポリシー設定| Windows 8.1 以降| Windows Phone 8.1 以降| iOS 8.0 以降|Android 4.0 以降<br/>Samsung KNOX Standard 4.0 以降|
|-----|----|----|----|----|
|**PIN またはパスワードの構成** |修復|修復|修復|検疫済み|
|**デバイスの暗号化**|該当なし|修復|修復 (PIN の設定による)|検疫済み|
|**脱獄またはルート化されたデバイス**|該当なし|該当なし|検疫済み (設定ではありません)|検疫済み (設定ではありません)|
|**電子メールのプロファイル**|該当なし|該当なし|検疫済み|該当なし|
|**最小 OS バージョン**|検疫済み|検疫済み|検疫済み|検疫済み|
|**最大 OS バージョン**|検疫済み|検疫済み|検疫済み|検疫済み|
|**Windows 正常性構成証明書**|検疫済み: Windows 10 および Windows 10 Mobile<br /><br />該当なし: Windows 8.1|該当なし|該当なし|該当なし|

------------------------------

**修復** = デバイス オペレーティング システムによって準拠が強制されます  (たとえば、ユーザーは PIN を設定するように強制されます)。

**検疫済み** = デバイス オペレーティング システムによって準拠が強制されません  (たとえば、Android デバイスでは、ユーザーはデバイスの暗号化を強制されません)。デバイスが準拠していない場合、次のアクションが行われます。

-   ユーザーに条件付きアクセス ポリシーを適用すると、デバイスがブロックされます。

-   ポータル サイトは、コンプライアンスの問題をユーザーに通知します。

## <a name="next-steps"></a>次のステップ
[デバイス コンプライアンス ポリシーの作成](create-a-device-compliance-policy-in-microsoft-intune.md)

[デバイス コンプライアンス ポリシーの展開と監視](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>関連項目
[電子メールと O365 サービスへのアクセスを制限する](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
