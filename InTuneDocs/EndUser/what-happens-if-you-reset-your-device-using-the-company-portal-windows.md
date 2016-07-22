---
title: "ポータル サイトを使用してデバイスをリセットするとどうなるか | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ee6e275-d1ec-4da3-bbef-d5da2c61a02a
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 39e810466d3a98789f0f1338f68d2be80d757d39
ms.openlocfilehash: 9ff73d6e2066b0fb3d2e8ca9d7732d4685e258fd


---


# ポータル サイトを使用してデバイスをリセットするとどうなるか

ポータル サイト アプリや[ポータル サイト Web サイト](reset-your-device-cpwebsite.md)を使用して Windows デバイスをリセットすると、デバイスが工場出荷時設定にリセットされ、アプリケーション、設定、お客様の個人データを含むデータがすべて削除されます。 次の表に示すように、各デバイスでの操作結果は、デバイスの種類とその使用方法によって異なります。 紛失または盗難にあったデバイスをリセットする方法の手順については、「[紛失したまたは盗難にあったデバイスをリセット (消去) する](reset-erase-your-lost-or-stolen-device-windows.md)」を参照してください。

|デバイスの構成と管理|デバイスの種類|
|---------------------------------------|---------------|
|IT 管理者がモバイル デバイスを管理している|**Windows 10、Windows Phone 8.1、および Windows Phone 8**</br>デバイスはポータル サイトに表示されなくなります。また、ポータル サイトはデバイスを製造元の既定の設定にリセットしようとします。 個人のデータ、アプリケーション、および設定は削除されます。 <br /><br />**Windows 10 Mobile**: デバイスの登録を解除するには、リセットを実行する必要があります。<br /><br />**Windows RT**<br />Windows RT デバイスは、電子メール専用の場合を除き、リセットできません。|
|デバイスは会社の電子メールのみにアクセスできる|**Windows Phone 8.1 および Windows Phone 8**<br />デバイスはポータル サイトに表示されなくなります。また、会社のメール アカウントは削除され、保存されていないメールは削除されます。<br /><br />**Windows RT**<br />デバイスはポータル サイトに表示されなくなります。また、会社のメール アカウントは削除され、保存されていないメールは削除されます。<br /><br />**Windows 7 または Windows Vista コンピューター**<br />電子メール専用で Windows 7 以前を実行しているコンピューターはリセットできません。<br /><br />**Windows 8.1 および Windows 8 コンピューター**<br />デバイスはポータル サイトに表示されなくなります。また、会社のメール アカウントは削除され、保存されていないメールは削除されます。|
|PC およびラップトップ|**Windows 8.1 および Windows 8 コンピューター**<br />電子メール専用で Windows 8 または Windows 8.1 を実行しているコンピューターはリセットできません。<br /><br />**Windows 7 または Windows Vista コンピューター**<br />Windows 7 以前を実行しているコンピューターはリセットできません。|

ご質問がございましたら、IT 管理者に問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](http://portal.manage.microsoft.com)をご確認ください。

### 関連項目
[Windows デバイスを Intune で使用する](using-your-windows-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


