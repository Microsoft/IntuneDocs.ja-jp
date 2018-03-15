---
title: "デバイス登録のない管理対象アプリ用構成ポリシー"
titlesuffix: Microsoft Intune
description: "デバイス登録のない管理対象アプリ用構成ポリシーについて説明します。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 384804029ecbf403f526144136dc187212e6cf4a
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

登録されていないデバイスでも、Intune App SDK をサポートする管理対象アプリにアプリ構成ポリシーを使用できます。 

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **[すべてのサービス]** > **[Intune]** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[モバイル アプリ]** ワークロードを選択します。
4. **[管理]** グループの **[アプリ構成ポリシー]** を選択し、**[追加]** を選択します。
5. 次の詳細を設定します。
    - **名前**  
      Azure Portal に表示されるプロファイルの名前。
    - **説明**  
      Azure Portal に表示されるプロファイルの説明。
    - **デバイス登録の種類**  
      **[アプリの管理]** を選択します。
6. **[関連アプリ]** を選択して、構成するアプリを選択します。 承認して Intune に同期したアプリの一覧からアプリを選択します。
7. アプリでサポートする構成設定ごとに、**[名前]** と **[値]** を入力し、省略記号 (**[...]**) を選択します。  
    構成を削除するには、省略記号 (**[...]**) を選択し、**[削除]** を選択します。  
    
Intune App SDK 対応のアプリでは、キー/値のペアの構成がサポートされます。 サポートされるキーと値の構成の詳細については、各アプリのドキュメントを参照してください。 さらに、アプリケーションから生成されるデータが動的に設定されるトークンを使用できます。 Outlook for iOS アプリ構成ポリシー設定の詳細については、「[Microsoft Intune で Outlook for iOS のアプリ構成を管理する](https://technet.microsoft.com/en-us/library/mt813789(v=exchg.150).aspx)」を参照してください。

## <a name="configuration-values-for-using-tokens"></a>トークンを使用する場合の構成値

Intune では特定のトークンを生成して、マネージ アプリケーションに送信することができます。 たとえば、アプリ構成で電子メール設定を使用できる場合、トークンを使用して動的電子メールを追加することができます。 アプリに予期されている名前を **[名前]** フィールドに入力し、`\{\{mail\}\}` を **[値]** フィールドに入力します。

Intune は、構成設定で次のトークンの種類をサポートしています。

- \{\{userprincipalname\}\} — たとえば、**John@contoso.com**
- \{\{mail\}\} — たとえば、**John@contoso.com**
- \{\{partialupn\}\} — たとえば、**John**
- \{\{accountid\}\} — たとえば、**fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{userid\}\} — たとえば、**3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} — たとえば、**John Doe**
- \{\{PrimarySMTPAddress\}\} — たとえば、**testuser@ad.domain.com** 


> [!Note]  
> \{\{ 文字と \}\} 文字を使用できるのはトークンの種類のみであり、他の目的には使用しないでください。

## <a name="next-steps"></a>次の手順

通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。
