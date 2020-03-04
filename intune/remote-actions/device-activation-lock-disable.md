---
title: Intune で iOS/iPadOS アクティベーション ロックをバイパスする
titleSuffix: Microsoft Intune
description: Intune を使用して、iOS/iPadOS アクティベーション ロックをバイパスし、ロックされたデバイスにアクセスする方法を説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
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
ms.openlocfilehash: af5bb1c95a15a5c52585278605e2f7a86307cb76
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782226"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>Intune を使用して監視されている iOS/iPadOS デバイス上のアクティベーション ロックを無効にする


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune は、iOS/iPadOS 8.0 以降のデバイスの [iPhone を探す] アプリの機能である、iOS/iPadOS のアクティベーション ロックを管理するのに役立ちます。 iPhone を探すアプリをユーザーがデバイスで開くと、アクティブ化ロックが自動的に有効になります。 有効になると、ユーザーの Apple ID とパスワードを入力しない限り、以下の操作を実行できなくなります。

- iPhone を探すアプリをオフにする
- デバイスを消去する
- ディスクを再アクティブ化する

## <a name="how-activation-lock-affects-you"></a>アクティブ化ロックの影響

アクティベーション ロックにより、iOS/iPadOS デバイスをセキュリティで保護でき、紛失や盗難にあったデバイスが戻ってくる可能性が高まりますが、この機能は IT 管理者にさまざまな課題をもたらすことがあります。 次に例を示します。

- あるユーザーがデバイスでアクティブ化ロックを設定します。 その後、そのユーザーが退職し、デバイスを返却します。 ユーザーの Apple ID とパスワードがわからなければ、デバイスを再アクティブ化する方法がありません。
- アクティベーション ロックが有効になっているすべてのデバイスのレポートが必要です。
- 組織でデバイスを更新するときに、一部のデバイスを別の部門に再割り当てする必要があります。 その際に再割り当てできるのは、アクティベーション ロックが有効になっていないデバイスに限られます。

こうした問題を解決するために、Apple は iOS/iPadOS 7.1 でアクティベーション ロックの無効化を導入しました。 アクティベーション ロックの無効化により、ユーザーの Apple ID とパスワードがなくても、監視対象のデバイスのアクティベーション ロックを解除することができます。 監視対象のデバイスでは、デバイス固有のアクティブ化ロックのバイパス コードを生成できます。このコードは、Apple のアクティブ化サーバーに格納されます。

>[!TIP]
>iOS/iPadOS デバイスの監視モードでは、Apple Configurator を使用して、デバイスをロックダウンし、機能を特定のビジネス目的に必要なもののみに制限することができます。 監視モードは、会社所有のデバイス専用の機能です。

アクティベーション ロックについては、[Apple の Web サイト](https://support.apple.com/HT201365)をご覧ください。

## <a name="how-intune-helps-you-manage-activation-lock"></a>Intune でアクティブ化ロックを管理する方法
Intune では、iOS/iPadOS 8.0 以降を実行している監視対象デバイスに対してアクティベーション ロックの状態を要求できます。 監視対象のデバイスのみの場合、Intune では、アクティベーション ロックの無効化コードを取得し、直接デバイスに発行できます。 デバイスがワイプされている場合は、空のユーザー名とコードをパスワードとして使用し、デバイスに直接アクセスすることができます。

**Intune を使用してアクティベーション ロックを管理するビジネス上の利点は次のとおりです。**

- ユーザーが iPhone を探すアプリのセキュリティ上のメリットを受けることができる。
- デバイスを再利用する必要がある場合に、デバイスをインベントリから削除することや、ロック解除できることを把握したうえで、ユーザーが業務を遂行できるようにすることができる。

## <a name="before-you-start"></a>開始する前に
デバイスのアクティベーション ロックを無効にするには、次の手順に従って先にそれを有効にする必要があります。

1. [デバイスの制限設定を構成する方法](/intune-azure/configure-devices/how-to-configure-device-restrictions)に関する記事に記載されている情報を使用して、iOS/iPadOS 用の Intune デバイス制限プロファイルを構成します。
2. [iOS/iPadOS のデバイス制限設定](../configuration/device-restrictions-ios.md)の **[全般]** 設定で、 **[アクティベーション ロック]** オプションを有効にします。
3. プロファイルを保存し、アクティベーション ロックの無効化を管理するデバイスに[割り当て](../configuration/device-profile-assign.md)ます。


## <a name="how-to-use-disable-activation-lock"></a>アクティベーション ロックの無効化を使用する方法

>[!IMPORTANT]
>デバイス上でアクティベーション ロックを無効にした後に、iPhone を探すアプリを起動すると、新しいアクティベーション ロックが自動的に適用されます。 そのため、**デバイスが実際に手元にある状態で、この手順を実行してください。**

Intune の **[アクティベーション ロックの無効化]** リモート デバイス アクションを実行すると、ユーザーの Apple ID とパスワードを要求することなく iOS/iPadOS デバイスのアクティベーション ロックが解除されます。 アクティベーション ロックを無効にした後に iPhone を探すアプリを起動すると、デバイスのアクティベーション ロックが再度有効になります。 デバイスに物理的にアクセスできる場合にのみアクティベーション ロックを無効にしてください。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
3. **[Intune]** ブレードで、 **[デバイス]** を選択します。
4. **[デバイス]** ブレードで、 **[すべてのデバイス]** を選択します。
5. 管理対象のデバイスの一覧で、 **[Disable Activation Lock]\(アクティベーション ロックを無効にする\)** デバイス リモート操作を選択します。
6. デバイスの [ハードウェア] セクションに移動し、 **[条件付きアクセス]** の下の **[アクティベーション ロックのバイパス コード]** の値をコピーします。

    >[!NOTE]
    >デバイスをワイプする前にバイパス コードをコピーします。 コードをコピーする前にデバイスの設定をリセットすると、Azure からコードが削除されます。

7. デバイスの **[概要]** ブレードに移動し、 **[ワイプ]** を選択します。
8. デバイスをリセットすると、*Apple ID* と *パスワード*を入力するように求められます。 *[ID]* フィールドは空白のままとし、"*パスワード*" の**バイパス コード**を入力します。 これにより、デバイスからアカウントが削除されます。 


## <a name="next-steps"></a>次のステップ

**[デバイスの管理]** ワークロード内のデバイスの詳細ページで、ロック解除要求の状態を確認できます。
