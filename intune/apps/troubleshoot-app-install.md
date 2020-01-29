---
title: アプリのインストールに関する問題のトラブルシューティング
titleSuffix: Microsoft Intune
description: Microsoft Intune のトラブルシューティング ウィンドウを使用して、アプリのインストールに関する問題をトラブルシューティングします。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540981"
---
# <a name="troubleshoot-app-installation-issues"></a>アプリのインストールに関する問題のトラブルシューティング

Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 Microsoft Intune ではアプリのインストール失敗に関する詳細が提供されます。ヘルプ デスクのオペレーターや Intune の管理者は、これを利用してアプリの情報を確認し、ユーザーからのヘルプ要請に対処することができます。 Intune 内のトラブルシューティング ウィンドウではエラーの詳細が提供され、これにはユーザーのデバイス上のマネージド アプリに関する詳細も含まれます。 アプリのエンド ツー エンドのライフサイクルの詳細は、 **[マネージド アプリ]** ウィンドウ内の個々のデバイスの下に表示されます。 アプリの作成日時、変更日時、対象とされた日時、デバイスに配信された日時など、インストールに関する問題を表示できます。 

> [!NOTE]
> 特定のアプリ インストールのエラーコード情報については、[Intune アプリのインストール エラーのリファレンス](~/apps/app-install-error-codes.md)に関する記事を参照してください。

## <a name="app-troubleshooting-details"></a>アプリのトラブルシューティングの詳細

