---
title: Microsoft Intune での証明書プロファイルの作成 - Azure | Microsoft Docs
description: デバイスに対して、SCEP または PKCS 証明書の環境を構成して証明書プロファイルを追加または作成し、パブリック証明書をエクスポートし、Azure Portal でプロファイルを作成してから、Azure Portal の Microsoft Intune で証明書プロファイルに SCEP または PKCS を割り当てます
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 74b920deeb5255f6f938f0c8b07eaab6d765e68e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722970"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Microsoft Intune で認証に証明書を使用する  

Intune で証明書を使用し、VPN、Wi-Fi、電子メール プロファイルを介してアプリケーションや企業リソースに対してユーザーが本人であることを確認します。 接続の認証に証明書を使用すると、エンド ユーザーはユーザー名とパスワードを入力する必要がなくなり、アクセスがシームレスになります。 証明書は、S/MIME を使用した電子メールの署名と暗号化にも使用されます。

Intune では、次の種類の証明書がサポートされています。  

- Simple Certificate Enrollment Protocol (SCEP)  
- PKCS#12 (または PFX)  
- PKCS のインポートされた証明書

このような証明書を配備するには、証明書プロファイルを作成し、デバイスに割り当てます。  

作成する証明書プロファイルは、1 つにつきプラットフォームを 1 つサポートします。 たとえば、PKCS 証明書を使用する場合、Android 用の PKCS 証明書プロファイルと iOS 用の別の PKCS 証明書プロファイルを別々に作成します。 この 2 つのプラットフォームに SCEP 証明書も使用する場合、Android 用に 1 つ、iOS 用に 1 つ、SCEP 証明書プロファイルを作成します。  

**一般的な考慮事項**:  
- エンタープライズ証明機関 (CA) がない場合、それを作成するか、[サポートされているいずれかのパートナー](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners)のものを使用する必要があります。
- Microsoft Active Directory 証明書サービスを使用して SCEP 証明書プロファイルを使用する場合、ネットワークデバイス登録サービス (NDES) サーバーを構成します。
- SCEP と共に Microsoft のいずれかの証明機関パートナーを使用する場合、[それを Intune と統合する](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)必要があります。
- SCEP 証明書プロファイルと PKCS 証明書プロファイルのいずれでも、Microsoft Intune Certificate Connector をダウンロードし、インストールし、構成する必要があります。 
- PCKS のインポートされた証明書には、PFX Certificate Connector for Microsoft Intune をダウンロードし、インストールし、構成する必要があります。
- PKCS のインポートされた証明書の場合、証明機関から証明書をエクスポートし、それを Microsoft Intune にインポートする必要があります。 「[PFXImport PowerShell プロジェクト](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)」を参照してください。
- SCEP、PCKS、または PKCS のインポートされた証明書プロファイルをデバイスで使用するには、そのデバイスでルート証明機関を信頼する必要があります。 *信頼された証明書プロファイル*を使用し、信頼されたルート CA 証明書をデバイスに配備します。  

