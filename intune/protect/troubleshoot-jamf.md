---
title: Microsoft Intune との Jamf Pro 統合のトラブルシューティング
titleSuffix: Microsoft Intune
description: Microsoft Intune と共に Jamf Pro for Mac デバイスを統合するときの、いくつかの一般的な問題のトラブルシューティングに関する推奨事項。
keywords: ''
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
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44733eb369e520d2d5f0ff548d4f1921abcb8758
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503565"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Microsoft Intune との Jamf Pro の統合に関するトラブルシューティング

この記事は、intune 管理者が macOS 用の Jamf Pro と Intune の統合に関する問題を理解し、トラブルシューティングするのに役立ちます。

> [!TIP]  
> この記事に記載されている情報の多くは、support.microsoft.com で[Jamf を Microsoft Intune と統合する際の問題のトラブルシューティングに関する](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune)記事に記載されていました。

## <a name="prerequisites"></a>必要条件

トラブルシューティングを開始する前に、いくつかの基本的な情報を収集して問題を明確にし、解決策を見つけるための時間を短縮します。 たとえば、Jamf 統合に関連する問題が発生した場合は、前提条件がすべて満たされていることを必ず確認してください。 トラブルシューティングを開始する前に、次の考慮事項を確認してください。

- [Jamf Pro と Intune を統合](conditional-access-integrate-jamf.md#prerequisites)するための前提条件を確認します。
- すべてのユーザーが Microsoft Intune と Microsoft AAD Premium P1 ライセンスを持っている必要があります 
- Jamf Pro コンソールで Microsoft Intune 統合アクセス許可を持つユーザーアカウントが必要です。
- Azure でグローバル管理者のアクセス許可を持つユーザーアカウントが必要です。


Intune と Jamf Pro の統合を調査するときは、次の情報を考慮してください。 
- 正確なエラー メッセージは何ですか?
- エラーメッセージはどこにありますか。
- 問題が発生し始めたのはいつですか?  Intune と Jamf Pro の統合は成功しましたか?
- 影響を受けるユーザーの数を確認できます。 すべてのユーザーに影響があるのか、それともほんの一部であるか。
- 影響を受けるデバイスの数を確認できます。 すべてのデバイスが影響を受けていますか。
 

## <a name="common-problems"></a>一般的な問題 

次の情報は、Intune と Jamf Pro の統合を設定した後で、デバイスの一般的な問題を特定して解決するのに役立ちます。  

| 問題   | 詳細情報                  |
|-----------------|--------------------------|
| **Jamf Pro でデバイスが応答していないとマークされている**  | [デバイスは、Jamf Pro または Azure AD でチェックインできません](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **Mac デバイスアプリを開いたときにキーチェーンのサインインを求めるメッセージを登録できない**  | [ユーザーは、アプリが Azure AD に登録できるようにするために、パスワードの入力を求められ](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)ます。 |
| **デバイスを登録できない**  | 次の原因が該当します。 <br> **-** [***原因 1*** -Azure の Jamf Pro アプリに無効なアクセス許可がある](#cause-1) <br> **-** [***原因 2*** -の*Jamf Native macOS コネクタ*に問題があり Azure AD](#cause-2) <br> **-** [***原因 3*** -ユーザーに有効な Intune または Jamf ライセンスがない](#cause-3) <br> **-** [***原因 4*** -ユーザーが Jamf Self Service を使用してポータルサイトアプリを起動していない](#cause-4) <br> **-** [***原因 5*** -Intune 統合がオフになっている](#cause-5) <br> **-** [***原因 6*** -デバイスが既に Intune に登録されているか、ユーザーがデバイスを複数回登録しようとしました。](#cause-6) <br> **-** [***原因 7*** -JamfAAD は、ユーザーのキーチェーンからの "Microsoft Workplace Join Key" へのアクセスを要求します。](#cause-7) |
|  **Mac デバイスが Intune に準拠しているが Azure で非準拠と表示される** | [デバイス登録に関する問題](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Jamf を使用して登録された Mac デバイスの Intune コンソールに重複するエントリが表示される** | [同じデバイスに対する複数の登録](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **コンプライアンスポリシーがデバイスの評価に失敗する** | [ポリシーを対象とするデバイスグループ](#compliance-policy-fails-to-evaluate-the-device) |
| **Microsoft Graph API のアクセストークンを取得できませんでした** | 次の原因が該当します。 <br> [Azure の Jamf Pro アプリに対する - のアクセス許可](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> [Jamf または Intune の -  期限切れライセンス](#a-license-required-for-jamf-intune-integration-has-expired) <br> **-** [ポートが開いていません](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Jamf Pro でデバイスが応答していないとマークされている  

**原因**: デバイスが Jamf Pro によって*応答*していないとマークされている一般的な原因は次のとおりです。

- デバイスは Jamf Pro でチェックインできません。  
  Jamf Pro は、15分ごとにデバイスをチェックインすることを想定しています。 24時間にわたってチェックインできなかった場合、デバイスは Jamf によって応答不能とマークされます。  

- デバイスは Azure AD でチェックインできません。  
  Azure AD への登録に成功すると、macOS デバイスは Azure トークンを受信します。
  - このトークンは12時間ごとに更新します。   
  - 24時間以上トークンの更新に失敗すると、Jamf Pro はデバイスを応答不能としてマークします。  
  - Azure トークンの有効期限が切れると、ユーザーは Azure にサインインして新しいトークンを取得するように求められます。 Azure アクセスの更新トークンは7日おきに生成されます。

**解決方法**  
Jamf Pro によってデバイスが*応答*していないとマークされた後、デバイスの登録ユーザーは、応答しない状態を修正するためにサインインする必要があります。 このアカウントは、ログインキーチェーンの Intune からの id を持っているため、職場が参加しているユーザーである必要があります。



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>アプリを開いたときに、Mac デバイスがキーチェーンサインインを要求する  

Intune と Jamf Pro の統合を構成し、条件付きアクセスポリシーを展開した後、Jamf Pro で管理されているデバイスのユーザーは、チーム、Outlook、および Azure を必要とするその他のアプリなどの Microsoft Office 365 アプリケーションを開くと、パスワードの入力を求められます。AD 認証。 

たとえば、Microsoft Teams を開くと、次の例のようなテキストのプロンプトが表示されます。

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**原因**: Azure AD の登録を必要とする適用可能なアプリごとに、これらのプロンプトが Jamf Pro によって生成されます。 

**解決方法**   
プロンプトで、ユーザーは Azure AD にサインインするためにデバイスパスワードを入力する必要があります。 次のオプションがあります。
- **拒否**-サインインせずに、アプリを使用しません。
- ワンタイムサインインを**許可**します。 次回アプリを開いたときに、もう一度サインインするように求められます。
- **[常に許可]** -サインイン資格情報がアプリケーションに対してキャッシュされます。 次回アプリを開いたときに、サインインを求めるメッセージが表示されません。  

[*常に許可*する] を選択すると、そのアプリは今後のサインインでのみ承認されます。 その他のアプリも、 *Always Allow*として設定されるまで、認証を求めるプロンプトを表示します。 1つのアプリのキャッシュされた資格情報は、別のアプリでは使用できません。  

### <a name="devices-fail-to-register"></a>デバイスを登録できない  

Mac デバイスの登録に失敗する一般的な原因がいくつかあります。  

#### <a name="cause-1"></a>原因 1  

**Azure の Jamf Pro エンタープライズアプリケーションに間違ったアクセス許可があるか、複数のアクセス許可を持っています**  

  Azure でアプリを作成する場合は、すべての既定の API アクセス許可を削除してから、Intune に*update_device_attributes*の1つのアクセス許可を割り当てる必要があります。 

  **解決方法**  
  Azure AD で作成した Jamf アプリのアクセス許可を確認し、必要に応じて修正します。 Azure AD の「 [Jamf のアプリケーションを作成](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory)するには」の手順を参照してください。 

#### <a name="cause-2"></a>原因 2  

****Jamf Native MacOS コネクタ**アプリが Azure AD テナントに作成されなかったか、またはグローバル管理者権限を持たないアカウントによって署名されたことに同意しました。**  

  **解決方法**  
  「Docs.jamf.com での[Microsoft Intune との統合](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html)」の「 *macOS Intune 統合の構成*」セクションを参照してください。 

#### <a name="cause-3"></a>原因 3

**ユーザーには有効な Intune または Jamf ライセンスがありません**  

  有効なライセンスがないと、次のエラーが発生する可能性があります。これは、Jamf ライセンスの有効期限が切れていることを示します。  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **解決方法**
  - Jamf license: Jamf の新しいライセンスを取得する方法については、Jamf にお問い合わせください。  
  - Intune ライセンス: 現在のライセンスを取得する方法については、ユーザーに有効なライセンスを割り当てるか、Microsoft またはパートナーにお問い合わせください。

#### <a name="cause-4"></a>原因 4  

**ユーザーは、 *Jamf セルフサービス*を使用してポータルサイトアプリを開始しませんでした**

Jamf を通じてデバイスを登録して Intune に登録するには、ユーザーは Jamf Self Service を使用して、Intune ポータルサイトを開く必要があります。 ユーザーがポータルサイトを手動で開くと、デバイスが登録され、Jamf に接続されずに登録されます。  

デバイスで登録と登録に使用されているサービスを特定するには、デバイスのポータルサイトアプリを確認します。 Jamf を使用して登録すると、セルフサービスアプリを開いて変更を加えるように通知されます。

ポータルサイトアプリで、ユーザーに **`Not registered`** が表示され、次の例のようなエントリがポータルサイトログに表示されることがあります。  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**解決方法**  
登録ソースを Intune から Jamf に変更するには、次のようにします。
1. [Intune から macOS デバイスの登録を解除します](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos)。 Intune から完全に削除されていないデバイスの複雑な問題を回避するには、この一覧の原因[*6*](#cause-6)を参照してください。  

2. デバイスで、Jamf Self Service を使用してポータルサイトアプリを開き、Intune にデバイスを登録します。 このタスクでは、 [Jamf を使用して macOS 用のポータルサイトアプリを展開](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)し、[ユーザーデバイスを Azure AD に登録するポリシーを Jamf Pro で作成](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory)する必要があります。  

3. ポータルが開くと、最初の画面が表示され、サインインするように求められます。 職場または学校アカウントを使用する  

4. ポータル サイトではアカウント情報が確認され、デバイス登録の状況とデバイス コンプライアンスの状況が表示されます。 学校や職場の macOS デバイスをセキュリティで保護するために行う必要があるアクションが黄色の三角形で強調表示されます。 [開始] をクリックして登録を開始します。  

5. 求められたら、コンピューターのサインイン情報を入力します。  
     
デバイスを管理対象に登録するまで数分かかる場合があります。 この間、デバイスで他の作業を行ってもかまいません。 会社アクセス設定が完了した後、完了を知らせるメッセージが表示されます。

#### <a name="cause-5"></a>原因 5  

**Intune の統合がオフになっています**

Intune の統合を無効にすると、ユーザーがデバイスを登録しようとすると、ポータルサイトにポップアップウィンドウが表示され、次のメッセージが表示されます。  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

統合が無効になっていることを Intune に通知する統合を無効にすると、Jamf Pro サーバーから Intune サーバーにパルスが送信されます。 

**解決方法**  
Jamf Pro 内で Intune の統合を再度有効にします。 「[Jamf Pro で Microsoft Intune 統合を構成する](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro)」を参照してください。


#### <a name="cause-6"></a>原因 6  

**デバイスが既に Intune に登録されているか、ユーザーがデバイスを複数回登録しようとしました。**

デバイスが Jamf から登録解除されていても、Intune から正しく削除されていない場合、または複数の登録の試行が行われた場合は、同じデバイスの複数のインスタンスがポータルに表示されることがあります。 これにより、Jamf の登録が失敗します。

**解決方法**  
1. Mac で、**ターミナル**を起動します。
2. **SUDO JAMF removemdmprofile**を実行します。
3. **SUDO JAMF removeFramework**を実行します。
4. JAMF Pro サーバーで、コンピューターのインベントリレコードを削除します。
5. AzureAD からデバイスを削除します。
6. デバイス上の次のファイルが存在する場合は、削除します。
   - /Library/application support Support/com. usercontext. info
   - /Library/application support Support/com. microsoft ポータル
   - /Library/application support のサポート/com. jamfsoftware
   - /ライブラリ/保存済みアプリケーション
   - State/jamfsoftware. savedState. mac.
   - /Library/Saved アプリケーションの状態/com. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - //Library/Cookies/com.microsoft.CompanyPortal.binarycookies/<username>
   - //Library/Cookies/com.jamf.management.jamfAAD.binarycookies/<username>
   - com. microsoft ポータル
   - HockeySDK (com)
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft セッションのトランスポートキー (公開キーと秘密キー)
   - Microsoft Workplace Join キー (公開キーと秘密キー)
7. DeviceLogin.microsoft.com 証明書を含む、 *Microsoft*、 *Intune*、または*ポータルサイト*を参照する、デバイス上のキーチェーンからすべてを削除します。 JAMF public と private key を除き、 *JAMF*参照を削除します。 
   > [!IMPORTANT]  
   > 公開キーと秘密キーを削除すると、デバイスの登録が中断されます。

8. 見つかった次のいずれかのエントリを削除します。  
   - 種類: アプリケーションパスワード。アカウント: com. microsoft. ワークスペース
   - 種類: アプリケーションパスワード。アカウント: com. microsoft. ワークステーション (registeredUserPrincipalName)
   - 種類: Certificate;発行元: MS 組織-アクセス
   - 種類: Identity preference;Name (存在する場合は ADFS STS URL): https://adfs\<DNSName>.com/adfs/ls
   - 種類: Identity preference;名前: https://enterpriseregistration.windows.net
   - 種類: Identity preference;名前: https://enterpriseregistration.windows.net/  
9. Mac デバイスを再起動します。
10. デバイスからポータルサイトをアンインストールします。
11. Portal.manage.microsoft.com にアクセスし、Mac デバイスのすべてのインスタンスを削除します。 次の手順に進む前に、少なくとも30分待ってください。
12. JAMF Pro でデバイスを再登録します。
13. セルフサービスを再度開き、登録ポリシーを開始します。


#### <a name="cause-7"></a>原因 7  

**JamfAAD は、ユーザーのキーチェーンから "Microsoft Workplace Join Key" へのアクセスを要求します。**

登録時に、macOS デバイスのユーザーは、キーチェーンからキーへの JamfAAD アクセスを許可する次のプロンプトを受け取ります。 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**解決方法**  
デバイスを Azure AD に正常に登録するには、Jamf でユーザーがアカウントのパスワードを入力する必要があり、 **[許可]** を選択します。

この要求は、この記事の前半の「[アプリを開いたときのキーチェーンサインインの](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app)要求」に似ています。  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac デバイスが Intune に準拠しているが Azure で非準拠と表示される  

**原因**: 次の状況では、デバイスが Intune に準拠しているものの、Azure に準拠していないと表示されることがあります。  
- デバイスが正しく登録されていません。  
- デバイスは、必要なクリーンアップを行わずに複数回登録されました。

**解決方法**  
この問題を解決するには、この記事の前半の「*デバイスの登録に失敗*する[*原因*](#cause-6)」の解決方法に従います。 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Jamf を使用して登録された Mac デバイスの Intune コンソールに重複するエントリが表示される  
 
**原因**: デバイスが intune に複数回登録されています。通常、intune から削除された後に再登録されます。  

デバイスが Intune と Jamf Pro の統合から削除されると、一部のデータが残っている可能性があります。これにより、連続した登録によってエントリが重複して作成される可能性があります。  

**解決方法**  
この問題を解決するには、この記事の前半の「*デバイスの登録に失敗*する[*原因*](#cause-6)」の解決方法に従います。 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>コンプライアンスポリシーがデバイスの評価に失敗する  

**原因**: Jamf と Intune の統合では、デバイス グループを対象とするコンプライアンス ポリシーがサポートされません。 

**解決方法**  
ユーザーグループに割り当てられる macOS デバイスのコンプライアンスポリシーを変更します。 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Microsoft Graph API のアクセストークンを取得できませんでした

次のエラーが表示されます。

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

このエラーの原因として、次のいずれかの原因が考えられます。 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Azure の Jamf Pro アプリケーションでアクセス許可の問題が発生しています

Azure に Jamf Pro アプリを登録するときに、次のいずれかの条件が発生しました。  
- アプリが複数のアクセス許可を受け取りました。
- [  ***\<your company >* ] オプションに対する管理者の同意**が選択されていません。  

**解決方法**  
この記事の前半の「[デバイスの登録に失敗する](#devices-fail-to-register)原因1の解決策」を参照してください。

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Jamf へのライセンスが必要です-Intune の統合が期限切れになりました

**解決方法**:[デバイスの登録に失敗](#devices-fail-to-register)した場合の原因3の解決策を参照してください。 

#### <a name="the-required-ports-arent-open-on-your-network"></a>必要なポートがネットワーク上で開かれていません

**解決方法**: Jamf Pro と Intune を統合するための[前提条件](conditional-access-integrate-jamf.md#prerequisites)に関するネットワークポートの情報を確認します。


## <a name="next-steps"></a>次の手順
[Jamf Pro と Intune の統合](conditional-access-integrate-jamf.md)に関する詳細情報