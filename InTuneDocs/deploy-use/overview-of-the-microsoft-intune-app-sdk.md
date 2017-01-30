---
title: "Microsoft Intune アプリ SDK の概要 | Microsoft Docs"
description: "Intune アプリ SDK は、iOS プラットフォームと Android プラットフォームの両方で利用でき、Microsoft Intune を使ったモバイル アプリ管理機能が有効になります。"
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: oydang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f46f13e9dbf03fa2b3e2ec7339cad927ea0b38e0
ms.openlocfilehash: 99f3aa3c8640dd41133584b3e1cb056dfd493efa


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Microsoft Intune アプリ SDK の概要

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune アプリ SDK は、iOS プラットフォームと Android プラットフォームの両方で利用でき、Microsoft Intune を使ったモバイル アプリ管理機能が有効になります。 さらに、開発者が行う必要のあるコード変更の量を減らすことが図られています。

SDK の機能の大半は、アプリの動作を変更せずに利用できます。 エンド ユーザーと IT 管理者のエクスペリエンスを向上させるために、API を利用してアプリの動作をカスタマイズし、アプリ側の処理が必要な機能を実現できます。

アプリを有効にした後、IT 管理者は Intune で管理されたアプリにポリシーを展開し、これらの機能を活用して会社のデータを保護できます。

## <a name="features"></a>機能
### <a name="control-users-ability-to-move-corporate-documents"></a>ユーザーに会社のドキュメントの移動を許すかどうかを制御
IT 管理者は、Intune の管理対象アプリによる会社のドキュメントのファイル再配置を制御できます。 たとえば、会社のデータをファイル バックアップ アプリを使ってクラウドにバックアップすることができないようにするポリシーを展開できます。  

### <a name="configure-clipboard-restrictions"></a>クリップボードの制限の構成
IT 管理者は、Intune の管理対象アプリにおけるクリップボードの動作を構成できます。 たとえば、エンド ユーザーがクリップボードを使って Intune の管理対象アプリからデータを切り取るかコピーして、それを管理対象ではないアプリに貼り付けることができないよう、ポリシーを展開できます。

### <a name="enforce-encryption-on-saved-data"></a>保存データへの暗号化の適用
IT 管理者は、アプリによってデバイスに保存されたデータを確実に暗号化するポリシーを適用できます。

### <a name="remotely-wipe-corporate-data"></a>会社のデータのリモート ワイプ
デバイスが Microsoft Intune から登録解除されたときに、IT 管理者は、Intune の管理対象アプリからリモートで会社のデータをワイプできます。 これは ID ベースの機能で、エンドユーザーの社内 ID に関連するファイルのみが削除されます。 この機能を実行するには、アプリによる処理が必要です。 アプリは、ワイプする必要のある ID を、ユーザー設定を基に指定できます。 指定されたユーザー設定がアプリにない場合、既定の動作では、アプリケーションのディレクトリがワイプされ、エンド ユーザーに会社のリソースへのアクセスが削除されたことが通知されます。

### <a name="enforce-the-use-of-a-managed-browser"></a>管理対象ブラウザーの使用を強制
IT 管理者は、ユーザーが Intune の管理対象アプリの中からリンクを開くときに、強制的に管理対象ブラウザーを使用させることができます。 エンド ユーザーが Microsoft Intune の管理対象ブラウザーを使用すると、Intune の管理対象メール クライアント内のメールに表示されるリンクを、Intune の管理対象アプリのドメイン内に留めておくことができます。

### <a name="enforce-a-pin-policy"></a>暗証番号 (PIN) ポリシーの適用
IT 管理者は、Intune の管理対象アプリが開始するときに暗証番号 (PIN) ポリシーを適用できます。 このポリシーによって、Microsoft Intune を使用してデバイスを登録しているエンドユーザーとアプリを起動しているユーザーが同一であることを確認できます。 エンド ユーザーが自分の暗証番号 (PIN) を構成するとき、Intune アプリ SDK は Azure Active Directory を使用して、資格情報をデバイス登録資格情報に照らして確認します。

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>ユーザーは、アプリを起動する前に、資格情報を入力する必要があります。
IT 管理者は、エンド ユーザーが Intune の管理対象アプリを起動する前に、自分の資格情報を入力するように要求できます。 Intune アプリ SDK は、Azure Active Directory を使用して、シングル サインイン エクスペリエンスを提供します。 これは、入力された資格情報がその後のサインインに再利用されることを意味します。 SDK は、[Azure Active Directory とフェデレーション](/active-directory/active-directory-aadconnect-federation-compatibility)している ID 管理ソリューションの認証もサポートします。

### <a name="check-device-health-and-compliance"></a>デバイスのヘルスとコンプライアンスの確認
エンド ユーザーが Intune の管理対象アプリにアクセスする前に、IT 管理者は、デバイスのヘルスと企業のポリシーに対するコンプライアンスを確認できます。 iOS プラットフォームでは、このポリシーにより、デバイスが脱獄されているかどうかを確認できます。 Android プラットフォームでは、このポリシーにより、デバイスがルート化されているかどうかを確認できます。  



<!--HONumber=Dec16_HO3-->


