---
title: "サポートされるデバイス - Microsoft Intune"
description: "Intune デバイス管理でサポートされるデバイス プラットフォームとブラウザーの一覧を示します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/22/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4cfdf6a8aab1bda15015f85b1fb8f364e6a0edfa
ms.sourcegitcommit: 29ee35da2864b25f4432d2423b285014c77040af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2017
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
