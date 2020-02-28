---
title: Microsoft Intune でのデバイス アクションのトラブルシューティング - Azure | Microsoft Docs
description: デバイス アクションに関する問題のトラブルシューティングに役立つ情報を提供します。
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
ms.openlocfilehash: 545f287e8b7ee82e2008f239171b22e01714b8c7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514746"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Intune でのデバイス アクションのトラブルシューティング

Microsoft Intune には、マネージド デバイスに役立つ多くの操作があります。 この記事では、デバイス アクションのトラブルシューティングに役立つ、一般的な質問に対する回答を示します。

## <a name="disable-activation-lock-action"></a>アクティベーション ロック アクションを無効にする

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>ポータルで [Disable Activation Lock]\(アクティベーション ロックを無効にする\) アクションをクリックしましたが、デバイスでは何も起こりません。
これは通常の動作です。 [Disable Activation Lock]\(アクティベーション ロックを無効にする\) アクションを開始すると、Intune は Apple から更新されたコードを要求されます。 デバイスがアクティベーション ロック画面になったら、パスコード フィールドにコードを手動で入力します。 このコードの有効期間は 15 日間のみです。ワイプを発行する前に、必ずアクションをクリックしてコードをコピーしてください。

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-iosipados-device"></a>iOS/iPadOS デバイスの [Hardware overview]\(ハードウェアの概要\) ブレードに [Disable Activation Lock]\(アクティベーション ロックを無効にする\) コードが表示されないのはなぜですか?
最も可能性の高い理由は次のとおりです。
- コードの有効期限が切れており、サービスからクリアされている。
- デバイスが、アクティベーション ロックを許可するデバイスの制限ポリシーを使用して監視されていない。

Graph Explorer では、次のクエリを使用してコードを確認できます。

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-iosipados-device"></a>iOS/iPadOS デバイスで [Disable Activation Lock]\(アクティベーション ロックを無効にする\) アクションがグレー表示されるのはなぜですか?
最も可能性の高い理由は次のとおりです。 
- コードの有効期限が切れており、サービスからクリアされている。
- デバイスが、アクティベーション ロックを許可するデバイスの制限ポリシーを使用して監視されていない。

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>[Disable Activation Lock]\(アクティベーション ロックを無効にする\) のコードは大文字と小文字が区別されますか?
いいえ。 また、ダッシュを入力する必要はありません。

## <a name="remove-devices-action"></a>デバイスの削除アクション

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>インベントリから削除またはワイプを開始したユーザーを特定するにはどうすればよいですか?
[Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) で、**[テナント管理]** > **[監査ログ]** に移動し、**[開始者]** 列を確認します。
エントリが表示されない場合、アクションを開始した可能性が最も高いユーザーは、デバイスのユーザーです。 ポータル サイト アプリまたは portal.manage.microsoft.com を使用した可能性があります。

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>[インベントリから削除] の使用後にアプリケーションがアンインストールされなかったのはなぜですか?
マネージド アプリケーションとは見なされなかったためです。 この状況で、マネージド アプリケーションとは、Intune サービスを使用してインストールされたアプリケーションです。 以下は、必要な操作の例です。
- アプリは "必須" として展開されました
- アプリは "使用可能" として展開され、ポータル サイト アプリ内からエンド ユーザーによってインストールされました。

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Android Enterprise 仕事用プロファイル デバイスで [ワイプ] がグレー表示されるのはなぜですか?
これは通常の動作です。 Google では、MDM プロバイダーから仕事用プロファイル デバイスを工場出荷時設定にリセットすることは許可されていません。

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>デバイスをインベントリから削除した後も Office アプリにサインインできるのはなぜですか?
デバイスをインベントリから削除しても、アクセス トークンは失効しないためです。 条件付きアクセス ポリシーを使用して、この状況を軽減できます。

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>発行後のインベントリから削除またはワイプ アクションを監視するにはどうすればよいですか?
[Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) で、**[テナントの管理]** > **[監査ログ]** に移動します。

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>ワイプを実行すると "保留中" といつまでも表示されることがあるのはなぜですか?
リセットが開始される前に、常にデバイスから Intune サービスに状態が報告されるとは限りません。 そのため、アクションは "保留中" と表示されます。 アクションが成功したことを確認したら、デバイスをサービスから削除してください。

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>オフラインのデバイス、またはサービスとしばらく通信していないデバイス上で、インベントリから削除またはワイプを開始するとどうなりますか?
デバイスは、MDM 証明書の有効期限が切れるまで "**インベントリから削除またはワイプの保留中**" 状態のままになります。 MDM 証明書は登録から 1 年間有効であり、毎年自動的に更新されます。 MDM 証明書の有効期限が切れる前にデバイスがチェックインされると、デバイスはインベントリから削除またはワイプされます。 MDM 証明書の有効期限が切れる前にデバイスがチェックインされない場合は、サービスにチェックインできなくなります。 MDM 証明書の有効期限が切れてから 180 日後に、デバイスは Azure portal から自動的に削除されます。


