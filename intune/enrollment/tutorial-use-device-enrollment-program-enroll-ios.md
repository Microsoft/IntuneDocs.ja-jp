---
title: チュートリアル - Apple Business Manager または Device Enrollment Program を使用して、iOS/iPadOS デバイスを Intune に登録する
titleSuffix: Microsoft Intune
description: このチュートリアルでは、Apple の ABM の会社のデバイスを登録する機能を設定して、iOS/iPadOS デバイスを Intune に登録します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9aab0233c05416fc50413a7889435cb221179730
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415133"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-iosipados-devices-in-intune"></a>チュートリアル:Apple Business Manager (ABM) にある Apple の Corporate Device Enrollment 機能を使用して、iOS/iPadOS デバイスを Intune に登録する
Apple Business Manager の Device Enrollment 機能では、デバイスを簡単に登録できます。 Intune では Apple の以前の Device Enrollment Program (DEP) ポータルもサポートしていますが、Apple Business Manager でやり直すことをお勧めします。 デバイスは、Microsoft Intune と Apple Corporate Device Enrollment で、ユーザーが最初にデバイスをオンにしたときに、安全に自動的に登録されます。 そのため、各デバイスを個別に設定することなく、デバイスを多くのユーザーに配送できます。 

このチュートリアルでは、次の方法について説明します。
> [!div class="checklist"]
> * Apple Device Enrollment トークンを取得する
> * マネージド デバイスを Intune と同期する
> * 登録プロファイルを作成する
> * デバイスに登録プロファイルを割り当てる

Intune サブスクリプションがない場合は、[無料試用版アカウントにサインアップ](../fundamentals/free-trial-sign-up.md)します。

