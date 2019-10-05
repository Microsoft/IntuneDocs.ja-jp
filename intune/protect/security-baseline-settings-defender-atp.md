---
title: Microsoft Defender Advanced Threat Protection 向けの Intune のセキュリティのベースラインの設定
titleSuffix: Microsoft Intune
description: Microsoft Defender Advanced Threat Protection を管理するために、Intune でサポートされるセキュリティ ベースラインの設定
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eee3d4187dd513cd3945e86aff478fe96b341660
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732959"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Intune 向けの Microsoft Defender Advanced Threat Protection ベースライン設定

Microsoft Intune でサポートされている Microsoft Defender Advanced Threat Protection (旧称 Windows Defender Advanced Threat Protection) ベースライン設定を表示します。 Advanced Threat Protection (ATP) ベースラインの既定値は、ATP の推奨される構成を表しており、他のセキュリティ ベースラインのベースラインの既定値と一致しない場合があります。  

ご使用の環境が [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) を使用するための前提条件を満たしている場合は、Microsoft Defender Advanced Threat Protection ベースラインを使用できます。 

このベースラインは物理デバイス用に最適化されており、現在は仮想マシン (Vm) または VDI エンドポイントでの使用は推奨されていません。 特定のベースライン設定が、仮想化された環境でのリモート対話型セッションに影響を与える可能性があります。 詳細については、Windows ドキュメントの「[Increase compliance to the Microsoft Defender ATP security baseline (Microsoft Defender ATP のセキュリティ ベースラインに対するコンプライアンスの強化)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline)」をご覧ください。


> [!NOTE]  
> ATP ベースライン設定は、**プレビュー**段階にあります。 プレビュー段階の間は、使用可能な設定の一覧、およびこのコンテンツでそれらの設定が示される順序は、ポータル内で提供されるものと異なる可能性があります。  
>
> ベースライン設定のプレビュー段階が終了すると、このコンテンツは更新され、Intune でサポートされる最新のセキュリティ ベースライン設定を反映するようになります。

## <a name="application-guard"></a>Application Guard  
詳細については、Windows のドキュメントの「[WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp)」を参照してください。  

Microsoft Edge を使用しているとき、ご利用の環境は Windows Defender Application Guard によって、組織で信頼されていないサイトから保護されます。 分離ネットワーク境界のリストに含まれないサイトにユーザーがアクセスすると、そのサイトは Hyper-V 仮想ブラウズ セッションで開きます。 信頼済みサイトは、ネットワーク境界によって定義されます。  

- **Application Guard** - *Settings/AllowWindowsDefenderApplicationGuard*  
  *[はい]* を選択すると、この機能がオンになり、信頼されていないサイトが Hyper-V 仮想ブラウズ コンテナーで開かれます。 *[未構成]* に設定すると、サイト (信頼済みおよび信頼されていない) はいずれも仮想化されたコンテナー内ではなくデバイス上で開かれます。  

  **既定値**: はい
 
  - **エンタープライズ サイトの外部コンテンツ** - *ettings/BlockNonEnterpriseContent*  
    *[はい]* を選択すると、未承認の Web サイトからのコンテンツの読み込みがブロックされます。 *[未構成]* に設定すると、デバイス上で非エンタープライズ サイトを開けるようになります。 
 
    **既定値**: はい

  - **クリップボードの動作** - *Settings/ClipboardSettings*  
    ローカル PC と Application Guard 仮想ブラウザー間で許可するコピー/貼り付け操作を選択します。  次のオプションがあります。
    - *未構成*  
    - *双方向をブロック* - PC と仮想ブラウザーの間でデータを転送できません。  
    - *ホストからコンテナーへの方向をブロック* - PC から仮想ブラウザーにデータを転送できません。
    - *コンテナーからホストへの方向をブロック* - 仮想ブラウザーからホスト PC にデータを転送できません。
    - *ブロックなし* - コンテンツに対するブロックは存在しません。  

    **既定値**: 双方向をブロック  

- **Windows ネットワーク分離ポリシー – エンタープライズ ネットワーク ドメイン名**  
  詳細については、Windows のドキュメントの「[Policy CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation)」 (ポリシー CSP - NetworkIsolation) を参照してください。
  
  Application Guard がエンタープライズ サイトとして処理するクラウド内でホストされているドメイン、IP アドレス範囲、およびネットワーク境界として、エンタープライズ リソースのリストを指定します。  

  **既定値**: securitycenter.windows.com

## <a name="application-reputation"></a>アプリケーションの評判  

詳細については、Windows ドキュメントの「[Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen)」 (ポリシー CSP - SmartScreen) を参照してください。

- **Block execution of unverified files (確認されていないファイルの実行をブロックする)**  
    確認されていないファイルをユーザーが実行しないようにします。 *[未構成]* に設定すると、従業員は SmartScreen の警告を無視して悪意のあるファイルを実行することができます。 *[はい]* に設定すると、従業員は SmartScreen の警告を無視して悪意のあるファイルを実行することはできません。  
  
    **既定値**: はい

- **Require SmartScreen for apps and files (アプリとファイルに SmartScreen を要求する)**  
  *[はい]* に設定すると、Windows 用の SmartScreen が有効になります。  

  **既定値**: はい

## <a name="attack-surface-reduction"></a>攻撃の回避  

