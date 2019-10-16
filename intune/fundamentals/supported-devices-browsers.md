---
title: Microsoft Intune でサポートされているオペレーティング システムとブラウザー
titleSuffix: ''
description: Intune デバイス管理でサポートされるデバイス プラットフォームとブラウザーの一覧を示します
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d2777f2caabc24a457fc407b3e47facb1f6fc3c
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314616"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Intune でサポートされるオペレーティング システムとブラウザー

Microsoft Intune をセットアップする前に、サポートされているオペレーティング システムとブラウザーを確認してください。

デバイスへの Intune のインストールについては、「[マネージド デバイスを使用して作業する](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions)」と [Intune のネットワーク帯域幅の使用法](network-bandwidth-use.md)に関するページを参照してください。

構成サービス プロバイダー サポートの詳細については、「[Configuration service provider reference (構成サービス プロバイダー リファレンス)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)」を参照してください。

## <a name="intune-supported-operating-systems"></a>Intune でサポートされるオペレーティング システム

以下のオペレーティング システムを実行しているデバイスを管理できます。

[!INCLUDE [mdm-supported-devices](../../intune-classic/includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Samsung KNOX Standard デバイスのサポート

ポータル サイト アプリは、[サポートされている KNOX デバイスの一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)に掲載されている登録対象のデバイスでのみ、MDM の登録を阻止する Knox のライセンス認証エラーを回避するために MDM 登録時に、Samsung KNOX ライセンス認証を試みます。 Samsung KNOX ライセンス認証をサポートしていないデバイスは、標準の Android デバイスとして登録されます。 Samsung デバイスには、KNOX をサポートするモデル番号を持つものがある一方で、そうでないものもあります。 Samsung デバイスを購入および展開する前に、デバイスの再販業者に KNOX 対応の有無について確認してください。

> [!NOTE]
> Samsung KNOX デバイスの登録では、[Samsung サーバーへのアクセスを有効にする](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers)必要がある場合があります。 

以下の Samsung デバイス モデル一覧では、Knox をサポートしていません。 これらは、Android 用のポータル サイト アプリにより、ネイティブの Android デバイスとして登録されています。

| **デバイス名** | **デバイスのモデル番号** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="windows-pc-software-client"></a>Windows PC ソフトウェア クライアント

代替登録方法として、[Intune ソフトウェア クライアント](../manage-windows-pcs-with-microsoft-intune.md)を Windows PC に展開し、インストールできます。 この機能は、Intune クラシック ポータルを使用する場合のみ利用可能です。 Intune ソフトウェア クライアントを利用し、Windows 10 Home エディションを除く、Windows 7 以降の PC を管理できます。

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune でサポートされている Web ブラウザー

さまざまな管理タスクで、次の管理 Web サイトのいずれかを使用する必要があります。

- [Microsoft 365 管理センター](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure Portal](https://portal.azure.com/)

Intune ポータルでは、次のブラウザーがサポートされています。
- Microsoft Edge (最新バージョン)
- Microsoft Internet Explorer 11
- Safari (最新バージョン、Mac のみ)
- Chrome (最新バージョン)
- Firefox (最新バージョン)




### <a name="intune-classic-portal"></a>Intune クラシック ポータル

Intune クラシック ポータルは、Intune PC ソフトウェア クライアントで登録されたデバイスの管理にのみ使用されます (https://manage.microsoft.com) 。 Intune クラシック ポータルには、Silverlight のブラウザー サポートが必要です。

次の Silverlight ブラウザーは、Intune コンソールをサポートしています。
- Internet Explorer 10 以降
- Google Chrome (バージョン 42 より前のバージョン)
- Silverlight が有効な Mozilla Firefox (バージョン 56 より前のバージョン)

> [!Note]
> Intune クラシック ポータルで Microsoft Edge とモバイル ブラウザーがサポートされないのは、[Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx) がサポートされていないためです。

このポータルには、サービス管理者のアクセス許可を持つユーザーまたは全体管理者の役割を持つテナント管理者のみがサインインできます。 管理コンソールにアクセスするには、アカウントに Intune を使用するライセンスがあり、サインイン状態が**許可済み**になっている必要があります。
