---
title: アプリのインストールに関する問題のトラブルシューティング
titlesuffix: Microsoft Intune
description: Microsoft Intune のトラブルシューティング ウィンドウを使用して、アプリのインストールに関する問題をトラブルシューティングします。
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138681"
---
# <a name="troubleshoot-app-installation-issues"></a>アプリのインストールに関する問題のトラブルシューティング

Microsoft Intune の MDM で管理されたデバイスでは、アプリのインストールが失敗することがあります。 アプリのインストールが失敗した場合、失敗の理由を理解したり、問題をトラブルシューティングするのが難しい場合があります。 Microsoft Intune ではアプリのインストール失敗に関する詳細が提供されます。ヘルプ デスクのオペレーターや Intune の管理者は、これを利用してアプリの情報を確認し、ユーザーからのヘルプ要請に対処することができます。 Intune 内のトラブルシューティング ウィンドウではエラーの詳細が提供され、これにはユーザーのデバイス上のマネージド アプリに関する詳細も含まれます。 アプリのエンド ツー エンドのライフサイクルの詳細は、**[マネージド アプリ]** ウィンドウ内の個々のデバイスの下に表示されます。 アプリの作成日時、変更日時、対象とされた日時、デバイスに配信された日時など、インストールに関する問題を表示できます。 

## <a name="to-review-app-troubleshooting-details"></a>アプリのトラブルシューティングの詳細を確認するには

Intune では、特定のユーザーのデバイスにインストールされているアプリに基づいて、アプリのトラブルシューティングの詳細が提供されます。

1. サインイン、 [Azure ポータル](https://portal.azure.com)します。
2. **すべてのサービス** > **Intune** の順に選択します。 Intune は **[監視 + 管理]** セクションにあります。
3. **[Intune]** ウィンドウで、**[トラブルシューティング]** を選択します。
4. **[ユーザーの選択]** をクリックして、トラブルシューティングするユーザーを選択します。 **[ユーザーの選択]** ウィンドウが表示されます。
5. 名前または電子メール アドレスを入力して、ユーザーを選択します。 ウィンドウの下部にある **[選択]** をクリックします。 ユーザーに対するトラブルシューティング情報が、**[トラブルシューティング]** ウィンドウに表示されます。 
6. トラブルシューティングするデバイスを、**[デバイス]** の一覧から選択します。
    ![Intune のトラブルシューティング ウィンドウ。](media/troubleshoot-app-install-01.png)
7. 選択したデバイスのウィンドウから **[マネージド アプリ]** を選択します。 マネージド アプリの一覧が表示されます。
    ![Intune によって管理される特定のデバイスの詳細。](media/troubleshoot-app-install-02.png)
8. 一覧から、**[インストールのステータス]** が失敗を示しているアプリを選択します。
    ![インストールのエラーの詳細を示す選択したアプリ。](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > 同一のアプリを複数のグループに割り当てることは可能ですが、アプリに対して異なる意図したアクション (インテント) を使用する必要があります。 たとえば、アプリの割り当て中にアプリがユーザーのために除外される場合、アプリの解決されたインテントに **[除外されています]** と表示されます。 詳細については、「[アプリのインテントの競合を解決する方法](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)」をご覧ください。<br><br>
    > 現時点では、Intune が OS のプラットフォームに基づいてアプリを除外することはありません。

アプリのインストールのエラーに関する詳細では、問題点が示されます。 これらの詳細を使用して、問題解決のための最適なアクションを決定することができます。 アプリのインストールに関する問題のトラブルシューティングについて詳しくは、「[Error Codes For Troubleshooting App Installation Issues](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues)」(アプリのインストールに関する問題のトラブルシューティングのためのエラー コード) をご覧ください。

> [!Note]  
> **[トラブルシューティング]** ウィンドウには、ブラウザーで [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) に移動してアクセスすることもできます。

## <a name="next-steps"></a>次の手順

- Intune のトラブルシューティングに関する追加情報については、「[トラブルシューティング ポータルを使用して社内のユーザーをサポートする](help-desk-operators.md)」をご覧ください。 
- Microsoft Intune の既知の問題について学習します。 詳細については、「[Microsoft Intune の既知の問題](known-issues.md)」を参照してください。
- さらに支援が必要ですか。 「[Microsoft Intune のサポートを受ける方法](get-support.md)」を参照してください。
