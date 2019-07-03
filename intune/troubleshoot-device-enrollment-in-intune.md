---
title: デバイス登録に関するトラブルシューティング
titleSuffix: Microsoft Intune
description: Microsoft Intune でデバイス登録に問題が発生した場合の解決方法の推奨事項。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c304cafa03d9a88831048a271fa4d74b17a944f
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528756"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Microsoft Intune でのデバイス登録に関するトラブルシューティング

この記事では、[デバイス登録](device-enrollment.md)で問題が発生した場合の解決方法を提案します。 この情報で問題が解決しない場合、さらに役立つ方法を探すには、「[Microsoft Intune のサポートを受ける方法](get-support.md)」を参照してください。


## <a name="initial-troubleshooting-steps"></a>最初のトラブルシューティングの手順

トラブルシューティングを開始する前に、登録を有効にするように Intune を構成していることを確認してください。 構成要件は次で確認できます。

- [Microsoft Intune にデバイスを登録する準備](setup-steps.md)
- [iOS および Mac のデバイス管理をセットアップする](ios-enroll.md)
- [Windows デバイスの管理をセットアップする](windows-enroll.md)
- [Android デバイスの管理をセットアップする](android-enroll.md) - 追加の手順は必要ありません

ユーザーのデバイス上の時刻と日付が正しく設定されていることも確認できます。

1. デバイスを再起動します。
2. エンド ユーザーのタイム ゾーンに関して、時刻と日付の設定が GMT の標準に近いこと (+/- 12 時間以内) を確認します。
3. Intune ポータル サイトをアンインストールして、再インストールしてください (該当する場合)。

マネージド デバイスのユーザーが登録ログと診断ログを収集しておくと、管理者が確認できます。 ユーザーがログを収集する手順については、次のページを参照してください。

