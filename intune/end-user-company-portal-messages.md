---
title: "Android でユーザーに表示される可能性のあるポータル サイト メッセージ"
description: "Intune エンド ユーザーに表示される可能性のあるポータル サイト アプリのメッセージについて説明します。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
ms.openlocfilehash: f1a5c8a15007a38942fe543e6c1062bf957a481c
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="help-end-users-understand-company-portal-app-messages"></a>ポータル サイト アプリで表示されるメッセージに関してエンド ユーザーをサポートする

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

> [!NOTE]
> 次の情報は、Android 6.0 以上のデバイスにのみ適用されます。

登録プロセスで表示される 2 つのメッセージが、エンド ユーザーにとって混乱の原因となる場合があります。

- __電話での通話とその管理をポータル サイトに許可しますか?__
- __デバイス上の写真、メディア、およびファイルへのアクセスをポータル サイトに許可しますか?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>電話での通話とその管理をポータル サイトに許可しますか?

### <a name="where-it-appears"></a>表示内容
ユーザーがデバイスを登録するときにポータル サイト アプリで **[登録]** をタップすると、**[電話での通話とその管理をポータル サイトに許可しますか?]** のメッセージが表示されます。

### <a name="what-it-means"></a>意味
ユーザーがこの同意すると、デバイスの電話番号と IMEI 番号が Intune サービスに送信されるようになります。 これらは管理コンソールの __[ハードウェア]__ ページに表示されます。

> [!NOTE]
> **ポータル サイト アプリは電話での通話やその管理を行いません。** このメッセージ テキストは Google によって制御されているので、変更することはできません。

**[ハードウェア]** ページを参照するには、**[グループ]** > **[すべてのモバイル デバイス]** > **[デバイス]** に移動します。 ユーザーのデバイスを選択し、**[プロパティの表示]** > **[ハードウェア]** に移動します。

### <a name="what-happens-if-users-deny-access"></a>ユーザーがアクセスを拒否した場合の動作
ユーザーはアクセスを拒否した場合でも、引き続きポータル サイト アプリを使用してデバイスを登録できます。 ただし、管理コンソールの __[ハードウェア]__ ページでデバイスの電話番号と IMEI 番号が空白になります。 アクセスを拒否したあとで、ユーザーがポータル サイト アプリに 2 回目にサインインしたときに、メッセージに **[今後このメッセージを表示しない]** チェック ボックスが表示されます。これを選択すると、プロンプトが表示されなくなります。

ユーザーがアクセスを許可し、その後アクセスを拒否した場合は、登録後、次回ユーザーがポータル サイト アプリにサインインしたときに、メッセージが表示されます。

後でアクセスを許可する場合は、**[設定]** > **[アプリ]** > **[ポータル サイト]** > **[アクセス許可]** > **[電話]** の順に移動して、アクセス許可を有効にします。

### <a name="how-to-explain-this-to-your-users"></a>ユーザーへの説明方法
ユーザーは、「[Intune に Android デバイスを登録する](/intune-user-help/enroll-your-device-in-intune-android)」で詳細を参照できます。

## <a name="allow-company-portal-to-access-your-contacts"></a>ポータル サイトに連絡先へのアクセスを許可しますか?

### <a name="where-it-appears"></a>表示内容
ユーザーがデバイスを登録するときに、ポータル サイト アプリで **[登録]** をタップすると、**[連絡先へのアクセスをポータル サイトに許可しますか?]** のメッセージが表示されます。

### <a name="what-it-means"></a>意味
ユーザーが同意すると、Intune が職場アカウントを作成し、そのデバイスでユーザーに登録されている Azure Active Directory ID を管理できるようになります。

> [!NOTE]
> **Microsoft が連絡先にアクセスすることはありません。** このメッセージ テキストは Google によって制御されているので、変更することはできません。

### <a name="what-happens-if-users-deny-access"></a>ユーザーがアクセスを拒否した場合の動作
ユーザーがアクセスを拒否すると、デバイスは Intune に登録されず、管理できません。 アクセスを拒否したあとで、ユーザーがポータル サイト アプリに 2 回目にサインインしたときに、メッセージに **[今後このメッセージを表示しない]** チェック ボックスが表示されます。これを選択すると、プロンプトが表示されなくなります。

