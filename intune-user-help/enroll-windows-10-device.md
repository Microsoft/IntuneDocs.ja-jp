---
title: Intune ポータル サイトで Windows 10 デバイスを登録する | Microsoft Docs
description: Intune ポータル サイトで Windows 10 デバイスを登録する手順
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77b7f3adf4fa8675e3734f7eab8fbaa9391d952a
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67527960"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Intune ポータル サイトで Windows 10 デバイスを登録する

Intune ポータル サイトを使用して、自分の Windows 10 デバイスを組織で管理されるように登録します。 この記事では、Windows 10 バージョン 1607 以降および Windows 10 バージョン 1511 以前のデバイスを登録する方法について説明します。 始める前に、[自分のデバイスのバージョンを確認](windows-enrollment-company-portal.md#find-windows-10-version-number)し、正しい手順を利用できるようにしてください。  

Windows 10 は、デスクトップ、スマートフォン、タブレットなど、さまざまなデバイスの種類でサポートされています。 登録の手順は、使用しているデバイスにかかわらず同じです。 ただし、画面は、この記事で示す画像と少し異なる可能性があります。  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Windows 10 バージョン 1607 以降のデバイスを登録する 
以下の手順では、Windows 10 バージョン 1607 以降が実行されているデバイスを登録する方法について説明します。  

1. **[スタート]** メニューに移動します。 Windows 10 Mobile デバイスの場合は、 **[すべてのアプリ]** の一覧に進みます。

2. **[設定]** アプリを開きます。 アプリの一覧でアプリをすぐに使用できない場合は、検索バーに移動して「設定」と入力します。

3. **[アカウント]**  >  **[職場または学校にアクセスする]**  >  **[接続]** の順に選択します。  


    ![[職場または学校にアクセスする] アカウントの選択](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. 職場または学校の電子メール アドレスを入力し、 **[次へ]** を選択します。  


   ![職場または学校のアカウントを入力します。](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. 職場または学校のアカウントで Intune にサインインします。  


    ![職場または学校のアカウントを追加する](./media/w10-enroll-rs1-enter-your-credentials.png)  

    最終的に、会社または学校がデバイスを登録しているというメッセージが表示されます。

6. Windows Hello 用に PIN を設定する必要がある組織の場合は、確認コードの入力を求められます。 コードを入力し、画面の手順に従って PIN を作成します。  

7. **[準備が完了しました]** 画面で、 **[完了]** を選択します。 これでデバイスが登録されました。  

8. 接続を再確認するには、 **[設定]**  >  **[アカウント]**  >  **[職場または学校にアクセスする]** に戻ります。  自分のアカウントが表示されるようになっているはずです。  


    ![接続が正しくセットアップされたことを確認する](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

それでも職場または学校の電子メール、ファイルなどのデータにアクセスできない場合は、 [アカウントに関する問題のトラブルシューティングを行う](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)方法を参照してください。  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Windows 10 バージョン 1511 以前のデバイスを登録する  
以下の手順では、Windows 10 バージョン 1511 以前が実行されているデバイスを登録する方法について説明します。  

1. **[スタート]** メニューに移動します。 Windows 10 Mobile デバイスの場合は、 **[すべてのアプリ]** の一覧に進みます。

2. **[設定]** アプリを開きます。 アプリの一覧でアプリをすぐに使用できない場合は、検索バーに移動して「設定」と入力します。

3. **[アカウント]** を選択して、 >  **[Your accounts]\(自分のアカウント\)** を選択します。  


    ![[お使いのアカウント] を選択する](./media/W10-enroll-2-accounts-your-account.png)  

5. **[職場または学校アカウントを追加]** を選択します。  


    ![[職場または学校アカウントを追加] を選択する](./media/w10-enroll-3-add-work-school-acct.png)  

6. 職場または学校の資格情報でサインインします。  


    ![サインイン](./media/W10-enroll-4-sign-in.png)  

それでも職場または学校の電子メール、ファイルなどのデータにアクセスできない場合は、 登録中に[アカウント関連の問題のトラブルシューティングを行う](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account)方法を参照してください。  

## <a name="it-administrator-support"></a>IT 管理者のサポート   

デバイス登録中に問題に遭遇した IT 管理者は、「[Microsoft Intune の Windows デバイスの登録に関する問題のトラブルシューティング](https://support.microsoft.com/help/4469913)」を参照してください。 この記事では、一般的なエラー、その原因、解決する手順の一覧が示されています。 

## <a name="next-steps"></a>次の手順  
Intune ポータル サイトまたは登録に関するヘルプが必要な場合は、組織の IT サポート チームにお問い合わせください。 連絡先の情報は、[Intune ポータル サイトの Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)でわかります。 職場または学校のアカウントでサイトにサインインします。  

 

