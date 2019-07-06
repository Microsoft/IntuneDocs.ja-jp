---
title: 組織提供の macOS デバイスを管理対象に登録する | Microsoft Docs
description: 組織が購入して提供している macOS デバイスを Intune に登録する方法について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3941c41b24d458d14acb1361bc463af657a0ca67
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511933"
---
# <a name="enroll-your-organization-provided-macos-device-in-management"></a>組織から提供された macOS デバイスを管理登録する

新しい macOS デバイスを Intune で管理する方法について説明します。  

職場または学校から支給されるデバイスは多くの場合、受け取る前に事前構成されています。 初めてデバイスの電源を入れてサインインすると、事前構成済みの設定が組織からデバイスに送信されます。 デバイスのセットアップが完了すると、職場または学校のリソースにアクセスできるようになります。 

管理のセットアップを始めるには、デバイスの電源を入れて、職場または学校の資格情報でサインインします。 以下では、セットアップ アシスタントを使用する手順と表示される画面について説明します。   

## <a name="what-is-apple-dep"></a>Apple DEP とは
組織は、*Apple Device Enrollment Program* (DEP) を利用してデバイスを購入することがあります。 Apple DEP を利用することで、組織は iOS または macOS デバイスを大量に購入できます。 その後、組織は Intune などの適切なモバイル デバイス管理プロバイダーでデバイスを構成して管理できます。 Apple DEP についての情報がさらに必要な管理者は、「[Apple の Device Enrollment Program を使用して macOS デバイスを自動登録する](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos)」をご覧ください。  

## <a name="get-your-device-managed"></a>デバイスを管理対象にする 
macOS デバイスを管理対象に登録するには、次の手順のようにします。 会社支給のデバイスではなく個人所有のデバイスを使用している場合は、[個人デバイスと Bring Your Own デバイス](enroll-your-device-in-intune-macos-cp.md)に関するページをご覧ください。  

1. macOS デバイスの電源を入れます。 
2. ご自分の国を選択して **[Continue]\(続行\)** をクリックします。  

   ![選択できる言語の一覧が表示されている macOS デバイスのセットアップ アシスタントのようこそ画面のスクリーンショット。](./media/macos-dep-welcome-1808.png)   
3. キーボード レイアウトを選択します。 選択した国に基づいて 1 つ以上のオプションの一覧が表示されます。 選択した国に関係なくすべてのレイアウト オプションを表示するには、 **[Show All]\(すべて表示\)** をクリックします。 終了したら **[Continue]\(続行\)** をクリックします。  

   ![macOS デバイスのセットアップ アシスタントのキーボード レイアウト画面のスクリーンショット。選択できるキーボード言語の一覧、オフ状態の [Show All]\(すべて表示\) オプション、[Back]\(戻る\) ボタンと [Continue]\(続行\) ボタンが表示されている。](./media/macos-dep-keyboard-1808.png)  
4. お使いの Wi-Fi ネットワークを選択します。 セットアップを続けるには、インターネットに接続する必要があります。 お使いのネットワークが表示されない場合、または有線ネットワークで接続する必要がある場合は、 **[Other Network Options]\(その他のネットワーク オプション\)** をクリックします。 終了したら **[Continue]\(続行\)** をクリックします。  

   ![macOS デバイスのセットアップ アシスタントの Wi-Fi ネットワーク選択画面のスクリーンショット。選択できるネットワークの一覧が表示されている。 [Other Network Options]\(その他のネットワーク オプション\) ボタン、[Back]\(戻る\) ボタン、[Continue]\(続行\) ボタンも表示されている。](./media/macos-dep-wifi-1808.png)  
5. Wi-Fi に接続すると、 **[Remote Management]\(リモート管理\)** 画面が表示されます。 リモート管理を使用すると、組織の管理者は、会社で必要なアカウント、設定、アプリ、およびネットワークを指定してデバイスをリモート構成できます。 リモート管理の説明に目を通し、デバイスがどのように管理されているか理解します。 次に、 **[続行]** をクリックします。  

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
デバイスに macOS 用の Intune ポータル サイト アプリをダウンロードします。 このアプリでは、デバイスの監視、同期、追加、管理からのデバイスの削除、アプリのインストールを行うことができます。 これらの手順では、ポータル サイトにデバイスを登録する方法についても説明しています。  
1. ご使用の macOS デバイスで https://portal.manage.microsoft.com/EnrollmentRedirect.aspx に進みます。
2. 職場や学校のアカウントでポータル サイト Web サイトにサインインします。 
3. **[Get the App]\(アプリの取得\)** をクリックして、macOS 用のポータル サイト インストーラーをダウンロードします。
4. 求められたら .pkg ファイルを開き、インストール手順を完了します。
4. Intune ポータル サイト アプリを開き、職場または学校アカウントでサインインします。
5. デバイスを探し、 **[登録]** をクリックします。
6. **[続行]**  >  **[完了]** の順にクリックします。 これでご使用のデバイスは、会社の対応デバイスとしてポータル サイト アプリに表示されるはずです。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
