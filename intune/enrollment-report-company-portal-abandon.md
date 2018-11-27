---
title: Intune のポータル サイトでの登録の破棄
titlesuffix: Microsoft Intune
description: ポータル サイトの破棄レポートについて説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 44a6d89b649514a08193d7144dff7d89dc3d9c55
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183368"
---
# <a name="company-portal-abandonment-report"></a>ポータル サイトの破棄レポート

このレポートでは、ポータル サイトで登録を行ったユーザーが、登録のどの時点で登録を破棄しているかを知ることができます。

レポートを表示するには、**[Intune]** > **[デバイスの登録]** > **[ポータル サイトの破棄]** を選択します。

この破棄情報を使用すると、ユーザーが登録を完了できるように、オンボード ドキュメントを更新できます。 たとえば、多くのユーザーが利用規約で終了している場合、その区分を確認して、そこがユーザーにとってより直観的になるようにできます。

## <a name="what-is-abandonment"></a>破棄とは

破棄とは、ユーザーが次のいずれかを実行する場合です。

-   登録を停止するアクションを明示的に選ぶ
-   登録中にポータル サイトを閉じる
-   登録のセクション間で 30 分以上の時間を費やす

ユーザーが登録を何度も停止し、再開している場合、複数回試行され、複数回破棄されたと表示されます。 ユーザーが次の別の登録画面に移る間に 30 分間待機する場合、複数回破棄されたものと見なされます。

## <a name="what-does-the-report-show"></a>レポートで示されること

登録レポートには、iOS および Android デバイス用のデータが含まれます。

このレポートには、過去 2 週間のデータが表示されますが、レポートをフィルター処理すると、過去 30 日の任意の時点を表示できます。

**[フィルター]** を選択し、日付範囲、オペレーティング システム、登録のセクションでフィルタリングを実行できます。

### <a name="number-and-percentage-tiles"></a>回数と割合のタイル

レポートの上部には、すべての登録の破棄レポートの回数と割合が表示されます。

-   登録が開始されました: 登録の試行回数です。
-   破棄された登録: 登録完了および準拠デバイスとならなかった登録の試行回数です。
-   Abandonment rate\(破棄率\): 破棄された登録の試行の割合です (破棄された登録/開始された登録)。

### <a name="line-graph"></a>折れ線グラフ

折れ線グラフでは、次の 4 つの主要な登録セクションの日単位での破棄回数が示されます。

-   セットアップ チェックリスト
-   プラットフォーム画面
-   利用規約
-   コンプライアンス/アクティブ化

### <a name="user-abandonment-actions"></a>User abandonment actions\(ユーザーの破棄操作\)

次の表に、破棄と見なされるユーザー アクションの一覧を示します。 登録画面の例を見るには、[iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) と [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment) の登録動画を参照してください。 


#### <a name="setup-checklist-section"></a>[セットアップ チェックリスト] セクション

| 破棄名 | 画面またはフロー | プラットフォーム | 操作 |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | ポータル サイトでページを開くプロンプト | iOS/Android | **キャンセル** |
| EnrollmentWrapUp | **[会社のリソースを読み込んでいます]** が終わるまで [デバイスを登録しています] 画面 | iOS/Android | 30 分以上かかった |
| DeviceCategory | **[完了]** をクリックするまで (管理者が構成している場合) デバイス カテゴリの選択 | iOS/Android | 30 分以上かかった |
| PreEnrollmentWizard | 登録を開始したが [Set up access]\(アクセス設定\) に戻り [Set up access]\(アクセス設定\) 画面 | iOS/Android| **延期** |
| PreEnrollmentWizard | **[次の手順]** 画面で **[次へ]** をクリックするまで [Set up access]\(アクセス設定\) 画面 | iOS/Android | 30 分以上かかった |

#### <a name="platform-screens-section"></a>[プラットフォーム画面] セクション

| 破棄名 | 画面またはフロー | プラットフォーム | 操作 |
| ---- |---- |---- |---- |
| iOSProfileLaunch | 構成プロファイルを表示するプロンプト | iOS | **無視** |
| iOSProfileLaunch | [Installing profile]\(プロファイルのインストール\) 画面 | iOS | **キャンセル** |
| iOSProfileLaunch | デバイスを登録するためにプロファイルのソースを信頼するプロンプト | iOS | **キャンセル** |
| iOSProfileLaunch | プロファイルがインストールされるまで [Installing profile]\(プロファイルのインストール\) 画面 | iOS | 30 分以上かかった |
| AndroidPermissions | [Device administrator activation]\(デバイス管理者のアクティブ化\) 画面 | Android | **キャンセル** |
| AndroidPermissions | デバイス管理者が **[アクティブ化]** されるまで電話をかけたり管理したりする承認のためのプロンプト | Android | 30 分以上かかった |
| KnoxActivation | KLMS エージェントのアクティブ化 (Samsung のみ) | Android| **キャンセル** |
| KnoxActivation | **[確認]** まで KLMS エージェントのアクティブ化 | Android | 30 分以上かかった|

#### <a name="terms-of-use-section"></a>[利用規約] セクション

| 破棄名 | 画面またはフロー | プラットフォーム | 操作 |
| ---- |---- |---- |---- |
| TermsofUse | (管理者が構成している場合) 利用規約 | iOS/Android | **すべて拒否** |
| TermsofUse | **[Accept all]** \(すべて承諾\) まで利用規約 | iOS/Android | 30 分以上かかった |

#### <a name="complianceactivation-section"></a>[コンプライアンス/アクティブ化] セクション

| 破棄名 | 画面またはフロー | プラットフォーム | 操作 |
| ---- |---- |---- |---- |
| コンプライアンス | 登録後のアクセス設定で (管理者が構成している場合) [デバイスのポリシー準拠] が緑色でない| iOS/Android | **延期** |
| コンプライアンス | 更新され緑色になるまで [デバイスのポリシー準拠] が緑色でない | iOS/Android | 30 分以上かかった |
| ライセンス認証 | アクセス設定で (管理者が構成している場合) [登録のアクティブ化] が緑色でない | iOS/Android | **延期** |
| コンプライアンス | 更新され緑色になるまで [デバイスの有効化] が緑色でない | iOS/Android | 30 分以上かかった |

## <a name="next-steps"></a>次の手順

破棄の割合を確認したら、登録を改善させるために変更できることはないか、[登録オプション](enrollment-options.md)に関するページを確認します。