## <a name="supported-platforms-and-certificate-profiles"></a>サポートされているプラットフォームと証明書プロファイル  
| プラットフォーム              | 信頼された証明書プロファイル | PKCS 証明書プロファイル | SCEP 証明書プロファイル | PKCS のインポートされた証明書プロファイル  |
|--|--|--|--|---|
| Android デバイス管理者 | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png)|  ![サポート](./media/certificates-configure/green-check.png) |
| Android エンタープライズ <br> - デバイス所有者   | ![サポート](./media/certificates-configure/green-check.png) |   |  |   |
| Android エンタープライズ <br> - 仕事用プロファイル    | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) |
| iOS                   | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) |
| macOS                 | ![サポート](./media/certificates-configure/green-check.png) |   |![サポート](./media/certificates-configure/green-check.png)|![サポート](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![サポート](./media/certificates-configure/green-check.png)  |  | ![サポート](./media/certificates-configure/green-check.png)| ![サポート](./media/certificates-configure/green-check.png) |
| Windows 8.1 以降 |![サポート](./media/certificates-configure/green-check.png)  |  |![サポート](./media/certificates-configure/green-check.png) |   |
| Windows 10 以降  | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) | ![サポート](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>信頼されたルート CA 証明書をエクスポートする  
PKCS、SCEP、PKCS のインポートされた証明書を使用するには、デバイスでルート証明機関を信頼する必要があります。 この信頼を確立するには、信頼されたルート証明機関 (CA) 証明書だけでなく、中間または発行元の証明機関の証明書も公開証明書 (.cer) としてエクスポートします。 このような証明書は、発行元 CA か、発行元 CA を信頼する任意のデバイスから取得できます。  

証明書をエクスポートするには、証明機関のドキュメントを参照してください。 公開証明書は .cer ファイルとしてエクスポートする必要があります。  秘密キー (.pfx ファイル) をエクスポートしないでください。  

[信頼された証明書プロファイルを作成](#create-trusted-certificate-profiles)し、その証明書をデバイスに配備するとき、この .cer ファイルを使用します。  

## <a name="create-trusted-certificate-profiles"></a>信頼された証明書プロファイルを作成する  
SCEP、PKCS、または PKCS のインポートされた証明書プロファイルを作成する前に、信頼された証明書プロファイルを作成します。 信頼された証明書プロファイルを配備することで、CA の正当性が各デバイスで認識されます。 SCEP 証明書プロファイルでは、信頼された証明書プロファイルが直接参照されます。 PKCS 証明書プロファイルでは、信頼された証明書プロファイルが直接参照されず、CA をホストするサーバーが直接参照されます。 PKCS のインポートされた証明書プロファイルでは、信頼された証明書プロファイルが直接参照されませんが、デバイス上で利用されることがあります。 信頼された証明書プロファイルをデバイスに配備することで、この信頼が確立されます。 デバイスでルート CA が信頼されない場合、SCEP または PKCS 証明書プロファイル ポリシーは失敗します。  

SCEP、PCKS、PKCS のインポートされた証明書プロファイルの場合と同様に、サポートするデバイス プラットフォームごとに別個の信頼された証明書プロファイルを作成します。  


### <a name="to-create-a-trusted-certificate-profile"></a>信頼された証明書プロファイルを作成するには  

1. [Intune ポータル](https://aka.ms/intuneportal)にサインインします。  
2. **[デバイス構成]**  >  **[管理]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。  
3. 信頼された証明書プロファイルの **[名前] と [説明]** を入力します。  
4. **[プラットフォーム]** ドロップダウン リストで、この信頼された証明書のデバイス プラットフォームを選択します。  
5. **[プロファイルの種類]** ドロップダウン リストで、 **[信頼済み証明書]** を選択します。  
6. この証明書プロファイルと共に使用する目的でエクスポートした信頼されたルート CA 証明書 .cer ファイルを参照し、 **[OK]** を選択します。  
7. Windows 8.1 および Windows 10 デバイスの場合のみ、信頼された証明書の**保存先ストア**を以下から選択します。  
   - **コンピューター証明書ストア - ルート**
   - **コンピューター証明書ストア - 中間**
   - **ユーザー証明書ストア - 中間**
8. 完了したら、 **[OK]** を選択し、 **[プロファイルの作成]** ウィンドウに戻り、 **[作成]** を選択します。
プロファイルは *[デバイス構成 - プロファイル]* ビュー ウィンドウのプロファイル一覧に、 **[信頼済み証明書]** のプロファイル タイプと共に表示されます。  このプロファイルは必ず、SCEP または PCKS 証明書を使用するデバイスに割り当ててください。 プロファイルをグループに割り当てる場合は、[デバイス プロファイルの割り当て](../configuration/device-profile-assign.md)に関するページを参照してください。

> [!NOTE]  
> Android デバイスでは、信頼できる証明書がサード パーティによってインストールされたことを知らせるメッセージが表示される場合があります。  

## <a name="additional-resources"></a>その他のリソース  
- [デバイス プロファイルを割り当てる](../configuration/device-profile-assign.md)  
- [S/MIME を使用して電子メールに署名し、暗号化する](certificates-s-mime-encryption-sign.md)  
- [サード パーティの証明機関を使用する](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>次の手順  
信頼された証明書プロファイルを作成し、割り当てた後、使用する各プラットフォーム用に SCEP、PKCS、または PKCS のインポートされた証明書プロファイルを作成します。 続行するには、次の記事をご覧ください。  
- [Intune を使用して SCEP 証明書をサポートするようにインフラストラクチャを構成する](certificates-scep-configure.md)  
- [Intune で PKCS 証明書を構成して管理する](certficates-pfx-configure.md)  
- [PKCS のインポートされた証明書プロファイルを作成する](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