- **Office apps launch child process type (Office アプリの子プロセスの起動の種類)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *[ブロック]* に設定すると、Office アプリで子プロセスを作成することはできません。 Office アプリには、Word、Excel、PowerPoint、OneNote、および Access などがあります。 子プロセスを作成するのは、一般的なマルウェアの動作です。特に、Office アプリを使用して悪意のある実行可能ファイルの起動またはダウンロードを試みるマクロベースの攻撃で作成されます。  

  **既定値**: ブロック

- **Script downloaded payload execution type (スクリプトでダウンロードされたペイロードの実行タイプ)**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – ダウンロードするか、インストールを試みるアプリケーションについて、望ましくない可能性の検出レベルを指定します。  

  **既定値**: ブロック 

- **Prevent credential stealing type (資格情報盗難防止タイプ)**  
  *[有効]* に設定すると、[Credential Guard によりドメインの派生資格情報が保護されます](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)。 Windows Defender Credential Guard は、特権を持つシステム ソフトウェアだけがシークレットにアクセスできるように、仮想化ベースのセキュリティを使用してシークレットを分離します。 これらのシークレットへの不正アクセスは、Pass-the-Hash や Pass-The-Ticket などの、資格情報を盗む攻撃につながる可能性があります。 Windows Defender Credential Guard は、NTLM パスワード ハッシュ、Kerberos の Ticket Granting Ticket、およびアプリケーションによってドメイン資格情報として格納された資格情報を保護することで、これらの攻撃を防ぎます。  

  **既定値**: 有効にする

- **Email content execution type (電子メール コンテンツ実行タイプ)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *[ブロック]* に設定すると、このルールにより、次の種類のファイルは Microsoft Outlook または Web メール (Gmail.com や Outlook.com など) に表示された電子メールから実行または起動されるのをブロックされます。  

  - 実行可能ファイル (.exe、.dll、.scr など)  
  - スクリプト ファイル (PowerShell .ps、VisualBasic .vbs、JavaScript .js ファイルなど)  
  - スクリプト アーカイブ ファイル  

  **既定値**: ブロック

- **子プロセスでの Adobe Reader の起動**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – このルールを "*有効*" にすると、Adobe Reader での子プロセスの作成がブロックされます。 マルウェアは、ソーシャル エンジニアリングまたは悪用によって、追加のペイロードをダウンロードして起動し、Adobe Reader から抜け出すことができます。  

  **既定値**: 有効にする

- **Script obfuscated macro code type (スクリプト難読化マクロ コード タイプ)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - マルウェアや他の脅威によって、一部のスクリプト ファイル内で悪意のあるコードの難読化または隠ぺいが試みられる可能性があります。 このルールは、難読化されているらしいスクリプトが実行するのを防ぎます。  
    
  **既定値**: ブロック

- **Untrusted USB process type (信頼されていない USB 処理タイプ)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *[ブロック]* に設定すると、USB リムーバブル ドライブおよび SD カードからの署名なしまたは信頼されていない実行可能ファイルは実行できません。

  実行可能ファイルには次のようなものがあります。
  - 実行可能ファイル (.exe、.dll、.scr など)
  - スクリプト ファイル (PowerShell .ps、VisualBasic .vbs、JavaScript .js ファイルなど)  

  **既定値**: ブロック

- **Office apps other process injection type (Office アプリによる他のプロセスへの挿入タイプ)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - *[ブロック]* に設定すると、Word、Excel、PowerPoint、OneNote などの Office アプリから他のプロセスにコードを挿入することができません。 コードの挿入は、通常、マルウェアがウイルス対策スキャン エンジンからアクティビティを隠ぺいする試みの中で、悪意のあるコードを実行するために使用されます。  

  **既定値**: ブロック

- **Office macro code allow Win32 imports type (Office のマクロ コードによる Win32 のインポートの許可タイプ)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) - *[ブロック]* に設定すると、このルールによって、Win32 DLL をインポートできるマクロ コードが含まれた Office ファイルをブロックすることが試みられます。 Office ファイルには、Word、Excel、PowerPoint、OneNote などがあります。 マルウェアは、Office ファイルのマクロ コードを使用して、Win32 DLL をインポートして読み込んだ後、それを使用して API 呼び出しを行い、システム全体にさらに感染させる可能性があります。  

  **既定値**: ブロック

- **子プロセスでの Office 通信アプリの起動**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *[有効にする]* に設定すると、このルールによって Outlook による子プロセスの作成が防止されます。 このルールでは、子プロセスの作成をブロックすることで、ソーシャル エンジニアリング攻撃から保護すると共に、エクスプロイトコードが Outlook の脆弱性を悪用するのを防ぐことができます。  

  **既定値**: 有効にする

- **Office apps executable content creation or launch type (Office アプリの実行可能コンテンツの作成または起動タイプ)**  
  [攻撃面の減少ルール](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) – *ブロック* に設定すると、Office アプリで実行可能なコンテンツを作成できなくなります。 Office アプリには、Word、Excel、PowerPoint、OneNote、および Access などがあります。  

  このルールの対象は、実行可能ファイルを作成または起動する不審な悪意のあるアドオンとスクリプト (拡張機能) で使用される一般的な動作です。 これは、マルウェアの一般的な手法です。 拡張機能は、Office アプリによって使用されるのをブロックされます。 通常、これらの拡張機能では、特定のタスクを自動化したり、ユーザー作成のアドオン機能を提供したりするスクリプトを実行するために、Windows Scripting Host (.wsh ファイル) が使用されます。

  **既定値**: ブロック

