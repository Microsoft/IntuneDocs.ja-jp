---
title: 会社所有または会社提供の macOS デバイスを管理対象に登録する | Microsoft Docs
description: 組織が購入して提供している macOS デバイスを Intune に登録する方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 272a82f7d3d62d117fa5506ccf446b3169ff514f
ms.sourcegitcommit: bb56ada81e6d4950f130415918c4acc455bb52dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43016229"
---
# <a name="get-your-company-owned-macos-device-managed"></a>会社所有の macOS デバイスを管理対象にする

新しい macOS デバイスを Intune で自動的に管理されるようにする方法について説明します。

職場または学校が所有するデバイスは、ユーザーに提供される前に既に構成されていることがよくあります。 ユーザーが初めてデバイスの電源を入れてサインインすると、組織から事前構成済みの設定がデバイスに送信されます。 デバイスのセットアップが完了すると、職場または学校のリソースにアクセスできるようになります。 

管理のセットアップを始めるには、デバイスの電源を入れて、職場または学校の資格情報でサインインします。 以下では、セットアップ アシスタントを使用する手順と表示される画面について説明します。   

## <a name="what-is-apple-dep"></a>Apple DEP とは
会社所有のデバイスを使用している場合、Apple Device Enrollment Program (DEP) から購入されている可能性があります。 組織によっては、Apple DEP を通じて iOS デバイスまたは macOS デバイスを大量に購入することがあります。 その後、組織は Intune などの適切なモバイル デバイス管理プロバイダーでデバイスを構成して管理できます。 Apple DEP についての情報がさらに必要な管理者は、「[Apple の Device Enrollment Program を使用して macOS デバイスを自動登録する](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos)」をご覧ください。  

## <a name="set-up-your-macos-device"></a>macOS デバイスを設定する  
macOS デバイスを管理対象に登録するには、次の手順のようにします。 会社所有のデバイスではなく個人所有のデバイスを使用している場合は、[個人デバイスと Bring Your Own デバイス](enroll-your-device-in-intune-macos-cp.md)に関するページをご覧ください。  

1. macOS デバイスの電源を入れます。 
2. **[Language]\(言語\)** を選択して **[Continue]\(続行\)** をクリックします。  

   ![選択できる言語の一覧が表示されている macOS デバイスのセットアップ アシスタントのようこそ画面のスクリーンショット。](./media/macos-dep-welcome-1808.png)   
3. キーボード レイアウトを選択します。 選択した言語に基づいて 1 つ以上のオプションの一覧が表示されます。 選択した言語に関係なくすべてのレイアウト オプションを表示するには、**[Show All]\(すべて表示\)** をクリックします。 終了したら **[Continue]\(続行\)** をクリックします。  

   ![macOS デバイスのセットアップ アシスタントのキーボード レイアウト画面のスクリーンショット。選択できるキーボード言語の一覧、オフ状態の [Show All]\(すべて表示\) オプション、[Back]\(戻る\) ボタンと [Continue]\(続行\) ボタンが表示されている。](./media/macos-dep-keyboard-1808.png)  
4. お使いの Wi-Fi ネットワークを選択します。 セットアップを続けるには、インターネットに接続する必要があります。 お使いのネットワークが表示されない場合、または有線ネットワークで接続する必要がある場合は、**[Other Network Options]\(その他のネットワーク オプション\)** をクリックします。 終了したら **[Continue]\(続行\)** をクリックします。  

   ![macOS デバイスのセットアップ アシスタントの Wi-Fi ネットワーク選択画面のスクリーンショット。選択できるネットワークの一覧が表示されている。 [Other Network Options]\(その他のネットワーク オプション\) ボタン、[Back]\(戻る\) ボタン、[Continue]\(続行\) ボタンも表示されている。](./media/macos-dep-wifi-1808.png)  
5. Wi-Fi に接続すると、**[Remote Management]\(リモート管理\)** 画面が表示されます。 リモート管理を使用すると、組織の管理者は、会社で必要なアカウント、設定、アプリ、およびネットワークを指定してデバイスをリモート構成できます。 先に進む前に、ドキュメントを読んで、デバイスがどのように管理されるのかを理解してください。 次に、 **[続行]** をクリックします。  

   ![macOS デバイスのセットアップ アシスタントのリモート管理画面のスクリーンショット。リモート管理の説明文、詳細なドキュメントへのリンクが表示されている。 [Back]\(戻る\) ボタンと [Continue]\(続行\) ボタンも表示されている。](./media/macos-dep-remote-management-1-1808.png)  
6. メッセージが表示されたら、職場または学校アカウントでサインインします。 認証が済むと、デバイスに管理プロファイルがインストールされます。 プロファイルでは、組織のリソースへのアクセスが構成されて有効にされます。  
7. Apple のデータとプライバシーについての説明を読み、後でどのようなときに個人情報が収集されるのかを理解します。 次に、 **[続行]** をクリックします。  

   ![macOS デバイスのセットアップ アシスタントのデータとプライバシー画面のスクリーンショット。握手している 2 人の人のイラストと、Apple による個人情報の使用に関する説明が表示されている。 [Back]\(戻る\) ボタンと [Continue]\(続行\) ボタンも表示されている。](./media/macos-dep-apple-data-privacy-1808.png)  
8. デバイスが登録された後、場合によってはさらにいくつかの手順を行う必要があります。 表示される手順は、組織によるセットアップ エクスペリエンスのカスタマイズ方法によって異なります。 次のことが必要になる可能性があります。
    * Apple アカウントにサインインします
    * 使用条件に同意します
    * コンピューター アカウントを作成します
    * 高速セットアップを行います
    * お使いの Mac を設定します  
## <a name="get-the-company-portal-app"></a>Intune ポータル サイト アプリを取得する      
デバイスでアプリ ストアに移動して Intune ポータル サイト アプリを入手します。 このアプリでは、デバイスの監視、同期、追加、管理からのデバイスの削除、アプリのインストールを行うことができます。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
