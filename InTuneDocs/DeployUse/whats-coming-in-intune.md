---
title: "今後予定されている機能 | Microsoft Intune"
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52b9e786fe22b04081441db88a3629062fc85668
ms.openlocfilehash: 0949172a7b8517b12fb46e8fd1f8a3cd70d93099


---

# Microsoft Intune に今後予定されている機能
ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 定期的にこちらのページをご覧のうえ最新の機能をチェックしてください。

Intune に関して以下の機能が現在開発されています。 これらのすべての機能は、最終的にハイブリッド環境 (Configuration Manager と Intune の共存環境) でサポートされるようになります。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)を参照してください。


## アプリ管理
### iOS 9.3 で表示されないアプリと表示されるアプリ
iOS 9.3 以降を実行する管理されたデバイスでは、iOS の一般構成ポリシーの表示されないアプリと表示されるアプリのリストを使用して次のことができます。
- ユーザーに対して表示されないアプリの一覧を指定します。 ユーザーはこのようなアプリを表示または起動できません。
- ユーザーが表示および起動できるアプリの一覧を指定します。 他のアプリは表示または起動できません。

ユーザー自身が展開したアプリと、Messages や Notes などの iOS 組み込みアプリの両方を指定できます。
<!---TFS 1279009--->

### Samsung KNOX デバイスでの許可するアプリとブロックするアプリのポリシー

Samsung KNOX デバイスでは、次のいずれかを作成できるカスタム ポリシーを構成できます。
- デバイスでの実行をブロックするアプリの一覧。 ブロック リストで定義されているアプリは、インストールされている場合でも、デバイスでアクティブにできません。
- デバイスのユーザーが Google Play ストアからインストールできるアプリの一覧。 他のアプリはストアからインストールできません。

これらの設定は、Samsung KNOX を実行するデバイスでのみ使用できます。
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### モバイル アプリケーション管理 (MAM) ポリシーと互換性のある新しいアプリ
[iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) および [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) 向けの Yammer アプリは、デバイスが登録されていてもいなくても、[Intune バイル アプリケーション管理 (MAM) ポリシー](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)と互換性があります。

MAM と互換性のある全アプリの一覧については、[Microsoft Intune アプリケーション パートナー](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners)のサイトをご覧ください。
<!--- TFS 1252335 & 1252336--->

## デバイス管理
### Android 7.0 のサポート
8 月には、Intune は近日公開予定のモバイル デバイス向け Android 7.0 オペレーティング システムの "Day 0" サポートを提供します。
<!---TFS 1262053--->
### Google による Android 7.0 デバイスでのリモート パスコード リセット機能の削除
Google は、IT 管理者やエンド ユーザーが Android 7.0 デバイスのパスコードをリモートでリセットする機能を削除しています。 これまでは、IT 管理者はユーザーのパスコードをリモートでリセットでき、エンド ユーザーはポータル サイトから自分のパスコードをリセットできました。

## グループ管理
### Intune グループから Azure Active Directory グループへの移行 (2016年 9 月以降)
Intune は、Intune でのユーザーとデバイスのグループとして Azure Active Directory (AAD) のセキュリティ グループを使用する、新しいグループ管理エクスペリエンスを作成しています。 これらのグループは、**新しい Azure ベースの Intune 管理ポータルの導入時**に、すべてのグループの管理、ポリシーの展開、およびプロファイルの展開に使用されます。

この新しいエクスペリエンスにより、サービス間でグループを複製する必要がなくなり、**新しい Azure Active Directory Premium (AADP) グループ機能の一部にアクセスすることができ** 、PowerShell および Graph を使用して拡張機能を提供します。 またこれにより、エンタープライズ モビリティ管理でのグループ管理エクスペリエンスも統合されます。

セキュリティ グループへの移行を有効にするため、**現在の管理コンソール**のエクスペリエンスにいくつかの変更が施されます。 **これらの変更と、AAD セキュリティ グループの使用については、Intune のドキュメントに記録されます**。

Intune の新規のお客様には、**現在のテナントに表示される前に、セキュリティ グループの変更の一部**が表示されます。

グループ管理の変更に加えて、**次の機能が廃止される予定です**。
- 新規グループ作成時のメンバーまたはグループの除外
- **グループ化を解除されたユーザー**と**グループ化を解除されたデバイス**のグループ
- サービス管理者の役割での**グループの管理**
- 通知ルールに対するカスタム グループベースの警告
- レポート内のグループのピボット
<!--- TFS 1295329--->

## 廃止予定のサービス
### Windows 8 および Windows Phone 8 用のポータル サイト アプリは、2016 年 9 月以降は非推奨になる
2016年 10 月以降、Microsoft Intune は Windows 8 および Windows Phone 8 ポータル サイト アプリのサポートを廃止します。 Microsoft Intune は、Windows Phone 8 プラットフォームのサポートも廃止します。 その結果、Windows Phone 8 デバイスの登録または更新はできなくなります。 既に登録されている Windows Phone 8 および Windows 8 デバイスは継続して管理できます。 デバイスへのアプリの配布を中断することなく続行するには、Windows Phone 8 および Windows 8 デバイスを Windows 8.1 および Windows Phone 8.1 に更新し、対応する Windows 8.1 および Windows Phone 8.1 のポータル サイト アプリを使用します。
<!---TFS 1255391--->

### カスタム グループを対象とした通知規則の廃止
Intune の通知規則では、Intune からの電子メール アラートの送信先が定義されます。 現時点では、作成した Intune デバイス グループ内のデバイスのすべてのユーザーに電子メールを送信するように通知規則を構成することができます。 2016年 6 月以降、ユーザーが作成したグループは対象にできなくなります。

この変更に向けた準備は次のように予定されています。
- 2016 年 9 月に、新しいテナントでは通知規則の作成ウィザードの手順 2 が表示されなくなります。 既存のテナントは影響を受けません。
- 2016 年 10 月頃に、既存の一部のテナントではウィザードの "デバイス グループの選択" が表示されなくなります。
- 将来的に、すべてのテナントでウィザードの "デバイス グループの選択" が表示されなくなる予定です。

<!---   TFS 1278864--->
### iOS ポータル サイト アプリのサポートの変更
9 月には、iOS 用 Microsoft Intune ポータル サイト アプリのすべてのユーザーが、アプリの最新バージョンを使用するように要求されます。 新しいユーザーは最新バージョンのみをダウンロードでき、現在のユーザーは最新バージョンへの更新を求められます。 最新バージョンを使用するには iOS 8.0 以降が必要であり、デバイスで以前の iOS バージョンを実行している場合は、デバイスを iOS 8.0 以降に更新したうえでポータル サイト アプリを最新バージョンに更新するまで、ポータル サイトを使用できず、登録することもできません。 iOS 8.0 以前のバージョンを実行している登録済みのデバイスは、引き続き管理対象であり、Intune 管理コンソールに表示されます。

<!---TFS 1283165--->


### Intune Viewer アプリ
新しい RMS 共有アプリのリリースに伴い、2016 年 8 月には、次の Intune Viewer アプリを削除する予定です。
- Intune AV Viewer
- Intune PDF Viewer
- Google Play の Android 用 Intune Image Viewer

Intune Viewer アプリを使用する代わりに、Android 用の新しい Rights Management アプリ (RMS 共有) を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 RMS 共有アプリの詳細については、[こちら](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app)をご覧ください。
<!--- goes in 1608 What's New--->


### 関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。



<!--HONumber=Sep16_HO3-->