## <a name="bitlocker"></a>BitLocker  

詳細については、Windows のドキュメントの「[BitLocker グループ ポリシー設定](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)」を参照してください。  

- **デバイスの暗号化**  
  BitLocker デバイスの暗号化を有効にするには、 *[はい]* を選択します。 デバイスのハードウェアおよび Windows のバージョンによって異なりますが、デバイス ユーザーは、デバイス上にサードパーティの暗号化が存在しないことを確認するよう求められる場合があります。 サードパーティの暗号化がアクティブになっているときに Windows の暗号化をオンにすると、デバイスが不安定になります。  

   **既定値**: はい

- **Bit locker removable drive policy (Bitlocker のリムーバブル ドライブのポリシー)**  
  このポリシーの値では、BitLocker がリムーバブル ドライブの暗号化に使用する暗号化強度が決定されます。 企業では、セキュリティを強化するために、暗号化のレベルを制御します (AES-256 は AES-128 よりも強力です)。 *[はい]* を選択してこの設定を有効にした場合は、固定データ ドライブやオペレーティング システム ドライブ、リムーバブル データ ドライブのそれぞれに、暗号化アルゴリズムとキーの暗号化強度を構成できます。 固定ドライブやオペレーティング システム ドライブには、XTS-AES アルゴリズムを使用することをお勧めします。 リムーバブル ドライブには、Windows 10 バージョン 1511 以降を実行していないその他のデバイスでドライブを使用する場合は、AES-CBC 128 ビットまたは AES-CBC 256 ビットを使用する必要があります。 ドライブが既に暗号化されているか、暗号化が進行中の場合は、暗号化の種類を変更しても影響はありません。 このような場合、このポリシー設定は無視されます。 

  Bitlocker リムーバブル ドライブ ポリシーの場合は、次の設定を構成します。

  - **Require encryption for write access (書き込みアクセス用に暗号化が必要)**  
    **既定値**: はい

  - **[暗号化方法]**  
    **既定値**: AES 128 ビット CBC

- **Bit locker fixed drive policy (Bitlocker の固定ドライブのポリシー)**  
  このポリシーの値では、BitLocker が固定ドライブの暗号化に使用する暗号化強度が決定されます。 企業では、セキュリティを強化するために、暗号化のレベルを制御できます (AES-256 は AES-128 よりも強力です)。 この設定を有効にした場合は、固定データ ドライブやオペレーティング システム ドライブ、リムーバブル データ ドライブのそれぞれに、暗号化アルゴリズムとキーの暗号化強度を構成できます。 固定ドライブやオペレーティング システム ドライブには、XTS-AES アルゴリズムを使用することをお勧めします。 リムーバブル ドライブには、Windows 10 バージョン 1511 以降を実行していないその他のデバイスでドライブを使用する場合は、AES-CBC 128 ビットまたは AES-CBC 256 ビットを使用する必要があります。 ドライブが既に暗号化されているか、暗号化が進行中の場合は、暗号化の種類を変更しても影響はありません。 このような場合、このポリシー設定は無視されます。

  Bitlocker 固定ドライブ ポリシーの場合は、次の設定を構成します。

  - **Require encryption for write access (書き込みアクセス用に暗号化が必要)**  
    **既定値**: はい

  - **[暗号化方法]**  
    **既定値**: AES 128bit XTS

- **Bit locker system drive policy (Bitlocker のシステム ドライブのポリシー)**  
  このポリシーの値では、BitLocker がシステム ドライブの暗号化に使用する暗号化強度が決定されます。 企業では、セキュリティを強化するために、暗号化のレベルを制御したい場合があります (AES-256 は AES-128 よりも強力です)。 この設定を有効にした場合は、固定データ ドライブやオペレーティング システム ドライブ、リムーバブル データ ドライブのそれぞれに、暗号化アルゴリズムとキーの暗号化強度を構成できます。 固定ドライブやオペレーティング システム ドライブには、XTS-AES アルゴリズムを使用することをお勧めします。 リムーバブル ドライブには、Windows 10 バージョン 1511 以降を実行していないその他のデバイスでドライブを使用する場合は、AES-CBC 128 ビットまたは AES-CBC 256 ビットを使用する必要があります。 ドライブが既に暗号化されているか、暗号化が進行中の場合は、暗号化の種類を変更しても影響はありません。 このような場合、このポリシー設定は無視されます。  

  Bitlocker システム ドライブ ポリシーの場合は、次の設定を構成します。  

  - **[暗号化方法]**  
    **既定値**: AES 128bit XTS

## <a name="device-control"></a>デバイスの制御  

- **フル スキャン中に、リムーバブル ドライブをスキャンする**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) - *[はい]* に設定すると、Defender ではフルスキャン中に、フラッシュ ドライブなどのリムーバブル ドライブ内で悪意のある望ましくないソフトウェアがスキャンされます。 USB デバイス上のすべてのファイルが Defender Antivirus によってスキャンされてから、USB デバイス上のファイルは実行できるようになります。

  このリスト内の関連設定: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **既定値**: はい

