---
title: Microsoft Intune を使用する Windows 10 デバイスに PIN を使ってサインインする - Azure | Microsoft Docs
description: ユーザーが PIN、指紋などを使ってデバイスにサインインできるようにするには、Windows Hello for Business を使用します。 Intune for Windows 10 デバイスでこのような設定を含む ID 保護構成プロファイルを作成し、そのプロファイルをユーザー グループとデバイス グループに割り当てます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 333b94bf3226c99ed50c4b433f4b477814b8e4bb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509533"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Microsoft Intune がインストールされた Windows 10 デバイス上で Windows Hello for Business を使用する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Windows Hello for Business は、パスワード、スマート カード、および仮想スマート カードを置き換えることで Windows デバイスにサインインする方法です。 Intune には、管理者が Windows Hello for Business を構成および使用できるようになる組み込みの設定が含まれています。 たとえば、これらの設定を使用すると、次のようなことができます。

- デバイスとユーザーに対して Windows Hello for Business を有効にする
- PIN の長さの最小値または最大値など、デバイスの PIN の要件を設定する
- ユーザーがデバイスにサインインするために使用できる (または使用できない) 指紋などのジェスチャを許可する

この機能は、次を実行しているデバイスに適用されます。

- Windows 10 以降
- Windows 10 Mobile
- Windows Holographic for Business

Intune では、"構成プロファイル" を使用して、お客様の組織のニーズに合わせてこのような設定を作成およびカスタマイズします。 このような機能をプロファイルに追加したら、その設定を組織内のユーザーおよびデバイス グループにプッシュまたは展開します。

この記事では、デバイス構成プロファイルを作成する方法について説明します。 すべての設定の一覧とその実行内容については、[Windows Hello for Business を有効にするための Windows 10 デバイス設定](identity-protection-windows-settings.md)に関するページを参照してください。

## <a name="create-the-device-profile"></a>デバイス プロファイルを作成する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **[名前]** :新しいプロファイルのわかりやすい名前を入力します。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[Windows 10 以降]** を選択します。 Windows Hello for Business は、Windows 10 以降を実行しているデバイスのみでサポートされます。
    - **[プロファイルの種類]** : **[Identity Protection]** を選択します。
    - **[Windows Hello for Business の構成]** :Windows Hello for Business を構成する方法を選択します。 次のようなオプションがあります。

        - **[未構成]** :デバイス上に [Windows Hello for Business をプロビジョニング](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)します。 Identity Protection プロファイルをユーザーのみに割り当てた場合は、デバイス コンテキストは既定で **[未構成]** になります。
        - **[無効]** : Windows Hello for Business を使用しない場合は、このオプションを選択します。 このオプションを選択すると、すべてのユーザーの Windows Hello for Business が無効になります。
        - **有効**: Intune で Windows Hello for Business 設定を[プロビジョニング](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)し、構成するには、このオプションを選択します。 構成が必要な設定を入力します。 すべての設定の一覧とその実行内容については、以下を参照してください。

            - [Windows Hello for Business を有効にするための Windows 10 デバイス設定](identity-protection-windows-settings.md)

4. 完了したら、 **[OK]**  >  **[作成]** を選択して変更を保存します。

プロファイルが作成され、プロファイル一覧に表示されます。 次に、ご自分のニーズに合わせてこのプロファイルをユーザーとデバイス グループに[割り当てます](../configuration/device-profile-assign.md)。

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>次の手順

- すべての[設定の一覧とその実行内容](identity-protection-windows-settings.md)を参照してください。
- [プロファイルを割り当て](../configuration/device-profile-assign.md)、[その状態を監視](../configuration/device-profile-monitor.md)します。
