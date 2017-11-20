---
title: "Windows Defender をオンにする | Microsoft Docs"
description: "Windows Defender をオンにし、会社のリソースにアクセスする方法について説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope: User help
ROBOTS: 
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 446b395aab311d13ebc7ac6b8c3ed7c740070729
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Windows Defender をオンにし、会社のリソースにアクセスする

学校や職場は、そのリソースにアクセスするデバイスが確実にセキュリティで保護されるようにしたいと考えています。 悪意のあるソフトウェアに対して Windows 内蔵の保護機能である [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx) を適用する方法がいくつかあります。

アクセスに問題があり、それを解消するには、Windows Defender でいくつかの設定を変更しなければならないことがあります。 以下の手順では、場合によっては、コンピューター上のまざま場所に移動する必要があります。

## <a name="turn-on-windows-defender"></a>Windows Defender をオンにする

1. **[スタート]** で **[コントロール パネル]** を開きます。
2. **[管理ツール]**、**[グループ ポリシーの編集]** の順に開きます。 新しいウィンドウで **[ローカル グループ ポリシー エディター]** が開きます。
3. **[コンピューターの構成]**、**[管理テンプレート]**、**[Windows コンポーネント]**、**[Windows Defender ウイルス対策]** の順に開きます。 **[Windows Defender ウイルス対策を無効にします]** という設定がその他の設定のフォルダーの下にあります。 
4. **[Windows Defender ウイルス対策を無効にします]** を開き、**[無効]** または **[未構成]** に設定されていることを確認します。

## <a name="turn-on-real-time-protection"></a>リアルタイム保護を有効にする

リアルタイム保護がオンになっていることを確認します。**[スタート]** に移動し、**[Windows Defender セキュリティ センター]** を検索します。 **[ウイルスと脅威の防止の設定]** を選択し、**[リアルタイム保護]** と **[クラウドによる保護]** の両方が **[オン]** になっていることを確認します。 これらのオプションが表示されない場合、次の手順で有効にします。

1. **[スタート]** で **[コントロール パネル]** を開きます。
2. **[管理ツール]**、**[グループ ポリシーの編集]** の順に開きます。 新しいウィンドウで **[ローカル グループ ポリシー エディター]** が開きます。
3. **[コンピューターの構成]**、**[管理テンプレート]**、**[Windows コンポーネント]**、**[Windows Defender セキュリティ センター]**、**[ウイルスと脅威の防止]** の順に開きます。
4. **[Virus and threat protection area]\(ウイルスと脅威の防止の領域\)** という設定を開き、**[無効]** に設定します。

## <a name="update-your-antivirus-definitions"></a>ウイルス対策定義を更新する

ウイルス対策定義が最新の状態になっていることを確認します。**[スタート]** に移動し、**[Windows Defender セキュリティ センター]** を検索します。 **[保護の更新]** と **[更新プログラムの確認]** を選択し、現行のウイルス対策保護がデバイスに適用されていることを確認します。 このオプションが表示されない場合、「[リアルタイム保護を有効にする](turn-on-defender-windows.md#turn-on-real-time-protection)」の手順を実行します。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com)をご確認ください。
