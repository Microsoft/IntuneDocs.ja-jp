---
title: "サポートされるデバイス - Microsoft Intune"
description: "Intune デバイス管理でサポートされるデバイス プラットフォームとブラウザーの一覧を示します"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/03/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 56516562b9a7510020475d226c74bf719bdd33a3
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2018
---
# <a name="supported-devices-and-browsers"></a>サポートされるデバイスとブラウザー

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

この記事は、企業でデバイス管理を担当するシステム管理者を対象としています。 電話への Intune インストールについては、[管理デバイスでの作業](/intune-user-help/company-portal-frequently-asked-questions)に関するページを参照してください。

Microsoft Intune のセットアップを開始する前に、次の要件を確認してください。

- [サポートされているデバイスとコンピューター](#intune-supported-devices)
- [Intune 対応の Web ブラウザーの一覧](#intune-supported-web-browsers)

[Intune のネットワーク帯域幅の使用法](network-bandwidth-use.md) ([クラシック ポータル](/intune-classic/get-started/network-bandwidth-use)) についてもよく理解しておく必要があります。

## <a name="intune-supported-devices"></a>Intune 対応デバイス

次のデバイスを Intune モバイル デバイス管理を使用して管理できます。

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Samsung KNOX Standard デバイスのサポート

ポータル サイト アプリは、MDM 登録時に、登録対象のデバイスが[サポートされている KNOX デバイスの一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)に掲載されている場合のみ、Samsung KNOX ライセンス認証を試みます。 これにより、MDM 登録を妨げる KNOX ライセンス認証エラーの発生を回避できます。 Samsung KNOX ライセンス認証をサポートしていないデバイスは、標準の Android デバイスとして登録されます。 Samsung デバイスには、KNOX をサポートするモデル番号を持つものがある一方で、そうでないものもあります。 Samsung デバイスを購入および展開する前に、デバイスの再販業者に KNOX 対応の有無について確認してください。

> [!NOTE]
> Samsung KNOX デバイスの登録では、[Samsung サーバーへのアクセスを有効にする](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers)必要がある場合があります。 

以下に一覧表示した Samsung デバイス モデルは、KNOX をサポートしておらず、Android 用ポータル サイト アプリによってネイティブの Android デバイスとして登録されます。

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

Intune は Windows Server オペレーティング システムを管理できません。

### <a name="windows-pc-software-client"></a>Windows PC ソフトウェア クライアント

代替登録方法として、[Intune ソフトウェア クライアント](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune)を Windows PC に展開し、インストールできます。 この機能は、Intune クラシック ポータルを使用する場合のみ利用可能です。 Intune ソフトウェア クライアントを利用し、Windows 10 Home エディションを除く、Windows 7 以降の PC を管理できます。

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Intune でサポートされている Web ブラウザー

さまざまな管理タスクで、次の管理 Web サイトのいずれかを使用する必要があります。

- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure Portal](https://portal.azure.com/)

Intune ポータルでは、次のブラウザーがサポートされています。
- Microsoft Edge (最新バージョン)
- Microsoft Internet Explorer 11
- Safari (最新バージョン、Mac のみ)
- Chrome (最新バージョン)
- Firefox (最新バージョン)

### <a name="intune-classic-portal"></a>Intune クラシック ポータル

Intune PC ソフトウェア クライアントや Mobile Threat Defense パートナーとの統合といった Intune クラシック専用機能は、Intune クラシック ポータル (https://manage.microsoft.com) でのみ利用可能です。 Intune クラシック ポータルには、Silverlight のブラウザー サポートが必要です。

次の Silverlight ブラウザーは、Intune コンソールをサポートしています。
- Internet Explorer 10 以降
- Google Chrome (バージョン 42 より前のバージョン)
- SilveSilverlight が有効な Mozilla Firefox。[詳しくはこちらをご覧ください](https://go.microsoft.com/fwlink/?linkid=836872)。

> [!Note]
> Intune クラシック ポータルで Microsoft Edge とモバイル ブラウザーがサポートされないのは、[Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx) がサポートされていないためです。

このポータルには、サービス管理者のアクセス許可を持つユーザーまたは全体管理者の役割を持つテナント管理者のみがサインインできます。 管理コンソールにアクセスするには、アカウントに Intune を使用するライセンスがあり、サインイン状態が**許可済み**になっている必要があります。
