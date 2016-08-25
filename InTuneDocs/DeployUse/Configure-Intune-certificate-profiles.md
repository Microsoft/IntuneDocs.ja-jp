---
title: "証明書プロファイルを構成する | Microsoft Intune"
description: "Intune 証明書プロファイルを作成する方法について説明します。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6a7f2eeb0114f525890d1dcb61344d60a19943d1
ms.openlocfilehash: 14419092edc77b2229cf980a74e81048941a2c28


---

# Intune 証明書プロファイルを構成する
「[SCEP の証明書インフラストラクチャを構成する](configure-certificate-infrastructure-for-scep.md)」または「[PFX の証明書インフラストラクチャを構成する](configure-certificate-infrastructure-for-pfx.md)」の説明に従って証明書を構成した後、証明書プロファイルを構成できます。

**タスク 1** - 信頼されたルート CA 証明書をエクスポートする **タスク 2** - 信頼された CA 証明書プロファイルを作成する **タスク 3** - 次のどちらかを実行する

SCEP 証明書プロファイルを作成する

.PFX 証明書プロファイルを作成する

### タスク 1 - 信頼されたルート証明書をエクスポートする
発行元 CA または発行元 CA を信頼するデバイスから、信頼されたルート CA 証明書を **.cer** ファイルとしてエクスポートします。 秘密キーはエクスポートしません。

信頼された証明書プロファイルを構成するときにこの証明書をインポートします。

### タスク 2 - 信頼された証明書プロファイルを作成する
SCEP または .PFX 証明書プロファイルを作成する前に、**信頼された証明書プロファイル**を作成する必要があります。 モバイル デバイス プラットフォームごとに、信頼された証明書プロファイルと、SCEP または .PFS プロファイルが必要です。

##### 信頼された証明書プロファイルを作成するには

