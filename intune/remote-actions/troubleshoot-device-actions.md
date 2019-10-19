---
title: Microsoft Intune でのデバイス アクションのトラブルシューティング - Azure | Microsoft Docs
description: デバイスアクションに関する問題のトラブルシューティングに役立つ情報を入手します。
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96f6dc3d1a8f8589395cf49b3bb934adadf437a4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508498"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Intune でのデバイスの操作のトラブルシューティング

Microsoft Intune には、管理対象デバイスに役立つ多くの操作があります。 この記事では、デバイスアクションのトラブルシューティングに役立つ一般的な質問に対する回答を示します。

## <a name="bypass-activation-lock-action"></a>アクティベーション ロック アクションをバイパスする

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>ポータルで [バイパスアクティベーションロック] アクションをクリックしましたが、デバイスに何も発生していません。
これは想定されています。 バイパスアクティベーションロックアクションを開始した後、Intune は Apple から更新されたコードを要求します。 デバイスがアクティベーションロック画面に表示された後に、コードをパスコードフィールドに手動で入力します。 このコードは15日間のみ有効であるため、ワイプを発行する前に、アクションをクリックしてコードをコピーしてください。

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>IOS デバイスの [ハードウェアの概要] ブレードに、バイパスアクティベーションロックコードが表示されないのはなぜですか。
最も可能性の高い理由は次のとおりです。
- コードの有効期限が切れており、サービスからクリアされています。
- デバイスは、アクティベーションロックを許可するためにデバイスの制限ポリシーを使用して監視されていません。

Graph Explorer では、次のクエリを使用してコードを確認できます。

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>IOS デバイスで [バイパスアクティベーションロック] アクションがグレーで表示されるのはなぜですか。
最も可能性の高い理由は次のとおりです。 
- コードの有効期限が切れており、サービスからクリアされています。
- デバイスは、アクティベーションロックを許可するためにデバイスの制限ポリシーを使用して監視されていません。

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>バイパスアクティベーションロックコードの大文字と小文字は区別されますか。
いいえ。 また、ダッシュを入力する必要はありません。

## <a name="remove-devices-action"></a>デバイスの削除アクション

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>削除/ワイプを開始したユーザーを指定操作方法
[ **Intune**  > **デバイス** > **デバイスアクション**] にアクセスし、 **[開始者]** 列 > 確認します。
エントリが表示されない場合は、アクションを開始したユーザーがデバイスのユーザーである可能性があります。 ポータルサイトアプリまたは portal.manage.microsoft.com を使用したことがあります。

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>インベントリから削除した後にアプリケーションがアンインストールされなかったのはなぜですか。
マネージアプリケーションとは見なされませんでした。 このコンテキストでは、マネージアプリケーションは、Intune サービスを使用してインストールされたアプリケーションです。 以下は、必要な操作の例です。
- アプリは必須として展開されました
- アプリが利用可能として展開され、ポータルサイトアプリ内からエンドユーザーによってインストールされました。

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Android Enterprise Work Profile デバイスでワイプがグレー表示されるのはなぜですか。
これは通常の動作です。 Google では、MDM プロバイダーからの仕事用プロファイルデバイスの工場出荷時設定へのリセットは許可されていません。

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>デバイスをインベントリから削除した後に Office アプリにサインインするにはどうすればよいですか。
デバイスをインベントリから削除しても、アクセストークンは失効しません。 条件付きアクセスポリシーを使用して、この状況を軽減できます。

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>発行後のインベントリからの削除/ワイプアクションを監視するにはどうすればよいですか。
**Intune**  > **デバイス** >  デバイスの**操作**にアクセスします。

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>ワイプが無期限に保留中として表示される場合があるのはなぜですか。
デバイスは、リセットが開始される前に、状態が Intune サービスに報告されることはありません。 そのため、アクションは保留中として表示されます。 操作が成功したことを確認した場合は、サービスからデバイスを削除します。

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>オフラインデバイスまたはしばらくの間サービスと通信していないデバイスでインベントリからの削除/ワイプを開始するとどうなりますか。
デバイスは、MDM 証明書の有効期限が切れるまで、インベントリからの**削除/ワイプ保留**中の状態のままになります。 MDM 証明書は、登録から1年間継続し、毎年自動的に更新されます。 MDM 証明書の有効期限が切れる前にデバイスがチェックインされると、インベントリから削除またはワイプされます。 MDM 証明書の有効期限が切れる前にデバイスがチェックインされない場合、サービスにチェックインすることはできません。 180日の MDM 証明書の有効期限が切れると、デバイスは Azure portal から自動的に削除されます。


## <a name="reset-passcode-action"></a>パスコードのリセットアクション

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Android デバイス管理者が登録したデバイスで、パスコードのリセット操作がグレーで表示されるのはなぜですか。
Ransom ware を戦闘するために、Google はデバイス管理 API でパスコードリセット機能を削除しました (Android バージョン7.0 以上のデバイスに適用されます)。

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Android 8.0 以降の仕事用プロファイルに登録されているデバイスにパスコードのリセットを発行したときに "サポートされていない" というメッセージが表示されるのはなぜですか。
リセットトークンがデバイスでアクティブ化されていないためです。 リセットトークンをアクティブにするには:
1. 構成ポリシーで仕事用プロファイルのパスコードを要求する必要があります。
2. エンドユーザーは、適切な作業プロファイルのパスコードを設定する必要があります。
3. エンドユーザーは、パスコードのリセットを許可するために、セカンダリプロンプトを受け入れる必要があります。
これらの手順が完了すると、この応答を受信できなくなります。

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>パスコードの削除アクションを発行したときに、iOS デバイスで新しいパスコードを設定するように求めるメッセージが表示されるのはなぜですか。
コンプライアンスポリシーの1つはパスコードを必要とするためです。

## <a name="next-steps"></a>次の手順

[Microsoft からサポート](../fundamentals/get-support.md)を受けるか、[コミュニティ フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)を使用します。
