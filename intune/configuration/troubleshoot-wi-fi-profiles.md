---
title: Microsoft Intune での Wi-Fi デバイス プロファイル ログのトラブルシューティングと確認 - Azure | Microsoft Docs
description: Microsoft Intune での Android、iOS、Windows デバイス上の Wi-Fi デバイス構成プロファイルに関する問題について理解し、トラブルシューティングします。 ログを確認し、いくつかの一般的な問題と考えられる解決策を確認します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77f5787509438ec3280f29be8449d78979806042
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74542664"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Microsoft Intune での Wi-Fi デバイス構成プロファイルのトラブルシューティング

Intune では、Wi-Fi ネットワークの接続設定を含むデバイス構成プロファイルを作成できます。 ユーザーの Android、iOS、Windows デバイスを組織のネットワークに接続するには、これらの設定を使用します。

この記事では、Wi-Fi プロファイルがデバイスに正常に適用された場合にどのように見えるかを示します。 ログ情報、一般的な問題なども含まれます。 この記事では、Wi-Fi プロファイルのトラブルシューティングについて説明します。

Intune の Wi-Fi プロファイルの詳細については、[デバイスに Wi-Fi 設定を追加して使用する](wi-fi-settings-configure.md)方法に関する記事を参照してください。

## <a name="before-you-begin"></a>始める前に

この記事の例では、Intune プロファイルに SCEP 証明書認証を使用します。 また、信頼されたルート プロファイルと SCEP プロファイルがデバイスで正しく動作することを前提としています。

## <a name="android"></a>Android

このセクションでは、Android デバイスに構成プロファイルをインストールする際のエンド ユーザー エクスペリエンスについて順を追って説明します。

### <a name="end-user-experience-example"></a>エンド ユーザー エクスペリエンスの例

このシナリオでは、Nokia 6.1 デバイスを使用します。 Wi-Fi プロファイルをデバイスにインストールする前に、信頼されたルート プロファイルと SCEP プロファイルをインストールしてください。

