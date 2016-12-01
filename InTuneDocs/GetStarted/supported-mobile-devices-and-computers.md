---
title: "サポートされるモバイル デバイスとブラウザー |Microsoft Intune"
description: "Intune でサポートされるモバイル デバイスとコンピューター"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>サポートされるモバイル デバイスとコンピューター

登録の後に管理対象とすることのできるデバイスの種類は次のとおりです。

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

デバイスを登録すると、[これらのことが可能になります](/Intune/get-started/choose-how-to-manage-devices)。

別の方法として、Windows PC を Intune PC クライアント ソフトウェアで管理することもできます。 Intune PC クライアント ソフトウェアでは、Windows 10 Home を除く Windows 7 以降の PC がサポートされます。 クライアント ソフトウェアを使用して PC を管理する場合、[こちらの機能](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)を使用できます。

Enterprise Management Suite をお使いの場合は、Azure Active Directory (Azure AD) を使用して Windows 10 デバイスを登録することもできます。

## <a name="microsoft-intune-supported-web-browsers"></a>Microsoft Intune でサポートされている Web ブラウザー

さまざまな管理タスクで、次の管理 Web サイトのいずれかを使用する必要があります。

- [Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 管理コンソール](https://admin.manage.microsoft.com/)

> [!Note]
> Microsoft Edge とモバイル ブラウザーで管理コンソールがサポートされていないのは、[Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx) がサポートされていないためです。 Intune コンソールは一定期間を経て Silverlight に移行します。最終的には、Intune のすべてのモバイル デバイスとアプリケーションの管理機能が[新しい Microsoft Azure ポータルで使用できるようになります](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。

|Intune の機能 |サポートされているブラウザー|
|---------|---------|
|Intune 管理コンソール     |  Internet Explorer 10 以降<br /><br />Google Chrome (バージョン 42 より前のバージョン)<br /><br />Silverlight が有効な Mozilla Firefox<br /><br />**注:** Microsoft Edge とモバイル ブラウザーでは管理コンソールはサポートされていません。                      
|Office 365 管理ポータル     |モバイル ブラウザーと管理対象ブラウザーを含むすべてのブラウザー  |
|ポータル Web サイト     |**モバイル デバイスの場合:** サポートされている各プラットフォームに対して既定の Web ブラウザーを使用します   <br /><br />**Windows PC の場合:** Internet Explorer 10 以降または Microsoft Edge<br /><br />**Mac OS X 10.9 以降の場合:** Apple Safari    |

> [!Note]
> Microsoft Edge とモバイル ブラウザーで管理コンソールがサポートされていないのは、[Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx) がサポートされていないためです。 Intune コンソールは一定期間を経て Silverlight に移行します。最終的には、Intune のすべてのモバイル デバイスとアプリケーションの管理機能が[新しい Microsoft Azure ポータルで使用できるようになります](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Office 365 ポータル](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**テナント管理者として、このポータルを使用してサブスクリプションを管理します**。また、管理者の役割で許可されている場合、次のタスクを管理できます。

- サブスクリプションのユーザー アカウントを管理し、社内 Active Directory のディレクトリとの同期を構成する。
- セキュリティ グループと呼ばれる、ユーザーのグループを管理する。
- ユーザーに Intune を使用するためのライセンスを割り当てる。
- サブスクリプションで使用するドメイン名を構成する。 ドメイン名は、ユーザーがサインインに使用するアカウントを定義します。
- 保有するライセンス数や、使用できるクラウドの記憶域の量など、サブスクリプションの請求と購入の詳細を管理する。
- Intune サービスの正常性を表示するリンクを探す。
- アカウントに Intune を使用するライセンスが割り当てられていない場合でも、テナント管理者として、Office 365 ポータルにサインインしてサブスクリプションを管理できます。
- Intune のライセンスを持つ、管理者以外のユーザーは、このポータルを使用して、自分のパスワードをリセットしたり、プロファイルを編集したりできます。
- Office 365 ポータルにアクセスするには、アカウントのサインイン状態が "**許可済み**" になっている必要があります。 これは、サブスクリプションのライセンスを与えられていることとは別です。 既定では、すべてのユーザー アカウントは、"**許可済み**" の状態です。


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Microsoft Intune 管理コンソール](https://manage.microsoft.com/)

**サービス管理者として、このポータルを使用して、次のような日常のタスクを管理します**。

- コンピューターとモバイル デバイスのポリシーを設定する。
- ソフトウェアの更新プログラムやアプリなどのソフトウェアを、アップロードして展開する。
- コンピューターの Endpoint Protection を管理する。
- デバイスの状態を表示し、レポートを実行する。
- このポータルにサインインする。 このポータルにサインインするには、サービス管理者のアクセス許可があるか、または全体管理者の役割を持つテナント管理者である必要があります。


このポータルには、サービス管理者のアクセス許可を持つユーザーまたは全体管理者の役割を持つテナント管理者のみがサインインできます。 管理コンソールにアクセスするには、アカウントに Intune を使用するライセンスがあり、サインイン状態が**許可済み**になっている必要があります。



<!--HONumber=Nov16_HO4-->


