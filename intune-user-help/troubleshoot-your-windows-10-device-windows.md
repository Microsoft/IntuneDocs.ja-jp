---
title: "Windows 10 デバイスの登録に関するトラブルシューティング | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 7160f58f60624815137e2990bd06188edd4ede81
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Windows 10 デバイスの登録に関するトラブルシューティング
「[Intune に Windows 10 Mobile または Windows 10 デスクトップ デバイスを登録する](enroll-your-w10-phone-or-w10-pc-windows.md)」の手順を完了しても職場または学校の電子メールやファイルにアクセスできない場合は、次のトラブルシューティング手順を試してください。

1.  次の 2 つの画面を見て、お使いのデバイスの表示画面に似ている方をご確認ください。 お使いのデバイスの表示画面に対応する手順に従います。

    次の画面が表示されている場合は、「[[Access work or school (職場または学校へのアクセス)] が表示されている場合のトラブルシューティング手順](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)」の手順に従います。

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    次の画面が表示されている場合は、「[[お使いのアカウント] が表示されている場合のトラブルシューティング手順](#troubleshooting-steps-to-follow-if-you-see-your-account)」の手順に従います。

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>[職場または学校にアクセスする] が表示される場合のトラブルシューティング手順

1.  上記の手順を実行しても職場または学校の電子メールやファイルにアクセスできない場合は、**[Access work or school (職場または学校へのアクセス)]** に戻ります。

2. 以下のいずれかを実行します。

    - 次の画像のような接続が表示される場合は、その接続をタップして、[管理]、[情報]、[切断] の各オプションが表示されることを確認します。 これらのオプションが表示される場合は、登録および接続は完了しています。

    ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

    - 上に示した接続情報が表示されない場合、または接続情報は表示されるが一部のオプションが表示されない場合は、**[接続]** をタップし、職場または学校の資格情報でサインインします。 これで接続が完了します。

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>[お使いのアカウント] が表示される場合のトラブルシューティング手順

上記の手順を実行しても、職場または学校の電子メールやファイルなどのデータにアクセスできない場合は、**[アカウント]** に戻り、**[職場のアクセス]** をタップします。

- 職場または学校のアカウントが表示された場合は、正常に 接続されています。

- 職場または学校のアカウントが表示されない場合は、**[接続]** をタップしてから、職場または学校の資格情報でサインインします。

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>[職場または学校アカウントの設定] が表示される場合のトラブルシューティング手順

"__入力されたユーザー名と一致する管理エンドポイントを自動検出できませんでした。ユーザー名を確認して、やり直してください。管理エンドポイントの URL がわかっている場合は、それを入力してください。__" というメッセージが表示される場合は、ユーザー名とパスワードを再入力する必要があります。 それでもうまくいかない場合は、**[管理エンドポイント]** ボックスに入力する必要のある Web サイトの会社のサポートに確認する必要があります。 これは、**www.yourcompany.onmicrosoft.com** のような Web サイトです。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://portal.manage.microsoft.com#HelpDeskDialog)をご確認ください。
