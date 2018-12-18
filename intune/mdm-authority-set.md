---
title: モバイル デバイス管理機関の設定
titlesuffix: Microsoft Intune
description: Intune でモバイル デバイス管理機関を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6f0138da6e9ea427ad07ad3b41dd22b7319bb044
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112580"
---
# <a name="set-the-mobile-device-management-authority"></a>モバイル デバイス管理機関の設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

可能な構成は以下のとおりです。

- **Intune スタンドアロン** - Azure Portal を利用して構成する、クラウドのみの管理。 Intune で提供される機能がすべて含まれます。 [Intune コンソールで MDM 機関を設定](#set-mdm-authority-to-intune)します。

- **Intune ハイブリッド** - Intune クラウド ソリューションと System Center Configuration Manager の統合。 Configuration Manager コンソールを使用して Intune を構成します。 [Configuration Manager で MDM 機関を設定](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)します。 

    > [!Important]
    >ハイブリッド MDM への新規顧客のオンボードは、次のリリースから行われなくなります。 詳しくは、「[MC146431 Plan for Change blog](https://blogs.technet.microsoft.com/intunesupport/2018/08/14/move-from-hybrid-mobile-device-management-to-intune-on-azure/)」(MC146431 - 変更計画) に関するブログをご覧ください。

- **Office 365 のモバイル デバイス管理** - Office 365 と Intune クラウド ソリューションの統合。 Office 365 管理センターから Intune を構成します。 Intune スタンドアロンで利用できる機能の一部が含まれます。 Office 365 管理センターで MDM 機関を設定します。

> [!IMPORTANT]
> Configuration Manager 1610 以降のバージョンと Microsoft Intune バージョン 1705 では、MDM 機関の変更にあたって Microsoft サポートに問い合わせる必要はありません。また、既存のマネージド デバイスの登録を解除して再登録する必要もありません。 詳細については、「[MDM 機関を Configuration Manager に変更する準備](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager)」を参照してください。

## <a name="set-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

MDM 機関をまだ設定していない場合は、次の手順に従います。 MDM 機関を別の MDM 機関に変更するには、後述する[MDM 機関の変更](#prepare-to-change-the-mdm-authority-to-configuration-manager)に関するセクションを参照してください。

1. [Azure ポータル](https://portal.azure.com) にサインインします。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. オレンジのバナーを選択し、**[モバイル デバイス管理機関]** 設定を開きます。 オレンジのバナーは、MDM 機関をまだ設定していない場合にのみ表示されます。
4. **[モバイル デバイス管理機関]** で、次の選択肢から MDM 機関を選択します。
   - **Intune MDM 機関**
   - **Configuration Manager MDM 機関**
   - **なし**

   ![Intune のモバイル デバイス管理機関設定画面のスクリーンショット](media/set-mdm-auth.png)

   MDM 機関が Intune に正しく設定されたことを示すメッセージが表示されます。

### <a name="workflow-of-intune-administration-ui"></a>Intune 管理 UI のワークフロー
Android または Apple デバイスの管理が有効になっていると、Intune では、それぞれのデバイスを管理するために、デバイスとユーザー情報を送信し、これらのサード パーティ サービスと統合できるようにします。

データを共有することに同意するシナリオは、次の場合に含まれます。
- Android 仕事用プロファイルを有効にする。
- Apple MDM プッシュ通知証明書を有効にしてアップロードする
- Device Enrollment Program、School Manager および Volume Purchasing Program など、Apple の任意のサービスを有効にする

いずれの場合も、同意はモバイル デバイス管理サービスの実行に厳密に関連します。 たとえば、IT 管理者が Google または Apple デバイスの登録を許可されていることを確認します。 新しいワークフローが公開されたとき、どの情報が共有されるかを示すドキュメントは、次の場所から入手することができます。
- [Intune から Google に送られるデータ](https://aka.ms/Data-intune-sends-to-google)
- [Intune から Apple に送られるデータ](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>主な考慮事項
新しい MDM 機関に切り替えた後、多くの場合、デバイスがチェックインしてサービスと同期されるまでに移行時間 (最大 8 時間) があります。 新しい MDM 機関 (ハイブリッド) で、登録済みデバイスが変更後も管理および保護されるように設定を構成する必要があります。 
- デバイスの既存の設定が新しい MDM 機関の設定 (Intune スタンドアロン) に置き換わるように、変更後にご使用のデバイスをサービスに接続する必要があります。
- MDM 機関を変更した後に、MDM 機関 (Intune スタンドアロン) の基本的な設定 (プロファイルなど) の一部は、最大 7 日間、またはデバイスが初めてサービスに接続するまで、デバイスに残ります。 可能な限り早く新しい MDM 機関 (ハイブリッド) でアプリと設定 (ポリシー、プロファイル、アプリなど) を構成し、既存の登録済みデバイスがあるユーザーを含むユーザー グループにその設定を展開することをお勧めします。 MDM 機関の変更後、デバイスがサービスに接続すると、新しい MDM 機関の新しい設定がすぐに送信されるので、管理と保護の中断を回避できます。
- Intune と Configuration Manager の両方に同じカテゴリが存在するときは、新しい MDM 機関に切り替えた後、デバイスのいかなるカテゴリ割り当ても継承されません。 デバイス カテゴリを引き続き利用するには、MDM 機関を変更し、デバイスが Configuration Manager コンソールに表示された後、移行したデバイスを適切なコレクションに手動で追加する必要があります。
- 関連付けられているユーザーがいない (通常は iOS Device Enrollment Program または一括登録シナリオの場合) デバイスは、新しい MDM 機関に移行されません。 これらのデバイスでは、新しい MDM 機関への移行を支援してもらうためにサポートを要請する必要があります。

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>MDM 機関を Configuration Manager に変更する準備

MDM 機関の変更に備えて、次の情報を確認します。
- MDM 機関を変更するオプションを使用するには、Configuration Manager バージョン 1610 以降が必要です。
- 新しい MDM 機関に変更した後に、デバイスがサービスに接続できるようになるまでに最大 8 時間かかります。
- Intune スタンドアロンで現在管理されているすべてのユーザーを含む Configuration Manager ユーザー コレクションを作成します。このユーザー コレクションは、Configuration Manager コンソールで Intune サブスクリプションをセットアップするときに使用します。 このコレクションにより、MDM 機関の変更互換モード、ユーザーとそのデバイスには Configuration Manager ライセンスが割り当てられ、ハイブリッド環境で管理されるようになります。
- このユーザー コレクションには、IT 管理者ユーザーも必ず含めます。  
- 変更前は、MDM 機関は Intune 管理コンソールで **[Microsoft Intune に設定]** \(スタンドアロン\) と表示されます。
- Microsoft Intune 管理コンソールで、MDM 機関に **[Microsoft Intune に設定]** \(スタンドアロン テナント\) と表示されることを確認してから、MDM 機関を変更します。
    > [!NOTE]    
    > MDM 機関に **[Managed by Intune and Office 365]\(Intune と Office 365 が管理\)** と表示される場合、MDM 機関を **Configuration Manager** (ハイブリッド) に変更すると、Office 365 で管理されていた MDM デバイスは管理されなくなります。 このようなユーザーには、MDM 機関を変更する前に、Intune または Enterprise Mobility Suite のライセンスを付与することをお勧めします。   

- [Microsoft Intune 管理コンソール](http://manage.microsoft.com)で、デバイス登録マネージャー ロールを削除します。 詳細については、「[Intune からのデバイス登録マネージャーの削除](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions)」を参照してください。
- 構成するデバイス グループ マッピングをオフにします。 詳細については、「[Microsoft Intune でデバイス グループのマッピングを使用してデバイスを分類する](device-group-mapping.md)」を参照してください。
- MDM 機関の変更中に、エンドユーザーへの影響はあまりありません。 ただし、変更後すぐに、ユーザーがデバイスの電源を入れてサービスに接続するように、この変更について通知することをお勧めします。 この注意により、多数のデバイスが迅速に新しい機関経由でサービスに接続し、登録できるようになります。
- Intune スタンドアロンを使用して iOS デバイスを管理していて、MDM 機関を変更する予定の場合は、Intune で使用されていたものと同じ Apple Push Notification サービス (APNs) 証明書を更新し、Configuration Manager (ハイブリッド) でテナントのセットアップに使用する必要があります。    

    > [!IMPORTANT]  
    > ハイブリッドに別の APNs 証明書を使用する場合、以前に登録されていた iOS デバイスはすべて未登録になるため、デバイスを再登録するプロセスを実行する必要があります。 MDM 機関を変更する前に、Intune で iOS デバイスの管理に使用されていた APNs 証明書を正確に把握しておく必要があります。 Apple Push 証明書ポータル (https://identity.apple.com)) に記載されているものと同じ証明書を検索し、元の APNs 証明書の作成に使用された Apple ID を持つユーザーを特定し、新しい MDM 機関を変更する際に同じ APNs 証明書を更新できることを確認します。

## <a name="change-the-mdm-authority-to-configuration-manager"></a>MDM 機関を Configuration Manager に変更する

1. Configuration Manager コンソールで **[管理]** &gt; **[概要]** &gt; **[クラウド サービス]** &gt; **[Microsoft Intune サブスクリプション]** に移動し、Intune サブスクリプションを選択して追加します。
2. Intune で MDM 機関を設定したときに元々使用していた Intune テナントにサインインし、**[次へ]** をクリックします。
3. **[MDM 機関を Configuration Manager に変更]** を選択し、**[次へ]** をクリックします。
4. 新しいハイブリッド MDM 機関で継続して管理するすべてのユーザーを含むユーザー コレクションを選択します。
5. **[次へ]** をクリックして、ウィザードを完了します。 これで MDM 機関は **Configuration Manager** に変更されました。
6. 同じ Intune テナントを使用して [Microsoft Intune 管理コンソール](http://manage.microsoft.com)にサインインし、MDM 機関が **[Configuration Manager に設定]** に変更されたことを確認します。
7. MDM 機関を Configuration Manager に変更したら、[iOS の登録](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)と[Android の登録](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android)を設定することができます。
8. Configuration Manager コンソールで、新しい MDM 機関 (ハイブリッド) から新しい設定とアプリを構成し、展開します。

次にデバイスをサービスに接続すると、新しい MDM 機関と同期し、新しい設定を受信します。

## <a name="change-mdm-authority-to-office-365"></a>MDM 機関を Office 365 に変更する

既存の Intune サービスに加えて Office 365 MDM をアクティブにするには、[https://protection.office.com](https://protection.office.com) に進み、**[データ損失防止]** > **[デバイス セキュリティ ポリシー]** > **[View list of Managed Devices]\(マネージド デバイスの一覧を表示\)** > **[始めましょう]** の順に選択します。

詳細については、「[Office 365 でのモバイル デバイス管理 (MDM) の設定](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)」を参照してください。

エンド ユーザーの管理を Office 365 MDM によってのみ行う場合は、Office 365 MDM をアクティブにした後で、割り当てられている Intune および/または EMS ライセンスを削除します。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。

## <a name="remove-mdm-authority"></a>MDM 機関を削除する

MDM 機関を [不明] に戻すことはできません。 Microsoft サーバーでは、登録されたデバイスのレポート先のポータル (ConfigMGR、Azure Intune、Office 365 MDM) を特定するために MDM 機関を利用します。

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>MDM 機関を変更した後の注意点

- テナントの MDM 機関が変更されたことを Intune サービスが検出すると、登録されているすべてのデバイスに、サービスにチェックインして同期するように促す通知メッセージを送信します (この通知は定期的にスケジュールされているチェックインとは別になります)。 そのため、テナントの MDM 機関が Intune スタンドアロンからハイブリッドに変更された後は、電源を入れてオンラインになったすべてのデバイスはサービスに接続し、新しい MDM 機関を受信し、ハイブリッドに管理されるようになります。 これらのデバイスの管理と保護は中断されません。
- MDM 機関の変更中 (または変更直後) にデバイスの電源が入り、オンラインだった場合でも、デバイスが新しい MDM 機関のサービスに登録されるまでに最大 8 時間の遅れがあります (次の定期的なチェックインのタイミングによって異なります)。    

  > [!IMPORTANT]    
  > MDM 機関を変更してから、更新された APNs 証明書が新しい機関にアップロードされるまで、iOS デバイスの新しいデバイスの登録とデバイスのチェックインは失敗します。 そのため、MDM 機関を変更した後は、できるだけ早く APNs 証明書を確認し、新しい機関にアップロードすることが重要です。

- ユーザーが新しい MDM 機関にすぐに変更するには、デバイスからサービスへのチェックインを手動で開始します。 ポータル サイト アプリを使用して、デバイス コンプライアンス チェックを開始することで、ユーザーはこの変更を簡単に実行できます。
- MDM 機関の変更後に、デバイスがサービスにチェックインして同期した後に、正常に動作していることを確認するには、Configuration Manager コンソールでそのデバイスを探します。 Intune で管理されていたデバイスが、Configuration Manager でマネージド デバイスとして表示されるようになります。    
- MDM 機関の変更中にデバイスがオフラインだったときから、デバイスがサービスにチェックインするまでは中間期間があります。 この中間期間にも確実にデバイスを保護し、利用できるように、最大 7 日間 (またはデバイスが新しい MDM 機関に接続し、新しい設定を受信して既存の設定が上書きされるまで)、次のプロファイルがデバイスに残ります。
    - 電子メール プロファイル
    - VPN プロファイル
    - 証明書プロファイル
    - Wi-Fi プロファイル
    - 構成プロファイル
- 新しい MDM 機関に変更した後は、Microsoft Intune 管理コンソールのコンプライアンス データが正確に報告されるまでに最大 1 週間かかる可能性があります。 ただし、Azure Active Directory とデバイスのコンプライアンス状態は正確なので、デバイスは引き続き保護されます。
- 既存の設定を上書きするための新しい設定は、古い設定が確実に上書きされるように、古い設定と同じ名前にする必要があります。 そうしないと、デバイスのプロファイルとポリシーが重複する可能性があります。    

  > [!TIP]    
  > ベスト プラクティスとして、MDM 機関の変更が完了した直後に、すべての管理設定、構成、展開を作成することをお勧めします。 こうすることで、中間期間にもデバイスを保護し、アクティブに管理することができます。

-  MDM 機関を変更した後に、次の手順を実行して、新しいデバイスが新しい機関に正常に登録されたことを確認します。   
    - 新しいデバイスを登録する
    - 新しく登録したデバイスが、Configuration Manager コンソールに表示されることを確認します。
    - 管理コンソールからデバイスに対して、リモート ロックなどのアクションを実行します。 成功した場合、そのデバイスは新しい MDM 機関で管理されていることを示します。
- 特定のデバイスで問題がある場合、できるだけ早くデバイスを新しい機関に接続し、管理対象にするには、そのデバイスの登録を解除してから再登録します。

## <a name="next-steps"></a>次の手順

MDM 機関が設定されると、[デバイスの登録](device-enrollment.md)を開始することができます。