## <a name="reset-passcode-action"></a>パスコードのリセット アクション

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Android デバイス管理者が登録したデバイス上で [パスコードのリセット] アクションがグレー表示されるのはなぜですか?
ランサム ウェアに対抗するため、Google は Device Admin API のパスコードのリセット機能を削除しました (Android バージョン 7.0 以降のデバイスに適用されます)。

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Android 8.0 以降の仕事用プロファイルに登録されたデバイスにパスコード リセットを発行すると、"サポートされていません" というメッセージが表示されるのはなぜですか?
リセット トークンがデバイスでアクティブ化されていないためです。 リセット トークンをアクティブにするには:
1. 構成ポリシーに作業プロファイルのパスコードが必要です。
2. エンド ユーザーは、適切な作業プロファイルのパスコードを設定する必要があります。
3. エンド ユーザーは、2 つ目のプロンプトに同意してパスコードのリセットを許可する必要があります。
これらの手順が完了すると、この応答を受け取らなくなります。

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-iosipados-device-when-i-issue-the-remove-passcode-action"></a>パスコードの削除アクションを発行すると、iOS/iPadOS デバイス上で新しいパスコードを設定するように求められるのはなぜですか?
コンプライアンス ポリシーのいずれかでパスコードが必須のためです。


## <a name="wipe-action"></a>ワイプ アクション

### <a name="i-cant-restart-a-windows-10-device-after-using-the-wipe-action"></a>ワイプ操作を使用した後で Windows 10 デバイスを再起動できません
このようになる可能性があるのは、**[デバイスをワイプして、デバイスの電源が切れてもワイプを続行します。このオプションを選択すると、一部の Windows 10 デバイスが再起動しなくなる可能性があることに注意してください。]**  を、Windows 10 デバイスで選択した場合です。

これは、Windows のインストールにオペレーティング システムの再インストールが妨げられるような重大な破損がある場合に、発生する可能性があります。 そのような場合、プロセスは失敗し、システムは [Windows 回復環境]( https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)のままになります。

### <a name="i-cant-restart-a-bitlocker-encrypted-device-after-using-the-wipe-action"></a>ワイプ操作を使用した後、BitLocker で暗号化されたデバイスを再起動できません
このようになる可能性があるのは、**[デバイスをワイプして、デバイスの電源が切れてもワイプを続行します。このオプションを選択すると、一部の Windows 10 デバイスが再起動しなくなる可能性があることに注意してください。]**  オプションを、BitLocker で暗号化されたデバイスで選択した場合です。

この問題を解決するには、起動可能なメディアを使用して、デバイスに Windows 10 を再インストールします。


## <a name="next-steps"></a>次のステップ

[Microsoft からサポート](../fundamentals/get-support.md)を受けるか、[コミュニティ フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)を使用します。
