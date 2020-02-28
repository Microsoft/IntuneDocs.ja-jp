---
title: Microsoft Intune での BitLocker ポリシーのトラブルシューティングのヒント
titleSuffix: Microsoft Intune
description: Intune ポリシーを使用してデバイスで BitLocker 暗号化を有効にする方法と、ポリシーがデバイスに正常に展開されたことを確認する方法について説明します。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556501"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Microsoft Intune での BitLocker ポリシーのトラブルシューティング

この記事は、Intune 管理者が Intune ポリシーに基づいて Windows 10 デバイスで BitLocker を構成する方法を理解するのに役立ちます。 この記事では、Intune で管理するデバイス上の BitLocker 設定に関する問題をトラブルシューティングする方法についてのガイダンスも提供します。  

## <a name="understanding-bitlocker"></a>BitLocker について

BitLocker ドライブ暗号化は、Microsoft Windows オペレーティング システムによって提供されるサービスで、ユーザーが自分のハード ドライブ上のデータを暗号化できるようにします。 BitLocker では、オペレーティング システム ドライブ、リムーバブル メディア ドライブ、および固定データ ドライブの暗号化をサポートしています。 BitLocker では、機密データの保護を強化するために、256 ビット暗号化の使用もサポートしています。  

Microsoft Intune を使用して Windows 10 デバイスの BitLocker を管理するには、次の方法があります。

- **デバイス構成ポリシー** - エンドポイント保護を管理するためのデバイス構成プロファイルを作成するときに、Intune で特定の組み込みポリシー オプションを使用できます。 これらのオプションを見つけるには、[エンドポイント保護のデバイス プロファイルを作成](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings)し、*[プラットフォーム]* に **[Windows 10 以降]** を選択し、*[設定]* で **[Windows 暗号化]** カテゴリを選択します。 

   使用可能なオプションと機能については、「[Windows の暗号化](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)」を参照してください。

- **セキュリティ ベースライン** - [セキュリティ ベースライン](security-baselines.md)は、Windows デバイスをセキュリティで保護するために、関連するセキュリティ チームによって推奨される設定および既定値の既知のグループです。 *MDM のセキュリティ ベースライン*や *Microsoft Defender ATP ベースライン*のように異なるベースライン ソースで同じ設定を管理できるだけでなく、互いに異なる設定も管理できます。 また、デバイス構成ポリシーで管理するのと同じ設定を管理することもできます。 

Intune に加えて、Modern Standby と HSTI に準拠しているハードウェアでは、これらの機能のいずれかを使用すると、ユーザーがデバイスを Azure AD に参加させるたびに、BitLocker デバイス暗号化が自動的に有効になります。 Azure AD のポータルでは回復キーもバックアップされるため、ユーザーは必要に応じてセルフサービス用の回復キーを取得できます。

また、BitLocker の設定は、グループ ポリシーなどの他の方法で管理することも、デバイス ユーザーが手動で設定することもできます。

デバイスに設定を適用する方法に関係なく、BitLocker ポリシーは [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) を使用してデバイスで暗号化を構成します。 BitLocker CSP は Windows に組み込まれており、Intune が割り当てられたデバイスに BitLocker ポリシーを展開するときに、ポリシーの設定を有効にするために、Windows レジストリに適切な値を書き込むのが、そのデバイスの BitLocker CSP です。

