---
title: Windows 10 用の Intune セキュリティ ベースラインの設定
titleSuffix: Microsoft Intune
description: Intune で管理する Windows 10 デバイスの Windows MDM セキュリティベースラインにある既定値と使用可能な設定を確認します。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d673650a26f3917fa32babba42e5e2054c87e59
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060019"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Intune 用の MDM セキュリティ ベースラインの設定  

Windows 10 以降を実行しているデバイスの Microsoft Intune でサポートされている MDM セキュリティベースライン設定を表示します。 このベースラインの設定の既定値は、適用可能なデバイスに推奨される構成を表し、他のセキュリティベースラインからの基準の既定値とは一致しない場合があります。  

最新の基準バージョンは、 **2019 年5月の MDM セキュリティベースライン**です。  

以前のバージョンのこの基準の最新バージョンで変更された内容については、「[新しいテンプレートの変更点](#whats-changed-in-the-new-template)」を参照してください。  

> [!NOTE]  
> 2019年6月に、プレビュー MDM セキュリティベースラインは、一般公開されている (プレビューではない) 5*月2019テンプレートの Mdm セキュリティベースライン*のリリースに置き換えられました。 2019年 5*月の Mdm セキュリティ*ベースラインが使用可能になる前に作成されたプロファイルは、年 5 2019 月バージョンの Mdm セキュリティ基準に含まれる設定と値を反映して更新されません。  プレビューテンプレートに基づいて新しいプロファイルを作成することはできませんが、プレビューテンプレートに基づいて以前に作成したプロファイルを編集し、引き続き使用することができます。   
  
Intune でのセキュリティベースラインの使用方法については、「[セキュリティベースラインの使用](security-baselines.md)」を参照してください。  


   
## <a name="above-lock"></a>Above Lock (上でロック)  
詳細については、Windows の「[Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock)」(ポリシー CSP - AboveLock) を参照してください。  

- **Block display of toast notifications (トースト通知の表示をブロックする)**  
  このポリシー設定では、アプリ通知をロック画面に表示しないように設定します。 このポリシー設定を有効にした場合、ロック画面にどのアプリ通知も表示されません。 このポリシー設定を無効にした場合、または構成しなかった場合、ロック画面に通知を表示するアプリをユーザーが選択できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **既定値**: はい  

- **ロック画面から音声でアプリをアクティブ化する**  

  **既定値**: 無効

## <a name="app-runtime"></a>[アプリ実行時]    
詳細については、Windows の「[Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
)」(ポリシー CSP - AppRuntime) を参照してください。  

- **Microsoft accounts optional for Windows Store apps (Windows ストア アプリで Microsoft アカウントの省略を許可する)**  
  このポリシー設定によって、サインインにアカウントを必要とする Windows ストア アプリで Microsoft アカウントを省略可能にするかどうかを制御できます。 このポリシーが影響するのは、このポリシーをサポートする Windows ストア アプリだけです。 このポリシー設定を有効にした場合、通常はサインインに Microsoft アカウントを必要とする Windows ストア アプリで、ユーザーは、代わりにエンタープライズ アカウントを使用してサインインできます。 このポリシー設定を無効にした場合、または構成しなかった場合、ユーザーは Microsoft アカウントを使用してサインインする必要があります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **既定値**: 有効  

## <a name="application-management"></a>アプリケーション管理   
詳細については、Windows の「[Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)」(ポリシー CSP - ApplicationManagement) を参照してください。  

- **ユーザーによるインストールの制御をブロックする**  
  このポリシー設定を使用すると、通常はシステム管理者のみが使用できるインストールのオプションをユーザーが変更できるようになります。 このポリシー設定を有効にした場合、Windows インストーラーの一部のセキュリティ機能がバイパスされます。 このポリシーを使用すると、通常はセキュリティ違反のため強制的に中止されるインストールを完了させることができます。 このポリシー設定を無効にした場合、または構成しなかった場合、Windows インストーラーでは、通常システム管理者のみに許可されているインストールのオプション (たとえば、ファイルのインストール先の指定) をユーザーが変更することはできません。 保護されているオプションをユーザーが変更しようとすると、インストールは中止されエラー メッセージが表示されます。 このセキュリティ機能は、インストール プログラムが特権付きセキュリティ コンテキストで実行されており、ユーザーがアクセス許可を持っていないディレクトリにプログラムがアクセスできるときに機能します。 このポリシー設定は、規制を緩和するためのものです。 ソフトウェアのインストールを妨げるようなインストールのエラーを回避するためにも使用できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **既定値**: はい

- **管理者特権での MSI アプリのインストールをブロックする**  
  このポリシー設定を使用すると、Windows インストーラーを使ってシステムにプログラムをインストールするときに管理者特権のアクセス許可が使用されます。  
  - "*このポリシー設定を有効にすると*"、特権がすべてのプログラムに適用されます。 通常、このような特権はユーザー (デスクトップ上で提供されている) またはコンピューター (自動的にインストールされている)f に割り当てられているプログラム、またはコントロール パネルの [プログラムの追加と削除] で利用できるプログラム用に予約されています。 このプロファイル設定を使うと、ユーザーはアクセス許可が与えられていないため表示も変更もできないディレクトリ (厳しく制限されているコンピューター上のディレクトリを含む) へのアクセスを必要とするプログラムをインストールできます。
  - "*このポリシー設定を無効にした場合、または構成しなかった場合*" は、システム管理者から配布または提供されていないプログラムのインストール時にはユーザーの現在のアクセス許可が適用されます。 注: このポリシー設定は [コンピューターの構成] フォルダーおよび [ユーザーの構成] フォルダーにあります。 このポリシー設定を有効にするには、両方のフォルダーでこのポリシー設定を有効にする必要があります。 警告: 上級ユーザーは、このポリシー設定で付与されるアクセス許可を使って特権を変更し、制限付きのファイルおよびフォルダーに継続してアクセスできます。 このポリシー設定の [ユーザーの構成] バージョンのセキュリティ保護は必ずしも安全ではないことに注意してください。  
  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **既定値**: はい

- **Block game DVR (desktop only) (ゲーム DVR をブロックする (デスクトップのみ))**  
  ゲームの録画とブロードキャストを許可するかどうか設定します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **既定値**: はい  

## <a name="auto-play"></a>Auto Play (自動再生)   
詳細については、Windows の「[Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay)」(ポリシー CSP - Autoplay) を参照してください。  

- **Auto play default auto run behavior (自動再生の既定の自動実行の動作)**  
  この設定は、自動実行コマンドの既定の動作に影響します。 自動実行コマンドは、autorun.inf ファイルに保存されており、インストール プログラムやその他のルーチンを開始できます。 これを*有効*にすると、管理者は Windows Vista 以降を実行するデバイスの自動実行の既定の動作を変更することができます。 次の動作に設定できます: a) 自動実行コマンドを完全に無効にする、b) 自動実行コマンドを自動的に実行する Windows Vista 以前の動作に戻す。 *無効*または*未構成*にすると、Windows Vista 以降を実行するコンピューターで自動実行コマンドを実行するかユーザーはたずねられます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **既定値**: 実行しない  
  
- **Auto play mode (自動再生のモード)**  
  このポリシー設定では、自動再生機能をオフにできます。 自動再生とは、ドライブにメディアを挿入すると同時にドライブからの読み込みを開始する機能です。 この機能によって、プログラムのセットアップ ファイルやオーディオ メディアの音楽などがすぐに開始されます。 Windows XP SP2 より前は、自動再生は、フロッピー ディスク ドライブなどのリムーバブル ドライブ (CD-ROM ドライブは除く) およびネットワーク ドライブ上では既定で無効になっています。 Windows XP SP2 以降では、自動再生は Zip ドライブや一部の USB 大容量記憶装置デバイスなどのリムーバブル ドライブでも有効になっています。 このポリシー設定を有効にした場合、CD-ROM およびリムーバブル メディア ドライブの自動再生を無効にするか、すべてのドライブの自動再生を無効にすることができます。 このポリシー設定によって、これ以外の種類のドライブでの自動再生を無効にすることができます。 この設定を使用して、既定で無効になっているドライブ上の自動再生を有効にすることはできません。 このポリシー設定を無効にした場合、または構成しなかった場合、自動再生が有効になります。 注: このポリシー設定は [コンピューターの構成] フォルダーおよび [ユーザーの構成] フォルダーにあります。 ポリシー設定が競合する場合、[コンピューターの構成] にあるポリシー設定が [ユーザーの構成] にあるポリシー設定より優先されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **既定値**: 無効

- **Block auto play for non-volume devices (ボリューム以外のデバイスの自動再生をブロックする)**  
  このポリシー設定では、カメラや電話などの MTP デバイスの自動再生を許可しません。 このポリシー設定を有効にした場合、カメラや電話などの MTP デバイスの自動再生が許可されません。 このポリシー設定を無効にした場合、または構成しなかった場合、ボリューム以外のデバイスに対する自動再生が有効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **既定値**: 有効  

## <a name="bitlocker"></a>Bitlocker    
詳細については、Windows の「[Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
)」(ポリシー CSP - Bitlocker) を参照してください。  

- **Bit locker removable drive policy (Bitlocker のリムーバブル ドライブのポリシー)**  
  このポリシー設定は、暗号化方法および暗号化強度を制御するために使用します。 このポリシーの値は、BitLocker が暗号化に使用する暗号化強度を決定します。 企業では、セキュリティを強化するために、暗号化のレベルを制御したい場合があります (AES-256 は AES-128 よりも強力です)。 この設定を有効にした場合は、固定データ ドライブやオペレーティング システム ドライブ、リムーバブル データ ドライブのそれぞれに、暗号化アルゴリズムとキーの暗号化強度を構成できます。 固定ドライブやオペレーティング システム ドライブには、XTS-AES アルゴリズムを使用することをお勧めします。 リムーバブル ドライブには、Windows 10 バージョン 1511 以降を実行していないその他のデバイスでドライブを使用する場合は、AES-CBC 128 ビットまたは AES-CBC 256 ビットを使用する必要があります。 ドライブが既に暗号化されているか、暗号化が進行中の場合は、暗号化の種類を変更しても影響はありません。 このような場合、このポリシー設定は無視されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Bitlocker リムーバブル ドライブ ポリシーの場合は、次の設定を構成します。

  - **Require encryption for write access (書き込みアクセス用に暗号化が必要)**  
    **既定値**: はい  
  

## <a name="browser"></a>ブラウザー  
詳細については、Windows の「[Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)」(ポリシー CSP - Browser) を参照してください。  

- **Require SmartScreen for Microsoft Edge (Microsoft Edge で SmartScreen が必要)**  
  Microsoft Edge では、(オンになった) Microsoft Defender SmartScreen を使用して、フィッシング詐欺にあう可能性や悪意のあるソフトウェアから既定でユーザーを保護しています。 また、既定では、ユーザーは Microsoft Defender SmartScreen を無効 (オフ) にできません。 このポリシーを有効にすると、Microsoft Defender SmartScreen がオフになり、ユーザーがそれをオンにできないようになります。 ユーザーが Microsoft Defender SmartScreen のオンとオフを選択できるようにする場合は、このポリシーを構成しないでください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **既定値**: はい  
  
- **Block malicious site access (悪意のあるサイトへのアクセスをブロックする)**  
  既定では、Microsoft Edge では、悪意のある可能性があるサイトに関する Microsoft Defender SmartScreen の警告をユーザーがバイパス (無視) して、サイトに進むことができます。 このポリシーを使用すると、ユーザーが警告をバイパスし、サイトに進めないように Microsoft Edge を構成できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **既定値**: はい  
  
- **Block unverified file download (確認されていないファイルのダウンロードをブロックする)**  
  既定では、Microsoft Edge では、悪意のある可能性があるファイルに関する Microsoft Defender SmartScreen の警告をユーザーがバイパス (無視) して、未確認のファイルのダウンロードを続行することができます。 このポリシーを有効にすると、ユーザーはこの警告をバイパスして、確認されていないファイルをダウンロードできなくなります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **既定値**: はい  
  
- **Block Password Manager (Password Manager をブロックする)**  
  Microsoft Edge で既定で Password Manager が自動的に使用されることによって、ユーザーはパスワードをローカルで管理できるようになります。 このポリシーを無効にすると、Microsoft Edge で Password Manager が使用されなくなります。 ユーザーに Password Manager を使用してローカルでパスワードを保存および管理させる場合には、このポリシーは設定しないでください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **既定値**: はい  
  
- **Prevent certificate error overrides (証明書エラーのオーバーライドを防ぐ)**  
  このポリシー設定は、Internet Explorer での閲覧を妨げる Secure Sockets Layer/トランスポート層セキュリティ (SSL/TLS) 証明書エラー (期限切れ、失効、名前の不一致などのエラー) をユーザーが無視できないようにします。 このポリシー設定を有効にすると、ユーザーは閲覧を継続できません。 このポリシー設定を無効にするか、構成しない場合、ユーザーは証明書エラーを無視して閲覧を継続できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **既定値**: はい  

## <a name="connectivity"></a>接続  
詳細については、Windows の「[Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity)」(ポリシー CSP - Connectivity) を参照してください。  

- **Block Internet download for web publishing and online ordering wizards (Web 発行およびオンライン注文ウィザードのインターネット ダウンロードをブロックする)**  
  このポリシー設定では、Web 発行ウィザードおよびオンライン注文ウィザード用のプロバイダーの一覧をダウンロードするかどうかを指定します。 これらのウィザードでは、オンライン記憶域や写真印刷などのサービスを提供する会社の一覧から会社を選択できます。 既定では、レジストリで指定されているプロバイダーに加えて Windows Web サイトからダウンロードしたプロバイダーも表示されます。 このポリシー設定を有効にした場合、プロバイダーはダウンロードされず、ローカル レジストリにキャッシュされたサービス プロバイダーのみが表示されます。 このポリシー設定を無効にした場合、または構成しなかった場合、ユーザーが Web 発行ウィザードまたはオンライン注文ウィザードを使用するときに、プロバイダーの一覧がダウンロードされます。 レジストリでサービス プロバイダーを指定する方法などの詳細については、Web 発行ウィザードおよびオンライン注文ウィザードのドキュメントを参照してください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **既定値**: 有効  

- **UNC パスへのセキュリティで保護されたアクセスの構成**  
  このポリシー設定では、UNC パスへのセキュリティで保護されたアクセスを構成します。 このポリシーを有効にすると、追加のセキュリティ要件を満たした後に、指定した UNC パスへのアクセスのみが許可されます。
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **既定**: 追加のセキュリティ要件を満たした後に、指定した UNC パスへのアクセスのみを許可するように Windows を構成します。
  
  [追加のセキュリティ要件を満たす] を選択した後に、*指定した unc パスへのアクセスのみを許可するように Windows を構成*する場合は、* ハード終了 UNC パスの一覧を構成できます。
  - **書き込まれる UNC パスの一覧**  
    追加のセキュリティフラグとサーバーパスを指定するには、 **[追加]** を選択します。  

- **Block downloading of print drivers over HTTP (プリンター ドライバーの HTTP 経由でのダウンロードをブロックする)**  
  このポリシー設定では、クライアントが HTTP 経由でプリンター ドライバー パッケージをダウンロードするかどうかを指定します。 HTTP 経由の印刷をセットアップするには、付属していないドライバーを HTTP 経由でダウンロードする必要があります。 注: このポリシー設定が有効になっている場合でも、クライアントはイントラネットやインターネットのプリンターに HTTP 経由で出力できます。 ローカルにインストールされていないドライバーのダウンロードのみを禁止します。 この設定を有効にした場合、プリンター ドライバーは HTTP 経由でダウンロードできません。 このポリシー設定を無効にした場合、または構成しなかった場合、ユーザーは HTTP 経由でプリンター ドライバーをダウンロードできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **既定値**: 有効  

## <a name="credentials-delegation"></a>資格情報の委任  
詳細については、Windows の「[Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
)」(ポリシー CSP - CredentialsDelegation) を参照してください。  

- **Remote host delegation of non-exportable credentials (リモート ホストでエクスポートできない資格情報を委任する)**  
  リモート ホストでは、エクスポートできない資格情報を委任できます。 資格情報の委任を使用する場合、エクスポート可能なバージョンの資格情報がデバイスからリモート ホストに提供されます。これにより、ユーザーはリモート ホスト上の攻撃者に資格情報が盗まれるというリスクにさらされます。 このポリシー設定を有効にした場合、ホストは制限付き管理モードまたは Remote Credential Guard モードをサポートします。 このポリシー設定を無効にするか、構成しなかった場合、制限付き管理モードと Remote Credential Guard モードはサポートされません。 ユーザーは常に資格情報をホストに渡す必要があります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **既定値**: 有効  

## <a name="credentials-ui"></a>Credentials UI (資格情報 UI)  
詳細については、Windows の「[Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui)」(ポリシー CSP - CredentialsUI) を参照してください。  

- **Enumerate administrators (管理者の列挙)** このポリシー設定により、ユーザーが実行中のアプリケーションの昇格を試みたときに、管理者アカウントが表示されるかどうかを制御します。 既定では、ユーザーが実行中のアプリケーションの昇格を試みたときに、管理者アカウントは表示されません。 このポリシー設定を有効にした場合、PC 上のローカル管理者アカウントがすべて表示され、ユーザーがその 1 つを選択して、正しいパスワードを入力できます。 このポリシー設定を無効にした場合、ユーザーは、昇格時にユーザー名とパスワードを常に入力するよう要求されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **既定値**: 無効  

## <a name="data-protection"></a>データ保護  
詳細については、Windows の「[Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
)」(ポリシー CSP - DataProtection) を参照してください。  

- **Block direct memory access (ダイレクト メモリ アクセスをブロックする)**  
  このポリシー設定では、ユーザーが Windows にログインするまで、ホット プラグ可能なすべての PCI ダウンストリーム ポートへのダイレクト メモリ アクセス (DMA) をブロックできます。 ユーザーがログインすると、Windows はホット プラグ PCI ポートに接続されている PCI デバイスを列挙します。 ユーザーがコンピューターをロックするたびに、ユーザーが再ログインするまで、子デバイスが接続されていないホット プラグ PCI ポートで DMA がブロックされます。 コンピューターのロックが解除された際に既に列挙されていたデバイスは、取り外されるまで機能を維持します。 このポリシー設定は、BitLocker またはデバイスの暗号化が有効な場合にのみ適用されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **既定値**: はい  

## <a name="device-guard"></a>[Device Guard]  
詳細については、Windows の「[Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
)」(ポリシー CSP - DeviceGuard) を参照してください。  

- **[Credential Guard]**  
  ユーザーはこの設定で、次回の再起動時に資格情報が保護されるよう、仮想化ベースのセキュリティで Credential Guard をオンにできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **既定値**: UEFI ロックで有効化 

- **仮想化ベースのセキュリティを有効にする**   
  仮想化ベースのセキュリティ (VBS) を次の再起動時にオンにします。 仮想化ベースのセキュリティは、Windows ハイパーバイザーを使ってセキュリティ サービスのサポートを提供します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **既定値**: はい  


- **Launch system guard (System Guard を起動する)**     
  **既定値**: 有効  

## <a name="device-installation"></a>デバイスのインストール  
詳細については、Windows の「[Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation)」(ポリシー CSP - DeviceInstallation) を参照してください。  

