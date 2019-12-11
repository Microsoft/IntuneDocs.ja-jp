---
title: Microsoft Edge の Intune セキュリティ基準設定
titleSuffix: Microsoft Intune
description: Microsoft Edge ブラウザーを管理するために Intune でサポートされるセキュリティベースライン設定
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c75029c60609b0383e2f647e5b94144d4186248c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "73754865"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Intune の Microsoft Edge 基準設定

Microsoft Intune でサポートされている Microsoft Edge web ブラウザーのベースライン設定を表示します。 Microsoft edge のベースラインの既定値は、Microsoft Edge ブラウザーで推奨される構成を表し、他のセキュリティ基準のベースラインの既定値とは一致しない場合があります。

> [!NOTE]
> Microsoft Edge のベースラインは、パブリックプレビュー段階にあります。 

## <a name="microsoft-edge"></a>Microsoft Edge

- **サイトの Microsoft Defender SmartScreen プロンプトをバイパスできないようにする**  
  **既定値**: 有効  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  このポリシー設定を使用すると、悪意のある可能性のある web サイトに関する Microsoft Defender SmartScreen の警告をユーザーが上書きできるかどうかを決定できます。 
  - この設定を有効にした場合、ユーザーは Microsoft Defender SmartScreen 警告を無視できず、サイトへの続行がブロックされます。 
  - この設定を無効にした場合、または構成しなかった場合、ユーザーは Microsoft Defender SmartScreen 警告を無視してサイトに進むことができます。

- **有効な最小 SSL バージョン**  
  **既定値**: 有効  

  SSL のサポートされている最小バージョンを設定します。 このポリシーを [未構成] に設定した場合、Microsoft Edge では既定の最小バージョンの*TLS 1.0*が使用*さ*れます。 [*有効*] に設定すると、次の値から最小バージョンを選択できます。

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **有効な最小 SSL バージョン**  
    **既定値**: TLS 1.2

- **ダウンロードに関する Microsoft Defender SmartScreen の警告をバイパスできないようにする**  
  **既定値**: 有効  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  このポリシーを使用して、未確認のダウンロードに関する Microsoft Defender SmartScreen の警告をユーザーが上書きできるかどうかを指定できます。
  - このポリシーを有効にすると、組織内のユーザーは Microsoft Defender SmartScreen 警告を無視できなくなり、未確認のダウンロードを完了できなくなります。
  - このポリシーを無効にした場合、または構成しなかった場合、ユーザーは Microsoft Defender SmartScreen 警告を無視して、未確認のダウンロードを完了できます。

