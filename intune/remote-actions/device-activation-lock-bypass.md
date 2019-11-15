---
title: Intune での iOS アクティベーション ロックをバイパスする
titleSuffix: Microsoft Intune
description: Intune を使用して、iOS アクティベーション ロックをバイパスし、ロックされたデバイスにアクセスする方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02d0fb91df07d8bba233a6f814ffcf36d408e95d
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712365"
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Intune で、監視されている iOS デバイス上のアクティベーション ロックをバイパスする


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune では、iOS 8.0 以降向けの iPhone を探すアプリの機能である iOS のアクティブ化ロックを管理できます。 iPhone を探すアプリをユーザーがデバイスで開くと、アクティブ化ロックが自動的に有効になります。 有効になると、ユーザーの Apple ID とパスワードを入力しない限り、以下の操作を実行できなくなります。

- iPhone を探すアプリをオフにする
- デバイスを消去する
- ディスクを再アクティブ化する

## <a name="how-activation-lock-affects-you"></a>アクティブ化ロックの影響

アクティベーション ロックにより、iOS デバイスをセキュリティで保護でき、紛失や盗難にあったデバイスが戻ってくる可能性が高まりますが、この機能は IT 管理者にさまざまな課題をもたらすことがあります。 次に例を示します。

- あるユーザーがデバイスでアクティブ化ロックを設定します。 その後、そのユーザーが退職し、デバイスを返却します。 ユーザーの Apple ID とパスワードがわからなければ、デバイスを再アクティブ化する方法がありません。
- アクティベーション ロックが有効になっているすべてのデバイスのレポートが必要です。
- 組織でデバイスを更新するときに、一部のデバイスを別の部門に再割り当てする必要があります。 その際に再割り当てできるのは、アクティベーション ロックが有効になっていないデバイスに限られます。

こうした問題を解決するために、Apple は iOS 7.1 でアクティブ化ロックのバイパスを導入しました。 アクティベーション ロックのバイパスにより、ユーザーの Apple ID とパスワードがなくても、監視対象のデバイスのアクティベーション ロックを解除することができます。 監視対象のデバイスでは、デバイス固有のアクティブ化ロックのバイパス コードを生成できます。このコードは、Apple のアクティブ化サーバーに格納されます。

>[!TIP]
>iOS デバイスの監視モードでは、Apple Configurator を使用して、デバイスをロックダウンし、特定のビジネス目的に必要な機能のみに制限することができます。 監視モードは、会社所有のデバイス専用の機能です。

アクティベーション ロックについては、[Apple の Web サイト](https://support.apple.com/HT201365)をご覧ください。

## <a name="how-intune-helps-you-manage-activation-lock"></a>Intune でアクティブ化ロックを管理する方法
Intune では、iOS 8.0 以降を実行している監視対象デバイスのアクティブ化ロックの状態を要求できます。 監視対象のデバイスのみの場合、Intune では、アクティベーション ロックのバイパス コードを取得し、直接デバイスに発行できます。 デバイスがワイプされている場合は、空のユーザー名とコードをパスワードとして使用し、デバイスに直接アクセスすることができます。

**Intune を使用してアクティベーション ロックを管理するビジネス上の利点は次のとおりです。**

- ユーザーが iPhone を探すアプリのセキュリティ上のメリットを受けることができる。
- デバイスを再利用する必要がある場合に、デバイスをインベントリから削除することや、ロック解除できることを把握したうえで、ユーザーが業務を遂行できるようにすることができる。

## <a name="before-you-start"></a>開始する前に
デバイスのアクティベーション ロックをバイパスするには、次の手順に従って先にそれを有効にする必要があります。

1. [デバイスの制限設定を構成する方法](/intune-azure/configure-devices/how-to-configure-device-restrictions)に関するページにある情報を使用して、iOS 用の Intune デバイス制限プロファイルを構成します。
2. [iOS のデバイス制限設定](../configuration/device-restrictions-ios.md)の **[全般]** 設定で、 **[アクティベーション ロック]** オプションを有効にします。
3. プロファイルを保存し、アクティベーション ロックのバイパスを管理するデバイスに[割り当て](../configuration/device-profile-assign.md)ます。


## <a name="how-to-use-activation-lock-bypass"></a>アクティベーション ロックのバイパスの使用方法

>[!IMPORTANT]
>デバイス上でアクティベーション ロックをバイパスした後に、iPhone を探すアプリを起動すると、新しいアクティベーション ロックが自動的に適用されます。 そのため、**デバイスが実際に手元にある状態で、この手順を実行してください。**

Intune の **[アクティベーション ロックのバイパス]** のリモート デバイス操作では、ユーザーの Apple ID とパスワードを要求することなく iOS デバイスのアクティベーション ロックを解除します。 アクティベーション ロックをバイパスした後に iPhone を探すアプリを起動すると、デバイスのアクティベーション ロックが再度有効になります。 デバイスに物理的にアクセスできる場合にのみアクティベーション ロックをバイパスしてください。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[Intune]** ブレードで、 **[デバイス]** を選択します。
4. **[デバイス]** ブレードで、 **[すべてのデバイス]** を選択します。
5. 管理対象のデバイスの一覧で、 **[アクティベーション ロックのバイパス]** デバイス リモート操作を選択します。
6. デバイスの [ハードウェア] セクションに移動し、 **[条件付きアクセス]** の下の **[アクティベーション ロックのバイパス コード]** の値をコピーします。

    >[!NOTE]
    >デバイスをワイプする前にバイパス コードをコピーします。 コードをコピーする前にデバイスの設定をリセットすると、Azure からコードが削除されます。

7. デバイスの **[概要]** ブレードに移動し、 **[ワイプ]** を選択します。
8. デバイスをリセットすると、*Apple ID* と *パスワード*を入力するように求められます。 *[ID]* フィールドは空白のままとし、"*パスワード*" の**バイパス コード**を入力します。 これにより、デバイスからアカウントが削除されます。 


## <a name="next-steps"></a>次の手順

**[デバイスの管理]** ワークロード内のデバイスの詳細ページで、ロック解除要求の状態を確認できます。
