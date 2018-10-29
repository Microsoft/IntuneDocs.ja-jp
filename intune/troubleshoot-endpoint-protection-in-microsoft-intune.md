---
title: Intune での Endpoint Protection のトラブルシューティング - Azure | Microsoft Docs
description: Microsoft Intune Endpoint Protection の使用中に生じた問題を解決します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d8794345f22b2c19cf89eca2d3603fe8ac68161
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2018
ms.locfileid: "49643061"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Intune での Endpoint Protection のトラブルシューティング

Endpoint Protection の使用中に発生した問題を解決するには、この情報を参考にしてください。 [イベント ログとエラー コードを調べて Windows Defender AV での問題をトラブルシューティングする](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus)こともできます。

この情報を使っても問題が解決しない場合は、[Microsoft Intune のサポートを受ける](get-support.md)こともできます。

### <a name="error-messages"></a>エラー メッセージ
ここでは、以下のエラーと警告の考えられる原因と対処法を説明します。

|メッセージ|考えられる原因|対処法|
|---------------|--------------------|-----------------------|
|**Endpoint Protection エンジンを使用できません**|Intune Endpoint Protection エンジンが壊れているか、削除されています。|Intune Endpoint Protection エンジンが壊れている場合は、ソフトウェアの更新または再インストールを試みてください。<br /><br />直ちに更新するには、Endpoint Protection クライアント ソフトウェアの **[更新]** (マネージド コンピューターのタスク バーに表示されます) を選択します。<br /><br />Endpoint Protection エンジンを更新できない場合は、エンジンを再インストールする必要があります。<br /><br />マネージド コンピューターのコントロール パネルに一覧表示されるインストール済みプログラムから **[Microsoft Intune Endpoint Protection Agent]** を見つけて、アプリケーションをアンインストールします。<br /><br />次回更新プログラムを同期するときに、Microsoft Online Management 更新マネージャーが不足しているプログラムを検出し、スケジュールされているインストール時間にそのプログラムを再インストールします。|
|**Endpoint Protection が無効です**|管理者が構成プロファイルを使用して Intune Endpoint Protection を無効にしているか、マネージド コンピューターのユーザーが無効にしています。|Endpoint Protection を有効にします。 「[Intune でエンドポイント保護設定を追加する](endpoint-protection-configure.md)」または「[Windows Defender をオンにし、会社のリソースにアクセスする](/intune-user-help/turn-on-defender-windows)」をご覧ください。|
|**リアルタイム保護が無効です**|プロファイルを使用して管理者が、またはマネージド コンピューター上でユーザーが、リアルタイム保護を無効にしています。|Endpoint Protection を有効にします。 Intune での [Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)または[リアルタイム保護を有効にして会社のリソースにアクセスする方法](/intune-user-help/turn-on-defender-windows)に関する記事をご覧ください。 |
|**ダウンロードのスキャンは無効になっています**|プロファイルを使用して管理者が、またはマネージド コンピューター上でユーザーが、ダウンロードのスキャンを無効にしています。|スキャンを有効にします。 Intune での [Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)または[リアルタイム保護を有効にして会社のリソースにアクセスする方法](/intune-user-help/turn-on-defender-windows)に関する記事をご覧ください。 |
|**ファイルとプログラムの動作の監視は無効になっています**|プロファイルを使用して管理者が、またはマネージド コンピューター上でユーザーが、ファイルとプログラムの動作の監視を無効にしています。|ファイルとプログラムのアクティビティを有効にします。 Intune での [Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)または[リアルタイム保護を有効にして会社のリソースにアクセスする方法](/intune-user-help/turn-on-defender-windows)に関する記事をご覧ください。 |
|**動作の監視は無効になっています**|プロファイルを使用して管理者が、またはマネージド コンピューター上でユーザーが、動作の監視を無効にしています。|動作の監視を有効にします。 Intune での [Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)または[リアルタイム保護を有効にして会社のリソースにアクセスする方法](/intune-user-help/turn-on-defender-windows)に関する記事をご覧ください。 |
|**スクリプトのスキャンは無効になっています**|プロファイルを使用して管理者が、またはマネージド コンピューター上でユーザーが、スクリプトのスキャンを無効にしています。|スクリプトのスキャンを有効にします。 Intune での [Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)または[リアルタイム保護を有効にして会社のリソースにアクセスする方法](/intune-user-help/turn-on-defender-windows)に関する記事をご覧ください。 |
|**ネットワーク検査システムは無効になっています**|プロファイルを使用して管理者が、またはマネージド コンピューター上でユーザーが、ネットワーク検査システムを無効にしています。|ネットワーク検査システム (NIS) を有効にします。 Intune での [Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)または[リアルタイム保護を有効にして会社のリソースにアクセスする方法](/intune-user-help/turn-on-defender-windows)に関する記事をご覧ください。 |
|**マルウェア定義が最新ではない**|コンピューターが長期間インターネットから切断されていたため、そのマルウェア定義が更新されていない可能性があります。 このメッセージは、コンピューターのマルウェア定義の更新が 14 日以上遅れた場合に表示されます。|古くなったマルウェア定義は、[Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)を使用して更新することができます。|
|**フル スキャンの期限が過ぎています**|フル スキャンが 14 日間実行されていません。 フル スキャン中にコンピューターが再起動された可能性があります。|フル スキャンの期限が過ぎている場合は、1 回限りのフル スキャンを実行するか、定期的なフル スキャンのスケジュールを設定することができます。 「[Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)」をご覧ください。 |
|**クイック スキャンの期限が過ぎています**|クイック スキャンが 14 日間実行されていません。 クイック スキャン中にコンピューターが再起動された可能性があります。|クイック スキャンの期限が過ぎている場合は、1 回限りのクイック スキャンを実行するか、定期的なクイック スキャンのスケジュールを設定することができます。 「[Windows Defender ウイルス対策](device-restrictions-windows-10.md#windows-defender-antivirus)」をご覧ください。|
|**別のエンドポイント保護アプリケーションが実行されています**|別のエンドポイント保護アプリケーションが実行されており、コンピューターの状態は正常です。|既定では、別のエンドポイント保護アプリケーションがインストールされていて、Intune がそのアプリケーションを検出した場合、デバイスが不安定になる可能性があります。|

### <a name="next-steps"></a>次の手順
この情報を使っても問題が解決しない場合は、[Microsoft Intune のサポートを受ける](get-support.md)こともできます。
