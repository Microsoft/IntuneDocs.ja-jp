---
title: "Intune で Windows デバイスのパスコードをリセットする"
titlesuffix: Azure portal
description: "Microsoft PIN Reset Service が統合された Windows デバイスのパスコードを Intune を使用してリセットする方法を説明します。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: faf3e9b81f76755135f73f8753305d96d227ec14
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>Microsoft PIN Reset Service が統合された Windows デバイスのパスコードを Intune を使用してリセットする

Windows デバイスのパスコード リセット機能に Microsoft PIN Reset Service を統合することにより、Windows 10 Mobile を実行するデバイスで新しいパスコードを生成できます。 そのデバイスでは、Windows 10 Creators Update 以降を実行している必要があります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Windows - Windows 10 Creators Update 以降 (Azure AD に参加) でサポートされています
- Windows Phone - サポートされていません
- iOS - サポートされていません
- macOS - サポートされていません
- Android - サポートされていません


## <a name="before-you-start"></a>開始する前に

管理する Windows デバイスのパスコードをリモートからリセットする前に、PIN のリセット サービスを Intune テナントに組み込み、管理するデバイスを構成します。 このように設定するには、次の手順に従います。

### <a name="connect-intune-with-the-pin-reset-service"></a>PIN のリセット サービスを使用して Intune と接続する

1. [Microsoft PIN Reset Service Integration Web サイト](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent)に進み、Intune テナントを管理するテナント管理者アカウントを使用してサインインします。
2. ログインしたら **[同意]** をクリックして、PIN リセット サービスがアカウントにアクセスするのに同意します。<br>
![PIN をリセット サービスの [アクセス許可] ページ](./media/pin-reset-service-application.png)
3. Intune と PIN のリセット サービスが統合されたことは、Azure Portal で [Enterprise applications - All applications]/(エンタープライズ アプリケーション - すべてのアプリケーション)/ から確認できます。スクリーンショットは次のとおりです。<br>
![Azure の PIN リセット サービス アプリケーション](./media/pin-reset-service-home-screen.png)
4. Intune テナント管理資格情報を使用し、[この Web サイト](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent)にログインし、再度 **[同意]** してサービスがアクセスにアクセスすることに同意します。

### <a name="configure-windows-devices-to-use-pin-reset"></a>PIN のリセットを使用するよう Windows デバイスを構成する

管理する Windows デバイスで PIN のリセットを構成するには、その機能を有効にするために [Intune の Windows 10 カスタム デバイス ポリシー](custom-settings-windows-10.md)を使用します。 次の Windows ポリシー構成サービス プロバイダー (CSP) を使用して、ポリシーを構成します。


- **対象デバイス** - **./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery**

*tenant ID* は、Azure Active Directory の **[プロパティ]** ページで取得できる Azure Active Directory ディレクトリ ID を示します。

この CSP の値を **True** に設定します。

## <a name="steps-to-reset-the-passcode"></a>パスコードをリセットする手順

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[管理]** > **[すべてのデバイス]** の順に選択します。
5. パスコードをリセットするデバイスを選択し、その後、デバイス プロパティ ブレードで **[New passcode]/(新しいパスコード)/** を選択します。
6. 表示される確認メッセージの **[はい]** を選択します。 パスコードが生成され、以降 7 日間ポータルに表示されます。

## <a name="next-steps"></a>次のステップ

パスコードのリセットに失敗した場合、詳細が記載されたリンクがポータルに表示されます。


