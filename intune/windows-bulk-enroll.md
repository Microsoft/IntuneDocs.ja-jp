---
title: "Windows 10 の一括登録"
titlesuffix: Azure portal
description: "Microsoft Intune の一括登録パッケージを作成する"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 10/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: damionw
ms.custom: intune-azure
ms.openlocfilehash: 7738935675595bbdd3ba1f6411a78a2646894073
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="bulk-enrollment-for-windows-devices"></a>Windows デバイスの一括登録

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

管理者として、Azure Active Directory と Intune に多数の新しい Windows デバイスを参加させることができます。 Azure AD テナントのデバイスを一括登録するには、Windows Configuration Designer (WCD) アプリでプロビジョニング パッケージを作成します。 企業所有のデバイスにプロビジョニング パッケージを適用すると、Azure AD テナントにデバイスを参加させ、Intune 管理用に登録します。 パッケージが適用されると、Azure AD ユーザーがログオンするための準備は完了です。

Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みの Intune ポリシーと必須アプリを受け取ります。 この時点では、セルフ サービスとポータル サイトのシナリオはサポートされていません。

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windows デバイスの一括登録の前提条件

Windows デバイスの一括登録には、以下が必要です。

- Windows 10 Creator Update 以降が動作しているデバイス
- [Windows 自動登録](windows-enroll.md#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>プロビジョニング パッケージの作成

1. Microsoft ストアから [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) をダウンロードします。
![Windows Configuration Designer アプリ ストアのスクリーン ショットと説明のスクリーン ショット](media/bulk-enroll-store.png)

2. **Windows Configuration Designer** アプリを開き、**[Provision desktop devices]** (デスクトップ デバイスのプロビジョニング) を選択します。
![Windows Configuration Designer アプリでデスクトップ デバイスのプロビジョニングを選択するスクリーン ショット](media/bulk-enroll-select.png)

3. **[New project]\(新しいプロジェクト\)** ウィンドウが開くので、そこで次の項目を指定します。
  - **名前** - プロジェクトの名前
  - **プロジェクト フォルダー** - プロジェクトを保存する場所
  - **説明**-プロジェクトの説明 (オプション) ![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-name.png)

4.  デバイスの一意の名前を入力します。 名前には、シリアル番号 (%%SERIAL%%)、または文字のランダムなセットを含めることができます。 必要に応じて、Windows のエディションをアップグレードする場合にプロダクト キーを入力したり、デバイスを共有使用のために構成したり、事前にインストールされたソフトウェアを削除することもできます。
![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-device.png)

5.  必要に応じて、初回起動時にデバイスが接続する Wi-fi ネットワークを構成できます。  これが構成されていない場合は、デバイスの初回起動時にワイヤード (有線) ネットワーク接続が必要になります。
![Windows Configuration Designer アプリで、ネットワーク SSID やネットワークの種類のオプションを含む Wi-fi を有効にするスクリーン ショット](media/bulk-enroll-network.png)

6.  **[Enroll in Azure AD]\(Azure AD に登録\)** を選択し、**[Bulk Token Expiry]\(一括トークンの有効期限\)** の日付を入力して、**[Get Bulk Token]\(一括トークンの取得\)** を選択します。
![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-account.png)

7. 一括トークンを取得するための Azure AD の資格情報を入力します。
![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-cred.png)

8.  **一括トークン**が正常にフェッチされたら、**[次へ]** をクリックします。

9. 必要に応じて **[アプリケーションの追加]** や **[証明書の追加]** ができます。 これらのアプリと証明書がデバイスでプロビジョニングされます。

10. 必要に応じて、プロビジョニング パッケージをパスワードで保護できます。  **[作成]** をクリックします。
![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-create.png)

## <a name="provision-devices"></a>デバイスのプロビジョニング

1. アプリで指定した**プロジェクト フォルダー**の場所にあるプロビジョニング パッケージにアクセスします。

2. プロビジョニング パッケージをデバイスに適用する方法を選択します。  プロビジョニング パッケージは、次のいずれかの方法でデバイスに適用できます。
 - USB ドライブにプロビジョニング パッケージを置いて、USB ドライブを一括登録するデバイスに挿入し、初期セットアップ時に適用する
 - ネットワーク フォルダーにプロビジョニング パッケージを置いて、初期セットアップ後に、一括登録するデバイスに適用する

 スプロビジョニング パッケージを適用するステップ バイ ステップの手順については、「[プロビジョニング パッケージの適用](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package)」をご覧ください。

3. パッケージを適用したら、デバイスは 1 分後に自動的に再起動します。
 ![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-add.png)

4. デバイスが再起動すると、Azure Active Directory に接続して Microsoft Intune に登録します。

## <a name="troubleshooting-windows-bulk-enrollment"></a>Windows 一括登録のトラブルシューティング

### <a name="provisioning-issues"></a>プロビジョニングに関する問題
プロビジョニングは新しい Windows デバイスで使用することが想定されています。 プロビジョニングのエラーが起きると、デバイスを出荷時の設定に戻すか、ブート イメージからのデバイスの回復が必要な場合があります。 プロビジョニングのエラーが起きるいくつかの理由について例を挙げます。

- Active Directory ドメイン、またはローカル アカウントを作成していない Azure Active Directory テナントへの参加を試行するプロビジョニング パッケージでは、ネットワーク接続がないためにドメイン参加処理が失敗した場合、デバイスが到達不能になることがあります。
- プロビジョニング パッケージによって実行されるスクリプトは、システム コンテキストで実行され、デバイス ファイル システムと構成に任意の変更を加えることができます。 悪意のある、または正しくないスクリプトを使用すると、デバイスは再イメージングまたは工場出荷時に戻すことでのみ回復できる状態になることがあります。

### <a name="problems-with-bulk-enrollment-and-company-portal"></a>一括登録およびポータル サイトに関する問題
ユーザーが以前に一括登録したデバイスをポータル サイトで登録しようとすると、デバイスにセットアップまたは登録のどちらかの追加操作が必要なことを警告するメッセージが届きます。 デバイスは登録されていますが、登録がポータル サイト アプリまたは Web サイトで認識されていません。

### <a name="bulk-enrollment-with-wi-fi"></a>Wi-Fi で一括登録 

一括登録されたデバイスは、ユーザー対象の証明書と Wi-Fi 展開に使用することはできません。 これらの接続を管理するために、[デバイス レベルの証明書](certificates-configure.md)を使用する必要があります。 

### <a name="conditional-access"></a>条件付きアクセス
条件付きアクセスは、一括登録を使用して登録された Windows デバイスでは使用できません。
