---
title: マネージド Android Enterprise デバイス用にアプリ構成ポリシーを追加する
titleSuffix: Microsoft Intune
description: Microsoft Intune 上でアプリ構成ポリシーを使用して、ユーザーがマネージド Google Play アプリを実行するときに設定を指定します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59d93bed7bae2b757a4bd1e7b1dffc814629f6a1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725739"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>マネージド Android Enterprise デバイス用にアプリ構成ポリシーを追加する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune でのアプリ構成ポリシーによって、マネージド Android Enterprise デバイス上でのマネージド Google Play アプリへの設定を指定します。 アプリ開発者は、Android によるマネージド アプリの構成設定を公開します。 Intune では、これらの公開された設定を使用して、管理者がアプリ用に機能を構成できるようにします。 アプリ構成ポリシーは、ユーザー グループに割り当てられます。 ポリシー設定は、アプリによってそのチェックが行われるとき (通常はアプリの初回実行時) に使用されます。

> [!NOTE]  
> アプリ構成をサポートしていないアプリもあります。 アプリ上でアプリ構成ポリシーがサポートされているかどうかを確認するには、アプリの開発者にお問い合わせください。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) で、**[クライアント アプリ]** > **[アプリ構成ポリシー]** >  **[追加]** の順に選択します。
2. 次のプロパティを入力します。

    - **名前**: ポリシーのわかりやすい名前を入力します。 後で簡単に識別できるよう、ポリシーに名前を付けます。 たとえば、適切なポリシー名は、**Android Enterprise Nine Work app policy for entire company (企業全体での Android Enterprise Nine Work アプリ ポリシー)** となります。
    - **説明**:プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[デバイス登録の種類]**:**[マネージド デバイス]** を選択します。
    - **[プラットフォーム]**:**[Android]** を選択します。

