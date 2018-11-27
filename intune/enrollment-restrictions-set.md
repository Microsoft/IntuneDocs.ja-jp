---
title: Microsoft Intune で登録制限を設定する
titlesuffix: ''
description: Intune でプラットフォームごとに登録を制限し、デバイス登録の上限数を設定します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d9a7ad5d77f0c085fc1e91b6991657e6b848b3f3
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187839"
---
# <a name="set-enrollment-restrictions"></a>登録制限を設定する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

ユーザーは Intune 管理者として、Intune での管理に登録できるデバイスの数と種類を定義した登録の制限を作成して管理することができます。 制限を複数作成して、さまざまなユーザー グループに適用することができます。 さまざまな制限を作成した場合は、[優先度](#change-enrollment-restriction-priority)を設定することができます。

>[!NOTE]
>登録の制限はセキュリティ機能ではありません。 侵害されたデバイスでは特徴が正しく示されない可能性があります。 これらの制限は、悪意のないユーザーにとって最善の防御策となります。

具体的に作成できる登録の制限には、次のようなものがあります。

- 登録されるデバイスの最大数。
- 登録できるデバイスのプラットフォーム:
  - Android
  - Android の仕事用プロファイル
  - iOS
  - macOS
  - Windows
- iOS、Android、Android 仕事用プロファイル、および Windows のプラットフォームのオペレーティング システム バージョン。 (使用できる Windows のバージョンは 10 のみです。 Windows 8.1 が許可される場合は、空白のままにしておきます)。
  - 最小バージョン。
  - 最大バージョン。
- 個人所有デバイスを制限します (iOS、Android、Android 仕事用プロファイル、macOS、Windows のみ)。

## <a name="default-restrictions"></a>既定の制限

デバイスの種類とデバイス数の両方の登録制限には、既定の制限が提供されています。 既定の制限のオプションは変更することができます。 既定の制限は、すべてのユーザー登録とユーザーなし登録に適用されます。 このような既定の制限をオーバーライドするには、優先度の高い新しい制限を作成します。

## <a name="create-a-restriction"></a>制限を作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択し、**Intune** を検索して **[Intune]** を選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. **[制限の作成]** を選択します。
5. 制限に名前付け、説明を加えます。
6. **[制限の種類]** を選択し、**[作成]** を選択します。
7. デバイス数の制限については、**[デバイスの制限]** を選択して、ユーザーが登録できるデバイスの最大数を設定します。
8. デバイスの種類の制限については、**[プラットフォーム]**、**[プラットフォーム構成]** の順に選択して、各種のプラットフォームおよびバージョンを許可またはブロックします。
9. **[割り当て]** > **[+ グループの選択]** を選択します。
10. **[グループの選択]** で、1 つ以上のグループを選択し、**[選択]** を選択します。 制限が適用されるのは、制限が割り当てられているグループのみです。 少なくとも 1 つのグループに割り当てていない限り、制限は何も影響しません。
11. **[保存]** を選択します。
12. 既定値の制限のすぐ上の優先度を持つ新しい制限が作成されます。 [優先度は変更](#change-enrollment-restriction-priority)することができます。

## <a name="set-device-type-restrictions"></a>デバイスの種類の制限を設定する

デバイスの種類の制限に対する設定は以下の手順で変更できます。 この制限は、既に登録されているデバイスには適用されません。 [Intune PC エージェント](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)で登録されているデバイスはこの機能でブロックできません。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択し、**Intune** を検索して **[Intune]** を選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. **[デバイスの種類の制限]** で、設定する制限を選択し、**[プロパティ]** > **[プラットフォームの選択]** の順に選択します。 一覧されたプラットフォームごとに、**[許可]** または **[ブロック]** を選択します。
    ![スクリーンショット。プラットフォームを許可またはブロックします。](media/enrollment-restrictions-set/platform-allow-block.png)
5. **[OK]** を選びます。
6. **[プラットフォームの構成]** を選択します。
    ![スクリーンショット。プラットフォームを構成します。](media/enrollment-restrictions-set/configure-platforms.png)
7. リストされているプラットフォームの最小および最大の **[バージョン]** を選択します。 サポートされるバージョン形式:
    - Android 仕事用プロファイルは major.minor.rev.build をサポートしています。
    - iOS では major.minor.rev がサポートされます。オペレーティング システムのバージョンは、Device Enrollment Program、Apple School Manager、または Apple Configurator アプリを使用して登録する Apple デバイスには適用されません。
    - Windows では major.minor.rev.build がサポートされます (Windows 10 の場合のみ)。
8. 一覧にあるプラットフォームごとに、**個人所有**のデバイスを**許可**するか**ブロック**するかを選択します。
9. **[OK]** を選びます。

### <a name="blocking-personal-android-devices"></a>個人用 Android デバイスのブロック
- 個人所有の Android デバイスの登録をブロックした場合でも、個人所有の Android 仕事用プロファイル デバイスは登録できます。
- 既定では、Android 仕事用プロファイル デバイス設定は Android デバイスの設定と同じになります。 Android 仕事用プロファイル設定の変更後は、同じではなくなります。
- 個人の Android 仕事用プロファイルの登録をブロックした場合、会社の Android デバイスのみを Android 仕事用プロファイルとして登録できます。

### <a name="blocking-personal-windows-devices"></a>個人用 Windows デバイスのブロック
個人所有の Windows デバイスの登録をブロックした場合、Intune では、新しい Windows 登録要求がすべて会社の登録として承認されていることが確認されます。 無許可の登録はブロックされます。

次の方法は、Windows の会社登録として認証されたものと見なされます。
 - 登録ユーザーは[デバイス登録マネージャー アカウント]( device-enrollment-manager-enroll.md)を使用しています。
- デバイスは [Windows AutoPilot](enrollment-autopilot.md) 経由で登録されます。
- デバイスは、Windows Autopilot に登録されますが、Windows 設定からの MDM 登録のみオプションではありません。
- デバイスの IMEI 番号が **[デバイスの登録]** > **[[業務用デバイスの ID]](corporate-identifiers-add.md)** に記載されています。 (Windows Phone 8.1 ではサポートされていません。)
- デバイスが[一括プロビジョニング パッケージ](windows-bulk-enroll.md)経由で登録されます。
- デバイスが[共同管理用の SCCM からの自動登録](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md)経由で登録されます。
 
次の登録は Intune で会社として見なされますが、Intune 管理者のデバイスごとのコントロールがないため、ブロックされます。
 - [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows セットアップ中の Azure Active Directory 参加](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows 設定からの Azure Active Directory 参加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)。
 
次の個人登録方法もブロックされます。
- [自動 MDM 登録](windows-enroll.md#enable-windows-10-automatic-enrollment)と [Windows 設定からの職場アカウントの追加](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*。
- Windows 設定からの [MDM 登録のみ]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)オプション。

\* これらは、Autopilot に登録されている場合、ブロックされません。

## <a name="set-device-limit-restrictions"></a>デバイス数の制限を設定する

デバイス数の制限の設定は、次の手順に従って変更できます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択し、**Intune** を検索して **[Intune]** を選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. **[デバイス数の制限]** で、設定する制限を選択します。
5. **[デバイスの制限]** を選択し、ドロップダウン リストで、ユーザーが登録できるデバイスの最大数を選択します。
    ![デバイス数の制限を示す [デバイス数の制限] ブレード](./media/device-restrictions-limit.png)
6. **[保存]** を選択します。


ユーザーがデバイス登録の上限に達すると、そのことを伝える通知が表示されます。 たとえば、iOS では次のようになります。

![iOS のデバイス制限通知](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>登録制限の優先度を変更する

優先度は、制限が割り当てられた複数のグループにユーザーが存在する場合に使用されます。 ユーザーは、自分が属するグループに割り当てられている最も高い優先度の制限からのみ影響を受けます。 たとえば、Joe が優先度 5 の制限に割り当てられたグループ A に属しており、優先度 2 の制限に割り当てられたグループ B にも属しているとします。 Joe は優先度 2 の制限にのみ影響を受けます。

制限を作成すると、リストの既定の制限のすぐ上に追加されます。

デバイスの登録には、デバイスの種類の制限とデバイス数の制限の両方に対する既定の制限が含まれます。 これら 2 つの制限は、より高い優先度の制限でオーバーライドされない限り、すべてのユーザーに適用されます。

既定以外の制限の優先度は、変更することができます。

1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択し、**Intune** を検索して **[Intune]** を選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. 優先度リスト内の制限にマウス ポインタを移動させます。
5. 3 つの縦向きドットを使用して、リスト内の目的の位置に優先度をドラッグします。
