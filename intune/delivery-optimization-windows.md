---
title: Microsoft Intune での Windows 10 用の配信の最適化設定 - Azure | Microsoft Docs
description: Windows 10 以降のデバイスで利用できる配信の最適化クラウド サービスを使って、デバイスにソフトウェア更新プログラムを配信する方法を構成します。 Intune では、デバイス構成プロファイルを作成してインターネットから更新プログラムをインストールします。 また、既存の更新プログラム リングを配信の最適化プロファイルに置き換える方法についても確認します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36cfb5ac05b2d69b5c7349f4ebc6054848a08fc8
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "52730407"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune での Windows 10 (およびそれ以降) の配信の最適化設定

この記事では、Windows 10 デバイスに対して構成できるすべての配信の最適化設定を説明します。 これらの設定は、デバイスの構成プロファイルに追加した後、Microsoft Intune を使ってデバイスに割り当てたり展開したりします。

## <a name="settings"></a>Settings

**[配信の最適化ダウンロード モード]**: 更新プログラムをデバイスに配信する方法を選択します。 次のようなオプションがあります。

- **[未構成]**: エンド ユーザーはそれぞれ独自の方法を使って各デバイスを更新します。**Windows Updates** や、OS で使用できる **[配信の最適化]** 設定が使われる場合があります。
- **[HTTP のみ、ピアリングなし]**: 更新プログラムをインターネットからのみ取得します。 ネットワーク上の他のコンピューターからは更新プログラムを取得しません (ピアリングまたはピア ツー ピアと呼ばれます)。
- **[HTTP blended with peering behind the same NAT HTTP blended with peering across a private group]\(HTTP と同じ NAT HTTP の背後にあるピアリングとプライベート グループでのピアリングの組み合わせ\)**: インターネットおよびネットワーク上の他のコンピューターから更新プログラムを取得します。 ピアリングは、同じ Active Directory サイト (存在する場合) または同じドメイン内にあるデバイス上で発生します。 このオプションを選択した場合、ピアリングはネットワーク アドレス変換 (NAT) の IP アドレスを越えます。
- **[HTTP とインターネット ピアリングの組み合わせ]**: インターネットおよびネットワーク上の他のコンピューターから更新プログラムを取得します。
- **[ピアリングなしの簡易ダウンロード モード]**: インターネットを介して、Microsoft などの更新プログラムの所有者から更新プログラムを直接取得します。 これは配信の最適化クラウド サービスに接続しません。
- **[バイパス モード]**: バックグラウンド インテリジェント転送サービス (BITS) を使って更新プログラムを取得します。 配信の最適化を使いません。

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>既存の更新プログラム リングから配信の最適化に移動する

**[ソフトウェア更新プログラム] – [Windows 10 更新プログラムのリング]** は、**[配信の最適化]** 設定によって置き換えられます。 既存の更新プログラム リングは、**[配信の最適化]** 設定を使うように簡単に変更できます。 ステップ:

1. 配信の最適化の構成プロファイルを作成します。

    1. Intune で、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
    2. プロファイルの **[名前]** と **[説明]** を入力します。
    3. **[プラットフォーム]** に対して **[Windows 10 以降]** を選択します。 **[プロファイルの種類]** に対して **[配信の最適化]** を選択します。
    4. **[設定]** を選択します。 **[配信の最適化ダウンロード モード]** に対して、既存のソフトウェア更新プログラム リングによって使用されるものと同じモードを選択します。 次のようなオプションがあります。
        - **未構成**
        - **HTTP のみ、ピアリングなし**
        - **HTTP blended with peering behind the same NAT HTTP blended with peering across a private group** (HTTP と同じ NAT HTTP の背後にあるピアリングとプライベート グループでのピアリングの組み合わせ)
        - **HTTP とインターネット ピアリングの組み合わせ**
        - **ピアリングなしの簡易ダウンロード モード**
        - **バイパス モード**

2. 既存のソフトウェア更新プログラム リングと同じデバイスおよびユーザーに、この新しいプロファイルを割り当てます。 [プロファイルの割り当て](device-profile-assign.md)に関するページに手順が記載されています。

3. 既存のソフトウェアのリングの構成を解除します。
    1. Intune で、**[ソフトウェア更新プログラム]** > [Windows 10 更新プログラムのリング] の順に移動します。
    2. 一覧から更新プログラム リングを選択します。
    3. 設定で、**[配信の最適化ダウンロード モード]** を **[未構成]** に設定します。
    4. **[Ok]** >  変更を **[保存]** します。

## <a name="next-steps"></a>次の手順

[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。