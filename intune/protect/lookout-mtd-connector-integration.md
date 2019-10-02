---
title: Microsoft Intune との Lookout 統合を設定する
titleSuffix: Microsoft Intune
description: モバイル デバイスから会社のリソースへのアクセスを制御するために、Mobile Threat Defense ソリューションとして Intune を Lookout Mobile Endpoint Security と統合する方法について説明します。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5b0d7644-3183-45ba-a165-0d82d70cb71e
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be2e9371288961d0afdf7ad6e8cfec8f734087f6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721293"
---
# <a name="set-up-lookout-mobile-endpoint-security-integration-with-intune"></a>Intout と Lookout Mobile Endpoint Security の統合を設定する
[前提条件](lookout-mobile-threat-defense-connector.md#prerequisites)を満たす環境であれば、Lookout Mobile Endpoint Security と Intune を統合できます。 この記事の情報では、統合の設定と、Intune で使用するための Lookout の重要な設定の構成について案内します。  

> [!IMPORTANT]
> Azure AD と Intune の統合に、Azure AD と関連付けられていない既存の Lookout Mobile Endpoint Security テナントを使用することはできません。 新しい Lookout Mobile Endpoint Security テナントを作成するように、Lookout のサポートに依頼してください。 Azure AD ユーザーの追加にはこの新しいテナントを使用してください。

## <a name="collect-azure-ad-information"></a>Azure AD の情報を収集する  
Lookout と Intune を統合するには、Lookout Mobility Endpoint Security テナントを Azure Active Directory (AD) サブスクリプションに関連付けます。

Lookout Mobile Endpoint Security サブスクリプションと Intune の統合を有効にするには、Lookout サポート (enterprisesupport@lookout.com) に次の情報を提供します。  

- **Azure AD テナントのディレクトリ ID**  

- Lookout Mobile Endpoint Security (MES) Console の**フル** アクセスを持つグループの **Azure AD グループ オブジェクト ID**。  
  **Lookout Console** にサインインできる*フル アクセス*を持つユーザーを含めるには、Azure AD でこのユーザー グループを作成します。 ユーザーが Lookout Console にサインインするには、このグループ、またはオプションの*制限付きアクセス* グループのメンバーである必要があります。 

- Lookout MES Console へのアクセスが**制限されている**グループの **Azure AD グループ オブジェクト ID** *(省略可能なグループ)* 
  このオプションのユーザー グループを Azure AD で作成し、Lookout Console のいくつかの構成および登録関連のモジュールにアクセスできないユーザーを含めるようにします。 代わりに、これらのユーザーは Lookout Console の **セキュリティ ポリシー** モジュールへの読み取り専用アクセス権を持っています。 ユーザーが Lookout Console にサインインするには、このオプションのグループ、または必須の*フル アクセス* グループのメンバーである必要があります。

 > [!TIP] 
 > アクセス許可の詳細については、Lookout Web サイトの[こちらの記事](https://personal.support.lookout.com/hc/articles/114094105653)をご覧ください。

### <a name="collect-information-from-azure-ad"></a>Azure AD から情報を収集する 

1. グローバル管理者アカウントで [Azure portal](https://portal.azure.com) にサインインします。

2. **[Azure Active Directory]**  >  **[プロパティ]** に移動し、 **[ディレクトリ ID]** を探します。 *[コピー]* ボタンを使用して [ディレクトリ ID] をコピーし、それをテキスト ファイルに保存します。

   ![Azure AD のプロパティ](./media/lookout-mtd-connector-integration/azure-ad-properties.png)  

3. 次に、Azure AD ユーザーに Lookout Console へのアクセスを許可するために使用するアカウントの Azure AD グループ ID を見つけます。 1 つのグループは "*フル アクセス*" 用です。"*制限付きアクセス*" 用の 2 つ目のグループは省略可能です。 *[オブジェクト ID]* を取得するには、アカウントごとに次の手順を実行します。  
   1. **[Azure Active Directory]**  >  **[グループ]** に移動して *[グループ - すべてのグループ]* ウィンドウを開きます。  

   2. "*フル アクセス*" 用に作成したグループを選択し、その *[概要]* ウィンドウを開きます。  

   3. *[コピー]* ボタンを使用して [オブジェクト ID] をコピーし、それをテキスト ファイルに保存します。  

   4. *制限付きアクセス* グループを使用している場合は、そのグループに対してこのプロセスを繰り返します。  

      ![Azure AD グループ オブジェクト ID](./media/lookout-mtd-connector-integration/azure-ad-group-id.png)  

   この情報を収集した後で、Lookout のサポート (メール: enterprisesupport@lookout.com) にお問い合わせください。 Lookout のサポート担当者は、お客様の連絡窓口となっている方と協力し、お客様が提供した情報を使用してサブスクリプションの登録と Lookout Enterprise アカウントの作成を行います。  

## <a name="configure-your-lookout-subscription"></a>Lookout サブスクリプションを構成する  
Lookout のサポート担当者が Lookout Enterprise アカウントを作成すると、Lookout のサポート担当者はサインイン URL (https://aad.lookout.com/les?action=consent ) へのリンクを含むメールを会社の主要な連絡先に送信します。 

### <a name="initial-sign-in"></a>初回サインイン  
Lookout MES Console に初めてサインインすると、同意ページ (https://aad.lookout.com/les?action=consent) が表示されます。 Azure AD グローバル管理者は、サインインして **[Accept]\(同意\)** するだけです。 それ以降のサインインでは、ユーザーがこのレベルの Azure AD 権限を持つ必要はありません。 

 同意ページが表示されます。 **[同意]** を選んで登録を完了します。 
   ![Lookout Console の初回サインイン ページのスクリーンショット](./media/lookout-mtd-connector-integration/lookout_mtp_initial_login.png)

受け入れて同意すると、Lookout Console にリダイレクトされます。

初回のサインインと同意が完了すると、 https://aad.lookout.com からサインインしたユーザーは MES Console にリダイレクトされます。 同意がまだ与えられていない場合、すべてのサインイン試行は "Bad Login Error" (不正ログイン エラー) になります。

### <a name="configure-the-intune-connector"></a>Intune コネクタを構成する  
次の手順では、Lookout の展開をテストするために Azure AD でユーザー グループを以前に作成したことを前提としています。 ベスト プラクティスは、Lookout 管理者と Intune 管理者が製品の統合に慣れるように、少数のユーザー グループから始めることです。 慣れてきたら、追加のユーザー グループに登録を拡張できます。

1. [Lookout MES Console](https://aad.lookout.com) にサインインし、 **[System]\(システム\)**  >  **[Connectors]\(コネクタ\)** に移動して、 **[Add Connector]\(コネクタの追加\)** を選択します。  **[Intune]** を選択します。

   ![[Connectors]\(コネクタ\) タブに [Intune] オプションが表示された Lookout コンソールの画像](./media/lookout-mtd-connector-integration/lookout_mtp_setup-intune-connector.png)

2. *[Microsoft Intune]* ウィンドウで、 **[Connection Settings]\(接続設定\)** を選択し、 **[Heartbeat Frequency]\(ハートビート頻度\)** を分単位で指定します。 

   ![ハートビート頻度が構成された [Connection Settings]\(接続設定\) タブの画像](./media/lookout-mtd-connector-integration/lookout-mtp-connection-settings.png)

3. **[Enrollment Management]\(登録管理\)** を選択し、Lookout に使う Azure AD グループの "*グループ名*" を **[Use the following Azure AD security groups to identify devices that should be enrolled in Lookout for Work]\(次の Azure AD セキュリティ グループを使用して Lookout for Work に登録する必要があるデバイスを特定する\)** に指定してから、 **[Save changes]\(変更の保存\)** を選択します。

    ![Intune コネクタ登録ページのスクリーンショット](./media/lookout-mtd-connector-integration/lookout-mtp-enrollment.png)  

   **使用するグループについて**:
   - ベスト プラクティスとして、Lookout の統合をテストする少数のユーザーを含む Azure AD セキュリティ グループから始めます。
   - Azure portal のセキュリティ グループの **[プロパティ]** に表示される **[グループ名]** は大文字と小文字が区別されます。  
   - **[Enrollment Management]\(登録管理\)** に指定するグループによって、デバイスが Lookout に登録される一連のユーザーが定義されます。 ユーザーが登録グループに含まれる場合、Azure AD のデバイスは、Lookout MES に登録されてアクティブ化の対象になります。 サポートされているデバイス上でユーザーが *Lookout for Work* アプリケーションを初めて開くと、アクティブにするように求められます。

4. **[State Sync]\(状態の同期\)** を選択し、*デバイスの状態*と*脅威の状態*の両方が **[On]\(オン\)** に設定されていることを確認します。  Lookout と Intune の統合が正常に動作するには、両方が必要です。  

5. **[Error Management]\(エラー管理\)** を選択し、エラー レポートを受け取るメール アドレスを指定してから、 **[Save changes]\(変更の保存\)** を選択します。
 
   ![Intune コネクタ エラー管理ページのスクリーンショット](./media/lookout-mtd-connector-integration/lookout-mtp-connector-error-notifications.png)

6. **[Create connector]\(コネクタの作成\)** を選択してコネクタの構成を完了します。 後で、結果に問題がなければ、他のユーザー グループまで登録を広げることができます。

## <a name="configure-intune-to-use-lookout-as-a-mobile-threat-defense-provider"></a>Mobile Threat Defense プロバイダーとして Lookout を使用するように Intune を構成する
Lookout MES を構成したら、Intune で Lookout への接続を設定する必要があります。  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。

2. **[デバイスのポリシー準拠]**  >  **[Mobile Threat Defense]** に移動し、 **[追加]** を選択します。

3. *[コネクタの追加]* ウィンドウで、ドロップダウンを使用して **[Lookout for Work]** を選択します。  

4. **[作成]** を選択します。 コネクタが Lookout MES との接続を確立すると、 *[コネクタの設定]* を使用できるようになります。

5. **[iOS デバイスのアプリの同期を有効にする]** を **[オン]** に設定します。 

6. **[保存]** を選択して構成を完了します。  これで Intune と Lookout MES が統合され、使用できる状態になりました。


## <a name="additional-settings-in-the-lookout-mes-console"></a>Lookout MES Console のその他の設定
Lookout MES Console で構成できるその他の設定を次に示します。  

### <a name="configure-enrollment-settings"></a>登録設定を構成する
Lookout MES Console で、 **[System]\(システム\)**  >  **[Manage Enrollment]\(登録管理\)**  >  **[Enrollment settings]\(登録設定\)** を選択します。  

- **[Disconnected Status]\(切断状態\)** に、接続されていないデバイスが切断済みとマークされるまでの日数を指定します。  

  切断されたデバイスは非準拠と見なされ、Intune の条件付きアクセス ポリシーに基づいて会社のアプリケーションにアクセスできなくなります。 1 から 90 日の値を指定できます。

  ![システム モジュールでの Lookout 登録設定](./media/lookout-mtd-connector-integration/lookout-console-enrollment-settings.png)

### <a name="configure-email-notifications"></a>メールの通知を構成する
脅威に関するメール通知を受け取るには、通知を受け取るユーザー アカウントを使って [Lookout MES Console](https://aad.lookout.com) にサインインします。  

- **[Preferences]\(基本設定\)** に移動し、受信する通知を **[ON]\(オン\)** に設定してから、変更を **[Save]\(保存\)** します。  

- 電子メール通知を受け取る必要がなくなった場合は、通知を **[OFF]** (オフ) に設定して変更を保存します。

  ![ユーザー アカウントが表示された [Preferences]\(基本設定\) ページのスクリーンショット](./media/lookout-mtd-connector-integration/lookout-mtp-email-notifications.png)



## <a name="configure-threat-classifications"></a>脅威の分類を構成する  
Lookout Mobile Endpoint Security によって、さまざまな種類のモバイルの脅威が分類されます。 Lookout の脅威の分類には、既定のリスク レベルが関連付けられています。 リスク レベルは会社の要件に合わせていつでも変更できます。

脅威レベルの分類と、それらに関連付けられているリスク レベルの管理方法については、[Lookout の脅威リファレンス](https://enterprise.support.lookout.com/hc/articles/360011812974)に関するページを参照してください。

>[!IMPORTANT]
> リスク レベルは、Mobile Endpoint Security で重要な要素の 1 つです。デバイスのコンプライアンスは、これらのリスク レベルに従って実行時に計算されるためです。  
> 
> Intune 管理者が設定するポリシーのルールに従って、デバイスはアクティブな脅威の最低レベルが**高**、**中**、または**低**の場合に非準拠と判断されます。 Lookout Mobile Endpoint Security での脅威分類ポリシーは、Intune でのデバイスのコンプライアンス計算に直接影響を与えます。  

## <a name="monitor-enrollment"></a>モニターの登録
セットアップが完了すると、Lookout Mobile Endpoint Security は Azure AD のポーリングを開始し、指定された登録グループに対応するデバイスを探します。  登録済みのデバイスに関する情報は、Lookout MES Console の **[Devices]\(デバイス\)** で確認できます。  
- デバイスの初期状態は "*保留中*" です。  
- デバイスに *Lookout for Work* アプリをインストールし、開き、アクティブ化すると、デバイスの状態が更新されます。

*Lookout for Work* アプリをデバイスに表示する方法の詳細については、[Intune で Lookout for Work アプリを追加する](mtd-apps-ios-app-configuration-policy-add-assign.md)方法に関するページを参照してください。

## <a name="next-steps"></a>次の手順

[Lookout アプリを設定する](mtd-apps-ios-app-configuration-policy-add-assign.md)
