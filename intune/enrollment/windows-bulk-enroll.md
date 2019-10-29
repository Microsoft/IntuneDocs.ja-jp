---
title: Windows 10 の一括登録
titleSuffix: Microsoft Intune
description: Microsoft Intune の一括登録パッケージを作成する
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: spshumwa
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b2ce91cea1fdef211a8e6a9dc1c19086f355385
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585286"
---
# <a name="bulk-enrollment-for-windows-devices"></a>Windows デバイスの一括登録

管理者として、Azure Active Directory と Intune に多数の新しい Windows デバイスを参加させることができます。 Azure AD テナントのデバイスを一括登録するには、Windows Configuration Designer (WCD) アプリでプロビジョニング パッケージを作成します。 企業所有のデバイスにプロビジョニング パッケージを適用すると、Azure AD テナントにデバイスを参加させ、Intune 管理用に登録します。 パッケージが適用されると、Azure AD ユーザーがサインインするための準備が整います。

Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みの Intune ポリシーと必須アプリを受け取ります。 Windows 一括登録を使用して Intune に登録されている Windows デバイスは、ポータル サイト アプリを使用して、使用可能なアプリをインストールできます。 

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windows デバイスの一括登録の前提条件

- Windows 10 Creator Update (ビルド 1703) 以降が動作しているデバイス
- [Windows 自動登録](windows-enroll.md#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>プロビジョニング パッケージの作成

1. Microsoft ストアから [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) をダウンロードします。
   ![Windows Configuration Designer アプリ ストアのスクリーンショット](./media/windows-bulk-enroll/bulk-enroll-store.png)

2. **Windows Configuration Designer** アプリを開き、 **[Provision desktop devices]** (デスクトップ デバイスのプロビジョニング) を選択します。
   ![Windows Configuration Designer アプリでデスクトップ デバイスのプロビジョニングを選択するスクリーン ショット](./media/windows-bulk-enroll/bulk-enroll-select.png)

3. **[新しいプロジェクト]** ウィンドウが開くので、そこで次の情報を指定します。
   - **名前** - プロジェクトの名前
   - **プロジェクト フォルダー** - プロジェクトの保存場所
   - **説明**-プロジェクトの説明 (オプション) ![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](./media/windows-bulk-enroll/bulk-enroll-name.png)

4. デバイスの一意の名前を入力します。 名前には、シリアル番号 (%SERIAL%)、または文字のランダムなセットを含めることができます。 必要に応じて、Windows のエディションをアップグレードする場合にプロダクト キーを入力したり、デバイスを共有使用のために構成したり、事前にインストールされたソフトウェアを削除することもできます。
   
   ![Windows Configuration Designer アプリで名前とプロダクト キーを指定するスクリーンショット](./media/windows-bulk-enroll/bulk-enroll-device.png)

5. 必要に応じて、初回起動時にデバイスが接続する Wi-fi ネットワークを構成できます。  ネットワーク デバイスが構成されていない場合は、デバイスの初回起動時にワイヤード (有線) ネットワーク接続が必要になります。
   ![Windows Configuration Designer アプリで、ネットワーク SSID やネットワークの種類のオプションを含む Wi-fi を有効にするスクリーン ショット](./media/windows-bulk-enroll/bulk-enroll-network.png)

6. **[Enroll in Azure AD]\(Azure AD に登録\)** を選択し、 **[Bulk Token Expiry]\(一括トークンの有効期限\)** の日付を入力して、 **[Get Bulk Token]\(一括トークンの取得\)** を選択します。
   ![Windows Configuration Designer アプリでのアカウント管理のスクリーンショット](./media/windows-bulk-enroll/bulk-enroll-account.png)

7. 一括トークンを取得するための Azure AD の資格情報を入力します。
   ![Windows Configuration Designer アプリへのサインインのスクリーンショット](./media/windows-bulk-enroll/bulk-enroll-cred.png)

8. **一括トークン**が正常にフェッチされたら、 **[次へ]** をクリックします。

9. 必要に応じて **[アプリケーションの追加]** や **[証明書の追加]** ができます。 これらのアプリと証明書がデバイスでプロビジョニングされます。

10. 必要に応じて、プロビジョニング パッケージをパスワードで保護できます。  **[作成]** をクリックします。
    ![Windows Configuration Designer アプリでのパッケージ保護のスクリーンショット](./media/windows-bulk-enroll/bulk-enroll-create.png)

## <a name="provision-devices"></a>デバイスのプロビジョニング

1. アプリで指定した**プロジェクト フォルダー**の場所にあるプロビジョニング パッケージにアクセスします。

2. プロビジョニング パッケージをデバイスに適用する方法を選択します。  プロビジョニング パッケージは、次のいずれかの方法でデバイスに適用できます。
   - USB ドライブにプロビジョニング パッケージを置いて、USB ドライブを一括登録するデバイスに挿入し、初期セットアップ時に適用する
   - ネットワーク フォルダーにプロビジョニング パッケージを配置して、初期セットアップ後に適用する

   スプロビジョニング パッケージを適用するステップ バイ ステップの手順については、「[プロビジョニング パッケージの適用](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package)」をご覧ください。

3. パッケージを適用したら、デバイスは 1 分後に自動的に再起動します。
   ![Windows Configuration Designer アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](./media/windows-bulk-enroll/bulk-enroll-add.png)

4. デバイスが再起動すると、Azure Active Directory に接続して Microsoft Intune に登録します。

## <a name="troubleshooting-windows-bulk-enrollment"></a>Windows 一括登録のトラブルシューティング

### <a name="provisioning-issues"></a>プロビジョニングに関する問題
プロビジョニングは新しい Windows デバイスで使用することが想定されています。 プロビジョニングのエラーが起きると、場合によっては、デバイスをワイプするか、ブート イメージからデバイスを復元する必要があります。 プロビジョニングのエラーが起きるいくつかの理由について例を挙げます。

- Active Directory ドメイン、またはローカル アカウントを作成していない Azure Active Directory テナントへの参加を試行するプロビジョニング パッケージでは、ネットワーク接続がないためにドメイン参加処理が失敗した場合、デバイスが到達不能になることがあります。
- プロビジョニング パッケージによって実行されるスクリプトは、システム コンテキストで実行されます。 スクリプトは、デバイスのファイル システムと構成に、任意の変更を加えることができます。 悪意のある、または正しくないスクリプトを使用すると、デバイスは再イメージングまたはワイプすることでのみ回復できる状態になることがあります。

イベント ビューアーへの **Provisioning-Diagnostics-Provider** の管理者ログインでパッケージ内の設定が成功したかどうかを確認できます。

### <a name="bulk-enrollment-with-wi-fi"></a>Wi-Fi で一括登録 

一括登録されたデバイスは、ユーザー対象の証明書と Wi-Fi 展開に使用することはできません。 これらの接続を管理するには、[デバイス レベルの証明書](../protect/certificates-configure.md)を使用する必要があります。 

### <a name="conditional-access"></a>条件付きアクセス
条件付きアクセスは、一括登録を使用して登録された Windows デバイスでは使用できません。
