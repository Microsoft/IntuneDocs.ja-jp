---
title: "証明書プロファイルを構成する | Microsoft Docs"
description: "Intune 証明書プロファイルを作成する方法について説明します。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: acfcb5fc8bf0af2ba5fb897e9e18d61e60f11978
ms.lasthandoff: 04/14/2017


---

# <a name="configure-intune-certificate-profiles"></a>Intune 証明書プロファイルを構成する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

「[SCEP の証明書インフラストラクチャを構成する](configure-certificate-infrastructure-for-scep.md)」または「[PFX の証明書インフラストラクチャを構成する](configure-certificate-infrastructure-for-pfx.md)」の説明に従ってインフラストラクチャおよび証明書を構成した後、証明書プロファイルを作成できます。 その手順は次のとおりです。

- **タスク 1** - 信頼されたルート CA 証明書をエクスポートする
- **タスク 2** - 信頼された証明書プロファイルを作成する
- **タスク 3** - 2 種類の証明書プロファイルのいずれかを作成する:
  - SCEP 証明書プロファイル
  - .PFX 証明書プロファイル

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>**タスク 1** - 信頼されたルート CA 証明書をエクスポートする
発行元 CA または発行元 CA を信頼するデバイスから、信頼されたルート証明機関 (CA) 証明書を **.cer** ファイルとしてエクスポートします。 秘密キーをエクスポートしないでください。

信頼された証明書プロファイルを構成するときにこの証明書をインポートします。

## <a name="task-2-create-trusted-certificate-profiles"></a>**タスク 2** - 信頼された証明書プロファイルを作成する
Simple Certificate Enrollment Protocol (SCEP) または PKCS #12 (.PFX) 証明書プロファイルを作成する前に、信頼された証明書プロファイルを作成する必要があります。 モバイル デバイス プラットフォームごとに、信頼された証明書プロファイルと、SCEP または .PFX プロファイルが必要です。

### <a name="to-create-a-trusted-certificate-profile"></a>信頼された証明書プロファイルを作成するには

