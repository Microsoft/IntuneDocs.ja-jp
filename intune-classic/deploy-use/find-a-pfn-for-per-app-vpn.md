---
title: "アプリごとの VPN のパッケージ ファミリ名 (PFN) の検索"
description: "アプリごとの VPN を構成できるように PFN を検索する。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ms.reviewer: tycast
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: eea3b9e2888f07399c8cda1e81ae8a5318d02d42
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn-configuration"></a>アプリごとの VPN 構成のパッケージ ファミリー名 (PFN) を検索する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

アプリごとの VPN をセットアップできるように PFN を検索する方法は 2 つあります。

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Windows 10 コンピューターにインストールされているアプリの PFN を検索する

使用しているアプリが既に Windows 10 コンピューターにインストールされている場合、[Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell コマンドレットを使用して PFN を取得できます。

Get-AppxPackage の構文:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
PFN を取得するには、状況に応じて管理者として PowerShell を実行する必要があります。

たとえば、コンピューターにインストールされているすべてのユニバーサル アプリに関する情報を取得するには、`Get-AppxPackage` を使用します。

名前がわかっているアプリに関する情報を取得するには、`Get-AppxPackage *<app_name>` を使用します。 アプリの正確な名前がわからない場合は、ワイルドカード文字を使用すると便利です。 たとえば、OneNote に関する情報を取得するには、`Get-AppxPackage *OneNote` を使用します。


OneNote について取得される情報の例を次に示します。

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>アプリがコンピューターにインストールされていない場合に PFN を検索する

1.  https://www.microsoft.com/ja-jp/store/apps に移動します。
2.  検索バーにアプリ名を入力します。 この例では、OneNote を検索します。
3.  アプリのリンクを選びます。 URL の末尾に一連の文字があることに注意してください。 この例では、URL は `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl` のようになります。
4.  別のタブに URL "`https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`" を貼り付けます。 `<app id>` の部分を、https://www.microsoft.com/ja-jp/store/apps から取得したアプリ ID (手順 3 の URL の末尾にある一連の文字) で置き換えます。 この OneNote の例の場合、`https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata` を貼り付けます。

Microsoft Edge に目的の情報が表示されます。Internet Explorer で **[開く]** を選んで情報を確認します。 PFN 値は最初の行に表示されます。 この例の結果は次のようになります。


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