Intune では、特定のユーザーのデバイスにインストールされているアプリに基づいて、アプリのトラブルシューティングの詳細が提供されます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[トラブルシューティング + サポート]** を選択します。
4. **[ユーザーの選択]** をクリックして、トラブルシューティングするユーザーを選択します。 **[ユーザーの選択]** ウィンドウが表示されます。
5. 名前または電子メール アドレスを入力して、ユーザーを選択します。 ウィンドウの下部にある **[選択]** をクリックします。 ユーザーに対するトラブルシューティング情報が、 **[トラブルシューティング]** ウィンドウに表示されます。 
6. トラブルシューティングするデバイスを、 **[デバイス]** の一覧から選択します。
    ![Intune のトラブルシューティング ウィンドウ。](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. 選択したデバイスのウィンドウから **[マネージド アプリ]** を選択します。 マネージド アプリの一覧が表示されます。
    ![Intune によって管理される特定のデバイスの詳細。](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. 一覧から、 **[インストールのステータス]** が失敗を示しているアプリを選択します。
    ![インストールのエラーの詳細を示す選択したアプリ。](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > 同一のアプリを複数のグループに割り当てることは可能ですが、アプリに対して異なる意図したアクション (インテント) を使用する必要があります。 たとえば、アプリの割り当て中にアプリがユーザーのために除外される場合、アプリの解決されたインテントに **[除外されています]** と表示されます。 詳細については、「[アプリのインテントの競合を解決する方法](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)」をご覧ください。<br><br>
    > 必要なアプリのインストールに失敗した場合、自分で、あるいはヘルプデスクに依頼してデバイスを同期し、アプリのインストールを再試行できます。

アプリのインストールのエラーに関する詳細では、問題点が示されます。 これらの詳細を使用して、問題解決のための最適なアクションを決定することができます。 アプリのインストールに関する問題のトラブルシューティングの詳細については、「[Android アプリのインストール エラー](app-install-error-codes.md#android-app-installation-errors)」と「[iOS アプリのインストール エラー](app-install-error-codes.md#ios-app-installation-errors)」のセクションを参照してください。

> [!Note]  
> **[トラブルシューティング]** ウィンドウには、ブラウザーで [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) に移動してアクセスすることもできます。

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>ユーザー グループを対象にしたアプリのインストールでデバイスがアクセスされない
アプリのインストールで問題が発生した場合は、次のアクションを考慮する必要があります。
- アプリがポータル サイトに表示されない場合は、確実に、アプリが**利用可能**のインテントを指定して展開されていて、ユーザーがアプリでサポートされているデバイスの種類を使用してポータル サイトにアクセスしているようにします。
- Windows BYOD デバイスの場合、ユーザーは職場アカウントをデバイスに追加する必要があります。
- ユーザーが AAD デバイスの制限を超えているかどうかを確認します。
  1. [Azure Active Directory デバイスの設定](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId)に移動します。
  2. **[ユーザーごとのデバイスの最大数]** の値をメモしておきます。
  3. [Azure Active Directory のユーザー](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers)に移動します。
  4. 影響を受けているユーザーを選択し、 **[デバイス]** をクリックします。
  5. ユーザーが設定された制限を超えている場合は、不要になった古いレコードを削除します。
- iOS DEP デバイスの場合は、確実にユーザーが Intune のデバイスの概要ペインに **[ユーザーによって登録済み]** と表示されているようにします。 NA と表示されている場合は、Intune ポータル サイトの構成ポリシーを展開します。 詳細については、[ポータル サイト アプリの構成](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices)に関する記事をご覧ください。

## <a name="win32-app-installation-troubleshooting"></a>Win32 アプリのインストールのトラブルシューティング

Intune 管理拡張機能を使用して展開された Win32 アプリを選択します。 Win32 アプリのインストールに失敗した場合は、 **[ログの収集]** オプションを選択できます。 

> [!IMPORTANT]
> Win32 アプリがデバイスに正常にインストールされると、 **[ログの収集]** オプションは有効になりません。<p>Win32 アプリのログ情報を収集する前に、Intune 管理拡張機能を Windows クライアントにインストールする必要があります。 PowerShell スクリプトまたは Win32 アプリをユーザーまたはデバイスのセキュリティ グループに展開すると、Intune 管理拡張機能がインストールされます。 詳細については、[Intune 管理拡張機能の前提条件](intune-management-extension.md#prerequisites)に関する記事を参照してください。

### <a name="collect-log-file"></a>ログ ファイルを収集する

Win32 アプリのインストール ログを収集するには、まずセクション「[アプリのトラブルシューティングの詳細情報](troubleshoot-app-install.md#app-troubleshooting-details)」に記載されている手順を実行します。 次に、以下の手順に進みます。

1. **[インストールの詳細]** ウィンドウの **[ログの収集]** オプションをクリックします。

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. ファイル パスにログ ファイル名を指定してログ ファイル収集プロセスを開始し、 **[OK]** をクリックします。

    > [!NOTE]
    > ログ収集にかかる時間は 2 時間未満です。 サポートされるファイルの種類: *.log、.txt、.dmp、.cab、.zip、.xml、.evtx、.evtl*。 最大 25 個のファイル パスが許可されています。

3. ログ ファイルが収集されたら、**ログ** リンクを選択してログ ファイルをダウンロードできます。

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > アプリのログ収集の成功を示す通知が表示されます。

#### <a name="win32-log-collection-requirements"></a>Win32 ログ収集の要件

ログ ファイルを収集するには、従う必要がある特定の要件があります。

- 完全なログ ファイルのパスを指定する必要があります。 
- 以下のようなログ収集用の環境変数を指定できます。<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- 次のような正確なファイル拡張子のみが許可されています。<br>
  *.log、.txt、.dmp、.cab、.zip、.xml*
- アップロードできる最大ログ ファイルは、60 MB または 25 個ファイルのうち、どちらか早い方です。 
- Win32 アプリのインストール ログ収集は、必須、利用可能、およびアンインストールのアプリ割り当ての意図を満たすアプリに対して有効になります。
- 保存されたログは、ログに含まれる個人を特定できる情報を保護するために暗号化されます。
- Win32 アプリの失敗に関するサポート チケットを開くときは、上記の手順を使用して関連するエラー ログを添付してください。

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Microsoft ストア アプリのトラブルシューティング

トピック「[Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)」 (Microsoft ストア アプリのパッケージ化、展開、およびクエリのトラブルシューティング) に記載されている情報は、Microsoft ストアからアプリをインストールする際に発生する可能性がある一般的な問題のトラブルシューティングで役に立ちます (Intune を使用する場合、または他の手段を使用する場合に関係なく)。

## <a name="app-troubleshooting-resources"></a>アプリのトラブルシューティングに関するリソース
- [Office Pro Plus の展開の一部として Visio と Project を展開する](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [確実に Intune を使用して Windows 10 1903 に MSfB アプリを展開するためのアクションを実行する](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Microsoft Intune での MSI アプリの展開のトラブルシューティング](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Intune クラシック Windows PC エージェントへのソフトウェアの配布に関するベスト プラクティス](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>次のステップ

- Intune のトラブルシューティングに関する追加情報については、「[トラブルシューティング ポータルを使用して社内のユーザーをサポートする](../fundamentals/help-desk-operators.md)」をご覧ください。 
- Microsoft Intune の既知の問題について学習します。 詳細については、「[Intune カスタマー サクセス](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)」を参照してください。
- さらに支援が必要ですか? 「[Microsoft Intune のサポートを受ける方法](../fundamentals/get-support.md)」を参照してください。
