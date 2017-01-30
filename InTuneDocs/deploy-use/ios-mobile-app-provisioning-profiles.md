---
title: "アプリのプロビジョニング プロファイル | Microsoft Docs"
description: "Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に展開するツールが用意されています。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: db76786da0428b0e064f2091089653244d90ee2a


---

# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>iOS モバイル プロビジョニング プロファイルのポリシーを使用して、アプリが期限切れにならないようにする

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

iPhone および iPad に展開された Apple iOS 基幹業務アプリは、含まれるプロビジョニング プロファイルおよび証明書で署名されたコードで構築されます。 アプリを実行すると、iOS は iOS アプリの整合性を確認し、プロビジョニング プロファイルで定義されたポリシーを適用します。 次の検証が行われます。

- **インストール ファイルの整合性** - iOS は、アプリの詳細と、エンタープライズ署名証明書の公開キーを比較します。 これらが異なる場合はアプリの内容が変更されている可能性があり、アプリは実行を許可されません。
- **機能の強制** - iOS は、アプリのインストール (.ipa) ファイルに含まれる、(個々の開発者プロビジョニング プロファイルではなく) エンタープライズ プロビジョニング プロファイルからアプリの機能の適用を試行します。


アプリの署名に使用するエンタープライズ署名証明書は、通常 3 年間は継続します。 ただし、プロビジョニング プロファイルは 1 年後に期限が切れます。 証明書が有効である期間中、Intune には、有効期限が近づいているアプリを持つデバイスに新しいプロビジョニング プロファイルのポリシーを事前に展開するツールが用意されています。
証明書の期限が切れると、新しい証明書を使用してアプリを再び署名して、新しい証明書のキーを持つ新しいプロビジョニング プロファイルを埋め込む必要があります。



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>基幹業務アプリの有効期限が切れる日付を確認する方法

1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[アプリ]** > **[アプリ]** の順に選択します。
2. アプリの一覧の **[有効期限の日付]** 列で、アプリの有効期限を確認します。 **[フィルター]** ドロップダウン リストを **[期限切れまたは間もなく有効期限が切れる]** に設定して、処理が必要なアプリのみを表示することもできます。

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>iOS モバイル プロビジョニング プロファイルのポリシーを作成する方法


1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** > **[概要]** > **[ポリシーの追加]** の順に選択します。
2. **[新しいポリシーの作成]** ダイアログ ボックスで、**[iOS]** > **[Mobile Provisioning Profile Policy] (モバイル プロビジョニング プロファイルのポリシー)** の順に選択して、**[ポリシーの作成]** を選択します。
3. **[全般]** ページで、次の値を構成します。
    - **名前** -このモバイル プロビジョニング プロファイルのポリシーの名前を指定します。
    - **説明** - 必要に応じて、ポリシーの説明を指定します。
    - **構成プロファイル ファイル** - **[インポート]** をクリックして、Apple Developer Web サイトからダウンロードした Apple モバイル構成プロファイル ファイル (拡張子 **.mobileprovision**) を選択します。
4. 終了したら、**[ポリシーの保存]** を選択します。
5. 次に、必要な iOS デバイスにポリシーを展開します。 詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」を参照してください。



<!--HONumber=Dec16_HO5-->


