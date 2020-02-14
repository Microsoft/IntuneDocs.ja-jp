---
title:
- 記事のタイトル | サービス名
description: ''
keywords: ''
author:
- GITHUB USERNAME
manager:
- ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid:
- GET ONE FROM guidgenerator.com
ms.openlocfilehash: ed2d00541c2d89efd0f8cd6aa60f29c527656fc0
ms.sourcegitcommit: 5178aec0244e023e73546f3d10f1a76eaf1f4a3e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971815"
---
# <a name="metadata-and-markdown-template"></a>メタデータとマークダウン テンプレート

この docs.ms テンプレートには、メタデータの設定に関するガイダンスとマークダウン構文のサンプルが含まれています。 各 EM パイロット リポジトリのルート ディレクトリ (例： ~/Azure-RMSDocs-pr /template.md) で入手し、[公開済みのバージョン](https://stage.docs.microsoft.com/en-us/rights-management/template)を参照してマークダウン サンプルがどのように表示されるのかを確認できますが、読み取り専用のマークダウン ファイルとして提供されています。

マークダウン ファイルを作成する場合、テンプレートを新しいファイルにコピーし、次に指定するメタデータを入力し、上の H1 見出しを本記事のタイトルに設定して、コンテンツを削除します。 


## <a name="metadata"></a>メタデータ 

完全なメタデータ ブロックは上部で必要なフィールドと省略可能なフィールドに分けられます。詳細については、「[OPS metadata cheatsheet (OPS メタデータ チートシート)](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data)」をご覧ください。 一部の重要な注意事項を以下に挙げます。

- コロン (:) とメタデータ要素の値との間にスペースを入れる**必要があります**。
- 省略可能なメタデータ要素が値を持たない場合は、その要素を # でコメント アウトします (空欄にしたり "na" を使用したりしないでください)。コメント アウトした要素に値を追加する場合は、忘れずに # を削除してください。
- 値にコロンが含まれていると (例: タイトル) 、メタデータのパーサーが正常に機能しません。 代わりに、HTML エンコード &#58; を使用します (例: "タイトル:Azure Rights Management&#58; 基本 | Azure RMS")。
- **タイトル**:このタイトルが検索エンジンの結果に表示されます。 タイトルは、末尾にパイプ (|) を付け、その後にサービス名を付ける必要があります (例: 上の方をご覧ください)。 タイトルと H1 見出しを一致させる必要はありません (おそらく、一致させないほうがよいでしょう)。 だいたい 65 文字まで ("| サービス名" を含む) にします。
- **作成者**、**管理者**、**レビュー担当者**:作成者フィールドには、作成者のエイリアスではなく、**Github のユーザー名**を含める必要があります。  反対に、"管理者" と "レビュー担当者" フィールドにはエイリアスを含める必要があります。 ms.reviewer は記事またはサービスに関連付けられている PM の名前を指定します。
- **ms.assetid**:これは CAPS の記事の GUID です。 新しいマークダウン ファイルを作成する場合は、[https://www.guidgenerator.com](https://www.guidgenerator.com) から GUID を取得します。 
- **ms.prod**、**ms.service**、**ms.technology**、**ms.devlang**、**ms.topic**、**ms.tgt_pltfrm**:これらの要素に使用できる値については、[こちら](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default)を参照してください。

## <a name="basic-markdown-and-gfm"></a>基本的な Markdown と GFM

基本的なマークダウンと GitHub フレーバー Markdown はすべてサポートされています。 これらについて詳しくは、以下のページをご覧ください。

- [マークダウンの基本的な構文](https://daringfireball.net/projects/markdown/syntax)
- [GitHub フレーバー Markdown (GFM) のドキュメント](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>見出し

第 1 レベルと第 2 レベルの見出しのサンプルは上部をご覧ください。 

第 1 レベルの見出しは、**必ず**各トピックに 1 つしかないようにします。この見出しは、ページ上のタイトルとして表示されます。  

第 2 レベルの見出しは、ページ内のタイトルの下にある "この記事内" セクションに表示されるページ内の内容一覧を生成します。

### <a name="third-level-heading"></a>第 3 レベルの見出し
#### <a name="fourth-level-heading"></a>第 4 レベルの見出し
##### <a name="fifth-level-heading"></a>第 5 レベルの見出し
###### <a name="sixth-level-heading"></a>第 6 レベルの見出し

## <a name="text-styling"></a>テキストのスタイル設定

*斜体* 

**太字** 

~~取り消し線~~



## <a name="links"></a>Links

同じリポジトリ内のマークダウン ファイルにリンクするには、[相対リンク](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)を使用します。 

- 例:[Azure Rights Management の概要](./understand-explore/what-is-azure-rights-management.md)

同じマークダウン ファイル内のヘッダーにリンクするには、公開済みの記事のソースを確認して、先頭の ID を見つけます (例: `id="blockquote"`、であるとして、# と ID を使用してリンクします (例: `#blockquote`)。

- 例:[ブロック引用](#blockquote)

同じリポジトリ内のマークダウン ファイルのヘッダーにリンクするには、相対リンクとハッシュタグ リンクを使用します。

- 例: [サインアップ プロセスの技術概要](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

外部ファイルにリンクするには、完全 URL をリンクとして使用します。

- 例:[Github](http://www.github.com)

マークダウン ファイル内に URL がある場合は、クリック可能なリンクに変換されます。

- 例: http://www.github.com

## <a name="lists"></a>リスト

### <a name="ordered-lists"></a>順序指定された一覧

1. これ 
1. が
1. 順序指定済み
1. Ordered
1. 一覧  


#### <a name="ordered-list-with-an-embedded-list"></a>埋め込みリストを含む順序指定された一覧

1. これ
1. が
1. 埋め込み
1. リスト付きの
    1. Miss Scarlett
    1. Plum 教授
1. 順序指定された
1. 一覧


### <a name="unordered-lists"></a>順序指定されていない一覧

- これが
- 次の文字列と同じ:
- a
- 埋め込み
- 一覧


#### <a name="unordered-list-with-an-embedded-lists"></a>埋め込みリストを含む順序指定されていない一覧

- これが 
- 箇条書き 
- 一覧
  - Mrs. Peacock
  - Mr. Green
- 次の値を含む  
- その他
    1. Mustard 大佐
    1. Mrs. White
- リストです


## <a name="horizontal-rule"></a>水平線

---

## <a name="tables"></a>テーブル

| テーブル        | も           | クール  |
| ------------- |:-------------:| -----:|
| 列 3 は      | 右揃え | $1600 |
| 列 2 は      | 中央揃え      |   $12 |
| 列 1 は規定値 | 左揃え     |    $1 |


## <a name="code"></a>コード

### <a name="codeblock"></a>コードブロック

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>インライン コード

これは `in-line code` のサンプルです。

## <a name="blockquotes"></a>ブロック引用

> 干ばつはすでに 1000 万年も続いていました。恐竜が君臨した時代はとうに終わっていたのです。 ここ赤道上の、いずれアフリカと呼ばれることになる大陸では、生存をかけた争いがこれまでにないほど苛烈を極め、もはや勝者の姿も無くなっていました。 この乾燥した不毛の大地では、小さなもの、すばしこいもの、どう猛なもののみ栄えることができ、また生存の望みをつなぐことができた。

## <a name="images"></a>画像

### <a name="static-image"></a>静止画像

![これは代替テキストです](./media/AzRMS_elements.png)

### <a name="linked-image"></a>リンクされているイメージ

[![リンクされている画像の代替テキスト](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

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

## <a name="docsms-extensions"></a>docs.ms 拡張機能

### <a name="button"></a>Button

> [!div class="button"]
[ボタン リンク](/rights-management)

### <a name="selector"></a>セレクター

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### <a name="step-by-step"></a>詳細な手順

>[!div class="step-by-step"]
[前へ](https://www.example.com)
[次へ](https://www.example.com)