1.  [Intune 管理コンソール](https://manage.microsoft.com)を開き、**[ポリシー]** &gt; **[ポリシーの追加]** の順にクリックします。

2.  次のポリシーの種類のいずれかを構成します。

    **Android &gt; 信頼された証明書プロファイル (Android 4 以降)**

    **iOS &gt; 信頼された証明書プロファイル (iOS 7.1 以降)**

    **Mac OS X &gt; 信頼された証明書プロファイル (Mac OS X 10.9 以降)**

    **Windows &gt; 信頼された証明書プロファイル (Windows 8.1 以降)**

    **Windows &gt; 信頼された証明書プロファイル (Windows Phone 8.1 以降)**

    詳しくは、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

3.  要求された情報を指定して、Android、iOS、Mac OS X、Windows 8.1、または Windows Phone 8.1 用の信頼された証明書プロファイルの設定を構成します。 

    - **[証明書ファイル]** 設定で、発行元 CA からエクスポートした信頼されたルート CA 証明書 (**.cer**) をインポートします。 **[保存先ストア]** 設定は、Windows 8.1 以降を実行中のデバイスで、1 つ以上の証明書ストアを持っているデバイスにのみ適用されます。

    
    - **[サブジェクト名の形式]** で、**[カスタム]** を選択してサブジェクト名のカスタム形式を指定します。  

        カスタム形式で現在サポートされている 2 つの変数は、**共通名 (CN)** と**電子メール (E)** です。 これらの変数と静的文字列の組み合わせを使用することで、この例で示すようなサブジェクト名のカスタム形式を作成できます。  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        例では、管理者は CN と E の変数に加えて、組織単位、組織、市区町村、州、および国の文字列を使用してサブジェクト名形式を作成しています。 サポートされる文字列の一覧は、トピック [CertStrToName 関数](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx)で提供されています。  


4.  終了したら、 **[ポリシーの保存]**をクリックします。

新しいポリシーが [ **ポリシー** ] ワークスペースに表示され、展開できるようになります。

### タスク 3 – SCEP または .PFX 証明書プロファイルを作成する
信頼された CA 証明書プロファイルを作成した後、使用する各プラットフォーム用の SCEP または .PFX 証明書プロファイルを作成します。 SCEP 証明書プロファイルを作成するときは、その同じプラットフォームに対する信頼された証明書プロファイルを指定する必要があります。 これにより 2 つの証明書プロファイルがリンクされますが、それでも各プロファイルを個別に展開する必要があります。

##### SCEP 証明書プロファイルを作成するには

1.  [Intune 管理コンソール](https://manage.microsoft.com)を開き、**[ポリシー]** &gt; **[ポリシーの追加]** の順にクリックします。

2.  次のポリシーの種類のいずれかを構成します。

    **Android &gt; SCEP 証明書プロファイル (Android 4 以降)**

    **iOS &gt; SCEP 証明書プロファイル (iOS 7.1 以降)**

    **Mac OS X &gt; SCEP 証明書プロファイル (Mac OS X 10.9 以降)**

    **Windows &gt; SCEP 証明書プロファイル (Windows 8.1 以降)**

    **Windows &gt; SCEP 証明書プロファイル (Windows Phone 8.1 以降)**

    詳しくは、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

3.  プロファイル構成ページの指示に従って、SCEP 証明書プロファイル設定を構成します。
    > [!NOTE]
    > 
    > **[サブジェクト名の形式]** で、**[カスタム]** を選択してサブジェクト名のカスタム形式を指定します。
    > 
    >  カスタム形式で現在サポートされている 2 つの変数は、共通名 (CN) と電子メール (E) です。 これらの変数と静的文字列の組み合わせを使用することで、この例で示すようなサブジェクト名のカスタム形式を作成できます。
    
    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US
    
    >    例では、管理者は *CN* と *E* の変数に加えて、組織単位、組織、市区町村、州、および国の文字列を使用してサブジェクト名形式を作成しています。 サポートされる文字列の一覧は、トピック [CertStrToName 関数](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx)で提供されています。

4.  終了したら、 **[ポリシーの保存]**をクリックします。

新しいポリシーが [ **ポリシー** ] ワークスペースに表示され、展開できるようになります。

##### .PFX 証明書プロファイルを作成するには

1.  [Intune 管理コンソール](https://manage.microsoft.com)を開き、**[ポリシー]** &gt; **[ポリシーの追加]** の順にクリックします。

2.  次のポリシーの種類のいずれかを構成します。



-   **Android &gt; .PFX 証明書プロファイル (Android 4 以降)**

    -   **Windows &gt; PKCS #12 (.PFX) 証明書プロファイル (Windows 10 以降)**

    -   **Windows &gt; PKCS #12 (.PFX) 証明書プロファイル (Windows Phone 10 以降)**

    -    **iOS > PKCS #12 (.PFX) 証明書プロファイル (iOS 7.1 以降)**    

    詳しくは、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

3.  ポリシー フォームで要求されている情報を入力します。

4.  終了したら、 **[ポリシーの保存]**をクリックします。

新しいポリシーが [ **ポリシー** ] ワークスペースに表示され、展開できるようになります。

## 証明書プロファイルを展開する
証明書プロファイルを展開すると、信頼された CA 証明書プロファイルの証明書ファイルがデバイスにインストールされ、デバイスは SCEP または .PFX 証明書プロファイルを使用して証明書要求を作成します。

証明書プロファイルは、プロファイルを作成するときに使用するプラットフォームを基にして、該当するデバイスのみにインストールされます。

-   ユーザー コレクションまたはデバイス コレクションに証明書プロファイルを展開できます。

    > [!TIP]
    > デバイス登録後すぐに証明書がデバイスに公開されるようにするには、証明書プロファイルを (デバイス グループではなく) ユーザー グループに展開します。 デバイス グループに展開した場合は、デバイスの登録が完全に行われるまで、デバイスはポリシーを受け取りません。

-   各プロファイルは個別に展開されますが、信頼されたルート プロファイルと SCEP/.PFX プロファイルの両方を展開する必要があります。そうしないと、SCEP/.PFX 証明書ポリシーは失敗します。

Intune の他のポリシーを展開するのと同じ方法で、証明書プロファイルを展開します。

1.   **[ポリシー]** ワークスペースで、展開するポリシーを選択し、 **[展開の管理]**をクリックします。

2.   **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。

    -   **ポリシーを展開するには**、ポリシーを展開する対象となる 1 つ以上のグループを選択して、**[追加]** &gt; **[OK]** をクリックします。

    -   **ポリシーを展開せずにダイアログ ボックスを閉じるには**、**[キャンセル]** をクリックします。

展開済みポリシーを選択すると、ポリシー一覧の下部に展開についての詳細が表示されます。
###  次のステップ

証明書を使用して、電子メール、Wi-fi、VPN プロファイルをセキュリティで保護できます。

-  [電子メール プロファイルを使用して会社の電子メールへのアクセスを構成にする](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Microsoft Intune での Wi-Fi 接続](wi-fi-connections-in-microsoft-intune.md)
-  [Microsoft Intune での VPN 接続](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


