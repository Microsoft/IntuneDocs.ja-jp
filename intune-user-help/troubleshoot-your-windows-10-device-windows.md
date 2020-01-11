---
title: Windows 10 デバイスの登録に関するトラブルシューティング | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 75c28fb662daaf96aba6324b468b50e7c9081fd2
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857893"
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Windows 10 デバイスの登録に関するトラブルシューティング
ご利用のデバイスを登録しても、職場または学校のメール アドレスやファイルにまだアクセスできない場合は、次のトラブルシューティング手順をお試しください。  

1. 次の 2 つの画面を見て、お使いのデバイスの表示画面に似ている方をご確認ください。 お使いのデバイスの表示画面に対応する手順に従います。

    次の画面が表示されている場合は、「[[Access work or school (職場または学校へのアクセス)] が表示されている場合のトラブルシューティング手順](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)」の手順に従います。

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    次の画面が表示されている場合は、「[[お使いのアカウント] が表示されている場合のトラブルシューティング手順](#troubleshooting-steps-to-follow-if-you-see-your-account)」の手順に従います。

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>[職場または学校にアクセスする] が表示される場合のトラブルシューティング手順

1. 上記の手順を実行しても職場または学校の電子メールやファイルにアクセスできない場合は、 **[Access work or school (職場または学校へのアクセス)]** に戻ります。

2. 以下のいずれかを実行します。

   - 次の画像のような接続が表示される場合は、その接続をタップして、[管理]、[情報]、[切断] の各オプションが表示されることを確認します。 これらのオプションが表示される場合は、登録および接続は完了しています。

     ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

   - 上に示した接続情報が表示されない場合、または接続情報は表示されるが一部のオプションが表示されない場合は、 **[接続]** をタップします。 職場または学校の資格情報でサインインして、接続します。  

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>[お使いのアカウント] が表示される場合のトラブルシューティング手順

上記の手順を実行しても、職場または学校の電子メールやファイルなどのデータにアクセスできない場合は、 **[アカウント]** に戻り、 **[職場のアクセス]** をタップします。

- ご利用の職場または学校のアカウントが一覧に表示された場合は、接続されています。  

- 職場または学校のアカウントが表示されない場合は、 **[接続]** をタップしてから、職場または学校の資格情報でサインインします。

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>[職場または学校アカウントの設定] が表示される場合のトラブルシューティング手順

"<strong>入力されたユーザー名と一致する管理エンドポイントを自動検出できませんでした。ユーザー名を確認して、やり直してください。管理エンドポイントの URL がわかっている場合は、それを入力してください。</strong>" というメッセージが表示される場合は、ユーザー名とパスワードを再入力する必要があります。 それでもうまくいかない場合は、<strong>[管理エンドポイント]</strong> ボックスに入力する必要のある Web サイトの会社のサポートに確認する必要があります。 これは、<strong>www.yourcompany.onmicrosoft.com</strong> のような Web サイトです。

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
