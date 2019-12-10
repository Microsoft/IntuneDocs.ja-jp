---
title: デバイス登録のない管理対象アプリ用構成ポリシー
titleSuffix: Microsoft Intune
description: デバイス登録のない管理対象アプリ用構成ポリシーについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68032f47be043e8c49b6ad922392d14549293c35
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564290"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

登録されていないデバイスでも、Intune App SDK をサポートする管理対象アプリにアプリ構成ポリシーを使用できます。 

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[アプリ構成ポリシー]**  >  **[追加]**  >  **[マネージド アプリ]** を選択します。
3. 次の詳細を設定します。
    - **名前**  
      Azure Portal に表示されるプロファイルの名前。
    - **説明**  
      Azure Portal に表示されるプロファイルの説明。
4. 構成するアプリを選択するために、 **[パブリック アプリの選択]** または **[カスタム アプリの選択]** のいずれかを選択します。 承認して Intune に同期したアプリの一覧からアプリを選択します。
5. アプリでサポートする構成設定ごとに、 **[名前]** と **[値]** を入力します。  
    構成を削除するには、省略記号 ( **[...]** ) を選択し、 **[削除]** を選択します。  
    
Intune App SDK 対応のアプリでは、キー/値のペアの構成がサポートされます。 サポートされるキーと値の構成の詳細については、各アプリのドキュメントを参照してください。 さらに、アプリケーションから生成されるデータが動的に設定されるトークンを使用できます。 Outlook for iOS アプリ構成ポリシー設定の詳細については、「[Microsoft Intune で Outlook for iOS のアプリ構成を管理する](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx)」を参照してください。

## <a name="configuration-values-for-using-tokens"></a>トークンを使用する場合の構成値

Intune では特定のトークンを生成して、マネージド アプリケーションに送信することができます。 たとえば、アプリ構成で電子メール設定を使用できる場合、トークンを使用して動的電子メールを追加することができます。 アプリに予期されている名前を **[名前]** フィールドに入力し、`\{\{mail\}\}` を **[値]** フィールドに入力します。

Intune は、構成設定で次のトークンの種類をサポートしています。 その他のカスタム キーと値の組み合わせはサポートされていません。

- \{\{userprincipalname\}\} — たとえば、John@contoso.com
- \{\{mail\}\} — たとえば、John@contoso.com
- \{\{partialupn\}\} — たとえば、John
- \{\{accountid\}\} — たとえば、fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} — たとえば、3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} — たとえば、John Doe
- \{\{PrimarySMTPAddress\}\} — たとえば、testuser@ad.domain.com


> [!Note]  
> \{\{ 文字と \}\} 文字を使用できるのはトークンの種類のみであり、他の目的には使用しないでください。

## <a name="next-steps"></a>次の手順

通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。
