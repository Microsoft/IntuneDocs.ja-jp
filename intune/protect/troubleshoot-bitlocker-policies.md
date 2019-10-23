---
title: Microsoft Intune での BitLocker ポリシーのトラブルシューティングのヒント
titleSuffix: Microsoft Intune
description: Intune ポリシーを使用してデバイスで BitLocker 暗号化を有効にする方法と、ポリシーがデバイスに正常に展開されたことを確認する方法について説明します。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 440eb2d457783ac71b905d064a6d83abaa966cfe
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503773"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Microsoft Intune での BitLocker ポリシーのトラブルシューティング

この記事は、intune 管理者が Intune ポリシーに基づいて Windows 10 デバイスで BitLocker を構成する方法を理解するのに役立ちます。 この記事では、Intune で管理するデバイスの BitLocker 設定に関する問題をトラブルシューティングする方法についてのガイダンスも提供します。  

## <a name="understanding-bitlocker"></a>BitLocker について

BitLocker ドライブ暗号化は、ユーザーが自分のハードドライブ上のデータを暗号化できるようにする、Microsoft Windows オペレーティングシステムによって提供されるサービスです。 BitLocker では、オペレーティングシステムドライブ、リムーバブルメディアドライブ、および固定データドライブの暗号化をサポートしています。 BitLocker では、機密データの保護を強化するために、256ビット暗号化の使用もサポートしています。  

Microsoft Intune では、Windows 10 デバイスで BitLocker を管理するには、次の方法があります。

- **デバイス構成ポリシー** -特定の組み込みポリシーオプションは、Intune 管理コンソールの [**デバイス構成** > **Endpoint Protection**  > **Windows 暗号化ポリシー**] で使用できます。 使用可能なすべてのスイッチと機能については、「 [Windows 暗号化](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)」を参照してください。

- **セキュリティベースライン  - ** [セキュリティ基準](security-baselines.md)は、Windows デバイスをセキュリティで保護するために、関連するセキュリティチームによって推奨される設定および既定値のグループです。 *MDM のセキュリティベース*ラインや*Microsoft Defender ATP のベース*ラインなど、さまざまな基準ソースは、同じ設定を互いに異なる設定で管理できます。 また、デバイス構成ポリシーで管理するのと同じ設定を管理することもできます。 

Intune に加えて、BitLocker 設定がグループポリシーなどの他の方法で管理されているか、デバイスユーザーによって手動で設定されている可能性があります。

デバイスに設定を適用する方法に関係なく、BitLocker ポリシーは[BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)を使用してデバイスの暗号化を構成します。 BitLocker CSP は Windows に組み込まれており、Intune が割り当てられたデバイスに BitLocker ポリシーを展開するときに、ポリシーの設定を有効にするために、Windows レジストリに適切な値を書き込むデバイスの BitLocker CSP です。

