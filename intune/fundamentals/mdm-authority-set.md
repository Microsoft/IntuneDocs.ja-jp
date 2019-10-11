---
title: モバイル デバイス管理機関の設定
titleSuffix: Microsoft Intune
description: Intune でモバイル デバイス管理機関を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cb5abe54529a9de575cf84b8a89b0f402f8d117b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727052"
---
# <a name="set-the-mobile-device-management-authority"></a>モバイル デバイス管理機関の設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。

可能な構成は以下のとおりです。

- **Intune スタンドアロン** - Azure Portal を利用して構成する、クラウドのみの管理。 Intune で提供される機能がすべて含まれます。 [Intune コンソールで MDM 機関を設定](#set-mdm-authority-to-intune)します。

- **Intune 共同管理** - Intune クラウド ソリューションと Windows 10 用 System Center Configuration Manager デバイスの統合。 Configuration Manager コンソールを使用して Intune を構成します。 [Intune へのデバイスの自動登録を構成します](https://docs.microsoft.com/sccm/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune)。 

    > [!Important]
    >新規のハイブリッド MDM の顧客のオンボーディングは非推奨となりました。 詳細については、「[Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)」 (ハイブリッド MDM から Azure での Intune に移行する) のブログ記事を参照してください。

- **Office 365 のモバイル デバイス管理** - Office 365 と Intune クラウド ソリューションの統合。 Microsoft 365 管理センターから Intune を構成します。 Intune スタンドアロンで利用できる機能の一部が含まれます。 Microsoft 365 管理センターで MDM 機関を設定します。

- **Office 365 MDM との共存** テナント上で MDM for Office 365 および Intune を両方とも同時実行でアクティブ化して使用し、ユーザーごとに管理機関を Intune または MDM for Office 365 のどちらかに設定して、どのサービスがモバイル デバイスの管理に使用されるかを指定します。 ユーザーの管理機関は、ユーザーに割り当てられたライセンスに基づいて定義されます。 詳細については、「[Microsoft Intune Co-existence with MDM for Office 365 (Microsoft Itune と MDM for Office 365 の共存)](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)」を参照してください。

## <a name="set-mdm-authority-to-intune"></a>MDM 機関を Intune に設定する

MDM 機関をまだ設定していない場合は、次の手順に従います。 SCCM から変更するには、「[ハイブリッド MDM のユーザーとデバイスを Intune スタンドアロンに移行する](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)」を参照してください。

1. [Azure portal 内の Intune ](https://aka.ms/intuneportal)で、オレンジのバナーを選択して **[モバイル デバイス管理機関]** 設定を開きます。 オレンジのバナーは、MDM 機関をまだ設定していない場合にのみ表示されます。
2. **[モバイル デバイス管理機関]** で、次の選択肢から MDM 機関を選択します。
   - **Intune MDM 機関**
   - **なし**

   ![Intune のモバイル デバイス管理機関設定画面のスクリーンショット](./media/mdm-authority-set/set-mdm-auth.png)

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

## <a name="change-mdm-authority-to-office-365"></a>MDM 機関を Office 365 に変更する

Office 365 MDM をアクティブにするには (または、既存の Intune サービスに加えて MDM の共存を有効にするには)、[https://protection.office.com](https://protection.office.com) に進み、 **[データ損失防止]**  >  **[デバイス セキュリティ ポリシー]**  >  **[管理対象デバイスの一覧を表示する]**  >  **[始めましょう]** の順に選択します。

詳細については、「[Office 365 でのモバイル デバイス管理 (MDM) の設定](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)」を参照してください。

エンド ユーザーの管理を Office 365 MDM によってのみ行う場合は、Office 365 MDM をアクティブにした後で、割り当てられている Intune および/または EMS ライセンスを削除します。

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>MDM 証明書の有効期限が切れた後のモバイル デバイスのクリーンアップ

MDM 証明書は、モバイル デバイスが Intune サービスと通信しているときに自動的に更新されます。 モバイル デバイスがワイプされたり、一定の時間 Intune サービスとモバイル デバイスが通信できなかったりすると、MDM 証明書は更新されません。 デバイスは、MDM 証明書の有効期限が切れてから 180 日後に、Azure Portal から削除されます。

## <a name="remove-mdm-authority"></a>MDM 機関を削除する

MDM 機関を [不明] に戻すことはできません。 MDM 機関は、登録されたデバイスからどのポータルにレポートするか (Microsoft Intune または Office 365 MDM) を特定するサービスによって利用されます。

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

- MDM 機関を変更した後に、次の手順を実行して、新しいデバイスが新しい機関に正常に登録されたことを確認します。   
  - 新しいデバイスを登録する
  - 新しく登録したデバイスが、Configuration Manager コンソールに表示されることを確認します。
  - 管理コンソールからデバイスに対して、リモート ロックなどのアクションを実行します。 成功した場合、そのデバイスは新しい MDM 機関で管理されていることを示します。
- 特定のデバイスで問題がある場合、できるだけ早くデバイスを新しい機関に接続し、管理対象にするには、そのデバイスの登録を解除してから再登録します。

## <a name="next-steps"></a>次の手順

MDM 機関が設定されると、[デバイスの登録](../enrollment/device-enrollment.md)を開始することができます。
