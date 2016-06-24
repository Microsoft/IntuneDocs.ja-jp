---
# required metadata

title: 電子メール プロファイルに関するトラブルシューティング | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune の電子メール プロファイルに関するトラブルシューティング
ここでは、電子メール プロファイルに関する問題と、そのトラブルシューティングと解決方法について説明します。

この情報で問題が解決しない場合、さらに役立つ方法を探すには、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」を参照してください。


## 電子メール アカウントから画像を送信できない
電子メール アカウントを自動的に構成したユーザーが、自分のデバイスから画像を送信することができません。
**[サード パーティ アプリケーションから電子メールを送信できるようにする]** がオフになっている場合に、この問題が発生します。

### Intune での解決方法

1.  Microsoft Intune 管理コンソールで、**[ポリシー]** ワークロード &gt;**[構成ポリシー]** の順に選択します。

2.  電子メール プロファイルを選択し、**[編集]** を選択します。

3.  **[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。

### Windows Intune と統合された Configuration Manager

1.  Configuration Manager コンソール &gt;**[資産とコンプライアンス]** の順に開きます。

2.  **[概要]**  -&gt; **[コンプライアンス設定]**  -&gt; **[会社のリソースへのアクセス]** の順に展開して、**[電子メール プロファイル]** を選択します。

3.  電子メール プロファイルを右クリックし、**[プロパティ]** を開きます。

4.  **[同期設定]** タブで、**[サード パーティ アプリケーションから電子メールを送信できるようにする]** をオンにします。

## 次のステップ
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](how-to-get-support-for-microsoft-intune.md)」の説明に従って Microsoft サポートにお問い合わせください。


<!--HONumber=Jun16_HO1-->


