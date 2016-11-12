---
title: "アプリケーションのロールアウト | Microsoft Intune"
description: "Microsoft Intune でアプリを段階的にロールアウトする場合の推奨事項。"
keywords: 
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8921043334630bbd2955c0423ca9cd1b76c27758
ms.openlocfilehash: aea7c235ad643a2a03ac7b3ea68c6b8c717bcd48


---

# アプリケーションのロールアウト
このトピックでは、Microsoft Intune でアプリを段階的にロールアウトする場合の推奨事項を具体的に説明します。 ロールアウトのフェーズの詳細については、「[Microsoft Intune のロールアウト フェーズ](rollout-phases-for-microsoft-intune-deployment.md)」をご覧ください。

### アプリのロールアウトの段階
アプリのロールアウトの各段階は、以下のとおりです。

-   プロジェクト スコープ

-   概念実証

-   パイロット運用

-   企業でのロールアウト

-   運用とメンテナンス

## プロジェクト スコープ
次の点を考慮します。

-   アプリによって有効になるユーザー タスク。

-   ユーザーとユーザーのデバイス (使用される可能性のあるすべてのオペレーティング システム) に対するアプリの適合性。

-   「[Microsoft Intune でアプリを追加する](/intune/deploy-use/add-apps)」の説明に従い、選択したアプリのインストーラーが Intune のアプリの配布でサポートされていることを確認します。

-   アプリ配布の前提条件がインストールされていることを確認します。 <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md).--->

-   Intune でアプリの種類がサポートされていることを確認します。

-   アプリをアップロードするのに十分な容量のクラウド記憶域があることを確認します。 追加の記憶域を購入する手順については、「[Microsoft Intune でアプリを追加する](/intune/deploy-use/add-apps)」で説明しています。

> [!NOTE]           
> この[モバイル アプリ向けの計画に関するテンプレート](https://gallery.technet.microsoft.com/Mobile-app-planning-18689d59)をダウンロードすると、ロールアウト プロセスに役立ちます。

## 概念実証
概念実証の段階では、テスト用に厳密に構成したデバイスおよびユーザーのラボ環境で、アプリを展開してテストします。

-   このフェーズでヘルプ デスクを参加させ、パイロット運用や運用環境の展開でどのような問題が発生する可能性があるか学習させます。 トラブルシューティングの情報については、「[Microsoft Intune のポリシーのトラブルシューティング](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)」を参照してください。

-   手順のこの段階で、パイロットおよび運用環境ユーザーにコミュニケーション計画を作成します。 計画には少なくとも、展開の対象となるアプリ、ユーザーがアプリを入手する時期と方法、展開のビジネス上の目的、問題が発生した場合の対処方法 (セルフヘルプ情報およびヘルプ デスクへの連絡方法の両方) が含まれている必要があります。

## パイロット運用
パイロット運用中は、小人数のテスト ユーザーやデバイスのグループにアプリを展開します。 次の点を考慮します。

-   テスト グループが、運用環境へのロールアウト後にアプリを使用するユーザーやデバイスの代表者で構成されていることを確認します。

-   アプリの展開についてヘルプ デスク向けの教育を実施し、テスト グループのユーザーを支援するための準備を整えます。

-   アプリを通常の方法で使用し、パイロット管理者に対して問題の報告を確実に行えるテスト ユーザーを選抜します。

-   パイロット ユーザーのコミュニケーション計画を有効にします。

## 企業でのロールアウト

-   パイロット運用の結果に基づき、全社的なロールアウトの調整を行います。

-   アプリのロールアウト スケジュールをヘルプ デスクに通知します。 ヘルプ要請に対応できる仕組みを用意し、必要に応じてロールアウトを調整します。

-   問題が発生した場合に、展開のトラブルシューティングを行える準備をします。

-   運用環境のユーザーのコミュニケーション計画を有効にします。

-   段階的なアプローチでアプリを展開し、グループを徐々に追加して、ロールアウトのスムーズな進行を確保します。

## 運用とメンテナンス
**運用:** Intune コンソールでアラートおよびユーザーやデバイスの問題を監視し、アプリケーションの配布が計画に従って実行されていることを確認します。

**ヘルプ デスク:** サポート リクエストにつながる可能性のあるアプリの入手に関する変更点について、ヘルプ デスクへの周知を徹底します。

### 関連項目
[アプリの展開](/intune/deploy-use/deploy-apps)

[Microsoft Intune のアプリ展開に関する問題のトラブルシューティング](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)



<!--HONumber=Oct16_HO4-->


