---
title: Wandera モバイル脅威保護と Intune との統合を設定する
titleSuffix: Intune on Azure
description: Microsoft Intune で Wandera モバイル脅威保護ソリューションを設定し、モバイル デバイスから会社のリソースへのアクセスを制御する方法。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4f2969c6bb7f15022990aa99bbf20e94588406e
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512301"
---
# <a name="integrate-wandera-mobile-threat-protection-with-intune"></a>Wandera モバイル脅威保護を Intune と統合する  

Wandera Mobile Threat Defense ソリューションを Intune と統合するには、以下の手順を実行します。  

## <a name="before-you-begin"></a>始める前に  

Wandera を Intune と統合する手順を開始する前に、次の前提条件を満たしていることを確認してください。
- Microsoft Intune サブスクリプション  
- 次のアクセス許可を付与する Azure Active Directory 管理者資格情報:  
  - サインインしてユーザー プロファイルを読み取る  
  - サインインしたユーザーとしてディレクトリにアクセスする  
  - ディレクトリ データの読み込み  
  - Intune にデバイス情報を送信する  

- Wandera サブスクリプション:
  - EMM Connect のライセンスを取得している 1 つ以上の Wandera アカウント  
  - Wandera でのスーパー管理者特権を持つアカウント  
 
### <a name="wandera-mobile-threat-defense-app-authorization"></a>Wandera Mobile Threat Defense アプリの承認  

Wandera Mobile Threat Defense アプリの承認プロセス:  
- Wandera Mobile Threat Defense サービスがデバイスの正常性状態に関する情報を Intune に戻すことが許可されます。  
- Wandera は、Azure AD 登録グループ メンバーシップと同期してデバイスのデータベースを設定します。  
- Wandera RADAR 管理ポータルが Azure AD シングル サインオン (SSO) を使用することが許可されます。  
- Wandera Mobile Threat Defense アプリが Azure AD SSO を使ってサインインすることが許可されます。  


## <a name="set-up-wandera-mobile-threat-defense-integration"></a>Wandera Mobile Threat Defense の統合を設定する  
Wandera の *EMM Connect* の設定には、Intune と Wandera コンソールの両方で完了するワンタイム構成プロセスが必要です。 この構成プロセスには約 15 分かかります。 この構成は、Wandera テクニカル アカウントやサポート担当者との連携なしで完了できます。  

### <a name="enable-support-for-wandera-in-intune"></a>Intune での Wandera のサポートを有効にする
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインして、 **[デバイスのポリシー準拠]**  >  **[Mobile Threat Defense]** に移動し、 **[追加]** を選択します。

2. **[コネクタの追加]** ページで、ドロップダウンを使用して **[Wandera]** を選択します。 次いで **[作成]** を選択します。  

3. [Mobile Threat Defense] ウィンドウで、コネクタの一覧から **[Wandera]** MTD コネクタを選択し、 *[コネクタの編集]* ウィンドウを開きます。 **[Open the Wandera admin console]\(Wandera 管理コンソールを開く\)** を選択して [RADAR](https://radar.wandera.com/login) (Wandera の管理コンソール) を開き、サインインします。 

4. Wandera コンソールで、 **[設定]**  >  **[EMM Integration]\(EMM 統合\)** に移動し、 **[EMM Connect]** タブを選択します。 *[EMM Vendor]\(EMM ベンダー\)* ドロップダウンを使用して、 *[Microsoft Intune]* を選択します。

   ![Intune の選択](media/wandera-mtd-connector-integration/set-up-intune-in-radar.png)

5. **[アクセス許可の付与]** を選択して Intune ポータルへの接続を開きます。 Intune 管理者の資格情報を使用してサインインし、チェックボックスをオンにした後、アクセス許可要求に **[同意する]** を選択します。  

   ![アクセス許可に同意する](media/wandera-mtd-connector-integration/permissions.png) 

6. Wandera によって接続が完了し、RADAR 管理コンソールに戻ります。 必要に応じて、さらなる構成に対してアクセスを **[許可]** するプロセスを繰り返します。  

   ![統合とアクセス許可](media/wandera-mtd-connector-integration/integrations-and-permissions.png) 

7. RADAR コンソールで、 **[EMM Label]\(EMM ラベル\)** の下に表示される **SyncOnly** グループの名前をコピーします。 Wandera との同期用に Intune でグループを構成するために、この名前を使用します。

   ![統合とアクセス許可](media/wandera-mtd-connector-integration/sync-group-name.png) 

8. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) コンソールに戻り、Wandera MTD コネクタを編集します。 使用可能な切り替えを **[オン]** に設定して、構成を **[保存]** します。  

   ![Wandera の有効化](media/wandera-mtd-connector-integration/enable-wandera.png) 