- **Kernel DMA Protection と互換性のない外部デバイスの列挙**  
   「[Policy CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)」 (ポリシー CSP - DmaGuard) の「*DmaGuard/DeviceEnumerationPolicy*」を参照してください。

  このポリシーでは、外部 DMA 対応デバイスに対して追加のセキュリティが提供されます。 これにより、DMA デバイス メモリの分離およびサンドボックス化と互換性のない外部 DMA 対応デバイスの列挙をより詳細に制御できます。

  このポリシーが有効になるのは、Kernel DMA Protection がシステム ファームウェアによってサポートされていて、それによって有効にされた場合のみです。 Kernel DMA Protection は、ポリシーによってもデバイスのユーザーによっても制御できないプラットフォーム機能です。 製造時には、それがシステムによってサポートされている必要があります。 

  システムで Kernel DMA Protection がサポートされているかどうかを確認するには、システム上で MSINFO32.exe を実行し、[概要] ページの *[Kernel DMA Protection]* フィールドを確認してください。  

  次のオプションがあります。 
  - *デバイスの既定値* - サインインを行うか、または画面ロックを解除すると、互換性のあるドライバーを再マッピングする DMA を備えたデバイスをいつでも列挙することができます。 互換性のないドライバーを再マッピングする DMA を備えたデバイスは、ユーザーが画面ロックを解除した後でのみ列挙されます。
  - *すべて許可* - 外部 DMA 対応 PCIe デバイスはすべて、いつでも列挙できます。
  - *すべてブロック* - 互換性のあるドライバーを再マップする DMA を備えたデバイスは、いつでも列挙することができます。 互換性のないドライバーを再マップする DMA を備えたデバイスが、DMA の起動および実行を許可されることはありません。

  **既定値**: デバイスの既定値

