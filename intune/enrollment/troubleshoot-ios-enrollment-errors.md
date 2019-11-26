---
title: Microsoft Intune での iOS デバイスの登録に関する問題のトラブルシューティング
titleSuffix: Microsoft Intune
description: Intune に iOS デバイスを登録するときに発生する最も一般的な問題のトラブルシューティングに関する推奨事項。
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
ms.openlocfilehash: e71ae2d2bcee22040c256ea711edd22b1d1fc80a
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199266"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Microsoft Intune での iOS デバイスの登録に関する問題のトラブルシューティング

この記事は、intune 管理者が Intune に iOS デバイスを登録するときに発生する問題を理解し、トラブルシューティングするのに役立ちます。

## <a name="prerequisites"></a>必要条件

トラブルシューティングを開始する前に、いくつかの基本的な情報を収集することが重要です。 この情報は、問題の理解を深め、解決策を見つけるための時間を短縮するのに役立ちます。

問題に関する次の情報を収集します。

- 正確なエラー メッセージは何ですか?
- エラー メッセージはどこに表示されますか?
- 問題が発生し始めたのはいつですか? 登録は成功しましたか?
- どのプラットフォーム (Android、iOS、Windows) に問題がありますか。
- 影響を受けるユーザーの数を確認できます。 すべてのユーザーに影響があるのか、それともほんの一部であるか。
- 影響を受けるデバイスの数を確認できます。 すべてのデバイスが影響を受けていますか。
- MDM 機関とは System Center Configuration Manager ている場合は、どのバージョンの Configuration Manager を使用していますか。
- 登録はどのように実行されますか? 登録プロファイルを使用して "自分のデバイスを持ち込む" (BYOD) または Apple Device Enrollment Program (DEP) ですか。

## <a name="error-messages"></a>エラー メッセージ

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>プロファイルのインストールに失敗しました。 ネットワーク エラーが発生しました。

**原因:** デバイスの iOS には、特定できない問題があります。

#### <a name="resolution"></a>解決策