これで Intune と Wandera が接続されました。  

## <a name="configure-the-wandera-applications-and-synchronization-group"></a>Wandera アプリケーションと同期グループを構成する  
Wandera を展開するには、使用するプラットフォーム (iOS および Android) 用の Wandera モバイル アプリを Intune に追加して、それらを同期用の特定のグループ、すなわち *SyncOnly* グループに割り当てます。 

以下のセクションと手順では、このプロセスについて説明します。

Wandera からのこのプロセスに関する詳細情報については、Wandera の [RADAR](https://radar.wandera.com/login) にサインインしてください。 **[設定]**  >  **[EMM Integration]\(EMM 統合\)** に移動し、 **[App Push]\(アプリのプッシュ\)** タブを選択してから、 **[Microsoft Intune]** を選択します。 [App Push]\(アプリのプッシュ\) タブが Intune に固有の手順と共に更新されます。  

### <a name="add-the-wandera-apps"></a>Wandera アプリを追加する  
Intune でクライアント アプリを作成して、Android および iOS デバイスに Wandera アプリを展開します。 Wandera アプリに固有の手順とカスタムの詳細については、[MTD アプリの追加](mtd-apps-ios-app-configuration-policy-add-assign.md)に関する記事をご覧ください。  

アプリを作成したら、ここに戻り、同期グループを作成してアプリを割り当てます。  


### <a name="create-the-synchronization-group-and-assign-the-apps"></a>同期グループを作成してアプリを割り当てる

1. Wandera RADAR コンソール内から、 **[EMM Label]\(EMM ラベル\)** の下に表示される **SyncOnly** グループの名前を取得します。 手順 7 で、[Intune で Wandera のサポートを有効化](#enable-support-for-wandera-in-intune)しているときに、この名前を保存していたかもしれません。 Wandera の同期用に Intune のグループの名前としてこの名前を使用します。  

2. Intune コンソールで、 **[グループ]** に移動して **[新しいグループ]** を選択します。 次を指定して、Wandera で使用する同期グループを構成します。
   - **[グループの種類]** :**セキュリティ**
   - **[グループ名]** :Wandera RADAR 管理コンソールから取得した **SyncOnly** の名前を指定します。

   ![同期グループの構成](media/wandera-mtd-connector-integration/configure-sync-group.png)

3. **[メンバー]** を選択して、Wandera で使用する Android および iOS デバイスを含むグループを割り当てます。

4. **[作成]** を選択してグループを保存します。

詳細については、[アプリの展開](apps-deploy.md)に関する記事をご覧ください

### <a name="assign-the-wandera-apps-to-the-synchronization-group"></a>Wandera アプリを同期グループに割り当てる  
iOS および Android 用に作成した Wandera アプリについて、次の手順を繰り返します。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインして **[クライアント アプリ]**  >  **[アプリ]** に移動し、Wandera アプリを選択します。  

2. **[割り当て]** を選択してから、 **[グループの追加]** を選択します。  

3. *[グループの追加]* ウィンドウで、 *[割り当ての種類]* に対して **[必須]** を選択します。

4. **[組み込まれたグループ]** を選択した後、 **[含めるグループを選択]** します。 Wandera の同期用に作成したグループを指定し、 **[選択]**  >  **[OK]**  >  **[OK]** の順にクリックします。 **[保存]** を選択してグループの割り当てを完了します。  
 

## <a name="next-steps"></a>次の手順  
これで統合を構成できたので、ポリシーの構成、高度な条件付きアクセスの設定、Wandera 管理コンソールでのレポートの表示を始められます。 Wandera の管理および構成について詳しくは、Wandera ドキュメント内の[サポート センターの入門ガイド](https://radar.wandera.com/?return_to=https://wandera.force.com/Customer/s/getting-started)をご覧ください。  
 