1.  [Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[ポリシーの追加]** を選択し、デバイスのプラットフォームを選択します。 次のデバイスについて信頼済み証明書プロファイルを作成できます。

-  Android 4 以降

-  Android for Work

-  iOS 7.1 以降

-  Mac OS X 10.9 以降

-  Windows 8.1 以降

-  Windows Phone 8.1 以降

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

2.  **信頼済み証明書プロファイル** ポリシーを追加します。

    詳しくは、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

3.  要求された情報を入力して、Android、iOS、Mac OS X、Windows 8.1、または Windows Phone 8.1 用の信頼された証明書プロファイルの設定を構成します。
4.  **[証明書ファイル]** 設定で、発行元 CA からエクスポートした信頼されたルート CA 証明書 (.cer ファイル) をインポートします。 **[保存先ストア]** 設定は、Windows 8.1 以降を実行中のデバイスで、1 つ以上の証明書ストアを持っているデバイスにのみ適用されます。

4.  **[ポリシーの保存]** を選択します。

新しいポリシーが **[ポリシー]** ワークスペースに表示されます。 これでデプロイが可能になりました。

> [!NOTE]
>
> Android デバイスと Android for Work デバイスでは、サードパーティにより信頼できる証明書がインストールされたことを知らせる通知が表示されます。


## <a name="task-3-create-scep-or-pfx-certificate-profiles"></a>**タスク 3** – SCEP または .PFX 証明書プロファイルを作成する
信頼された CA 証明書プロファイルを作成した後、使用する各プラットフォーム用の SCEP または .PFX 証明書プロファイルを作成します。 SCEP 証明書プロファイルを作成するときは、その同じプラットフォームに対する信頼された証明書プロファイルを指定する必要があります。 これにより 2 つの証明書プロファイルがリンクされますが、それでも各プロファイルを個別にデプロイする必要があります。

### <a name="to-create-an-scep-certificate-profile"></a>SCEP 証明書プロファイルを作成するには

1.  [Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[ポリシーの追加]** を選択し、デバイスのプラットフォームを選択します。  次のデバイスについて SCEP 証明書プロファイルを作成できます。

-  Android 4 以降

-  Android for Work

-  iOS 7.1 以降

-  Mac OS X 10.9 以降

-  Windows 8.1 以降

-  Windows Phone 8.1 以降

2.  **SCEP 証明書プロファイル** ポリシーを追加します

    詳しくは、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。

3.  プロファイル構成ページの指示に従って、SCEP 証明書プロファイル設定を構成します。
    > [!NOTE]
    >
    > **[サブジェクト名の形式]** で、**[カスタム]** を選択してサブジェクト名のカスタム形式を入力します (iOS のプロファイルのみ)。
    >
    > カスタム形式で現在サポートされている 2 つの変数は、`Common Name (CN)` と `Email (E)` です。 これらの変数と静的文字列の組み合わせを使用することで、このようなサブジェクト名のカスタム形式を作成できます。

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > この例では、管理者は `CN` と `E` の変数に加えて、組織単位、組織、市区町村、州、および国の値の文字列を使用してサブジェクト名形式を作成しています。 「[CertStrToName 関数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)」で、サポートされる文字列を一覧にしています。

4.  **[ポリシーの保存]** を選択します。

新しいポリシーが **[ポリシー]** ワークスペースに表示されます。 これでデプロイが可能になりました。

### <a name="to-create-a-pfx-certificate-profile"></a>.PFX 証明書プロファイルを作成するには

1.  [Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[ポリシーの追加]** を選択し、デバイスのプラットフォームを選択します。 次のデバイスについては、.PFX 証明書がサポートされています。
  - Android 4 以降
  - Android for Work
  - Windows 10 以降
  - Windows Phone 10 以降
  - iOS 8.0 以降)    


2.  **.PFX 証明書プロファイル** ポリシーを追加します。
      詳しくは、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」をご覧ください。
3.  ポリシー フォームで要求されている情報を入力します。
4.  **[ポリシーの保存]** を選択します。

新しいポリシーが **[ポリシー]** ワークスペースに表示されます。 これでデプロイが可能になりました。

## <a name="deploy-certificate-profiles"></a>証明書プロファイルを展開する
証明書プロファイルをデプロイするときに、信頼された CA 証明書プロファイルの証明書ファイルは、デバイスにインストールされます。 デバイスは、SCEP または .PFX 証明書プロファイルを使用してデバイスによる証明書要求を作成します。

証明書プロファイルは、プロファイルを作成するときに使用するプラットフォームを実行しているデバイスのみにインストールされます。

-   ユーザー コレクションまたはデバイス コレクションに証明書プロファイルをデプロイできます。

    > [!TIP]
    > デバイス登録後すぐに証明書をデバイスに公開するには、証明書プロファイルをデバイス グループではなくユーザー グループにデプロイします。 デバイス グループにデプロイした場合は、デバイスがポリシーを受け取る前に、デバイスの登録を完全に行う必要があります。

-   各プロファイルは個別にデプロイしますが、信頼されたルート CA と、SCEP または .PFX プロファイルをデプロイする必要もあります。 そうしないと、SCEP または .PFX 証明書ポリシーは失敗します。

Intune の他のポリシーをデプロイするのと同じ方法で、証明書プロファイルをデプロイします。

1.  **[ポリシー]** ワークスペースで、展開するポリシーを選び、**[展開の管理]** を選びます。
2.  **[展開の管理]** ダイアログ ボックスで、次の操作を実行します。
    -   **ポリシーをデプロイするには**、ポリシーをデプロイする 1 つ以上のグループを選択して、**[追加]**&gt;**[OK]** の順に選択します。
    -   **ポリシーをデプロイせずにダイアログ ボックスを閉じるには**、**[キャンセル]** を選択します。

デプロイ済みポリシーを選択すると、ポリシー一覧の下部にデプロイについての詳細が表示されます。

### <a name="next-steps"></a>次のステップ

次に、証明書を使用して、電子メール、Wi-Fi、VPN プロファイルをセキュリティで保護する方法について説明します。

-  [電子メール プロファイルを使用して会社の電子メールへのアクセスを構成する](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Microsoft Intune での Wi-Fi 接続](wi-fi-connections-in-microsoft-intune.md)
-  [Microsoft Intune での VPN 接続](vpn-connections-in-microsoft-intune.md)

