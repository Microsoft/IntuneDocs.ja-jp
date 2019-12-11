---
title: Microsoft Intune での Windows for Business Update 設定 - Azure | Microsoft Docs
description: Intune を使用して展開できる Windows 10 デバイスの WUfB 設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f3359bc5544b3a353271ea17083c8c3acb49742
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72584463"
---
# <a name="windows-update-settings-for-intune"></a>Intune での Windows Update の設定  

Microsoft Intune を使用して[構成および管理](windows-update-for-business-configure.md)できる Windows 10 更新プログラムの設定を表示します。  

Intune 内で Windows 10 更新プログラム リングの設定を構成する場合、Windows Update の設定を構成することになります。 Windows Update の設定に Windows 10 バージョンの依存関係がある場合、バージョンの依存関係は設定の詳細に記載されています。  

## <a name="update-settings"></a>Update の設定  

Update の設定では、デバイスによってダウンロードされるものとそのタイミングを制御します。 各設定の動作について詳しくは、Windows リファレンス ドキュメントを参照してください。  

- **サービス チャネル**  
  **既定**: 半期チャネル  
  Windows Update CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  デバイスが Windows 更新プログラムを受信するチャネル (ブランチ) を設定します。 異なるチャネルでは、更新プログラムが配信される前に異なる延期期間を使用できます。  

  たとえば、"*半期チャネル*" では 6 か月間延期されます。 この設定の本文で延期を追加せずにこのチャネルを使用する場合、デバイスでは更新プログラムがそのリリースから 6 か月後にインストールされることを意味します。  

  サポートされる更新チャネル:  

  - 半期チャネル  
  - 半期チャネル (対象指定)  
  - Windows Insider - 高速  
  - Windows Insider - 低速  
  - Windows Insider のリリース  

  Intune チャネルを選択した場合、Intune では、Insider ビルドが動作するように Windows Update 設定 [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) が自動的に構成されます。  


  > [!IMPORTANT]  
  > Windows バージョン 1903 以降では、"*半期チャネル (対象指定)* " (SAC-T) の使用が廃止されました。 この変更により、SAC-T は "*半期チャネル*" とマージされます。 この変更およびそれが Windows Update for Business に与える影響について詳しくは、Windows IT Pro ブログの投稿「[Windows Update for Business and the retirement of SAC-T (Windows Update for Business と、SAC T の廃止)](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523)」をご覧ください。  
 
- **Microsoft 製品の更新**  
  **既定値**: 許可  
  Windows Update CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **許可**-[*許可*] を選択して、Microsoft Update からアプリの更新プログラムをスキャンします。  
  - **ブロック**選択ブロックを使用して、アプリの更新プログラムのスキャンを防止します。  

- **Windows ドライバー**  
  **既定値**: 許可  
  Windows Update CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **許可**-[更新中に Windows Update ドライバを含める] を*選択します*。  
  - **ブロック**を選択して、ドライバーのスキャンを防止します。  

- **品質更新プログラムの延期期間 (日数)**  
  **既定値**: 0  
  Windows Update CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  品質更新プログラムを延期する日数を 0 から 30 で指定します。 この期間は、選択したサービス チャネルの一部である延期期間に加算されます。 延期期間は、ポリシーがデバイスによって受信されたときに開始します。  

  品質更新プログラムは通常、既存の Windows 機能の修正プログラムや機能強化です。  

- **機能更新プログラムの延期期間 (日数)**  
  **既定値**: 0  
  Windows Update CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  機能更新プログラムを延期する日数を指定します。 この期間は、選択したサービス チャネルの一部である延期期間に加算されます。 延期期間は、ポリシーがデバイスによって受信されたときに開始します。  

  サポートされている延期期間:  

  - *Windows バージョン1709以降*-0 ~ 365 日  
  - "*Windows バージョン 1703*" - 0 日から 180 日まで  

  機能更新プログラムは、通常、Windows の新しい機能です。  

- **機能更新プログラムのアンインストール期間 (2 から 60 日間) の設定**  
  **既定値**: 10  
  Windows Update CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  経過後に機能更新プログラムをアンインストールできなくなる時間を構成します。  

  この期間を過ぎると、以前の更新プログラムがデバイスから削除され、アンインストールして以前の更新バージョンに戻すことができなくなります。  

  たとえば、機能更新プログラムのアンインストール期間が 20 日の更新プログラム リングについて考えます。 25 日後に、最新の機能更新プログラムをロールバックすることを決定し、[アンインストール] オプションを使用します。  20 日より前に機能更新プログラムをインストールしたデバイスでは、これらをアンインストールできません。メンテナンスの一環として必要なファイルが削除されているからです。 一方、最大 19 日前に機能更新プログラムをインストールしたデバイスでは、20 日のアンインストール期間が経過する前に正常にチェックインしてアンインストール コマンドを受信した場合には、更新プログラムをアンインストールできます。  

