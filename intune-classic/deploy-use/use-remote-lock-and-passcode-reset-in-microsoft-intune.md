---
title: "リモート ロックとパスコードのリセット"
description: "Intune には、リモート ロック機能とパスコードのリセット機能の両方が備わっています。"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.custom: intune-classic
ms.openlocfilehash: fc1cad418904de335b434a3726e2772d0558b303
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>リモート ロックとパスコードのリセットによってデバイスを保護する

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune には、リモート ロック機能とパスコードのリセット機能が備わっています。

## <a name="lock-a-device-remotely"></a>デバイスのリモート ロック
ユーザーがデバイスを紛失した場合は、リモートでデバイスをロックできます。 リモート ロックを利用するには、PIN またはパスコードをデバイスに設定しておく必要があります。

次の表に、各モバイル プラットフォームのリモート ロックの動作を示します。

|プラットフォーム|リモート ロック|
|------------|---------------|
|macOS|サポートされていません|
|iOS|サポートされています|
|Android|サポート|
|Android for Work|サポート|
|Windows 10 (モバイル)|サポート|
|Windows 10 (デスクトップ)|サポートされていません|
|Windows Phone 8 および Windows Phone 8.1|サポート|
|Windows RT 8.1 および Windows RT|デバイスの現在のユーザーが、デバイスを登録したユーザーと同じ場合にはサポートされます。|
|Windows 8.1|デバイスの現在のユーザーが、デバイスを登録したユーザーと同じ場合にはサポートされます。|

リモート ロックは、Intune ソフトウェア クライアントに登録されている Windows PC ではサポートされません。

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>Intune コンソールを使用してモバイル デバイスをリモートでロックする

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[すべてのデバイス]** &gt; **[すべてのモバイル デバイス]** を選択します。

2.  Intune に登録されているデバイスの場合は **[ダイレクト管理されているすべてのデバイス]**、それ以外の場合は **[Exchange ActiveSync で管理されているすべてのデバイス]** を選択します。

    > [!TIP]
    > 各ユーザーのデバイスを選択することもできます。 **[すべてのユーザー]** を選択します。 ユーザーの [プロパティ] ページで、**[デバイス]** を選択して、ロックするモバイル デバイスの名前を選択します。

3.  一覧で、ロックするデバイスを選択します (複数も可)。 タスク バーで、**[リモート タスク]** をクリックして、**[リモート ロック]** を選択します。

## <a name="reset-the-passcode-on-a-device"></a>デバイスのパスコードをリセットします。
ユーザーがパスコードを忘れた場合、デバイスからパスコードを削除したり、デバイスに新しい一時的なパスコードを強制したりすることができます。 以下の表は、各モバイル プラットフォームでパスコードをリセットしたときの動作です。

|プラットフォーム|パスコードのリセット|
|------------|------------------|
|macOS|サポートされていません|
|iOS|デバイスからパスコードをクリアする場合にサポートされます。 新しい一時的なパスコードは作成されません。|
|Android|Android 7.0 より前のバージョンでサポートされます。 一時的なパスコードを作成します。|
|Android for Work|サポートされていません|
|Windows 10 Mobile|Azure AD に参加している、Windows 10 Creator バージョン以降のモバイル デバイスでサポートされます。|
|Windows Phone 8 および Windows Phone 8.1|サポート|
|Windows RT 8.1|サポートされません|
|Windows 8.1|サポートされません|
|Windows 10 Desktop|サポートされません|

パスコード リセットは、Intune ソフトウェア クライアントに登録されている Windows PC ではサポートされません。

### <a name="reset-a-passcode"></a>パスコードのリセット

1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[グループ]** &gt; **[すべてのデバイス]** &gt; **[すべてのモバイル デバイス]** を選択します。

2.  Intune に登録されているデバイスの場合は **[ダイレクト管理されているすべてのデバイス]**、それ以外の場合は **[Exchange ActiveSync で管理されているすべてのデバイス]** を選択します。

    > [!TIP]
    > 各ユーザーのデバイスを選択することもできます。 **[すべてのユーザー]** をクリックします。 ユーザーの [プロパティ] ページで、**[デバイス]** をクリックして、ワイプするモバイル デバイスの名前をクリックします。

3.  一覧で、ロックするデバイスを選択します (複数も可)。 タスク バーで、**[リモート タスク]** をクリックして、**[パスコードのリセット]** を選択します。


### <a name="see-also"></a>関連項目
[デバイスをインベントリから削除する](retire-devices-from-microsoft-intune-management.md)および[Windows のデバイス データ管理の選択的ワイプ](http://technet.microsoft.com/library/dn486874.aspx)
