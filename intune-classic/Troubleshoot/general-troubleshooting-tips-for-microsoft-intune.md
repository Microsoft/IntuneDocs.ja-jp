---
title: "一般的なトラブルシューティングのヒント | Microsoft Docs"
description: "Intune の問題を解決するための一般的なリソース。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 63bb7ca097390582d85f3ea7daced42d2a97fbb4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---

# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Microsoft Intune の一般的なトラブルシューティングのヒント

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune を展開した後、構成やクライアントのデバイスに問題が発生する可能性があります。 次のリソースを使用すると、問題解決のための原因を発見しやすくなります。

> [!NOTE]
> サポート リクエストを作成したり、既存のリクエストを確認したりするには、[Office 365 管理センターにアクセスしてしてください](https://portal.office.com/admin/default.aspx)。 サポート オプションの詳細については、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」を参照してください。

## <a name="define-the-problem"></a>問題の定義

-   どのように動作しますか?

-   この動作はだれが操作し、また、どのプラットフォームまたデバイスで生じていますか?

-   デバイスは以前は正常に動作していましたか?

-   Intune またはデバイスの構成にどのような変更を加えましたか?

-   構成の変更以外に、操作環境にその他の変更が加えられましたか?

-   この問題はどのくらいの頻度で発生しますか? 突発的ですか? あるいは一貫性がありますか?

-   ユーザーに認証の問題が発生する可能性はありますか?  可能性がある場合、ユーザーが Azure Active Directory を使用する他のサービスにサインインできるかどうかを確認してください。 また、ユーザーが別のデバイスからサインインできるかどうかも確認してください。

-   サービスの状態を確認しましたか? Intune のサービス正常性は、[Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)で監視できます。 左側のウィンドウで **[サービス正常性]** を選択します。

## <a name="collect-available-data"></a>利用可能なデータの収集

-   次のリソースは、デバイスのログを収集する方法を理解するのに役立ちます。
  - [USB ケーブルを使用して Android の診断データのログを IT 管理者に送信する](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [メールを使用して Android の診断データのログを IT 管理者に送信する](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [IT 管理者に Android の登録に関するエラーを送信する](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)
  - [IT 管理者に iOS の登録に関するエラーを送信する](/intune-user-help/send-errors-to-your-it-admin-ios)

-   管理コンソール データ。たとえば、ポリシー実装の問題の場合は、「Microsoft Intune でユーザーとデバイスの管理にグループを使用する」に記載されている説明に従って、目的のポリシーとその状態を調べます。

## <a name="research-the-solution"></a>ソリューションの調査

-   ソリューションについて Web を検索します。 たとえば、エラー 0x80073CF0 が返された場合は、Web 上で **technet intune 0x80073cf0** を検索すると、「[Microsoft Intune のアプリ展開に関する問題のトラブルシューティング](troubleshoot-app-deployment-problems-in-microsoft-intune.md)」の記事が見つかります。 この記事では、このエラーに対処するための推奨事項を提供します。

-   [Intune TechNet フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)で、回答を検索できます。  これまで扱われたことのない問題の場合、コミュニティから提案を受けられるように、質問を投稿してください。

-   サポートを依頼します。 お客様が問題を特定し、入手できるデータを収集されていると、Intune のサポートが問題の解決をより支援しやすくなります。

    サポート リクエストを作成するには、[Office 365 管理センターにアクセスしてください](https://portal.office.com/admin/default.aspx)。 サポート オプションの詳細については、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」を参照してください。

## <a name="find-community-resources"></a>コミュニティのリソースを探す
以下のコミュニティ リソースには、その他の有用な情報があります。

-   [Microsoft Intune サバイバル ガイド](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx)。ここには、Intune の構成、保守、およびトラブルシューティングに役立つ多くのリソースへのリンクが記載されています。

-   [Intune のブログ](http://blogs.technet.com/b/windowsintune/)

-   [Twitter で Intune をフォローする](https://twitter.com/MSIntune)

-   [Intune フォーラム](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>次のステップ
以下のトピックには、特定の問題に関するトラブルシューティングのヘルプが含まれています。 この情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。

[Microsoft Intune におけるエンドポイント保護のトラブルシューティング](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Microsoft Intune での会社のリソースへのアクセスに関する問題のトラブルシューティング](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Microsoft Intune のアプリ展開に関する問題のトラブルシューティング](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Intune のデバイス登録に関するトラブルシューティング](troubleshoot-device-enrollment-in-intune.md)

[Microsoft Intune のポリシーのトラブルシューティング](troubleshoot-policies-in-microsoft-intune.md)

[Microsoft Intune でのクライアント セットアップのトラブルシューティング](troubleshoot-client-setup-in-microsoft-intune.md)

[Microsoft Intune でのソフトウェア更新のトラブルシューティング](troubleshoot-software-updates-in-microsoft-intune.md)