## <a name="prerequisites"></a>[前提条件]
- [Apple Business Manager](https://business.apple.com) または [Apple の Device Enrollment Program](http://deploy.apple.com) で購入したデバイス
- [[モバイル デバイス管理機関]](../fundamentals/mdm-authority-set.md) を設定する
- [[Apple MDM プッシュ通知証明書]](apple-mdm-push-certificate-get.md) を取得する

## <a name="get-an-apple-device-enrollment-token"></a>Apple Device Enrollment トークンを取得する
iOS/iPadOS デバイスを Apple の会社登録機能を使用して登録する前に、Apple Device Enrollment トークン (.pem) ファイルが必要です。 このトークンにより、ご自分の会社で所有している Apple デバイスの情報を Intune が同期できるようになります。 また、Intune は Apple に登録プロファイルをアップロードして、デバイスをそれらのプロファイルに割り当てられるようになります。

Device Enrollment トークンの作成には、ABM または DEP ポータルを使用します。 このポータルは、管理するデバイスを Intune に割り当てるためにも使用します。

1. [Microsoft Endpoint Manage 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[Enrollment Program トークン]**  >  **[追加]** を選択します。

2. **[同意する]** を選択して、Microsoft がユーザーとデバイスの情報を Apple に送信できるようにします。

   ![公開キーをダウンロードするための [Apple 証明書] ワークスペースの [Enrollment Program トークン] のスクリーンショット。](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. **[公開キーをダウンロードします]** を選択し、暗号化キー (.pem) ファイルをダウンロードしてローカルに保存します。 .pem ファイルは、ABM または DEP ポータルから信頼関係証明書を要求するために使用されます。

4. **[Create a token for Apple's Device Enrollment Program]\(Apple Device Enrollment Program 用のトークンを作成します\)** を選択して Apple の Deployment Program ポータルを開き、会社の Apple ID でサインインします。 この Apple ID を使って、DEP トークンを更新できます。

5. Apple の [Deployment Programs ポータル](https://deploy.apple.com) で、 **[Device Enrollment Program]** の **[開始]** を選択します。 ユーザーが実行する [Apple Business Manager](https://business.apple.com) での以下の手順は、若干異なる場合があります。

4. **[Manage Servers\(サーバーの管理\)]** ページで、 **[Add MDM Server\(MDM サーバーの追加\)]** を選びます。

5. **[MDM Server Name]\(MDM サーバー名\)** に、「*TestMDMServer*」と入力して **[次へ]** を選びます。 サーバー名は、自分がモバイル デバイス管理 (MDM) サーバーを識別できるようにするための名前です。 Microsoft Intune サーバーの名前または URL ではありません。

6. **[Add &lt;ServerName&gt;\(<サーバー名> の追加\)]** ダイアログ ボックスが開き、 **[Upload Your Public Key\(公開キーをアップロードする\)]** と表示されます。 **[ファイルの選択…]** を選択して .pem ファイルをアップロードし、 **[Next]** (次へ) を選択します。

6. **[Deployment Programs]**  >  **[Device Enrollment Program]**  >  **[デバイスの管理]** に移動します。
7. **[Choose Devices By]\(デバイスの選択基準\)** で、 **[シリアル番号]** を選びます。 <!--ask Tiffany about this-->

8. **[アクションの選択]** で **[Assign to Server]\(サーバーに割り当てる\)** を選択し、Microsoft Intune に指定した **ServerName** を選択して、&lt;[OK]&gt; を選択します。 指定したデバイスが管理用に Intune サーバーに割り当てられて、 **[Assignment Complete\(割り当て完了\)]** と表示されます。

   Apple ポータルで、 **[Deployment Programs]\(配備プログラム\)** &gt; **[Device Enrollment Program]\(Device Enrollment Program\)** &gt; **[View Assignment History]\(割り当て履歴の表示\)** の順に移動して、デバイスとその MDM サーバーの割り当てのリストを表示します。

9. 後で参照するために、Azure portal の Intune で、このトークンを作成するために使用した Apple ID を指定します。

    ![Enrollment Program トークンの作成に使った Apple ID の指定と、Enrollment Program トークンの参照のスクリーンショット。](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. **[Apple トークン]** ボックスで、証明書 (.pem) ファイルを参照し、 **[開く]** を選択して、 **[作成]** を選択します。 

11. スコープのタグを適用してこのトークンにアクセスできる管理者を制限するには、スコープを選択します。

## <a name="create-an-apple-enrollment-profile"></a>Apple 登録プロファイルの作成
これでトークンがインストールされたので、会社で所有している iOS/iPadOS デバイスの登録プロファイルを作成できます。 デバイス登録プロファイルで、デバイス グループに対して登録時に適用する設定を定義します。

1. [Microsoft Endpoint Manage 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[Enrollment Program トークン]** を選択します。

2. インストールしたトークンを選択し、 **[プロファイル]**  >  **[プロファイルの作成]** を選びます。

3. **[プロファイルの作成]** で、 **[名前]** に「*TestDEPProfile*」、 **[説明]** に「*iOS/iPadOS デバイス用の DEP のテスト*」と入力します。 ユーザーにはこれらの詳細は表示されません。

4. **[プラットフォーム]** の下から **[iOS]** を選択します。

5. デバイスの登録を、**ユーザー アフィニティ**を使用して、または使用しないで行うかを決めます。 ユーザー アフィニティは、特定のユーザー向けのデバイス用に設計されています。 ユーザーが、アプリのインストールなどのサービスにポータル サイトを使用する場合、 **[ユーザー アフィニティとともに登録する]** を選択します。 ユーザーがポータル サイトを必要としない場合、または多数のユーザーに対してデバイスをプロビジョニングする場合は、 **[ユーザー アフィニティを使用しないで登録する]** を選択します。

6. 登録をユーザー アフィニティを使用して行う場合、ポータル サイトまたは Apple 設定アップ アシスタントのどちらで認証を行うかを決めます。 Multi-Factor Authentication を使用する場合、最初のサインイン時にユーザーにパスワードを変更することを許可するか、登録時にユーザーに有効期限が切れたパスワードをリセットすることを求めます。これには、 **[Apple セットアップ アシスタントの代わりにポータル サイトで認証します]** で **[はい]** を選択します。 Apple が提供している Apple 設定アシスタントの基本の HTTP 認証で十分な場合は、 **[いいえ]** を選択します。 **[はい]** を選択し、ポータル サイト アプリケーションをエンド ユーザーのデバイス上で自動的に更新する場合は、Apple の Volume Purchasing Program (VPP) を使用して、そのユーザーに対してポータル サイトを必須アプリとして個別に展開します。

7. ユーザー アフィニティで登録を行い、ポータル サイトで認証を行う場合、Apple の Volume Purchase Program (VPP) でポータル サイトをインストールするかどうかを決定します。 VPP トークンを使用してポータル サイトをインストールする場合、ユーザーは登録時に、App Store からポータル サイトをダウンロードするときに、Apple ID とパスワードを入力する必要がありません。 **[VPP によるポータル サイトのインストール]** の下の **[使用するトークン]** を選択し、使用可能なポータル サイトの無料ライセンスがある VPP トークンを選択します。 ポータル サイトの展開に VPP を使用しない場合、 **[VPP によるポータル サイトのインストール]** の下の **[Don't use VPP]** \(VPP を使用しない\) を選択します。 

8. ユーザー アフィニティを使用して登録を行い、ポータル サイトで認証を行い、VPP を使用してポータル サイトをインストールすることを選択した場合、認証までポータル サイトを単一アプリケーション モードで実行するかかどうかを決定します。 この設定では、ユーザーが会社の登録を完了するまで、その他のアプリにアクセスできないことが保証されます。 登録が完了するまで、ユーザーにこのフローを限定したい場合、 **[Run Company Portal in Single App Mode until authentication]** \(認証までポータル サイトを単一アプリ モードで実行する\) の下で **[はい]** を選択します。 

9. **[デバイス管理の設定]** を選択し、 **[監視下]** で **[はい]** を選択します。 監視下のデバイスでは、会社の iOS/iPadOS デバイスに対して最も多くの管理オプションを使用できます。

10. **[ロックされた登録]** の下で **[はい]** を選択し、ユーザーがデバイスを会社の管理から削除できないようにします。 

11. **[コンピューターと同期する]** でオプションを選択し、iOS/iPadOS デバイスでコンピューターと同期できるかどうかを決定します。

12. Apple でデバイスは、既定で (iPad などの) デバイスの種類が使用され命名されます。 別の名前テンプレートを使用する場合は、 **[デバイス名のテンプレートを適用する]** で **[はい]** を選択します。 デバイスに付ける名前を入力します。ここで、 *{{シリアル}}* と *{{デバイスの種類}}* の文字列は、各デバイスのシリアル番号とデバイスの種類に置き換えます。 または、 **[デバイス名のテンプレートを適用する]** の下で **[いいえ]** を選択します。

13. **[OK]** を選びます。

14. **[セットアップ アシスタントのカスタマイズ]** を選んで、 **[部署名]** に「*チュートリアル部門*」と入力します。 この文字列は、デバイスのアクティブ化中にユーザーが **[About configuration]\(構成について\)** をタップすると表示される内容です。

15. **[部署の電話番号]** に電話番号を入力します。 この番号は、アクティブ化中にユーザーが **[ヘルプが必要ですか]** ボタンをタップすると表示されます。

16. デバイスのアクティブ化中にさまざまな画面を**表示**したり、**非表示**にしたりすることができます。 登録を最もスムーズに行うには、すべての画面を **[非表示]** に設定します。

17. **[OK]**  >  **[作成]** の順に選択します。

## <a name="sync-managed-devices-to-intune"></a>マネージド デバイスを Intune と同期する

ABM、ASM、または DEP ポータルを使用して登録プログラムのトークンを設定し、そこでデバイスを MDM サーバーに割り当てたら、それらのデバイスが Intune サービスで同期されるのを待機するか、手動で同期をプッシュします。手動で同期を行うと、デバイスが Azure portal に表示されるまで、最大 24 時間かかる場合があります。

1. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[Enrollment Program トークン]** の順に選択し、一覧からトークンを選択し、 **[デバイス]**  >  **[同期]** の順に選択します。

## <a name="assign-an-enrollment-profile-to-iosipados-devices"></a>登録プロファイルを iOS/iPadOS デバイスに割り当てる

登録する前に、Enrollment Program プロファイルをデバイスに割り当てる必要があります。 これらのデバイスは、Apple から Intune に同期されて、ABM、ASM、または DEP ポータルの適切な MDM サーバー トークンに割り当てられる必要があります。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[iOS]**  >  **[iOS の登録]**  >  **[Enrollment Program トークン]** を選択し、一覧から使用するトークンを選択します。
2. **[デバイス]** を選択し、リスト内でデバイスを選択し、 **[プロファイルの割り当て]** を選択します。
3. **[プロファイルの割り当て]** の下でデバイス用のプロファイルを選択し、 **[割り当て]** を選択します。

## <a name="distribute-devices-to-users"></a>デバイスのユーザーへの配布

Apple と Intune の間の同期と管理を設定し、DEP デバイスを登録できるようにプロファイルを割り当てました。 ユーザーにデバイスを配布できるようになりました。 ユーザー アフィニティがあるデバイスでは、各ユーザーに Intune ライセンスを割り当てる必要があります。

## <a name="next-steps"></a>次のステップ

iOS/iPadOS デバイスの登録に使用できる他のオプションについての詳細を確認できます。

> [!div class="nextstepaction"]
> [iOS/iPadOS DEP の登録に関する詳細な記事](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS/iPadOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
