---
title: Microsoft Intune での iOS/iPadOS デバイスの登録に関する問題のトラブルシューティング
titleSuffix: Microsoft Intune
description: Intune で iOS/iPadOS デバイスを登録するときに発生する最も一般的な問題のトラブルシューティングに関する推奨事項。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514321"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune での iOS/iPadOS デバイスの登録に関する問題のトラブルシューティング

この記事は、Intune 管理者が iOS/iPadOS デバイスを Intune に登録するときに発生する問題を理解し、トラブルシューティングするのに役立ちます。

## <a name="prerequisites"></a>[前提条件]

トラブルシューティングを開始する前に、いくつかの基本的な情報を収集することが重要です。 この情報は、問題の理解を深め、解決策を見つけるための時間を短縮するのに役立ちます。

問題に関する次の情報を収集します。

- 正確なエラー メッセージは何ですか?
- エラー メッセージはどこに表示されますか?
- 問題が発生し始めたのはいつですか? 登録は成功しましたか?
- どのプラットフォーム (Android、iOS、iPadOS、Windows) に問題がありますか?
- 影響を受けているユーザーの数はどれくらいですか? すべてのユーザーに影響がありますか、それとも一部だけですか?
- 影響を受けているデバイスの数はどれくらいですか? すべてのデバイスですか、一部だけですか?
- MDM 機関は何ですか?
- 登録はどのように実行されますか?  "Bring Your Own Device" (BYOD) ですか、または登録プロファイルを使用する Apple Device Enrollment Program (DEP) ですか?

## <a name="error-messages"></a>エラー メッセージ

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>プロファイルのインストールに失敗しました。 ネットワーク エラーが発生しました。

**原因:** デバイスの iOS/iPadOS に、特定できない問題があります。

#### <a name="resolution"></a>解決策

