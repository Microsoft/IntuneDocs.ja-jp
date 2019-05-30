---
title: Intune ポータル サイトで Android デバイスを登録する | Microsoft Docs
description: Intune ポータル サイトで Android デバイスを登録する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 736b1d891207a19f281aa1127975de1a55889e8b
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197028"
---
# <a name="enroll-your-device-with-company-portal"></a>Intune ポータル サイトでデバイスを登録する  
自分個人または会社所有の Android デバイスを登録して、会社のメール、アプリ、データにアクセスします。 Intune ポータル サイトでは、Android 4.4 以降が実行されている Samsung Knox などの Android デバイスがサポートされています。  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung KNOX は、ネイティブ Android に用意されている以外の追加保護のために特定の Samsung 製のデバイスで使用されるセキュリティの一種です。 Samsung KNOX デバイスかどうかを確認するには、 **[設定]**  >  **[About device]\(デバイス情報\)** を選択します。 そこに **[KNOX version]\(KNOX バージョン\)** と表示されない場合は、ネイティブ Android デバイスです。

## <a name="enroll-device"></a>デバイスを登録する  
必ず、[無料の Intune ポータル サイト アプリを Google Play からインストール](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)します。 

登録中に、デバイスの使用方法に適したカテゴリを選ぶように求められる場合があります。 会社のサポートは、その回答を使用して、ユーザーがアクセスできるアプリを確認します。  

1. ポータル サイト アプリを開きます。  

3. ポータル サイトの **[ようこそ]** 画面で、 **[サインイン]** をタップし、職場または学校アカウントを使用してサインインします。

   ![必要な職場または学校アカウントでサインインするようにユーザーに求める Android のようこそ画面のポータル サイト アプリ。 Microsoft アカウントなどの個人用アカウントは使用できないことも警告します。](./media/and-enroll-0-welcome-screen.png)   