BitLocker の詳細については、次のリソースを参照してください。

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker の概要と要件に関する FAQ](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

これらのポリシーの機能と仕組みの概要を理解したので、BitLocker 設定が Windows クライアントに正しく適用されているかどうかを確認する方法を見ていきましょう。

## <a name="verify-the-source-of-bitlocker-settings"></a>BitLocker 設定のソースを確認する

Windows 10 デバイスで BitLocker の問題を調査するときは、まず、問題が Intune 関連か Windows 関連かを判断することが重要です。 エラーの考えられる原因が判明すると、トラブルシューティング作業を適切な場所に集中させ、必要に応じて適切なチームからサポートを受けることができます。  

最初の手順として、Intune ポリシーがターゲット デバイスに正常に展開されたかどうかを確認します。 次の例に示されているように、Windows 暗号化 (BitLocker) 設定を展開するデバイス構成ポリシーがあります。

![Windows 暗号化デバイス構成ポリシーとその設定](./media/troubleshooting-bitlocker-policies/settings.png)

設定がターゲット デバイスに適用されているかどうかを確認するにはどうすればよいですか。 これを行うには、次のいくつかの方法があります。

### <a name="device-configuration-policy-device-status"></a>デバイス構成ポリシーのデバイスの状態  

デバイス構成ポリシーを使用して BitLocker を構成するときに、Intune ポータルでポリシーの状態を確認できます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** > **[構成プロファイル]** の順に選択し、BitLocker 設定を含むプロファイルを選択します。

3. 表示するプロファイルを選択したら、**[デバイスの状態]** を選択します。 プロファイルに割り当てられているデバイスが一覧表示され、*[デバイスの状態]* 列に、デバイスがプロファイルを正常に展開したかどうかが示されます。

BitLocker ポリシーを受信しているデバイスと、完全に暗号化されるドライブの間には遅延がある場合があることに注意してください。  

### <a name="use-control-panel-on-the-client"></a>クライアントでコントロール パネルを使用する  

BitLocker が有効になっており、ドライブが暗号化されているデバイスでは、デバイスのコントロール パネルから BitLocker の状態を確認できます。 デバイスで、**[コントロール パネル]** > **[システムとセキュリティ]** > **[BitLocker ドライブ暗号化]** の順に開きます。 次の図に示すように、確認が表示されます。  

![コントロール パネルで BitLocker が有効になっている](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>コマンド プロンプトを使用する  

BitLocker が有効になっており、ドライブが暗号化されているデバイスで、管理者の資格情報を使用してコマンド プロンプトを起動し、`manage-bde -status` を実行します。 その結果は、次の例のようになります。  
![A 結果の状態コマンド](./media/troubleshooting-bitlocker-policies/command.png)

この例では、次のようになります。

- **BitLocker による保護**が**オン**になっている
- **暗号化された割合**は **100%** です
- **暗号化方法**は **XTS-AES 256**

次のコマンドを実行して、**キーの保護機能**を確認することもできます。

```cmd
Manage-bde -protectors -get c:
```

PowerShell の場合:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>デバイスのレジストリ キーの構成を確認する

BitLocker ポリシーがデバイスに正常に展開されたら、BitLocker 設定の構成を確認できるデバイスで次のレジストリ キーを表示します: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*。 次に例を示します。

![BitLocker レジストリ キー](./media/troubleshooting-bitlocker-policies/registry.png)

これらの値は、BitLocker CSP によって構成されます。 キーの値が、Intune Windows 暗号化ポリシーのソースで指定されている設定と一致していることを確認します。 これらの各設定の詳細については、「[BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)」を参照してください。

> [!NOTE]
> Windows イベント ビューアーには、Bitlocker に関連するさまざまな情報も含まれます。 多すぎてここに一覧表示することはできませんが、「**Bitlocker API**」を検索すると、多くの有用な情報が得られます。

### <a name="check-the-mdm-diagnostics-report"></a>MDM 診断レポートを確認する

BitLocker が有効になっているデバイスでは、ターゲット デバイスから MDM 診断レポートを生成して表示し、BitLocker ポリシーが存在することを確認できます。 レポートにポリシー設定が表示されている場合は、それはポリシーが正常に展開されたことのもう 1 つの兆候です。 次のリンクにある "*Microsoft ヘルプ*" のビデオでは、Windows デバイスから MDM 診断レポートをキャプチャする方法を説明しています。

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

MDM 診断レポートを分析するときに、最初は内容が少しわかりにくいかもしれません。 次の例では、レポートの内容をポリシーの設定と関連付ける方法を示しています。

![MDM 診断レポートの例](./media/troubleshooting-bitlocker-policies/report.png)

出力結果には、BitLocker ポリシーの値に対応する値が表示されます。

![値が示されている出力結果 ](./media/troubleshooting-bitlocker-policies/output.png)

MDM 診断の出力結果:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

それぞれの値の意味は、[BitLocker CSP のドキュメント](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)を参照して確認することができます。 この例では、次の図でスニペットが共有されています。

![値の目的](./media/troubleshooting-bitlocker-policies/shared-example.png)

同様に、すべての値を表示して、BitLocker CSP リンクからそれらを確認することもできます。

> [!TIP]
> MDM 診断レポートの主な目的は、問題のトラブルシューティングを行う際に Microsoft サポートを支援することです。 Intune のサポート ケースを開き、問題が Windows クライアントに関係している場合は、常にこのレポートを収集し、サポート リクエストに含めることをお勧めします。

## <a name="troubleshooting-bitlocker-policy"></a>BitLocker ポリシーのトラブルシューティング

BitLocker ポリシーが Intune によって正常に展開された (BitLocker の構成が Windows の BitLocker CSP に渡される) ことを確認する方法がわかるようになってきたと思います。

**ポリシーがデバイスに到達できない** - Intune ポリシーがどの容量にも存在しない場合:

- **デバイスが Microsoft Intune に正しく登録されていますか?** されていない場合は、ポリシーに固有の問題を解決する前に、それに対処する必要があります。 Windows の登録に関する問題のトラブルシューティングについては、[こちら](../enrollment/troubleshoot-windows-enrollment-errors.md)を参照してください。

- **デバイス上にアクティブなネットワーク接続がありますか?** デバイスが機内モードまたはオフになっている場合、またはユーザーがサービスのない場所でデバイスを持っている場合は、ネットワーク接続が復元されるまで、ポリシーは配信されず、適用されません。

- **BitLocker ポリシーは正しいユーザーまたはデバイス グループに展開されましたか?** 正しいユーザーまたはデバイスが、ターゲット グループのメンバーであることを確認します。

**ポリシーは存在するが、一部の設定が正常に構成されない** - Intune ポリシーがデバイスに到達しても、一部の構成が設定されない:

- **ポリシー全体の展開が失敗していますか、それとも特定の設定だけが適用されていませんか?** 一部のポリシー設定のみが適用されないシナリオに直面した場合は、次の考慮事項を確認してください。

  1. **すべての BitLocker 設定がすべての Windows バージョンでサポートされているわけではありません。**
     ポリシーは 1 つのユニットとしてデバイスに送信されるので、一部の設定が適用され、他の設定が適用されない場合でも、ポリシー自体は受信されています。 このシナリオでは、デバイス上の Windows のバージョンが、問題のある設定をサポートしていない可能性があります。 各設定のバージョン要件の詳細については、Windows ドキュメントの「[BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)」を参照してください。

  2. **BitLocker は、すべてのハードウェアでサポートされているわけではありません**。
     適切なバージョンの Windows を使用している場合でも、基になるデバイスのハードウェアが BitLocker 暗号化の要件を満たしていない可能性があります。 [BitLocker のシステム要件](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)については、Windows のドキュメントを参照してください。ただし、主な確認事項は、デバイスに互換性のある TPM チップ (1.2 以降) と Trusted Computing Group (TCG) 準拠の BIOS または UEFI ファームウェアが搭載されていることです。
     
**Bitlocker 暗号化がサイレント モードで実行されない** - 設定 [他のディスクの暗号化に対する警告] をブロックに設定して Endpoint Protection ポリシーを構成しても、暗号化ウィザードがまだ表示されます。

- **Windows のバージョンでサイレント暗号化がサポートされていることを確認する** バージョン 1803 以降が必要です。 ユーザーがデバイスの管理者でない場合は、バージョン 1809 以降が必要です。 さらに、1809 では、Modern Standby をサポートしていないデバイスのサポートが追加されています

**Bitlocker で暗号化されたデバイスが、Intune コンプライアンス ポリシーで非準拠と表示される** - この問題は、BitLocker 暗号化が完了していない場合に発生します。 ディスク サイズ、ファイル数、BitLocker の設定などの要因によっては、BitLocker 暗号化に時間がかかることがあります。 暗号化が完了すると、デバイスは準拠していると表示されます。 WIndows 更新プログラムのインストール直後に、デバイスが一時的に非準拠になることもあります。

**ポリシーで 256 ビットが指定されていても、デバイスが 128 ビット アルゴリズムを使用して暗号化される** - Windows 10 の既定では、ドライブは XTS-AES 128 ビット暗号化を使用して暗号化されます。 [Autopilot の間の BitLocker に対する 256 ビット暗号化の設定](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#)に関するガイドを参照してください。


**調査の例**

- Windows 10 デバイスに BitLocker ポリシーを展開して、**[デバイスの暗号化]** 設定にポータルの**エラー**状態が表示されます。

- 名前が示すように、この設定により、管理者は *[BitLocker] > [デバイスの暗号化]* を使用して暗号化を有効にするように要求できます。 前に説明したトラブルシューティングのヒントを使用して、まず MDM 診断レポートを確認します。 このレポートにより、デバイスに正しいポリシーが展開されたことを確認できます。

  ![正しいポリシーがデバイスに展開されていることを確認するレポート](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- また、レジストリの成功も確認します。

  ![1 を示している RequiredDeviceEncryption レジストリ値](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 次に、PowerShell を使用して TPM の状態を確認し、デバイスで TPM が使用できないことを確認します。

  ![PowerShell を使用して確認された TPM の状態](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- BitLocker は TPM に依存しているため、Intune またはポリシーの問題が原因で BitLocker が失敗することはありませんが、デバイス自体に TPM チップが搭載されていないか、BIOS で TPM が無効になっていることが原因で失敗することはあります。

  追加のヒントとして、**[アプリケーションとサービス ログ]** > **[Microsoft]** > **[Windows]** > **[BitLocker API]** の下にある Windows イベント ビューアーでも同じことを確認できます。 **BitLocker API** イベント ログには、TPM を使用できないことを示すイベント ID 853 があります。

  ![イベント ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > デバイスで **tpm.msc** を実行して、TPM の状態を確認することもできます。

## <a name="summary"></a>[概要]

Intune で BitLocker ポリシーに関する問題のトラブルシューティングを行い、ポリシーが目的のデバイスに到達していることを確認できる場合は、その問題は Intune に直接関係していないと見なすことができます。 Windows OS またはハードウェアの問題である可能性が高いです。 この場合は、TPM 構成、UEFI、セキュア ブートなどの他の領域を参照してください。

## <a name="next-steps"></a>次のステップ  

BitLocker を使用する場合に役立つリソースを次に示します。

- [BitLocker 製品ドキュメント](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker のシステム要件](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker に関してよく寄せられる質問 (FAQ)](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP のドキュメント](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows 暗号化ポリシー設定](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [AAD/MDM を使用したハードウェアに依存しない自動 BitLocker 暗号化](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [自動パイロット デバイスでの BitLocker 暗号化の CSP ポリシー](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Intune での BitLocker ポリシーの作成と展開に関するチュートリアル](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
