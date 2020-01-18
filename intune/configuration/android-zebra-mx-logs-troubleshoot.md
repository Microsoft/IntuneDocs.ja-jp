---
title: Microsoft Intune の Android ゼブラデバイスで StageNow ログを使用する-Azure |Microsoft Docs
description: Microsoft Intune で Android デバイスで StageNow を使用する際の一般的な問題と解決策をご覧ください。 また、ログを取得する方法についても説明し、成功またはエラーのログを読み取る方法の例を示します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2319fb0d1198289398912793e52482bf66d87173
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206841"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Microsoft Intune で Android ゼブラデバイスのトラブルシューティングを行い、潜在的な問題を確認する



Microsoft Intune では、[ゼブラ Mobility Extensions (MX) を使用して、Android ゼブラデバイスを管理](android-zebra-mx-overview.md)できます。 ゼブラデバイスを使用する場合は、StageNow でプロファイルを作成して設定を管理し、Intune にアップロードします。 Intune では、StageNow アプリを使用して、デバイスに設定を適用します。 また、StageNow アプリは、トラブルシューティングに使用されるデバイス上に詳細なログファイルも作成します。

この機能は、以下に適用されます。

- Android

たとえば、StageNow でプロファイルを作成してデバイスを構成したとします。 StageNow プロファイルを作成すると、最後のステップによって、プロファイルをテストするためのファイルが生成されます。 このファイルは、デバイス上の StageNow アプリで使用します。

別の例では、StageNow でプロファイルを作成し、テストします。 Intune で、StageNow プロファイルを追加し、ゼブラデバイスに割り当てます。 割り当てられたプロファイルの状態を確認するときに、プロファイルに高レベルのステータスが表示されます。

どちらの場合も、StageNow ログファイルから詳細情報を取得できます。これは、StageNow プロファイルが適用されるたびにデバイスに保存されます。

一部の問題は StageNow プロファイルの内容に関連しないため、ログには反映されません。

この記事では、StageNow ログを読み取る方法について説明します。また、ログに反映されない可能性があるゼブラデバイスの潜在的な問題をいくつか示します。

この機能の詳細については[、「ゼブラモビリティ拡張機能を使用してゼブラデバイスを管理する](android-zebra-mx-overview.md)」を参照してください。

## <a name="get-the-logs"></a>ログを取得する

### <a name="use-the-stagenow-app-on-the-device"></a>デバイスで StageNow アプリを使用する
でコンピューターの StageNow を使用してプロファイルを直接テストする場合、Intune を使用して[プロファイルを展開する](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)のではなく、デバイス上の StageNow アプリによってテストのログが保存されます。 ログファイルを取得するには、デバイスの StageNow アプリで**More (...)** オプションを使用します。

### <a name="get-logs-using-android-debug-bridge"></a>Android Debug Bridge を使用してログを取得する
プロファイルが既に Intune と共に展開された後でログを取得するには、 [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb)を搭載したコンピューターにデバイスを接続します (Android の web サイトを開きます)。

デバイスでは、ログはに保存され `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>電子メールからログを取得する
プロファイルが既に Intune と共に展開された後でログを取得するために、エンドユーザーは、デバイス上の電子メールアプリを使用してログを電子メールで送信できます。 ゼブラデバイスで、ポータルサイトアプリを開き、ログを[送信](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)します。 ログの送信機能を使用すると、PowerLift インシデント ID も作成されます。これは、Microsoft サポートに連絡する場合に参照できます。

## <a name="read-the-logs"></a>ログを読み取る

ログを見ると、`<characteristic-error>` タグが表示されるたびにエラーが発生します。 エラーの詳細は `desc` プロパティ > `<parm-error>` タグに書き込まれます。

## <a name="error-types"></a>エラーの種類

ゼブラデバイスには、さまざまなエラー報告レベルがあります。

- CSP はデバイスではサポートされていません。 たとえば、デバイスは携帯電話デバイスではなく、携帯電話マネージャーを備えていません。
- MX または OSX のバージョンが一致しません。 各 CSP はバージョン管理されます。 完全なサポートマトリックスについては、[ゼブラのドキュメント](http://techdocs.zebra.com/mx/)(ゼブラの web サイトを開きます) を参照してください。
- デバイスは、別の問題またはエラーを報告します。

## <a name="examples"></a>例

たとえば、次の入力プロファイルがあるとします。

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

ログでは、XML は入力と同じです。 この一致出力は、プロファイルが正常にデバイスに適用され、エラーが発生しないことを意味します。

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

別の例では、次の入力があります。

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

ログには `<characteristic-error>` タグが含まれているため、エラーが表示されます。 このシナリオでは、プロファイルは、指定されたパスに存在しない Android パッケージ (APK) をインストールしようとしました。

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>ゼブラデバイスに関するその他の潜在的な問題

このセクションでは、デバイス管理者でゼブラデバイスを使用する場合に発生する可能性のあるその他の問題について説明します。 これらの問題は、StageNow ログでは報告されません。

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView が最新ではありません

古いデバイスがポータルサイトアプリを使用してサインインすると、システムの WebView コンポーネントが古く、アップグレードが必要であるというメッセージがユーザーに表示されることがあります。 デバイスに Google Play がインストールされている場合は、インターネットに接続し、更新プログラムを確認します。 デバイスに Google Play がインストールされていない場合は、更新されたバージョンのコンポーネントを取得し、デバイスに適用します。 または、ゼブラによって発行された最新のデバイス OS に更新します。

### <a name="management-actions-take-a-long-time"></a>管理アクションに長い時間がかかる

Google Play サービスが利用できない場合は、一部のタスクが完了するまでに最大8時間かかります。 [Android 用の Intune ポータルサイトアプリ](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china)(別の Microsoft web サイトを開く) の制限は、適切なリソースである可能性があります。

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune での "デバイススプーフィングの疑い" の表示

このエラーは、ゼブラ以外の Android デバイスが、モデルと製造元をゼブラデバイスとして報告していることを Intune が推測していることを意味します。

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>ポータルサイトアプリが最低限必要なバージョンより古い

Intune は、ポータルサイトアプリの最低限必要なバージョンを更新する場合があります。 デバイスに Google Play がインストールされていない場合、ポータルサイトアプリは自動的に更新されません。 最低限必要なバージョンがインストールされているバージョンより新しい場合、ポータルサイトアプリは動作を停止します。 [ゼブラデバイスでサイドローディング](android-zebra-mx-overview.md#sideload-the-company-portal-app)を使用して、最新のポータルサイトアプリに更新します。

## <a name="next-steps"></a>次のステップ

[ゼブラディスカッションボード](https://developer.zebra.com/community/home/discussions)(ゼブラの web サイトを開く)

[Intune で Zebra モビリティ拡張機能を備えた Zebra デバイスを使用および管理する](android-zebra-mx-overview.md)
