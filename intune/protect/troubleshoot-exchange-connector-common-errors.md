---
title: Intune Exchange connector の一般的なエラーのトラブルシューティング
titleSuffix: Microsoft Intune
description: 内部設置型の Microsoft Intune Exchange Connector の一般的なエラーのトラブルシューティングと解決
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b30a7e843850d6918abc2e76f84397a1f197516f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508864"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Intune Exchange Connector の一般的なエラーを解決する

この記事では、intune 管理者が Intune Exchange Connector の操作に関する特定のエラーとメッセージを解決するのに役立つ情報を提供します。  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>構成に失敗し、エラーコード0x0000001 が返されました

**問題**:  
Microsoft Intune Exchange Connector を構成しようとすると、次のエラーメッセージが表示されます。

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

この問題は、インターネットプロキシ設定が正しく構成されていない場合に発生する可能性があります。

**解決方法**:  
プロキシ設定の構成:
1. ローカルネットワーク管理者に問い合わせて、プロキシ設定が正しく構成されていることを確認してください。 
2. **Netsh winhttp**コマンドを使用してプロキシサーバーを構成し、必要な除外リストを追加します。 次に例を示します。  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>構成に失敗し、エラーコード0x000000b が返されました   

**問題**:  
Microsoft Intune Exchange Connector を構成しようとすると、次のエラーメッセージが表示されます。  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Intune へのサインインに使用したアカウントが、Intune のグローバル管理者アカウントではない場合に、この問題が発生する可能性があります。

**解決方法**:  
グローバル管理者であるアカウントを使用して Intune にサインインするか、グローバル管理者グループにアカウントを追加します。 詳細については、「[Microsoft Intune でのロール ベースの管理制御 (RBAC)](../fundamentals/role-based-access-control.md)」を参照してください。

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>構成に失敗し、エラーコード0x0000006 が返されました

**問題**:  
Microsoft Intune Exchange Connector を構成しようとすると、次のエラーメッセージが表示されます。  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
このエラーは、プロキシサーバーを使用してインターネットに接続し、Intune サービスへのトラフィックをブロックしている場合に発生する可能性があります。 プロキシが使用されているかどうかを確認するには、**コントロールパネル**の **[インターネットオプション]**  > 、 **[接続]** タブを選択し、 **[LAN の設定]** をクリックします。

**解決方法**:  

- **オプション 1** -プロキシ設定を削除して、プロキシを経由せずにコンピューターがインターネットに接続できるようにします。  

- **オプション 2** -「 [intune Exchange Connector の要件](exchange-connector-install.md#intune-exchange-connector-requirements)」に記載されているように、intune サービスとの通信を許可するようにプロキシサーバーを構成します。



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>イベント7000または 7041: Microsoft Intune Exchange Connector サービスが開始されない

**問題**:  
IOS デバイスを Intune に登録できず、次のエラーメッセージのいずれかが生成されます。  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
この問題は、 **WIEC_User**アカウントがローカルポリシーに "**サービスとしてログオン**" ユーザー権利を持っていない場合に発生する可能性があります。

**解決方法**:  
Intune Exchange Connector を実行するコンピューターで、 **[サービスとしてログオン**] ユーザー権利を**WIEC_User**サービスアカウントに割り当てます。 コンピューターがクラスター内のノードである場合は、クラスター内のすべてのノードのクラスターサービスアカウントに、"*サービスとしてログオン*" ユーザー権利を割り当ててください。  

コンピューターの**WIEC_User**サービスアカウントに**サービスとしてログオン**するユーザー権利を割り当てるには、次の手順を実行します。

1. 管理者または Administrators グループのメンバーとしてコンピューターにログオンします。
2. **Secpol.msc**を実行して、ローカルセキュリティポリシーを開きます。
3. **[セキュリティの設定]** **[ローカルポリシー]**  >  **[ユーザー権利の割り当て]** の順に選択します。
4. 右のウィンドウで、 **[サービスとしてログオン]** をダブルクリックします。
5. **[ユーザーまたはグループの追加]** を選択し、ポリシーに**WIEC_USER**を追加して、[ **OK]** を2回選択します。

**サービスとしてのログオン**のユーザー権利が**WIEC_User**に割り当てられていて、後で削除された場合は、ドメイン管理者に問い合わせて、グループポリシー設定で上書きされているかどうかを確認します。  

## <a name="next-steps"></a>次の手順  

次の記事は、特定のエラーの解決に役立ちます。
- [Intune Exchange Connector の一般的な問題を解決](troubleshoot-exchange-connector-common-problems.md)します。 git 

サポートや Intune コミュニティからサポートを受けることができます。
- 「Intune コンソールを使用して問題のトラブルシューティングを行う」また[は「Microsoft](../fundamentals/get-support.md)でサポートケースを開く」を参照してください。 
- [Microsoft Intune フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)に問題を投稿してください。  
