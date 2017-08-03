---
title: "記事のタイトル | サービス名"
description: 
keywords: 
author: GITHUB USERNAME
manager: ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: GET ONE FROM guidgenerator.com
ms.openlocfilehash: 68090a038cec49009b6bd0ce0515a075f62483b8
ms.sourcegitcommit: 02fb1274ae0dc11288f8bd9cd4799af144b8feae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2017
---
# <a name="metadata-and-markdown-template"></a>メタデータとマークダウン テンプレート

この docs.ms テンプレートには、メタデータの設定に関するガイドラインとマークダウン構文のサンプルが含まれています。 各 EM パイロット リポジトリのルート ディレクトリ (例： ~/Azure-RMSDocs-pr /template.md) で入手し、[公開済みのバージョン](https://stage.docs.microsoft.com/en-us/rights-management/template)を参照してマークダウン サンプルがどのように表示されるのかを確認できますが、読み取り専用のマークダウン ファイルとして提供されています。

マークダウン ファイルを作成する場合、テンプレートを新しいファイルにコピーし、次に指定するメタデータを入力し、上の H1 見出しを本記事のタイトルに設定して、コンテンツを削除します。 


## <a name="metadata"></a>メタデータ 

完全なメタデータ ブロックは上部で必要なフィールドと省略可能なフィールドに分けられます。詳細については、「[OPS metadata cheatsheet (OPS メタデータ チートシート)](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data)」をご覧ください。 注記: 

- コロン (:) とメタデータ要素の値との間にスペースを入れる**必要があります**。
- 省略可能なメタデータ要素が値を持たない場合は、その要素を # でコメント アウトします (空欄にしたり "na" を使用したりしないでください)。コメント アウトした要素に値を追加する場合は、忘れずに # を削除してください。
- 値 (title など) に使用するコロンはメタデータ パーサーを中断します。 代わりに HTML エンコーディングの &#58; を使用します ("title: Azure Rights Management&#58; 基本情報 | Azure RMS" など)。
- **title**: このタイトルは検索エンジンの結果に表示されます。 タイトルの後ろにパイプ (|) を付け、サービス名を入れる必要があります (前述の例のように)。 このタイトルを H1 見出しのタイトルと同じにする必要はありません (変えることをお勧めします)。 65 文字前後に収めます ("| サービス名" も含め)。
- **author**、**manager**、**reviewer**: author フィールドには、エイリアスではなく、作成者の **Github ユーザー名** を含める必要があります。  一方、"manager" と "reviewer" フィールドにはエイリアスを含める必要があります。 ms.reviewer は記事またはサービスに関連付けられている PM の名前を指定します。
- **ms.assetid**: CAPS からの記事の GUID です。 新しいマークダウン ファイルを作成する場合、[https://www.guidgenerator.com](https://www.guidgenerator.com) から GUID を取得します。 
- **ms.prod**、**ms.service**、**ms.technology**、**ms.devlang**、**ms.topic**、**ms.tgt_pltfrm**: これらの要素で利用可能な値は、[こちら](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default)で検索できます。

## <a name="basic-markdown-and-gfm"></a>基本的なマークダウンと GFM

すべての基本的なマークダウンと Github Flavored Markdown がサポートされています。 詳細については、次をご覧ください。

- [ベースライン マークダウン構文](https://daringfireball.net/projects/markdown/syntax)
- [Github Flavored Markdown (GFM) ドキュメント](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>見出し

第 1 レベルと第 2 レベルの見出しの例は前述のとおりです。 

トピックには第 1 レベルの見出しを 1 つのみ含める**必要があります**。この見出しはページ タイトルとして表示されます。  

第 2 レベルの見出しは、ページ タイトルの下の "この記事では" セクションに表示されるページ上の目次を生成します。

### <a name="third-level-heading"></a>第 3 レベルの見出し
#### <a name="fourth-level-heading"></a>第 4 レベルの見出し
##### <a name="fifth-level-heading"></a>第 5 レベルの見出し
###### <a name="sixth-level-heading"></a>第 6 レベルの見出し

## <a name="text-styling"></a>テキスト スタイルの設定

*斜体* 

**太字** 

~~取り消し線~~



## <a name="links"></a>Links

同じリポジトリ内のマークダウン ファイルにリンクさせるには、[相対リンク](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)を使用します。 

- 例: [Azure Rights Management とは](./understand-explore/what-is-azure-rights-management.md)

同じマークダウン ファイル内の見出しにリンクさせるには、公開された記事のソースを表示して見出しの ID を見つけます (例: `id="blockquote"`、あるいは `#blockquote` のように # + id を使用したリンク)。

- 例: [Blockquotes](#blockquote)

同じリポジトリ内のマークダウン ファイルにリンクさせるには、相対リンクとハッシュタグ リンクを使用します。

- 例: [サインアップ プロセスの技術概要](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

外部ファイルにリンクさせるには、完全な URL をリンクに使用します。

- 例: [Github](http://www.github.com)

マークダウン ファイルに URL が表示されると、クリック可能なリンクに変換されます。

- 例: http://www.github.com

## <a name="lists"></a>リスト

### <a name="ordered-lists"></a>順序指定された一覧

1. この 
1. リスト
1. は
1. Ordered
1. 一覧  


#### <a name="ordered-list-with-an-embedded-list"></a>埋め込みリストを含む順序指定された一覧

1. Here
1. こちら
1. は
1. 埋め込まれた
    1. Miss Scarlett
    1. Professor Plum
1. 順序指定された
1. リスト


### <a name="unordered-lists"></a>順序指定されていない一覧

- この
- 次の文字列と同じ:
- a
- 箇条書き
- リスト


##### <a name="unordered-list-with-an-embedded-lists"></a>埋め込みリストを含む順序指定されていない一覧

- この 
- 箇条書き 
- リスト
    - Mrs. Peacock
    - Mr. Green
- 次の値を含む  
- その他
    1. Colonel Mustard
    1. Mrs. White
- リスト


## <a name="horizontal-rule"></a>水平線

---

## <a name="tables"></a>テーブル

| テーブル        | も           | 作れます  |
| ------------- |:-------------:| -----:|
| col 3 は      | 右揃え | $1600 |
| col 2 は      | 中央揃え      |   $12 |
| col 1 が既定 | 左揃え     |    $1 |


## <a name="code"></a>コード

### <a name="codeblock"></a>コードブロック

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>インライン コード

これは `in-line code` の例です。

## <a name="blockquotes"></a>Blockquotes

> 干ばつは 1000 万年も続き、恐竜の治世はとうに終わっていた。 ここ、赤道地帯、いずれアフリカと呼ばれるようになる大陸では、生存の戦いは熾烈なクライマックスを迎えていたが、勝者はまだ現れていなかった。 この乾燥した不毛の大地では、小さなもの、すばしこいもの、どう猛なもののみ栄えることができ、また生存の望みをつなぐことができた。

## <a name="images"></a>画像

### <a name="static-image"></a>静止画像

![これは代替テキストです](./media/AzRMS_elements.png)

### <a name="linked-image"></a>リンクされた画像

[![リンク画像のテキスト](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>アニメーション GIF

![アニメーション GIF](./media/hololens.gif)

## <a name="alerts"></a>アラート

### <a name="note"></a>メモ

> [!NOTE]
> これは注記です

### <a name="warning"></a>警告

> [!WARNING]
> これは警告です

### <a name="tip"></a>ヒント

> [!TIP]
> これはヒントです

### <a name="important"></a>重要

> [!IMPORTANT]
> これは重要事項です

## <a name="videos"></a>ビデオ

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms 拡張子

### <a name="button"></a>Button

> [!div class="button"]
[ボタン リンク](/rights-management)

### <a name="selector"></a>セレクター

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### <a name="step-by-step"></a>ステップ バイ ステップ

>[!div class="step-by-step"]
[前へ](https://www.example.com)
[次へ](https://www.example.com)