## <a name="user-experience-settings"></a>ユーザー エクスペリエンスの設定  

ユーザー エクスペリエンスの設定は、デバイスの再起動とアラームに関するエンド ユーザー エクスペリエンスを制御します。 各設定の動作について詳しくは、Windows Update の CSP に関するドキュメントをご覧ください。  

- **自動更新動作**  
  **既定**: メンテナンス時刻に自動的にインストールする  
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  自動更新プログラムをインストールする方法、また、必要に応じてデバイスを再起動する条件を選択します。  

  サポートされているオプション:  

  - **[ダウンロードを通知する]** - 更新プログラムをダウンロードする前にユーザーに通知します。 ユーザーは、更新プログラムをダウンロードしてインストールすることを選択します。  

  - **[メンテナンス時に自動的にインストールする]** - 更新プログラムを自動的にダウンロードし、デバイスが使用中でもバッテリで実行中でもない自動メンテナンス中にインストールします。 再起動が必要な場合、ユーザーに再起動を求めるメッセージが最大で 7 日間表示され、その後強制的に再起動されます。  

    このオプションでは、更新プログラムをインストールした後、デバイスを自動的に再起動できます。 **[アクティブ時間]** 設定を使用して、自動再起動がブロックされる期間を定義します。  

    - **[アクティブ時間の開始]** - 更新プログラムのインストールによる再起動を抑制する開始時刻を指定します。  
      **既定値**: 午前 8 時  
      Windows Update CSP:[更新/アクティブ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **[アクティブ時間の終了]** - 更新プログラムのインストールによる再起動を抑制する終了時刻を指定します。  
      **既定値**: 午後 5 時  
      Windows Update CSP:[更新/アクティブ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **[メンテナンス時に自動的にインストールおよび再起動する]** - 更新プログラムを自動的にダウンロードし、デバイスが使用中でもバッテリで実行中でもない自動メンテナンス中にインストールします。 再起動が必要な場合、デバイスは使用されていないときに再起動されます (これは、アンマネージド デバイスの既定値です)。  

    このオプションでは、更新プログラムをインストールした後、デバイスを自動的に再起動できます。 **[アクティブ時間]** 設定の使用については Windows Update 設定で説明されていませんが、自動再起動がブロックされる期間を定義するために Intune によって使用されます。  

    - **[アクティブ時間の開始]** - 更新プログラムのインストールによる再起動を抑制する開始時刻を指定します。  
      **既定値**: 午前 8 時  
      Windows Update CSP:[更新/アクティブ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **[アクティブ時間の終了]** - 更新プログラムのインストールによる再起動を抑制する終了時刻を指定します。  
      **既定値**: 午後 5 時  
      Windows Update CSP:[更新/アクティブ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **[スケジュールした時刻に自動的にインストールおよび再起動する]** - インストールの日付と時刻を指定します。 指定しない場合、インストールは毎日午前 3 時に実行され、その後に再起動まで 15 分のカウントダウンが始まります。 ログオン中のユーザーは、カウントダウンと再起動を遅延させることができます。   
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    このオプションでは、追加の設定がサポートされます。  

    - **[自動動作の頻度]** - この設定を使用して、週、日、時刻など、更新プログラムをインストールするタイミングをスケジュールします。  
      **既定値**: 毎週

    - **[スケジュールされたインストール日]** - 更新プログラムをインストールする曜日を指定します。  
      **既定値**: 任意の日  

    - **[スケジュールされたインストール時刻]** - 更新プログラムをインストールする時刻を指定します。  
      **既定値**: 午前 3 時  

  - **[エンド ユーザーによる制御なしで自動的にインストールおよび再起動する]** - 更新プログラムを自動的にダウンロードし、デバイスが使用中でもバッテリで動作中でもない自動メンテナンス中にインストールします。 再起動が必要な場合、デバイスは使用されていないときに再起動されます このオプションでは、エンドユーザーのコントロール ウィンドウが読み取り専用に設定されます。  

  - **[既定にリセット]** - 2018 年 10 月更新以降を実行している Windows 10 コンピューター上で元の自動更新設定を復元します。  


- **再起動チェック**  
  **既定値**: 許可  
  Windows Update CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  デバイスの再起動時にこれらのチェックをスキップするには、 **[スキップ]** を選択します。 
  
  この設定の結果は、デバイスの Windows バージョンによって異なります:  
 
  - "*Windows バージョン 1703 以前*" - デバイスの再起動時には、アクティブなユーザー、バッテリ レベル、実行中のゲームなどについて、いくつかのチェックが実行されます。  
  
  - "*Windows バージョン 1709 以降*" - アクティブ時間中は、更新プログラムに対するスキャン、ダウンロード、インストール、再起動のプロセスが実行されません。 アクティブ時間後は、更新プログラム プロセスが実行され、バッテリ チェックと電源チェックに合格していれば、デバイスのスリープ状態からの復帰、ダウンロード、インストール、再起動を実行できます。 

- **ユーザーによる Windows Update の一時停止をブロックする**  
  **既定値**: 許可  
  Windows Update CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **許可**-デバイスユーザーが更新プログラムのインストールを一時停止できるようにします。  
  - **ブロック**-デバイスユーザーが更新プログラムのインストールを一時停止できないようにします。  

- **ユーザーによる Windows Update のスキャンをブロックする**  
  **既定値**: 許可  
  Windows Update CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **許可**-デバイスユーザーが Windows Update スキャンを使用して、更新プログラムを検索してダウンロードし、機能をインストールできるようにします。
  - **ブロック**-デバイスユーザーが Windows Update スキャンにアクセスしたり、更新プログラムをダウンロードしたり、機能をインストールしたりするのを防ぎます。  

- **作業時間外に再起動するにはユーザーの承認が必要です**  
  **既定値**: 未構成  
  Windows Update CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **未構成**  
  - **[必須]** - 作業時間外のデバイスの再起動の承認をユーザーに要求します。  
   
- **無視できるアラームを使用して必要な自動再起動の前にユーザーに通知する (時間)**  
  **既定値**: 4  
  Windows Update CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  自動再起動の前にその再起動について無視できる通知をデバイスのユーザーに表示する時間の長さを指定します。 **2**、**4**、**8**、**12**、または **24** 時間の値がサポートされています。  
  
  既定値をオフにすると、この設定は構成され*なく*なります。  

- **固定アラームを使用して必要な自動再起動の前にユーザーに通知する (分)**  
  **既定値**: 15  
  Windows Update CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  自動再起動の前にその再起動について無視できない警告をデバイスのユーザーに表示する時間の長さを指定します。 **15**、**30** または **60** 分の値がサポートされています。  

  既定値をオフにすると、この設定は構成され*なく*なります。  

- **Update 通知レベルを変更する**  
  **既定値**: 既定の Windows Update 通知を使用します  
  Windows Update CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  ユーザーに表示される Windows Update 通知レベルを指定します。 この設定では、更新プログラムのダウンロードとインストールの方法とタイミングを管理することはできません。  

  サポートされているオプション:
  - **未構成**
  - **既定の Windows Update 通知を使用します**
  - **再起動警告を除くすべての通知をオフにする**
  - **再起動警告を含む、すべての通知をオフにする**  

- **期限の設定を使用する**  
  **既定値**: 未構成  
 
  ユーザーが期限の設定を使用できるようにします。  

  - **未構成**
  - **許可**

  [*許可*] に設定すると、期限に対して次の設定を構成できます。

  - **機能更新プログラムの期限**  
    **既定値**: *[未構成]*  
    Windows Update CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    機能更新プログラムがデバイスに自動的にインストールされるまでのユーザーの日数を指定します (2-30)。

  - **品質更新プログラムの期限**  
    **既定値**: *[未構成]*  
    Windows Update CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    品質更新プログラムがデバイスに自動的にインストールされるまでのユーザーの日数を指定します (2-30)。

  - **猶予期間**  
    **既定**: CSP: [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod) Windows Update 構成され*ていません*。

    再起動が自動的に行われるまでの最小日数を指定します (2-7)。

  - **期限前の自動再起動**  
    **既定値**: YES Windows Update CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    期限前にデバイスを自動的に再起動するかどうかを指定します。
    - **あり**
    - **いいえ**

### <a name="delivery-optimization-download-mode"></a>配信の最適化ダウンロード モード  

配信の最適化は、ソフトウェアの更新プログラムで Windows 10 更新リングの一部として構成されなくなりました。 現在、配信の最適化はデバイスの構成で設定されます。 ただし、以前の構成は引き続きコンソールで使用できます。 これらの以前の構成は、 *[未構成]* へと編集することで削除できますが、それ以外の変更を行うことはできません。 

新しいポリシーと既存のポリシーの間の競合を避けるには、[既存の更新リングから配信の最適化へ移動する](../configuration/delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization)方法に関するページを参照し、設定を配信の最適化プロファイルに移動します。
