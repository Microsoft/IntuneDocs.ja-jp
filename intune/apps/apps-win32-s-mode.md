---
title: S モード デバイスで Win32 アプリを有効にする
titleSuffix: Microsoft Intune
description: Microsoft Intune を使用して、S モード デバイスで Win32 アプリを有効にする方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2ab21321b171c8fe8f5f9dab3032507c0e740cf
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059767"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>S モード デバイスで Win32 アプリを有効にする

[Windows 10 S モード](https://docs.microsoft.com/windows/deployment/s-mode)は、Store アプリのみが実行される、ロックダウンされたオペレーティング システムです。 既定では、Windows S モード デバイスで Win32 アプリをインストールして実行することはできません。 このようなデバイスには、S モード デバイスによる Win32 アプリの実行をロックする 1 つの "*Win 10 S 基本ポリシー*" が含まれています。 ただし、Intune で **S モード補足ポリシー**を作成して使用することにより、Windows 10 S モードのマネージド デバイスに Win32 アプリをインストールして実行できます。 [Microsoft Defender アプリケーション制御 (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) PowerShell ツールを使用して、Windows S モード用に 1 つ以上の補足ポリシーを作成できます。 [Device Guard 署名サービス (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) または [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) を使用して補足ポリシーに署名した後、Intune を使用してポリシーをアップロードおよび配布する必要があります。 別の方法として、組織のコード署名証明書を使用して補足ポリシーに署名することもできますが、DGSS を使用することをお勧めします。 組織のコード署名証明書を使用するインスタンスでは、コード署名証明書がチェーンされているルート証明書が、デバイス上に存在している必要があります。

Intune で S モード補足ポリシーを割り当てることにより、デバイスで既存の S モード ポリシーに対する例外を作成できます。これにより、アップロードされた対応する署名済みアプリ カタログが許可されます。 ポリシーでは、S モード デバイスで使用できるアプリ (アプリ カタログ) の許可リストが設定されます。

> [!NOTE]
> S モード デバイス上の Win32 アプリは、Windows 10 November 2019 Update (ビルド 18363) 以降のバージョンでのみサポートされています。

<!-- Add WDAC tooling diagram  -->

S モードの Windows 10 デバイスで Win32 アプリの実行を許可する手順は、次のとおりです。

1. Windows 10 S の登録プロセスの一環として、Intune で S モード デバイスを有効にします。
2. Win32 アプリを許可する補足ポリシーを作成します。
   - [Microsoft Defender アプリケーション制御 (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) ツールを使用して、補足ポリシーを作成できます。 ポリシー内の基本ポリシー ID は、(クライアントでハード コーディングされている) S モード基本ポリシー ID と一致している必要があります。 また、ポリシーのバージョンが以前のバージョンより高いことを確認します。
   - DGSS を使用して、補足ポリシーに署名します。 詳しくは、「[Device Guard の署名を使ったコード整合性ポリシーへの署名](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing)」をご覧ください。
   - Windows 10 S モード補足ポリシーを作成して、署名済み補足ポリシーを Intune にアップロードします (下記参照)。
3. Intune で Win32 アプリ カタログを許可します。
   - カタログ ファイルを作成し (すべてのアプリに対して 1 つ)、DGSS または他の証明書インフラストラクチャを使用して署名します。
   - [Microsoft Win32 コンテンツ準備ツール](https://go.microsoft.com/fwlink/?linkid=2065730)を使用して、署名済みのカタログを *.intunewin* ファイルにパッケージ化します。 詳しくは、「[Win32 アプリ管理 - Win32 アプリ コンテンツのアップロードを準備する](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload)」をご覧ください。
   - Intune により、署名済みアプリ カタログが適用され、[Intune 管理拡張機能](~/apps/intune-management-extension.md)を使用して S モード デバイスに Win32 アプリがインストールされます。

> [!NOTE]
> Windows 10 S モードでの基幹業務 (LOB) `.appx` バンドルおよび `.appx` バンドルは、Microsoft Store for Business (MSFB) 署名を通じてサポートされます。
>
> アプリの **S モード補足ポリシー**は、Intune 管理拡張機能を使用して配信する必要があります。
>
> S モード ポリシーはデバイス レベルで適用されます。 複数のターゲット ポリシーはデバイス上でマージされます。 マージされたポリシーが、デバイスに適用されます。

Windows 10 S モード補足ポリシーを作成するには、次の手順のようにします。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[Intune]** ウィンドウで、 **[クライアント アプリ]**  >  **[S モードの補足ポリシー]**  >  **[ポリシーの作成]** を選択します。
3. **ポリシー ファイル**を追加する前に、作成して署名する必要があります。 詳細については、次をご覧ください。
    - [PowerShell ツールを使用して WDAC ポリシーを作成し、バイナリ形式に変換する](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Device Guard 署名サービスを使用して署名する](https://go.microsoft.com/fwlink/?linkid=2095629) **(推奨)**

4. **[基本]** ページで、次の値を追加します。

    | 値 | 説明 |
    |--------------|------------------------------------------------|
    | ポリシー ファイル | WDAC ポリシーが含まれるファイル。 |
    | 名前 | このポリシーの名前。 |
    | 説明 | (省略可能) このポリシーの説明。 |

5. **[次へ]:[スコープ タグ]** をクリックします。<br>
   **[スコープ タグ]** ページでは、必要に応じて、スコープ タグを構成することにより、Intune でアプリ ポリシーを表示できるユーザーを決定できます。 スコープのタグの詳細については、[分散 IT のためのロールベースのアクセス制御とスコープのタグの使用](~/fundamentals/scope-tags.md)に関するページをご覧ください。

6. **[次へ]:[割り当て]** をクリックします。<br>
   **[割り当て]** ページでは、ユーザーとデバイスにポリシーを割り当てることができます。 デバイスが Intune で管理されているかどうかに関係なく、デバイスにポリシーを割り当てることができることに注意してください。
7. **[次へ]:[確認と作成]** をクリックして、プロファイルに対して入力した値を確認します。
8. 終わったら、 **[作成]** をクリックして、Intune で S モード補足ポリシーを作成します。 

ポリシーが作成されると、Intune の S モード補足ポリシーの一覧に追加されたポリシーが表示されます。 ポリシーを割り当てると、ポリシーがデバイスに展開されます。 補足ポリシーと同じセキュリティ グループにアプリを展開する必要があることに注意してください。 それらのデバイスに対するアプリのターゲット設定と割り当てを始めることができます。 これにより、エンド ユーザーは、S モード デバイスにアプリをインストールして実行できるようになります。

## <a name="removal-of-s-mode-policy"></a>S モード ポリシーの削除

現時点では、デバイスから S モード補足ポリシーを削除するには、空のポリシーを割り当てて展開し、既存の S モード補足ポリシーを上書きする必要があります。

## <a name="policy-reporting"></a>ポリシーのレポート

デバイス レベルで適用される S モード補足ポリシーには、デバイス レベルのレポートのみがあります。 デバイス レベルのレポートは、成功およびエラーの状態に対して使用できます。 

S モード レポート ポリシーに対して Intune コンソールに表示されるレポート値:
- **成功**: S モード補足ポリシーは有効になっています。
- **不明**:S モード補足ポリシーの状態は不明です。
- **TokenError**: S モード補足ポリシーは、構造的には問題ありませんが、トークンの承認に関してエラーがあります。
- **NotAuthorizedByToken**: そのトークンでは、この S モード補足ポリシーは承認されません。
- **PolicyNotFound**: S モード補足ポリシーは見つかりません。

## <a name="next-steps"></a>次の手順

- 詳しくは、[S モードでの Win32 アプリ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s)に関するページをご覧ください。
- Intune にアプリを追加する方法の詳細については、「[Microsoft Intune にアプリを追加する](apps-add.md)」を参照してください。
- Win32 アプリについて詳しくは、[Intune での Win32 アプリの管理](~/apps/apps-win32-app-management.md)に関するページをご覧ください。
