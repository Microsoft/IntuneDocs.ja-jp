---
title: "Android for Work アプリ構成ポリシー"
description: "Intune のモバイル アプリ構成ポリシーを使用して、ユーザーが Android for Work アプリを実行するときに必要となる可能性がある設定を指定できます。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f2284920852de5a79cf47fee81922a5b069157c3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2017
---
# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Microsoft Intune でのモバイル アプリ構成ポリシーを使用した Android for Work アプリの構成

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune のモバイル アプリ構成ポリシーを使用して、ユーザーがアプリを実行するときに必要となる可能性がある設定を指定できます。 たとえば、アプリは次の内容を指定することをユーザーに要求することがあります。

-   カスタム ポート番号
-   言語の設定
-   会社のロゴなどのブランドの設定

ユーザーが設定を誤って入力すると、ヘルプ デスクの負荷が増加し、新しいアプリの採用が遅くなる可能性があります。

モバイル アプリ構成ポリシーを使用すると、ユーザーがアプリを実行する前にこれらの設定をデバイスに展開することができます。 設定は自動的に指定されるため、ユーザーの操作は不要です。

アプリ構成ポリシーを利用するには、アプリの開発元が作成時にエンタープライズ アプリ構成を公開している必要があります。 たとえば、Google Chrome は、既定のブックマーク、許可するサイト、拒否するサイトの設定を公開しているので、アプリ構成ポリシーを利用できます。 このような設定がサポートされているかどうか、およびポリシーで指定する方法については、アプリの開発元に問い合わせてください。

アプリ構成ポリシーは、構成するアプリを展開したユーザーと同じユーザーに展開します。 アプリ設定はアプリの実行時に適用されます。

## <a name="configure-a-mobile-app-configuration-policy"></a>モバイル アプリ構成ポリシーを構成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[概要]** &gt; **[ポリシーの追加]** の順に選択します。

2.  ポリシーの一覧で **[Android for Work]** を展開し、**[モバイル アプリ構成ポリシー (Android for Work)]** を選択し、**[ポリシーを作成する]** を選択します。

    > [!TIP]
    > この種類のポリシーではカスタム設定のみを構成できます。 推奨設定はありません。

3.  **[ポリシーの作成]** ページの **[全般]** セクションで、名前とモバイル アプリ構成ポリシーのオプションの説明を指定します。

4. ページの **[モバイル アプリ構成ポリシー]** セクションで、次の情報を指定します。
    - **[この構成が適用されるアプリケーションのパッケージ ID]** - パッケージ ID は、Google Play ページのアプリ URL の ’id=’ セクションで確認できます。 たとえば、Microsoft Excel アプリのパッケージ ID は **com.microsoft.office.excel** です。
    - テキスト ボックスに構成するアプリ設定のデータを入力します。 これらの設定は、アプリの提供元から入手します。 これらの設定をサポートしていないアプリもあります。
5.  **[検証]** をクリックして、入力したデータが有効なプロパティ リスト形式であることを確認します。

    > [!IMPORTANT]
    > **[検証]** をクリックすると、Intune によって、入力した構成データが有効な形式であるかどうかがチェックされます。 データが関連付けられているアプリで動作するかどうかはチェックされません。

6.  終了したら、 **[ポリシーの保存]**をクリックします。

新しいポリシーは、 **[構成ポリシー]** ノードに表示されます。


## <a name="deploy-the-app-configuration-policy"></a>アプリ構成ポリシーを展開する
モバイル アプリ構成ポリシーを作成したら、設定が適用されるアプリを展開するユーザーと同じユーザーにポリシーを展開する必要があります。

ポリシーを展開する方法の詳細については、「[構成ポリシーを展開する](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)」を参照してください。

Android for Work デバイスにアプリを展開する方法については、「[How to deploy Android for Work apps with Intune](android-for-work-apps.md)」(Android for Work アプリを展開する方法) を参照してください

展開したアプリをデバイスで実行すると、モバイル アプリ構成ポリシーで構成した設定を使用して実行されます。

> [!TIP]
> 各ユーザーの各アプリには、1 つのアプリ構成ポリシーのみを展開します。
