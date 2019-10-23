---
title: Microsoft Intune での共有デバイスまたはマルチユーザー デバイスの設定 - Azure | Microsoft Docs
description: Microsoft Intune で共有されるか複数のユーザーによって使用される Windows 10 デバイスと Windows Holographic for Business デバイスを追加および使用します。 すべての設定と、Microsoft HoloLens などのデバイスでのその動作の一覧を参照してください。 デバイス構成プロファイルで、ゲスト アカウントの制御、アカウントの管理、非アクティブなアカウントの削除、ローカル ストレージへの保存の許可または禁止、電源とスリープのオプションの設定、更新プログラムをインストールするタイミングの選択、および教育環境でのデバイスの使用を行います。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8dfab31d770c012acf88eb3775313634c3c14cc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492306"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Intune を使用して共有 PC またはマルチユーザー デバイスでのアクセス、アカウント、および電源機能を制御する

複数のユーザーを持つデバイスは共有デバイスと呼ばれ、モバイル デバイス管理 (MDM) ソリューションの一般的な部分です。 Microsoft Intune を使用して、次のプラットフォームを実行している共有デバイスをカスタマイズできます。

- Windows 10 Professional 以降
- Windows 10 Enterprise 以降
- Windows Holographic for Business (HoloLens など)

たとえば、学校には、通常多くの学生によって使用されるデバイスがあります。 この設定では、学校の Intune 管理者は共有 PC 機能をオンにして、一度に 1 人のユーザーを許可することができます。 学生は、デバイス上で異なるサインイン アカウント間を切り替えることはできません。 また、管理者は、学生がサインアウトしたときにすべてのユーザー固有設定を削除するよう選択できます。

エンドユーザーは、これらの共有デバイスにゲスト アカウントでサインインできます。 ユーザーがサインインした後、資格情報がキャッシュされます。 エンドユーザーは、デバイスを使用する際、管理者が許可する機能にのみアクセスできます。 管理者は、たとえば、デバイスがスリープ モードになるタイミング、ユーザーがファイルをローカルに表示および保存できるかどうか、電源管理設定の有効化または無効化などを選択します。 また、ユーザーがサインオフしたときにゲスト アカウントを削除するかどうかや、しきい値に達したときに非アクティブなアカウントを削除するかどうかも制御します。

この記事では、構成プロファイルを作成する方法について説明し、使用可能な設定へのリンクとその説明を示します。

Intune でプロファイルが作成されると、そのプロファイルを組織内のデバイス グループにデプロイするか割り当てます。 このプロファイルは、さまざまな種類のデバイスやさまざまなバージョンのオペレーティング システム (OS) から成るデバイス グループに割り当てることもできます。

## <a name="create-the-profile"></a>プロファイルの作成

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]** 、 **[プロファイル]** 、 **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

   - **[名前]** :新しいプロファイルのわかりやすい名前を入力します。
   - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
   - **[プラットフォーム]** : **[Windows 10 以降]** を選択します。
   - **[プロファイルの種類]** : **[共有のマルチユーザーのデバイス]** を選択します。

4. [Windows 10 以降](shared-user-device-settings-windows.md)または [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) の設定を構成します。

5. **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、一覧に表示されていますが、まだ何も行われていません。 必ず組織内のデバイス グループに[プロファイルを割り当てて](device-profile-assign.md)ください。

## <a name="next-steps"></a>次の手順

- [Windows 10 以降](shared-user-device-settings-windows.md)および [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) のすべての設定を参照します。
- [プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
