---
title: "デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する | Microsoft Docs"
titlesuffix: Azure portal
description: "デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを使用する方法について説明します。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 750ce7dbb0dccf08757e076826e2d3650b6e6ab5
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>デバイス登録なしで管理対象アプリ用アプリ構成ポリシーを追加する

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

登録されていないデバイスでも、Intune App SDK をサポートする管理対象アプリにアプリ構成ポリシーを使用できます。 

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** + **[Intune]** の順に選択します。
3. **[モバイル アプリ]** ワークロードを選択します。
4. **[管理]** グループの **[アプリ構成ポリシー]** を選択し、**[追加]** をクリックします。
5. 次の詳細を設定します。
    - **名前**  
      Azure Portal に表示されるプロファイルの名前。
    - **説明**  
      Azure Portal に表示されるプロファイルの説明。
    - **デバイス登録の種類**  
      **[アプリの管理]** を選択します。
6. **[関連アプリ]** を選択して、構成するアプリを選択します。 承認して Intune に同期したアプリの一覧からアプリを選択します。
7. アプリでサポートする構成設定ごとに、**[名前]** と **[値]** を入力し、省略記号 (**[...]**) をクリックします。  
    構成を削除するには、省略記号 (**[...]**) をクリックし、**[削除]** を選択します。  
    Intune App SDK 対応のアプリは、キーと値のペアの構成をサポートしています。 サポートされるキーと値の構成の詳細については、各アプリのドキュメントを参照してください。  
    さらに、アプリケーションから生成されるデータが動的に設定されるトークンを使用できます。

## <a name="configuration-values-using-tokens"></a>トークンを使用する構成値

Intune によって特定のトークンが生成され、管理対象アプリケーションに送信されることがあります。 たとえば、アプリ構成で電子メール設定を使用できる場合、トークンを使用して動的電子メールを追加することができます。 アプリに予期されている名前を **[名前]** フィールドに入力し、`\{\{mail\}\}` を **[値]** フィールドに入力します。

Intune は、構成設定で次のトークンの種類をサポートしています。

- \{\{userprincipalname\}\} - (例: **John@contoso.com**)
- \{\{mail\}\} - (例: **John@contoso.com**)
- \{\{partialupn\}\} - (例: **John**)
- \{\{accountid\}\} - (例: **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- \{\{deviceid\}\} - (例: **b9841cd9-9843-405f-be28-b2265c59ef97**)
- \{\{userid\}\} - (例: **3ec2c00f-b125-4519-acf0-302ac3761822**)
- \{\{username\}\} - (例: **John Doe**)
- \{\{PrimarySMTPAddress\}\} - (例: testuser@ad.domain.com) 


> [!Note]  
> \{\{ 文字と \}\} 文字を使用できるのはトークンの種類のみであり、他の目的には使用しないでください。

## <a name="next-steps"></a>次のステップ

通常どおり、アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。