- [IT 管理者に Android の登録に関するエラーを送信する](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [IT 管理者に iOS に関するエラーを送信する](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>登録に関する一般的な問題
これらの問題は、すべてのデバイス プラットフォームで発生する可能性があります。

### <a name="device-cap-reached"></a>デバイス キャップに達しました
**問題:** 登録中にエラー ( **"ポータル サイトは一時的に使用できません"** など) がユーザーに表示され、Configuration Manager の DMPdownloader.log にエラー **DeviceCapReached** が含まれます。

**解決方法:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>登録済みデバイス数と上限を確認する

次の手順に従って、割り当てられているユーザーの数が最大デバイス数を超えていないことを確認します。

1. Intune で、 **[デバイスの登録]**  >  **[登録制限]**  >  **[デバイス数の制限]** の順に選択します。 **[デバイス制限]** 列の値に注目してください。

2. Intune で、 **[ユーザー]**  >  **[すべてのユーザー]** > 目的のユーザー > **[デバイス]** の順に選択します。 デバイス数に注目してください。

3. ユーザーの登録済みデバイス数が既にデバイス数の上限に達している場合、以下の操作が行われるまでユーザーはそれ以上の登録を実行することができません。
    - [既存のデバイスが削除される](devices-wipe.md)、または
    - [デバイスの制限を設定](enrollment-restrictions-set.md#set-device-limit-restrictions)することにより、デバイスの上限を増やす。

デバイスの上限に達するのを回避するには、必ず古いデバイス レコードを削除します。

> [!NOTE]
> 
> デバイスの登録上限を超えないように、デバイス登録マネージャー アカウントを使用します (「[Microsoft Intune のデバイス登録マネージャーを使用した企業所有のデバイスの登録](device-enrollment-manager-enroll.md)」をご覧ください)。
> 
> デバイス登録マネージャー アカウントに追加されているユーザー アカウントのユーザー ログインについて条件付きアクセス ポリシーが適用されている場合、そのアカウントは登録を完了できません。

### <a name="company-portal-temporarily-unavailable"></a>"ポータル サイトは一時的に使用できません"
**問題:** デバイスで **"ポータル サイトは一時的に使用できません"** というエラーが表示されます。

**解決方法:**

1.  デバイスから Intune ポータル サイト アプリを削除します。

2.  デバイスでブラウザーを開き、[https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) にアクセスして、ユーザー ログインを試みます。

3.  ユーザーはサインインに失敗した場合、別のネットワークを試してみる必要があります。

4.  それでも失敗する場合は、ユーザーの資格情報が Azure Active Directory と正常に同期していることを確認します。

5.  iOS デバイスでは、ユーザーがログインに成功すると、Intune ポータル サイト アプリをインストールして登録するように求められます。 Android デバイスでは、Intune ポータル サイト アプリを手動でインストールする必要があります。インストール後に、登録を再試行できます。

### <a name="mdm-authority-not-defined"></a>MDM 機関が定義されていません
**問題:** ユーザーに **"MDM 機関が定義されていません"** というエラーが表示されます。

**解決方法:**

1.  MDM 機関が[適切に設定](mdm-authority-set.md)されていることを確認します。
    
2.  ユーザーの資格情報が Azure Active Directory と正常に同期していることを確認します。 ユーザーの UPN と、Microsoft 365 管理センターの Active Directory 情報が一致していることを確認できます。
    UPN が Active Directory 情報と一致しない場合:

    1.  ローカル サーバーで DirSync を無効にします。

    2.  **Intune アカウント ポータル** のユーザー一覧から、一致しないユーザーを削除します。

    3.  Azure サービスで不適切なデータが削除されるまで、約 1 時間待ちます。

    4.  再び DirSync を有効にして、ユーザーが適切に同期していることを確認します。

3.  System Center Configuration Manager と Intune を使用しているシナリオでは、ユーザーが有効なクラウド ユーザー ID を持っていることを確認します。

    1.  SQL Management Studio を開きます。

    2.  適切な DB に接続します。

    3.  データベース フォルダーを開き、**CM_DBName** を探して開きます (この DBName は顧客データベースの名前です)。

    4.  上部にある **[新しいクエリ]** を選択し、次のクエリを実行します。

        -   すべてのユーザーを表示する場合のクエリ: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   特定のユーザーを表示する場合のクエリ (%testuser1% は、検索対象ユーザーの username@domain.com のプレースホルダーです): `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        クエリを入力したら、 **[! 実行]** を選択します。
        結果が返されたら、クラウド ユーザー ID を検索します。  ID が見つからない場合、そのユーザーには Intune を使用するライセンスが付与されていません。

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>会社名に特殊文字が含まれている場合にポリシーの作成またはデバイスの登録ができない
**問題:** ポリシーを作成することやデバイスを登録することができません。

**解決方法:** [Microsoft 365 管理センター](https://admin.microsoft.com/)で、会社名から特殊文字を削除した後、会社情報を保存します。

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>確認済みドメインが複数ある場合にデバイスへのサインインまたはデバイスの登録ができない
**問題:** この問題は、ADFS に 2 番目の確認済みドメインを追加すると発生する可能性があります。 2 番目のドメインのユーザー プリンシパル名 (UPN) サフィックスを持つユーザーがポータルにログインできなくなる場合や、デバイスを登録できなくなる場合があります。


<strong>解決方法:</strong>Microsoft Office 365 ユーザーは、次の場合に、各サフィックスに対して別々の AD FS 2.0 フェデレーション サービス インスタンスを展開する必要があります。
- AD FS 2.0 によるシングル サインオン (SSO) を使用する。かつ
- 組織内にユーザーの UPN サフィックス用のトップ レベル ドメイン (@contoso.com、@fabrikam.com など) を複数持っている。


[AD FS 2.0 用ロールアップ](http://support.microsoft.com/kb/2607496)が <strong>SupportMultipleDomain</strong> スイッチと連携することで、AD FS 2.0 サーバーを追加しなくても、AD FS サーバーはこのような状況に対応できます。 詳細については、[このブログ](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/)を参照してください。


## <a name="android-issues"></a>Android の問題

### <a name="android-enrollment-errors"></a>Android の登録エラー

次の表は、Intune に Android デバイスを登録しているときに、エンド ユーザーに表示される可能性があるエラーの一覧です。

|エラー メッセージ|問題|解決策|
|---|---|---|
|**IT 管理者がアクセスするためのライセンスを割り当てる必要があります**<br>IT 管理者は、このアプリを使用するためのアクセス許可を付与していません。 IT 管理者から支援を受けるか、後でやり直してください。|ユーザーのアカウントに必要なライセンスがないため、このデバイスを登録することはできません。|ユーザーは自分のデバイスを登録する前に、必要なライセンスを割り当てられている必要があります。 このメッセージは、モバイル デバイス管理機関に必要なライセンスの種類をユーザーが持っていないことを示します。 たとえば、次の両方に該当する場合はこのエラーが表示されます。<ol><li>Intune がモバイル デバイス管理機関として設定されている。</li><li>System Center 2012 R2 Configuration Manager ライセンスを使用している。</li></ol>詳細については、「[ユーザー アカウントに Intune のライセンスを割り当てる](/intune/licenses-assign)」を参照してください。|
|**IT 管理者は、MDM 機関を設定する必要があります**<br>IT 管理者が、MDM 機関を設定していないようです。 IT 管理者から支援を受けるか、後でやり直してください。|モバイル デバイス管理機関が定義されていません。|Intune でモバイル デバイス管理機関が設定されていません。 [モバイル デバイス管理機関を設定する](/intune/mdm-authority-set)方法に関する情報を参照してください。|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>デバイスが Intune サービスでチェックインできず、Intune 管理コンソールに "異常" と表示される
**問題:** Android バージョン 4.4.x と 5.x を実行している一部の Samsung デバイスで、Intune サービスでのチェックインが停止する場合があります。 デバイスがチェックインしないと次のような状態になります。

- デバイスは Intune サービスから、ポリシー、アプリ、およびリモート コマンドを受信できない。
- 管理コンソールに**異常**という管理状態が表示される。
- 条件付きアクセス ポリシーによって保護されているユーザーが、企業リソースにアクセスできない可能性がある。

特定の Samsung デバイスに付属する Samsung Smart Manager ソフトウェアは、Intune ポータル サイトとそのコンポーネントを非アクティブ化することができます。 ポータル サイトが非アクティブ状態の場合、バックグラウンドで実行できないため、Intune サービスには接続できません。

**解決方法 1:**

ポータル サイト アプリを手動で起動するようユーザーに通知します。 アプリが再起動すると、デバイスは Intune サービスでチェックインします。

> [!IMPORTANT]
> Samsung Smart Manager はポータル サイト アプリを再度非アクティブ化する場合があるため、ポータル サイト アプリを手動で開くのは一時的な解決法です。

**解決方法 2:**

Android 6.0 へのアップグレードを試みるようユーザーに通知します。 Android 6.0 デバイスでは、非アクティブ化の問題は発生しません。 更新プログラムが利用可能かどうかを確認するには、 **[設定]**  >  **[デバイスのバージョン情報]**  >  **[Download updates manually]\(更新プログラムを手動でダウンロードする\)** の順に移動し、指示に従います。

**解決方法 3:**

解決方法 2 で解決しない場合は、ユーザーに以下の手順に従って、Smart Manager でポータル サイト アプリを除外するよう通知します。

1. デバイスで Smart Manager アプリを起動します。

   ![デバイスの Smart Manager アイコンを選択する](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. **[バッテリ]** タイルを選択します。

   ![[バッテリ] タイルを選択する](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. **[App power saving]** (アプリの省電力) または **[App optimization]** (アプリの最適化) で、 **[詳細]** を選択します。

   ![[App power saving] (アプリの省電力) または [App optimization] (アプリの最適化) で [詳細] を選択する](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. アプリのリストから **[ポータル サイト]** を選択します。

   ![アプリ リストから [ポータル サイト] を選択する](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. **[オフ]** を選択します。

   ![[App optimization] (アプリの最適化) ダイアログから [オフ] を選択する](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. **[App power saving]** (アプリの省電力) または **[App optimization]** (アプリの最適化) で、ポータル サイトがオフになっていることを確認します。

   ![ポータル サイトがオフになっていることを確認する](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>プロファイルのインストールに失敗しました
**問題:** Android デバイスで **"プロファイルのインストールに失敗しました"** というエラーがユーザーに表示されます。

**解決方法:**

1.  使用している Intune サービスのバージョンについて、適切なライセンスがユーザーに割り当てられていることを確認します。

2.  デバイスが別の MDM プロバイダーに既に登録されていないことを確認します。

3. デバイスに管理プロファイルが既にインストールされていないことを確認します。

4.  Android 用の Chrome が既定のブラウザーであり、Cookie が有効であることを確認します。

### <a name="android-certificate-issues"></a>Android 証明書に関する問題

**問題**:ユーザーが自分のデバイス上で、[*You cannot sign in because your device is missing a required certificate.]\(デバイスに必要な証明書がないためにサインインすることはできません。\)* というメッセージを受信します。

**解決方法 1**:

ユーザーは「[Your device is missing a required certificate (デバイスに必要な証明書がありません)](/intune-user-help/your-device-is-missing-a-required-certificate-android)」の手順に従って、不足している証明書を取得できる場合があります。 引き続きエラーが発生する場合は、解決方法 2 をお試しください。

**解決方法 2**:

企業の資格情報を入力し、フェデレーション ログイン ページにリダイレクトされた後も、証明書がないというエラーが表示される場合があります。 その場合のエラーは、Active Directory フェデレーション サービス (AD FS) サーバーで中間証明書が不足していることを意味する可能性があります。

Android デバイスでは、[SSL のサーバー ハロー](https://technet.microsoft.com/library/cc783349.aspx)に中間証明書が含まれている必要があるため、この証明書エラーが発生します。 現在、AD FS サーバーまたは WAP - AD FS プロキシ サーバーの既定のインストールでは、AD FS サービスの SSL 証明書だけが、SSL のクライアント ハローに対する SSL のサーバー ハロー応答で送信されます。

この問題を解決するには、AD FS サーバーまたはプロキシでコンピューターの個人証明書に証明書を次のようにインポートします。

1. ADFS およびプロキシ サーバー上で、 **[開始]** を右クリックし、 **[実行]**  >  **[certlm.msc]** の順にクリックして、ローカル コンピューターの証明書管理コンソールを起動します。
2. **[個人用]** を展開し、 **[証明書]** を選択します。
3. AD FS サービス通信の証明書を見つけ (公的に署名された証明書)、ダブルクリックしてそのプロパティを表示します。
4. **[証明のパス]** タブを選択し、証明書の親証明書を選択します。
5. 親証明書ごとに、 **[証明書の表示]** を選択します。
6. **[詳細]**  >  **[ファイルへコピー]** の順に選択します。
7. ウィザードの指示に従い、親証明書の公開鍵を任意のファイル保存先にエクスポート (保存) します。
8. 右クリックして **[証明書]**  >  **[すべてのタスク]**  >  **[インポート]** の順に選択します。
9. ウィザードの指示に従い、親証明書を **Local Computer\Personal\Certificates** にインポートします。
10. AD FS サーバーを再起動します。
11. すべての AD FS サーバーとプロキシ サーバーで上記の手順を繰り返します。

証明書が適切にインストールされたことを確認するには、[https://www.digicert.com/help/](https://www.digicert.com/help/) で診断ツールを使用できます。 **[Server Address]\(サーバー アドレス\)** ボックスに、AD FS サーバーの FQDN (例: sts.contso.com) を入力し、 **[Check Server]\(サーバーの確認\)** をクリックします。

**証明書が正しくインストールされていることを確認するには**:

証明書が正しくインストールされていることを確認する方法とツールはたくさんあります。下記で紹介する手順はその 1 つです。

1. [[無料の Digicert ツール]](ttps://www.digicert.com/help/) に進みます。
2. AD FS サーバーの完全修飾ドメイン名 (例: sts.contoso.com) を入力し、 **[CHECK SERVER]** を選択します。

サーバー証明書が正しくインストールされている場合、結果にすべてのチェック マークが表示されます。 上記の問題が存在する場合、レポートの "Certificate Name Matches" (証明書名の一致) セクションと "SSL Certificate is correctly Installed" (SSL 証明書が正しくインストールされている) セクションに赤い X 印が付きます。


## <a name="ios-issues"></a>iOS の問題

### <a name="ios-enrollment-errors"></a>iOS の登録エラー
次の表は、Intune に iOS デバイスを登録している最中にエンド ユーザーに表示される可能性があるエラーの一覧です。

|エラー メッセージ|問題|解決策|
|-------------|-----|----------|
|NoEnrollmentPolicy|登録ポリシーが見つかりません|Apple Push Notification Services (APNs) 証明書などのすべての登録前提条件が構成済みであること、"プラットフォームとしての iOS" が有効であることを確認します。 手順については、「[iOS および Mac のデバイス管理をセットアップする](ios-enroll.md)」を参照してください。|
|DeviceCapReached|登録されているモバイル デバイス数が多すぎます。|別のモバイル デバイスを登録する前に、ユーザーは現在登録されているモバイル デバイスの 1 つをポータル サイトから削除する必要があります。 使用しているデバイスの種類ごとの手順([Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android)、[iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios)、[Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows)) を参照してください。|
|APNSCertificateNotValid|モバイル デバイスと会社のネットワークとの通信を可能にする証明書に問題があります。<br /><br />|Apple Push Notification Service (APNs) には、登録済みの iOS デバイスに接続するチャネルが用意されています。 次場合、登録は失敗し、このメッセージが表示されます。<ul><li>APN 証明書を取得する手順が完了していない。または</li><li>APN 証明書の有効期限が切れている。</li></ul>ユーザー設定方法の詳細については、「[Active Directory を同期化して Intune にユーザーを追加する](users-add.md)」と[ユーザーとデバイスの整理](groups-add.md)に関するページを確認してください。|
|AccountNotOnboarded|モバイル デバイスと会社のネットワークとの通信を可能にする証明書に問題があります。<br /><br />|Apple Push Notification Service (APNs) には、登録済みの iOS デバイスに接続するチャネルが用意されています。 次場合、登録は失敗し、このメッセージが表示されます。<ul><li>APN 証明書を取得する手順が完了していない。または</li><li>APN 証明書の有効期限が切れている。</li></ul>詳細については、「[Microsoft Intune を使用して iOS および Mac の管理をセットアップする](ios-enroll.md)」を確認してください。|
|DeviceTypeNotSupported|ユーザーが iOS 以外のデバイスを使用して登録を試みた可能性があります。 登録しようとしているモバイル デバイスの種類はサポートされていません。<br /><br />デバイスが iOS バージョン 8.0 以降を実行していることを確認します。<br /><br />|ユーザーのデバイスで iOS バージョン 8.0 以降が実行されていることを確認します。|
|UserLicenseTypeInvalid|ユーザーのアカウントがまだ必要なユーザー グループのメンバーではないため、デバイスを登録できません。<br /><br />|ユーザーが自分のデバイスを登録できるようにするには、ユーザーは適切なユーザー グループのメンバーである必要があります。 このメッセージは、モバイル デバイス管理機関に必要なライセンスの種類をユーザーが持っていないことを示します。 たとえば、次の両方に該当する場合はこのエラーが表示されます。<ol><li>Intune がモバイル デバイス管理機関として設定されている。</li><li>System Center 2012 R2 Configuration Manager ライセンスを使用している。</li></ol>詳細については、以下の記事を参照してください。<br /><br />「[Microsoft Intune を使用して iOS および Mac の管理をセットアップする](ios-enroll.md)」のほか、「[Active Directory を同期化して Intune にユーザーを追加する](users-add.md)」と[ユーザーとデバイスの整理](groups-add.md)に関するページでユーザー設定方法についての情報を確認してください。|
|MdmAuthorityNotDefined|モバイル デバイス管理機関が定義されていません。<br /><br />|Intune でモバイル デバイス管理機関が設定されていません。<br /><br />「手順 6:モバイル デバイスを登録してアプリをインストールする」セクションの項目 1 ([Microsoft Intune の 30 日間の試用版の使用](free-trial-sign-up.md)に関するページ) を確認してください。|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>デバイスが無効か、管理コンソールとデバイスが通信できない
**問題:** iOS デバイスが Intune サービスでチェックインしていません。 保護されている企業リソースへのアクセスを維持するには、デバイスがサービスで定期的にチェックインする必要があります。 デバイスがチェックインしないと次のような状態になります。

- デバイスは Intune サービスから、ポリシー、アプリ、およびリモート コマンドを受信できない。
- 管理コンソールに**異常**という管理状態が表示される。
- 条件付きアクセス ポリシーによって保護されているユーザーが、企業リソースにアクセスできない可能性がある。

**解決方法:** 次の解決方法をエンド ユーザーに伝え、企業リソースへのアクセスの回復を支援します。

ユーザーが iOS 用のポータル サイト アプリを起動すると、デバイスと Intune の通信状態が通知されることがあります。 通信していないことが検出された場合、Intune との同期 (再接続) が自動的に試行されます ( **[同期しています]** メッセージが 表示されます)。

  ![[同期しています...] 通知](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

同期できた場合、 **[同期に成功しました]** インライン通知が iOS ポータル サイト アプリに表示されます。デバイスが正常な状態にあることを意味します。

  ![[同期に成功しました] 通知](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

同期できなかった場合、 **[同期できません]** インライン通知が iOS ポータル サイト アプリに表示されます。

  ![[同期できません] 通知](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

この問題を修正するには、 **[セットアップ]** ボタンを選択する必要があります。このボタンは、 **[同期できません]** 通知の右にあります。 [セットアップ] ボタンを押すと、[会社アクセスのセットアップ] フロー画面が表示されます。この画面の指示に従い、デバイスを登録します。

  ![[会社アクセスのセットアップ] 画面](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

登録後、デバイスは正常な状態に戻り、会社リソースへのアクセスが回復します。

### <a name="verify-ws-trust-13-is-enabled"></a>WS-Trust 1.3 が有効になっていることを確認する
**問題** Device Enrollment Program (DEP) iOS デバイスを登録できません

ユーザー アフィニティが設定された DEP デバイスを登録するには、ユーザー トークンを要求するよう WS-Trust 1.3 Username/Mixed エンドポイントを有効にする必要があります。 Active Directory は既定でこのエンドポイントを有効にします。 有効なエンドポイントの一覧を表示するには、Get-AdfsEndpoint PowerShell コマンドレットを使用し、trust/13/UsernameMixed エンドポイントを探します。 次に例を示します。

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

詳細については、[Get-AdfsEndpoint のドキュメント](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint)を参照してください。

詳細については、「[Best practices for securing Active Directory Federation Services](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs)」 (Active Directory フェデレーション サービスのセキュリティ保護に関するベスト プラクティス) を参照してください。 WS-Trust 1.3 Username/Mixed が ID フェデレーション プロバイダーで有効になっているかどうかを判断するには、次にお問い合わせください。
- ADFS を使用している場合は、Microsoft サポート
- サード パーティの ID ベンダー


### <a name="profile-installation-failed"></a>プロファイルのインストールに失敗しました
**問題:** iOS デバイスで **"プロファイルのインストールに失敗しました"** というエラーがユーザーに表示されます。

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>プロファイルのインストールに失敗する場合のトラブルシューティング手順

1.  使用している Intune サービスのバージョンについて、適切なライセンスがユーザーに割り当てられていることを確認します。

2.  デバイスが別の MDM プロバイダーに既に登録されていないことを確認します。

3. デバイスに管理プロファイルが既にインストールされていないことを確認します。

4.  [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) に移動して、プロンプトが表示されたら、プロファイルのインストールを試みます。

5.  iOS 用の Safari が既定のブラウザーであり、Cookie が有効であることを確認します。

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Intune と System Center Configuration Manager を使用するときに、登録済みの iOS デバイスがコンソールに表示されない
**問題:** ユーザーが iOS デバイスを登録しても、そのデバイスが Configuration Manager 管理コンソールに表示されません。 そのデバイスでは、登録済みであることが示されません。 次の原因が考えられます。

- Configuration Manager サイトの Microsoft Intune Connector と Intune サービスとの通信が行われてない。
- データ探索マネージャー (ddm) コンポーネントまたは状態マネージャー (statmgr) のどちらかで Intune サービスからのメッセージが処理されていない。
- あるアカウントで MDM 証明書をダウンロードした後で、それを別のアカウントで使用した可能性があります。


**解決方法:** エラーが発生していないかどうかを次のログ ファイルで確認します。

- dmpdownloader.log
- ddm.log
- statmgr.log

これらのログ ファイルで探す内容の例は近日追加される予定です。


### <a name="users-ios-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>ユーザーの iOS デバイスが登録画面で 10 分以上スタックしている

**問題**:登録中のデバイスが次の 2 つの画面のいずれかでスタックする場合があります。
- "Microsoft" から最終的な構成を待機している。
- ガイド付きのアクセス アプリを利用できない。 管理者に問い合わせてください。

この問題は、次の場合に発生する可能性があります。
- Apple サービスに一時停止が発生している。または
- 次の表に示すように、VPP トークンを使用するよう iOS 登録が設定されているが、VPP トークンに問題がある。

| 登録設定 | 値 |
| ---- | ---- |
| プラットフォーム | iOS |
| ユーザー アフィニティ | ユーザー アフィニティとともに登録する |
|Apple セットアップ アシスタントの代わりにポータル サイトで認証します | はい |
| VPP によるポータル サイトのインストール | Use token: token address\(トークンの使用: トークン アドレス\) |
| Run Company Portal in Single App Mode until authentication\(認証されるまでシングル アプリ モードでポータル サイトを実行する\) | はい |

**解決方法**:問題を解決するには、次の操作を実行する必要があります。
1. VPP トークンに問題があるかどうかを判断し、修正します。
2. ブロックされているデバイスを特定します。
3. 影響を受けているデバイスをワイプします。
4. 登録プロセスを再起動するようユーザーに通知します。

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>VPP トークンに問題があるかどうかを判断する
1. **Intune** >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment program トークン]** > トークン名 > **[プロファイル]** > プロファイル名 > **[管理]**  >  **[プロパティ]** に移動します。
2. プロパティを参照して、次のようなエラーが表示されているかどうかを確認します。
    - このトークンは期限切れになっています。
    - このトークンは、ポータル サイトのライセンスが不足しています。
    - このトークンは別のサービスが使用しています。
    - このトークンは別のテナントが使用しています。
    - このトークンは削除されました。
3. トークンの問題を修正します。

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>VPP トークンを使用して、ブロックされているデバイスを特定する
1. **Intune** >  **[デバイスの登録]**  >  **[Apple の登録]**  >  **[Enrollment Program トークン]** > トークン名 > **[デバイス]** に移動します。
2. **[プロファイルの状態]** 列を **[ブロック]** でフィルターします。
3. **ブロック**されているすべてのデバイスのシリアル番号をメモしておきます。

#### <a name="remotely-wipe-the-blocked-devices"></a>ブロックされているデバイスをリモートでワイプする
VPP トークンを使用して問題を修正した後は、ブロックされているデバイスをワイプする必要があります。
1. **Intune** >  **[デバイス]**  >  **[すべてのデバイス]**  >  **[列]**  >  **[シリアル番号]**  >  **[適用]** に移動します。 
2. ブロックされているデバイスごとに、 **[すべてのデバイス]** の一覧で選択し、 **[ワイプ]**  >  **[はい]** を選択します。

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>登録プロセスを再起動するようユーザーに通知する
ブロックされているデバイスをワイプしたら、登録プロセスを再起動するようユーザーに通知できます。

## <a name="macos-issues"></a>macOS の問題

### <a name="macos-enrollment-errors"></a>macOS の登録エラー
**エラー メッセージ 1:** *It looks like you're using a virtual machine.Make sure you've fully configured your virtual machine, including serial number and hardware model.If this isn't a virtual machine, please contact support.* (仮想マシンを使用しているようです。シリアル番号やハードウェア モデルなど、仮想マシンを完全に構成したことを確認してください。仮想マシンではない場合は、サポートにお問い合わせください。)  

**エラー メッセージ 2**:*We’re having trouble getting your device managed.This problem could be caused if you're using a virtual machine, have a restricted serial number, or if this device is already assigned to someone else.Learn how to resolve these problems or contact your company support.* (デバイスを管理されている状態にする際に問題が発生しました。この問題は、仮想マシンを使用している場合、シリアル番号が制限されている場合、またはこのデバイスが他のユーザーに既に割り当てられている場合に、発生することがあります。これらの問題の解決方法を確認するか、会社のサポートにお問い合わせください。)

**問題:** このメッセージは、次のいずれかの理由の結果である可能性があります。  
* macOS 仮想マシン (VM) が正しく構成されていません  
* デバイスが会社の所有であるか、またはデバイスのシリアル番号が Intune に登録されていることが必要な、デバイス制限が有効になっています  
* デバイスは既に登録されており、Intune 内の他のユーザーにまだ割り当てられています  

**解決方法:** 最初に、ユーザーに確認して、デバイスに影響している問題がどれかを特定します。 次に、次の解決策のうち最も関連のあるものを実行します。
* ユーザーがテスト用に VM を登録している場合は、Intune がそのシリアル番号とハードウェア モデルを認識できるように、完全に構成してあることを確認します。 Intune で [VM をセットアップする](macos-enroll.md#enroll-virtual-macos-machines-for-testing)方法について詳しく学びます。  
* 組織で個人の macOS デバイスをブロックする登録制限が有効になっている場合は、手動で Intune に[個人デバイスのシリアル番号を追加する](corporate-identifiers-add.md#manually-enter-corporate-identifiers)必要があります。  
* デバイスが Intune でまだ別のユーザーに割り当てられている場合は、前の所有者が Intune ポータル サイト アプリを使用してデバイスを削除またはリセットしませんでした。 Intune から古いデバイス レコードをクリーンアップするには:  

    1. [Azure portal で Intune](https://portal.manage.microsoft.com) に移動し、管理資格情報でサインインします。
    2. Intune > **[デバイス]**  >  **[すべてのデバイス]** の順に移動します。  
    3. 登録に問題があるデバイスを探します。 デバイス名または MAC/HW アドレスで検索して結果を絞り込みます。
    4. デバイスを選択し、 **[削除]** を選択します。 デバイスに関連付けられている他のすべてのエントリを削除します。  

## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>System Center Configuration Manager と Intune を使用しているときの問題
### <a name="mobile-devices-disappear"></a>モバイル デバイスが表示されない
**問題:** モバイル デバイスを Configuration Manager に正常に登録した後に、モバイル デバイス コレクションに表示されません。 ただし、デバイスには管理プロファイルがあり、CSS ゲートウェイには表示されます。

**解決方法:** この問題は、次の原因によって発生する可能性があります。
- ドメインに参加していないデバイスを削除するカスタム プロセスがある。または 
- ユーザーがサブスクリプションからデバイスを削除した。
Configuration Manager コンソールで、デバイスを削除したプロセスまたはユーザー アカウントを確認するには、次の手順を実行します。

#### <a name="check-how-device-was-removed"></a>デバイスの削除方法を確認する

1.  Configuration Manager 管理コンソールで、 **[監視]** &gt; **[システム ステータス]** &gt; **[ステータス メッセージ クエリ]** の順に選択します。

2.  **[手動で削除されたコレクションのメンバー リソース]** を右クリックし、 **[メッセージを表示]** を選択します。

3.  適切な時刻/日付または過去 12 時間を選択します。

4.  対象のデバイスを検索し、デバイスが削除された方法を確認します。 次の例では、アカウント SCCMInstall が "不明なアプリケーション" でデバイスを削除しています。

    ![デバイス削除の診断のスクリーン ショット](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  ドメインに参加していない、モバイル、または関連するデバイスを自動的に削除するような、スケジュールされたタスク、スクリプト、または他のプロセスが Configuration Manager にないことを確認します。

### <a name="other-ios-enrollment-errors"></a>iOS のその他の登録エラー
iOS 登録エラーの一覧は、「[Troubleshooting iOS device enrollment problems in Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune)」 (Microsoft Intune での iOS デバイス登録に関する問題のトラブルシューティング) のドキュメントにあります。

## <a name="pc-issues"></a>PC の問題

|エラー メッセージ|問題|解決策|
|---|---|---|
|**IT 管理者がアクセスするためのライセンスを割り当てる必要があります**<br>IT 管理者は、このアプリを使用するためのアクセス許可を付与していません。 IT 管理者から支援を受けるか、後でやり直してください。|ユーザーのアカウントに必要なライセンスがないため、このデバイスを登録することはできません。|ユーザーは自分のデバイスを登録する前に、必要なライセンスを割り当てられている必要があります。 このメッセージは、モバイル デバイス管理機関に必要なライセンスの種類をユーザーが持っていないことを示します。 たとえば、次の両方に該当する場合はこのエラーが表示されます。 <ol><li>Intune がモバイル デバイス管理機関として設定されている。</li><li>System Center 2012 R2 Configuration Manager ライセンスを使用している。</li></ol>[ユーザー アカウントに Intune のライセンスを割り当てる](https://docs.microsoft.com/intune/licenses-assign)方法に関する情報を参照してください。|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>コンピューターは既にサービスに登録されています - エラー hr 0x8007064c
**問題:** **"The machine is already enrolled"** (コンピューターは既にサービスに登録されています) というエラーが発生し、登録に失敗します。 登録ログにはエラー **hr 0x8007064c** が記録されます。

このエラーは、コンピューターが次の状態になったために発生する可能性があります。
- 以前に登録されていた。または
- 既に登録されているコンピューターの複製イメージがある。
前のアカウントのアカウント証明書が、そのコンピューターにまだ存在しています。

**解決方法:**

1. **[スタート]** メニューで、 **[ファイル名を指定して実行]** を選択し、「**MMC**」と入力します。
1. **[ファイル]**  >  **[スナップインの追加と削除]** の順に選択します。
1. **[証明書]** をダブルクリックし、 **[コンピューター アカウント]**  >  **[次へ]** 、 **[ローカル コンピューター]** の順に選択します。
1. **[証明書 (ローカル コンピューター)]** をダブルクリックして、 **[個人証明書]** を選択します。
1. Sc_Online_Issuing によって発行された Intune 証明書を探し、もし見つかった場合は削除します。
1. レジストリ キー**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** が存在する場合は削除し、サブ キーもすべて削除します。
1. 再登録を試行します。
1. それでも PC を登録できない場合は、キー**KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95** を探して、存在する場合は削除してください。
1. 再登録を試行します。

    > [!IMPORTANT]
    > このセクションの作業には、レジストリを変更する手順が含まれます。 ただし、レジストリを正しく変更していない場合、重大な問題が発生する可能性があります。 そのため、手順は確認の上、注意して行ってください。 さらに安全を考慮して、レジストリのバックアップをとってから変更を行ってください。 バックアップがあれば、問題が生じた場合でもレジストリを復元できます。
    > レジストリのバックアップと復元の方法については、「[Windows でレジストリをバックアップおよび復元する方法](https://support.microsoft.com/kb/322756)」をご覧ください。

## <a name="general-enrollment-error-codes"></a>登録の一般的なエラー コード

|エラー コード|問題|推奨される解決策|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |クライアント コンピューターのクロックが正しい時刻に設定されていません。|クライアント コンピューターのクロックおよびタイム ゾーンが正しく設定されていることを確認してください。|
|0x80240438、0x80CF0438、0x80CF402C|Intune サービスに接続できません。 クライアントのプロキシ設定を確認してください。|Intune がクライアント コンピューターでプロキシ構成をサポートしていることを確認します。 クライアント コンピューターがインターネットに接続していることを確認します。|
|0x80240438、0x80CF0438|Internet Explorer とローカル システムのプロキシ設定が構成されていません。|Intune サービスに接続できません。 クライアントのプロキシ設定を確認します。Intune がクライアント コンピューターでプロキシ構成をサポートしていることを確認します。 クライアント コンピューターがインターネットに接続していることを確認します。|
|0x80043001、0x80CF3001、0x80043004、0x80CF3004|登録パッケージが最新ではありません。|[管理] ワークスペースを使用して、最新のクライアント ソフトウェア パッケージをダウンロードしてインストールしてください。|
|0x80043002、0x80CF3002|アカウントがメンテナンス モードです。|アカウントがメンテナンス モードになっている場合は、新しいクライアント コンピューターを登録することはできません。 自分のアカウントの設定を見るには、アカウントにサインインしてください。|
|0x80043003、0x80CF3003|アカウントが削除されています。|Intune のアカウントとサブスクリプションがアクティブであることを確認します。 自分のアカウントの設定を見るには、アカウントにサインインしてください。|
|0x80043005、0x80CF3005|クライアント コンピューターがインベントリから削除されています。|数時間待ってから、コンピューターにある古いバージョンのクライアント ソフトウェアをすべて削除し、クライアント ソフトウェアをもう一度インストールしてください。|
|0x80043006、0x80CF3006|このアカウントに許可されている接続クライアントの最大数に達しました。|サービスにさらにコンピューターを登録する前に、接続クライアント ライセンスを追加購入する必要があります。|
|0x80043007、0x80CF3007|インストーラーと同じフォルダーに証明書ファイルが見つかりませんでした。|インストールを開始する前にすべてのファイルを抽出してください。 抽出したファイルの名前を変更したり移動したりしないでください。すべてのファイルが同じフォルダー内にないと、インストールが失敗します。|
|0x8024D015、0x00240005、0x80070BC2、0x80070BC9、0x80CFD015|クライアント コンピューターの再起動が保留中になっているため、ソフトウェアをインストールできません。|コンピューターを再起動してから、クライアント ソフトウェアをもう一度インストールしてください。|
|0x80070032|クライアント コンピューターが、クライアント ソフトウェアのインストールに必要な 1 つまたは複数の前提条件を満たしていません。|必要なすべての更新プログラムがクライアント コンピューターにインストールされていることを確認してから、クライアント ソフトウェアをもう一度インストールしてください。|
|0x80043008、0x80CF3008|Microsoft オンライン管理更新ービスを開始できませんでした。|「[Microsoft Intune のサポートを受ける方法](get-support.md)」の説明に従って、Microsoft サポートにお問い合わせください。|
|0x80043009、0x80CF3009|クライアント コンピューターは、既にサービスに登録されています。|サービスを再登録する前に、クライアント コンピューターを削除する必要があります。|
|0x8004300B、0x80CF300B|クライアントで実行されている Windows のバージョンがサポートされていないため、クライアント ソフトウェア インストール パッケージを実行できません。|Intune が、クライアント コンピューターで実行されている Windows のバージョンをサポートしていません。|
|0xAB2|Windows インストーラーが、カスタム動作に必要な VBScript ランタイムにアクセスできませんでした。|このエラーは、ダイナミック リンク ライブラリ (DLL) に基づくカスタム動作が原因で発生します。 DLL のトラブルシューティング時に、場合によっては「[Microsoft サポート技術情報 198038:パッケージと展開の問題のための便利なツールの情報](https://support.microsoft.com/kb/198038)」に記載されているツールを使用する必要があります。|
|0x80cf0440|サービス エンドポイントとの接続が切断されました。|試用アカウントまたは有料アカウントが中断されています。 新しい試用アカウントまたは有料アカウントを作成し、再登録してください。|




### <a name="next-steps"></a>次の手順
このトラブルシューティング情報を使っても問題が解決しない場合は、「[Microsoft Intune のサポートを受ける方法](get-support.md)」の説明に従って Microsoft サポートにお問い合わせください。
