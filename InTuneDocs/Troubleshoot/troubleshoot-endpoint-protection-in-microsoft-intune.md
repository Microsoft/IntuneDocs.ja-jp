---
title: "エンドポイント保護のトラブルシューティング | Microsoft Docs"
description: "Microsoft Intune Endpoint Protection の使用中に生じた問題を解決します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: c0942dc6911a67dc7c3fa0c19e5a38ac60ec18b8


---

# <a name="troubleshoot-endpoint-protection-in-microsoft-intune"></a>Troubleshoot Endpoint Protection in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune エンドポイント保護の使用中に生じた問題を解決するには、このセクションの情報を参考にしてください。

この情報で問題が解決しない場合、さらに役立つ方法を探すには、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」を参照してください。


### <a name="endpoint-protection-error-messages"></a>Endpoint Protection のエラー メッセージ
ここでは、[Intune 管理コンソール](https://manage.microsoft.com)の **[Endpoint Protection の状態]** ウィンドウに表示される以下のエラーと警告の考えられる原因と対処法を説明します。

|メッセージ|考えられる原因|対処法|
|---------------|--------------------|-----------------------|
|**Endpoint Protection エンジンを使用できません**|Intune Endpoint Protection エンジンが壊れているか、削除されています。|Intune Endpoint Protection エンジンが壊れている場合は、ソフトウェアの更新または再インストールを試みてください。<br /><br />直ちに更新するには、Endpoint Protection クライアント ソフトウェアの **[更新]** (管理対象コンピューターのタスク バーに表示されます) を選択します。<br /><br />Endpoint Protection エンジンを更新できない場合は、エンジンを再インストールする必要があります。<br /><br />管理対象コンピューターのコントロール パネルに一覧表示されるインストール済みプログラムから **[Microsoft Intune Endpoint Protection Agent]** を見つけて、アプリケーションをアンインストールします。<br /><br />次回更新プログラムを同期するときに、Microsoft Online Management 更新マネージャーが不足しているプログラムを検出し、スケジュールされているインストール時間にそのプログラムを再インストールします。|
|**Endpoint Protection が無効です**|管理者がポリシーを使用して Intune Endpoint Protection を無効にしているか、管理対象コンピューターのユーザーが無効にしています。|Endpoint Protection が無効になっている場合は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)で Endpoint Protection を有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用されるポリシーの **[Endpoint Protection を有効にする]** 設定を変更します。<br /><br />または、<br /><br />管理対象コンピューターで Endpoint Protection を有効にするには、通知領域から Intune Endpoint Protection クライアントを起動します。すると、Endpoint Protection を有効にするように求めるメッセージが表示されます。|
|**リアルタイム保護が無効です**|管理者 (ポリシーを使用)、または管理対象コンピューターのユーザーが、リアルタイム保護を無効にしています。|リアルタイム保護が無効になっている場合は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)でリアルタイム保護を有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用するポリシーの **[リアルタイム保護を有効にする]** 設定を **[はい]** に変更します。<br /><br />または、<br /><br />管理対象コンピューターでリアルタイム保護を有効にするには、通知領域から Endpoint Protection クライアント ソフトウェアを起動します。 リアルタイム保護を有効にするようにというメッセージが表示されます。|
|**ダウンロードのスキャンは無効になっています**|管理者 (ポリシーを使用)、または管理されたコンピューターのユーザーが、ダウンロードのスキャンを無効にしています。|ダウンロードのスキャンが無効になっている場合は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)でダウンロードのスキャンを有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用するポリシーの **[すべてのダウンロードをスキャンする]** 設定を **[はい]** に変更します。<br /><br />または、<br /><br />管理対象コンピューターでダウンロードのスキャンを有効にするには、通知領域から Endpoint Protection クライアント ソフトウェアを起動します。 **[設定]** タブの **[リアルタイム保護]** を選択し、**[すべてのダウンロードをスキャンする]** チェック ボックスをオンにして、**[変更の保存]** を選択します。|
|**ファイルとプログラムの動作の監視は無効になっています**|管理者 (ポリシーを使用)、または管理されたコンピューターのユーザーが、ファイルとプログラムの動作の監視を無効にしています。|ファイルとプログラムの動作の監視が無効になっている場合は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)でファイルとプログラムの動作の監視を有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用されるポリシーの **[コンピューターのファイルとプログラムの動作を監視する]** 設定を **[はい]** に変更します。<br /><br />または、<br /><br />管理対象コンピューターでファイルとプログラムの動作の監視を有効にするには、通知領域から Endpoint Protection クライアント ソフトウェアを起動します。 **[設定]** タブの **[リアルタイム保護]** を選択し、**[コンピューターのファイルとプログラムの動作を監視する]** チェック ボックスをオンにして、**[変更の保存]** を選択します。|
|**動作の監視は無効になっています**|管理者 (ポリシーを使用)、または管理対象コンピューターのユーザーが、動作の監視を無効にしています。|動作の監視が無効になっている場合は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)で動作の監視を有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用されるポリシーの **[動作の監視を有効にする]** 設定を **[はい]** に変更してから、管理対象コンピューターを再起動します。<br /><br />または、<br /><br />管理対象コンピューターで動作の監視を有効にするには、通知領域から Endpoint Protection クライアント ソフトウェアを起動します。 **[設定]** タブの **[リアルタイム保護]** を選択し、**[動作の監視を有効にする]** チェック ボックスをオンにして、**[変更の保存]** を選択します。 次に、コンピューターを再起動します。|
|**スクリプトのスキャンは無効になっています**|管理者 (ポリシーを使用)、または管理対象コンピューターのユーザーが、スクリプトのスキャンを無効にしています。|スクリプトのスキャンが無効になっている場合は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)でスクリプトのスキャンを有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用されるポリシーの **[スクリプトのスキャンを有効にする]** 設定を **[はい]** に変更します。<br /><br />または、<br /><br />管理対象コンピューターでスクリプトのスキャンを有効にするには、通知領域から Endpoint Protection クライアント ソフトウェアを起動します。 **[設定]** タブの **[リアルタイム保護]** を選択し、**[スクリプトのスキャンを有効にする]** チェック ボックスをオンにして、**[変更の保存]** を選択します。|
|**ネットワーク検査システムは無効になっています**|管理されたコンピューターのネットワーク検査システムが、管理者 (ポリシーを使用) またはユーザーによって無効にされています。|ネットワーク検査システムは、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで有効にすることができます。 以下のいずれかを実行します。<br /><br />[Intune 管理コンソール](https://manage.microsoft.com)でネットワーク検査システムを有効にするには、**[ポリシー]** ワークスペースを開き、コンピューターに適用されるポリシーの **[ネットワーク検査システムを有効にする]** 設定を **[はい]** に変更してから、管理対象コンピューターを再起動します。<br /><br />または、<br /><br />管理対象コンピューターでネットワーク検査システムを有効にするには、通知領域から Endpoint Protection クライアント ソフトウェアを起動します。 **[設定]** タブの **[リアルタイム保護]** を選択し、**[ネットワーク検査システムを有効にする]** チェック ボックスをオンにして、**[変更の保存]** を選択します。 コンピューターを再起動します。|
|**マルウェア定義が最新ではない**|コンピューターが長期間インターネットから切断されていたため、そのマルウェア定義が更新されていない可能性があります。 このメッセージは、コンピューターのマルウェア定義の更新が 14 日以上遅れた場合に表示されます。|古くなったマルウェア定義は、[Intune 管理コンソール](https://manage.microsoft.com)、または管理対象コンピューターで更新することができます。<br /><br />詳細については、トピック「[Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)」をご覧ください。|
|**フル スキャンの期限が過ぎています**|フル スキャンが 14 日間実行されていません。 フル スキャン中にコンピューターが再起動された可能性があります。|フル スキャンの期限が過ぎている場合は、「[Microsoft Intune コンピューター クライアントを使用した一般的な Windows PC 管理タスク](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)」に従い、[Intune 管理コンソール](https://manage.microsoft.com)で 1 回限りのフル スキャンを実行するか、定期的なフル スキャンのスケジュールを設定することができます。|
|**クイック スキャンの期限が過ぎています**|クイック スキャンが 14 日間実行されていません。 クイック スキャン中にコンピューターが再起動された可能性があります。|クイック スキャンの期限が過ぎている場合は、「[Microsoft Intune コンピューター クライアントを使用した一般的な Windows PC 管理タスク](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)」に従い、[Intune 管理コンソール](https://manage.microsoft.com)で 1 回限りのクイック スキャンを実行するか、定期的なクイック スキャンのスケジュールを設定することができます。|
|**別のエンドポイント保護アプリケーションが実行されています**|別のエンドポイント保護アプリケーションが実行されており、コンピューターの状態は正常です。|既定では、別のエンドポイント保護アプリケーションがインストールされていることが検出された場合、Endpoint Protection が自動的に無効になります。 別のエンドポイント保護アプリケーションが検出されなかった場合、Endpoint Protection は引き続き有効です。 詳細については、「[Microsoft Intune の Endpoint Protection を使用して Windows PC を保護する](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)」を参照してください。|

### <a name="next-steps"></a>次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。



<!--HONumber=Dec16_HO2-->


