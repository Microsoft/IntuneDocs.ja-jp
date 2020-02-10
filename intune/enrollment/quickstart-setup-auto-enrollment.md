---
title: 'クイック スタート: Intune で自動登録を設定する'
description: 'クイック スタート: Intune で Windows 10 デバイスの自動登録を設定する。'
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5cc7cf3661caa2b2640d9370d26402b7702d36b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541052"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>クイック スタート:Windows 10 デバイスの自動登録を設定する

このクイック スタートでは、特定のユーザーが Windows 10 デバイスにサインインしたとき、Microsoft Intune がデバイスを自動的に登録するように設定します。

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="prerequisites"></a>[前提条件]

- Microsoft Intune サブスクリプション - [無料試用版アカウントにサインアップします](../fundamentals/free-trial-sign-up.md)。
- このクイック スタートを完了するには、まず[ユーザーを作成](../fundamentals/quickstart-create-user.md)し、[グループを作成](../fundamentals/quickstart-create-group.md)する必要があります。

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager で Intune にサインインする

全体管理者または Intune サービス管理者として、[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。 Intune の試用版サブスクリプションを作成した場合、サブスクリプションを作成したアカウントがグローバル管理者になります。

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を設定する

この例では、会社のデバイスと個人所有デバイスの両方を自動登録できるように MDM 登録を使用します。 無料の Azure Active Directory Premium サブスクリプションにサインアップします。

1. [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431) で、 **[すべてのサービス]**  >  **[M365 Azure Active Directory]**  >  **[Azure Active Directory]**  >  **[モビリティ (MDM および MAM)]** を選択します。
2. **[無料の Premium 評価版を入手してこの機能を使用する]** を選択します。 このオプションを選択すると、Azure Active Directory の無料 Premium 試用版を使用して自動登録できます。 

    ![Azure Active Directory 無料 Premium 評価版を選択する](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

3. **[Enterprise Mobility + Security E5]** 無料評価版オプションを選択します。 
4. 無料試用版について、 **[無料試用版]**  >  **[有効化]** をクリックします。

    ![[Enterprise Mobility + Security E5] 無料評価版を選択する](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

    > [!NOTE]
    > 有効化には 1 分かかる場合があります。 

3. **[Microsoft Intune]** を選択して Intune を構成します。 

    ![一覧から [Microsoft Intune] を選択する](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. **[MDM ユーザー スコープ]** から **[一部]** を選択し、MAM の自動登録を使用して、従業員の Windows デバイス上のエンタープライズ データを管理します。 MDM 自動登録は、AAD 参加済みデバイスと Bring Your Own Device のシナリオ向けに構成されます。

    ![構成の一覧から [一部] を選択する](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. 割り当てられたグループとして **[グループの選択]**  >  **[Contoso Testers]**  >  **[選択]** の順にクリックします。

    ![登録するグループを選択する](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. **[MAM ユーザー スコープ]** から **[一部]** を選択して、従業員のデバイス上のデータを管理します。

    ![登録するグループを選択する](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-06.png)

7. 割り当てられたグループとして **[グループの選択]**  >  **[Contoso Testers]**  >  **[選択]** の順に選択します。 
8. 残りの構成値には既定値を使用します。
9. **[保存]** を選びます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

Intune の自動登録を再構成するには、「[Windows デバイスの登録をセットアップする](windows-enroll.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

このクイック スタートでは、Windows 10 デバイスの自動登録方法について学習しました。 デバイスの登録について詳しくは、「[デバイス登録とは](device-enrollment.md)」をご覧ください

この一連の Intune のクイック スタートに従うには、次のクイック スタートに進んでください。

> [!div class="nextstepaction"]
> [クイック スタート: Windows 10 デバイスの登録](../quickstart-enroll-windows-device.md)
