---
title: Microsoft Intune - Azure での Android Zebra デバイス ログオン使用 StageNow |Microsoft Docs
description: Microsoft Intune で Android デバイスで StageNow を使用する場合、一般的な問題と解決策を参照してください。 ログを取得し、成功またはエラーのログを読み取る方法の例を参照する方法についても説明します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490543"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>トラブルシューティングを行うし、Microsoft Intune で Android Zebra デバイスで潜在的な問題を参照してください。

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune で使用することができます[Zebra の Android デバイスを管理するように、Zebra モビリティ拡張機能 (MX)](android-zebra-mx-overview.md)します。 Zebra デバイスを使用する場合は、設定を管理する StageNow でプロファイルを作成し、Intune にアップロードします。 Intune では、StageNow アプリを使用して、デバイスの設定を適用します。 StageNow アプリには、トラブルシューティングに使用されるデバイスの詳細なログ ファイルも作成します。

この機能は、以下に適用されます。

- Android

などのデバイスを構成する StageNow でプロファイルを作成します。 StageNow プロファイルを作成するときに、最後の手順は、プロファイルをテストするのにファイルを生成します。 デバイス上 StageNow アプリでは、このファイルを使用するとします。

別の例では、StageNow でプロファイルを作成し、それをテストします。 Intune では、StageNow プロファイルを追加し、Zebra デバイスに割り当てます。 割り当てられたプロファイルの状態を確認するには、プロファイルには、全体的な状態が表示されます。

どちらの場合も、StageNow プロファイルが適用されるたびに、デバイスに保存されている StageNow ログ ファイルからの詳細を取得できます。

いくつかの問題は、StageNow プロファイルの内容に関連していないし、ログに反映されません。

この記事では、StageNow ログを読み取る方法を示し、ログが反映されない Zebra デバイスとその他のいくつかの潜在的な問題を一覧表示されます。

[使用して、Zebra モビリティの拡張機能による Zebra デバイスの管理](android-zebra-mx-overview.md)がこの機能の詳細について。

## <a name="get-the-logs"></a>ログを取得します

### <a name="use-the-stagenow-app-on-the-device"></a>StageNow アプリをデバイスを使用します。
使用する代わりに、コンピューターに直接 StageNow を使用してプロファイルをテストするとき[Intune プロファイルを展開する](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)デバイス上の StageNow アプリ、テストからログを保存します。 ログ ファイルを取得するには、使用、**以上 (...)** StageNow アプリでデバイス上のオプション。

### <a name="get-logs-using-android-debug-bridge"></a>Android Debug Bridge を使用してログを取得します。
プロファイルが既に Intune を使用したデプロイ後にログを取得、デバイスを使用しているコンピューターに接続[Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) (Android の web サイトを開きます)。

デバイスのログを保存します。 `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>電子メールからログを取得します。
プロファイルが既に Intune を使用したデプロイ後にログを取得、エンドユーザーを電子メール送信でくデバイスの電子メール アプリを使用してログ。 Zebra デバイスでポータル サイト アプリを開くと[、ログの送信先](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)します。 送信のログ機能を使用しても作成、PowerLift インシデント ID で、Microsoft サポートに連絡する場合に参照することができます。

## <a name="read-the-logs"></a>ログを読み取る

ログを調べるときにエラーがあるが表示されるたびに、`<characteristic-error>`タグ。 エラーの詳細が書き込む、`<parm-error>`タグ >`desc`プロパティ。

## <a name="error-types"></a>エラーの種類

Zebra デバイスには、レポート レベル別のエラーが含まれます。

- CSP は、デバイスでサポートされていません。 たとえば、デバイスは、携帯電話デバイスはありませんし、移動体通信マネージャーがないです。
- MX または os X バージョンが一致しません。 各 CSP では、バージョン管理します。 完全なサポート マトリックスの場合は、次を参照してください。 [Zebra のドキュメント](http://techdocs.zebra.com/mx/)(Zebra の web サイトを開きます)。
- デバイスは、別の問題またはエラーを報告します。

## <a name="examples"></a>例

たとえば、次の入力プロファイルがあります。

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

ログには、XML は、入力と同じです。 一致するこの出力は、エラーなしでデバイスに正常に適用するプロファイルを意味します。

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

含まれているログは、エラーを表示、`<characteristic-error>`タグ。 このシナリオでは、プロファイルがで指定されたパスが存在しない Android パッケージ (APK) をインストールしようとしました。

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

## <a name="other-potential-issues-with-zebra-devices"></a>Zebra デバイスとその他の潜在的な問題

このセクションでは、Zebra デバイスがデバイスの管理者を使用する場合に表示されるその他の考えられる問題を示します。 これらの問題は、StageNow ログで報告されません。

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView が古くなっています。

古いデバイスがポータル サイト アプリを使用してサインインするときに、ユーザーが System WebView コンポーネントは、期限切れであり、必要なアップグレードを表示することがあります。 Google Play がインストールされている場合は、デバイスがある、インターネット、および更新プログラムの確認に接続します。 デバイスを持っていない場合は、Google Play がインストールされているし、コンポーネントの更新バージョンを取得、デバイスに適用します。 または、Zebra によって発行された OS の最新のデバイスに更新します。

### <a name="management-actions-take-a-long-time"></a>管理操作に時間がかかる

Google Play サービスが使用できない場合、いくつかのタスクを完了する最大 8 時間がかかる場合します。 [Android 用の制限事項の Intune 会社ポータル アプリ](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china)(別の Microsoft web サイトを開きます) 適切なリソースがあります。

### <a name="device-spoofing-suspected-shows-in-intune"></a>Intune で「デバイスのスプーフィングの疑いのある」が表示されます。

このエラーは、Intune 可能性 Zebra Android 以外のデバイスをそのモデルと製造元 Zebra デバイスとして報告があることを意味します。

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>ポータル サイト アプリが必要な最小バージョンより古い

Intune は、ポータル サイト アプリの必要最小バージョンは更新できます。 Google Play がデバイスにインストールされていない場合、ポータル サイト アプリを自動的に更新を取得しません。 必要な最小バージョンがインストールされているバージョンより新しい、ポータル サイト アプリは動作を停止します。 使用してポータル サイト アプリの最新の更新[Zebra デバイスにサイドローディング](android-zebra-mx-overview.md#sideload-the-company-portal-app)します。

## <a name="next-steps"></a>次の手順

[Zebra ディスカッション掲示板](https://developer.zebra.com/community/home/discussions)(Zebra の web サイトを開きます)

[使用し、Intune で Zebra モビリティの拡張機能による Zebra デバイスの管理](android-zebra-mx-overview.md)