1. 次の手順でデータが失われないように (iOS/iPadOS を復元すると、デバイス上のすべてのデータが削除されます)、必ずデータをバックアップしてください。
2. デバイスを回復モードにしてから復元を行います。 新しいデバイスとして設定していることを確認してください。 iOS/iPadOS デバイスを復元する方法について詳しくは、[https://support.apple.com/HT201263](https://support.apple.com/HT201263) を参照してください。
3. デバイスを再度登録します。

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>プロファイルのインストールに失敗しました。 サーバーへの接続を確立できませんでした。

**原因:** 企業所有のデバイスのみを許可するように、Intune テナントが構成されています。 

#### <a name="resolution"></a>解決策
1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択して、Intune を検索した後、**[Intune]** を選択します。
3. **[デバイスの登録]** > **[登録の制限]** を選択します。
4. **[デバイスの種類の制限]** で、>**プロパティ** >  設定する制限を選択し、 **[プラットフォームの選択]** > [ **iOS**で**許可**する] の順に選択し、[ **OK]** をクリックします。
5. **[プラットフォームの構成]** を選択し、個人所有の iOS/iPadOS デバイスに対して **[許可]** を選択して、**[OK]** をクリックします。
6. デバイスを再度登録します。

**原因:** DNS に必要な CNAME レコードが存在しません。

#### <a name="resolution"></a>解決策
会社のドメインの CNAME DNS リソース レコードを作成します。 たとえば、会社のドメインが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより、ユーザーによる登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 enrollment.manage.microsoft.com を入力するように求められます。

検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。 CNAME リソース レコードには次の情報を含める必要があります。

|種類:|ホスト名|指定先|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 時間|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

> [!NOTE]
> DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

**原因:** 以前に別のユーザー アカウントで登録されたデバイスを登録していますが、以前のユーザーが Intune から適切に削除されていません。

#### <a name="resolution"></a>解決策
1. 現在のプロファイルのインストールを取り消します。
2. Safari で [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) を開きます。
3. デバイスを再度登録します。

> [!NOTE]
> 登録がまだ失敗する場合は、Safari で Cookie を削除し (Cookie をブロックしないでください)、デバイスを再登録します。

**原因:** デバイスは、既に別の MDM プロバイダーに登録されています。

#### <a name="resolution"></a>解決策
1. iOS/iPadOS デバイスの **[Settings]\(設定\)** を開き、**[General]\(全般\) > [Device Management]\(デバイス管理\)** に移動します。
2. 既存の管理プロファイルを削除します。
3. デバイスを再度登録します。

**原因:** デバイスを登録しようとしているユーザーに、Microsoft Intune ライセンスがありません。

#### <a name="resolution"></a>解決策
1. [Office 365 管理センター](https://portal.office.com/adminportal/home#/homepage)にアクセスし、**[ユーザー] > [アクティブなユーザー]** を選択します。
2. Intune ユーザー ライセンスを割り当てるユーザー アカウントを選択し、**[製品ライセンス] > [編集]** の順に選択します。
3. このユーザーに割り当てるライセンスのトグルを **[オン]** 位置に切り替え、**[保存]** を選択します。
4. デバイスを再度登録します。

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>このサービスはサポート対象外です。 登録ポリシーがありません。

**原因**: Intune で Apple MDM プッシュ通知証明書が構成されていないか、証明書が無効です。 

#### <a name="resolution"></a>解決策

- MDM プッシュ通知証明書が構成されていない場合は、「[Apple MDM プッシュ証明書を取得する](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)」の手順に従います。
- MDM プッシュ通知証明書が無効な場合は、「[Apple MDM プッシュ証明書を更新する](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)」の手順に従います。

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>ポータル サイトは一時的に使用できません。 ポータル サイト アプリに問題が発生しました。 問題が解決しない場合は、システム管理者に問い合わせてください。

**原因:** ポータル サイト アプリが古くなっているか、破損しています。

#### <a name="resolution"></a>解決策
1. デバイスからポータル サイト アプリを削除します。
2. **App Store**から **Microsoft Intune ポータル サイト** アプリをダウンロードしてインストールします。
3. デバイスを再度登録します。
 > [!NOTE]
    > このエラーは、デバイス登録で許可するように構成されている数より多くのデバイスをユーザーが登録しようとした場合にも、発生する可能性があります。 以上の手順で問題が解決しない場合は、下記の「**デバイス キャップに達しました**」の解決手順に従ってください。

### <a name="device-cap-reached"></a>デバイス キャップに達しました

**原因:** ユーザーは、デバイス登録制限より多くのデバイスを登録しようとしています。

#### <a name="resolution"></a>解決策
1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、**[デバイス]** > **[すべてのデバイス]** を選択し、ユーザーが登録したデバイスの数を確認します。
    > [!NOTE]
    > また、影響を受けたユーザーを [Intune ユーザーポータル](https://portal.manage.microsoft.com/)にログオンさせ、登録したデバイスを確認させる必要もあります。 [Intune ユーザー ポータル](https://portal.manage.microsoft.com/)には表示され、[Intune 管理ポータル](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)には表示されないデバイスが存在する可能性があります。そのようなデバイスも、デバイス登録制限にカウントされます。
2. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、**[デバイス]** > **[登録制限]** を選択して、デバイスの登録制限を確認します。 既定では、制限は 15 に設定されています。 
3. 登録済みのデバイスの数が制限に達している場合は、不要なデバイスを削除するか、デバイスの登録制限を増やします。 すべての登録済みデバイスによって Intune ライセンスが消費されるため、必ず最初に不要なデバイスを削除することをお勧めします。
4. デバイスを再度登録します。

### <a name="workplace-join-failed"></a>Workplace Join が失敗する

**原因:** ポータル サイト アプリが古くなっているか、破損しています。  

#### <a name="resolution"></a>解決策
1. デバイスからポータル サイト アプリを削除します。
2. **App Store**から **Microsoft Intune ポータル サイト** アプリをダウンロードしてインストールします。
3. デバイスを再度登録します。

### <a name="user-license-type-invalid"></a>ユーザー ライセンスの種類が無効です

**原因:** デバイスを登録しようとしているユーザーに、有効な Intune ライセンスがありません。

#### <a name="resolution"></a>解決策
1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)にアクセスし、 **[ユーザー]** > **[アクティブなユーザー]** の順に選択します。
2. 影響を受けているユーザー アカウントを選択し、**[製品ライセンス]** > **[編集]** を選択します。
3. 有効な Intune ライセンスがこのユーザーに割り当てられていることを確認します。
4. デバイスを再度登録します。

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>ユーザー名を認識できません。 このユーザー アカウントは、Microsoft Intune の使用が許可されていません。 このメッセージが誤りであると思われる場合には、システム管理者に連絡してください。

**原因:** デバイスを登録しようとしているユーザーに、有効な Intune ライセンスがありません。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)にアクセスし、 **[ユーザー]** > **[アクティブなユーザー]** の順に選択します。
2. 影響を受けているユーザー アカウントを選択し、**[製品ライセンス]** > **[編集]** を選択します。
3. 有効な Intune ライセンスがこのユーザーに割り当てられていることを確認します。
4. デバイスを再度登録します。

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>プロファイルのインストールに失敗しました。 新しい MDM ペイロードが古いペイロードと一致しません。

**原因:** 管理プロファイルがデバイスに既にインストールされています。

#### <a name="resolution"></a>解決策

1. iOS/iPadOS デバイスの **[Settings]\(設定\)** を開き、**[General]\(全般\)** > **[Device Management]\(デバイス管理\)** を選択します。
2. 既存の管理プロファイルをタップし、**[Remove Management]\(管理の削除\)** をタップします。
3. デバイスを再度登録します。

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**原因:** Apple Push Notification Service (APNs) 証明書がないか、無効であるか、有効期限が切れています。

#### <a name="resolution"></a>解決策
有効な APNs 証明書が Intune に追加されていることを確認します。 詳しくは、「[iOS/iPadOS の登録を設定する](ios-enroll.md)」を参照してください。

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**原因:** Intune で構成されている Apple Push Notification Service (APNs) 証明書に問題があります。

#### <a name="resolution"></a>解決策
APNs 証明書を更新してから、デバイスを再登録します。

> [!IMPORTANT]
> APNs 証明書を更新したことを確認します。 APNs 証明書を置き換えないでください。 証明書を置き換えた場合は、すべての iOS/iPadOS デバイスを Intune に再登録する必要があります。 

- Intune スタンドアロンで APNs 証明書を更新するには、「[Apple MDM プッシュ証明書を更新する](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)」を参照してください。
- Office 365 で APNs 証明書を更新するには、[iOS/iPadOS デバイスでの APNs 証明書の作成](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)に関する記事を参照してください。

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 接続が無効です

登録プロファイルが割り当てられている DEP で管理されたデバイスの電源を入れると、登録が失敗し、次のエラー メッセージが表示されます。

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**原因:** デバイスと Apple DEP サービスの間の接続に問題があります。

#### <a name="resolution"></a>解決策
接続の問題を修正するか、別のネットワーク接続を使用してデバイスを登録します。 問題が解決しない場合は、Apple への問い合わせが必要になる場合もあります。


## <a name="other-issues"></a>その他の問題

### <a name="dep-enrollment-doesnt-start"></a>DEP の登録が開始しない
登録プロファイルが割り当てられている DEP で管理されたデバイスの電源を入れても、Intune の登録プロセスが開始されません。

**原因:** DEP トークンが Intune にアップロードされる前に、登録プロファイルが作成されています。

#### <a name="resolution"></a>解決策

1. 登録プロファイルを編集します。 プロファイルの変更はどのようなものでもかまいません。 目的は、プロファイルの変更時刻を更新することです。
2. DEP マネージド デバイスを同期する:[Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、**[デバイス]** > **[iOS]** > **[iOS の登録]** > **[Enrollment Program トークン]** の順に選択し、トークンを選択して **[今すぐ同期]** を選択します。 同期要求が Apple に送信されます。

### <a name="dep-enrollment-stuck-at-user-login"></a>ユーザー ログインで DEP の登録がスタックする
登録プロファイルが割り当てられている DEP で管理されたデバイスの電源を入れると、資格情報を入力した後で初期セットアップが停止します。

**原因:** 多要素認証 (MFA) が有効になっています。 現在、DEP デバイスでの登録時に MFA は機能しません。

#### <a name="resolution"></a>解決策
MFA を無効にしてから、デバイスを再登録します。


## <a name="next-steps"></a>次のステップ

- [Intune のデバイス登録に関するトラブルシューティング](../troubleshoot-device-enrollment-in-intune.md)
- [Intune フォーラムで質問する](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune サポート チームのブログを読む](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility and Security チームのブログを読む](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
