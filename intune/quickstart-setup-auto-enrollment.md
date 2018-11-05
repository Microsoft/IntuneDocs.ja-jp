---
title: 'クイック スタート: Intune で自動登録を設定する'
description: 'クイック スタート: Intune で Windows 10 デバイスの自動登録を設定する。'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581646"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>クイック スタート: Windows 10 デバイスの自動登録を設定する

このクイック スタートでは、特定のユーザーが Windows 10 デバイスにサインインしたとき、Microsoft Intune がデバイスを自動的に登録するように設定します。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](free-trial-sign-up.md)します。

## <a name="prerequisites"></a>必要条件

- このクイック スタートを完了するには、まず[ユーザーを作成](quickstart-create-user.md)し、[グループを作成](quickstart-create-group.md)する必要があります。

## <a name="sign-in-to-intune"></a>Intune にサインインする

グローバル管理者または Intune サービス管理者として [Intune](https://aka.ms/intuneportal) にサインインします。

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を設定する

この例では、会社のデバイスと個人所有デバイスの両方を自動登録できるように MDM 登録を使用します。

1. Azure で、**[Azure Active Directory]** > **[モビリティ (MDM および MAM)]** > **[Microsoft Intune]** > **[一部]** の順に選択します。
![ブラウザー](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. **[グループの選択]** > **[Contoso Testers]** > **[選択]** の順に選択します。
3. 次の URL の既定値を使用します。
    - MDM 使用条件 URL
    - MDM 探索 URL
    - MDM 準拠 URL
4. **[保存]** を選びます。
5. グループ内のユーザーとして Windows 10 デバイスにサインインし、プロンプトに従います。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

Intune の自動登録を再構成するには、「[Windows デバイスの登録をセットアップする](windows-enroll.md)」を参照してください。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Windows 10 デバイスの自動登録方法について学習しました。 すべてのプラットフォーム全体にデバイスを登録する他の方法について学習することができます。

> [!div class="nextstepaction"]
> [デバイス登録とは](device-enrollment.md)