- **[SSL の警告] ページからユーザーが続行できるようにする**  
  **既定値**: 無効  
  Microsoft Edge CSP: [Browser/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge では、ユーザーが SSL エラーが発生したサイトにアクセスするときに警告ページが表示されます。 このポリシーを [*有効*] または [*未構成*] に設定した場合、ユーザーはこれらの警告ページをクリックすることができます。 このポリシーが*無効になっ*ていると、ユーザーは警告ページをクリックしてもブロックされます。 

- **既定の Adobe Flash 設定**  
  **既定値**: 有効  
  Microsoft Edge CSP: [browser/AllowFlash](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflash)および[browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  ' PluginsAllowedForUrls ' または ' PluginsBlockedForUrls ' でカバーされていない web サイトで Adobe Flash プラグインを自動的に実行できるかどうかを指定します。 

  - すべてのサイトで Adobe Flash をブロックするには、[BlockPlugins] を選択します
  - [ClickToPlay] を選択すると、Adobe Flash を実行できますが、ユーザーがプレースホルダーをクリックして開始する必要があります。
  
   どのような場合でも、' PluginsAllowedForUrls ' および ' PluginsBlockedForUrls ' ポリシーは ' DefaultPluginsSetting ' よりも優先されます。 自動再生は、' PluginsAllowedForUrls ' ポリシーに明示的に一覧表示されているドメインに対してのみ許可されます。 
   すべてのサイトで自動再生を有効にする場合は、この一覧に http://* と https://* を追加することを検討してください。 
   
   - このポリシーを [*未構成*] に設定した場合、ユーザーはこの設定を手動で変更できます。 * 2 = Adobe Flash プラグインをブロックする * 3 = クリックすると、前の ' 1 ' オプションが [許可-すべて] に設定されますが、この機能は "PluginsAllowedForUrls" ポリシーによってのみ処理されるようになりました。 ' 1 ' を使用する既存のポリシーは、クリックツープレイモードで動作します。  
 
  - **既定の Adobe Flash 設定**  
    **既定**: Adobe Flash プラグインをブロックします。

- **すべてのサイトでサイトの分離を有効にする**  
  **既定値**: 有効  

  "SitePerProcess" ポリシーを使用すると、すべてのサイトを分離する既定の動作をユーザーがオプトアウトするのを防ぐことができます。 IsolateOrigins ポリシーを使用して、さらに細かいオリジンを分離することもできます。

  - このポリシーが [有効] に設定されている場合、ユーザーは、各サイトが独自のプロセスで実行される既定の動作を*無効*にすることはできません。 
  - *無効に*した場合、または*構成しなかっ*た場合、ユーザーはサイトの分離を無効にすることができます。 (たとえば、edge://flags で "site 分離を無効にする" というエントリを使用します)。ポリシーを無効にした場合、またはポリシーを構成しなかった場合は、サイトの分離は無効になりません。

- **サポートされている認証方式**  
  **既定値**: 有効  

  サポートされている HTTP 認証スキームを指定します。 ポリシーを構成するには、次の値を使用します。 ' basic '、' digest '、' ntlm '、および ' negotiate '。 複数の値はコンマで区切ります。 このポリシーを構成しない場合は、4つのスキームがすべて使用されます。
 
  - **サポートされている認証方式**  
    次のオプションから選択します。 
    - 基本
    - Digest
    - NTLM *(既定で選択されています)*
    - Negotiate *(既定で選択されて*います)

- **パスワードマネージャーにパスワードを保存できるようにする**  
  **既定値**: 無効  
  Microsoft Edge CSP: [Browser/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Microsoft Edge でユーザーのパスワードを保存できるようにします。 
  - このポリシーを有効にすると、ユーザーは Microsoft Edge にパスワードを保存できます。 次回サイトにアクセスしたときに、Microsoft Edge によって自動的にパスワードが入力されます。 
  - このポリシーを無効にした場合、ユーザーは新しいパスワードを保存できませんが、以前に保存されたパスワードを使用できます。 
  
  このポリシーを [*有効*] または [*無効*] に設定すると、ユーザーは Microsoft Edge でこのポリシーを変更または上書きできなくなります。 
  
  このオプションを [*未構成*] に設定すると、ユーザーはこの機能を無効にするだけでなく、パスワードを保存することもできます。

- **インストールできない拡張機能を制御する**  
  **既定値**: 有効  

  ユーザーが Microsoft Edge にインストールできない特定の拡張機能を一覧表示します。 このポリシーを展開すると、以前にインストールされた拡張機能がすべて無効になり、ユーザーはこれらの拡張機能を有効にできなくなります。 ブロックされている拡張機能の一覧から項目を削除すると、その拡張機能は、以前にインストールされていたすべての場所で自動的に再度有効になります。
  
  許可一覧に明示的に記載されていないすべての拡張機能をブロックするには、 **\*** を使用します。 このポリシーが [未構成] に設定され*て*いる場合、ユーザーは Microsoft Edge に拡張機能をインストールできます。 
  
  値の例: extension_id1 extension_id2。  
  <br>
  - **ユーザーがインストールできないようにする拡張機能 Id (または * すべて)**  
    **[追加]** を選択し、追加の拡張機能を指定します。 **\*** は既定で選択されています。

- **Microsoft Defender SmartScreen を構成する**  
  **既定値**: 有効  
  Microsoft Edge CSP: [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  このポリシー設定を使用すると、Microsoft Defender SmartScreen を有効にするかどうかを構成できます。 Microsoft Defender SmartScreen では、ユーザーをフィッシング詐欺や悪意のあるソフトウェアから保護するために、警告メッセージが表示されます。 
  
  - 既定では、Microsoft Defender SmartScreen が有効になっています。 この設定を有効にした場合、Microsoft Defender SmartScreen が有効になり、ユーザーは無効にできなくなります。
  - この設定を無効にした場合、Microsoft Defender SmartScreen は無効になり、ユーザーは有効にできなくなります。 
  - [未構成] に設定され*て*いる場合、ユーザーは Microsoft Defender SmartScreen を使用するかどうかを選択できます。 
  
  このポリシーは、Microsoft Active Director ドメインに参加している Windows インスタンス、またはデバイス管理に登録されている Windows 10 Pro または Enterprise インスタンスでのみ使用できます。

- **ユーザーレベルのネイティブメッセージングホストを許可する (管理者権限なしでインストールされます)**  
  **既定値**: 無効  

  ネイティブメッセージングホストのユーザーレベルのインストールを有効にします。 
  - このポリシーを無効にすると、Microsoft Edge ではシステムレベルにインストールされているネイティブのメッセージングホストのみが使用されます。 既定では、このポリシーを構成しない場合、Microsoft Edge ではユーザーレベルのネイティブメッセージングホストの使用が許可されます。

## <a name="next-steps"></a>次の手順

[Intune でのセキュリティ基準の使用](security-baselines.md)
