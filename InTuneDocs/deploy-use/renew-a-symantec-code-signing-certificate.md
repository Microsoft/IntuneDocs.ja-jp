---
title: "Intune で使用する Symantec エンタープライズ コード署名証明書を更新する | Microsoft Docs"
description: "特定の Windows および Windows Phone モバイル デバイスの管理に使用する Symantec 証明書を更新するためのガイダンス"
keywords: 
author: staciebarker
ms.author: stabar
manager: angerobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 928e4e8097b9cd326e0863a45b183226a7eae056
ms.openlocfilehash: acd1ab3a988adc4fee2a57ff4be82bac8e92a435


---

# <a name="renew-a-symantec-enterprise-code-signing-certificate-for-windows-devices"></a>Windows デバイス用の Symantec エンタープライズ コード署名証明書を更新する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Windows および Windows Phone モバイル アプリを展開するのに使用する Symantec 証明書は、定期的に更新する必要があります。

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Symantec エンタープライズ コード署名証明書を更新する方法

1.  証明書の有効期限の約 14 日前に Symantec から送信される更新に関する電子メールを探します。 この電子メールには、エンタープライズ証明書の更新に関する Symantec から指示が記載されています。

    Symantec 証明書の詳細については、[www.symantec.com](http://www.symantec.com) にアクセスするか、1-877-438-8776 または 1-650-426-3400 に電話をかけてください。

2.  Web サイト (例: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) に移動し、証明書に関連付けられている Symantec 発行者 ID と電子メール アドレスを使用してログインします。 更新を開始するコンピューターは、証明書のダウンロードに使用するのと同じコンピューターである必要があります。

3.  更新が承認され支払いが済んだら、証明書をダウンロードします。

## <a name="how-to-install-the-updated-certificate-for-windows-phone-80"></a>Windows Phone 8.0 の更新された証明書をインストールする方法

1.  最新の Windows Phone ポータル サイト ( [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060)) をダウンロードして署名します。

2.  Intune 管理コンソール ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)) を開き、**[管理者]**、**[モバイル デバイス管理]** &gt; **[Windows Phone]** の順に進み、**[署名済みアプリのアップロード]** をクリックします。

3.  新しく署名したポータル サイトをアップロードします。 新しく署名した SSP.xap と、Symantec から送信された新しい .PFX ファイルまたはこの新しい .PFX ファイルを使用して作成されたアプリケーション登録トークンが必要になります。

4.  アップロードが完了したら、Intune 管理コンソールの [ **ソフトウェア** ] ワークスペースでポータル サイトの古いバージョンを削除します。

5.  同じ証明書を使用してすべてのエンタープライズ基幹業務アプリにもう一度署名し、アップロードして、既存のアプリケーションと置き換えます。

現在は、署名済みの SSP.xap ファイルを提供することが、更新されたコード署名証明書を提供する唯一の方法です。 署名済みの基幹業務アプリをサポートするには、ユーザーがストアからポータル サイト アプリをインストールする場合でも、ポータル サイト アプリに署名してアップロードする必要があります。

## <a name="how-to-install-the-updated-certificate-for-windows-phone-81-and-later-devices"></a>Windows Phone 8.1 以降のデバイスの更新された証明書をインストールする方法

1.  ダウンロード センター ( [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060)) から最新の Windows Phone ポータル サイトをダウンロードして署名します。

2.  [Intune 管理コンソール](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) を開き、**[管理者]** &gt; **[モバイル デバイス管理]** &gt; **[Windows Phone]** の順に進み、**[署名済みアプリのアップロード]** をクリックします。

3.  新しく署名したポータル サイトをアップロードします。 新しく署名した SSP.xap と、Symantec から送信された新しい .PFX ファイルまたはこの新しい .PFX ファイルを使用して作成されたアプリケーション登録トークンが必要になります。

4.  アップロードが完了したら、 **[ソフトウェア]**  ワークスペースで古いバージョンのポータル サイトを削除します。

5.  新しい証明書を使用して、新しいエンタープライズ基幹業務アプリと更新されたエンタープライズ基幹業務アプリのすべてに署名します。 既存のアプリケーションを再署名して再展開する必要はありません。


### <a name="see-also"></a>関連項目
[Windows Phone 8.0 のデバイス管理のセットアップ](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Windows Phone の管理をセットアップする](set-up-windows-phone-management-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


