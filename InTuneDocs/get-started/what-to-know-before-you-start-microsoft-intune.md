---
title: "サポートされるデバイス - Microsoft Intune | Microsoft Docs"
description: "Intune デバイス管理でサポートされるデバイス プラットフォームとブラウザーの一覧を示します"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b3732d0c6461f9fb8462ae5584055204d597aae0
ms.openlocfilehash: 0af4f49713a65900079d69a09f20d210797c935c


---

# <a name="supported-devices-and-browsers"></a>サポートされるデバイスとブラウザー

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

この記事は、企業でデバイス管理を担当するシステム管理者を対象としています。 電話への Intune インストールについては、[管理デバイスでの作業](https://docs.microsoft.com/intune/enduser/company-portal-frequently-asked-questions)に関するページを参照してください。

Microsoft Intune のセットアップを開始する前に、次の要件を確認してください。

- [サポートされているデバイスとコンピューター](#intune-supported-devices)
- [Intune 対応の Web ブラウザーの一覧](#intune-supported-web-browsers)

[Intune のネットワーク帯域幅の使用法](network-bandwidth-use.md)について、よく理解しておく必要もあります。

## <a name="intune-supported-devices"></a>Intune 対応デバイス

次のデバイスを Intune モバイル デバイス管理を使用して管理できます。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Intune は Windows Server オペレーティング システムを管理できません。

Intune デバイス管理は、[これらの機能](mobile-device-management-capabilities-in-microsoft-intune.md)を提供します。

### <a name="windows-pc-software-client"></a>Windows PC ソフトウェア クライアント

代替登録方法として、[Intune ソフトウェア クライアント](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)を Windows PC に展開し、インストールできます。 Intune ソフトウェア クライアントを利用し、Windows 10 Home エディションを除く、Windows 7 以降の PC を管理できます。 クライアント ソフトウェアを使用して PC を管理する場合、[こちらの機能](windows-pc-management-capabilities-in-microsoft-intune.md)を使用できます。

### <a name="exchange-activesync-management"></a>Exchange ActiveSync による管理

Intune コンソールから [Exchange ActiveSync デバイス](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)を管理できます。 このオプションでは、他の方法と比較した場合、管理機能が限られます。 サポートされているデバイスの一覧については、「[Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0)」 (Office 365 に組み込まれているモバイル デバイス管理の機能) を参照してください。

## <a name="intune-supported-web-browsers"></a>Intune でサポートされている Web ブラウザー

さまざまな管理タスクで、次の管理 Web サイトのいずれかを使用する必要があります。

- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 管理コンソール](https://admin.manage.microsoft.com/)

|Intune の機能 |サポートされているブラウザー|
|---------|---------|
|**Intune 管理コンソール**     |  Internet Explorer 10 以降<br /><br />Google Chrome (バージョン 42 より前のバージョン)<br /><br />Silverlight が有効な Mozilla Firefox<br />**注意:** 2017 年 3 月で、Mozilla は Silverlight のサポートを終了する予定です。 [詳細については、ここをクリック](https://go.microsoft.com/fwlink/?linkid=836872)してください。 |
|**Office 365 管理ポータル**     |モバイル ブラウザーと管理対象ブラウザーを含むすべてのブラウザー  |
|**ポータル Web サイト**     |**モバイル デバイスの場合:** サポートされている各プラットフォームに対して既定の Web ブラウザーを使用します   <br /><br />**Windows PC の場合:** Internet Explorer 10 以降または Microsoft Edge<br /><br />**Mac OS X 10.9 以降の場合:** Apple Safari    |

> [!Note]
> Microsoft Edge とモバイル ブラウザーで管理コンソールがサポートされていないのは、[Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx) がサポートされていないためです。 Intune コンソールは一定期間を経て Silverlight に移行します。最終的には、Intune のすべてのモバイル デバイスとアプリケーションの管理機能が[新しい Microsoft Azure ポータルで使用できるようになります](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。


このポータルには、サービス管理者のアクセス許可を持つユーザーまたは全体管理者の役割を持つテナント管理者のみがサインインできます。 管理コンソールにアクセスするには、アカウントに Intune を使用するライセンスがあり、サインイン状態が**許可済み**になっている必要があります。

>[!div class="step-by-step"]

>[**ネットワーク** &rarr;](network-bandwidth-use.md)  



<!--HONumber=Feb17_HO2-->


