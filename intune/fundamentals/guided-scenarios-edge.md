---
title: ガイド付きシナリオ - モバイル用の Microsoft Edge を展開する
titleSuffix: Microsoft Intune
description: Microsoft 365 デバイス管理ポータルからモバイル用の Microsoft Edge を展開するためのガイド付きシナリオについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afb8f431ae301fe74f420c11205a7ed2637434b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514627"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>ガイド付きシナリオ - モバイル用の Microsoft Edge を展開する 

この[ガイド付きシナリオ](~/fundamentals/guided-scenarios-overview.md)に従うことで、組織の iOS/iPadOS、Android デバイスのユーザーに、Microsoft Edge アプリを割り当てることができます。 このアプリを割り当てると、ユーザーは会社のデバイスを使用してコンテンツをシームレスに参照できます。 

Microsoft Edge を使用すると、ユーザーは、作業内容の統合、配置、管理に役立つ組み込み機能を使用して、混乱した Web に対応できます。 Microsoft Edge アプリケーションで会社の Azure AD アカウントを使用してサインインした iOS/iPadOS および Android デバイスのユーザーは、定義した**お気に入り**ワークプレースと Web サイト フィルターがブラウザーに事前に読み込まれていることがわかります。

> [!NOTE]
> ユーザーが iOS/iPadOS、Android のデバイスを登録できないようにしてある場合、このシナリオでは登録できず、ユーザーは自分で Edge をインストールする必要があります。
Intune ポリシーによって有効化された次の Microsoft Edge エンタープライズ機能が含まれます。 

- **デュアル ID** -ユーザーは、閲覧用に、個人アカウントに加えて、職場アカウントを追加できます。 2 つの ID の間は完全に分離されており、Office 365 と Outlook のアーキテクチャとエクスペリエンスに似ています。 Intune 管理者は、職場アカウント内に保護された閲覧エクスペリエンス用の必要なポリシーを設定できます。 
- **Intune アプリ保護ポリシーの統合**- 管理者は、切り取り、コピー、貼り付けの制御、画面キャプチャの禁止、ユーザーが選択したリンクを他の管理対象アプリでのみ開けるようにするなどのアプリ保護ポリシーの対象として Microsoft Edge を指定できるようになりました。
- **Azure アプリケーション プロキシの統合**- エンドユーザーが企業ネットワークから接続するか、インターネットから接続するかに関係なく、管理者は SaaS アプリおよび Web アプリへのアクセスを制御し、ブラウザー ベースのアプリをセキュリティで保護された Microsoft Edge ブラウザーでのみ実行させることができます。 
- **管理されたお気に入りとホーム ページのショートカット** - 管理者は、企業コンテキスト内のエンドユーザーがアクセスしやすいように、[お気に入り] の下に表示される URL を設定できます。 管理者は、企業ユーザーが Microsoft Edge で新しいページまたは新しいタブを開いたときに、プライマリ ショートカットとして表示されるホームページ ショートカットを設定できます。

## <a name="prerequisites"></a>[前提条件]