- **Hardware device installation by device identifiers (デバイス識別子を使用してハードウェア デバイスをインストールする)**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) - このポリシーでは、Windows によるインストールが禁止されているデバイス用のプラグ アンド プレイ ハードウェア ID および互換性 ID のリストを指定します。 このポリシー設定は、デバイスのインストールを許可する他のポリシー設定よりも優先されます。 このポリシー設定を有効にした場合 ( *[ハードウェア デバイスのインストールをブロックする]* に設定)、Windows ではプラグ アンド プレイ ハードウェア ID または互換性 ID が作成した一覧に含まれているデバイスはインストールできません。 リモート デスクトップ サーバーでこのポリシーを有効にした場合、このポリシー設定は、リモート デスクトップ クライアントからリモート デスクトップ サーバーへの指定されたデバイスのリダイレクトに影響します。 このポリシー設定を無効にした場合、または構成しなかった場合 ( *[ハードウェア デバイスのインストールを許可する]* に設定) は、他のポリシー設定に従って、デバイスのインストールや更新が許可されるかどうかが決まります。  

  **既定値**: Block hardware device installation (ハードウェア デバイスのインストールをブロックする)  

  *[ハードウェア デバイスのインストールをブロックする]* を選択すると、次の設定を使用できます。
  - **Remove matching hardware devices (一致するハードウェア デバイスを削除する)**  
    この設定は *[Hardware device installation by device identifiers]\(デバイス識別子でハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。  

    **既定値**: *既定の構成はありません*

  - **Hardware device identifiers that are blocked (ブロックされているハードウェア デバイス識別子)**  
    この設定は *[Hardware device installation by device identifiers]\(デバイス識別子でハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。 この設定を構成するには、オプションを展開し、 **[+ 追加]** を選択して、ブロックするハードウェア デバイスの識別子を指定します。  

    **既定値**: *デバイスはブロックされません*  

- **Block direct memory access (ダイレクト メモリ アクセスをブロックする)**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) - このポリシー設定を使用すると、ユーザーが Windows にログインするまで、デバイス上のホット プラグ可能なすべての PCI ダウンストリーム ポートへのダイレクト メモリ アクセス (DMA) をブロックできます。 ユーザーがログインすると、Windows はホット プラグ PCI ポートに接続されている PCI デバイスを列挙します。 ユーザーがコンピューターをロックするたびに、ユーザーが再ログインするまで、子デバイスが接続されていないホット プラグ PCI ポートで DMA がブロックされます。 コンピューターのロックが解除された際に既に列挙されていたデバイスは、取り外されるまで機能を維持します。 

  このポリシー設定は、BitLocker またはデバイスの暗号化が有効な場合にのみ適用されます。  

  **既定値**: はい


- **Hardware device installation by setup classes (セットアップ クラスを使用してハードウェア デバイスをインストールする)**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) - このポリシーでは、インストールを禁止するデバイス ドライバーのデバイス セットアップ クラス GUID (グローバル一意識別子) の一覧を指定できます。 このポリシー設定は、デバイスのインストールを許可する他のポリシー設定よりも優先されます。 このポリシー設定を有効にした場合 ( *[ハードウェア デバイスのインストールをブロックする]* に設定)、デバイス セットアップ クラス GUID が作成した一覧に含まれているデバイス ドライバーはインストールすることも更新することもできません。 リモート デスクトップ サーバーでこのポリシー設定を有効にした場合、このポリシー設定は、リモート デスクトップ クライアントからリモート デスクトップ サーバーへの指定されたデバイスのリダイレクトに影響します。 このポリシー設定を無効にした場合、または構成しなかった場合 ( *[ハードウェア デバイスのインストールを許可する]* に設定)、他のポリシー設定に従って、デバイスのインストールや更新が許可されるかどうかが決まります。  

  **既定値**: Block hardware device installation (ハードウェア デバイスのインストールをブロックする)

  *[ハードウェア デバイスのインストールをブロックする]* を選択すると、次の設定を使用できます。  

  - **Remove matching hardware devices (一致するハードウェア デバイスを削除する)**  
    この設定は *[Hardware device installation by setup classes]\(設定クラスでハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。  
 
    **既定値**: *既定の構成はありません*  

  - **Hardware device identifiers that are blocked (ブロックされているハードウェア デバイス識別子)**  
    この設定は [Hardware device installation by setup classes]\(設定クラスでハードウェア デバイスをインストールする\) が [Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\) に設定されているときのみ使用できます。 この設定を構成するには、オプションを展開し、 **[+ 追加]** を選択して、ブロックするハードウェア デバイスの識別子を指定します。  
 
    **既定値**: *デバイスはブロックされません*

## <a name="endpoint-detection-and-response"></a>エンドポイントの検出と応答  
詳細については、Windows のドキュメントの「[WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp)」を参照してください。  

- **テレメトリの報告頻度を早める** - *Configuration/TelemetryReportingFrequency*  

  Microsoft Defender Advanced Threat Protection テレメトリの報告頻度を早めます。  

  **既定値**: はい

- **すべてのファイルのサンプル共有** - *Configuration/SampleSharing*  

  Microsoft Defender Advanced Threat Protection サンプル共有の構成パラメーターを返すか設定します。  

  **既定値**: はい

## <a name="exploit-protection"></a>悪用に対する保護  

- **[Exploit Protection XML]**  
  詳細については、Windows ドキュメントの「[Import, export, and deploy exploit protection configurations](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml)」 (悪用保護構成のインポート、エクスポート、および展開) を参照してください。  

  IT 管理者が、組織内のすべてのデバイスに対して、目的のシステムとアプリケーションの軽減策オプションを表す構成をプッシュできるようにします。 この構成は XML で表されます。 

  Exploit Protection を適用すると、拡散と感染のために悪用するマルウェアからデバイスを保護できます。 Windows セキュリティ アプリまたは PowerShell を使用して、一連の軽減策 (構成と呼ばれます) を作成します。 次に、この構成を XML ファイルとしてエクスポートし、ネットワーク上の複数のマシンと共有して、すべてのマシンに同じ軽減策設定が適用されるようにすることができます。
 
  既存の EMET 構成 XML ファイルを変換して Exploit Protection 構成 XML にインポートすることもできます。

- **悪用に対する保護のオーバーライドをブロックする**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – *[はい]* に設定すると、Windows Defender Security Center 内の悪用に対する保護設定に対してユーザーは変更を加えることができなくなります。 この設定を無効にした場合、または構成しなかった場合、ローカルユーザーは悪用に対する保護設定の領域で変更を加えることができます。  
  **既定値**: はい  

- **フォルダー アクセスの制御**  
  「[Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications)」および「[Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders)」を参照してください。 
  
   ファイルおよびフォルダーを、悪意のあるアプリによる未承認の変更から保護します。

  **既定値**: 監査モード

## <a name="web--network-protection"></a>Web とネットワークの保護  

- **Network protection type (ネットワーク保護タイプ)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)  - このポリシーでは、Windows Defender Exploit Guard 内でネットワーク保護をオンまたはオフにすることができます。 ネットワーク保護は Windows Defender Exploit Guard の機能であり、任意のアプリを使用する従業員がインターネット上のフィッシング詐欺、悪用ホスティング サイト、悪意のあるコンテンツにアクセスするのを防ぎます。 これには、サード パーティ製のブラウザーが危険なサイトに接続するのを防ぐことが含まれます。  

  *[有効]* または *[監査モード]* のいずれかに設定すると、ユーザーはネットワーク保護を無効にできなくなります。Windows Defender セキュリティ センターを使用すれば、接続の試行に関する情報を表示できます。  
 
  - *[有効]* に設定すると、ユーザーおよびアプリが危険なドメインに接続するのをブロックできます。  
  - *[監査モード]* に設定した場合、ユーザーおよびアプリが危険なドメインに接続するのを防ぐことはできません。  

  *[ユーザー定義]* に設定すると、ユーザーおよびアプリが危険なドメインに接続するのをブロックすることはできず、Windows Defender セキュリティ センターで接続に関する情報は提供されません。  

  **既定値**: 監査モード

- **Require SmartScreen for Microsoft Edge (Microsoft Edge で SmartScreen が必要)**  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) - Microsoft Edge では、(有効に設定された) Windows Defender SmartScreen を使用して、フィッシング詐欺にあう可能性や悪意のあるソフトウェアから既定でユーザーを保護しています。 既定では、このポリシーは有効になっています ( *[はい]* に設定されています)。有効になっている場合、ユーザーは Windows Defender SmartScreen をオフすることができません。  デバイス用の有効なポリシーが [未構成] に相当する場合、ユーザーは Windows Defender SmartScreen を無効にして、デバイスを保護されていない状態にすることができます。  

  **既定値**: はい
  