BitLocker の詳細については、以下のリソースを参照してください。

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker の概要と要件に関する FAQ](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

これらのポリシーの機能と動作についてよく理解できたら、BitLocker 設定が Windows クライアントに正しく適用されているかどうかを確認する方法を確認します。

## <a name="verify-the-source-of-bitlocker-settings"></a>BitLocker 設定のソースを確認する

Windows 10 デバイスで BitLocker の問題を調査するときは、まず、問題が Intune 関連か Windows 関連かを判断することが重要です。 原因として考えられるエラーの原因が判明したら、トラブルシューティング作業を適切な場所に配置し、必要に応じて適切なチームからサポートを受けることができます。  

最初の手順として、Intune ポリシーがターゲットデバイスに正常に展開されたかどうかを確認します。 次の例では、Windows 暗号化 (BitLocker) 設定を展開するデバイス構成ポリシーを使用します。次に例を示します。 

![設定を使用した Windows 暗号化デバイス構成ポリシー](./media/troubleshooting-bitlocker-policies/settings.png)

設定が対象デバイスに適用されているかどうかを確認するにはどうすればよいですか。 これを行うには、次のいくつかの方法があります。

### <a name="device-configuration-policy-device-status"></a>デバイス構成ポリシーデバイスの状態  

デバイス構成ポリシーを使用して BitLocker を構成する場合は、Intune ポータルでポリシーの状態を確認できます。 ポータルで、デバイスの **[構成]** [ > **プロファイル**] の順に選択し > BitLocker 設定を含むプロファイルを選択し、 **[デバイスの状態]** を選択します。 プロファイルに割り当てられているデバイスが一覧表示され、[*デバイスの状態*] 列に、デバイスがプロファイルを正常に展開したかどうかが示されます。 

BitLocker ポリシーを受信しているデバイスと、ドライブが完全に暗号化されるまでには時間がかかる場合があることに注意してください。  

 
### <a name="use-control-panel-on-the-client"></a>クライアントでコントロールパネルを使用する  

BitLocker を有効にし、ドライブを暗号化したデバイスでは、コントロールパネルの [デバイス] で BitLocker の状態を確認できます。 デバイスで、**コントロールパネル**を開き、**システムとセキュリティ** > **BitLocker ドライブ暗号化** >  ます。 次の図に示すように、確認が表示されます。  

![コントロールパネルで BitLocker が有効になっている](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>コマンド プロンプトを使用する  

BitLocker を有効にし、ドライブを暗号化したデバイスで、管理者の資格情報を使用してコマンドプロンプトを起動し、`manage-bde -status` を実行します。 その結果は、次の例のようになります。  
![A 結果の状態コマンド](./media/troubleshooting-bitlocker-policies/command.png)

この例では、次のようになります。 
- **BitLocker による保護**が**オンになって**います。  
- **暗号化された割合**は **100%** です  
- **暗号化方法**は**xts-aes-AES 256**です。  

次のコマンドを実行して、**キープロテクター**を確認することもできます。

```cmd
Manage-bde -protectors -get c:
```

PowerShell の場合:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>デバイスのレジストリキーの構成を確認する   

BitLocker ポリシーがデバイスに正常に展開された後、デバイスで次のレジストリキーを表示して、BitLocker 設定の構成を確認できます。 *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. 次に例を示します。

![BitLocker レジストリキー](./media/troubleshooting-bitlocker-policies/registry.png)

これらの値は、BitLocker CSP によって構成されます。 キーの値が、Intune Windows 暗号化ポリシーのソースで指定されている設定と一致していることを確認します。 これらの各設定の詳細については、「 [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)」を参照してください。

> [!NOTE]
> Windows イベントビューアーには、Bitlocker に関連するさまざまな情報も含まれます。 ここに一覧表示するのは多すぎますが、 **BITLOCKER API**を検索すると、多くの有用な情報が得られます。

### <a name="check-the-mdm-diagnostics-report"></a>MDM 診断レポートを確認する  

BitLocker が有効になっているデバイスでは、対象デバイスから MDM 診断レポートを生成して表示し、BitLocker ポリシーが存在することを確認できます。 レポートにポリシー設定が表示されている場合は、ポリシーが正常に展開されたことが示されています。 Microsoft では、次のリンクを*使用*して、Windows デバイスから MDM 診断レポートをキャプチャする方法を説明しています。 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

MDM 診断レポートを分析するときに、最初に内容が少しわかりにくいことがあります。 次に示すのは、レポートの内容をポリシーの設定と関連付ける方法を示す例です。

![MDM 診断レポートの例](./media/troubleshooting-bitlocker-policies/report.png)

出力結果には、BitLocker ポリシーの値に対応する値が表示されます。

![出力結果に値が表示されます ](./media/troubleshooting-bitlocker-policies/output.png)

MDM 診断の出力結果:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

[BITLOCKER CSP のドキュメント](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)を参照して、それぞれの値の意味を確認することができます。 この例では、次の図でスニペットが共有されています。

![値の目的](./media/troubleshooting-bitlocker-policies/shared-example.png)

 同様に、すべての値を表示して、BitLocker CSP リンクからそれらを確認することもできます。

> [!TIP]
> MDM 診断レポートの主な目的は、問題のトラブルシューティングを行う際に Microsoft サポートを支援することです。 Intune のサポートケースを開き、問題に Windows クライアントが関係している場合は、常にこのレポートを収集し、サポート要求に含めることをお勧めします。

## <a name="troubleshooting-bitlocker-policy"></a>BitLocker ポリシーのトラブルシューティング

Bitlocker ポリシーが Intune によって正常に展開されたことを確認する方法がわかりました。 bitlocker の構成を WIndows の BitLocker CSP にハンドオフします。  

**ポリシーがデバイスに接続でき**ない-Intune ポリシーがどの容量にも存在しない場合:  
- **デバイスは Microsoft Intune に適切に登録されていますか。** それ以外の場合は、ポリシーに固有の問題を解決する前に、そのことに対処する必要があります。 Windows の登録に関する問題のトラブルシューティングについては、[こちら](../enrollment/troubleshoot-windows-enrollment-errors.md)を参照してください。  
- **デバイスにアクティブなネットワーク接続があるかどうか。** デバイスが機内モードまたはオフになっている場合、またはユーザーがサービスのない場所にデバイスを持っている場合は、ネットワーク接続が復元されるまで、ポリシーは配信されず、適用されません。  
- **BitLocker ポリシーは正しいユーザーまたはデバイスグループに展開されましたか?** 正しいユーザーまたはデバイスが、対象のグループのメンバーであることを確認します。  

**ポリシーは存在しますが、すべての設定が正常に構成されているわけではありません**。 Intune ポリシーがデバイスに到達しても、一部の構成が設定されていません。  
- **ポリシー全体の展開が失敗するか、適用されない特定の設定のみになりますか。** 一部のポリシー設定のみが適用されないシナリオに直面した場合は、次の考慮事項を確認してください。

  1. すべて**の BitLocker 設定がすべての Windows バージョンでサポートされているわけではありません**。  
  ポリシーは1つのユニットとしてデバイスに送信されるので、一部の設定が適用され、他の設定が適用されない場合は、ポリシー自体を受け取ることができます。 このシナリオでは、デバイス上の Windows のバージョンが、問題のある設定をサポートしていない可能性があります。 各設定のバージョン要件の詳細については、Windows ドキュメントの「 [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 」を参照してください。  

  1. **BitLocker は、すべてのハードウェアでサポートされていません**。  
  適切なバージョンの Windows を使用している場合でも、基になるデバイスのハードウェアが BitLocker 暗号化の要件を満たしていない可能性があります。 Windows のマニュアルの「BitLocker のシステム要件」 (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) を参照してください。ただし、主な確認事項は、デバイスに互換性のある TPM チップ (1.2 以降) と Trusted Computing Group (TCG) 準拠の BIOS または UEFI ファームウェアがあることです。

**調査例**-Windows 10 デバイスに BitLocker ポリシーを展開し、[デバイスの**暗号化**] 設定に [ポータルに**エラー** ] の状態が表示されます。

- 名前が示すように、この設定により、管理者は*BitLocker > デバイスの暗号化*を使用して暗号化を有効にする必要があります。 前に説明したトラブルシューティングのヒントを使用して、まず MDM 診断レポートを確認します。 このレポートは、正しいポリシーがデバイスに展開されたことを確認します。

  ![正しいポリシーがデバイスに展開されていることを確認するレポート](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- また、レジストリの成功も確認します。

  ![RequiredDeviceEncryption レジストリ値は1を示します](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 次に、PowerShell を使用して TPM の状態を確認し、デバイスで TPM が使用できないことを確認します。

  ![PowerShell を使用した TPM ステータスの確認](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- BitLocker は TPM に依存しているため、Intune またはポリシーの問題が原因で BitLocker が失敗しないことを確認できますが、デバイス自体に TPM チップが搭載されていないか、BIOS で TPM が無効になっているためです。

  追加のヒントとして、[**アプリケーションとサービスログ** > **WINDOWS**  > **BitLocker API**] の下にある windows イベントビューアーでも同じことを確認できます。 **BITLOCKER API**イベントログには、TPM を使用できないことを示すイベント ID 853 があります。

  ![イベント ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > デバイスで**tpm .msc**を実行して、tpm の状態を確認することもできます。



## <a name="summary"></a>[概要]

Intune での BitLocker ポリシーに関する問題のトラブルシューティングを行い、ポリシーが目的のデバイスに到達していることを確認できる場合は、問題が Intune に直接関係していないということをお勧めします。 Windows OS またはハードウェアに問題がある可能性があります。 この場合は、TPM 構成、UEFI、セキュアブートなどの他の領域を参照してください。

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>次の手順  

BitLocker を使用する場合に役立つリソースを次に示します。

- [BitLocker 製品ドキュメント](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker のシステム要件](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker に関してよく寄せられる質問 (FAQ)](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP のドキュメント](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows 暗号化ポリシー設定](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [AAD/MDM を使用したハードウェアに依存しない自動 BitLocker 暗号化](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [自動パイロットデバイスでの BitLocker 暗号化の CSP ポリシー](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Intune での BitLocker ポリシーの作成と展開に関するチュートリアル](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)