ユーザーがアクセスを許可し、その後アクセスを拒否した場合は、登録後、次回ユーザーがポータル サイト アプリにサインインしたときに、メッセージが表示されます。

後でアクセスを許可する場合は、**[設定]** > **[アプリ]** > **[ポータル サイト]** > **[アクセス許可]** > **[電話]** の順に移動して、アクセス許可を有効にします。

### <a name="how-to-explain-this-to-your-users"></a>ユーザーへの説明方法
ユーザーは、「[Intune に Android デバイスを登録する](/intune-user-help/enroll-your-device-in-intune-android)」で詳細を参照できます。

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>デバイス上の写真、メディア、およびファイルへのアクセスをポータル サイトに許可しますか?

### <a name="where-it-appears"></a>表示内容
ユーザーがログを IT 管理者に送信するときに、**[データを送信]** をタップすると、**[デバイス上の写真、メディア、およびファイルへのアクセスをポータル サイトに許可しますか?]** のメッセージが表示されます。

### <a name="what-it-means"></a>意味
これに同意すると、ユーザーのデバイスでデータ ログがデバイスの SD カードに書き込まれ、それらのログを USB ケーブルを使用して移動することが許可されます。   

> [!NOTE]
> **ポータル サイト アプリはユーザーの写真、メディア、およびファイルにアクセスしません。** このメッセージ テキストは Google によって制御されているので、変更することはできません。

### <a name="what-happens-if-users-deny-access"></a>ユーザーがアクセスを拒否した場合の動作
ユーザーがアクセスを拒否した場合、ユーザーは引き続きデータ ログを電子メールで送信できますが、ログはデバイスの SD カードにコピーされません。

アクセスを拒否すると、ユーザーがポータル サイト アプリに 2 回目にサインインしたときに、メッセージに **[今後このメッセージを表示しない]** チェック ボックスが表示されます。ユーザーはこれを選ぶことによって、メッセージが再び表示されないようにできます。 ユーザーがアクセスを許可し、その後アクセスを拒否した場合は、次回ユーザーがログを送信しようとすると、メッセージが表示されます。 後でアクセスを許可する場合は、**[設定]** >  **[アプリ]** >  **[ポータル サイト]** > **[アクセス許可]** > **[ストレージ]** に移動して、アクセス許可を有効にします。


### <a name="how-to-explain-this-to-your-users"></a>ユーザーへの説明方法
ユーザーは、[IT 管理者への電子メールによるログの送信](/intune-user-help/send-logs-to-your-it-admin-by-email-android)に関する記事を参照できます。 また、[IT 管理者へのケーブルを使用したログの送信](/intune-user-help/send-logs-to-your-it-admin-by-cable-android)に関する記事を参照すると、2 つの方法を比較できます。

## <a name="your-company-support-needs-to-give-you-access-to-company-resources"></a>会社のサポートが会社のリソースへのアクセス権を与える必要がある

### <a name="where-it-appears"></a>表示内容
ポータル サイト アプリを **[許可されたアプリ]** または **[適用から除外されるアプリ]** の一覧に追加していない場合にユーザーがサインインしようとすると、サインインが失敗します。 次のメッセージが表示されます:

> **Your company support needs to give you access to company resources\(会社のサポートから会社のリソースへのアクセス権を付与してもらう必要があります\)**  
> あなたの会社は Windows 情報保護ポリシーを使用してデバイスを保護しています。 ポータル サイトからこのポリシーにアクセスできることを、会社のサポートが確認する必要があります。

### <a name="what-it-means"></a>意味

ポータル サイトを Windows 情報保護 (WIP) のアプリ保護ポリシーの **[許可されたアプリ]** または**[適用から除外されるアプリ]** 一覧に追加します。 詳細については、「[Intune で Windows 情報保護 (WIP) アプリ保護ポリシーを作成して展開する](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune)」を参照してください。

### <a name="see-also"></a>関連項目
[Intune の使用に関するエンドユーザーへの通知内容](end-user-educate.md)
