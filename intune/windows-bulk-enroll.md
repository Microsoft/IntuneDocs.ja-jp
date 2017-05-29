---
title: "Windows 10 の一括登録 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Microsoft Intune の一括登録パッケージを作成する"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: damionw
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f8d1ff7a9a8bd804d4fe40f8aec7e7d0bf998e35
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="bulk-enrollment-for-windows-devices"></a>Windows デバイスの一括登録

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

管理者として、Azure Active Directory と Intune に多数の新しい Windows デバイスを参加させることができます。 Azure AD テナントのデバイスを一括登録するには、Windows 構成デザイナー (WCD) アプリでプロビジョニング パッケージを作成します。 企業所有のデバイスにプロビジョニング パッケージを適用すると、Azure AD テナントにデバイスを参加させ、Intune 管理用に登録します。 パッケージが適用されると、Azure AD ユーザーがログオンするための準備は完了です。

Azure AD ユーザーはこれらのデバイス上の標準ユーザーであり、割り当て済みの Intune ポリシーと必須アプリを受け取ります。 この時点では、セルフ サービスと会社ポータルのシナリオはサポートされていません。

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windows デバイスの一括登録の前提条件

Windows デバイスの一括登録には、以下が必要です。

- Windows 10 Creator Update 以降が動作しているデバイス
- [Windows 自動登録](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>プロビジョニング パッケージの作成

1. Windows ストアから [Windows 構成デザイナー (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) をダウンロードします。
![Windows 構成デザイナー アプリ ストアのスクリーンショットと説明のスクリーンショット](media/bulk-enroll-store.png)

2. **Windows 構成デザイナー** アプリを開き、**[Provision desktop devices] (デスクトップ デバイスのプロビジョニング)** を選択します。
![Windows 構成デザイナー アプリでデスクトップ デバイスのプロビジョニングを選択するスクリーンショット](media/bulk-enroll-select.png)

3. **[新しいプロジェクト]** ウィンドウが開くので、そこで次の項目を指定します。
  - **名前** - プロジェクトの名前
  - **プロジェクト フォルダー** - プロジェクトを保存する場所
  - **説明**-プロジェクトの説明 (オプション) ![Windows 構成デザイナーアプリで、名前、プロジェクト フォルダー、説明を指定するスクリーン ショット](media/bulk-enroll-name.png)

4.    デバイスの一意の名前を入力します。 名前には、シリアル番号 (%%SERIAL%%)、または文字のランダムなセットを含めることができます。 必要に応じて、Windows のエディションをアップグレードする場合にプロダクト キーを入力したり、デバイスを共有使用のために構成したり、事前にインストールされたソフトウェアを削除することもできます。
![Windows 構成デザイナー アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーンショット](media/bulk-enroll-device.png)

5.    必要に応じて、初回起動時にデバイスが接続する Wi-fi ネットワークを構成できます。  これが構成されていない場合は、デバイスの初回起動時にワイヤード (有線) ネットワーク接続が必要になります。
![Windows 構成デザイナー アプリで、ネットワーク SSID やネットワーク種類のオプションを含む Wi-Fi を有効にするスクリーンショット](media/bulk-enroll-network.png)

6.    **[Enroll in Azure AD] (Azure AD に登録)** を選択し、**[Bulk Token Expiry] (一括トークンの有効期限)** の日付を入力して、**[Get Bulk Token] (一括トークンの取得)** を選択します。
![Windows 構成デザイナー アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーンショット](media/bulk-enroll-account.png)

7. 一括トークンを取得するための Azure AD の資格情報を入力します。
![Windows 構成デザイナー アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーンショット](media/bulk-enroll-cred.png)

8.    **一括トークン**が正常にフェッチされたら、**[次へ]** をクリックします。

9. 必要に応じて **[アプリケーションの追加]** や **[証明書の追加]** ができます。 これらのアプリと証明書がデバイスでプロビジョニングされます。

10. 必要に応じて、プロビジョニング パッケージをパスワードで保護できます。  **[作成]** をクリックします。
![Windows 構成デザイナー アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーンショット](media/bulk-enroll-create.png)

## <a name="provision-devices"></a>デバイスのプロビジョニング

1. アプリで指定した**プロジェクト フォルダー**の場所にあるプロビジョニング パッケージにアクセスします。

2. プロビジョニング パッケージをデバイスに適用する方法を選択します。  プロビジョニング パッケージは、次のいずれかの方法でデバイスに適用できます。
 - USB ドライブにプロビジョニング パッケージを置いて、USB ドライブを一括登録するデバイスに挿入し、初期セットアップ時に適用する
 - ネットワーク フォルダーにプロビジョニング パッケージを置いて、初期セットアップ後に、一括登録するデバイスに適用する

 プロビジョニング パッケージを適用するステップ バイ ステップの手順については、「[Apply a provisioning package (プロビジョニング パッケージの適用)](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package)」をご覧ください。

3. パッケージを適用したら、デバイスは 1 分後に自動的に再起動します。
 ![Windows 構成デザイナー アプリで、名前、プロジェクト フォルダー、説明を指定するスクリーンショット](media/bulk-enroll-add.png)

4. デバイスが再起動すると、Azure Active Directory に接続して Microsoft Intune に登録します。

## <a name="troubleshooting-windows-bulk-enrollment"></a>Windows 一括登録のトラブルシューティング

プロビジョニングは新しい Windows デバイスで使用することが想定されています。 プロビジョニングのエラーが起きると、デバイスを出荷時の設定に戻すか、ブート イメージからデバイスを回復する必要が生じる場合があります。 プロビジョニングのエラーが起きるいくつかの理由について例を挙げます。

- Active Directory ドメインへの参加を試行するプロビジョニング パッケージ、またはローカル アカウントを作成していない Azure Active Directory テナントでは、ネットワーク接続がないためにドメイン参加処理が失敗した場合に、デバイスが到達不能になることがあります。
- プロビジョニング パッケージによって実行されるスクリプトは、システム コンテキストで実行され、デバイス ファイル システムと構成に任意の変更を加えることができます。 悪意のあるまたは不正なスクリプトでは、デバイスは、再イメージングまたは工場出荷時に戻すことでのみ回復できる状態になることがあります。