- **Hardware device installation by device identifiers (デバイス識別子を使用してハードウェア デバイスをインストールする)**  
  このポリシー設定では、インストールを禁止するデバイスのプラグ アンド プレイ ハードウェア ID および互換性 ID を指定できます。 このポリシー設定は、デバイスのインストールを許可する他のポリシー設定よりも優先されます。 このポリシー設定を有効にした場合、プラグ アンド プレイ ハードウェア ID または互換性 ID が作成した一覧に含まれているデバイスはインストールできません。 リモート デスクトップ サーバーでこのポリシー設定を有効にした場合、このポリシー設定は、リモート デスクトップ クライアントからリモート デスクトップ サーバーへの指定されたデバイスのリダイレクトに影響します。 この設定を無効にした場合、または構成しなかった場合は、他のポリシー設定に従って、デバイスのインストールや更新が許可されるかどうかが決まります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **既定値**: Block hardware device installation (ハードウェア デバイスのインストールをブロックする)  

  *[ハードウェア デバイスのインストールをブロックする]* を選択すると、次の設定が利用できます。

  - **Remove matching hardware devices (一致するハードウェア デバイスを削除する)**    
    この設定は *[Hardware device installation by device identifiers]\(デバイス識別子でハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。
    
    **既定値**: はい

  - **Hardware device identifiers that are blocked (ブロックされているハードウェア デバイス識別子)**  
    この設定は *[Hardware device installation by device identifiers]\(デバイス識別子でハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。
    
    **既定値**: はい  
  
- **Hardware device installation by setup classes (セットアップ クラスを使用してハードウェア デバイスをインストールする)**  
  このポリシー設定では、インストールを禁止するデバイス ドライバーのデバイス セットアップ クラス GUID (グローバル一意識別子) の一覧を指定できます。 このポリシー設定は、デバイスのインストールを許可する他のポリシー設定よりも優先されます。 このポリシー設定を有効にした場合、デバイス セットアップ クラス GUID が作成した一覧に含まれているデバイス ドライバーはインストールすることも更新することもできません。 リモート デスクトップ サーバーでこのポリシー設定を有効にした場合、このポリシー設定は、リモート デスクトップ クライアントからリモート デスクトップ サーバーへの指定されたデバイスのリダイレクトに影響します。 この設定を無効にした場合、または構成しなかった場合は、他のポリシー設定に従って、デバイスのインストールや更新が許可されるかどうかが決まります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **既定値**: Block hardware device installation (ハードウェア デバイスのインストールをブロックする)  

  *[ハードウェア デバイスのインストールをブロックする]* を選択すると、次の設定が利用できます。
  - **Remove matching hardware devices (一致するハードウェア デバイスを削除する)**     
    この設定は *[Hardware device installation by setup classes]\(設定クラスでハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。  

    **既定値**: *既定の構成はありません*  

  - **Hardware device identifiers that are blocked (ブロックされているハードウェア デバイス識別子)**  
    この設定は *[Hardware device installation by setup classes]\(設定クラスでハードウェア デバイスをインストールする\)* が *[Block hardware device installation]\(ハードウェア デバイスのインストールをブロックする\)* に設定されているときのみ使用できます。
    
    **既定値**: *既定の構成はありません*  

## <a name="device-lock"></a>デバイスのロック  
詳細については、Windows の「[Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)」(ポリシー CSP - DeviceLock) を参照してください。  

- **Prevent use of camera (カメラの使用を禁止する)**  
  PC 設定でロック画面カメラのトグル スイッチを無効にし、ロック画面でカメラを呼び出せないようにします。 既定では、ユーザーはロック画面で使用可能なカメラを呼び出すことができます。 この設定を有効にした場合、ユーザーは、PC 設定でロック画面カメラへのアクセスを有効または無効にできなくなり、ロック画面でカメラを呼び出せなくなります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **既定値**: 有効  

- **Require password (パスワードを必須にする)**  
  デバイスのロックを有効にするかどうかを指定します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **既定値**: はい  
  
  *[パスワードを要求する]* を *[はい]* に設定すると、次の設定が利用できます。

  - **Password minimum character set count (パスワードの最小文字セット数)**  
    強力な PIN またはパスワードに必要な複合要素の種類 (大文字、小文字、数字、句読点) の数です。 デスクトップおよびモバイル デバイスには次の動作が PIN によって強制されます。1 - 数字のみ 2 - 数字と小文字が必要 3 - 数字、小文字、および大文字が必要。 デスクトップの Microsoft アカウントおよびドメイン アカウントではサポートされていません。 4 - 数字、小文字、大文字、および特殊文字が必要。 デスクトップではサポートされていません。 既定値は 1 です。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **既定値**: 3  

  - **デバイスがワイプされるまでのサインイン失敗回数**  
    デバイスがワイプされるまでに許容される認証の失敗回数。 値 0 を指定すると、デバイスのワイプ機能が無効になります。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **既定値**: 10  

  - **パスワードの有効期限 (日)**  
    パスワードの最大有効期間ポリシー設定によって、ユーザーがパスワードの変更を要求されるまでにパスワードを使用できる期間 (日数) が決まります。 1 から 999 までの日数の経過後にパスワードが期限切れになるように設定できます。また、日数を 0 に設定することでパスワードが期限切れにならないように指定することもできます。 [Maximum password age]\(パスワードの最大有効期間\) が 1 から 999 日の間である場合、パスワードの最小有効期間はパスワードの最大有効期間よりも短くする必要があります。 [Maximum password age]\(パスワードの最大有効期間\) が 0 に設定されている場合、[Minimum password]\(パスワードの最小有効期間\) には 0 から 998 日の値を設定できます。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **既定値**: 60  

  - **必要なパスワードの種類**  
    必要な PIN またはパスワードの種類を決定します。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **既定値**: 英数字  

  - **最小のパスワードの長さ**  
    [Minimum password length]\(最小のパスワードの長さ\) ポリシー設定によって、ユーザー アカウントのパスワードを構成できる最小文字数が決まります。 1 から 14 文字の値を設定できます。また、文字数を 0 に設定して、パスワードが必須ではないことを設定できます。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **既定値**: 8  

  - **Block simple passwords (単純なパスワードをブロックする)**  
    "1111" や "1234" などの PIN またはパスワードを許可するかどうかを指定します。 デスクトップでは、ピクチャ パスワードの使用も制御します。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **既定値**: はい  
      *[Yes]\(はい\) に設定すると、単純なパスワードを使用できなくなります。* 

  - **前のパスワードの再利用を防止**  
    使用できないパスワードを履歴にいくつ保存できるかを指定します。 この値には、ユーザーの現在のパスワードも含まれます。 たとえば、設定が *1* の場合、ユーザーは新しいパスワードを選択すると、現在のパスワードは再利用できません。 設定が *5* の場合は、ユーザーは新しいパスワードを現在のパスワードに設定することも、以前の 4 つのパスワードのいずれかに設定することもできません。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **既定値**: 24  

- **Prevent slide show (スライド ショーを禁止する)**  
  PC 設定でロック画面スライド ショー設定を無効にし、ロック画面でスライド ショーを再生できないようにします。 既定では、ユーザーは、コンピューターのロック後に実行されるスライド ショーを有効にできます。 この設定を有効にした場合、ユーザーは [PC 設定] でスライド ショー設定を修正することができず、スライド ショーは開始できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **既定値**: 有効  
  *有効に設定すると、スライド ショーは実行されなくなります。* 

- **Password minimum age in days (パスワードの最小有効期間 (日))**  
  [Minimum password age]\(パスワードの最小有効期間\) ポリシー設定によって、ユーザーがパスワードを変更できるようになるまでの使用する必要がある期間 (日数) が決まります。 1 から 998 日の値を設定できます。また、日数を 0 に設定することで、パスワードの変更をすぐに許可することもできます。 パスワードの最大有効期間が 0 (パスワードが期限切れにならないことを示します) に設定されている場合を除き、パスワードの最小有効期間はパスワードの最大有効期限よりも短くする必要があります。 パスワードの最大有効期間が 0 に設定されている場合、パスワードの最小有効期間は 0 から 998 の任意の値に設定できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **既定値**: 1  

## <a name="dma-guard"></a>DMA ガード  
詳細については、Windows ドキュメントの「[Policy CSP - DmaGuard (ポリシー CSP - DmaGuard)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard)」をご覧ください。
- **Kernel DMA Protection と互換性のない外部デバイスの列挙**  
  このポリシーは、外部 DMA 対応デバイスに対して追加のセキュリティを提供することを目的としています。 これにより、DMA の再マッピング/デバイス メモリの分離およびサンドボックス化と互換性のない外部 DMA 対応デバイスの列挙をより詳細に制御できます。 このポリシーが有効になるのは、Kernel DMA Protection がシステム ファームウェアによってサポートされていて、それによって有効にされた場合のみです。 カーネル DMA 保護は、ポリシーまたはエンドユーザーが制御できないプラットフォーム機能です。 これは、製造時にシステムによってサポートされている必要があります。 システムでカーネル DMA 保護がサポートされているかどうかを確認するには、MSINFO32 の [概要] ページで [カーネル DMA 保護] フィールドを確認してください。  
  [詳細情報](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **既定値**: すべてブロックする   

## <a name="event-log-service"></a>イベント ログ サービス  
詳細については、Windows の「[Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice)」(ポリシー CSP - EventLogService) を参照してください。  

- **Security log maximum file size in KB (セキュリティ ログの最大ファイル サイズ (KB))**  
  このポリシー設定は、ログ ファイルの最大サイズを KB 単位で指定します。 このポリシー設定を有効にした場合、ログ ファイルの最大サイズを KB 単位で 1 MB (1024 KB) から 2 TB (2147483647 KB) までの範囲内に設定できます。 このポリシー設定を無効にした場合、または構成しなかった場合、ログ ファイルの最大サイズはローカルで構成された値に設定されます。 ローカル管理者は [ログのプロパティ] ダイアログを使用してこの値を変更できます。既定値は 20 MB に設定されています。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **既定値**: 196608  

- **System log maximum file size in KB (システム ログの最大ファイル サイズ (KB))**  
  このポリシー設定は、ログ ファイルの最大サイズを KB 単位で指定します。 このポリシー設定を有効にした場合、ログ ファイルの最大サイズを KB 単位で 1 MB (1024 KB) から 2 TB (2147483647 KB) までの範囲内に設定できます。 このポリシー設定を無効にした場合、または構成しなかった場合、ログ ファイルの最大サイズはローカルで構成された値に設定されます。 ローカル管理者は [ログのプロパティ] ダイアログを使用してこの値を変更できます。既定値は 20 MB に設定されています。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **既定値**: 32768  

- **Application log maximum file size in KB (アプリケーション ログの最大ファイル サイズ (KB))**  
  このポリシー設定は、ログ ファイルの最大サイズを KB 単位で指定します。 このポリシー設定を有効にした場合、ログ ファイルの最大サイズを KB 単位で 1 MB (1024 KB) から 2 TB (2147483647 KB) までの範囲内に設定できます。 このポリシー設定を無効にした場合、または構成しなかった場合、ログ ファイルの最大サイズはローカルで構成された値に設定されます。 ローカル管理者は [ログのプロパティ] ダイアログを使用してこの値を変更できます。既定値は 20 MB に設定されています。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **既定値**: 32768  

## <a name="experience"></a>エクスペリエンス  
詳細については、Windows の「[Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)」(ポリシー CSP - Experience) を参照してください。  

- **Block Windows Spotlight (Windows スポットライトをブロックする)**  
  ロック画面上の Windows スポットライト、Windows のヒント、Microsoft のコンシューマー向け機能、その他の関連機能など、すべての Windows スポットライト機能を IT 管理者がオフにできるようにします。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **既定値**: はい  

  *[Windows Spotlight をブロックする]* を *[はい]* に設定すると、次の設定が利用できるようになります。
  
  - **Block third-party suggestions in Windows Spotlight (Windows スポットライトでのサードパーティのおすすめをブロックする)**  
    ロック画面上のスポットライト、[スタート] メニューのおすすめのアプリ、Windows のヒントなど、Windows スポットライト機能でサードパーティのソフトウェア発行元からのアプリやコンテンツのおすすめを許可するかどうかを指定します。 ただし、Microsoft の機能、アプリ、およびサービスに関するおすすめはユーザーに表示されることがあります。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **既定値**: はい  
  - **Block consumer specific features (コンシューマー向け機能をブロックする)**  
    通常はコンシューマー向けのエクスペリエンスを IT 管理者がオンにできるようにします。たとえば、開始時の提案、メンバーシップ通知、OOBE 後のアプリ インストール、リダイレクト タイルなどです。  
    [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **既定値**: はい  

## <a name="exploit-guard"></a>Exploit Guard  
詳細については、Windows の「[Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard)」(ポリシー CSP - ExploitGuard) を参照してください。  

- **[Exploit Protection XML]**  
  IT 管理者が、組織内のすべてのデバイスに対して、目的のシステムとアプリケーションの軽減策オプションを表す構成をプッシュできるようにします。 この構成は XML で表されます。 Exploit Protection は、拡散と感染のためにエクスプロイトを使用するマルウェアからデバイスを保護するのに役立ちます。 Windows セキュリティ アプリまたは PowerShell を使用して、一連の軽減策 (構成と呼ばれます) を作成します。 次に、この構成を XML ファイルとしてエクスポートし、ネットワーク上の複数のマシンと共有して、すべてのマシンに同じ軽減策設定が適用されるようにすることができます。 既存の EMET 構成 XML ファイルを変換して Exploit Protection 構成 XML にインポートすることもできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **既定値**: *サンプル XML を指定する* 
 
## <a name="file-explorer"></a>エクスプローラー  
詳細については、Windows の「[Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer)」(ポリシー CSP - FileExplorer) を参照してください。  

- **Block data execution prevention (データ実行防止をブロックする)**  
  データ実行防止を無効にすると、エクスプローラーを終了せずに特定のレガシ プラグイン アプリケーションを実行できるようになります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **既定値**: 無効  
   
- **Block heap termination on corruption (破損後のヒープ終了をブロックする)**  
  破損後のヒープ終了を無効にすると、エクスプローラーを直ちに終了せずに特定のレガシ プラグイン アプリケーションを機能させることができます。ただし、エクスプローラーは後で予期せず終了する可能性があります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **既定値**: 無効  
    

## <a name="internet-explorer"></a>Internet Explorer  
詳細については、Windows の「[Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer)」(ポリシー CSP - InternetExplorer) を参照してください。  

- **Internet Explorer の制限付きゾーンでのスクリプトによるステータス バーの更新**  
  このポリシー設定を使用すると、スクリプトを介してゾーン内のステータス バーを更新できるかどうかを管理できます。 
  - "*このポリシー設定を有効にすると*"、スクリプトを介してステータス バーを更新できます。
  - "*このポリシー設定を無効にした場合、または構成しなかった場合*"、スクリプトを介してステータス バーを更新することはできません。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **既定値**: 無効

- **Internet Explorer のインターネット ゾーンでのファイルのドラッグ アンド ドロップまたはコピーと貼り付け**  
  このポリシー設定を使用すると、ユーザーがゾーン内のソースからファイルのドラッグまたはコピーと貼り付けを行うことができるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーはこのゾーンからファイルをドラッグしたり、コピーして貼り付けたりできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、このゾーンからファイルをドラッグまたはコピーするかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーはこのゾーンからファイルをドラッグしたり、コピーして貼り付けたりできません。 このポリシー設定を構成しない場合は、自動的に、ユーザーはこのゾーンからファイルをドラッグしたり、コピーして貼り付けたりできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **既定値**: 無効にする

- **Internet Explorer の制限付きゾーンでの .NET Framework 依存コンポーネント**    
  このポリシー設定を使用すると、Authenticode を使って署名済みではない .NET Framework コンポーネントを Internet Explorer から実行できるかどうかを管理できます。 これらのコンポーネントには、object タグから参照された管理されたコントロール、リンクから参照された管理された実行可能ファイルなどが含まれます。 このポリシー設定を有効にすると、Internet Explorer は署名されていない管理されたコンポーネントを実行します。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名されていない管理されたコンポーネントを実行するかどうかを確認するメッセージが Internet Explorer によって表示されます。 このポリシー設定を無効にすると、Internet Explorer は署名済みではない管理されたコンポーネントを実行しません。 このポリシー設定を構成しない場合は、Internet Explorer は署名済みではない管理されたコンポーネントを実行しません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067077)

  **既定値**: 無効にする


- **Internet Explorer のローカル コンピューター ゾーンで Active X コントロールに対してマルウェア対策を実行しない**  
  このポリシー設定では、ActiveX コントロールをページに読み込んでも安全かどうかを調べるために Internet Explorer がマルウェア対策プログラムを実行するかどうかを決定します。 このポリシー設定を有効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 このポリシー設定を無効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 このポリシー設定を構成しない場合、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 ユーザーは、Internet Explorer の [セキュリティ] 設定を使用して、この動作の有効と無効を切り替えることができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067152)

  **既定値**: 無効

- **Internet Explorer internet zone access to data sources (Internet Explorer のインターネット ゾーンにあるデータ ソースへのアクセス)**  
  このポリシー設定を使用すると、Internet Explorer が Microsoft XML パーサー (MSXML) または ActiveX Data Objects (ADO) を使用して他のセキュリティ ゾーンからデータにアクセスできるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーはゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことができます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、ゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことはできません。 このポリシー設定を構成しないと、ゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことはできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone drag content from different domains within windows (Internet Explorer の制限付きゾーンでウィンドウ内の異なるドメインからコンテンツをドラッグする)**  
  このポリシー設定により、移行元と移行先が同じウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグするオプションを設定できます。 このポリシー設定を有効にして、[有効にする] をクリックすると、ユーザーは移行元と移行先が同じウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。 このポリシー設定を有効にして、[無効にする] をクリックすると、ユーザーは移行元と移行先が同じウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグすることはできません。 ユーザーは、[インターネット オプション] ダイアログでこの設定を変更できます。 Internet Explorer 10 では、このポリシー設定を無効にする場合、または構成しない場合、[有効にする] をクリックすると、ユーザーは移行元と移行先が同じウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグできません。 ユーザーは、[インターネット オプション] ダイアログでこの設定を変更できます。 Internet Explorer 9 以前のバージョンでは、このポリシーを無効にする場合、または構成しない場合は、ユーザーは移行元と移行先が同じウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 ユーザーは、[インターネット オプション] ダイアログでこの設定を変更できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **既定値**: 無効
  
- **[Internet Explorer certificate address mismatch warning]\(Internet Explorer の証明書アドレスの不一致についての警告\)**  
  このポリシー設定では、証明書アドレスの不一致についてのセキュリティ警告を有効にできます。 このポリシー設定が有効である場合、ユーザーが別の Web サイト アドレス用に発行された証明書を提示する Secure HTTP (HTTPS) Web サイトを訪問すると、警告が表示されます。 この警告により、スプーフィング攻撃を防止できます。 このポリシー設定を有効にすると、証明書のアドレスの不一致についての警告が常に表示されます。 このポリシー設定を無効にするか、構成しないと、ユーザーはインターネット コントロール パネルの [詳細] ページを使用して、証明書のアドレスの不一致についての警告を表示するかどうかを選択できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **既定値**: 有効 
  
- **Internet Explorer restricted zone less privileged sites (Internet Explorer の制限付きゾーンのより権限の少ないサイト)**  
  このポリシー設定を使用すると、インターネット サイト ゾーンなどのより権限の少ないゾーンにある Web サイトがこのゾーンに移動できるかどうかを管理できます。 このポリシー設定を有効にすると、より権限の少ないゾーンの Web サイトがこのゾーンで新しいウィンドウを開いたり、このゾーンに移動したりできます。 セキュリティ ゾーンは、[ゾーン昇格からの保護] のセキュリティ機能で提供されるセキュリティの追加のレイヤーなしに実行されます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、危険を及ぼす可能性のあるナビゲーションが実行されるときにユーザーに警告が表示されます。 このポリシー設定を無効にすると、危害を及ぼす可能性のあるナビゲーションは禁止されます。 Internet Explorer のセキュリティ機能は、[ゾーン昇格からの保護] 機能コントロールで設定されているように、このゾーンでオンになります。 このポリシー設定を構成しない場合は、危害を及ぼす可能性のあるナビゲーションは禁止されます。 Internet Explorer のセキュリティ機能は、[ゾーン昇格からの保護] 機能コントロールで設定されているように、このゾーンでオンになります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone automatic prompt for file downloads (Internet Explorer の制限付きゾーンでのファイルのダウンロードに対する自動プロンプト)**  
  このポリシー設定を使用すると、ファイルのダウンロードがユーザー以外によって開始されたときにユーザーにメッセージを表示するかどうかを管理できます。 この設定に関係なく、ユーザーによってダウンロードが開始された場合はファイル ダウンロードのダイアログが表示されます。 この設定を有効にすると、ダウンロードが自動的に試行されたときにファイル ダウンロードのダイアログが表示されます。 この設定を無効にした場合、または構成しなかった場合は、ユーザー以外によって開始されたファイルのダウンロードはブロックされ、ファイル ダウンロードのダイアログの代わりに通知バーがユーザーに表示されます。 その後、ユーザーは通知バーをクリックしてファイル ダウンロードのダイアログ表示を許可できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **既定値**: 無効
  
- **Internet Explorer internet zone .NET Framework reliant components (Internet Explorer のインターネット ゾーンでの .NET Framework 依存コンポーネント)**  
  このポリシー設定を使用すると、Authenticode を使用して署名されている .NET Framework コンポーネントを Internet Explorer から実行できるかどうかを管理できます。 これらのコンポーネントには、object タグから参照された管理されたコントロール、リンクから参照された管理された実行可能ファイルなどが含まれます。 このポリシー設定を有効にすると、Internet Explorer は署名されていない管理されたコンポーネントを実行します。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名されていない管理されたコンポーネントを実行するかどうかを確認するメッセージが Internet Explorer によって表示されます。 このポリシー設定を無効にすると、Internet Explorer は署名済みではない管理されたコンポーネントを実行しません。 このポリシー設定を構成しない場合は、Internet Explorer は署名済みではない管理されたコンポーネントを実行します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls (Internet Explorer のインターネット ゾーンで承認済みドメインにのみ tdc ActiveX コントロールを使用できるようにする)**  
  このポリシー設定では、Web サイト上でユーザーが TDC ActiveX コントロールを実行できるようにするかどうかを制御します。 このポリシー設定を有効にすると、TDC ActiveX コントロールはこのゾーン内の Web サイトから実行されません。 このポリシー設定を無効にすると、TDC Active X コントロールがこのゾーンのすべてのサイトから実行されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **既定値**: 有効 
  
- **Internet Explorer restricted zone script initiated windows (Internet Explorer の制限付きゾーンのスクリプトによって開かれるウィンドウ)**  
  このポリシー設定を使用すると、スクリプトによって起動されるポップアップ ウィンドウ、およびタイトルとステータス バーを持ったウィンドウの制限を管理できます。 このポリシー設定を有効にすると、Windows Restrictions セキュリティはこのゾーンでは適用されません。 セキュリティ ゾーンは、この機能で提供されるセキュリティの追加のレイヤーなしに実行されます。 このポリシー設定を無効にすると、スクリプトによって起動されたポップアップ ウィンドウや、タイトルとステータス バーを含むウィンドウに含まれる、危害を及ぼす可能性のある動作は実行されません。 この Internet Explorer のセキュリティ機能は、プロセスの [スクリプト化されたウィンドウのセキュリティ制限] 機能コントロール設定で指定されたように、このゾーンでオンになります。 このポリシー設定を構成しないと、スクリプトによって起動されたポップアップ ウィンドウや、タイトルとステータス バーを含むウィンドウに含まれる、危害を及ぼす可能性のある動作は実行されません。 この Internet Explorer のセキュリティ機能は、プロセスの [スクリプト化されたウィンドウのセキュリティ制限] 機能コントロール設定で指定されたように、このゾーンでオンになります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **既定値**: 無効 
  
- **Internet Explorer internet zone include local path when uploading files to server (Internet Explorer のインターネット ゾーンでサーバーへのファイルのアップロード時にローカル パスを含める)**  
  このポリシー設定では、ユーザーが HTML フォーム経由でファイルをアップロードするときに、ローカル パス情報が送信されるかどうかが制御されます。 ローカル パス情報が送信された場合、意図せずに、一部の情報がサーバーに公開されることがあります。 たとえば、ユーザーのデスクトップから送信されたファイルに、パスの一部としてユーザー名が含まれている可能性があります。 このポリシー設定を有効にすると、ユーザーが HTML フォーム経由でファイルをアップロードするときに、パス情報が送信されます。 このポリシー設定を無効にすると、ユーザーが HTML フォーム経由でファイルをアップロードするときに、パス情報は削除されます。 このポリシー設定を構成しないと、ユーザーは、HTML フォーム経由でファイルをアップロードするときに、パス情報を送信するかどうかを選択できます。 既定では、パス情報は送信されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **既定値**: 無効 
  
- **Internet Explorer disable processes in enhanced protected mode (Internet Explorer の拡張保護モードでプロセスを無効にする)**  
  このポリシー設定では、64 ビット バージョンの Windows の拡張保護モードで実行しているときに Internet Explorer 11 で (セキュリティの向上を目的として) 64 ビット プロセスを使用するか、または (互換性の向上を目的として) 32 ビット プロセスを使用するかを決定します。 重要: 64 ビット プロセスを使用する場合、一部の ActiveX コントロールおよびツール バーが使用できなくなる可能性があります。 このポリシー設定を有効にすると、64 ビット バージョンの Windows の拡張保護モードで実行しているときに Internet Explorer 11 で 64 ビット タブ プロセスを使用します。 このポリシー設定を無効にすると、64 ビット バージョンの Windows の拡張保護モードで実行しているときに Internet Explorer 11 で 32 ビット タブ プロセスを使用します。 このポリシー設定を構成しない場合、ユーザーは、Internet Explorer の設定を使用して、この機能の有効と無効を切り替えることができます。 この機能は既定で無効になっています。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **既定値**: 有効 
  
- **Internet Explorer ignore certificate errors (Internet Explorer で証明書エラーを無視する)**  
  このポリシー設定は、Internet Explorer での閲覧を妨げる Secure Sockets Layer/トランスポート層セキュリティ (SSL/TLS) 証明書エラー (期限切れ、失効、名前の不一致などのエラー) をユーザーが無視できないようにします。 このポリシー設定を有効にすると、ユーザーは閲覧を継続できません。 このポリシー設定を無効にするか、構成しない場合、ユーザーは証明書エラーを無視して閲覧を継続できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **既定値**: 無効 
  
- **Internet Explorer internet zone loading of XAML files (Internet Explorer のインターネット ゾーンでの XAML ファイルの読み込み)**  
  このポリシー設定を使用すると、Extensible Application Markup Language (XAML) ファイルの読み込みを管理できます。 XAML は、XML をベースにした宣言型マークアップ言語であり、Windows Presentation Foundation を活用した高度なユーザー インターフェイスやグラフィックスを作成するために一般に使用されます。 このポリシー設定を有効にして、ドロップダウン ボックスで [有効にする] を選択した場合、XAML ファイルは Internet Explorer 内で自動的に読み込まれます。 ユーザーはこの動作を変更できません。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、XAML ファイルを読み込むかどうかを確認するダイアログが表示されます。 このポリシー設定を無効にすると、XAML ファイルは Internet Explorer 内で読み込まれません。 ユーザーはこの動作を変更できません。 このポリシー設定を構成しなかった場合、ユーザーは XAML ファイルを Internet Explorer 内で読み込むかどうかを選択できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer internet zone automatic prompt for file downloads (Internet Explorer のインターネット ゾーンでのファイルのダウンロードに対する自動プロンプト)**  
  このポリシー設定を使用すると、ファイルのダウンロードがユーザー以外によって開始されたときにユーザーにメッセージを表示するかどうかを管理できます。 この設定に関係なく、ユーザーによってダウンロードが開始された場合はファイル ダウンロードのダイアログが表示されます。 この設定を有効にすると、ダウンロードが自動的に試行されたときにファイル ダウンロードのダイアログが表示されます。 この設定を無効にした場合、または構成しなかった場合は、ユーザー以外によって開始されたファイルのダウンロードはブロックされ、ファイル ダウンロードのダイアログの代わりに通知バーがユーザーに表示されます。 その後、ユーザーは通知バーをクリックしてファイル ダウンロードのダイアログ表示を許可できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **既定値**: 無効  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files (Internet Explorer の制限付きゾーンでの安全でない可能性があるファイルに対するセキュリティ警告)**  
  このポリシー設定では、ユーザーが (たとえば、エクスプローラーを使用してイントラネット ファイル共有から) 実行可能ファイルまたはその他の安全でない可能性があるファイルを開こうとしたときに、"ファイルを開く - セキュリティ警告" というメッセージが表示されるかどうかを制御します。 このポリシー設定を有効にして、ドロップダウン ボックスで [有効にする] を選択した場合、そうしたファイルを開くときにセキュリティ警告は表示されません。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、ファイルを開く前にセキュリティ警告が表示されます。 このポリシー設定を無効にした場合、そうしたファイルは開きません。 このポリシー設定を構成しなかった場合、ユーザーがそうしたファイルの処理方法を構成できます。 既定では、そうしたファイルは制限付きゾーンではブロックされ、イントラネットおよびローカル コンピューター ゾーンでは有効になり、インターネットおよび信頼済みゾーンではダイアログを表示するように設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer internet zone cross site scripting filter (Internet Explorer のインターネット ゾーンのクロスサイト スクリプト フィルター)**  
  このポリシーでは、クロスサイト スクリプト (XSS) フィルターがこのゾーン内の Web サイトにあるクロスサイト スクリプト インジェクションを検出して防止するかどうかを制御します。 このポリシー設定を有効にすると、XSS フィルターはこのゾーン内のサイトに対して有効になり、クロスサイト スクリプト インジェクションのブロックを試みます。 このポリシー設定を無効にすると、XSS フィルターはこのゾーン内のサイトに対して無効となり、Internet Explorer ではクロスサイト スクリプト インジェクションが許可されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **既定値**: 有効 
  
- **Internet Explorer fallback to SSL3 (Internet Explorer の SSL3 へのフォールバック)**  
  このポリシー設定を使用すると、SSL 3.0 への安全ではないフォールバックをブロックできます。 このポリシーが有効な場合、Internet Explorer では TLS 1.0 以降が失敗すると SSL 3.0 以前を使用してサイトへの接続を試行します。 中間者攻撃を防ぐために、安全でないフォールバックを許可しないことをお勧めします。 このポリシーは、どのセキュリティ プロトコルが有効になっているかには影響しません。 このポリシー設定を無効にすると、システムの既定値が使用されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **既定値**: サイトなし  

- **Internet Explorer の暗号化のサポート**  
  このポリシー設定では、ブラウザーで Transport Layer Security (TLS) 1.0、TLS 1.1、TLS 1.2、Secure Sockets Layer (SSL) 2.0、または SSL 3.0 のサポートを無効にできます。 TLS と SSL は、ブラウザーとターゲット サーバー間の通信を保護するのに役立つプロトコルです。 ブラウザーがターゲット サーバーとの保護された通信を設定しようとすると、ブラウザーとサーバーは使用するプロトコルとバージョンについてネゴシエートします。 ブラウザーとサーバーは、サポートするプロトコルとバージョンに関する互いの一覧を照らし合わせ、最善の組み合わせを選択します。 このポリシー設定を有効にした場合、ブラウザーは、ユーザーがドロップダウン リストから選択した暗号化方法を使用して暗号トンネルをネゴシエートするときとしないときがあります。 このポリシー設定を無効にするか構成しない場合、ユーザーはブラウザーがサポートする暗号化方法を選択できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067057)

  **既定値**: 2 項目: tls V1.1 および tls v1.0  
  *下矢印を選択すると、この設定で選択できるオプションが表示されます。*
  
- **Internet Explorer locked down internet zone smart screen (Internet Explorer のロックダウンされたインターネット ゾーンでのスマート スクリーン)**  
  このポリシー設定では、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。 このポリシー設定を有効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンします。 このポリシー設定を無効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンしません。 このポリシー設定を構成しない場合、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかをユーザーが選択できます。 注: Internet Explorer 7 の場合、このポリシー設定では、フィッシング詐欺検出機能がこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **既定値**: 有効 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame (Internet Explorer の制限付きゾーンで iFrame のアプリケーションとファイルを起動する)**  
  このポリシー設定を使用すると、このゾーン内のページの HTML にある IFRAME 参照からアプリケーションを実行したりファイルをダウンロードしたりすることができるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、このゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、このゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりするかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーがこのゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりすることはできません。 このポリシー設定を構成しない場合は、ユーザーがこのゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりすることはできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer での一般的ではないファイルに関するスマート スクリーン警告のバイパス**  
  このポリシー設定では、ユーザーが SmartScreen フィルター機能からの警告をバイパスできるかどうかを決定します。 SmartScreen フィルター機能では、ダウンロードしたユーザー数が少ない実行可能ファイルについてユーザーに警告します。 このポリシー設定を有効にすると、ユーザーは SmartScreen フィルター機能の警告によってブロックされます。 このポリシー設定を無効にした場合、または構成しなかった場合、ユーザーは SmartScreen フィルター機能の警告をバイパスできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **既定値**: 無効  
  
- **Internet Explorer internet zone popup blocker (Internet Explorer のインターネット ゾーンのポップアップ ブロッカー)**  
  このポリシー設定を使用すると、不要なポップアップ ウィンドウが表示されるかどうかを管理できます。 エンド ユーザーがリンクをクリックしたときに開かれるポップアップ ウィンドウはブロックされません。 このポリシー設定を有効にすると、不要なポップアップ ウィンドウは表示されません。 このポリシー設定を無効にすると、ポップアップ ウィンドウの表示は禁止されません。 このポリシー設定を構成しない場合は、不要なポップアップ ウィンドウは表示されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **既定値**: 有効にする  
  
- **Internet Explorer processes consistent MIME handling (Internet Explorer での一貫性のある MIME 処理)**  
  Internet Explorer には動的なバイナリ ビヘイビアー (動作が関連付けられている HTML 要素のための特定の機能をカプセル化するコンポーネント) が含まれます。 このポリシー設定はバイナリ ビヘイビアーのセキュリティの制限の設定を許可するかまたは使用不可にするかを制御します。 このポリシー設定を有効にすると、バイナリ ビヘイビアーはエクスプローラーおよび Internet Explorer のプロセスでは使用不可になります。 このポリシー設定を無効にすると、バイナリ ビヘイビアーはエクスプローラーおよび Internet Explorer のプロセスで許可されます。 このポリシー設定を構成しない場合は、バイナリ ビヘイビアーはエクスプローラーおよび Internet Explorer のプロセスでは使用不可になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **既定値**: 有効  
  
- **Internet Explorer の制限付きゾーンの Java のアクセス許可**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しなかった場合、Java アプレットは無効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **既定値**: Java を無効にする  
    
  
- **Internet Explorer Active X controls in protected mode (Internet Explorer の保護モードでの ActiveX コントロール)**  
  このポリシー設定を使用すると、拡張保護モードが有効になっている場合に保護モードで ActiveX コントロールを実行できなくなります。 拡張保護モードと互換性がない ActiveX コントロールがインストールされ、Web サイトがそのコントロールの読み込みを試行した場合、Internet Explorer によってユーザーに通知が行われ、Web サイトを通常の保護モードで実行するためのオプションが表示されます。 本ポリシー設定を使用すると、この通知が無効になり、すべての Web サイトが拡張保護モードで実行されるようになります。 拡張保護モードでは、64 ビット バージョンの Windows で 64 ビット プロセスが使用され、悪意のある Web サイトに対する保護が強化されています。 Windows 8 以降が実行されているコンピューターでは、拡張保護モードによって、Internet Explorer が読み取り元に設定できる場所もレジストリとファイル システムに制限されています。 拡張保護モードが有効になっていて、拡張保護モードと互換性がない ActiveX コントロールの読み込みを試行する Web サイトをユーザーが表示しようとした場合は、Internet Explorer によってユーザーに通知が行われ、その Web サイトで拡張保護モードを無効にするためのオプションが表示されます。 このポリシー設定を有効にすると、拡張保護モードを無効にするオプションは Internet Explorer でユーザーに表示されなくなります。 保護モードの Web サイトはすべて、拡張保護モードで実行されます。 このポリシー設定を無効にした場合、または構成しない場合は、Internet Explorer によってユーザーに通知が行われ、互換性がない ActiveX コントロールが含まれている Web サイトを通常の保護モードで実行するためのオプションが表示されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **既定値**: 無効  
  
- **Internet Explorer restricted zone loading of XAML files (Internet Explorer の制限付きゾーンでの XAML ファイルの読み込み)**  
  このポリシー設定を使用すると、Extensible Application Markup Language (XAML) ファイルの読み込みを管理できます。 XAML は、XML をベースにした宣言型マークアップ言語であり、Windows Presentation Foundation を活用した高度なユーザー インターフェイスやグラフィックスを作成するために一般に使用されます。 このポリシー設定を有効にして、ドロップダウン ボックスで [有効にする] を選択した場合、XAML ファイルは Internet Explorer 内で自動的に読み込まれます。 ユーザーはこの動作を変更できません。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、XAML ファイルを読み込むかどうかを確認するダイアログが表示されます。 このポリシー設定を無効にすると、XAML ファイルは Internet Explorer 内で読み込まれません。 ユーザーはこの動作を変更できません。 このポリシー設定を構成しなかった場合、ユーザーは XAML ファイルを Internet Explorer 内で読み込むかどうかを選択できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer processes scripted window security restrictions (Internet Explorer プロセスでのスクリプト化されたウィンドウのセキュリティ制限)**  
  Internet Explorer は、スクリプトがプログラムを使ってさまざまな種類のウィンドウを開いたり、ウィンドウのサイズや場所を変更したりすることを許可しています。 ウィンドウ制限のセキュリティ機能は、ポップアップ ウィンドウを制限し、スクリプトがタイトル バーやステータス バーがユーザーに表示されないウィンドウ、または Windows の他のタイトル バーやステータス バーと混乱するようなウィンドウを表示することを禁止します。 このポリシー設定を有効にすると、スクリプト化されたウィンドウはすべてのプロセスで制限されます。 このポリシー設定を無効にするか、または構成しない場合は、スクリプト化されたウィンドウには制限は適用されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **既定値**: 有効   
  
- **Internet Explorer restricted zone run Active X controls and plugins (Internet Explorer の制限付きゾーンで Active X コントロールおよびプラグインを実行する)**  
  このポリシー設定を使用すると、指定されたゾーンのページ上で ActiveX コントロールおよびプラグインが実行できるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、コントロールやプラグインを実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、コントロールやプラグインの実行を許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、コントロールとプラグインは実行されません。 このポリシー設定を構成しない場合は、コントロールとプラグインは実行されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting (Internet Explorer の制限付きゾーンでスクリプトを実行しても安全であるとマークされた Active X コントロールをスクリプト化する)**  
  このポリシー設定を使用すると、スクリプトを実行しても安全であるとマークされた ActiveX コントロールがスクリプトと対話できるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、スクリプトの対話を自動的に実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、スクリプトの対話を許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、スクリプトの対話は実行されません。 このポリシー設定を構成しない場合は、スクリプトの対話は実行されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone logon options (Internet Explorer の制限付きゾーンのログオン オプション)**  
  このポリシー設定を使用すると、サインイン オプションの設定を管理できます。 このポリシー設定を有効にすると、次のサインイン オプションから選択できます。 
  - *匿名* - HTTP 認証を無効にして、Common Internet File System (CIFS) プロトコル用にのみ guest アカウントを使用する場合は、匿名サインインを使用します。 
  - *プロンプト* - ユーザーの ID とパスワードを照会するために、ユーザー名とパスワードの入力を求めます。 ユーザーが照会された後に、これらの値は残りのセッションで警告なしに使用されます。 
  - *イントラネット ゾーンでのみ自動的にサインインする* - 他のゾーンでのユーザー ID とパスワードをユーザーに照会するには、このオプションを使用します。 ユーザーが照会された後に、これらの値は残りのセッションで警告なしに使用されます。 
  - *現在のユーザー名とパスワードで自動的にサインインする* - Windows NT チャレンジ応答 (別名 NTLM 認証) を使用してログオンを試みるには、このオプションを使用します。 サーバーで Windows NT チャレンジ応答がサポートされている場合、サインインでは、ユーザーのサインイン用のネットワーク ユーザー名とパスワードが使用されます。 サーバーで Windows NT チャレンジ応答がサポートされていない場合、ユーザーはユーザー名とパスワードを提供する必要があります。 

  このポリシー設定を無効にすると、サインインは "*イントラネット ゾーンでのみ自動的にサインインする*" に設定されます。 このポリシー設定を構成しなかった場合、サインインは "*プロンプト*" に設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **既定値**: 匿名  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe (Internet Explorer の信頼済みゾーンで安全であるとマークされていない Active X コントロールを初期化およびスクリプト化する)**  
  このポリシー設定を使用すると、安全であるとマークされていない ActiveX コントロールを管理できます。 このポリシー設定を有効にすると、ActiveX コントロールがパラメーターを読み込んで実行され、また、信頼されていないデータまたはスクリプトに対するオブジェクトの安全性を設定することなくスクリプト化されます。 この設定は、安全でかつ管理されたゾーン以外では推奨しません。 この設定では、安全なコントロールと安全ではないコントロールの両方を初期化およびスクリプト化します。[スクリプトを実行しても安全だとマークされている ActiveX コントロールのスクリプトの実行] オプションは無視されます。 このポリシー設定を有効にして、ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、コントロールにパラメーターを読み込んだりスクリプト化したりすることを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。 このポリシー設定を構成しなかった場合、コントロールにパラメーターを読み込んだりスクリプト化したりするかどうかをユーザーにたずねます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer check server certificate revocation (Internet Explorer でサーバー証明書の失効状態を確認する)**  
  このポリシー設定を使うと、サーバーの証明書の失効状態を確認するかどうかを管理できます。 証明書は、危害を受けたか、有効ではなくなった場合に失効されます。このオプションを使うと、詐欺目的であるか、安全ではない可能性があるサイトにユーザーが機密データを送信するのを防ぐことができます。 このポリシー設定を有効にすると、サーバーの証明書が失効したかどうかが確認されます。 このポリシー設定を無効にすると、サーバーの証明書が失効したかどうかが確認されません。 このポリシー設定を構成しなかった場合、サーバーの証明書が失効したかどうかが確認されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **既定値**: 有効 
  
- **Internet Explorer internet zone less privileged sites (Internet Explorer のインターネット ゾーンのより権限の少ないサイト)**  
  このポリシー設定を使用すると、制限付きサイト ゾーンなどのより特権が低いゾーンにある Web サイトがこのゾーンに移動できるかどうかを管理できます。 このポリシー設定を有効にすると、より権限の少ないゾーンの Web サイトがこのゾーンで新しいウィンドウを開いたり、このゾーンに移動したりできます。 セキュリティ ゾーンは、[ゾーン昇格からの保護] のセキュリティ機能で提供されるセキュリティの追加のレイヤーなしに実行されます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、危険を及ぼす可能性のあるナビゲーションが実行されるときにユーザーに警告が表示されます。 このポリシー設定を無効にすると、危害を及ぼす可能性のあるナビゲーションは禁止されます。 Internet Explorer のセキュリティ機能は、[ゾーン昇格からの保護] 機能コントロールで設定されているように、このゾーンでオンになります。 このポリシー設定を構成しない場合は、より権限の少ないゾーンの Web サイトがこのゾーンで新しいウィンドウを開いたり、このゾーンに移動したりできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone file downloads (Internet Explorer の制限付きゾーンでのファイルのダウンロード)**  
  このポリシー設定を使用すると、ゾーンからのファイルのダウンロードが許可されるかどうかを管理できます。 このオプションは、ファイルの配信元のゾーンではなく、ダウンロードを開始するリンクがあるページのゾーンによって決定されます。 このポリシー設定を有効にすると、ゾーンからファイルをダウンロードできます。 このポリシー設定を無効にすると、ゾーンからファイルをダウンロードできません。 このポリシー設定を構成しない場合は、ゾーンからファイルをダウンロードできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode (Internet Explorer のインターネット ゾーンで Authenticode 署名済みの .NET Framework 依存コンポーネントを実行する)**  
  このポリシー設定を使用すると、Authenticode を使用して署名されている .NET Framework コンポーネントを Internet Explorer から実行できるかどうかを管理できます。 これらのコンポーネントには、object タグから参照された管理されたコントロール、リンクから参照された管理された実行可能ファイルなどが含まれます。 このポリシー設定を有効にすると、Internet Explorer は署名済みの管理されたコンポーネントを実行します。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名済みの管理されたコンポーネントを実行するかどうかを確認するメッセージが Internet Explorer によって表示されます。 このポリシー設定を無効にすると、Internet Explorer は署名済みの管理されたコンポーネントを実行しません。 このポリシー設定を構成しない場合は、Internet Explorer は署名済みの管理されたコンポーネントを実行します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer でユーザーごとに ActiveX コントロールをインストールできないようにする**  
  このポリシー設定では、ActiveX コントロールをユーザーごとにインストールできないようにできます。 このポリシー設定を有効にすると、ActiveX コントロールはユーザーごとにインストールできなくなります。 このポリシー設定を無効にするか構成しないと、ActiveX コントロールはユーザーごとにインストールできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **既定値**: 有効  
  
- **Internet Explorer prevent managing smart screen filter (Internet Explorer でスマート スクリーン フィルターを管理できないようにする)**  
  このポリシー設定は、ユーザーが SmartScreen フィルターを管理できないようにします。SmartScreen フィルターを有効にすると、"フィッシング" を通じて個人情報を不正に収集することがわかっている Web サイト、または悪意のあるソフトウェアをホストしていることがわかっている Web サイトにアクセスしようとすると警告が表示されます。 このポリシー設定を有効にすると、ユーザーには、SmartScreen フィルターを有効にするためのダイアログは表示されません。 フィルターの許可リストに含まれない Web サイトのアドレスはすべて Microsoft に自動的に送信され、ユーザーにはダイアログは表示されません。 このポリシー設定を無効にするか、構成しない場合、ユーザーには、初回実行時に SmartScreen フィルターを有効にするかどうかを選択するためのダイアログが表示されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **既定値**: 有効にする  
  
- **Internet Explorer processes MIME sniffing safety feature (Internet Explorer プロセスでの MIME スニッフィングの安全機能)**  
  このポリシー設定は、ある種類のファイルをより危険な種類のファイルに昇格することを Internet Explorer MIME スニッフィングが防止するかどうかを決定します。 このポリシー設定を有効にすると、MIME スニッフィングは、ある種類のファイルをより危険な種類に昇格することはありません。 このポリシー設定を無効にすると、Internet Explorer プロセスで、MIME スニッフィングがファイルをより危険な種類に昇格することは許可されます。 このポリシー設定を構成しない場合は、MIME スニッフィングは、ある種類のファイルをより危険な種類に昇格することはありません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **既定値**: 有効  
  
- **Internet Explorer restricted zone download signed Active X controls (Internet Explorer の制限付きゾーンで署名された Active X コントロールをダウンロードする)**  
  このポリシー設定を使用すると、ユーザーがゾーンにあるページから署名された ActiveX コントロールをダウンロードすることを許可するかどうかを管理できます。 このポリシーを有効にすると、ユーザーによる手動操作を必要とすることなく、署名されたコントロールをダウンロードできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、信頼されていない発行元によって署名されたコントロールをダウンロードするかどうかをユーザーにたずねます。 信頼されている発行元によって署名されたコードは警告なしにダウンロードされます。 このポリシー設定を無効にすると、署名されたコントロールはダウンロードできません。 このポリシー設定を構成しない場合は、信頼されていない発行元によって署名されたコントロールをダウンロードするかどうかをユーザーにたずねます。 信頼されている発行元によって署名されたコードは警告なしにダウンロードされます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **既定値**: 無効にする  
  
- **Internet Explorer auto complete (Internet Explorer のオート コンプリート)**  
  このオートコンプリート機能では、フォーム上のユーザー名とパスワードを記憶して、候補を表示できます。 この設定を有効にすると、ユーザーは [フォームのユーザー名およびパスワード] や [パスワードを保存する確認をする] のオプションを変更できません。 フォームのユーザー名とパスワードのオートコンプリート機能は有効になります。 管理者は、[パスワードを保存する確認をする] オプションを選択するかどうかを決定する必要があります。 この設定を無効にすると、ユーザーは [フォームのユーザー名およびパスワード] や [パスワードを保存する確認をする] を変更できません。 フォームのユーザー名とパスワードのオートコンプリート機能は無効になります。 ユーザーは、パスワードの保存を確認するように選択することもできません。 この設定を構成しない場合、ユーザーは、[フォームのユーザー名およびパスワード] や [パスワードを保存する確認をする] のオプションを有効にすることができます。 このオプションを表示するには、ユーザーは [インターネット オプション] ダイアログ ボックスを開いて、[コンテンツ] タブ、[設定] ボタンの順にクリックします。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **既定値**: 無効  
  
- **Internet Explorer internet zone allow VBscript to run (Internet Explorer のインターネット ゾーンで VB スクリプトの実行を許可する)**  
  このポリシー設定では、VB スクリプトが特定の Internet Explorer のゾーンでページを実行できるかどうかを決定できます。 次のオプションがあります。 
  - "*有効*" - 対話式の操作を行くことなく、VB スクリプトが特定のゾーンのページ上で実行されます。 
  - "*プロンプト*" - 従業員は VB スクリプトをそのゾーンで実行できるようにするかどうかを確認されます。 
  - "*無効*" - VB スクリプトはそのゾーンで実行できないようにされます。 このポリシー設定を無効にした場合、または構成しない場合は、VBScript は特定のゾーンで対話式の操作を行くことなく実行されます。    

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls (Internet Explorer の制限付きゾーンで承認済みドメインのみ TDC Active X コントロールを使用できるようにする)**  
  このポリシー設定では、Web サイト上でユーザーが TDC ActiveX コントロールを実行できるようにするかどうかを制御します。 このポリシー設定を有効にすると、TDC ActiveX コントロールはこのゾーン内の Web サイトから実行されません。 このポリシー設定を無効にすると、TDC Active X コントロールがこのゾーンのすべてのサイトから実行されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **既定値**: 有効  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls (Internet Explorer の信頼済みゾーンで Active X コントロールに対してマルウェア対策を実行しない)**  
  このポリシー設定では、ActiveX コントロールをページに読み込んでも安全かどうかを調べるために Internet Explorer がマルウェア対策プログラムを実行するかどうかを決定します。 このポリシー設定を有効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 このポリシー設定を無効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 このポリシー設定を構成しない場合、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 ユーザーは、Internet Explorer の [セキュリティ] 設定を使用して、この動作の有効と無効を切り替えることができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **既定値**: 無効 
  
- **Internet Explorer local machine zone java permissions (Internet Explorer のローカル コンピューター ゾーンでの Java のアクセス許可)**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しない場合は、アクセス許可は [安全性 - 中] に設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **既定値**: Java を無効にする 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls (Internet Explorer のイントラネット ゾーンで Active X コントロールに対してマルウェア対策を実行しない)**  
  このポリシー設定では、ActiveX コントロールをページに読み込んでも安全かどうかを調べるために Internet Explorer がマルウェア対策プログラムを実行するかどうかを決定します。 このポリシー設定を有効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 このポリシー設定を無効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 このポリシー設定を構成しない場合、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 ユーザーは、Internet Explorer の [セキュリティ] 設定を使用して、この動作の有効と無効を切り替えることができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **既定値**: 無効  

- **Internet Explorer restricted zone scriptlets (Internet Explorer の制限付きゾーンのスクリプトレット)**  
  このポリシー設定を使用すると、ユーザーがスクリプトレットを実行できるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーはスクリプトレットを実行できます。 このポリシー設定を無効にすると、ユーザーはスクリプトレットを実行できません。 このポリシー設定を構成しなかった場合、ユーザーはスクリプトレットを有効または無効にできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **既定値**: 無効  
  
- **Internet Explorer processes notification bar (Internet Explorer プロセスの通知バー)**  
  このポリシー設定を使うと、ファイルやコードのインストールが制限されている場合に、Internet Explorer プロセスに対して通知バーを表示するかどうかを管理できます。 既定では、通知バーは Internet Explorer プロセスに対して表示されます。 このポリシー設定を有効にすると、通知バーは Internet Explorer プロセスに対して表示されます。 このポリシー設定を無効にすると、通知バーは Internet Explorer プロセスに対して表示されません。 このポリシー設定を構成しない場合は、通知バーは Internet Explorer プロセスに対して表示されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **既定値**: 有効  
  
- **Internet Explorer internet zone download signed ActiveX controls (Internet Explorer のインターネット ゾーンで署名された Active X コントロールをダウンロードする)**  
  このポリシー設定を使用すると、ユーザーがゾーンにあるページから署名された ActiveX コントロールをダウンロードすることを許可するかどうかを管理できます。 このポリシーを有効にすると、ユーザーによる手動操作を必要とすることなく、署名されたコントロールをダウンロードできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、信頼されていない発行元によって署名されたコントロールをダウンロードするかどうかをユーザーにたずねます。 信頼されている発行元によって署名されたコードは警告なしにダウンロードされます。 このポリシー設定を無効にすると、署名されたコントロールはダウンロードできません。 このポリシー設定を構成しない場合は、信頼されていない発行元によって署名されたコントロールをダウンロードするかどうかをユーザーにたずねます。 信頼されている発行元によって署名されたコードは警告なしにダウンロードされます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone smart screen (Internet Explorer の制限付きゾーンのスマート スクリーン)**  
  このポリシー設定では、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。 このポリシー設定を有効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンします。 このポリシー設定を無効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンしません。 このポリシー設定を構成しない場合、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかをユーザーが選択できます。 注: Internet Explorer 7 の場合、このポリシー設定では、フィッシング詐欺検出機能がこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **既定値**: 有効  
  
- **Internet Explorer remove run this time button for outdated Active X controls (Internet Explorer で古い Active X コントロール用の [今回は実行] ボタンを削除する)**  
  このポリシー設定を使用すると、Internet Explorer で [今回は実行] ボタンが表示されないようにして、ユーザーが特定の古い ActiveX コントロールを実行できないようにすることができます。 このポリシー設定を有効にした場合、Internet Explorer で古い ActiveX コントロールがブロックされるときに表示される警告メッセージに [今回は実行] ボタンが表示されなくなります。 このポリシー設定を無効にした場合、または構成しなかった場合、Internet Explorer で古い ActiveX コントロールがブロックされるときに表示される警告メッセージに [今回は実行] ボタンが表示されます。 このボタンをクリックすると、ユーザーは古い ActiveX コントロールを 1 回実行できます。 詳細については、Internet Explorer TechNet ライブラリの古い ActiveX コントロールに関するページを参照してください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **既定値**: 有効 
  
- **Internet Explorer internet zone launch applications and files in an iframe (Internet Explorer のインターネット ゾーンで IFRAME のアプリケーションとファイルを起動する)**  
  このポリシー設定を使用すると、このゾーン内のページの HTML にある IFRAME 参照からアプリケーションを実行したりファイルをダウンロードしたりすることができるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、このゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、このゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりするかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーがこのゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりすることはできません。 このポリシー設定を構成しない場合は、このゾーンにあるページ上の IFRAME からアプリケーションを実行したりファイルをダウンロードしたりするかどうかをユーザーにたずねます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains (Internet Explorer の制限付きゾーンで異なるドメインを超えてウィンドウとフレームを移動する)**  
  このポリシー設定により、移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグするオプションを設定できます。 このポリシー設定を有効にして [有効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウにある場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。 このポリシー設定を有効にして [無効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウにある場合、あるドメインから別のドメインにコンテンツをドラッグできません。 この設定はユーザーが変更できません。 Internet Explorer 10 では、このポリシー設定を無効にする場合、または構成しない場合、[有効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグできません。 ユーザーは、[インターネット オプション] ダイアログでこの設定を変更できます。 Internet Explorer 9 以前のバージョンでは、このポリシーを無効にする場合、または構成しない場合は、ユーザーは移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer internet zone smart screen (Internet Explorer のインターネット ゾーンのスマート スクリーン)**  
  このポリシー設定では、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。 このポリシー設定を有効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンします。 このポリシー設定を無効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンしません。 このポリシー設定を構成しない場合、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかをユーザーが選択できます。 注: Internet Explorer 7 の場合、このポリシー設定では、フィッシング詐欺検出機能がこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **既定値**: 有効  
  
- **Internet Explorer locked down trusted zone java permissions (Internet Explorer のロックダウンされた信頼済みゾーンでの Java のアクセス許可)**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しなかった場合、Java アプレットは無効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **既定値**: Java を無効にする 
  
- **Internet Explorer check signatures on downloaded programs (Internet Explorer でダウンロードされたプログラムの署名を確認する)**  
  このポリシー設定を使うと、実行可能プログラムをダウンロードする前に、(署名済みソフトウェアの発行者を識別し、変更や改ざんが行われていないことを確認する) デジタル署名をコンピューター上で確認するかどうかを管理できます。 このポリシー設定を有効にすると、コンピューターに実行可能プログラムをダウンロードする前に、プログラムのデジタル署名を確認し、識別情報を表示します。 このポリシー設定を無効にすると、コンピューターに実行可能プログラムをダウンロードする前に、プログラムのデジタル署名の確認や識別情報の表示を行いません。 このポリシー設定を構成しなかった場合、コンピューターに実行可能プログラムをダウンロードする前に、プログラムのデジタル署名の確認や識別情報の表示を行いません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **既定値**: 有効  
  
- **Internet Explorer restricted zone scripting of web browser controls (Internet Explorer の制限付きゾーンでの Web ブラウザー コントロールのスクリプト化)**  
  このポリシー設定では、ページで、スクリプトを使用して埋め込みの WebBrowser コントロールを制御できるかどうかを決定します。 このポリシー設定を有効にすると、WebBrowser コントロールへのスクリプト アクセスが許可されます。 このポリシー設定を無効にすると、WebBrowser コントロールへのスクリプト アクセスは許可されません。 このポリシー設定を構成しなかった場合、ユーザーは WebBrowser コントロールへのスクリプト アクセスを有効または無効にできます。 既定では、WebBrowser コントロールへのスクリプト アクセスは、ローカル コンピューターおよびイントラネット ゾーン内でのみ許可されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **既定値**: 無効  
  
- **Internet Explorer restricted zone cross site scripting filter (Internet Explorer の制限付きゾーンのクロスサイト スクリプト フィルター)**  
  このポリシーでは、クロスサイト スクリプト (XSS) フィルターがこのゾーン内の Web サイトにあるクロスサイト スクリプト インジェクションを検出して防止するかどうかを制御します。 このポリシー設定を有効にすると、XSS フィルターはこのゾーン内のサイトに対して有効になり、クロスサイト スクリプト インジェクションのブロックを試みます。 このポリシー設定を無効にすると、XSS フィルターはこのゾーン内のサイトに対して無効となり、Internet Explorer ではクロスサイト スクリプト インジェクションが許可されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **既定値**: 有効  
  
- **Internet Explorer restricted zone binary and script behaviors (Internet Explorer の制限付きゾーンでのバイナリ ビヘイビアーとスクリプト ビヘイビアー)**  
  このポリシー設定を使用すると、動的なバイナリ ビヘイビアーとスクリプト ビヘイビアー (動作が関連付けられた HTML 要素のための特定の機能をカプセル化するコンポーネント) を管理できます。 このポリシー設定を有効にすると、バイナリ ビヘイビアーとスクリプト ビヘイビアーを利用できます。 ドロップダウン ボックスで [管理者の許可済み] を選択した場合、[バイナリ ビヘイビアーのセキュリティの制限] ポリシーの管理者によって許可されたビヘイビアーに一覧表示されている動作のみ利用できます。 このポリシー設定を無効にした場合、アプリケーションがカスタムのセキュリティ マネージャーを実装していない限り、バイナリ ビヘイビアーとスクリプト ビヘイビアーは利用できません。 このポリシー設定を構成しない場合は、アプリケーションがカスタムのセキュリティ マネージャーを実装していない限り、バイナリ ビヘイビアーとスクリプト ビヘイビアーは利用できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer security settings check (Internet Explorer のセキュリティ設定のチェック)**  
  このポリシー設定は、セキュリティ設定チェック機能を無効にします。この機能は、Internet Explorer のセキュリティ設定をチェックして、Internet Explorer を危険にさらす設定が含まれていないか確認します。 このポリシー設定を有効にすると、機能は無効になります。 このポリシー設定を無効にするか、構成しない場合、機能は有効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **既定値**: 有効  
  
- **Internet Explorer internet zone security warning for potentially unsafe files (Internet Explorer のインターネット ゾーンでの安全でない可能性があるファイルに対するセキュリティ警告)**  
  このポリシー設定では、ユーザーが (たとえば、エクスプローラーを使用してイントラネット ファイル共有から) 実行可能ファイルまたはその他の安全でない可能性があるファイルを開こうとしたときに、"ファイルを開く - セキュリティ警告" というメッセージが表示されるかどうかを制御します。 このポリシー設定を有効にして、ドロップダウン ボックスで [有効にする] を選択した場合、そうしたファイルを開くときにセキュリティ警告は表示されません。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、ファイルを開く前にセキュリティ警告が表示されます。 このポリシー設定を無効にした場合、そうしたファイルは開きません。 このポリシー設定を構成しなかった場合、ユーザーがそうしたファイルの処理方法を構成できます。 既定では、そうしたファイルは制限付きゾーンではブロックされ、イントラネットおよびローカル コンピューター ゾーンでは有効になり、インターネットおよび信頼済みゾーンではダイアログを表示するように設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **既定値**: プロンプト  
  
- **Internet Explorer intranet zone java permissions (Internet Explorer のイントラネット ゾーンでの Java のアクセス許可)**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しない場合は、アクセス許可は [安全性 - 中] に設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **既定値**: 安全性 - 高 
  
- **Internet Explorer で古い Active X コントロールをブロックする**   
  このポリシー設定では、Internet Explorer で特定の古い ActiveX コントロールをブロックするかどうかを決定します。 イントラネット ゾーンでは、古い ActiveX コントロールがブロックされません。 このポリシー設定を有効にした場合、Internet Explorer では、古い ActiveX コントロールのブロックが停止します。 このポリシー設定を無効にした場合、または構成しなかった場合、Internet Explorer では、引き続き特定の古い ActiveX コントロールがブロックされます。 詳細については、Internet Explorer TechNet ライブラリの古い ActiveX コントロールに関するページを参照してください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **既定値**: 有効  
  
- **Internet Explorer restricted zone popup blocker (Internet Explorer の制限付きゾーンでのポップアップ ブロック)**  
  このポリシー設定を使用すると、不要なポップアップ ウィンドウが表示されるかどうかを管理できます。 エンド ユーザーがリンクをクリックしたときに開かれるポップアップ ウィンドウはブロックされません。 このポリシー設定を有効にすると、不要なポップアップ ウィンドウは表示されません。 このポリシー設定を無効にすると、ポップアップ ウィンドウの表示は禁止されません。 このポリシー設定を構成しない場合は、不要なポップアップ ウィンドウは表示されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **既定値**: 有効にする  
  
- **Internet Explorer processes MK protocol security restriction (Internet Explorer プロセスでの MK プロトコル セキュリティの制限)**  
  [MK プロトコル セキュリティの制限] ポリシー設定を使うと、MK プロトコルを使用不可にすることで危険を回避できます。 MK プロトコルでホストされているリソースはエラーになります。 このポリシー設定を有効にすると、エクスプローラーおよび Internet Explorer で MK プロトコルが使用不可になり、MK プロトコルでホストされているリソースはエラーになります。 このポリシー設定を無効にすると、アプリケーションは MK プロトコル API を使うことができます。 MK プロトコルでホストされているリソースは、エクスプローラーおよび Internet Explorer のプロセスで機能します。 このポリシー設定を構成しない場合は、エクスプローラーおよび Internet Explorer で MK プロトコルが使用不可になり、MK プロトコルでホストされているリソースはエラーになります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **既定値**: 有効  
  
- **Internet Explorer の信頼済みゾーンでの Java のアクセス許可**   
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しなかった場合、アクセス許可は [安全性 - 低] に設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **既定値**: 安全性 - 高  
  
- **Internet Explorer restricted zone scripting of java applets (Internet Explorer の制限付きゾーンでの Java アプレットのスクリプト化)**  
  このポリシー設定を使用すると、ゾーン内のスクリプトがアプレットにアクセスできるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、スクリプトはアプレットに自動的にアクセスできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、スクリプトがアプレットにアクセスすることを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、スクリプトはアプレットにアクセスできません。 このポリシー設定を構成しなかった場合、スクリプトはアプレットにアクセスできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer のロックダウンされた制限付きゾーンでの Java のアクセス許可**   
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しなかった場合、Java アプレットは無効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **既定値**: Java を無効にする 
  
- **Internet Explorer のインターネット ゾーンで承認済みドメインだけが ActiveX コントロールを使用できるようにする**   
  このポリシー設定では、ActiveX コントロールをインストールした Web サイト以外の Web サイトで ActiveX コントロールを実行する許可を求めるメッセージをユーザーに表示するかどうかを制御します。 このポリシー設定を有効にすると、このゾーン内の Web サイトで ActiveX コントロールが実行される前に、ユーザーにメッセージが表示されます。 ユーザーは、現在のサイトからのコントロールの実行を許可するか、すべてのサイトからのコントロールの実行を許可するかを選択できます。 このポリシー設定を無効にすると、ユーザーにはサイトごとの ActiveX 警告は表示されず、ActiveX コントロールはこのゾーン内のすべてのサイトから実行できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **既定値**: 有効  
  
- **Internet Explorer include all network paths (Internet Explorer ですべてのネットワーク パスを含める)**  
  Internet Explorer にはすべてのネットワーク パスが含まれます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **既定値**: 無効 
  
- **Internet Explorer internet zone protected mode (Internet Explorer のインターネット ゾーンの保護モード)**  
  このポリシー設定を使用すると、保護モードを有効にできます。 保護モードを使用すると、Internet Explorer が書き込むことができるレジストリやファイル システム内の場所を制限することで、脆弱点を悪用した攻撃から Internet Explorer を保護できます。 このポリシー設定を有効にすると、保護モードが有効になります。 ユーザーは保護モードを無効にできません。 このポリシー設定を無効にすると、保護モードが無効になります。 ユーザーは保護モードを有効にできません。 このポリシー設定を構成しなかった場合、ユーザーは保護モードを有効または無効にできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **既定値**: 有効にする 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe (Internet Explorer のインターネット ゾーンで安全であるとマークされていない Active X コントロールを初期化およびスクリプト化する)**  
  このポリシー設定を使用すると、安全であるとマークされていない ActiveX コントロールを管理できます。 このポリシー設定を有効にすると、ActiveX コントロールがパラメーターを読み込んで実行され、また、信頼されていないデータまたはスクリプトに対するオブジェクトの安全性を設定することなくスクリプト化されます。 この設定は、安全でかつ管理されたゾーン以外では推奨しません。 この設定では、安全なコントロールと安全ではないコントロールの両方を初期化およびスクリプト化します。[スクリプトを実行しても安全だとマークされている ActiveX コントロールのスクリプトの実行] オプションは無視されます。 このポリシー設定を有効にして、ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、コントロールにパラメーターを読み込んだりスクリプト化したりすることを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。 このポリシー設定を構成しなかった場合、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer のロックダウンされた制限付きゾーンでのスマート スクリーン**   
  このポリシー設定では、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。 このポリシー設定を有効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンします。 このポリシー設定を無効にすると、SmartScreen フィルターはこのゾーンのページの悪意のあるコンテンツをスキャンしません。 このポリシー設定を構成しない場合、SmartScreen フィルターがこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかをユーザーが選択できます。 注: Internet Explorer 7 の場合、このポリシー設定では、フィッシング詐欺検出機能がこのゾーンのページの悪意のあるコンテンツをスキャンするかどうかを制御します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **既定値**: 有効  
  
- **Internet Explorer crash detection (Internet Explorer のクラッシュの検出)**  
  このポリシー設定を使うと、アドオン管理のクラッシュ検出機能を管理できます。 このポリシー設定を有効にすると、Internet Explorer でクラッシュが起きた場合、Windows XP Professional Service Pack 1 またはそれ以前の場合と同様に、Windows エラー報告が起動されます。 Windows エラー報告のポリシー設定はすべて引き続き適用されます。 このポリシー設定を無効にするか、または構成しない場合は、アドオン管理のクラッシュ検出機能は動作します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **既定値**: 無効  
  
- **Internet Explorer internet zone java permissions (Internet Explorer のインターネット ゾーンでの Java のアクセス許可)**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しない場合は、アクセス許可は [安全性 - 高] に設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **既定値**: Java を無効にする  
  
- **Internet Explorer restricted zone active scripting (Internet Explorer の制限付きゾーンでのアクティブ スクリプティング)**  
  このポリシー設定を使用すると、ゾーンのページにあるスクリプト コードを実行するかどうかを管理できます。 このポリシー設定を有効にすると、ゾーン内のページ上のスクリプト コードを自動的に実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、ゾーン内のページ上のスクリプト コードの実行を許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ゾーンのページ上のスクリプト コードは実行されません。 このポリシー設定を構成しない場合は、ゾーンのページ上のスクリプト コードは実行されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer internet zone logon options (Internet Explorer のインターネット ゾーンのログオン オプション)**  
  このポリシー設定を使用すると、サインイン オプションの設定を管理できます。 このポリシー設定を有効にすると、次のサインイン オプションから選択できます。 HTTP 認証を無効にして、Common Internet File System (CIFS) プロトコル用にのみ guest アカウントを使用する場合は、[匿名ログオン] を選択してください。 ユーザーの ID とパスワードを照会するために、ユーザー名とパスワードの入力を求めます。 ユーザーが照会された後に、これらの値は残りのセッションで警告なしに使用されます。 他のゾーンでユーザーの ID とパスワードを照会するには [イントラネット ゾーンでのみ自動ログオンを許可する] を選択してください。 ユーザーが照会された後に、これらの値は残りのセッションで警告なしに使用されます。 現在のユーザー名とパスワードで自動的にサインインし、Windows NT チャレンジ応答 (別名 NTLM 認証) を使用してログオンを試みます。 サーバーで Windows NT チャレンジ応答がサポートされている場合、サインインでは、ユーザーのログオン用のネットワーク ユーザー名とパスワードが使用されます。 サーバーで Windows NT チャレンジ応答がサポートされていない場合、ユーザーはユーザー名とパスワードを提供する必要があります。 このポリシー設定を無効にすると、サインインは [イントラネット ゾーンでのみ自動ログオンを許可する] に設定されます。 このポリシー設定を構成しない場合、サインインは [イントラネット ゾーンでのみ自動的にサインインする] に設定されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **既定値**: プロンプト  
  
- **Internet Explorer の制限付きゾーンで VB スクリプトの実行を許可する**   
  このポリシー設定を使用すると、Internet Explorer 内の指定されたゾーンのページ上で VB スクリプトを実行できるかどうかを管理できます。 ドロップダウン ボックスで [有効にする] を選択すると、ユーザーによる手動操作を必要とすることなく、VB スクリプトを実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、ユーザーは VB スクリプトの実行を許可するかどうかをたずねられます。 ドロップダウン ボックスで [無効にする] を選択した場合、VB スクリプトは実行されません。 このポリシー設定を構成しなかった場合、または無効にした場合、VB スクリプトは実行されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer internet zone drag content from different domains across windows (Internet Explorer のインターネット ゾーンでウィンドウを超えて異なるドメインからコンテンツをドラッグする)**  
  このポリシー設定により、移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグするオプションを設定できます。 このポリシー設定を有効にして [有効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウにある場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。 このポリシー設定を有効にして [無効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウにある場合、あるドメインから別のドメインにコンテンツをドラッグできません。 この設定はユーザーが変更できません。 Internet Explorer 10 では、このポリシー設定を無効にする場合、または構成しない場合、[有効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグできません。 ユーザーは、[インターネット オプション] ダイアログでこの設定を変更できます。 Internet Explorer 9 以前のバージョンでは、このポリシーを無効にする場合、または構成しない場合は、ユーザーは移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **既定値**: 無効 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe (Internet Explorer のイントラネット ゾーンで安全であるとマークされていない Active X コントロールを初期化およびスクリプト化する)**  
  このポリシー設定を使用すると、安全であるとマークされていない ActiveX コントロールを管理できます。 このポリシー設定を有効にすると、ActiveX コントロールがパラメーターを読み込んで実行され、また、信頼されていないデータまたはスクリプトに対するオブジェクトの安全性を設定することなくスクリプト化されます。 この設定は、安全でかつ管理されたゾーン以外では推奨しません。 この設定では、安全なコントロールと安全ではないコントロールの両方を初期化およびスクリプト化します。[スクリプトを実行しても安全だとマークされている ActiveX コントロールのスクリプトの実行] オプションは無視されます。 このポリシー設定を有効にして、ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、コントロールにパラメーターを読み込んだりスクリプト化したりすることを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。 このポリシー設定を構成しなかった場合、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer download enclosures (Internet Explorer での添付ファイルのダウンロード)**  
  このポリシー設定は、添付ファイルをフィードからユーザーのコンピューターにダウンロードできないようにします。 このポリシー設定を有効にすると、フィードのプロパティ ページで、フィード同期エンジンが添付ファイルをダウンロードするように設定できません。 開発者は、フィードの API を使用してダウンロード設定を変更できません。 このポリシー設定を無効にするか、構成しない場合、フィードのプロパティ ページで、フィード同期エンジンが添付ファイルをダウンロードするように設定できます。 開発者は、フィードの API を使用してダウンロード設定を変更できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **既定値**: 無効  
  
- **Internet Explorer restricted zone download unsigned Active X controls (Internet Explorer の制限付きゾーンで署名されていない Active X コントロールをダウンロードする)**  
  このポリシー設定を使用すると、ユーザーがゾーンから署名されていない ActiveX コントロールをダウンロードすることを許可するかどうかを管理できます。 このようなコードは、特に信頼されていないゾーンから来た場合は、危険である可能性があります。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、署名されていないコントロールを実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名されていないコントロールを実行することを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーは署名されていないコントロールを実行できません。 このポリシー設定を構成しない場合、ユーザーは署名されていないコントロールを実行できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer internet zone drag content from different domains within windows (Internet Explorer のインターネット ゾーンでウィンドウ内の異なるドメインからコンテンツをドラッグする)**  
  このポリシー設定を使用すると、ユーザーがゾーンから署名されていない ActiveX コントロールをダウンロードすることを許可するかどうかを管理できます。 このようなコードは、特に信頼されていないゾーンから来た場合は、危険である可能性があります。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、署名されていないコントロールを実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名されていないコントロールを実行することを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーは署名されていないコントロールを実行できません。 このポリシー設定を構成しない場合、ユーザーは署名されていないコントロールを実行できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **既定値**: 無効  
  
- **Internet Explorer プロセスで Active X インストールを制限する**   
  このポリシー設定は、Web ブラウザー コントロールをホストしているアプリケーションで、ActiveX コントロール インストールの確認ダイアログの自動表示のブロックを有効にします。 このポリシー設定を有効にすると、すべてのプロセスにおいて ActiveX コントロール インストールの確認ダイアログの自動表示は Web ブラウザー コントロールによってブロックされます。 このポリシー設定を無効にするか、または構成しない場合は、ActiveX コントロール インストールの確認ダイアログの自動表示はすべてのプロセスにおいて Web ブラウザー コントロールによってブロックされません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **既定値**: 有効  
  
- **Internet Explorer のインターネットゾーンのスクリプトレット**  
  このポリシー設定を使用すると、ユーザーがスクリプトレットを実行できるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーはスクリプトレットを実行できます。 このポリシー設定を無効にすると、ユーザーはスクリプトレットを実行できません。 このポリシー設定を構成しなかった場合、ユーザーはスクリプトレットを有効または無効にできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files (Internet Explorer の制限付きゾーンでファイルのドラッグ アンド ドロップまたはコピーと貼り付けを行う)**  
  このポリシー設定を使用すると、ユーザーがゾーン内のソースからファイルのドラッグまたはコピーと貼り付けを行うことができるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーはこのゾーンからファイルをドラッグしたり、コピーして貼り付けたりできます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、このゾーンからファイルをドラッグまたはコピーするかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーはこのゾーンからファイルをドラッグしたり、コピーして貼り付けたりできません。 このポリシー設定を構成しない場合は、このゾーンからファイルをドラッグまたはコピーするかどうかをユーザーにたずねます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer software when signature is invalid (Internet Explorer での署名が無効な場合のソフトウェア)**  
  このポリシー設定を使うと、署名が無効な場合でもユーザーがソフトウェア (ActiveX コントロールやファイル ダウンロードなど) をインストールまたは実行できるかどうかを管理できます。 署名が無効である場合、そのファイルをだれかが改ざんした可能性があります。 このポリシー設定を有効にすると、ユーザーが無効な署名を持つファイルをインストールまたは実行するときにダイアログが表示されます。 このポリシー設定を無効にすると、ユーザーは無効な署名を持つファイルを実行したりインストールしたりすることはできません。 このポリシーを構成しなかった場合は、ユーザーは無効な署名を持つファイルを実行またはインストールするかどうかを選択できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **既定値**: 無効  
  
- **Internet Explorer restricted zone copy and paste via script (Internet Explorer の制限付きゾーンでのスクリプトによるコピーと貼り付け)**  
  このポリシー設定を使用すると、指定された領域でスクリプトがクリップボードの操作 (例: 切り取り、コピー、貼り付け) を実行できるかどうかを管理できます。 このポリシー設定を有効にすると、スクリプトはクリップボードの操作を実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、クリップボードの操作を実行するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、スクリプトはクリップボードの操作を実行できません。 このポリシー設定を構成しなかった場合、スクリプトはクリップボードの操作を実行できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer restricted zone drag content from different domains across windows (Internet Explorer の制限付きゾーンでウィンドウを超えて異なるドメインからコンテンツをドラッグする)**  
  このポリシー設定により、移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグするオプションを設定できます。 このポリシー設定を有効にして [有効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウにある場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。 このポリシー設定を有効にして [無効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウにある場合、あるドメインから別のドメインにコンテンツをドラッグできません。 この設定はユーザーが変更できません。 Internet Explorer 10 では、このポリシー設定を無効にする場合、または構成しない場合、[有効にする] をクリックすると、ユーザーは移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグできません。 ユーザーは、[インターネット オプション] ダイアログでこの設定を変更できます。 Internet Explorer 9 以前のバージョンでは、このポリシーを無効にする場合、または構成しない場合は、ユーザーは移行元と移行先が異なるウィンドウの場合、あるドメインから別のドメインにコンテンツをドラッグすることができます。 この設定はユーザーが変更できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **既定値**: 無効  
  
- **Internet Explorer のユーザーによるサイトの追加**  
  セキュリティ ゾーンからサイトを追加したり削除したりできないようにします。 セキュリティ ゾーンとは、同じセキュリティ レベルが設定されている Web サイトのグループのことです。 このポリシーを有効にすると、ユーザーは、セキュリティ ゾーンのサイト管理の設定画面を使用できなくなります (セキュリティ ゾーンのサイト管理の設定画面を表示するには、[インターネット オプション] ダイアログ ボックスで [セキュリティ] タブをクリックし、[サイト] ボタンをクリックします)。このポリシーを無効にするか、構成しない場合、ユーザーは [信頼済みサイト] および [制限付きサイト] ゾーンに対して Web サイトの追加と削除を行うことができます。また、[ローカル イントラネット] ゾーンの設定を変更できます。 このポリシーを有効にすると、ユーザーは、管理者が設定したセキュリティ ゾーンのサイト管理の設定を変更できなくなります。 注: インターフェイスから [セキュリティ] タブを削除する [[セキュリティ] ページの使用を許可しない] ポリシー (場所: \ユーザーの構成\管理用テンプレート\Windows コンポーネント\Internet Explorer\インターネット コントロール パネル) は、このポリシーより優先されます。 それが有効になっている場合、このポリシーは無視されます。 [セキュリティ ゾーン: コンピューターの設定のみ使用する] ポリシーも参照してください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **既定値**: 無効  
  
- **Internet Explorer のインターネット ゾーンのスクリプトによって開かれるウィンドウ**  
  このポリシー設定を使用すると、スクリプトによって起動されるポップアップ ウィンドウ、およびタイトルとステータス バーを持ったウィンドウの制限を管理できます。 このポリシー設定を有効にすると、Windows Restrictions セキュリティはこのゾーンでは適用されません。 セキュリティ ゾーンは、この機能で提供されるセキュリティの追加のレイヤーなしに実行されます。 このポリシー設定を無効にすると、スクリプトによって起動されたポップアップ ウィンドウや、タイトルとステータス バーを含むウィンドウに含まれる、危害を及ぼす可能性のある動作は実行されません。 この Internet Explorer のセキュリティ機能は、プロセスの [スクリプト化されたウィンドウのセキュリティ制限] 機能コントロール設定で指定されたように、このゾーンでオンになります。 このポリシー設定を構成しないと、スクリプトによって起動されたポップアップ ウィンドウや、タイトルとステータス バーを含むウィンドウに含まれる、危害を及ぼす可能性のある動作は実行されません。 この Internet Explorer のセキュリティ機能は、プロセスの [スクリプト化されたウィンドウのセキュリティ制限] 機能コントロール設定で指定されたように、このゾーンでオンになります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **既定値**: 無効  
  
- **Internet Explorer のセキュリティ ゾーンでコンピューターの設定のみ使用する**  
  セキュリティ ゾーンの設定情報をコンピューターに接続するすべてのユーザーに適用します。 セキュリティ ゾーンとは、同じセキュリティ レベルが設定されている Web サイトのグループのことです。 このポリシーを有効にすると、変更したセキュリティ ゾーンの設定はコンピューターに接続するすべてのユーザーに適用されます。 このポリシーを無効にしたり構成しない場合には、ユーザーは、独自のセキュリティ ゾーンを設定できます。 このポリシーを使用すると、セキュリティ ゾーンの設定が同じコンピューターに統一して適用され、ユーザーごとに設定を変えることはできません。 [セキュリティ ゾーン: ポリシーの変更を許可しない] ポリシーも参照してください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **既定値**: 有効  
  
- **Internet Explorer のロックダウンされたローカル コンピューター ゾーンの Java アクセス許可**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しなかった場合、Java アプレットは無効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **既定値**: Java を無効にする 
  
- **Internet Explorer の制限付きゾーンで Active X コントロールに対してマルウェア対策を実行しない**   
  このポリシー設定では、ActiveX コントロールをページに読み込んでも安全かどうかを調べるために Internet Explorer がマルウェア対策プログラムを実行するかどうかを決定します。 このポリシー設定を有効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 このポリシー設定を無効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 このポリシー設定を構成しない場合、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 ユーザーは、Internet Explorer の [セキュリティ] 設定を使用して、この動作の有効と無効を切り替えることができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **既定値**: 無効  
  
- **Internet Explorer の制限付きゾーンで Authenticode 署名済みの .NET Framework 依存コンポーネントを実行する**  
  このポリシー設定を使用すると、Authenticode を使用して署名されている .NET Framework コンポーネントを Internet Explorer から実行できるかどうかを管理できます。 これらのコンポーネントには、object タグから参照された管理されたコントロール、リンクから参照された管理された実行可能ファイルなどが含まれます。 このポリシー設定を有効にすると、Internet Explorer は署名済みの管理されたコンポーネントを実行します。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名済みの管理されたコンポーネントを実行するかどうかを確認するメッセージが Internet Explorer によって表示されます。 このポリシー設定を無効にすると、Internet Explorer は署名済みの管理されたコンポーネントを実行しません。 このポリシー設定を構成しない場合は、Internet Explorer は署名済みの管理されたコンポーネントを実行します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer の制限付きゾーンにあるデータ ソースへのアクセス**  
  このポリシー設定を使用すると、Internet Explorer が Microsoft XML パーサー (MSXML) または ActiveX Data Objects (ADO) を使用して他のセキュリティ ゾーンからデータにアクセスできるかどうかを管理できます。 このポリシー設定を有効にすると、ユーザーはゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことができます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、ゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことはできません。 このポリシー設定を構成しないと、ゾーン内の他のサイトにあるデータに MSXML または ADO を使用してアクセスするゾーン内のページを読み込むことはできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **既定値**: 無効にする 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls (Internet Explorer のインターネット ゾーンで Active X コントロールに対してマルウェア対策を実行しない)**  
  このポリシー設定では、ActiveX コントロールをページに読み込んでも安全かどうかを調べるために Internet Explorer がマルウェア対策プログラムを実行するかどうかを決定します。 このポリシー設定を有効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するためにマルウェア対策プログラムを実行しません。 このポリシー設定を無効にすると、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 このポリシー設定を構成しない場合、Internet Explorer は、ActiveX コントロールのインスタンスを安全に作成できるかどうかを確認するために常にマルウェア対策プログラムを実行します。 ユーザーは、Internet Explorer の [セキュリティ] 設定を使用して、この動作の有効と無効を切り替えることができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **既定値**: 無効  
  
- **Internet Explorer のインターネット ゾーンでのスクリプトによるコピーと貼り付け**  
  このポリシー設定を使用すると、指定された領域でスクリプトがクリップボードの操作 (例: 切り取り、コピー、貼り付け) を実行できるかどうかを管理できます。 このポリシー設定を有効にすると、スクリプトはクリップボードの操作を実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、クリップボードの操作を実行するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、スクリプトはクリップボードの操作を実行できません。 このポリシー設定を構成しなかった場合、スクリプトはクリップボードの操作を実行できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer での Activex インストーラー サービスの使用**  
  このポリシー設定では、ActiveX コントロールのインストール方法を指定できます。 このポリシー設定を有効にすると、ActiveX インストーラー サービスが存在し、ActiveX コントロールのインストールを許可するように構成されている場合のみ、ActiveX コントロールがインストールされます。 このポリシー設定を無効にするか、または構成しない場合、ActiveX コントロール (ユーザーごとのコントロールを含む) は標準インストール プロセスを使用してインストールされます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **既定値**: 有効  
  
- **Internet Explorer でゾーン昇格からの保護を処理する**  
  Internet Explorer は開く Web サイトのページに制限を付けます。 制限は Web ページの場所 (インターネット ゾーン、イントラネット ゾーン、ローカル コンピューター ゾーンなど) によって決まります。 たとえば、ローカル コンピューターにある Web ページはローカル コンピューター セキュリティ ゾーンにあり、最小限の制限を受けるため、ローカル コンピューター セキュリティ ゾーンは悪意のあるユーザーの一番のターゲットとなります。 このポリシー設定を有効にすると、すべてのプロセスにおいて、どのゾーンもゾーン昇格から保護されます。 このポリシー設定を無効にするか、または構成しない場合は、Internet Explorer のプロセス以外のプロセス、またはプロセスの一覧にあるプロセス以外のプロセスは、このような保護を受けません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **既定値**: 有効  
  
- **Internet Explorer のインターネット ゾーンで署名なしの Active X コントロールをダウンロードする**   
  このポリシー設定を使用すると、ユーザーがゾーンから署名されていない ActiveX コントロールをダウンロードすることを許可するかどうかを管理できます。 このようなコードは、特に信頼されていないゾーンから来た場合は、危険である可能性があります。 このポリシー設定を有効にすると、ユーザーによる手動操作を必要とすることなく、署名されていないコントロールを実行できます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、署名されていないコントロールを実行することを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーは署名されていないコントロールを実行できません。 このポリシー設定を構成しない場合、ユーザーは署名されていないコントロールを実行できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **既定値**: 無効にする  
  
- **Internet Explorer のインターネット ゾーンで異なるドメインとの間でウィンドウとフレームを移動する**   
  このポリシー設定を使用すると、異なるドメイン間でウィンドウとフレームを開くことや、アプリケーションにアクセスすることを管理できます。 このポリシー設定を有効にすると、ユーザーは他のドメインからウィンドウとフレームを開くことや、アプリケーションにアクセスすることができます。 ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、他のドメインからウィンドウとフレームを開いたりアプリケーションにアクセスしたりするかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、ユーザーは他のドメインからウィンドウとフレームを開けることや、アプリケーションにアクセスすることができません。 このポリシー設定を構成しない場合は、ユーザーは他のドメインからウィンドウとフレームを開くことや、アプリケーションにアクセスすることができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer のインターネット ゾーンでスクリプトを介してステータス バーを更新する**  
  このポリシー設定を使用すると、スクリプトを介してゾーン内のステータス バーを更新できるかどうかを管理できます。 このポリシー設定を有効にすると、スクリプトを介してステータス バーを更新できます。 このポリシー設定を無効にした場合、または構成しなかった場合、スクリプトを介してステータス バーを更新できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **既定値**: 無効  
  
- **Internet Explorer の制限付きゾーンでサーバーへのファイルのアップロード時にローカル パスを含める**  
  このポリシー設定では、ユーザーが HTML フォーム経由でファイルをアップロードするときに、ローカル パス情報が送信されるかどうかが制御されます。 ローカル パス情報が送信された場合、意図せずに、一部の情報がサーバーに公開されることがあります。 たとえば、ユーザーのデスクトップから送信されたファイルに、パスの一部としてユーザー名が含まれている可能性があります。 このポリシー設定を有効にすると、ユーザーが HTML フォーム経由でファイルをアップロードするときに、パス情報が送信されます。 このポリシー設定を無効にすると、ユーザーが HTML フォーム経由でファイルをアップロードするときに、パス情報は削除されます。 このポリシー設定を構成しなかった場合、ユーザーが HTML フォーム経由でファイルをアップロードするときに、パス情報を送信するかどうかをユーザーが選択できます。 既定では、パス情報は送信されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **既定値**: 無効  
  
- **Internet Explorer のプロセスでファイルのダウンロードを制限する**   
  このポリシー設定は、Web ブラウザー コントロールをホストしているアプリケーションで、ユーザーが開始していないファイル ダウンロードの確認ダイアログの自動表示をブロックすることを有効にします。 このポリシー設定を有効にすると、ユーザーによって開始されていないファイル ダウンロードの確認ダイアログの自動表示はすべてのプロセスにおいて Web ブラウザー コントロールによってブロックされます。 このポリシー設定を無効にすると、ユーザーによって開始されていないファイル ダウンロードの確認ダイアログの自動表示はすべてのプロセスにおいて Web ブラウザー コントロールによってブロックされません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **既定値**: 有効  
  
- **Internet Explorer の制限付きゾーンで承認済みドメインのみが Active X コントロールを使用できるようにする**   
  このポリシー設定では、ActiveX コントロールをインストールした Web サイト以外の Web サイトで ActiveX コントロールを実行する許可を求めるメッセージをユーザーに表示するかどうかを制御します。 このポリシー設定を有効にすると、このゾーン内の Web サイトで ActiveX コントロールが実行される前に、ユーザーにメッセージが表示されます。 ユーザーは、現在のサイトからのコントロールの実行を許可するか、すべてのサイトからのコントロールの実行を許可するかを選択できます。 このポリシー設定を無効にすると、ユーザーにはサイトごとの ActiveX 警告は表示されず、ActiveX コントロールはこのゾーン内のすべてのサイトから実行できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **既定値**: 有効  
  
- **Internet Explorer の制限付きゾーンで安全であるとマークされていない Active X コントロールを初期化およびスクリプト化する**  
  このポリシー設定を使用すると、安全であるとマークされていない ActiveX コントロールを管理できます。 このポリシー設定を有効にすると、ActiveX コントロールがパラメーターを読み込んで実行され、また、信頼されていないデータまたはスクリプトに対するオブジェクトの安全性を設定することなくスクリプト化されます。 この設定は、安全でかつ管理されたゾーン以外では推奨しません。 この設定では、安全なコントロールと安全ではないコントロールの両方を初期化およびスクリプト化します。[スクリプトを実行しても安全だとマークされている ActiveX コントロールのスクリプトの実行] オプションは無視されます。 このポリシー設定を有効にして、ドロップダウン ボックスで [ダイアログを表示する] を選択した場合、コントロールにパラメーターを読み込んだりスクリプト化したりすることを許可するかどうかをユーザーにたずねます。 このポリシー設定を無効にすると、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。 このポリシー設定を構成しなかった場合、安全であるとマークできない ActiveX コントロールにパラメーターを読み込んだりスクリプト化したりすることはできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **既定値**: 無効にする  
  
- **Internet Explorer のユーザーによるポリシーの変更**  
  セキュリティ ゾーンの設定を変更できないようにします。 セキュリティ ゾーンとは、同じセキュリティ レベルが設定されている Web サイトのグループのことです。 このポリシーを有効にすると、ユーザーは、インターネット オプションの [セキュリティ] タブで表示される [レベルのカスタマイズ] ボタンとセキュリティ レベルを設定するスライダーを使用できなくなります。 このポリシーを無効にするか、または構成しない場合は、セキュリティ ゾーンの設定を変更できます。 このポリシーを有効にすると、ユーザーは、管理者が設定したセキュリティ ゾーンの設定を変更できなくなります。 注: このポリシーよりも優先される [[セキュリティ] ページの使用を許可しない] ポリシー (場所: \ユーザーの構成\管理用テンプレート\Windows コンポーネント\Internet Explorer\インターネット コントロール パネル) を有効にすると、コントロール パネルのインターネット オプションから [セキュリティ] タブが削除され、 それが有効になっている場合、このポリシーは無視されます。 [セキュリティ ゾーン: コンピューターの設定のみ使用する] ポリシーも参照してください。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **既定値**: 無効  
  
- **Internet Explorer の制限付きゾーンでの保護モード**  
  このポリシー設定を使用すると、保護モードを有効にできます。 保護モードを使用すると、Internet Explorer が書き込むことができるレジストリやファイル システム内の場所を制限することで、脆弱点を悪用した攻撃から Internet Explorer を保護できます。 このポリシー設定を有効にすると、保護モードが有効になります。 ユーザーは保護モードを無効にできません。 このポリシー設定を無効にすると、保護モードが無効になります。 ユーザーは保護モードを有効にできません。 このポリシー設定を構成しなかった場合、ユーザーは保護モードを有効または無効にできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **既定値**: 有効にする  
  
- **Internet Explorer のインターネット ゾーンでのユーザー データ永続化**  
  このポリシー設定を使用すると、ブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存された Web ページ内に直接入っている情報の保管を管理できます。 このポリシー設定を正しく構成すると、ユーザーが固定されたページに戻ったときに、ページの状態を復元できます。 このポリシー設定を有効にすると、ユーザーはブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存されている Web ページ内に直接、情報を保管できます。 このポリシー設定を無効にすると、ユーザーはブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存されている Web ページ内に直接、情報を保管できません。 このポリシー設定を構成しなかった場合、ユーザーはブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存されている Web ページ内に直接、情報を保管できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **既定値**: 無効  
  
- **Internet Explorer のインターネット ゾーンでの Web ブラウザー コントロールのスクリプト化**  
 
  このポリシー設定では、ページで、スクリプトを使用して埋め込みの WebBrowser コントロールを制御できるかどうかを決定します。 このポリシー設定を有効にすると、WebBrowser コントロールへのスクリプト アクセスが許可されます。 このポリシー設定を無効にすると、WebBrowser コントロールへのスクリプト アクセスは許可されません。 このポリシー設定を構成しなかった場合、ユーザーは WebBrowser コントロールへのスクリプト アクセスを有効または無効にできます。 既定では、WebBrowser コントロールへのスクリプト アクセスは、ローカル コンピューターおよびイントラネット ゾーン内でのみ許可されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **既定値**: 無効  
  
- **Internet Explorer の制限付きゾーンでのユーザー データ永続化**  
  このポリシー設定を使用すると、ブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存された Web ページ内に直接入っている情報の保管を管理できます。 このポリシー設定を正しく構成すると、ユーザーが固定されたページに戻ったときに、ページの状態を復元できます。 このポリシー設定を有効にすると、ユーザーはブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存されている Web ページ内に直接、情報を保管できます。 このポリシー設定を無効にすると、ユーザーはブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存されている Web ページ内に直接、情報を保管できません。 このポリシー設定を構成しなかった場合、ユーザーはブラウザーの履歴、お気に入り、XML ストア、またはディスクに保存されている Web ページ内に直接、情報を保管できません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **既定値**: 無効  
  
- **Internet Explorer のロックダウンされた信頼済みゾーンでの Java のアクセス許可**  
  このポリシー設定を使用すると、Java アプレットのアクセス許可を管理できます。 このポリシー設定を有効にすると、ドロップダウン ボックスからオプションを選択できます。 アクセス許可の設定を個々に制御するには [カスタム] を選択してください。 [安全性 - 低] を選択すると、アプレットはすべての操作を実行できます。 [安全性 - 中] を選択すると、アプレットはサンドボックス (メモリ内の領域で、その外側にはプログラムは呼び出しを実行できない) 内で実行されます。また、スクラッチ領域 (クライアント コンピューター内の安全でセキュリティで保護された記憶域) やユーザーによって制御されたファイル I/O などの機能が利用できます。 [安全性 - 高] を選択すると、サンドボックス内でアプレットが実行されます。 アプレットを実行しないようにするには、[Java の無効化] を選択してください。 このポリシー設定を無効にすると、Java アプレットは実行されません。 このポリシー設定を構成しなかった場合、Java アプレットは無効になります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **既定値**: Java を無効にする  
  
- **Internet Explorer の拡張保護モード**  
  拡張保護モードでは、64 ビット バージョンの Windows で 64 ビット プロセスが使用され、悪意のある Web サイトに対する保護が強化されています。 Windows 8 以降が実行されているコンピューターでは、拡張保護モードによって、Internet Explorer が読み取り元に設定できる場所もレジストリとファイル システムに制限されています。 このポリシー設定を有効にすると、拡張保護モードが有効になります。 保護モードが有効になっているゾーンでは、拡張保護モードが使用されます。 ユーザーが拡張保護モードを無効にすることはできません。 このポリシー設定を無効にすると、拡張保護モードが無効になります。 保護モードが有効になっているゾーンでは、Windows Vista の Internet Explorer 7 で導入されたバージョンの保護モードが使用されます。 このポリシー設定を構成しない場合、ユーザーは、[インターネット オプション] ダイアログの [詳細設定] タブで拡張保護モードを有効または無効にできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **既定値**: 有効  
  
- **Internet Explorer のスマート スクリーン警告のバイパス**  
  このポリシー設定では、ユーザーが SmartScreen フィルター機能からの警告をバイパスできるかどうかを決定します。 SmartScreen フィルター機能では、ダウンロードしたユーザー数が少ない実行可能ファイルについてユーザーに警告します。 このポリシー設定を有効にすると、ユーザーは SmartScreen フィルター機能の警告によってブロックされます。 このポリシー設定を無効にした場合、または構成しなかった場合、ユーザーは SmartScreen フィルター機能の警告をバイパスできます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **既定値**: 無効  
  
- **Internet Explorer の制限付きゾーンのメタ更新**  
  このポリシー設定を使用すると、Web ページの作成者がブラウザーを別の Web ページにリダイレクトするために Meta Refresh 設定 (タグ) を使用している場合に、ユーザーのブラウザーを別の Web ページにリダイレクトするかどうかを管理できます。 このポリシー設定を有効にすると、アクティブな Meta Refresh 設定を含むページを読み込むブラウザーを他の Web ページにリダイレクトできます。 このポリシー設定を無効にすると、アクティブな Meta Refresh 設定を含むページを読み込むブラウザーを他の Web ページにリダイレクトできません。 このポリシー設定を構成しなかった場合、アクティブな Meta Refresh 設定を含むページを読み込むブラウザーを他の Web ページにリダイレクトできません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **既定値**: 無効  
  
## <a name="local-policies-security-options"></a>ローカル ポリシーのセキュリティ オプション
詳細については、Windows のドキュメントの「[Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions)」(ポリシー CSP - LocalPoliciesSecurityOptions) を参照してください。 

- **名前付きパイプと共有への匿名アクセスを制限する**  
  このセキュリティ設定を有効にすると、次の設定と一致する共有およびパイプへの匿名アクセスが制限されます: (1) 匿名でアクセスできる名前付きパイプ (2) 匿名でアクセスできる共有。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **既定値**: はい  
  
- **NTLM SSP ベースのサーバー向け最小セッション セキュリティ**  
  このセキュリティ設定を使用すると、サーバーで 128 ビット暗号化および/または NTLMv2 セッション セキュリティのネゴシエーションが必要になるようにすることができます。 これらの値は、LAN Manager 認証レベルのセキュリティ設定値に依存します。 オプションは次のとおりです。NTLMv2 セッション セキュリティが必要: メッセージの整合性がネゴシエートされていない場合、接続は失敗します。 128 ビット暗号化が必要: 強力な暗号化 (128 ビット) がネゴシエートされない場合、接続は失敗します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **既定値**: NTLM V2 および 128 ビットの暗号化が必要  
  
- **スクリーン セーバーがアクティブになるまでのロック画面の非アクティブ時間 (分)**  
  ログオン セッションの非アクティブ状態が Windows によって通知されます。また、非アクティブ状態の時間が非アクティブ状態の上限を超えるとスクリーン セーバーが実行され、セッションがロックされます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **既定値**: 15
  
- **常に通信にデジタル署名するようにクライアントに求める** このセキュリティ設定では、ドメインのメンバーによって開始された、セキュリティで保護されたチャネルのトラフィックすべてに対して署名または暗号化を行う必要があるかどうかを決定します。 コンピューターがドメインに参加すると、コンピューター アカウントが作成されます。 それ以降、システムでは起動時に、そのコンピューター アカウントのパスワードを使用して、そのドメイン用のドメイン コントローラーとの間でセキュリティで保護されたチャネルが確立されます。 このセキュリティで保護されたチャネルは、NTLM パススルー認証や LSA SID/名前の参照などの操作を実行するために使用されます。 この設定では、ドメインのメンバーによって開始された、セキュリティで保護されたチャネルのトラフィックすべてが最低限のセキュリティ要件を満たす必要があるかどうかを決定します。 具体的には、ドメインのメンバーによって開始された、セキュリティで保護されたチャネルのトラフィックすべてに対して署名または暗号化を行う必要があるかどうかを決定します。 このポリシーを有効にすると、セキュリティで保護されたチャネルのトラフィックすべてに対する署名または暗号化がネゴシエートされるまで、セキュリティで保護されたチャネルは確立されません。 このポリシーを無効にすると、セキュリティで保護されたチャネルのトラフィックすべてに対する暗号化および署名は、ドメイン コントローラーとネゴシエートされます。この場合、署名と暗号化のレベルは、ドメイン コントローラーのバージョンと次の 2 つのポリシーの設定によって決まります: ドメイン メンバー: セキュリティで保護されたチャネルのデータをデジタル的に暗号化する (可能な場合) ドメイン メンバー: セキュリティで保護されたチャネルのデータをデジタル的に署名する (可能な場合)。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **既定値**: はい
  
- **認証レベル**  
  このセキュリティ設定では、ネットワーク ログオンに使用されるチャレンジ/レスポンス認証プロトコルが決定されます。 この選択は、以下に示すように、クライアントで使用する認証プロトコルのレベル、ネゴシエートされるセッション セキュリティのレベル、およびサーバーによって受け入れられる認証レベルに影響します:  
  - "*LM と NTLM 応答を送信する*" - クライアントでは LM および NTLM 認証が使用され、NTLMv2 セッション セキュリティは使用されません。ドメイン コントローラーでは LM、NTLM、および NTLMv2 認証が受け入れられます。 
  - "*LM と NTLM を送信する - ネゴシエートされた場合は NTLMv2*" - クライアントでは LM および NTLM 認証が使用され、サーバーでサポートされている場合は NTLMv2 セッション セキュリティも使用されます。ドメイン コントローラーでは、LM、NTLM、および NTLMv2 認証が受け入れられます。 
  - "*NTLM 応答のみ送信する*" - クライアントでは NTLM 認証のみが使用され、サーバーでサポートされている場合は NTLMv2 セッション セキュリティも使用されます。ドメイン コントローラーでは、LM、NTLM、および NTLMv2 認証が受け入れられます。 
  - "*NTLMv2 応答のみ送信する*" - クライアントでは NTLMv2 認証のみが使用され、サーバーでサポートされている場合は NTLMv2 セッション セキュリティも使用されます。ドメイン コントローラーでは、LM、NTLM、および NTLMv2 認証が受け入れられます。 
  - "*NTLMv2 応答のみ送信する。LM を拒否する*" - クライアントでは NTLMv2 認証のみが使用され、サーバーでサポートされている場合は NTLMv2 セッション セキュリティも使用されます。ドメイン コントローラーでは LM は拒否されます (NTLM および NTLMv2 認証のみが受け入れられます)。 
  - "*NTLMv2 応答のみ送信する。LM と NTLM を拒否する*" - クライアントでは NTLMv2 認証のみが使用され、サーバーでサポートされている場合は NTLMv2 セッション セキュリティも使用されます。ドメイン コント ローラーでは LM と NTLM は拒否されます (NTLMv2 認証のみが受け入れられます)。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **既定値**: NTLMv2 応答のみ送信する。 LM と NTLM を拒否する
  
- **暗号化されていないパスワードがクライアントからサード パーティの SMB サーバーに送信されるのを防ぐ**  
  このセキュリティ設定を有効にすると、サーバー メッセージ ブロック (SMB) リダイレクターは、認証時にパスワードの暗号化をサポートしていない Microsoft 以外の SMB サーバーにプレーンテキストのパスワードを送信することができます。 暗号化されていないパスワードを送信することには、セキュリティ上のリスクがあります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **既定値**: はい
  
- **サーバーが常に通信にデジタル署名を行うことを要求する**  
  このセキュリティ設定では、SMB クライアントによって SMB パケットの署名がネゴシエートされるかどうかが決定されます。 サーバー メッセージ ブロック (SMB) プロトコルは、Microsoft ファイルおよびプリンターの共有の基礎、さらにはリモート Windows 管理などのネットワーク操作の基礎となります。 転送中に SMB パケットを変更する中間者攻撃を防ぐために、SMB プロトコルでは SMB パケットのデジタル署名がサポートされています。 このポリシー設定では、SMB クライアント コンポーネントが SMB サーバーに接続するときに、その SMB クライアント コンポーネントによって SMB パケットの署名がネゴシエートされるかどうかが決定されます。 この設定を有効にすると、セッションのセットアップ時に SMB パケットの署名を実行するよう Microsoft ネットワーク クライアントからサーバーに要求が出されます。 サーバーでパケットの署名が有効になっている場合、パケットの署名がネゴシエートされます。 このポリシーを無効にすると、SMB クライアントによって SMB パケットの署名がネゴシエートされることはありません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **既定値**: はい
  
- **管理者に対する昇格時のプロンプトの動作**  
  このポリシー設定では、管理者に対する昇格時のプロンプトの動作が制御されます。 オプションは次のとおりです。 
  - "*プロンプトを表示せずに昇格する*" - 昇格を必要とする操作を、同意または資格情報の必要なしに実行することを権限アカウントに許可します。 注: このオプションは非常に制限された環境内でのみ使用します。 
  - "*セキュリティで保護されたデスクトップで資格情報を要求する*" - 操作で特権の昇格が必要になると、ユーザーはセキュリティで保護されたデスクトップ上で特権を持つユーザー名とパスワードを入力するように求められます。 ユーザーが有効な資格情報を入力すると、ユーザーが利用できる最も高い特権で操作が続行されます。 
  - "*セキュリティで保護されたデスクトップで同意を要求する*" - 操作で特権の昇格が必要になると、ユーザーはセキュリティで保護されたデスクトップ上で許可または拒否のいずれかを選択するように求められます。 ユーザーが許可を選択すると、ユーザーが利用できる最も高い特権で操作が続行されます。 
  - "*資格情報を要求する*" - 操作で特権の昇格が必要になると、ユーザーは管理者のユーザー名とパスワードを入力するように求められます。 ユーザーが有効な資格情報を入力すると、適用可能な特権で操作が続行されます。 
  - "*同意を要求する*" - 操作で特権の昇格が必要になると、ユーザーは許可または拒否のいずれかを選択するように求められます。 ユーザーが許可を選択すると、ユーザーが利用できる最も高い特権で操作が続行されます。  
  - "*非 Windows バイナリに対して同意を要求する*" - Microsoft 以外のアプリケーションの操作で特権の昇格が必要になると、ユーザーはセキュリティで保護されたデスクトップ上で許可または拒否のいずれかを選択するように求められます。 ユーザーが許可を選択すると、ユーザーが利用できる最も高い特権で操作が続行されます。 
  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **既定値**: セキュリティで保護されたデスクトップで同意を要求する
  
- **NTLM SSP ベースのクライアント向け最小セッション セキュリティ**  
  このセキュリティ設定を使用すると、クライアントで 128 ビット暗号化および/または NTLMv2 セッション セキュリティのネゴシエーションが必要になるようにすることができます。 これらの値は、LAN Manager 認証レベルのセキュリティ設定値に依存します。 オプションは次のとおりです。
  - "*NTLMv2 セッション セキュリティが必要*" - NTLMv2 プロトコルがネゴシエートされていない場合、接続は失敗します。 
  - "*128 ビット暗号化が必要*" - 強力な暗号化 (128 ビット) がネゴシエートされない場合、接続は失敗します。
  - *NTLMv2 および 128 ビットの暗号化が必要*。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **既定値**: NTLM V2 128 暗号化が要求
  
- **スマート カードを取り外したときの動作**  
  このセキュリティ設定では、ログオンしているユーザーのスマート カードがスマート カード リーダーから取り出されたときの動作を決定します。 オプションは次のとおりです。
  - *操作の必要なし*。 
  - *ワークステーションをロックする* - スマート カードが取り出されたときにワークステーションはロックされます。これにより、ユーザーはスマート カードを持って場所を離れ、なおかつ、保護されたセッションを維持できます。
  - "*ログオフを強制する*" - スマート カードが取り出されると、ユーザーは自動的にログオフされます。
  - "*リモート デスクトップ セッションを切断する*" - スマート カードを取り出すと、ユーザーをログオフさせずにセッションを切断します。 このため、ユーザーは後でスマート カードを挿入し、セッションを再開することも、スマート カード リーダーを装備した別のコンピューターにスマート カードを挿入し、セッションを再開することもできます。もう一度ログオンする必要はありません。 セッションがローカルの場合、このポリシーの機能は [ワークステーションをロックする] と同じになります。
  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **既定値**: ワークステーションをロックする
  
- **SAM アカウントと共有の匿名の列挙をブロックする**  
  このセキュリティ設定では、SAM アカウントと共有の匿名の列挙を許可するかどうかが決定されます。 Windows では匿名ユーザーがドメイン アカウントとネットワーク共有の名前の列挙など、特定の操作を行うことを許可しています。 これは、たとえば管理者が、相互信頼関係のない信頼される側のドメイン内のユーザーにアクセス許可を付与するのに便利です。 SAM アカウントおよび共有の匿名の列挙を許可しない場合は、このポリシーを "*はい*" に設定します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **既定値**: はい
  
- **空のパスワードを使用したリモート ログオンをブロックする**  
  このセキュリティ設定では、パスワードで保護されていないローカル アカウントを使用して物理的なコンピューター コンソール以外の場所からログオンできるようにするかどうかが決定されます。 有効にすると、パスワードで保護されていないローカル アカウントには、そのコンピューターのキーボードを使用してログオンする必要があります。 

  *警告*: 物理的に安全な場所に置かれていないコンピューターでは、すべてのローカル ユーザー アカウントに対して常に強力なパスワード ポリシーが適用される必要があります。 そうしないと、パスワードのないユーザー アカウントを使用し、コンピューターに物理的にアクセスできるすべてのユーザーがコンピューターにログオンできてしまいます。 これは、持ち運びができるコンピューターの場合に特に重要です。 

  Everyone グループにこのセキュリティ ポリシーを適用すると、すべてのユーザーがリモート デスクトップ サービスを使用してログオンできなくなります。 ドメイン アカウントを使用するログオンにはこの設定は影響しません。 リモートからの対話型ログオンを使用するアプリケーションでは、この設定を回避できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **既定値**: はい
  
- **Standard user elevation prompt behavior\(標準ユーザーに対する昇格時のプロンプトの動作\)**  
  このポリシー設定では、標準ユーザーに対する昇格時のプロンプトの動作を制御します。 
  - "*昇格要求を自動的に拒否する*" - 操作で特権の昇格が必要な場合、構成可能なアクセス拒否エラー メッセージが表示されます。 デスクトップの実行を標準ユーザーが行う企業では、ヘルプ デスクへの問い合わせを減らすためにこの設定が選択される場合があります。 
  - "*セキュリティで保護されたデスクトップで資格情報を要求する*" - 操作で特権の昇格が必要になると、ユーザーはセキュリティで保護されたデスクトップ上で別のユーザー名とパスワードを入力するように求められます。 ユーザーが有効な資格情報を入力すると、適用可能な特権で操作が続行されます。 
  - "*資格情報を要求する*" - 操作で特権の昇格が必要になると、ユーザーは管理者のユーザー名とパスワードを入力するように求められます。 ユーザーが有効な資格情報を入力すると、適用可能な特権で操作が続行されます。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **既定値**: 昇格要求を自動的に拒否する
  
- **Require admin approval mode for administrators (管理者に管理者承認モードを要求する)**  
  このポリシー設定は、コンピューターのすべてのユーザー アカウント制御 (UAC) ポリシー設定の動作を制御します。 このポリシー設定を変更した場合、コンピューターを再起動する必要があります。 オプションは次のとおりです。   
  - "*未構成*" - 管理者承認モードと関連するすべての UAC ポリシー設定が無効になります。 注: このポリシー設定を無効にすると、オペレーティング システムのセキュリティが全体的に低下したという通知が Security Center からあります。 
  - "*はい*" - 管理者承認モードが有効になります。 組み込まれている管理者アカウントや管理者グループのその他のすべてのユーザーが管理者承認モードで実行することを許可するには、このポリシーを有効にし、関連する UAC ポリシー設定を正しく設定する必要があります。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **既定値**: はい
  
- **Prevent anonymous enumeration of SAM accounts (SAM アカウントの匿名の列挙を防ぐ)**  
  このセキュリティ設定は、コンピューターに対する匿名接続にどのようなアクセス許可を追加付与するかを決定します。 Windows では匿名ユーザーがドメイン アカウントとネットワーク共有の名前の列挙など、特定の操作を行うことを許可しています。 これは、たとえば管理者が、相互信頼関係のない信頼される側のドメイン内のユーザーにアクセス許可を付与するのに便利です。 このセキュリティ オプションでは、次のような追加の制限が匿名接続に課せられます。 
  - "*はい*" - SAM アカウントの列挙を許可しません。 このオプションでは、リソースに対するセキュリティのアクセス許可の Everyone を認証されたユーザーに置き換えます。
  - "*未構成*" - 追加の制限はありません。 既定のアクセス許可が使用されます。  
  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **既定値**: はい
  
- **Allow remote calls to security accounts manager (セキュリティ アカウント マネージャーへのリモート呼び出しを許可する)**  
  このポリシー設定では、SAM へのリモート rpc 接続を制限することができます。 これを選択しない場合、既定のセキュリティ記述子が使用されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **既定値**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode (管理者承認モードを使用する)**  
  このポリシー設定は、組み込みの管理者アカウントの管理者承認モードの動作を制御します。 オプションは次のとおりです。 
  - "*はい*" - あらかじめ登録された Administrator アカウントでは、管理者承認モードが使用されます。 既定では、特権の昇格が必要な操作では、ユーザーにその操作の承認が求められます。 
  - "*未構成*" - あらかじめ登録された Administrator アカウントでは、すべてのアプリケーションが完全な管理特権で実行されます。 

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **既定値**: はい
  
- **Allow UI access applications for secure locations (セキュリティで保護された場所に対して UI アクセス アプリケーションを許可する)**  
  このポリシー設定は、標準ユーザーに対して昇格がプロンプトされたときにセキュリティで保護されたデスクトップを、ユーザー インターフェイス アクセシビリティ (UIAccess または UIA) プログラムが自動的に無効にできるかどうかを制御します。 
  - "*はい*" - Windows リモート アシスタンスなどの UIA プログラムは、昇格時のプロンプトに対してセキュリティで保護されたデスクトップを自動的に無効にします。 "ユーザー アカウント コントロールを無効にしない場合: 昇格のプロンプト時にセキュリティで保護されたデスクトップに切り替える" ポリシー設定を無効にしない場合、セキュリティで保護されたデスクトップではなく、対話ユーザーのデスクトップにプロンプトが表示されます。 
  - "*未構成*" - セキュリティで保護されたデスクトップを無効にするには、対話型のデスクトップのユーザーが無効にするか、"ユーザー アカウント制御: 昇格のプロンプト時にセキュリティで保護されたデスクトップに切り替える" ポリシー設定を無効にする必要があります。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **既定値**: はい

- **アプリケーションのインストールを検出し、昇格をプロンプトする**  
  このポリシー設定は、コンピューターへのアプリケーションのインストールの検出動作を制御します。 オプションは次のとおりです。 
  - "*有効*" - 特権の昇格を必要とするアプリケーション インストール パッケージが検出されると、ユーザーは管理ユーザー名とパスワードを入力するように求められます。 ユーザーが有効な資格情報を入力すると、適用可能な特権で操作が続行されます。 
  - "*無効*" - アプリケーション インストール パッケージは検出されず、昇格は求められません。 グループ ポリシー ソフトウェア インストールや Systems Management Server (SMS) などの委任されたインストール技術を活用している、標準ユーザー デスクトップを実行する企業では、この機能を無効にします。 この場合、インストーラーの検出は不要です。  
  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **既定値**: はい
  
- **Prevent storing LAN manager hash value on next password change (次のパスワードの変更で LAN Manager のハッシュ値を保存しない)**  
  このセキュリティ設定は、次のパスワードの変更で、新しいパスワードの LAN Manager (LM) のハッシュ値を保存するかどうかを決定します。 LM ハッシュは、暗号化強度の高い Windows NT ハッシュと比べて比較的弱く、攻撃されやすいです。 LM ハッシュはセキュリティ データベースのローカル コンピューターに保存されるので、セキュリティ データベースが攻撃された場合、パスワードが漏えいすることがあります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **既定値**: はい

- **各ユーザーの場所へのファイルまたはレジストリの書き込みエラーを仮想化する**  
  このポリシー設定は、アプリケーションの書き込みエラーを、定義されているレジストリおよびファイル システムの場所にリダイレクトするかどうかを制御します。 このポリシー設定は、管理者として実行されるアプリケーションが、実行時のアプリケーション データを *%ProgramFiles%* 、 *%Windir%* 、 *%Windir%\system32*、または *HKLM\Software* に書き込むよう緩和します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **既定値**: はい

## <a name="ms-security-guide"></a>MS Security Guide (MS セキュリティ ガイド)  
詳細については、Windows の「[Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide)」(ポリシー CSP - MSSecurityGuide) を参照してください。  

- **Apply UAC restrictions to local accounts on network logon (ネットワーク ログオン時にローカル アカウントに UAC 制限を適用する)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **既定値**: 有効
  
- **SMB v1 client driver start configuration (SMB v1 クライアント ドライバーの開始時の構成)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **既定値**: 無効なドライバー
  
- **SMB v1 server (SMB v1 サーバー)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **既定値**: 無効
  
- **ダイジェスト認証**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **既定値**: 無効
  
- **Structured exception handling overwrite protection (構造化例外処理の上書き保護)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **既定値**: 有効
  
## <a name="mss-legacy"></a>MSS Legacy (MSS レガシ)  
詳細については、Windows の「[Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy)」(ポリシー CSP - MSSLegacy) を参照してください。  

- **Network IP source routing protection level (ネットワーク IP ソース ルーティングの保護レベル)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **既定値**: 最高の保護  
  
- **Network ignore NetBIOS name release requests except from WINS servers (ネットワークが WINS サーバーからのを除く NetBIOS 名のリリース要求を無視する)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **既定値**: 有効
  
- **Network IPv6 source routing protection level (ネットワーク IPv6 ソース ルーティングの保護レベル)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **既定値**: 最高の保護

- **Network ICMP redirects override OSPF generated (ネットワーク ICMP が生成されたオーバーライド OSPF をリダイレクトする)**  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **既定値**: 無効
  
## <a name="power"></a>電源  
詳細については、Windows の「[Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power)」(ポリシー CSP - Power) を参照してください。  

- **Require password on wake while plugged in (電源接続中のスリープ解除時にパスワードを要求する)**  
  このポリシー設定では、システムのスリープ状態を解除するときに、ユーザーにパスワードを要求するかどうかを指定します。 このポリシー設定を有効にした場合、または構成しなかった場合、ユーザーはシステムのスリープ状態を解除するときにパスワードを要求されます。 このポリシー設定を無効にすると、ユーザーはシステムのスリープ状態を解除するときにパスワードを要求されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **既定値**: 有効
  
- **Standby states when sleeping while on battery (バッテリ使用中のスリープ状態時のスタンバイ状態)**  
  このポリシー設定では、コンピューターをスリープ状態にするときに Windows でスタンバイ状態を使用できるかどうかを管理します。 このポリシー設定を有効にしたり、構成しない場合、Windows はスタンバイ状態を使用してコンピューターをスリープ状態にします。 このポリシー設定を無効にすると、スタンバイ状態 (S1-S3) は許可されなくなります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **既定値**: 無効
  
- **Standby states when sleeping while plugged in (電源接続中のスリープ状態時のスタンバイ状態)**  
  このポリシー設定では、コンピューターをスリープ状態にするときに Windows でスタンバイ状態を使用できるかどうかを管理します。 このポリシー設定を有効にしたり、構成しない場合、Windows はスタンバイ状態を使用してコンピューターをスリープ状態にします。 このポリシー設定を無効にすると、スタンバイ状態 (S1-S3) は許可されなくなります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **既定値**: 無効
  
- **Require password on wake while on battery (バッテリ使用中のスリープ解除時にパスワードを要求する)**  
  このポリシー設定では、システムのスリープ状態を解除するときに、ユーザーにパスワードを要求するかどうかを指定します。 このポリシー設定を有効にした場合、または構成しなかった場合、ユーザーはシステムのスリープ状態を解除するときにパスワードを要求されます。 このポリシー設定を無効にすると、ユーザーはシステムのスリープ状態を解除するときにパスワードを要求されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **既定値**: 有効

## <a name="remote-assistance"></a>リモート アシスタンス
- **リモートアシスタンスの要請**  
  このポリシー設定を使用すると、このコンピューター上で要請されたリモート アシスタンスを有効または無効に設定することができます。 
  - "*このポリシー設定を有効にすると*"、このコンピューターのユーザーは電子メールやファイル転送を使用して他のユーザーに支援を求めることができます。 また、ユーザーはインスタント メッセージング プログラムを使用してこのコンピューターへの接続を許可することができ、管理者は追加のリモート アシスタンスの設定を構成することができます。 
  - "*このポリシー設定を無効にすると*"、このコンピューターのユーザーは電子メールやファイル転送を使用して他のユーザーに支援を求めることができません。 また、ユーザーは、インスタント メッセージング プログラムを使用してこのコンピューターへの接続を許可することができなくなります。 
  - "*このポリシー設定を構成しない場合*" は、コントロール パネルの [システムのプロパティ] からユーザーが自分で、要請されたリモート アシスタンスを有効または無効に設定することができます。 ユーザーは、リモート アシスタンスの設定を構成することもできます。 

  このポリシー設定を有効にすると、ヘルパーによるリモート アシスタンスの提供に、次の 2 つの方法が使用できます。[ヘルパーにコンピューターの閲覧のみを許可する] と [ヘルパーにコンピューターのリモート制御を許可する] です。 [チケットの最大時間] ポリシー設定は、電子メールまたはファイル転送を使用して作成されたリモートアシスタンスの招待が開いたままになる時間の制限を設定します。 [電子メールの招待の送信方法を選択する] 設定によって、リモート アシスタンスの招待の送信に使用する電子メール規格を指定できます。 お使いの電子メールのプログラムによって、Mailto 規格 (招待を受信する側がインターネット リンク経由で接続) か、または SMAPI (簡易 MAPI) 規格 (招待を電子メールのメッセージに添付) を使用できます。 Windows Vista では SMAPI だけがサポートされている方法であるため、このポリシー設定は使用できません。 このポリシー設定を有効にした場合は、リモート アシスタンスが通信できるように、適切なファイアウォールの例外を有効にする必要もあります。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067198)

  **既定**: リモートアシスタンスを無効にする

  *リモートアシスタンスを有効*にするように設定した場合は、次の追加設定を構成します。  
  - **リモートアシスタンスの要請アクセス許可**  
    **既定値**: ビュー  

  - **チケットの最大有効時間値**  
    **既定値**: *[未構成]*  

  - **チケットの最大有効期間**  
    **既定値**: Minutes    

  - **電子メールの招待方法**  
    **既定**: 簡易 MAPI

  
## <a name="remote-desktop-services"></a>リモート デスクトップ サービス  
詳細については、Windows ドキュメントの「[Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices)」(ポリシー CSP - RemoteDesktopServices) を参照してください。  

- **Block password saving (パスワードの保存をブロックする)**  
  リモート デスクトップ接続からこのコンピューター上でパスワードを保存できるようにするかどうかを制御します。 この設定を有効にすると、リモート デスクトップ接続のパスワードを保存するためのチェック ボックスが使用できなくなり、以降、ユーザーはパスワードを保存できなくなります。 ユーザーがリモート デスクトップ接続で RDP ファイルを開いて設定を保存した場合、RDP ファイルに以前から存在していたパスワードはすべて削除されます。 この設定を無効または未構成にする場合、ユーザーはリモート デスクトップ接続でパスワードを保存できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **既定値**: 有効
  
- **Secure RPC communication (セキュリティで保護された RPC 通信)**  
  リモート デスクトップ セッション ホスト サーバーに、クライアントすべてとのセキュリティで保護された RPC 通信が必要か、またはセキュリティで保護されていない通信を許可するかどうかを指定します。 この設定を使って、認証されて暗号化された要求のみを許可することで、クライアントとの RPC 通信のセキュリティを強化できます。 状態が有効に設定されている場合、リモート デスクトップ サービスは、セキュリティで保護された要求をサポートする RPC クライアントからの要求を受け入れて、信用されていないクライアントとのセキュリティで保護されていない通信を許可しません。 状態が無効に設定されている場合は、リモート デスクトップ サービスは RPC トラフィックすべてのセキュリティを常に要求します。 しかし、要求に応答しない RPC クライアントにはセキュリティで保護されていない通信が許可されます。 状態が未構成に設定されている場合は、セキュリティで保護されていない通信は許可されます。 注: RPC インターフェイスがリモート デスクトップ サービスの管理または構成に使用されています。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **既定値**: 有効
  
- **Block drive redirection (ドライブのリダイレクトをブロックする)**  
  このポリシー設定は、リモート デスクトップ サービス セッションで、クライアント ドライブのマッピングをしないようにするかどうかを指定します (ドライブ リダイレクト)。 既定では、RD セッション ホスト サーバーは接続時に自動的にクライアント ドライブをマップします。 マップされたドライブは、エクスプローラーまたは [コンピューター] のセッション フォルダー ツリーに、 *\<コンピューター名>* の *\<ドライブ文字>* という形式で表示されます。 このポリシー設定を使ってこの動作をオーバーライドできます。 このポリシー設定を有効にすると、クライアント ドライブのリダイレクトはリモート デスクトップ サービス セッションでは許可されません。また、クリップボードでのファイル コピーのリダイレクトは、Windows Server 2003、Windows 8、および Windows XP を実行しているコンピューターでは許可されません。 このポリシー設定を無効にすると、クライアント ドライブのリダイレクトは常に許可されます。 また、クリップボードのリダイレクトを許可すると、クリップボードでのファイル コピーのリダイレクトは常に許可されます。 このポリシー設定を構成しなかった場合、クライアント ドライブのリダイレクトおよびクリップボードでのファイル コピーのリダイレクトはグループ ポリシー レベルでは指定されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **既定値**: 有効
  
- **Prompt for password upon connection (接続するときにパスワードを要求する)**  
  このポリシー設定は、接続時にクライアントが、リモート デスクトップ サービスによって常にパスワードの入力を要求されるかどうかを指定します。 リモート デスクトップ サービスにログオンしているユーザーが、リモート デスクトップ接続のクライアントでパスワードを既に提供していても、この設定を使ってパスワードの入力を強制できます。 既定では、リモート デスクトップ サービスによりユーザーはリモート デスクトップ接続のクライアントにパスワードを入力して自動的にログオンできます。 このポリシー設定を有効にすると、ユーザーはリモート デスクトップ接続のクライアントでパスワードを供給しても、リモート デスクトップ サービスに自動的にログオンできません。 ユーザーは、ログオンするためにパスワードを要求されます。 このポリシー設定を無効にすると、ユーザーは常にリモート デスクトップ接続のクライアントでパスワードを供給することでリモート デスクトップ サービスに自動的にログオンできます。 このポリシー設定を構成しなかった場合、自動ログオンはグループ ポリシー レベルでは指定されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **既定値**: 有効
  
- **Remote desktop services client connection encryption level (リモート デスクトップ サービス クライアント接続の暗号化レベル)**  
  リモート デスクトップ プロトコル (RDP) 接続時に、クライアント コンピューターと RD セッション ホスト サーバー間の通信をセキュリティで保護するために、特定の暗号化レベルの使用を必要とするかどうかを指定します。 このポリシーは、ネイティブの RDP 暗号化を使用しているときにのみ適用されます。 ただし (SSL 暗号化と異なり) ネイティブ RDP 暗号化は推奨されません。 SSL 暗号化にこのポリシーは適用されません。 このポリシー設定を有効にした場合、リモート接続時のクライアントと RD セッション ホスト サーバー間のすべての通信で、この設定で指定された暗号化方法を使用する必要があります。 既定では、暗号化レベルは [高] に設定されています。 次の暗号化方法を利用できます。  
  - "*高*" - [高] 設定では、強力な 128 ビット暗号化を使ってクライアントとサーバー間で送受信されるデータを暗号化します。 この暗号化レベルは、128 ビット クライアント (リモート デスクトップ接続クライアントなど) のみが含まれる環境で使用します。 この暗号化レベルをサポートしていないクライアントは RD セッション ホスト サーバーに接続できません。  
  - "*クライアント互換*" - [クライアント互換] 設定では、クライアントとサーバーの間で送信されるすべてのデータは、クライアントでサポートされている最高のキー強度で暗号化されます。 この暗号化レベルは、128 ビット暗号化をサポートしていないクライアントが含まれる環境で使用します。  
  - "*低*" - [低] 設定では、56 ビット暗号化を使ってクライアントからサーバーへ送信されるデータのみを暗号化します。  
  
  この設定を無効にするか、または構成しない場合は、RD セッション ホスト サーバーへのリモート接続に使用される暗号化レベルは、グループ ポリシーを通じて強制されません。 重要 FIPS 準拠は、システム暗号化を通じて構成できます。 グループ ポリシーの [暗号化、ハッシュ、署名のための FIPS 準拠アルゴリズムを使う] 設定 (場所: "コンピューターの構成\Windows の設定\セキュリティの設定\ローカル ポリシー\セキュリティ オプション")。[FIPS 準拠] 設定では、Microsoft 暗号化モジュールを使用して、Federal Information Processing Standard (FIPS) 140 暗号化アルゴリズムによって、クライアントとサーバー間で送受信されるデータを暗号化および暗号化解除します。 この暗号化レベルは、クライアントと RD セッション ホスト サーバー間の通信で最高レベルの暗号化が必要な場合に使用します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **既定値**: 高
  
## <a name="remote-management"></a>リモート管理  
詳細については、Windows ドキュメントの「[Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement)」(ポリシー CSP - RemoteManagement) を参照してください。  

- **Block storing run as credentials (実行アカウントの資格情報の保存をブロックする)**  
  クライアントの基本認証。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **既定値**: 有効
  
- **Basic authentication (基本認証)**  
  このポリシー設定を使用して、Windows リモート管理 (WinRM) サービスでリモート クライアントからの基本認証を受け付けるかどうかを管理できます。 このポリシー設定を有効にすると、WinRM サービスはリモート クライアントからの基本認証を受け付けます。 このポリシー設定を無効にした場合、または構成しなかった場合は、WinRM サービスはリモート クライアントからの基本認証を受け付けません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **既定値**: 無効
  
- **Block client digest authentication (クライアントのダイジェスト認証をブロックする)**  
  このポリシー設定を使用して、Windows リモート管理 (WinRM) クライアントでダイジェスト認証を使用するかどうかを管理できます。 このポリシー設定を有効にすると、WinRM クライアントでダイジェスト認証は使用されません。 このポリシー設定を無効にした場合、または構成しなかった場合は、WinRM クライアントでダイジェスト認証が使用されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **既定値**: 有効
  
- **暗号化されていないトラフィック**  
  このポリシー設定を使用して、Windows リモート管理 (WinRM) サービスで、暗号化されていないメッセージをネットワーク経由で送受信するかどうかを管理できます。 このポリシー設定を有効にすると、WinRM クライアントは、暗号化されていないメッセージをネットワーク経由で送受信します。 このポリシー設定を無効にした場合、または構成しなかった場合は、WinRM クライアントは、暗号化されたメッセージのみをネットワーク経由で送受信します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **既定値**: 無効
  
- **クライアントが暗号化されていないトラフィック**  
  このポリシー設定を使用して、Windows リモート管理 (WinRM) クライアントで、暗号化されていないメッセージをネットワーク経由で送受信するかどうかを管理できます。 このポリシー設定を有効にすると、WinRM クライアントは、暗号化されていないメッセージをネットワーク経由で送受信します。 このポリシー設定を無効にした場合、または構成しなかった場合は、WinRM クライアントは、暗号化されたメッセージのみをネットワーク経由で送受信します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **既定値**: 無効
  
- **Client basic authentication (クライアントの基本認証)**  
  このポリシー設定を使用して、Windows リモート管理 (WinRM) クライアントで基本認証を使用するかどうかを管理できます。 このポリシー設定を有効にすると、WinRM クライアントで基本認証が使用されます。 WinRM が HTTP トランスポートを使用するように構成されている場合は、ユーザー名とパスワードがクリア テキストとしてネットワーク経由で送信されます。 このポリシー設定を無効にした場合、または構成しなかった場合は、WinRM クライアントで基本認証は使用されません。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **既定値**: 無効
  
## <a name="remote-procedure-call"></a>リモート プロシージャ コール  
詳細については、Windows ドキュメントの「[Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall)」(ポリシー CSP - RemoteProcedureCall) を参照してください。  

- **RPC unauthenticated client options (RPC の認証されていないクライアント オプション)**  
  このポリシー設定は、RPC サーバーに接続する認証されていない RPC クライアントを RPC サーバー ランタイムが処理する方法を制御します。 このポリシー設定は、すべての RPC アプリケーションに影響します。 ドメイン環境では、このポリシー設定はグループ ポリシーの処理自体を含む広範な機能に影響する可能性があるため、注意して使用する必要があります。 このポリシー設定の変更を元に戻す場合、影響するコンピューターごとに手動での操作が必要になることがあります。 このポリシー設定は、ドメイン コントローラーには適用しないでください。 このポリシー設定を無効にすると、RPC サーバー ランタイムは Windows クライアントでは [認証済み] の値を使用し、このポリシー設定をサポートする Windows Server バージョンでは [なし] の値を使用します。 このポリシー設定を構成しない場合、設定は無効のままになります。 RPC サーバー ランタイムは、Windows クライアントでは [認証済み] の値の使用が、このポリシー設定をサポートする Server SKU では [なし] の値の使用が有効にされた場合と同じように動作します。 このポリシー設定を有効にすると、コンピューター上の RPC サーバーに接続する、認証されていない RPC クライアントを制限するよう RPC サーバー ランタイムに指示します。 サーバーとの通信時に名前付きパイプを使用している場合、または RPC セキュリティを使用している場合に、クライアントは認証済みとして認識されます。 このポリシー設定で選択された値によっては、未認証のクライアントがアクセスできるよう明示的に要求した RPC インターフェイスは、この制限から除外される場合もあります。  
  - *[なし]* では、このポリシー設定が適用されるコンピューター上で実行されている RPC サーバーへの、すべての RPC クライアントの接続を許可します。 
  - *[認証済み]* では、このポリシー設定が適用されるコンピューター上で実行されている RPC サーバーへの、認証済み (前の定義による) の RPC クライアントのみの接続を許可します。 除外を要求したインターフェイスは除外されます。 
  - *[認証済み (例外なし)]* では、このポリシー設定が適用されるコンピューター上で実行されている RPC サーバーへの、認証済み (前の定義による) の RPC クライアントのみの接続を許可します。 例外は許可されません。 注: このポリシー設定は、システムが再起動されるまで適用されません。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **既定値**: 認証済み

## <a name="search"></a>検索 
詳細については、Windows ドキュメントの「[Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)」(ポリシー CSP - Search) を参照してください。  

- **Disable indexing encrypted items (暗号化されたアイテムのインデックス作成を無効にする)**  
  アイテムのインデックス作成を許可または禁止します。 これは Windows Search Indexer 用のスイッチです。Windows 情報保護 (WIP) で保護されたファイルなど、暗号化されたアイテムにインデックスを付けるかどうかを制御します。 このポリシーが有効な場合、WIP で保護されたアイテムにインデックスが付けられ、それらのメタデータは暗号化されていない場所に保存されます。 メタデータには、ファイル パスや変更日などがあります。 このポリシーが無効な場合、WIP で保護されたアイテムにはインデックスが付けられず、Cortana またはエクスプローラーの結果に表示されません。 また、デバイスに WIP で保護されたメディア ファイルが多数ある場合は、写真や Groove アプリのパフォーマンスにも影響が出る可能性があります。  
  [詳細情報]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **既定値**: はい
  
## <a name="smart-screen"></a>スマート スクリーン  
詳細については、Windows ドキュメントの「[Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen)」 (ポリシー CSP - SmartScreen) を参照してください。  

- **Block execution of unverified files (確認されていないファイルの実行をブロックする)**  
  確認されていないファイルをユーザーが実行しないようにします。 
  - "*未構成*" - 従業員は SmartScreen の警告を無視し、悪意のあるファイルを実行できます。 
  - "*はい*" - 従業員は SmartScreen の警告を無視して、悪意のあるファイルを実行することはできません。

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **既定値**: はい

- **Require SmartScreen for apps and files (アプリとファイルに SmartScreen を要求する)**  
  IT 管理者が Windows 用の SmartScreen を構成することを許可します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **既定値**: はい
  
## <a name="system"></a>System (システム)  
詳細については、Windows ドキュメントの「[Policy CSP - System ](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system)」(ポリシー CSP - System) を参照してください。  

- **System boot start driver initialization (システム ブート開始ドライバーの初期化)**  
  このポリシー設定を使用すると、起動時マルウェア対策のブート開始ドライバーによって決まる分類に基づいて、どのブート開始ドライバーを初期化するかを指定できます。 起動時マルウェア対策のブート開始ドライバーは、各ブート開始ドライバーに次のような分類を返します。 
  - "*良好*" - ドライバーが署名されていて、改ざんされていません。  
  - *不良* - ドライバーがマルウェアとして認識されました。 既知の不良のドライバーの初期化を許可しないことをお勧めします。 
  - "*不良 (ブートに不可欠)* " - ドライバーはマルウェアとして認識されましたが、このドライバーを読み込まなければコンピューターを正常に起動できません。 
  - "*不明*" - このドライバーは、マルウェアの検出アプリケーションで証明されていないため、起動時マルウェア対策のブート開始ドライバーによって分類されていません。  

  このポリシー設定を有効にした場合、次にコンピューターを起動したときに初期化するブート開始ドライバーを選択できます。 このポリシー設定を無効にした場合、または構成しなかった場合、良好、不明、または不良 (ブートに不可欠) と判定されたブート開始ドライバーは初期化され、不良と判定されたドライバーの初期化はスキップされます。 お使いのマルウェアの検出アプリケーションに起動時マルウェア対策のブート開始ドライバーが含まれない場合、または起動時マルウェア対策のブート開始ドライバーが無効になっている場合、この設定は影響せず、すべてのブート開始ドライバーが初期化されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **既定値**: 良好、不明、および不良 (ブートに不可欠)


## <a name="wi-fi"></a>Wi-Fi  
詳細については、Windows ドキュメントの「[Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)」(ポリシー CSP - Wifi) を参照してください。  

- **インターネット共有をブロックする**  
  インターネット共有がデバイスで可能かどうかを指定します。   
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **既定値**: はい  

- **Block Automatically connecting to Wi-Fi hotspots (Wi-Fi ホットスポットへの自動接続をブロックする)**  
  デバイスが Wi-Fi ホットスポットに自動的に接続するのを許可または禁止します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **既定値**: はい  
  
## <a name="windows-connection-manager"></a>Windows 接続マネージャー  
詳細については、Windows ドキュメントの「[Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager)」(ポリシー CSP - WindowsConnectionManager) を参照してください。  

- **Block connection to non-domain networks (非ドメイン ネットワークへの接続をブロックする)**  
  このポリシー設定は、コンピューターがドメイン ベースのネットワークと非ドメイン ベースのネットワークに同時に接続することを禁止します。 このポリシー設定を有効にした場合、コンピューターは次の状況で自動または手動のネットワーク接続試行に応答します。 
  - 自動接続試行 - コンピューターがドメイン ベースのネットワークに既に接続している場合は、非ドメイン ネットワークへの自動接続試行がすべてブロックされます。 コンピューターが非ドメイン ベースのネットワークに既に接続している場合は、ドメイン ネットワークへの自動接続試行がブロックされます。 
  - 手動接続試行 - コンピューターがイーサネット以外のメディアを介して非ドメイン ベースのネットワークまたはドメイン ベースのネットワークに接続しているときに、ユーザーがこのポリシー設定に違反して他のネットワークへの手動接続を作成しようとした場合は、既存のネットワーク接続が切断され、手動接続が許可されます。 コンピューターがイーサネットを介して非ドメイン ベースのネットワークまたはドメイン ベースのネットワークに接続しているときに、ユーザーがこのポリシー設定に違反して他のネットワークへの手動接続を作成しようとした場合は、既存のイーサネット接続が保持され、手動接続試行がブロックされます。  

  このポリシー設定を構成しなかった場合、または無効にした場合、コンピューターはドメイン ネットワークと非ドメイン ネットワークの両方に同時に接続できます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **既定値**: 有効
  
## <a name="microsoft-defender"></a>Microsoft Defender  
詳細については、Windows ドキュメントの「[Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)」(ポリシー CSP - Defender) を参照してください。  

- **受信メール メッセージをスキャンする**  
  メールのスキャンを許可または禁止します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **既定値**: はい  

- **Office apps launch child process type (Office アプリの子プロセスの起動の種類)**  
  Office アプリは子プロセスを作成できなくなります。 これには、Word、Excel、PowerPoint、OneNote、および Access が含まれます。 これは一般的なマルウェアの動作です。特に、Office アプリを使用して悪意のある実行可能ファイルを起動またはダウンロードしようとするマクロベースの攻撃の場合に一般的です。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **既定値**: ブロック
  
- **Defender sample submission consent type (Defender のサンプル送信の同意の種類)**  
  Microsoft Defender でデータを送信するためのユーザーの同意レベルを確認します。 必要な同意が既に与えられている場合、Microsoft Defender からそれらが送信されます。 それ以外の場合 (かつユーザーが "確認しない" を指定した場合)、(Defender/AllowCloudProtection が許可されている場合は) データを送信する前にユーザーの同意を求める UI が起動します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **既定値**: 安全なサンプルを自動的に送信します 
  
- **Signature update interval (in hours) (署名更新間隔 (時単位))**  
  Defender の署名更新間隔 (時間)
  
  **既定値**: 4
  
- **Script downloaded payload execution type (スクリプトでダウンロードされたペイロードの実行タイプ)**  
  Defender スクリプト ダウンロード ペイロード実行タイプ
  
  **既定値**: ブロック
  
- **Prevent credential stealing type (資格情報盗難防止タイプ)**  
  Microsoft Defender Credential Guard では、仮想化ベースのセキュリティを使用してシークレットを分離し、特権を持つシステム ソフトウェアだけがアクセスできるようにします。 これらのシークレットへの不正アクセスは、Pass-the-Hash や Pass-The-Ticket などの、資格情報を盗む攻撃につながる可能性があります。 Microsoft Defender Credential Guard では、NTLM パスワード ハッシュ、Kerberos のチケット保証チケット、およびアプリケーションによってドメイン資格情報として格納された資格情報を保護することで、これらの攻撃を防ぎます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **既定値**: 有効にする

- **Email content execution type (電子メール コンテンツ実行タイプ)**  
  このルールでは、次の種類のファイルが Microsoft Outlook または Web メール (Gmail.com や Outlook.com など) に表示された電子メールから実行または起動されるのをブロックします: 実行可能ファイル (例: .exe、.dll、.scr)、スクリプト ファイル (例: PowerShell .ps、VisualBasic .vbs、JavaScript .js)、スクリプト アーカイブ ファイル。  
  [詳細情報](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail) 
  
  **既定値**: ブロック

- **子プロセスでの Adobe Reader の起動**  

  **既定値**: 有効にする

- **Network protection type (ネットワーク保護タイプ)**  
  このポリシーを使うと、Microsoft Defender Exploit Guard でネットワーク保護 (ブロック/監査) をオンまたはオフにできるようになります。 ネットワーク保護は Microsoft Defender Exploit Guard の機能であり、任意のアプリを使用する従業員がインターネット上のフィッシング詐欺、悪用ホスティング サイト、悪意のあるコンテンツにアクセスするのを防ぎます。 これには、サード パーティ製のブラウザーが危険なサイトに接続するのを防ぐことが含まれます。 値の型は整数です。 この設定を有効にした場合、ネットワーク保護が有効になり、従業員では無効にできません。 その動作は次のオプションで制御できます: ブロックと監査。 このポリシーを "ブロック" オプションで有効にした場合、ユーザーとアプリは危険なドメインに接続するのをブロックされます。 このアクティビティは、Microsoft Defender セキュリティ センターで表示することができます。 このポリシーを "監査" オプションで有効にした場合、ユーザー/アプリは危険なドメインに接続するのをブロックされません。 ただし、それでもこのアクティビティは Microsoft Defender セキュリティ センターで表示されます。 このポリシーを無効にした場合、ユーザー/アプリは危険なドメインに接続するのをブロックされません。 ネットワーク アクティビティは、Microsoft Defender セキュリティ センターに表示されません。 このポリシーを構成しない場合、ネットワーク ブロックは既定で無効になります。  
  [詳細情報](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)  
  
  **既定値**: 有効にする
  
- **Defender schedule scan day (Defender のスキャン日スケジュール)**  
  Defender のスキャン日スケジュール。
  
  **既定値**: 毎日
  
- **Cloud-delivered protection (クラウドによる保護)**  
  PC を最大限に保護するため、Microsoft Defender では検出した問題についての情報が Microsoft に送信されます。 Microsoft は、その情報を分析し、報告者や他の顧客に影響する問題について詳細に把握して、強化されたソリューションを提供します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **既定値**: はい  

- **Defender potentially unwanted app action (Defender の望ましくないアプリに対するアクション)**  
  Microsoft Defender ウイルス対策に備わっている望ましくない可能性があるアプリケーション (PUA) 保護機能では、PUA を特定して、ご使用のネットワーク内のエンドポイントへのダウンロードやインストールをブロックできます。 これらのアプリケーションはウイルス、マルウェア、または他の種類の脅威とは見なされませんが、パフォーマンスや使用に悪影響を与えるアクションをエンドポイントで実行する可能性があります。 PUA は、評価が低いと考えられるアプリケーションを指すこともあります。 一般的な PUA の動作は次のとおりです。さまざまな種類のソフトウェア バンドル。Web ブラウザーへの広告挿入。問題を検出し、エラーの修正に対して支払いを要求するが、エンドポイント上に残っていて変更や最適化を何も行わないドライバーやレジストリのオプティマイザー ("偽装ウイルス対策" プログラムとも呼ばれます)。 これらのアプリケーションは、ネットワークがマルウェアに感染するリスクを高め、識別困難なマルウェア感染を引き起こし、アプリケーションのクリーンアップで IT リソースを浪費させる可能性があります。  
  [詳細情報](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **既定値**: ブロック  

- **Script obfuscated macro code type (スクリプト難読化マクロ コード タイプ)**  
  マルウェアや他の脅威は、一部のスクリプト ファイルに悪意のあるコードを難読化または隠ぺいしようとすることがあります。 このルールは、難読化されているらしいスクリプトが実行するのを防ぎます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **既定値**: ブロック
  
- **フル スキャン中に、リムーバブル ドライブをスキャンする**  
  Microsoft Defender が、フル スキャン中にリムーバブル ドライブ (フラッシュ ドライブなど) 内の悪意のあるソフトウェアや望ましくないソフトウェアをスキャンできるようにします。 Microsoft Defender ウイルス対策では、実行する前に USB デバイス上のすべてのファイルがスキャンされます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **既定値**: はい  
  
- **アーカイブ ファイルをスキャンする**  
  Defender はアーカイブ ファイルをスキャンします。
  
  **既定値**: はい
  
- **動作の監視**  
  Microsoft Defender の動作監視機能を許可または禁止します。 Windows 10 内蔵のこれらのセンサーでは、オペレーティング システムから動作信号を収集して処理し、プライベート クラウドに他から切り離されて存在する Microsoft Defender ATP インスタンスにこのセンサー データを送信します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **既定値**: はい

- **ネットワーク フォルダーから開いたファイルをスキャンする**  
  ファイルが読み取り専用の場合、ユーザーは検出されたマルウェアを削除できません。
  
  **既定値**: はい

- **Untrusted USB process type (信頼されていない USB 処理タイプ)**  
  このルールでは、管理者は署名されていない実行可能ファイルまたは信頼されていない実行可能ファイルが SD カードも含む USB リムーバブル ドライブから実行されるのを防ぐことができます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **既定値**: ブロック
  
- **Office apps other process injection type (Office アプリによる他のプロセスへの挿入タイプ)**  
  Word、Excel、PowerPoint、OneNote などの Office アプリは、他のプロセスにコードを挿入できません。 これは通常、マルウェアがウイルス対策スキャン エンジンからアクティビティを隠ぺいする試みで、悪意のあるコードを実行するために使用されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **既定値**:  ブロック
  
- **Office macro code allow Win32 imports type (Office のマクロ コードによる Win32 のインポートの許可タイプ)**  
  マルウェアは、Office ファイルのマクロ コードを使用して、Win32 DLL をインポートして読み込んだ後、それを使用して API 呼び出しを行い、システム全体にさらに感染させることができます。 このルールは、Win32 DLL をインポートできるマクロ コードが含まれる Office ファイルのブロックを試みます。 これには、Word、Excel、PowerPoint、OneNote が含まれます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **既定値**: ブロック  
  
- **Defender cloud block level (Defender クラウド ブロック レベル)**  
  Defender のクラウド ブロック レベルです。
  
  **既定値**: 未構成

- **リアルタイム監視**:  
  Defender では、リアルタイムの監視が必要です。
  
  **既定値**: はい
 
- **子プロセスでの Office 通信アプリの起動**  

  **既定値**: 有効にする

- **Office apps executable content creation or launch type (Office アプリの実行可能コンテンツの作成または起動タイプ)**  
  このルールの対象は、実行可能ファイルを作成または起動する不審な悪意のあるアドオンとスクリプト (拡張機能) で使用される一般的な動作です。 これは、マルウェアの一般的な手法です。 拡張機能は、Office アプリによって使用されるのをブロックされます。 通常、これらの拡張機能では、特定のタスクを自動化したり、ユーザー作成のアドオン機能を提供したりするスクリプトを実行するために、Windows Scripting Host (.wsh ファイル) が使用されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **既定値**: ブロック

## <a name="microsoft-defender-firewall"></a>Microsoft Defender ファイアウォール  
詳細については、Windows プロトコルのドキュメントの「 [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) 」を参照してください。  

- **ファイアウォールプロファイルドメイン**  
  ルールが属するプロファイルを指定します: ドメイン、プライベート、パブリック。 この値は、ドメインに接続されているネットワークのプロファイルを表します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **受信接続をブロック**  
    **既定値**: はい

  - **送信接続が必要**  
    **既定値**: はい 

  - **着信通知をブロック**  
    **既定値**: はい

  - **ファイアウォールの有効化**  
    **既定値**: 許可

- **ファイアウォールプロファイルパブリック**  
  ルールが属するプロファイルを指定します: ドメイン、プライベート、パブリック。 この値は、パブリック ネットワークのプロファイルを表します。 これらのネットワークは、サーバー ホストで管理者によってパブリックとして分類されます。 分類は、ホストが初めてネットワークに接続したときに行われます。 通常、このようなネットワークは、空港や喫茶店など、ネットワーク内のピアまたはネットワーク管理者が信頼されていない公共の場所にあるものです。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **受信接続をブロック**  
    **既定値**: はい

  - **送信接続が必要**  
    **既定値**: はい 

  - **着信通知をブロック**  
    **既定値**: はい

  - **ファイアウォールの有効化**  
    **既定値**: 許可

  - **グループ ポリシーからの接続セキュリティ ルールをマージしない**  
    **既定値**: はい

  - **グループ ポリシーからのポリシー ルールをマージしない**  
    **既定値**: はい

- **ファイアウォールプロファイルのプライベート**  
  ルールが属するプロファイルを指定します: ドメイン、プライベート、パブリック。 この値は、プライベート ネットワークのプロファイルを表します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **受信接続をブロック**  
    **既定値**: はい

  - **送信接続が必要**  
    **既定値**: はい 

  - **着信通知をブロック**  
    **既定値**: はい

  - **ファイアウォールの有効化**  
    **既定値**: 許可

## <a name="windows-hello-for-business"></a>Windows Hello for Business  
- **使用可能な場合は、高度なスプーフィング対策を要求する**  
  「はい」の場合、デバイスは拡張スプーフィング対策を使用します (使用可能な場合)。 それ以外の場合、スプーフィング対策はブロックされます。 構成されていない場合は、クライアントで行われた構成を優先します。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067192)

  **既定値**: はい

- **Windows Hello for Business の構成**   
    Windows Hello for Business は、パスワード、スマート カード、および仮想スマート カードを置き換えることで Windows にサインインする代替方法です。  

  - *[はい]* に設定すると、このポリシーが有効になり、デバイスは Windows Hello for Business をプロビジョニングします。  
  - [*未構成*] に設定した場合、ベースラインはデバイスのポリシー設定に影響しません。 これは、Windows Hello for Business がデバイスで無効になっていると、無効のままになることを意味します。 有効になっている場合は、有効のままになります。 

  この基準を使用して Windows Hello for Business を無効にすることはできません。 Windows Hello for Business を無効にするには、 [windows の登録](windows-hello.md)を構成するか、 [identity protection](identity-protection-configure.md)のデバイス構成プロファイルの一部としてを使用します。  

  **既定値**: はい

- **PIN に小文字が必要**  
  必要に応じて、ユーザーの PIN には少なくとも1つの小文字を含める必要があります。

  **既定値**: 許可

- **PIN に特殊文字が必要**  
  必要に応じて、ユーザーの PIN には少なくとも1つの特殊文字を含める必要があります。

  **既定値**: 許可

- **PIN の長さの最小値**  
  PIN の最小長は 4 ~ 127 の範囲で指定する必要があります。

  **既定値**: 6

- **PIN に大文字が必要**  
  必要に応じて、ユーザーの PIN には少なくとも1つの大文字を含める必要があります。

  **既定値**: 許可

## <a name="windows-ink-workspace"></a>Windows Ink ワークスペース  
詳細については、Windows ドキュメントの「[Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)」(ポリシー CSP - WindowsInkWorkspace) を参照してください。  

- **Ink Workspace (Ink ワークスペース)**  
  ユーザーに Ink ワークスペースへのアクセスを許可するかどうかを指定します。 
  - "*無効*" - Ink ワークスペースへのアクセスは無効にされます。 機能はオフになります。
  - "*有効*" - Ink ワークスペース機能はオンですが、ユーザーはロック画面上ではそれにアクセスできません。
  - *未構成* - Ink ワークスペース機能がオンにされ、ユーザーはロック画面上でそれを使用できるようになります。  

  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **既定値**: 有効
 
## <a name="windows-powershell"></a>Windows PowerShell  
詳細については、Windows ドキュメントの「[Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell)」 (ポリシー CSP - WindowsPowerShell) を参照してください。  

- **Power shell shell script block logging (PowerShell シェル スクリプト ログ記録ブロック)**  
  このポリシー設定は、Microsoft-Windows-PowerShell/Operational イベント ログへのすべての PowerShell スクリプト入力のログ記録を有効にします。 このポリシー設定を有効にした場合、Windows PowerShell は対話的に、またはオートメーションを介して呼び出された、コマンド、スクリプト ブロック、関数、およびスクリプトの処理をログに記録します。 このポリシー設定を無効にすると、PowerShell スクリプトの入力のログ記録は無効になります。 スクリプト ブロックの呼び出しのログ記録を有効にすると、PowerShell はさらに、コマンド、スクリプト ブロック、関数、またはスクリプトの呼び出しの開始時または停止時にイベントを記録します。 呼び出しのログ記録を有効にすると、大量のイベント ログが生成されます。 注: このポリシー設定は、グループ ポリシー エディターの [コンピューターの構成] と [ユーザーの構成] の両方の下にあります。 [コンピューターの構成] のポリシー設定は、[ユーザーの構成] のポリシー設定よりも優先されます。  
  [詳細情報](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **既定値**: 有効

## <a name="whats-changed-in-the-new-template"></a>新しいテンプレートの変更点
2019年 5*月の MDM セキュリティベースライン*テンプレートは、*プレビュー*テンプレートから次のように変更されています。

### <a name="changes-to-the-baseline-settings"></a>ベースライン設定の変更
以下の設定は、次のいずれかになります。
- この最新バージョンのベースラインに*新しく追加*された。
- この最新のベースラインバージョンから*削除さ*れましたが、以前のバージョンには存在していました。
- 以前のバージョンでの設定の表示から、何らかの方法で*変更*されています。 

*[新規]* [**ロックを超え**](#above-lock)ています:
- **ロック画面から音声でアプリをアクティブ化する**    

" *[新規]* " [**アプリケーション管理**](#application-management): 
- **ユーザーによるインストールの制御をブロックする**  
- **管理者特権での MSI アプリのインストールをブロックする**  

*[削除]* [**Bitlocker**](#bitlocker):  
- ビットロッカーリムーバブルドライブポリシー >**暗号化方法**
- **ビットロッカー固定ドライブポリシー** *(すべての設定)*
- **ビットロッカーシステムドライブポリシー** *(すべての設定)*

" *[新規]* " [**接続**](#connectivity):
- **UNC パスへのセキュリティで保護されたアクセスの構成**

" *[新規]* " [**Device Guard**](#device-guard):
- **仮想化ベースのセキュリティ**


*[新規]* [**DMA ガード**](#dma-guard):
- **Kernel DMA Protection と互換性のない外部デバイスの列挙**  

" *[新規]* " [**Internet Explorer**](#internet-explorer):
- **Explorer のインターネット ゾーンでスクリプトを介してステータス バーを更新する**
- **Internet Explorer のインターネット ゾーンでのファイルのドラッグ アンド ドロップまたはコピーと貼り付け**  
- **Internet Explorer の制限付きゾーンでの .NET Framework 依存コンポーネント**  
- **Internet Explorer のローカル コンピューター ゾーンで Active X コントロールに対してマルウェア対策を実行しない**
- **Internet Explorer の暗号化のサポート**  

*[変更済み]* [**Internet Explorer**](#internet-explorer):
- 既定値が**無効になっ**ている > **internet Explorer のインターネットゾーンの自動プロンプトでファイルのダウンロード**が有効になりました。 プレビューでは、この設定は 有効になっています。

" *[新規]* " [**リモート アシスタンス**](#remote-assistance):  
- **リモートアシスタンスの要請** 
  - **リモートアシスタンスの要請アクセス許可**
  - **チケットの最大有効時間値**  
  - **チケットの最大有効期間**  
  - **電子メールの招待方法**


" *[新規]* " [**Microsoft Defender**](#microsoft-defender):
- **子プロセスでの Adobe Reader の起動**  
- **子プロセスでの Office 通信アプリの起動** 

*[新規]* [ **Microsoft Defender ファイアウォール**](#microsoft-defender-firewall)
- **ファイアウォールプロファイルドメイン**  
  - **受信接続をブロック**  
  - **送信接続が必要**  
  - **着信通知をブロック**  
  - **ファイアウォールの有効化**  
- **ファイアウォールプロファイルパブリック**  
  - **受信接続をブロック**  
  - **送信接続が必要**  
  - **着信通知をブロック**  
  - **ファイアウォールの有効化** 
  - **グループ ポリシーからの接続セキュリティ ルールをマージしない**   
  - **グループ ポリシーからのポリシー ルールをマージしない**  
- **ファイアウォールプロファイルのプライベート**  
  - **受信接続をブロック**  
  - **送信接続が必要**  
  - **着信通知をブロック**  
  - **ファイアウォールの有効化**  

" *[新規]* " [**Windows Hello for Business**](#windows-hello-for-business):  
- **使用可能な場合は、高度なスプーフィング対策を要求する**  
- **Windows Hello for Business の構成**  
- **PIN に小文字が必要** 
- **PIN に特殊文字が必要** 
- **PIN の長さの最小値**  
- **PIN に大文字が必要** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Microsoft Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Microsoft Defender SmartScreen. Enabling this policy turns off Microsoft Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Microsoft defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Microsoft Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Microsoft Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Microsoft Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in WinMMicrosofticrosoftdows Defender to send data. If the required consent has already been granted, Microsoft Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Microsoft Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Microsoft Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Microsoft Defender Exploit Guard. Network protection is a feature of Microsoft Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Microsoft Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Microsoft Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Microsoft Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Microsoft Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Microsoft Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Microsoft Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Microsoft Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Microsoft Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
