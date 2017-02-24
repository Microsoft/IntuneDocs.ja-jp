---
title: "デバイスをインベントリから削除する | Microsoft Docs"
description: "Intune では、デバイスのポリシーとポータル サイトを削除することによって Intune の管理対象からデバイスを削除する選択的ワイプとフル ワイプの両方をサポートします。"
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 00e9dfd165a449182c5b937372db7085c981c68f
ms.openlocfilehash: cca12024ba12cff5cdb8c515f7719a7592ba97ea


---

# <a name="retire-devices-from-intune-management"></a>Intune の管理からデバイスを削除する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

会社所有のデバイスであっても個人所有のデバイスであっても、デバイスを Intune の管理対象から削除することが必要となる場合があります。

デバイスが一定期間 Intune サービスに接続されていない場合でも、ユーザーが手動で削除しなければ、Intune からデバイスが削除されることはありません。

デバイスの削除が必要になる理由はさまざまです。

-    ユーザーが予定どおりに退社する ("管理された" 退職)
-    ユーザーが急に退社する (解雇や辞職など)
-    デバイスの紛失
-    デバイスの用途変更 (別のユーザーへの移譲、異なる目的での再使用など)

モバイル デバイスとして管理されているデバイスで選択的ワイプまたはフル ワイプを実行することも、デバイスをロックしてパスワードをリセットすることもできます。 デバイスをワイプすると、ユーザーのサブスクリプションを解放して別のデバイスを追加することができます。 また、Intune クライアント ソフトウェアの管理対象 PC も削除できます。

## <a name="wipe-data-and-apps-from-devices"></a>デバイスからデータとアプリをワイプする
選択的ワイプとフル ワイプは、デバイスのポリシーとポータル サイトを削除することによって Intune の管理対象からデバイスを削除します。 その結果、デバイスには Microsoft SharePoint、電子メール、Office 365 などの会社リソースへのサインインに必要な資格情報がなくなります。

[選択的ワイプ](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)は、デバイス上の個人情報には影響を与えないため、従業員が Intune に個人のデバイスを登録している場合にお勧めの方法です。 会社のデータだけが削除されます。

他の目的に再利用する必要のあるデバイスの場合、デバイスを工場出荷時の既定の設定にリセットする[フル ワイプ](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)も使用できます。

### <a name="removing-user-licenses-and-managed-devices"></a>ユーザー ライセンスと管理対象デバイスを削除する
ユーザー ライセンスを削除する場合は、そのユーザーの登録済みデバイスの登録を停止します。 ベスト プラクティスとして、選択的ワイプを使用して、ユーザーの Intune ライセンスを削除する前に、管理対象デバイスから会社のデータを削除する必要があります。 ユーザー ライセンスを削除すると、デバイスをリモート アクションのターゲットにすることはできません。

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Azure Active Directory ポータルでデバイスを削除するには

1.  組織の資格情報で [http://aka.ms/accessaad](http://aka.ms/accessaad) または [https://portal.office.com](https://portal.office.com) にサインインし、**[管理センター]** &gt; **[Azure AD]** の順に選択します。

2.  組織 ID がない場合は、Azure サブスクリプションを作成します。 有料アカウントがある場合、クレジット カードや支払いは不要です。 **[Register your free Azure Active Directory]** (無料 Azure Active Directory に登録) サブスクリプション リンクを選択します。

4.  **[Active Directory]** を選択し、組織を選択します。

5.  **[ユーザー]** タブを選択します。

6.  削除するデバイスのユーザーを選択します。

7.  **[デバイス]** を選択します。

8.  対象のデバイスを選択して、**[デバイスの削除]** を選択します。 Active Directory との次の同期時にデバイスが削除されます。 通常は&4; 時間内に行われます。 同期の後、デバイスは管理から削除されます。 これにより、そのユーザーのデバイス制限から&1; つのデバイスが削除されます。

## <a name="retire-managed-computers"></a>管理対象コンピューターを削除する
Intune クライアント ソフトウェアによって管理されているコンピューターを、Intune 管理コンソールで管理から削除できます。 これにより、コンピューターからのクライアント ソフトウェアのアンインストールと Intune ポリシーの削除も行われます。 [Intune クライアント ソフトウェアで管理されているコンピューターの削除](retire-a-windows-pc-with-microsoft-intune.md)に関する情報を参照してください。

## <a name="block-access-a-device"></a>デバイスへのアクセスをブロックする
デバイスを紛失した場合、または社員が会社所有のハードウェアを返却しないで退職したためにデバイスを削除する必要がある場合は、デバイスの[パスコードをリセットしてリモートでロック](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)することもできます。 これにより、会社の情報の不正使用を防止できます。ただし、デバイスを損失として会計処理することが必要な場合があります。

また、その従業員の Intune のユーザー アカウントからライセンスを失効させる必要もあります。 これにより、ライセンスが解放され、そのライセンスを新しいユーザー アカウントに割り当てることができます。

## <a name="retire-hardware"></a>ハードウェアをインベントリから削除する
デバイス自体の寿命が訪れることがあります。 その場合は、フル ワイプによってデバイスを[工場出荷時の設定にリセット](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)して、すべてのデータを削除し、Intune からデバイスを削除します。 その後は、会社のポリシーに従って、ハードウェアを処分できます。

### <a name="see-also"></a>関連項目
[フル ワイプまたは選択的ワイプを使用してデータを保護する](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Feb17_HO2-->


