---
title: Active Directory 用の Intune コネクタのプロキシ設定を構成する
description: 既存のオンプレミス プロキシ サーバーと連携するように Active Directory 用の Intune コネクタを構成する方法について説明します。
keywords: ''
author: master11218
ms.author: erikje
manager: dougeby
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a1af2e7c8aff281e04e92344b3e2c762bb23e0a
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465750"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>既存のオンプレミス プロキシ サーバーと連携する

この記事では、送信プロキシ サーバーと連携するように Active Directory 用の Intune コネクタを構成する方法について説明します。 ネットワーク環境に既存のプロキシがあるお客様を対象としています。

コネクタのしくみの詳細については、「[Azure AD アプリケーション プロキシ コネクタを理解する](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors)」を参照してください。

## <a name="bypass-outbound-proxies"></a>送信プロキシをバイパスする

コネクタには、送信要求を行う基礎となる OS コンポーネントがあります。 これらのコンポーネントは、Web プロキシ自動検出 (WPAD) を使用してネットワーク上のプロキシ サーバーの検索を自動的に試行します。

OS コンポーネントでは、wpad.domainsuffix の DNS ルックアップを実行してプロキシ サーバーの検索が試行されます。 ルックアップが DNS で解決されると、HTTP 要求が wpad.dat の IP アドレスに対して行われます。 この要求は、環境内のプロキシ構成スクリプトになります。 コネクタはこのスクリプトを使用して、送信プロキシ サーバーを選択します。 ただし、プロキシ上で追加の構成設定が必要なため、コネクタ トラフィックはまだ通過できない可能性があります。

コネクタがオンプレミス プロキシをバイパスして確実に Azure サービスに直接接続するようにコネクタを構成できます。 保守する構成が 1 つ少なくなるため、ネットワーク ポリシーで許可されている限り、この方法をお勧めします。

コネクタの送信プロキシの使用を無効にするには、\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config ファイルを編集し、次のコード サンプルに示すセクションにプロキシ アドレスとプロキシ ポートを追加します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Connector Updater サービスも確実にプロキシをバイパスするようにするには、C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config にも同様の変更を加えます。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

既定の .config ファイルに戻す必要がある場合に備えて、必ず元のファイルのコピーを作成してください。

構成ファイルを変更したら、Intune コネクタ サービスを再起動する必要があります。 

1. **services.msc** を開きます。
2. **Intune ODJConnector サービス**を検索して選択します。
3. **[再起動]** を選択します。

![サービスの再起動のスクリーンショット](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>次の手順

[デバイスの管理](../remote-actions/device-management.md)
