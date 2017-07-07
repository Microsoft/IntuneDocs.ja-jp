---
title: "デバイス コンプライアンス ポリシーの作成"
description: "会社データのアクセスに使用するモバイル デバイスや PC をセキュリティで保護するためにコンプライアンス ポリシーを作成します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3dcafbd3cfdbccdfa851e8d21572d834d629564b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="create-a-device-compliance-policy-in-microsoft-intune"></a>Microsoft Intune でデバイスのコンプライアンス ポリシーを作成する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

このトピックでは、デバイスが準拠しているとみなされるために従う必要があるコンプライアンス ポリシーを作成するために使用できる手順について説明します。

##  <a name="step-1-add-a-new-policy"></a>手順 1: 新しいポリシーを追加する
  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[コンプライアンス ポリシー]** &gt; **[追加]** の順に選択します。

  ![上部の [追加] メニューを示している Intune 管理コンソールのコンプライアンス ポリシー ページ](./media/intune-sa-3a-add-compliance-policy.png)

##  <a name="step-2--configure-settings"></a>手順 2: 設定を構成する
**[ポリシーの作成]** ページで、必要に応じて以下の設定を有効にします。
  -   パスワードや暗号化などのシステムのセキュリティ設定
  -   デバイスが改造されているかどうか、Windows デバイス正常性構成証明書サービスによって正常と報告されているかどうかなどのデバイスのヘルスの設定
  -   必要な最小オペレーティング システム バージョンや許可される最大オペレーティング システム バージョンなどのデバイスのプロパティの設定
![[ポリシーの作成] ページの [全般] タブ](./media/intune-sa-3b-create-policy.png)


##  <a name="step-3-save-the-policy"></a>手順 3: ポリシーを保存する
終了したら、**[ポリシーの保存]** を選びます。

ポリシーは、保存した後、すぐ展開できますが、後で展開することもできます。 **[ポリシー]** ワークスペースの **[コンプライアンス ポリシー]** ノードに新しいポリシーが表示されます。

##  <a name="step-4-set-the-compliance-status-validity-period"></a>手順 4: コンプライアンス対応状態の有効期間を設定する
デバイスがコンプライアンス対応していないと見なされる前にチェックインする必要がある時間を指定するには、コンプライアンス ポリシーの設定に移動し、この時間を更新します。 既定は、30 日間に設定されています。

![ポリシーのメニュー バーのコンプライアンス ポリシー設定オプション](../media/mdm-compliance-policy-settings.png)

![[コンプライアンス ポリシー] ダイアログ ボックス](../media/mdm-ca-compliance-status-validity-period.png)

## <a name="supported-policy-settings"></a>サポートされるポリシー設定
次の表は、コンプライアンス ポリシー設定と、それらがサポートされるプラットフォームの一覧を示しています。

-------------
|Setting|iOS|Android|Windows|
|-----|----|-----|-----|
|モバイル デバイスのロックを解除するパスワードを要求する|iOS 6 以降|Android 4.0 以降 <br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降|
|単純なパスワードを許可する|iOS 6 以降|サポートされていません|Windows Phone 8.1 以降|
|パスワードの最小文字数|iOS 6 以降| Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降| Windows Phone 8.1 以降<br>Windows 8.1|
|必要なパスワードの種類|iOS 6 以降|利用不可|Windows Phone 8.1 以降 <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|文字セットの最小数|iOS 6 以降|利用不可|Windows Phone 8.1 以降 <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|パスワードの品質|利用不可|Android 4.0 以降 <br>Samsung KNOX Standard 4.0 以降|利用不可|
|パスワードが必要になるまでの非アクティブ状態の時間 (分)|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|パスワードの有効期限 (日数)|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|パスワードの履歴を記憶する|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|前のパスワードの再利用を防止|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|デバイスがアイドル状態から戻るときにパスワードを必須とする| 利用不可| 利用不可|[Windows] 10 Mobile|
|モバイル デバイスの暗号化を要求する|該当なし|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降<br> Windows 8.1|
|デバイスが正常と報告されることを要求する| 利用不可| 利用不可|Windows <br>[Windows] 10 Mobile|
|デバイスは改造もルート化も行われていなければならない|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|利用不可|
|電子メール アカウントは Intune によって管理される必要がある|iOS 6 以降|利用不可| 利用不可|
|Intune によって管理される必要のある電子メール プロファイルを選択する|iOS 6 以降|利用不可| 利用不可|
|必要な最小 OS バージョン|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降| Windows Phone 8.1 以降<br>Windows 8.1|
|許可される最大 OS バージョン|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8.1 以降<br>Windows 8.1|

各プラットフォームでサポートされるコンプライアンス設定の詳細については、次のいずれかを選択してください。
> [!div class="op_single_selector"]
- [iOS デバイス向けのコンプライアンス ポリシー設定](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Android デバイス向けのコンプライアンス ポリシー設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [Windows と Windows Phones 向けのコンプライアンス ポリシー設定](windows-compliance-policy-settings-in-microsoft-intune.md)


## <a name="next-steps"></a>次のステップ
[コンプライアンス ポリシーを展開して監視する](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>関連項目
[デバイス コンプライアンス ポリシーの概要](introduction-to-device-compliance-policies-in-microsoft-intune.md)
