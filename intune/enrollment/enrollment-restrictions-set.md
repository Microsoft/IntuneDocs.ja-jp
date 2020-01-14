---
title: Microsoft Intune で登録制限を設定する
titleSuffix: ''
description: Intune でプラットフォームごとに登録を制限し、デバイス登録の上限数を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4246dab0cf22053d76fdd50f99de53e827332a23
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547820"
---
# <a name="set-enrollment-restrictions"></a>登録制限を設定する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

ユーザーは Intune 管理者として、Intune での管理に登録できるデバイスについて、以下を定義する登録制限を作成して管理することができます。
- デバイスの数。
- オペレーティング システムとバージョン。

制限を複数作成して、さまざまなユーザー グループに適用することができます。 さまざまな制限を作成した場合は、[優先度](#change-enrollment-restriction-priority)を設定することができます。

>[!NOTE]
>登録の制限はセキュリティ機能ではありません。 侵害されたデバイスでは特徴が正しく示されない可能性があります。 これらの制限は、悪意のないユーザーにとって最善の防御策となります。

具体的に作成できる登録の制限には、次のようなものがあります。

- 登録されるデバイスの最大数。
- 登録できるデバイスのプラットフォーム:
  - Android デバイス管理者
  - Android Enterprise 仕事用プロファイル
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- iOS、Android、Android デバイス管理者、Android Enterprise 仕事用プロファイル、Windows、および Windows Mobile プラットフォームのオペレーティング システムのバージョン (使用できる Windows のバージョンは 10 のみです。 Windows 8.1 が許可される場合は、空白のままにしておきます)。
  - 最小バージョン。
  - 最大バージョン。
- [個人所有デバイス](device-enrollment.md#bring-your-own-device)を制限します (iOS、Android デバイス管理者、Android Enterprise 仕事用プロファイル、macOS、Windows、および Windows Mobile のみ)。

## <a name="default-restrictions"></a>既定の制限

デバイスの種類とデバイス数の両方の登録制限には、既定の制限が提供されています。 既定の制限のオプションは変更することができます。 既定の制限は、すべてのユーザー登録とユーザーなし登録に適用されます。 このような既定の制限をオーバーライドするには、優先度の高い新しい制限を作成します。

## <a name="create-a-device-type-restriction"></a>デバイスの種類の制限を作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、 **[デバイス]**  >  **[登録制限]**  >  **[制限の作成]**  >  **[デバイスの種類の制限]** の順に選択します。
2. **[基本]** ページで、制限の **[名前]** を入力します。 **[説明]** の入力は省略できます。
3. **[次へ]** を選択して、 **[プラットフォームの設定]** ページに移動します。
4. **[プラットフォーム]** で、この制限を許可するプラットフォームに対して **[許可]** を選択します。
    ![プラットフォームの設定を選択する画面のキャプチャ](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. **[バージョン]** で、許可されるプラットフォームでサポートされる最小バージョンと最大バージョンを選択します。 バージョン制限は、ポータル サイトを使用して登録されるデバイスにのみ適用されます。
     サポートされるバージョン形式:
    - Android デバイス管理者と Android Enterprise 仕事用プロファイルでは、major.minor.rev.build がサポートされます。
    - iOS では major.minor.rev がサポートされます。オペレーティング システムのバージョンは、Device Enrollment Program、Apple School Manager、または Apple Configurator アプリを使用して登録する Apple デバイスには適用されません。
    - Windows は、Windows 10 の場合にのみ major.minor.build.rev をサポートします。
    
    > [!IMPORTANT]
    > Android Enterprise (仕事用プロファイル) プラットフォームと Android デバイス管理者プラットフォームには、次のような特徴があります。
    > - 両方のプラットフォームが同じグループに対して許可されている場合、ユーザーは、自分のデバイスで仕事用プロファイルがサポートされていればそれに登録され、そうでなければ、DA として登録されます。 
    > - 両方のプラットフォームがグループに対して許可され、特定の重複しないバージョンに合わせて調整されている場合、ユーザーは自分の OS バージョン用に定義された登録フローを受け取ります。 
    > - 両方のプラットフォームは許可されているが、同じバージョンに対してブロックされている場合、ブロックされたバージョンを使用するデバイス上のユーザーは、Android デバイス管理者登録フローに移動し、登録がブロックされて、サインアウトするように求められます。 
    >
    > 適切な前提条件が Android 登録内で完了していない限り、仕事用プロファイルもデバイス管理者の登録も機能しないことに注意してください。 
    
   > [!Note]
   > Windows 10 では登録時にリビジョン番号が提供されないため、たとえば 10.0.17134.100 と入力し、デバイスが 10.0.17134.174 の場合、登録中にブロックされます。

6. **[個人所有]** で、個人所有デバイスとして許可するプラットフォームに対して **[許可]** を選択します。
7. **[次へ]** を選択して、 **[割り当て]** ページに移動します。
8. **[含めるグループを選択]** を選択した後、検索ボックスを使用して、この制限に含めるグループを検索します。 制限が適用されるのは、制限が割り当てられているグループのみです。 少なくとも 1 つのグループに割り当てていない限り、制限は何も影響しません。 次に **[選択]** を選択します。 
    ![プラットフォームの設定を選択する画面のキャプチャ](./media/enrollment-restrictions-set/select-groups.png)
9. **[次へ]** を選択して、 **[確認と作成]** ページへ移動します。
10. **[作成]** を選択して、制限を作成します。
11. 既定値の制限のすぐ上の優先度を持つ新しい制限が作成されます。 [優先度は変更](#change-enrollment-restriction-priority)することができます。


## <a name="create-a-device-limit-restriction"></a>デバイスの上限数の制限を作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、 **[デバイス]**  >  **[登録制限]**  >  **[制限の作成]**  >  **[デバイスの上限数の制限]** の順に選択します。
2. **[基本]** ページで、制限の **[名前]** を入力します。 **[説明]** の入力は省略できます。
3. **[次へ]** を選択して、 **[デバイスの上限数]** ページにアクセスします。
4. **[デバイスの上限数]** で、ユーザーが登録できるデバイスの最大数を選択します。
    ![デバイスの上限を選択する画面のキャプチャ](./media/enrollment-restrictions-set/choose-device-limit.png)
5. **[次へ]** を選択して、 **[割り当て]** ページに移動します。
6. **[含めるグループを選択]** を選択した後、検索ボックスを使用して、この制限に含めるグループを検索します。 制限が適用されるのは、制限が割り当てられているグループのみです。 少なくとも 1 つのグループに割り当てていない限り、制限は何も影響しません。 次に **[選択]** を選択します。 
    ![グループを選択する画面のキャプチャ](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. **[次へ]** を選択して、 **[確認と作成]** ページへ移動します。
8. **[作成]** を選択して、制限を作成します。
9. 既定値の制限のすぐ上の優先度を持つ新しい制限が作成されます。 [優先度は変更](#change-enrollment-restriction-priority)することができます。

BYOD の登録中にユーザーがデバイス登録の上限に達すると、そのことを伝える通知が表示されます。 たとえば、iOS の場合:

![iOS のデバイス制限通知](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> デバイス数の制限は、次の Windows 登録の種類に適用されません。
> - 共同管理登録
> - GPO の登録
> - Azure Active Directory 参加済み登録
> - Azure Active Directory 参加済み一括登録
> - Autopilot 登録
> - デバイス登録マネージャー登録
>
> これらの登録の種類は共有デバイス シナリオと見なされるため、デバイスの上限数の制限は適用されません。
> これらの登録の種類のハード制限を [Azure Active Directory に](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings)設定できます。


## <a name="change-enrollment-restrictions"></a>登録制限を変更する

登録制限に対する設定は、以下の手順で変更できます。 これらの制限は、既に登録されているデバイスには適用されません。 [Intune PC エージェント](../fundamentals/manage-windows-pcs-with-microsoft-intune.md)で登録されているデバイスはこの機能でブロックできません。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインし、 **[デバイス]**  >  **[登録制限]** の順に選択し、変更する制限を選択してから **[プロパティ]** を選択します。
2. 変更する設定の横にある **[編集]** を選択します。
3. **[編集]** ページで、必要な変更を行い、 **[レビューと保存]** ページに進み、 **[保存]** を選択します。


## <a name="blocking-personal-android-devices"></a>個人用 Android デバイスのブロック
- 個人所有の Android デバイス管理者デバイスの登録をブロックした場合でも、個人所有の Android Enterprise 仕事用プロファイル デバイスは登録できます。
- 既定では、Android Enterprise 仕事用プロファイル デバイス設定は Android デバイス管理者デバイスの設定と同じです。 Android Enterprise 仕事用プロファイルまたは Android デバイス管理者の設定を変更した後は、そうではなくなります。
- 個人の Android Enterprise 仕事用プロファイルの登録をブロックした場合、会社所有の Android デバイスのみを Android Enterprise 仕事用プロファイルとして登録できます。

## <a name="blocking-personal-windows-devices"></a>個人用 Windows デバイスのブロック
個人所有の Windows デバイスの登録をブロックした場合、Intune では、新しい Windows 登録要求がすべて会社の登録として承認されていることが確認されます。 無許可の登録はブロックされます。

次の方法は、Windows の会社登録として認証されたものと見なされます。
- 登録ユーザーは[デバイス登録マネージャー アカウント]( device-enrollment-manager-enroll.md)を使用しています。
- デバイスは [Windows Autopilot](enrollment-autopilot.md) 経由で登録されます。
- デバイスは、Windows Autopilot に登録されますが、Windows 設定からの MDM 登録のみオプションではありません。
- デバイスの IMEI 番号が **[デバイスの登録]**  >  **[[業務用デバイスの ID]](corporate-identifiers-add.md)** に記載されています。 (Windows Phone 8.1 ではサポートされていません。)
- デバイスが[一括プロビジョニング パッケージ](windows-bulk-enroll.md)経由で登録されます。
- デバイスが GPO または[共同管理用の Configuration Manager からの自動登録](https://docs.microsoft.com/configmgr/comanage/quickstart-paths#bkmk_path1)経由で登録されます。
 
次の登録は Intune で会社として見なされます。 しかし、Intune 管理者のデバイスごとのコントロールがないため、ブロックされます。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows セットアップ中の Azure Active Directory 参加](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows 設定からの Azure Active Directory 参加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)。
 
次の個人登録方法もブロックされます。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows 設定からの職場アカウントの追加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*。
- Windows 設定からの [MDM 登録のみ]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)オプション。

\* これらは、Autopilot に登録されている場合、ブロックされません。


## <a name="blocking-personal-ios-devices"></a>個人の iOS デバイスをブロックする
Intune の既定では、iOS デバイスは個人所有として分類されます。 企業所有に分類するには、iOS デバイスが次のいずれかの条件を満たしている必要があります。
- シリアル番号または IMEI を使用して登録されている。
- 自動デバイス登録 (旧称 Device Enrollment Program) を使用して登録されている


## <a name="change-enrollment-restriction-priority"></a>登録制限の優先度を変更する

優先度は、制限が割り当てられた複数のグループにユーザーが存在する場合に使用されます。 ユーザーは、自分が属するグループに割り当てられている最も高い優先度の制限からのみ影響を受けます。 たとえば、Joe が優先度 5 の制限に割り当てられたグループ A に属しており、優先度 2 の制限に割り当てられたグループ B にも属しているとします。 Joe は優先度 2 の制限にのみ影響を受けます。

制限を作成すると、リストの既定の制限のすぐ上に追加されます。

デバイスの登録には、デバイスの種類の制限とデバイス数の制限の両方に対する既定の制限が含まれます。 これら 2 つの制限は、より高い優先度の制限でオーバーライドされない限り、すべてのユーザーに適用されます。

既定以外の制限の優先度は、変更することができます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択し、**Intune** を検索して **[Intune]** を選択します。
3. **[デバイスの登録]**  >  **[登録の制限]** を選択します。
4. 優先度リスト内の制限にマウス ポインタを移動させます。
5. 3 つの縦向きドットを使用して、リスト内の目的の位置に優先度をドラッグします。