1. エンド ユーザーは、信頼されたルート証明書プロファイルをインストールするための通知を受け取ります。

    > [!div class="mx-imgBorder"]
    > ![信頼されたルート証明書プロファイルをインストールするための Android のサンプル ポータル サイト アプリの通知](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. 次の通知では、SCEP 証明書プロファイルをインストールするように求められます。

    > [!div class="mx-imgBorder"]
    > ![Android で SCEP 証明書プロファイルをインストールするためのサンプル ポータル サイト アプリの通知](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > デバイス管理者によって管理されている Android デバイスを使用する場合、複数の証明書が表示される場合があります。 証明書プロファイルが失効または削除されても、証明書はデバイスに残ります。 このシナリオでは、最新の証明書を選択します。 通常、一覧の最後に表示される証明書です。
    >
    > このような状況は、Android Enterprise および Samsung Knox デバイスでは発生しません。 詳細については、[Android の仕事用プロファイル デバイスの管理](../enrollment/android-enterprise-overview.md)と [SCEP および PKCS 証明書の削除](../protect/remove-certificates.md#android-knox-devices)に関する記事を参照してください。

3. 次に、ユーザーは Wi-Fi プロファイルをインストールするための通知を受け取ります。

    > [!div class="mx-imgBorder"]
    > ![Android で SCEP 証明書プロファイルをインストールするためのサンプル ポータル サイト アプリの通知](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. 完了すると、Wi-Fi 接続は保存済みのネットワークとして表示されます。

    > [!div class="mx-imgBorder"]
    > ![Wi-Fi 接続が保存済みのネットワークとして表示される](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>ポータル サイト アプリのログを確認する

Android 上の **Omadmlog.log** ファイルには、デバイスにインストールされたときの Wi-Fi プロファイルのアクティビティの詳細が記録されます。 最大 5 つの Omadmlog ログ ファイルが存在する場合があります。 関連するログ エントリを見つけるために役立つので、最後の同期のタイムスタンプを必ず取得してください。

次の例では、[CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) を使用してログを読み取り、"wifimgr" を検索します。

> [!div class="mx-imgBorder"]
> ![Wi-Fi 接続が保存済みのネットワークとして表示される](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

次のログには検索結果が示され、Wi-Fi プロファイルが正常に適用されたことが示されています。

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

Wi-Fi プロファイルがデバイスにインストールされると、 **[Management Profile]\(管理プロファイル\)** に表示されます。

> [!div class="mx-imgBorder"]
> ![iOS デバイスの [Management Profile]\(管理プロファイル\)](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![Wi-Fi 接続が iOS デバイス上で Wi-Fi ネットワークと表示される](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>iOS コンソールとデバイスのログを確認する

iOS デバイスでは、ポータル サイト アプリのログに Wi-Fi プロファイルに関する情報は含まれません。 Wi-Fi プロファイルのインストールの詳細を確認するには、コンソールまたはデバイスのログを使用します。

1. iOS デバイスを Mac に接続します。 **[アプリケーション]**  >  **[ユーティリティ]** にアクセスし、コンソール アプリを開きます。
2. **[アクション]** で、 **[Include Info Messages]\(情報メッセージを含める\)** と **[Include Debug Messages]\(デバッグ メッセージを含める\)** を選択します。

    > [!div class="mx-imgBorder"]
    > ![iOS コンソール アプリの [Include Info Messages]\(情報メッセージを含める\) と [Include Debug Messages]\(デバッグ メッセージを含める\)](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. シナリオを再現し、ログをテキスト ファイルに保存します。

    1. 現在の画面上にあるすべてのメッセージを選択します: **[編集]**  >  **[すべて選択]** 。
    2. 次のメッセージをコピーします: **[編集]**  >  **[コピー]** 。
    3. ログ データをテキスト エディターに貼り付け、ファイルを保存します。

4. 保存されているログ ファイルを検索して、詳細情報を確認します。 プロファイルが正常にインストールされると、出力は次のログのようになります。

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Wi-Fi プロファイルがデバイスにインストールされたら、 **[設定]**  >  **[アカウント]**  >  **[職場または学校にアクセスする]** の順に移動します。 [アカウント] > **[情報]** の順に選択します。

> [!div class="mx-imgBorder"]
> ![[職場または学校にアクセスする]、Windows デバイスの [情報] を選択する](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

**[Areas managed by Microsoft]\(Microsoft によって管理される領域\)** には **[Wi-Fi]** が表示されます。

> [!div class="mx-imgBorder"]
> ![[Areas managed by Microsoft]\(Microsoft によって管理される領域\) で Wi-Fi が Windows に表示されることを確認します](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Wi-Fi 接続を確認するには、 **[設定]**  >  **[ネットワークとインターネット]**   >  **[Wi-Fi]** の順に移動します。

> [!div class="mx-imgBorder"]
> ![Windows の場合は、[設定] に既知のネットワークとして表示される Wi-Fi 接続を確認します](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>イベント ビューアーのログを確認する

Windows デバイスでは、Wi-Fi プロファイルの詳細がイベント ビューアーに記録されます。

1. **イベント ビューアー** アプリを開きます。
2. **[表示]** メニューで、 **[分析およびデバッグ ログの表示]** を選択します。
3. **[アプリケーションとサービス ログ]**  >  **[Microsoft]**  >  **[Windows]**  >  **[DeviceManagement-Enterprise-Diagnostic-Provider]**  >  **[Admin]** を展開します

出力は次のログのようになります。

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>一般的な問題

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>問題 1:Wi-Fi プロファイルがデバイスに展開されていない

- Wi-Fi プロファイルが正しいグループに割り当てられていることを確認します。

    1. [Microsoft エンドポイント マネージャー管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)で、 **[デバイス]**  >  **[構成プロファイル]** の順に選択します。
    2. プロファイル、 **[割り当て]** の順に選択します。 選択したグループが正しいことを確認します。
    3. エンドポイント マネージャーで、 **[トラブルシューティング + サポート]** を選択します。 **[割り当て]** 情報を確認します。

- エンドポイント マネージャーで、 **[トラブルシューティング + サポート]** を選択します。 **[最後のチェックイン]** の時刻を確認して、デバイスが Intune と同期できることを確認します。

- Wi-Fi プロファイルが信頼されたルート プロファイルと SCEP プロファイルにリンクされている場合、両方のプロファイルがデバイスに展開されていることを確認します。 Wi-Fi プロファイルは、このようなプロファイルに依存しています。

- Windows 10 以降のデバイスで、MDM 診断情報ログを確認します。

  1. **[設定]**  >  **[アカウント]**  >  **[職場または学校にアクセスする]** の順に移動します。
  2. 職場または学校のアカウント > **[情報]** の順に選択します。
  3. **[設定]** ページの下部にある **[レポートの作成]** を選択します。
  4. ログ ファイルのパスを示すウィンドウが開きます。 **[エクスポート]** を選択します。
  5. `\Users\Public\Documents\MDMDiagnostics` パスに移動し、レポートを表示します。

      > [!div class="mx-imgBorder"]
      > ![Windows 10 デバイスの WiFi プロファイル構成を示すサンプル MDM 診断情報](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > 詳細については、「[Windows 10 での MDM エラーの診断](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)」を参照してください。

- Android デバイスでは、信頼されたルート プロファイルと SCEP プロファイルがデバイスにインストールされていない場合、ポータル サイト アプリの Omadmlog ファイルに次のエントリがあります。

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - 信頼されたルート プロファイルと SCEP プロファイルが Android デバイス上にあり、準拠している場合、Wi-Fi プロファイルがデバイス上に存在しない可能性があります。 この問題は、ポータル サイトアプリの **CertificateSelector** プロバイダーが、指定された条件に一致する証明書を見つけられない場合に発生します。 具体的な条件は、証明書テンプレートまたは SCEP プロファイルにあります。

    一致する証明書が見つからない場合、デバイス上の証明書はインストールされません。 正しい証明書がないため、Wi-Fi プロファイルは適用されません。 このシナリオでは、ポータル サイト アプリの Omadmlog ファイルに次のエントリがあります。

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    次のサンプル ログには、**任意の目的**という拡張キー使用法 (EKU) の条件が指定されているため、除外されている証明書があります。 ただし、デバイスに割り当てられている証明書には、その EKU がありません。

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    次のサンプルは、**任意の目的**の EKU が入力された SCEP プロファイルを示しています。 ただし、証明機関 (CA) の証明書テンプレートには入力されていません。 この問題を解決するには、 **[任意の目的]** オプションを証明書テンプレートに追加します。 または、SCEP プロファイルから **[任意の目的]** オプションを削除します。

    > [!div class="mx-imgBorder"]
    > ![Android 上で、証明機関の証明書テンプレートに任意の目的を追加する](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![Android 上で、Intune の SCEP 証明書構成プロファイルに任意の目的を追加する](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - 完全な証明書チェーンの必要なすべての証明書が Android デバイス上にあることを確認します。 そうでない場合、Wi-Fi プロファイルをデバイスにインストールすることができません。 詳細については、「[中間認証局が存在しない](https://developer.android.com/training/articles/security-ssl#MissingCa)」(Android の Web サイトが開きます) を参照してください。
  - Omadmlog をキーワードでフィルター処理し、Wi-Fi プロファイルで使用されている証明書や、プロファイルが正常に適用されたかどうかなどの情報を探します。

    たとえば、[CMTrace](https://docs.microsoft.com/sccm/core/support/cmtrace) を使用してログを読み取ります。 検索文字列を使用して、"wifimgr" をフィルター処理します。

    > [!div class="mx-imgBorder"]
    > ![Android デバイスで Wi-FiMgr 構成プロファイルを検索するように CMTrace をフィルター処理する](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    出力は次の例のようになります。

    > [!div class="mx-imgBorder"]
    > ![Wi-Fi Intune 構成プロファイルがデバイスに正常に適用されたことを示すサンプル CMTrace ログ出力](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    ログにエラーが出現する場合は、そのエラーのタイム スタンプをコピーし、ログのフィルターを解除します。 次に、タイム スタンプと共に [検索] オプションを使用して、エラーの直前に何が起こったかを確認します。

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>問題 2:Wi-Fi プロファイルはデバイスに展開されていますが、デバイスはネットワークに接続できません

通常、この問題は Intune 以外の何かが原因で発生します。 次のタスクは、接続の問題を理解してトラブルシューティングするために役立ちます。

- Wi-Fi プロファイルと同じ条件を持つ証明書を使用して、ネットワークに手動で接続します。

  接続できる場合は、手動接続で証明書のプロパティを確認します。 次に、同じ証明書プロパティを使用して Intune Wi-Fi プロファイルを更新します。
- 通常、接続エラーは Radius サーバー ログに記録されます。 たとえば、デバイスが Wi-Fi プロファイルに接続しようとしたかどうかが示されます。

## <a name="need-more-help"></a>さらにヘルプが必要な場合

- [Intune ユーザー フォーラム](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)を使用するか、[Microsoft からサポートを受けます](../fundamentals/get-support.md)。

- Microsoft Intune の Wi-Fi プロファイルの詳細については、次の記事を参照してください。

  - [Android](wi-fi-settings-android.md)、[iOS](wi-fi-settings-ios.md)、[Windows 10 以降](wi-fi-settings-windows.md) を実行しているデバイスの Wi-Fi 設定を追加します。
  - [サポートのヒント - Intune で SCEP 証明書の展開用に NDES を構成する方法](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - [SCEP 証明書プロファイルの展開](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune)と [NDES の構成](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)をトラブルシューティングします。

- 最新のニュース、情報、技術のヒントについては、次の公式ブログを参照してください。
  - [Microsoft Intune サポート チームのブログ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Enterprise Mobility and Security のブログ](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>次の手順

[プロファイルを監視します](device-profile-monitor.md)。