- **Block malicious site access (悪意のあるサイトへのアクセスをブロックする)**  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) - 既定では、Microsoft Edge を使用する場合、ユーザーは悪意のある可能性があるサイトに関する Windows Defender SmartScreen の警告を無視してそのサイトへのアクセスを続行できます。 このポリシーを有効にした場合 ( *[はい]* に設定)、Microsoft Edge を使用しているユーザーは警告を無視してサイトへのアクセスを続行することはできません。  

  **既定値**: はい

- **Block unverified file download (確認されていないファイルのダウンロードをブロックする)**  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) - Microsoft Edge では、悪意のある可能性があるファイルに関する Windows Defender SmartScreen の警告を既定で無視して、確認されていないファイルのダウンロードを続行することができます。 このポリシーを有効にすると ( *[はい]* に設定)、ユーザーは警告を無視して確認されていないファイルをダウンロードすることはできません。  

  **既定値**: はい

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Windows Defender ウイルス対策    [このセクションの設定レビューは保留中]

詳細については、Windows ドキュメントの「[Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)」(ポリシー CSP - Defender) を参照してください。

- **Microsoft Web ブラウザーに読み込まれたスクリプトをスキャンする**:  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – *[はい]* に設定すると、Windows Defender のスクリプト スキャン機能が使用できるようになります。  

  **既定値**: はい

- **受信メール メッセージをスキャンする**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – *[はい]* に設定すると、Windows Defender で電子メールをスキャンできるようになります。  

  **既定値**: はい

- **Defender sample submission consent type (Defender のサンプル送信の同意の種類)**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) - Windows Defender でデータを送信するためのユーザーの同意レベルを確認します。 必要な同意が既に与えられている場合、Windows Defender からそれらが送信されます。 それ以外の場合 (かつユーザーが "確認しない" を指定した場合)、( *[クラウドによる保護]* が *[はい]* に設定されている場合は) データを送信する前にユーザーの同意を求める UI が起動します。  

  **既定値**: 安全なサンプルを自動的に送信します

- **ネットワーク検査システム (NIS)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) -ネットワーク検査システム (NIS) 内のシグネチャによって検出された悪意のあるトラフィックをブロックします。  
 
  **既定値**: はい

- **Signature update interval (in hours) (署名更新間隔 (時単位))**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – デバイスが新しい Defender シグネチャ更新をチェックする頻度を時間単位で指定します。  
 
  **既定値**: 4

- **スケジュールされたスキャン用に低い CPU 優先度を構成**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – *[はい]* に設定すると、スキャンに対する CPU 優先度は低く設定されます。 *[未構成]* の場合、スケジュールされたスキャンの CPU 優先度に変更は加えられません。  

    **既定値**: はい

- **アクセス保護に対する Defender のブロック**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – *[はい]* に設定すると、Windows Defender の常時保護が有効にされます。  

  **既定値**: はい

- **実行するシステム スキャンの種類**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) - Defender スキャンの種類。  

  **既定値**: クイック スキャン

- **すべてのダウンロードをスキャンする**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) - *[はい]* に設定すると、すべてのダウンロードされたファイルと添付ファイルが Defender によってスキャンされます。  

  **既定値**: はい

- **検疫済みマルウェアを削除するまでの日数**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) - 検疫アイテムを自動的に削除する前に、システム上で保持する日数を指定します。 0 に設定すると、検疫内のアイテムが自動的に削除されることはありません。  

  **既定値**: 0

- **スケジュールされたスキャンの開始時間**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – Defender がデバイスをスキャンする時刻をスケジュールします。 
  
  このリスト内の関連オプション: *Defender/ScheduleScanDay*   

  **既定値**: 午前 2 時

- **Cloud-delivered protection (クラウドによる保護)**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – *[はい]* に設定すると、検出された問題に関する情報が Windows Defender から Microsoft に送信されます。 Microsoft は、その情報を分析し、報告者や他の顧客に影響する問題について詳細に把握して、強化されたソリューションを提供します。

  このポリシーを *[はい]* に設定すると、 *[Defender のサンプル送信の同意の種類]* を使用して、ユーザーに自分のデバイスからの情報の送信を制御させることができます。  

  **既定値**: はい

- **Defender potentially unwanted app action (Defender の望ましくないアプリに対するアクション)**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – Windows Defender ウイルス対策では、*望ましくない可能性のあるアプリケーション*を識別し、それがご利用のネットワーク内のエンドポイント上にダウンロードおよびインストールされるのをブロックすることができます。 
 
  - *[ブロック]* に設定すると、Windows Defender によって PUA がブロックされ、他の脅威と一緒に履歴内に一覧表示されます。
  - *[監査]* に設定すると、Windows Defender によって PUA は検出されますが、ブロックされません。 Windows Defender がアクションを実行したアプリケーションに関する情報は、Windows Defender によって作成されたイベントをイベント ビューアーで検索することで確認できます。  
  - *[デバイスの既定値]* に設定すると、PUA 保護はオフになります。  
 
  **既定値**: ブロック

