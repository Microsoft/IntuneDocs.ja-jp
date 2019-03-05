---
title: Microsoft Intune での Windows for Business Update 設定 - Azure | Microsoft Docs
description: Intune を使用して展開できる Windows 10 デバイスの WUfB 設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28e7109a82a5c083b4be26bc823bb0e06d97a7ca
ms.sourcegitcommit: da9ee02de327f202b00be44c79bf7abd35b9929b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57334988"
---
# <a name="windows-update-settings-for-intune"></a>Intune での Windows Update の設定  

Microsoft Intune を使用して[構成および管理](windows-update-for-business-configure.md)できる Windows 10 更新プログラムの設定を表示します。  

Intune 内で Windows 10 更新プログラム リングの設定を構成する場合、Windows Update の設定を構成することになります。  Windows Update の設定に Windows 10 バージョンの依存関係がある場合、バージョンの依存関係は設定の詳細に記載されています。  

## <a name="update-settings"></a>Update の設定  

Update の設定では、デバイスによってダウンロードされるものとそのタイミングを制御します。 各設定の動作について詳しくは、Windows リファレンス ドキュメントをご覧ください。  

### <a name="servicing-channel"></a>サービス チャネル  

- **既定値**:半期チャネル (対象指定)  
- **Windows リファレンス ドキュメント**:[Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
デバイスが Windows 更新プログラムを受信するチャネル (ブランチ) を設定します。 異なるチャネルでは、更新プログラムが配信される前に異なる延期期間を使用できます。  

たとえば、"*半期チャネル*" では 6 か月間延期されます。 これは、この設定の本文で延期を追加せずにこのチャネルを使用する場合、デバイスでは更新プログラムがそのリリースから 6 か月後にインストールされることを意味します。  

サポートされる更新チャネル:  

- 半期チャネル  
- 半期チャネル (対象指定)  
- Windows Insider - 高速  
- Windows Insider - 低速  
- Windows Insider のリリース  

Intune チャネルを選択した場合、Intune では、Insider ビルドが動作するように Windows Update 設定 [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) が自動的に構成されます。  


> [!IMPORTANT]  
> Windows バージョン 1903 以降では、"*半期チャネル (対象指定)*" (SAC-T) の使用が廃止されました。 この変更により、SAC-T は "*半期チャネル*" とマージされます。 この変更およびそれが Windows Update for Business に与える影響について詳しくは、Windows IT Pro ブログの投稿「[Windows Update for Business and the retirement of SAC-T (Windows Update for Business と、SAC T の廃止)](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523)」をご覧ください。
 


### <a name="microsoft-product-updates"></a>Microsoft 製品の更新プログラム  

- **既定値**:Allow
- **Windows リファレンス ドキュメント**:[Update/AllowMUUpdateService](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Microsoft Update のアプリの更新プログラムをスキャンするには *[Allow]* を選択します。    

### <a name="windows-drivers"></a>Windows ドライバー  

- **既定値**:Allow
- **Windows リファレンス ドキュメント**:[Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

更新中に Windows Update ドライバーを含めるには *[Allow]* を選択します

### <a name="quality-update-deferral-period-days"></a>品質更新プログラムの延期期間 (日数)  

- **既定値**:0  
- **Windows リファレンス ドキュメント**:[Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

品質更新プログラムを延期する日数を 0 から 30 で指定します。 この期間は、選択したサービス チャネルの一部である延期期間に加算されます。 延期期間は、ポリシーがデバイスによって受信されたときに開始します。  

品質更新プログラムは通常、既存の Windows 機能の修正プログラムや機能強化です。  

### <a name="feature-update-deferral-period-days"></a>機能更新プログラムの延期期間 (日数)  

- **既定値**:0  
- **Windows リファレンス ドキュメント**:[Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

機能更新プログラムを延期する日数を指定します。 この期間は、選択したサービス チャネルの一部である延期期間に加算されます。 延期期間は、ポリシーがデバイスによって受信されたときに開始します。  
サポートされている延期期間:  

- *Windows バージョン 1709 以降*:0 日から 365 日  
- *Windows バージョン 1703*:0 日から 180 日  

機能更新プログラムは、通常、Windows の新しい機能です。  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>機能更新プログラムのアンインストール期間 (2 から 60 日間) の設定  

- **既定値**:10  
- **Windows リファレンス ドキュメント**:[Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

経過後に機能更新プログラムをアンインストールできなくなる時間を構成します。  

この期間を過ぎると、以前の更新プログラムがデバイスから削除され、アンインストールして以前の更新バージョンに戻すことができなくなります。  

たとえば、機能更新プログラムのアンインストール期間が 20 日の更新プログラム リングについて考えます。 25 日後に、最新の機能更新プログラムをロールバックすることを決定し、[アンインストール] オプションを使用します。  20 日より前に機能更新プログラムをインストールしたデバイスでは、これらをアンインストールできません。メンテナンスの一環として必要なファイルが削除されているからです。 一方、最大 19 日前に機能更新プログラムをインストールしたデバイスでは、20 日のアンインストール期間が経過する前に正常にチェックインしてアンインストール コマンドを受信した場合に更新プログラムをアンインストールできます。  


## <a name="user-experience-settings"></a>ユーザー エクスペリエンスの設定  

ユーザー エクスペリエンスの設定は、デバイスの再起動とアラームに関するエンド ユーザー エクスペリエンスを制御します。 各設定の動作について詳しくは、Windows リファレンス ドキュメントをご覧ください。  

### <a name="automatic-update-behavior"></a>自動更新の動作  

- **既定値**:スケジュールした時刻に自動的にインストールおよび再起動する  
- **Windows リファレンス ドキュメント**:[Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

自動更新プログラムをインストールする方法、また、必要に応じてデバイスを再起動するタイミングを選択します。  

サポートされている次のオプションの完全な開示については、Windows リファレンス ドキュメントをご覧ください。  

- **[ダウンロードを通知する]** - 更新プログラムをダウンロードする前にユーザーに通知します。 ユーザーは、更新プログラムをダウンロードしてインストールすることを選択します。  

- **[メンテナンス時に自動的にインストールする]** - 更新プログラムを自動的にダウンロードし、デバイスが使用中でもバッテリで実行中でもない自動メンテナンス中にインストールします。 再起動が必要な場合、ユーザーに再起動を求めるメッセージが最大で 7 日間表示され、その後強制的に再起動されます。  

  このオプションでは、更新プログラムをインストールした後、デバイスを自動的に再起動できます。 **[アクティブ時間]** 設定を使用して、自動再起動がブロックされる期間を定義します。  

  - **アクティブ時間の開始**:更新プログラムのインストールによる再起動を抑制する開始時刻を指定します。  
    **Windows リファレンス ドキュメント**:[Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **既定値**:午前 8 時  
  
  - **アクティブ時間の終了**:更新プログラムのインストールによる再起動を抑制する終了時刻を指定します。  
    **Windows リファレンス ドキュメント**:[Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **既定値**:午後 5 時  

- **[メンテナンス時に自動的にインストールおよび再起動する]** - 更新プログラムを自動的にダウンロードし、デバイスが使用中でもバッテリで実行中でもない自動メンテナンス中にインストールします。 再起動が必要な場合、デバイスは使用されていないときに再起動されます  (これは、アンマネージド デバイスの既定値です)。  

  このオプションでは、更新プログラムをインストールした後、デバイスを自動的に再起動できます。 **[アクティブ時間]** 設定の使用については Windows Update 設定で説明されていませんが、自動再起動がブロックされる期間を定義するために Intune によって使用されます。  

  - **アクティブ時間の開始**:更新プログラムのインストールによる再起動を抑制する開始時刻を指定します。  
    **Windows リファレンス ドキュメント**:[Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **既定値**:午前 8 時  

  - **アクティブ時間の終了**:更新プログラムのインストールによる再起動を抑制する終了時刻を指定します。  
    **Windows リファレンス ドキュメント**:[Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **既定値**:午後 5 時  

- **[スケジュールした時刻に自動的にインストールおよび再起動する]** - インストールの日付と時刻を指定します。 指定しない場合、インストールは毎日午前 3 時に実行され、その後に再起動まで 15 分のカウントダウンが始まります。 ログオン中のユーザーは、カウントダウンと再起動を遅延させることができます。  
  
  このオプションでは、追加の設定がサポートされます。  
  **Windows リファレンス ドキュメント**:[Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **自動動作の頻度**:この設定を使用して、週、日、時刻など、更新プログラムをインストールするタイミングをスケジュールします。  
    **既定値**:毎週

  - **スケジュールされたインストール日**:更新プログラムをインストールする曜日を指定します。  
    **既定値**:任意の日  

  - **スケジュールされたインストール時刻**:更新プログラムをインストールする時刻を指定します。  
    **既定値**:午前 3 時  

- **[エンド ユーザーによる制御なしで自動的にインストールおよび再起動する]** - 更新プログラムを自動的にダウンロードし、デバイスが使用中でもバッテリで実行中でもない自動メンテナンス中にインストールします。 再起動が必要な場合、デバイスは使用されていないときに再起動されます  このオプションでは、エンドユーザーのコントロール ウィンドウが読み取り専用に設定されます。  

- **[既定にリセット]** - 2018 年 10 月更新以降を実行している Windows 10 コンピューター上で元の自動更新設定を復元します。  


### <a name="restart-checks"></a>再起動チェック  

- **既定値**:Allow  
- **Windows リファレンス ドキュメント**:[Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

この設定の結果は、デバイスの Windows バージョンによって異なります:  

- Windows バージョン 1703 以前:デバイスの再起動時には、アクティブなユーザー、バッテリ レベル、実行中のゲームなどについて、いくつかのチェックが実行されます。 デバイスの再起動時にこれらのチェックをスキップするには、**[スキップ]** を選択します。  
- Windows バージョン 1709 以降:アクティブ時間中は、更新プログラムに対してスキャン、ダウンロード、インストール、再起動のプロセスは実行されません。 アクティブ時間後は、更新プログラム プロセスが実行され、バッテリ チェックと電源チェックに合格していれば、デバイスのスリープ状態からの復帰、ダウンロード、インストール、再起動を実行できます。 詳細については、「[Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)」を参照してください。  

### <a name="block-user-from-pausing-windows-updates"></a>ユーザーによる Windows Update の一時停止をブロックする  

- **既定値**:Allow  
- **Windows リファレンス ドキュメント**:[Update/SetDisablePauseUXAccess](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

デバイスのユーザーが更新プログラムのインストールを一時停止することを許可またはブロックします。  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>作業時間外に再起動するにはユーザーの承認が必要です  

- **既定値**:未構成  
- **Windows リファレンス ドキュメント**:[Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
作業時間外のデバイスの再起動の承認をユーザーに要求するには *[必須]* を選択します。  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>無視できるアラームを使用して必要な自動再起動の前にユーザーに通知する (時間)  

- **既定値**:*これは既定では構成されず、ユーザーにアラームは表示されません*。  
- **Windows リファレンス ドキュメント**:[Update/ScheduleRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

自動再起動の前にその再起動について無視できる通知をデバイスのユーザーに表示する時間の長さを指定します。 **2**、**4**、**8**、**12**、または **24** 時間の値がサポートされています。  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>固定アラームを使用して必要な自動再起動の前にユーザーに通知する (分)  

- **既定値**:*これは既定では構成されず、ユーザーにアラームは表示されません*。  
- **Windows リファレンス ドキュメント**:[Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

自動再起動の前にその再起動について無視できない警告をデバイスのユーザーに表示する時間の長さを指定します。 **15**、**30** または **60** 分の値がサポートされています。  
 
### <a name="allow-user-to-restart-engaged-restart"></a>ユーザーに再起動を許可する (再起動猶予期間)  

- **既定値**:未構成  
- **Windows リファレンス ドキュメント**:*該当なし*  
- **Windows バージョン**:Windows 10 バージョン 1803 以降でサポートされます  

  > [!NOTE]  
  > Windows 10 バージョン 1809 では、機能と品質の更新プログラムに個別の設定を適用できるようにする追加の再起動猶予期間設定が導入されています。 ただし、Intune によって管理される設定は、異なる更新の種類に個別には適用されません。 代わりに、Intune では、機能と品質両方の更新プログラムに同じ値が適用されます。  

**[必須]** に設定する場合、Windows 10 更新プログラムに対して再起動猶予期間オプションの使用を有効にします。 これらのオプションにより、デバイスのユーザーは、再起動が必要な更新プログラムのインストール後にデバイスを再起動するタイミングを管理できます。  

このオプションについて詳しくは、更新の展開に関する Windows 10 のドキュメントで「[再起動猶予期間](https://docs.microsoft.com/en-us/windows/deployment/update/waas-restart#engaged-restart)」をご覧ください。  

次の設定は、再起動猶予期間アクションが発生するタイミングの制御に使用されます。  

- **自動再起動後にユーザーを再起動猶予期間に切り替え (日数)**  
  - **既定値**:既定では、これは構成されませんが、**2** から **30** までの値がサポートされます。  
  - **Windows リファレンス ドキュメント**:[Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  更新プログラムのインストール後、デバイスが再起動猶予期間の動作に入るまでの時間の長さを指定します。 構成された日数後、ユーザーはデバイスの再起動を求めるメッセージを受け取ります。  

- **再起動猶予期間リマインダーの一時停止 (日数)**  
  - **既定値**:既定では、これは構成されませんが、**1** から **3** までの値がサポートされます。  
  - **Windows リファレンス ドキュメント**:[Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  再起動を求めるメッセージを一時停止できる時間の長さを指定します。  一時停止期間の後、再起動を求めるメッセージが再び表示されます。 ユーザーは、インストールの期限に達するまで、リマインダーの一時停止を続けることができます。  

- **保留中の再起動の期限を設定する (日数)**  
  - **既定値**:既定では、これは構成されませんが、**2** から **30** までの値がサポートされます。  
  - **Windows リファレンス ドキュメント**:[Update/EngagedRestartDeadline](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  再起動猶予期間の動作が開始した後、必要な再起動がデバイスによって強制的に実行される前に待機する最大日数を指定します。 この再起動により、ユーザーは作業内容の保存を求められます

### <a name="delivery-optimization-download-mode"></a>配信の最適化ダウンロード モード  

- **既定値**:適用できません
- **Windows リファレンス ドキュメント**:*該当なし*

配信の最適化は、ソフトウェアの更新プログラムで Windows 10 更新リングの一部として構成されなくなりました。 現在、配信の最適化はデバイスの構成で設定されます。 ただし、以前の構成は引き続きコンソールで使用できます。 これらの以前の構成は、*[未構成]* へと編集することで削除できますが、それ以外の変更を行うことはできません。 

新しいポリシーと既存のポリシーの間の競合を避けるには、[既存の更新リングから配信の最適化へ移動する](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization)方法に関するページを参照し、設定を配信の最適化プロファイルに移動します。