- [MDM 機関を Intune に設定する](mdm-authority-set.md#set-mdm-authority-to-intune) - モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。
- 必要な Intune 管理者アクセス許可:
    - マネージド アプリの読み取り、作成、削除、割り当てのアクセス許可
    - モバイル アプリの読み取り、作成、割り当てのアクセス許可
    - ポリシー セットの読み取り、作成、割り当てのアクセス許可
    - 組織の読み取り、更新のアクセス許可

## <a name="step-1---introduction"></a>ステップ 1 - 概要

**モバイル用の Microsoft Edge の展開**に関するガイド付きシナリオに従って、選択した iOS/iPadOS および Android のユーザー グループに対して Microsoft Edge の基本的な展開を設定します。 この展開では、**デュアル ID** と**管理対象のお気に入りとホーム ページのショートカット**を実装します。 さらに、選択したユーザーによって登録されたデバイスには、Intune によって Microsoft Edge アプリが自動的にインストールされます。 この自動インストールは、次のようなすべてのユーザー主導の登録の種類で行われます。 
- Intune ポータル サイト アプリを使用した iOS/iPadOS の登録 
- Apple Business Manager を使用した iOS/iPadOS ユーザー アフィニティの登録 
- Intune ポータル サイト アプリを使用したレガシ Android の登録 

このガイド付きシナリオでは、**MyApps** を Microsoft Edge のお気に入りに自動的に表示できるようにし、Intune ポータル サイト アプリに設定したのと同じブランドでブラウザーを構成します。 

### <a name="what-you-will-need-to-continue"></a>続けるために必要なこと
ユーザーが必要とするワークプレースのお気に入りと、Web 閲覧に必要なフィルターについて質問します。 続ける前に、次のタスクを完了していることを確認してください。

- Azure AD のグループにユーザーを追加します。 詳細については、「[Azure Active Directory を使用して基本グループを作成してメンバーを追加する](https://go.microsoft.com/fwlink/?linkid=2102458)」を参照してください。
- Intune で iOS、iPadOS または Android デバイスを登録します。 詳細については、[デバイスの登録](https://go.microsoft.com/fwlink/?linkid=2102547)に関する記事を参照してください。
- Microsoft Edge に追加するワークプレースのお気に入りの一覧を収集します。
- Microsoft Edge で適用する Web サイト フィルターの一覧を収集します。

## <a name="step-2---basics"></a>ステップ 2 - 基本

このステップでは、新しい Microsoft Edge ポリシーの名前と説明を入力する必要があります。 これらのポリシーは、割り当てと構成を変更する必要がある場合、後で参照できます。 このガイド付きシナリオでは、iOS/iPadOS デバイス用の Microsoft Edge iOS/iPadOS アプリと、Android デバイス用の Microsoft Edge Android アプリの両方を追加して割り当てます。 また、このステップでは、これらのアプリの構成ポリシーを作成します。

## <a name="step-3---configuration"></a>ステップ 3 - 構成

ガイド付きシナリオのこのステップでは、Intune を使用してユーザーに割り当てられている他のすべてのアプリが表示され、Microsoft Intune ポータル サイト アプリと同じブランドが共有されるように、Microsoft Edge を構成します。 さらに、**ホーム ページのショートカット URL**、**マネージド ブックマーク**の一覧、および**ブロックされている URL** の一覧で、Microsoft Edge を構成することもできます。 **ホーム ページのショートカット URL** は、デバイスの Microsoft Edge で新しいタブを開いたときに、検索バーの下に最初のアイコンとして、ユーザーに表示されます。 **マネージド ブックマーク**は、ユーザーが作業コンテキストで Microsoft Edge を使用するときに使用できるお気に入りの URL の一覧です。 **ブロックされた URL** では、ユーザーが作業コンテキストでブロックされるサイトが指定されています。 その他のサイトはすべて許可されます。 

## <a name="step-4---assignments"></a>ステップ 4 - 割り当て

このステップでは、Microsoft Edge モバイルを動作させる構成に含めるユーザー グループを選択できます。 Microsoft Edge は、これらのユーザーが登録したすべての iOS/iPadOS および Android のデバイスにもインストールされます。

## <a name="step-5---review--create"></a>ステップ 5 - 確認と作成

最後のステップでは、構成した設定の概要を確認できます。 選択内容を確認した後、 **[作成]** をクリックしてガイド付きシナリオを完了します。 

> [!NOTE]
> Edge が構成を受け取るまでに、最大で 12 時間かかる場合があります。 詳細については、「[Microsoft Intune 用アプリ構成ポリシー](~/apps/app-configuration-policies-overview.md)」を参照してください。

> [!IMPORTANT]
> ガイド付きシナリオが完了すると、概要が表示されます。 概要の一覧で示されているリソースを後で変更できますが、これらのリソースが表示されているテーブルは保存されません。

## <a name="next-steps"></a>次のステップ

- Intune アプリ保護ポリシーの統合を設定して、Microsoft Edge の使用のセキュリティを強化します。 詳細については、「[Microsoft Edge のアプリケーション保護ポリシー](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge)」を参照してください。
- 含めるイントラネット サイトがある場合は、Azure アプリケーション プロキシの統合によるアクセスの保護を確認してください。 詳細については、「[Microsoft Edge 用にアプリケーション プロキシの設定を構成する](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge)」を参照してください。