- **Defender クラウド延長タイムアウト**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) - Windows Defender ウイルス対策がクラウドからの結果を待機している間にファイルをブロックする最大追加時間を指定します。 Windows Defender が待機する基本的な時間の長さは 10 秒です。 ここで指定した追加の時間 (最大 50 秒) は、それらの 10 秒に追加されます。 ほとんどの場合、スキャンにかかる時間は最大値より短くなります。 時間を延長すると、クラウドは疑わしいファイルを徹底的に調査できます。  

  既定では、延長時間の値は 0 (無効) です。 Intune では、この設定を有効にし、少なくとも 20 秒の追加を指定することが推奨されています。  
 
  **既定値**: 0

- **アーカイブ ファイルをスキャンする**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – *[はい]* に設定すると、Windows Defender でアーカイブ ファイルがスキャンされます。  

  **既定値**: はい

- **Defender システム スキャンのスケジュール**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) - Defender がデバイスをスキャンする日をスケジュールします。 
 
  このリスト内の関連オプション: *Defender/ScheduleScanTime*

  **既定値**: ユーザー定義

- **動作の監視**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – *[はい]* に設定すると、Windows Defender の動作監視機能がオンになります。 Windows 10 内蔵の、Windows Defender の動作監視機能センサーでは、オペレーティング システムから動作信号を収集して処理し、プライベート クラウドに他から切り離されて存在する Microsoft Defender ATP インスタンスにこのセンサー データを送信します。  

  **既定値**: はい

- **ネットワーク フォルダーから開いたファイルをスキャンする**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – *[はい]* に設定すると、Windows Defender によってネットワーク上のファイルがスキャンされます。 ユーザーは、読み取り専用のファイルから検出されたマルウェアを削除することはできません。  

  **既定値**: はい

- **Defender cloud block level (Defender クラウド ブロック レベル)**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – このポリシーを使用すると、Windows Defender ウイルス対策で悪意のあるファイルをブロックおよびスキャンする際にどの程度積極的に行うかを決定できます。 次のオプションがあります。

  - 高 - クライアントのパフォーマンスの最適化中に不明なファイルを積極的にブロックします (誤検知の可能性が高くなります)
  - \+ 高 - 不明なファイルを積極的にブロックし、追加の保護策を適用します (クライアントのパフォーマンスに影響を及ぼす可能性があります)
  - ゼロ トレランス - 不明な実行可能ファイルをすべてブロックします。

  **既定値**: 未構成

- **リアルタイム監視**:  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – *[はい]* に設定すると、Windows Defender リアルタイム監視が許可されます。  

  **既定値**: はい

- **スキャン中の CPU 使用率の制限**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – Windows Defender がスキャン中に使用できる最大平均 CPU 使用率を指定します。  

  **既定値**: 50

- **フル スキャン中に、マップされたネットワーク ドライブをスキャンする**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) - *[はい]* に設定すると、Windows Defender によってネットワーク上のファイルがスキャンされます。 ユーザーは読み取り専用ファイルから検出されたマルウェアを削除することはできません。

  このリスト内の関連設定: *Defender/AllowScanningNetworkFiles*

  **既定値**: はい

- **エンドユーザーによる Defender へのアクセスをブロックする**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – *[はい]* に設定すると、エンドユーザーは自分のデバイス上での Windows Defender UI へのアクセスをブロックされます。  

  **既定値**: はい

- **クイック スキャン開始日時**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) - Defender がクイック スキャンを実行する時刻をスケジュールします。  

  **既定値**: 午前 2 時

## <a name="windows-defender-firewall"></a>Windows Defender ファイアウォール
詳細については、Windows のドキュメントの「[Firewall CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)」 (ファイアウォール CSP) を参照してください。

- **セキュリティ アソシエーションが削除されるまでのアイドル時間** - *MdmStore/Global/SaIdleTime*   
  この秒数の間、ネットワーク トラフィックが確認されなかった場合は、セキュリティ アソシエーションが削除されます。  
  **既定値**: 300

- **ファイル転送プロトコル** - *MdmStore/Global/DisableStatefulFtp*   
  ステートフル ファイル転送プロトコル (FTP) をブロックします。  
  **既定値**: はい

- **パケット キュー** - *MdmStore/Global/EnablePacketQueue*    
  IPsec トンネル ゲートウェイのシナリオで、暗号化された受信とクリア テキストの転送について受信側のソフトウェアのスケーリングを有効にする方法を指定します。 これにより、パケットの順序が確実に保持されます。  
  **既定値**: デバイスの既定値

- **ファイアウォール プロファイル ドメイン** - *FirewallRules/FirewallRuleName/Profiles*  
  ルールが属するプロファイルを指定します: ドメイン、プライベート、パブリック。 この値は、ドメインに接続されているネットワークのプロファイルを表します。  

  利用可能な設定:  
  - **マルチキャスト ブロードキャストへのユニキャスト応答が必要**  
    **既定値**: はい

  - **グループ ポリシーからの承認されたアプリケーション ルールをマージ**  
    **既定値**: はい

  - **着信通知をブロック**  
    **既定値**: はい

  - **グループ ポリシーからのグローバル ポート ルールをマージ**  
    **既定値**: はい

  - **ステルス モードをブロック**  
    **既定値**: はい

  - **ファイアウォールの有効化**  
    **既定値**: 許可

  - **グループ ポリシーからの接続セキュリティ ルールをマージしない**  
    **既定値**: はい

  - **グループ ポリシーからのポリシー ルールをマージしない**  
    **既定値**: はい

