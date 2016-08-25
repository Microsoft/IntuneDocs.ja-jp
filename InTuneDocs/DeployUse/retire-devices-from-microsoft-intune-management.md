---
title: "デバイスをインベントリから削除する | Microsoft Intune"
description: "Intune では、デバイスのポリシーとポータル サイトを削除することによって Intune の管理対象からデバイスを削除する選択的ワイプとフル ワイプの両方をサポートします。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7bea7ba4ef59c6b1400414b59456e19dc1c152fb
ms.openlocfilehash: ad5e9453f8132d383f8c23886e48505769c7f44b


---

# Intune の管理からデバイスを削除する

会社所有のデバイスであっても個人所有のデバイスであっても、デバイスを Intune の管理対象から削除することが必要となる場合があります。 デバイスを管理対象から除外するのは比較的簡単です。 モバイル デバイスとして管理されているデバイスで、選択的ワイプまたはフル ワイプを実行できます。 また、Intune クライアント ソフトウェアで管理されている PC を削除することもできます。

## デバイスからデータとアプリをワイプする
選択的ワイプとフル ワイプではいずれも、デバイスのポリシーとポータル サイトを削除することによって、Intune の管理対象からデバイスを削除します。それによって、デバイスには Microsoft SharePoint、電子メール、Office 365 などの会社のリソースにログオンするために必要な資格情報がなくなります。

[選択的ワイプ](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)は、デバイス上の個人情報には影響を与えないため、従業員が Intune に個人のデバイスを登録している場合にお勧めの方法です。 会社のデータだけが削除されます。

他の目的に再利用する必要のあるデバイスの場合、デバイスを工場出荷時の既定の設定にリセットする[フル ワイプ](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)も使用できます。

## Azure Active Directory ポータルでデバイスを削除するには

1.  組織の資格情報で [http://aka.ms/accessaad](http://aka.ms/accessaad) または [https://portal.office.com](https://portal.office.com) にログインし、**[管理センター]** &gt; **[Azure AD]** の順に選択します。

2.  組織 ID がない場合は、Azure サブスクリプションを作成します。 有料アカウントを持っている場合は、作成時にクレジット カードや支払いは必要ありません (**[無料の Azure Active Directory の登録]** サブスクリプション リンクを選択します)。

4.   **[Active Directory]** を選択し、組織を選択します。

5.   **[ユーザー]** タブを選択します。

6.  削除するデバイスのユーザーを選択します。

7.  **[デバイス]** を選択します。

8.  対象のデバイスを選択して、**[デバイスの削除]** を選択します。 Active Directory との次の同期時にデバイスが削除されます。 通常は 4 時間内に行われます。 同期の後、デバイスは管理から削除されます。 これにより、そのユーザーのデバイス制限から 1 つのデバイスが削除されます。

## 管理対象コンピューターを削除する
Intune クライアント ソフトウェアによって管理されているコンピューターを、Intune 管理コンソールで管理から削除できます。 これにより、コンピューターからのクライアント ソフトウェアのアンインストールと Intune ポリシーの削除も行われます。 [Intune クライアント ソフトウェアで管理されているコンピューターの削除](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md)に関する情報を参照してください。

## デバイスへのアクセスをブロックする
デバイスを紛失した場合、または社員が会社所有のハードウェアを返却しないで退職したためにデバイスを削除する必要がある場合は、デバイスの[パスコードをリセットしてリモートでロック](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)することもできます。 これにより、会社の情報の不正使用を防止できます。ただし、デバイスを損失として会計処理することが必要な場合があります。

また、その従業員の Intune のユーザー アカウントからライセンスを失効させる必要もあります。 これにより、ライセンスが解放され、そのライセンスを新しいユーザー アカウントに割り当てることができます。

## ハードウェアをインベントリから削除する
デバイス自体の寿命が訪れることがあります。 その場合は、フル ワイプによってデバイスを[工場出荷時の設定にリセット](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)して、すべてのデータを削除し、Intune からデバイスを削除します。 その後は、会社のポリシーに従って、ハードウェアを処分できます。

### 関連項目
[フル ワイプまたは選択的ワイプを使用してデータを保護する](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Aug16_HO2-->