1. 次の手順でデータが失われないようにするには (iOS の復元によってデバイス上のすべてのデータが削除される)、必ずデータをバックアップしてください。
2. デバイスを回復モードにしてから復元します。 新しいデバイスとして設定していることを確認してください。 IOS デバイスを復元する方法の詳細については、「 [https://support.apple.com/HT201263](https://support.apple.com/HT201263)」を参照してください。
3. デバイスを再度登録します。

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>プロファイルのインストールに失敗しました。 サーバーへの接続を確立できませんでした。

**原因:** Intune テナントは、企業所有のデバイスのみを許可するように構成されています。 

#### <a name="resolution"></a>解決策
1. Azure ポータルにサインインします。
2. **[その他のサービス]** を選択して、Intune を検索した後、 **[Intune]** を選択します。
3. **[デバイスの登録]**  >  **[登録の制限]** を選択します。
4. **[デバイスの種類の制限]** で、>**プロパティ** >  設定する制限を選択し、 **[プラットフォームの選択]** > [ **iOS**で**許可**する] の順に選択し、[ **OK]** をクリックします。
5. **[プラットフォームの構成]** を選択し、個人所有の iOS デバイスに対して **[許可]** を選択して、[ **OK]** をクリックします。
6. デバイスを再度登録します。

**原因:** DNS に必要な CNAME レコードが存在しません。

#### <a name="resolution"></a>解決策
会社のドメインの CNAME DNS リソース レコードを作成します。 たとえば、会社のドメインが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。

CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 enrollment.manage.microsoft.com を入力するように求められます。

検証済みドメインが複数ある場合、ドメインごとに CNAME レコードを作成します。 CNAME リソース レコードには次の情報を含める必要があります。

|種類:|ホスト名|指定先|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 時間|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

> [!NOTE]
> DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

**原因:** 以前に別のユーザーアカウントで登録されていたデバイスを登録すると、以前のユーザーは適切に Intune から削除されませんでした。

#### <a name="resolution"></a>解決策
1. 現在のプロファイルのインストールを取り消します。
2. Safari で[https://portal.manage.microsoft.com](https://portal.manage.microsoft.com)を開きます。
3. デバイスを再度登録します。

> [!NOTE]
> 登録がまだ失敗する場合は、Safari の cookie を削除し (cookie をブロックしません)、デバイスを再登録します。

**原因:** デバイスは、既に別の MDM プロバイダーに登録されています。

#### <a name="resolution"></a>解決策
1. IOS デバイスの **[設定]** を開き、 **[全般 > デバイス管理**] にアクセスします。
2. 既存の管理プロファイルを削除します。
3. デバイスを再度登録します。

**原因:** デバイスを登録しようとしているユーザーには Microsoft Intune ライセンスがありません。

#### <a name="resolution"></a>解決策
1. [Office 365 管理センター](https://portal.office.com/adminportal/home#/homepage)にアクセスし、 **[ユーザー > アクティブユーザー]** を選択します。
2. Intune ユーザー ライセンスを割り当てるユーザー アカウントを選択し、 **[製品ライセンス] > [編集]** の順に選択します。
3. このユーザーに割り当てるライセンスの **[オン**] の位置に切り替え、 **[保存]** を選択します。
4. デバイスを再度登録します。

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>このサービスはサポート対象外です。 登録ポリシーがありません。

**原因**: Intune で Apple MDM プッシュ通知証明書が構成されていないか、証明書が無効です。 

#### <a name="resolution"></a>解決策

- MDM プッシュ通知証明書が構成されていない場合は、「 [APPLE MDM プッシュ通知証明書を取得する](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)」の手順に従います。
- MDM プッシュ通知証明書が無効な場合は、「 [APPLE MDM プッシュ通知証明書の更新](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)」の手順に従ってください。

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>ポータル サイトは一時的に使用できません。 ポータルサイトアプリで問題が発生しました。 問題が解決しない場合は、システム管理者に問い合わせてください。

**原因:** ポータルサイトアプリが古くなっているか、破損しています。

#### <a name="resolution"></a>解決策
1. デバイスからポータル サイト アプリを削除します。
2. **App Store**から **Microsoft Intune ポータル サイト** アプリをダウンロードしてインストールします。
3. デバイスを再度登録します。
 > [!NOTE]
    > このエラーは、デバイスの登録が許可するように構成されているよりも多くのデバイスをユーザーが登録しようとした場合にも発生する可能性があります。 これらの手順で問題が解決しない場合は、下記の**デバイス上限に達し**た場合の解決手順に従ってください。

### <a name="device-cap-reached"></a>デバイス キャップに達しました

**原因:** ユーザーは、デバイス登録制限よりも多くのデバイスを登録しようとしています。

#### <a name="resolution"></a>解決策
1. [Intune 管理ポータル](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) >  台の**デバイス** > **すべてのデバイス** を開き、ユーザーが登録したデバイスの数を確認します。
    > [!NOTE]
    > また、影響を受けるユーザーが[Intune ユーザーポータル](https://portal.manage.microsoft.com/)にログオンし、登録されているデバイスを確認する必要があります。 Intune[ユーザーポータル](https://portal.manage.microsoft.com/)に表示されるデバイスもありますが、 [intune 管理ポータル](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)には表示されません。このようなデバイスは、デバイスの登録制限にもカウントされます。
2. [**管理** > **モバイルデバイス管理** > の**登録ルール**] に移動して、デバイスの登録制限を確認 > ます。 既定では、制限は 15 に設定されています。 
3. 登録されているデバイスの数が制限に達した場合は、不要なデバイスを削除するか、デバイスの登録制限を増やします。 登録されているすべてのデバイスで Intune ライセンスが使用されるため、まず不要なデバイスを必ず削除することをお勧めします。
4. デバイスを再度登録します。

### <a name="workplace-join-failed"></a>Workplace Join 失敗

**原因:** ポータルサイトアプリが古くなっているか、破損しています。  

#### <a name="resolution"></a>解決策
1. デバイスからポータル サイト アプリを削除します。
2. **App Store**から **Microsoft Intune ポータル サイト** アプリをダウンロードしてインストールします。
3. デバイスを再度登録します。

### <a name="user-license-type-invalid"></a>ユーザーライセンスの種類が無効です

**原因:** デバイスを登録しようとしているユーザーには、有効な Intune ライセンスがありません。

#### <a name="resolution"></a>解決策
1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)にアクセスし、 **[ユーザー]**  >  **[アクティブなユーザー]** の順に選択します。
2. 影響を受けるユーザーアカウント >**製品ライセンス** > **編集** を選択します。
3. 有効な Intune ライセンスがこのユーザーに割り当てられていることを確認してください。
4. デバイスを再度登録します。

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>ユーザー名を認識できません。 このユーザーアカウントには Microsoft Intune を使用する権限がありません。 このメッセージを "エラー" として受信したと思われる場合は、システム管理者に連絡してください。

**原因:** デバイスを登録しようとしているユーザーには、有効な Intune ライセンスがありません。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)にアクセスし、 **[ユーザー]**  >  **[アクティブなユーザー]** の順に選択します。
2. 影響を受けるユーザーアカウントを選択し、 **[製品ライセンス]**  >  **[編集]** の順に選択します。
3. 有効な Intune ライセンスがこのユーザーに割り当てられていることを確認してください。
4. デバイスを再度登録します。

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>プロファイルのインストールに失敗しました。 新しい MDM ペイロードが古いペイロードと一致しません。

**原因:** 管理プロファイルはデバイスに既にインストールされています。

#### <a name="resolution"></a>解決策

1. IOS デバイスの **設定** を開き、 **全般** >  **デバイス管理**> ます。
2. 既存の管理プロファイルをタップし、 **[管理の削除]** をタップします。
3. デバイスを再度登録します。

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**原因:** Apple Push Notification Service (APNs) 証明書がないか、無効であるか、有効期限が切れています。

#### <a name="resolution"></a>解決策
有効な APNs 証明書が Intune に追加されていることを確認します。 詳細については、[iOS および Mac のデバイス管理の設定](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)に関するページをご覧ください。 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**原因:** Intune で構成されている Apple Push Notification service (APNs) 証明書に問題があります。

#### <a name="resolution"></a>解決策
APNs 証明書を更新してから、デバイスを再登録します。

> [!IMPORTANT]
> APNs 証明書を更新していることを確認します。 APNs 証明書を置き換えないでください。 証明書を置き換える場合は、すべての iOS デバイスを Intune に再登録する必要があります。 

- Intune スタンドアロンで APNs 証明書を更新するには、「 [APPLE MDM プッシュ通知証明書を更新](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)する」を参照してください。
- Configuration Manager を使用して Intune ハイブリッドで APNs 証明書を更新する方法については、「 [System Center Configuration Manager と Microsoft Intune を使用した iOS ハイブリッドデバイス管理のセットアップ](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)」を参照してください。
- Office 365 で APNs 証明書を更新するには、「 [iOS デバイス用の Apns 証明書を作成](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7)する」を参照してください。

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR 接続が無効です

登録プロファイルが割り当てられている DEP 管理対象デバイスを有効にすると、登録が失敗し、次のエラーメッセージが表示されます。

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**原因:** デバイスと Apple DEP サービスの間に接続の問題があります。

#### <a name="resolution"></a>解決策
接続の問題を修正するか、別のネットワーク接続を使用してデバイスを登録してください。 問題が解決しない場合は、Apple に問い合わせる必要がある場合もあります。


## <a name="other-issues"></a>その他の問題

### <a name="dep-enrollment-doesnt-start"></a>DEP 登録が開始しない
登録プロファイルが割り当てられている DEP 管理対象デバイスを有効にすると、Intune の登録プロセスが開始されません。

**原因:** 登録プロファイルは、DEP トークンが Intune にアップロードされる前に作成されます。

#### <a name="resolution"></a>解決策

1. 登録プロファイルを編集します。 プロファイルに変更を加えることができます。 目的は、プロファイルの変更時刻を更新することです。
2. DEP で管理されているデバイスの同期: Intune ポータル >**管理** > **モバイルデバイス管理**の > **iOS** > **Device Enrollment Program** > 同期 を**開始**します。 同期要求が Apple に送信されます。

### <a name="dep-enrollment-stuck-at-user-login"></a>ユーザーログイン時の DEP 登録スタック
登録プロファイルが割り当てられている DEP 管理対象デバイスを有効にすると、資格情報を入力した後に初期セットアップが表示されます。

**原因:** Multi-factor authentication (MFA) が有効になっています。 現在、DEP デバイスでの登録時に MFA は機能しません。

#### <a name="resolution"></a>解決策
MFA を無効にしてから、デバイスを再登録します。

## <a name="next-steps"></a>次の手順

- [Intune のデバイス登録に関するトラブルシューティング](../troubleshoot-device-enrollment-in-intune.md)
- [Intune フォーラムで質問する](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Microsoft Intune サポートチームのブログを確認する](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Microsoft Enterprise Mobility and Security のブログを確認する](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