- **ファイアウォール プロファイル パブリック** - *FirewallRules/FirewallRuleName/Profiles*  
  ルールが属するプロファイルを指定します: ドメイン、プライベート、パブリック。 この値は、パブリック ネットワークのプロファイルを表します。 これらのネットワークは、サーバー ホストで管理者によってパブリックとして分類されます。 分類は、ホストが初めてネットワークに接続したときに行われます。 通常、これらのネットワークは空港や喫茶店など、ネットワーク内のピアまたはネットワーク管理者が信頼されていない公共の場所にあります。  

  利用可能な設定:

  - **受信接続をブロック**  
    **既定値**: はい 

  - **マルチキャスト ブロードキャストへのユニキャスト応答が必要**  
    **既定値**: はい  

  - **ステルス モードが必要**  
    **既定値**: はい 
 
  - **送信接続が必要**  
    **既定値**: はい  

  - **グループ ポリシーからの承認されたアプリケーション ルールをマージ**  
    **既定値**: はい  

  - **着信通知をブロック**  
    **既定値**: はい  

  - **グループ ポリシーからのグローバル ポート ルールをマージ**  
    **既定値**: はい

  - **ステルス モードをブロック**  
    **既定値**: はい

  - **ファイアウォールの有効化**  
    **既定値**: 許可  

  - **グループ ポリシーからの接続セキュリティ ルールをマージしない**  
    **既定値**: はい  

  - **着信トラフィックが必要**  
    **既定値**: はい

  - **グループ ポリシーからのポリシー ルールをマージしない**  
    **既定値**: はい  

- **ファイアウォール プロファイル プライベート** - *FirewallRules/FirewallRuleName/Profiles*  
  ルールが属するプロファイルを指定します: ドメイン、プライベート、パブリック。 この値は、プライベート ネットワークのプロファイルを表します。  

  利用可能な設定: 

  - **受信接続をブロック**  
    **既定値**: はい

  - **マルチキャスト ブロードキャストへのユニキャスト応答が必要**  
    **既定値**: はい

  - **ステルス モードが必要**  
    **既定値**: はい

  - **送信接続が必要**  
    **既定値**: はい

  - **着信通知をブロック**  
    **既定値**: はい

  - **グループ ポリシーからのグローバル ポート ルールをマージ**  
    **既定値**: はい

  - **ステルス モードをブロック**  
    **既定値**: はい  

  - **ファイアウォールの有効化**  
    **既定値**: 許可

  - **グループ ポリシーからの承認されたアプリケーション ルールをマージしない**  
    **既定値**: はい

  - **グループ ポリシーからの接続セキュリティ ルールをマージしない**  
    **既定値**: はい

  - **着信トラフィックが必要**  
    **既定値**: はい

  - **グループ ポリシーからのポリシー ルールをマージしない**  
    **既定値**: はい  

- **ファイアウォール事前共有キー エンコード方式**  
  **既定値**: UTF8

- **証明書失効リストの検証**  
  **既定値**: デバイスの既定値

## <a name="windows-hello-for-business"></a>Windows Hello for Business  

詳細については、Windows のドキュメントの「[PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp)」を参照してください。

- **Windows Hello for Business を構成する** - *TenantId/Policies/UsePassportForWork*    
  Windows Hello for Business は、パスワード、スマート カード、および仮想スマート カードを置き換えることで Windows にサインインする代替方法です。  

  - *[はい]* に設定すると、このポリシーが有効になり、デバイスは Windows Hello for Business をプロビジョニングします。  
  - [*未構成*] に設定した場合、ベースラインはデバイスのポリシー設定に影響しません。 これは、Windows Hello for Business がデバイスで無効になっていると、無効のままになることを意味します。 有効になっている場合は、有効のままになります。 

  この基準を使用して Windows Hello for Business を無効にすることはできません。 Windows Hello for Business を無効にするには、 [windows の登録](windows-hello.md)を構成するか、 [identity protection](identity-protection-configure.md)のデバイス構成プロファイルの一部としてを使用します。  

Windows Hello for Business は、パスワード、スマート カード、および仮想スマート カードを置き換えることで Windows にサインインする代替方法です。  

  このポリシー設定を有効にした場合、または構成しなかった場合、デバイスでは Windows Hello for Business がプロビジョニングされます。 このポリシー設定を無効にした場合、デバイスではどのユーザーに対しても Windows Hello for Business をプロビジョニングが行われません。

  Intune では Windows Hello の無効化はサポートされていません。 その代わり、Windows Hello for Business を有効にする (Yes) ように、または Windows Hello を直接設定しない (未構成) ようにポリシーを構成できます。 未構成の場合、デバイスでは他のポリシーを介して、この機能を有効または無効にする構成を受信することができます。  

  **既定値**: はい  

- **PIN に小文字が必要** - *TenantId/Policies/PINComplexity/LowercaseLetters*  
  **既定値**: 許可  

- **PIN に特殊文字が必要** - *TenantId/Policies/PINComplexity/SpecialCharacters*  
  **既定値**: 許可  

- **PIN に大文字が必要** - *TenantId/Policies/PINComplexity/UppercaseLetters*   
  **既定値**: 許可  