4. 組織の使用条件への同意を求められたら、 **[同意する]** をタップします。 この画面は、次の例のスクリーンショットと若干異なる可能性があります。 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. 職場または学校の電子メール アドレスとパスワードを使用してポータル サイト アプリにサインインし、 **[サインイン]** をタップします。

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. **[会社アクセスのセットアップ]** 画面で、 **[続行]** をタップします。

   ![[会社アクセスのセットアップ] 画面](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > 黄色い三角形は、エラーが既に発生していることを意味するものではありません。 これらのアイコンは、登録プロセスに完了する必要のある手順があることを示します。

7. 会社のサポートがユーザーのデバイスに関して確認できる情報と確認できない情報について確認し、 **[続行]** をタップします。

   ![プライバシーの設定](/intune/media/android_cp_enroll_02_after_1710.png)

8. **[What's next?]\(次のステップ\)** 画面で、登録中に行う内容を確認し、 **[登録]** をタップします。

   ![[次に行うこと] 画面](/intune/media/android_cp_enroll_03_after_1710.png)

9. Android 6.0 以降を使用している場合は、この手順を実行します。 使用できない場合は、次の手順に進みます。

   会社のサポートが特定のポリシーを設定している場合は、次のメッセージが表示されることがあります。
   - **電話での通話とその管理をポータル サイトに許可しますか?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   このメッセージが表示された場合は、 **[許可]** をタップします。 **Microsoft が通話や電話の管理を行うことはない**ため、[許可] をタップしても問題はありません。 このメッセージ テキストは Google が制御しているため、Microsoft ではそれを変更することができません。 アクセスを許可すると、デバイスからデバイスの国際移動体加入者識別番号 (IMEI) が Intune に自動的に送信されます。 IMEI は、モバイル デバイスを一意に識別するシリアル番号のような番号です。

   アクセスを拒否した場合は、次に Intune ポータル サイトにサインインするときにメッセージが再び表示されます。 今後このメッセージが表示されないようにするには、 **[今後このメッセージを表示しない]** を選択します。 アクセス許可を逆にする場合は、 **[設定]**  >  **[アプリ]**  >  **[Intune ポータル サイト]**  >  **[アクセス許可]**  >  **[電話]** に移動して、アクセス許可を有効にします。  

   - **ポータル サイトに連絡先へのアクセスを許可しますか?**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     このメッセージが表示された場合は、 **[許可]** をタップします。 **Microsoft が連絡先にアクセスすることはない**ため、[許可] をタップしても問題はありません。 このメッセージ テキストは Google が制御しているため、Microsoft ではそれを変更することができません。 アクセスを許可すると、ポータル サイト アプリに仕事用アカウントの作成、使用、管理のみを許可します。

     アクセスを拒否すると、次に会社のポータルにサインインしたときにもう一度メッセージが表示されますが、 **[今後このメッセージを表示しない]** ボックスをタップすると、メッセージ表示をオフにできます。 後でアクセスを許可する場合、 **[設定]** &gt; **[アプリ]** &gt; **[ポータル サイト]** &gt; **[アクセス許可]** &gt; **[電話]** に移動して、アクセス許可を有効にします。

10. **[デバイス管理者のアクティブ化]** 画面で、 **[アクティブ化]** をタップします。

    ![[デバイス管理者のアクティブ化] 画面](./media/and-enroll-5-activate.png)

    デバイス管理者の役割は、ポータル サイトでデバイスを管理するために必要な役割です。 この役割を用意すると、管理者は特定の項目、たとえば、画面のロック解除が何回試行されたかなどを表示し、措置を講じることができます。    

    Microsoft はこのメッセージは制御しません。その言葉遣いが少々極端であることは理解しています。 特定の組織に関連する制約やアクセスのみをポータル サイトで表示する方法はありません。 すべて一度にこの画面で与えられます。 個別の組織の利用に関して質問があれば、[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)の連絡先情報を利用し、会社のサポートに詳細を問い合わせてください。  

11. 画面の指示に従って、PIN またはパスワードを入力します。 このデバイス上で PIN またはパスワードを既に設定している場合は、この画面は表示されず、新しい PIN またはパスワードを入力するように求められます。  

    ![PIN またはパスワードを入力する](./media/and-enroll-6-PIN-native.png)

12. Samsung Knox デバイスを使用している場合は、 **[Confirm]** (確認) をタップすると、デバイスが登録されていることを示すメッセージが表示されます。 ネイティブ Android デバイスを使用している場合は、デバイスが登録されていることを示す次の画面にだけ注意してください。

    ![Samsung KNOX プライバシー ポリシー](./media/and-enroll-7-knox-privacy-policy.png)

    この画面は、デバイスが登録されていることを示します。

    ![デバイス登録中画面](./media/and-enroll-8-device-enrolling.png)

13. **[会社アクセスのセットアップ]** 画面が表示されたら、 **[続行]** をタップします。 デバイスが対応していないことを示すメッセージが表示された場合は、問題を解決するための指示に従い、 **[続行]** をタップします。

    ![デバイスはポリシー準拠していないが、登録されている](/intune/media/android_cp_enroll_05_post_1709.png)

    ![解決が必要なデバイスのポリシー準拠の問題が発生している](/intune/media/android_cp_enroll_03_post_1709.png)

    問題の詳細を表示するには、これらをタップします。

    ![展開されたデバイスのポリシー準拠の問題](/intune/media/android_cp_enroll_04_post_1709.png)

    ![[会社アクセスのセットアップ] 画面](./media/and-enroll-9d-comp-access-setup.png)  

14. **[会社アクセスのセットアップが完了しました]** の画面で、 **[完了]** をタップします。 これでデバイスが登録されました。

    ![[会社アクセスのセットアップが完了しました] 画面](./media/and-enroll-10-comp-access-setup-complete.png)

## <a name="next-steps"></a>次の手順  

会社のアプリをインストールするには、最初に **[設定]**  >  **[セキュリティ]** の順に選択し、 **[不明なソース]** をオンにします。 アプリをインストールする前に、このオプションをオンにしない場合、次のメッセージが表示されます。インストールがブロックされました。 セキュリティ上の理由から、デバイスは不明のソースから取得したアプリのインストールをブロックするように設定されています。 エラー ダイアログ ボックスの **[設定]** をタップすると、 **[不明なソース]** オプションを表示できます。  

> [!Note]
> 組織で通信費管理ソフトウェアを使用している場合は、デバイスの登録を完了する前にいくつかの追加手順を実行します。 詳細については、[こちら](enroll-your-device-with-telecom-expense-management-android.md)を参照してください。

Intune にデバイスを登録している最中にエラーが表示された場合は、[会社のサポートにメールを送る](send-logs-to-your-it-admin-by-email-android.md)ことができます。  

サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。
