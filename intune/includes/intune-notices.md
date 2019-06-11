---
title: ファイルを含める
description: ファイルを含める
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454124"
---
以下の通知では、今後の Intune の変更と機能に備えるために役立つ重要な情報が提供されます。 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Android 用ポータル サイト アプリを最新バージョンに更新する <!--4536963-->
Intune では、Android 用ポータル サイト アプリに対する更新プログラムが定期的にリリースされます。 2018 年 11 月に、ポータル サイトの更新プログラムがリリースされました。これには、Google による既存の通知プラットフォームから Google の Firebase Cloud Messaging (FCM) への変更に備えるための、バックエンド スイッチが含まれていました。 Google が既存の通知プラットフォームを終了して FCM に移行したとき、エンド ユーザーは、Google Play ストアとの交信を継続するために、各自のポータル サイト アプリを少なくとも 2018 年 11 月のリリースに更新済みである必要があります。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
利用統計情報では、5.0.4269.0 よりも前のバージョンのポータル サイトを備えたデバイスがあることが示されています。 このバージョン以上のポータル サイト アプリをインストールしないと、ワイプ、パスワードのリセット、入手可能な必須アプリのインストール、証明書の登録のような、IT プロフェッショナルが開始したデバイス アクションが意図したとおりに機能しない場合があります。 自分のデバイスが Intune の MDM に登録されている場合は、[クライアント アプリ] – [検出されたアプリ] に移動することで、ポータル サイトのバージョンとユーザーを確認できます。 以前のバージョンのポータル サイトを選択すると、どのエンド ユーザーがポータル サイトを更新していないデバイスを持っているのかを確認できます。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
更新していない Android デバイスを使っているエンド ユーザーに、Google Play を使ってポータル サイトを更新するよう依頼します。 ユーザーがポータル サイト アプリの自動更新を維持していない場合は、ヘルプ デスクに通知します。 Google の FCM プラットフォームと変更について詳しくは、「追加情報」にあるリンクをご覧ください。

#### <a name="additional-information"></a>追加情報
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Intune に設置された新しい全画面のエクスペリエンス <!--4593669-->
Azure portal では、Intune に対する UI 作成と編集のエクスペリエンスを更新して公開しました。 この新しいエクスペリエンスでは、1 つのブレード内にまとめられたウィザード形式のフォーマットを使用することで、既存のワークフローを簡素化します。 この更新によって、"ブレードが無秩序に増える" ことや、ブレードを詳細にドリルダウンしていくことが求められる作成および編集のフローを回避します。 また、作成のワークフローは、割り当て (アプリ割り当て以外) を含むように更新されます。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響
portal.azure.com および devicemanagement.microsoft.com の両方で、次の数か月間にわたって全画面のエクスペリエンスが Intune に公開されます。 この UI の更新は、既存のポリシーとプロファイルの機能には影響を及ぼしませんが、少し変更されたワークフローが表示されます。 たとえば、新しいポリシーを作成するときに、いくつかの割り当てをポリシーの作成後に行うのではなく、このフローの一部として設定できます。 コンソールでの新しいエクスペリエンスの外観を示したスクリーンショットは、「追加情報」にあるブログ投稿で確認してください。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>この変更に対して必要な準備
何らかのアクションを行う必要はありませんが、必要に応じて IT プロフェッショナル向けのガイダンスの更新を検討できます。 Microsoft では、Azure portal 上で Intune 内の各種のブレードに対してこのエクスペリエンスが公開され次第、ドキュメントを更新する予定です。

#### <a name="additional-information"></a>追加情報 
https://aka.ms/intune_fullscreen