3. **[関連アプリ]** を選択します。 アプリ構成ポリシーを定義するアプリを選択します。 承認して Intune に同期したマネージド Google Play アプリの一覧から選択します。
4. **[アクセス許可]** を選択します。 以下を使用して構成を設定できます。

    - [構成デザイナー](#use-the-configuration-designer)
    - [JSON エディター](#enter-the-json-editor)

5. **[OK]** > **[追加]** の順に選択します。

## <a name="use-the-configuration-designer"></a>構成デザイナーを使用する

アプリが構成設定をサポートするように設計されている場合、マネージド Google Play アプリに対して構成デザイナーを使用できます。 構成は、Intune に登録されているデバイスに適用されます。 デザイナーを使用すると、アプリによつて公開された設定に対して特定の構成値を構成できます。

1. **[追加]** を選択します。 アプリに入力する構成設定の一覧を選択します。

    電子メール アプリに GMail または Nine Work を使用している場合、これらの設定の詳細については、[電子メールを構成するための Android Enterprise デバイス設定](../email-settings-android-enterprise.md)に関する記事を参照してください。

2. 構成の各キーと値について、以下を設定します。

    - **値の型**:構成値のデータ型。 文字列値の型については、必要に応じて、値の型として変数または証明書プロファイルを選択できます。
    - **構成値**:構成の値。 **[値の型]** に対して変数または証明書を選択する場合は、変数または証明書プロファイルの一覧から選ぶことができます。 証明書を選択する場合は、デバイスに展開された証明書の証明書エイリアスが実行時に設定されます。

### <a name="supported-variables-for-configuration-values"></a>構成値でサポートされる変数

値の型として変数を選択する場合は、次のオプションを選ぶことができます。

| オプション | 例 |
|----|----|
| メール | john@contoso.com |
| ユーザー プリンシパル名 | john@contoso.com |
| UPN の一部 | john |
| Domain | contoso.com |
| [ユーザー名] | John Doe |
| アカウント ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ユーザー ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| デバイス ID | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>複数 ID アプリで構成済みの組織アカウントのみを許可する 

Android デバイスでは、次のキー/値ペアを使用します。

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **値** | <ul><li>1 つまたは複数の<code>;</code> で区切られた UPN。</li><li>このキーで定義された管理対象のユーザー アカウントのみが許可されます。</li><li> Intune に登録されているデバイスでは、<code>{{userprincipalname}}</code> のトークンを使用して登録済みのユーザー アカウントを表すことができます。</li></ul> |

   > [!NOTE]
   > 複数 ID で構成された組織アカウントのみを許可する場合は、Outlook for Android 2.2.222 以降を使用する必要があります。<p></p>
   > Microsoft Intune 管理者として、マネージド デバイス上の Microsoft Office アプリケーションにどのユーザー アカウントを追加するかを制御できます。 許可されている組織ユーザー アカウントのみにアクセスを制限したり、登録済みデバイス上の個人アカウントをブロックしたりできます。 サポートされているアプリケーションがアプリの構成を処理し、未承認のアカウントを削除してブロックします。<p></p>
   > Microsoft Word、Microsoft Excel、Microsoft PowerPoint では、アプリ バージョン 16.0.9327.1000 以降を使用する必要があります。 

## <a name="enter-the-json-editor"></a>JSON エディターの入力

構成デザイナーでは構成できないアプリの構成設定もあります (バンドル タイプを利用するアプリなど)。 それらの値には、JSON エディターを使用します。 設定は、アプリのインストール時に自動で行われます。

1. **[構成設定の形式]** で、**[Enter JSON editor]\(JSON エディターを使用する\)** を選択します。
2. エディターでは、構成設定の JSON 値を定義できます。 **[Download JSON template]\(JSON テンプレートをダウンロードする\)** を選択して、構成に使用できるサンプル ファイルをダウンロードできます。
3. **[OK]** を選択してから、**[追加]** を選択します。

ポリシーが作成され、一覧に表示されます。

割り当てたアプリをデバイスで実行すると、アプリ構成ポリシーで構成した設定を使用して実行されます。

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>アプリのアクセス許可の状態を事前に構成する

Android デバイス機能にアクセスするために、アプリのアクセス許可を事前に構成することもできます。 既定では、場所やデバイス カメラへのアクセスなど、デバイスのアクセス許可を必要とする Android アプリは、アクセス許可の承諾または拒否をユーザーに求めます。

たとえば、アプリでは、デバイスのマイクを使用します。 ユーザーは、マイクを使用するためのアクセス許可をアプリに付与するように求められます。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) で、**[クライアント アプリ]** > **[アプリ構成ポリシー]** >  **[追加]** の順に選択します。
2. 次のプロパティを入力します。

    - **名前**: ポリシーのわかりやすい名前を入力します。 後で簡単に識別できるよう、ポリシーに名前を付けます。 たとえば、適切なポリシー名は、**Android Enterprise prompt permissions app policy for entire company (Android Enterprise による企業全体でのアプリ ポリシーへのアクセス許可の要求)** となります。
    - **説明**。 プロファイルの説明を入力します。 この設定は省略可能ですが、推奨されます。
    - **[デバイス登録の種類]**:**[マネージド デバイス]** を選択します。
    - **[プラットフォーム]**:**[Android]** を選択します。

3. **[関連アプリ]** を選択します。 構成ポリシーを定義するアプリを選択します。 承認して Intune に同期した Android 仕事用プロファイル アプリの一覧から選択します。
4. **[アクセス許可]** > **[追加]** の順に選択します。 一覧から、使用可能なアプリのアクセス許可を選び、**[OK]** を選択します。
5. このポリシーに付与するアクセス許可ごとにオプションを選択します。
    - **プロンプト**。 承諾または拒否をユーザーに求める
    - **自動許可**。 ユーザーに通知することなく自動的に承諾します。
    - **自動拒否**。 ユーザーに通知することなく自動的に拒否します。
6. アプリ構成ポリシーを割り当てるには、アプリ構成ポリシーを選択して、**[割り当て]** > **[グループの選択]** の順に選択します。 割り当てるユーザー グループを選び、**[選択]** を選択します。
7. **[保存]** を選択して、ポリシーを割り当てます。

## <a name="additional-information"></a>追加情報

- [マネージド Google Play アプリを Android Enterprise デバイスに割り当てる](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [iOS および Android 用 Outlook のアプリ構成設定の展開](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>次の手順

アプリの[割り当て](apps-deploy.md)と[監視](apps-monitor.md)に進みます。
