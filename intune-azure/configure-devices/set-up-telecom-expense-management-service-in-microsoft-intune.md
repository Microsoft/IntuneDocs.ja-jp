---
title: "通信費管理サービスを設定する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Intune と統合できるように Saaswedo 通信費管理サービスを構成します。"
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Intune Azure プレビューで通信費管理サービスを設定する
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune は、サードパーティのソフトウェア開発企業である Saaswedo の Datalert 通信費管理ソリューションと統合されました。 Datalert とは、Intune で管理されているデバイスの通信データ使用量を管理し、コストのかかる予想外のデータ超過やローミング超過を防止することができる、リアルタイム通信費管理ソフトウェアです。 Intune と Datalert の統合により、定義済みのしきい値を超えた場合に警告する自動化されたアラートを使用することで、ローミングおよび国内のデータ使用料の上限を一元的に設定、監視、適用できるようになります。 ユーザーがしきい値を超過した場合に、ローミングの無効化を含むさまざまなアクションを個々のエンド ユーザーやそのグループに適用するように、サービスを構成できます。 Datalert 管理コンソールでは、データ使用量と監視情報を示すレポートが利用できます。

Datalert サービスを Intune で使用するには、Datalert コンソールと Intune で設定を構成する必要があります。 Datalert サービスと Intune の接続を有効にする必要があります。 Datalert 側の接続が有効になっていても Intune 側が有効になっていない場合、Intune は通信を受け入れますが無視します。

>[!NOTE]
>この機能を試用版のテナントで有効にするには、アクティブ化について [Microsoft サポートに問い合わせてください](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。また、必要なソフトウェア ライセンスについては Datalert サポートに問い合わせてください。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

- Samsung KNOX
- iOS 8.0 以降

## <a name="prerequisites"></a>必要条件

- Microsoft Intune のサブスクリプション
- Datalert 通信費管理サービスのサブスクリプション

## <a name="list-of-telecom-expense-management-providers"></a>通信費管理プロバイダーの一覧

Intune は、現時点で以下の通信費管理プロバイダーと統合されています。

[Saaswedo Datalert 通信費管理サービス](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>Datalert サービスと連携するように Intune を構成する

 

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
2. **[デバイス構成]** ブレードで、**[セットアップ]** > **[通信費管理]** の順に選択します。
2. **[通信費管理]** で、**[接続の状態]** を選択します。

3. **[TEM サービス プロバイダーの一覧]** を選択し、表示された一覧からご利用のプロバイダーを選択します。 ご利用のプロバイダーの専用ページが開きます。 Saaswedo の場合は、Datalert ページが開きます。 Saaswedo Datalert を使用してサブスクリプションを購入する必要があります。

4. **Datalert** 管理コンソールで、以下の操作を行います。

    a. **[Settings (設定)]** タブに移動し、**[MDM configuration (MDM 構成)]** セクションに移動します。

    b. **[Unlock (ロック解除)]** を選択し、ページに設定を入力できるようにします。

    c. **[Server MDM (サーバー MDM)]** で、**[Microsoft Intune]** を選択します。

    d. **[Tenant ID (テナント ID)]** に Intune テナント ID を入力し、**[Connection (接続)]** ボタンを選択します。 **[Connection (接続)]** を選択すると、Datalert と Intune の間に既存の接続がないことを確認するために、Datalert サービスによって Intune へのチェックインが行われます。 数秒後に Microsoft ログイン ページが表示され、その後に Datalert Azure 認証が行われます。

    e. Microsoft 認証ページで、**[Accept (同意する)]** を選択します。 Datalert の "Thank you" ページにリダイレクトされ、数秒後にそのページが閉じます。 Datalert によって接続が検証され、検証済みの項目一覧の横に緑色のチェック マークが表示されます。 検証に失敗した場合は、赤色のメッセージが表示されます。 その場合は、Datalert サポートに問い合わせてください。

5. 数分待ってから Azure Portal にアクセスし、[接続の状態] が **[アクティブ]** になっていることを確認します。 

    >[!NOTE]
    >試用テナントでこの機能を有効にする場合は、[Microsoft サポートにお問い合わせください](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

6. Datalert 管理コンソールに戻り、データ行を構成します。

    a. **[Settings (設定)]** タブに移動します。

    b. **Setup (セットアップ)** ウィザードに移動し、ウィザードの手順に従います。



これで Datalert サービスがアクティブになってデータ使用量の監視が開始され、デバイスでの構成済み使用量制限を超える携帯データおよびローミング データが無効化されるようになります。

## <a name="turning-off-the-datalert-service"></a>Datalert サービスを無効にする

Azure Portal で Datalert サービスを無効にすると、以下のような影響があります。

- 過去の使用量制限の違反によってデバイスに適用されたすべてのアクションが取り消されます。
- ユーザーによるデータ アクセスとローミングがブロックされなくなります。
- Intune は引き続きサービスからの信号を受け入れますが、それらを無視するようになります。

**サービスを無効にするには**

1. Azure Portal の **[通信費管理]** ブレードで、**[無効]** を選択します。

2. **[保存]** を選択します。

## <a name="viewing-data-usage-and-roaming-reports"></a>データ使用量およびローミング レポートを表示する

現時点では、Saaswedo の Datalert 管理コンソールでのみデータ使用量のレポートを利用できます。



<!--HONumber=Feb17_HO2-->


