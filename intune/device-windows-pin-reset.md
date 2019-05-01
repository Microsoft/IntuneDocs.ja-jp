---
title: Microsoft Intune で Windows のパスコードをリセットする - Azure | Microsoft Docs
description: Windows デバイスのパスコードをリセットするには、Microsoft PIN Reset Service と Microsoft PIN Reset Client をインストールし、Azure Active Directory ディレクトリ ID を使ってデバイス ポリシーを作成してから Azure Portal で Microsoft Intune を使ってパスコードをリセットします。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b53ffbed93195b84544570e6a740fa614e219458
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513550"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Intune を使って Windows デバイスのパスコードをリセットする

Windows デバイスのパスコードをリセットすることができます。 パスコード リセット機能は、Microsoft PIN Reset Service を使って、Windows 10 Mobile を実行するデバイス用に新しいパスコードを生成します。 

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Creators Update 以降を実行する Windows 10 Mobile (Azure AD に参加)。

次のプラットフォームは**サポートされません**。
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>PIN リセット サービスを承認する

Windows デバイスのパスコードをリセットするには、PIN Reset Service を Intune テナントにオンボードします。

1. [Microsoft PIN Reset Service Production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) に移動し、テナント管理者アカウントを使ってサインインします。
2. PIN リセット サービスの承諾に**同意**して、ご自分のアカウントにアクセスします。![アクセス許可に対する PIN Reset Server の要求を受け入れる](./media/pin-reset-service-home-screen.png)
3. [Microsoft PIN Reset Client Production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) に移動し、テナント管理者アカウントを使ってサインインします。 PIN Reset Client の承諾に**同意**して、ご自分のアカウントにアクセスします。
4. [Azure portal](https://portal.azure.com) で、PIN リセット サービスがエンタープライズ アプリケーション (すべてのアプリケーション) に表示されていることを確認します。![PIN リセット サービスの [アクセス許可] ページ](./media/pin-reset-service-application.png)

> [!NOTE]
> PIN リセット要求に同意した後、`Page not found` というメッセージが表示されたり、何も行われていないように見えたりすることがあります。 この動作は正常なものです。 2 つの PIN リセット アプリケーションがご自分のテナントに表示されることを確認してください。

## <a name="configure-windows-devices-to-use-pin-reset"></a>PIN のリセットを使用するよう Windows デバイスを構成する

管理する Windows デバイスで PIN のリセットを構成するには、[Intune の Windows 10 カスタム デバイス ポリシー](custom-settings-windows-10.md)を使います。 次の Windows ポリシー構成サービス プロバイダー (CSP) を使用して、ポリシーを構成します。

**デバイス ポリシーを使う** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

<*tenant ID*> をお使いの Azure AD ディレクトリ ID に置き換えます。この ID は、[Azure Portal](https://portal.azure.com) で Azure Active Directory の **[プロパティ]** に表示されます。

この CSP の値を **True** に設定します。

> [!TIP]
> 作成したポリシーを、グループに割り当て (または展開し) ます。 ポリシーは、ユーザー グループまたはデバイス グループに割り当てることができます。 ユーザー グループに割り当てる場合、iOS などの他のデバイスを使っているユーザーがグループに含まれることがあります。 技術的には、ポリシーは適用されませんが、状態の詳細にはこれらのデバイスも含まれます。

## <a name="reset-the-passcode"></a>パスコードをリセットする

1. [Azure ポータル](https://portal.azure.com)にサインインします。 
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス]**、**[すべてのデバイス]** の順に選択します。
4. パスコードをリセットするデバイスを選択します。 デバイスのプロパティで、**[新しいパスコード]** を選択します。
5. **[はい]** をクリックして操作を確定します。 パスコードが生成され、以降 7 日間ポータルに表示されます。

## <a name="next-step"></a>次の手順

パスコードのリセットに失敗した場合、詳細情報を提供するリンクがポータルに表示されます。
