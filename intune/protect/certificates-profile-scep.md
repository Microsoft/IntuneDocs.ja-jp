---
title: Microsoft Intune で SCEP 証明書プロファイルを使用する - Azure | Microsoft Docs
description: Microsoft Intune で Simple Certificate Enrollment Protocol (SCEP) 証明書プロファイルを作成して割り当てます。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 321595a2ce8849b3d150b68f9dcc38dfda6ad940
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390301"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Intune で SCEP 証明書プロファイルを作成して割り当てる

Simple Certificate Enrollment Protocol (SCEP) 証明書をサポートするように[インフラストラクチャを構成](certificates-scep-configure.md)したら、Intune で SCEP 証明書プロファイルを作成し、それをユーザーとデバイスに割り当てることができます。

> [!IMPORTANT]  
> SCEP 証明書プロファイルを作成する前に、SCEP 証明書プロファイルを使用するデバイスによって、ご利用の信頼されたルート証明機関 (CA) が信頼される必要があります。 Intune で*信頼された証明書プロファイル*を使用して、信頼されたルート CA 証明書をユーザーとデバイスに対してプロビジョニングします。信頼された証明書プロファイルについては、*Intune での認証に証明書を使用*に関するページの「[信頼されたルート CA 証明書をエクスポートする](certificates-configure.md#export-the-trusted-root-ca-certificate)」と「[信頼された証明書プロファイルを作成する](certificates-configure.md#create-trusted-certificate-profiles)」を参照してください。


## <a name="create-a-scep-certificate-profile"></a>SCEP 証明書プロファイルを作成する

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。

2. **[デバイス]** 、 **[構成プロファイル]** 、 **[プロファイルの作成]** の順に選択します。

3. 次のプロパティを入力します。

4. SCEP 証明書プロファイルの **[名前]** と **[説明]** を入力します。

5. **[プラットフォーム]** ドロップダウン リストで、この SCEP 証明書に対して[サポートされているデバイス プラットフォーム](certificates-configure.md#supported-platforms-and-certificate-profiles)を選択します。

6. **[プロファイルの種類]** ドロップダウン リストで、 **[SCEP 証明書]** を選択します。  

   **[Android エンタープライズ]** プラットフォームの場合、 *[プロファイルの種類]* は *[デバイスの所有者のみ]* と *[仕事用プロファイルのみ]* の 2 つのカテゴリに分かれています。 管理するデバイスに対する正しい SCEP 証明書プロファイルを選択してください。  

   "*デバイスの所有者のみ*" プロファイルの SCEP 証明書プロファイルには、次の制限があります。

   1. [監視] では、証明書レポートはデバイス所有者の SCEP 証明書プロファイルに対しては使用できません。

   2. Intune を使用して、デバイス所有者の SCEP 証明書プロファイルによってプロビジョニングされた証明書を失効させることはできません。 失効を管理するには、外部プロセスを使用するか、証明機関で直接行います。 

   4. Android Enterprise 専用デバイスの場合、SCEP 認証プロファイルは Wi-Fi ネットワーク構成と認証でのみサポートされます。  Android Enterprise 専用デバイスの SCEP 証明書プロファイルは、VPN またはアプリの認証ではサポートされていません。   

   
7. **[設定]** を選択し、次の構成を完了します。

   - **[証明書の種類]** :

     *(適用対象: Android、Android エンタープライズ、iOS、macOS、Windows 8.1 以降、Windows 10 以降。)*

     証明書プロファイルの使用方法に応じて、種類を選択します。

     - **ユーザー**: "*ユーザー*" 証明書では、証明書のサブジェクトと SAN 内にユーザー属性とデバイス属性の両方を含めることができます。  
     - **デバイス**: *[デバイス]* 証明書では、証明書のサブジェクトと SAN にデバイスの属性を含めることができます。

       キオスクのようなユーザーのいないデバイスなどのシナリオまたは Windows デバイスには、 **[デバイス]** を使用します。 Windows デバイスでは、ローカル コンピューターの証明書ストアに証明書が配置されます。

   - **[サブジェクト名の形式]** :

     Intune が証明書要求のサブジェクト名をどのように自動生成するかを選択します。 サブジェクト名の形式のオプションは、選択した証明書の種類 ( **[ユーザー]** または **[デバイス]** ) によって異なります。

     > [!NOTE]
     > SCEP を使用した証明書の取得について、生成される証明書署名要求 (CSR) 内のサブジェクト名に次の文字のいずれかがエスケープ文字 (前にバックスラッシュ \\ が付く) として含まれていた場合に関する[既知の問題](#avoid-certificate-signing-requests-with-escaped-special-characters)があります。
     > - \+
     > - ;
     > - 、
     > - =

     - **ユーザー証明書の種類**

       *[サブジェクト名の形式]* の形式オプションは次のとおりです。

       - **未構成**
       - **共通名**
       - **電子メールを含む共通名**
       - **電子メールとしての共通名**
       - **IMEI (International Mobile Equipment Identity)**
       - **シリアル番号**
       - **[カスタム]** : このオプションを選択すると、 **[カスタム]** テキスト ボックスも表示されます。 このフィールドを使用して、変数など、カスタムのサブジェクト名の形式を入力します。 カスタムの形式では、2 つの変数 (**共通名 (CN)** と**電子メール (E)** ) をサポートしています。 **共通名 (CN)** は、次のいずれかの変数に設定できます。

         - **CN={{UserName}}** : janedoe@contoso.com など、ユーザーのユーザー プリンシパル名。
         - **CN={{AAD_Device_ID}}** : Azure Active Directory (AD) にデバイスを登録するときに割り当てられた ID。 通常、この ID は Azure AD での認証に使われます。
         - **CN={{SERIALNUMBER}}** : 一意のシリアル番号 (SN)。通常はデバイスを識別するために製造元によって使われます。
         - **CN={{IMEINumber}}** : 携帯電話の識別に使用される IMEI (International Mobile Equipment Identity) の一意の番号です。
         - **CN={{OnPrem_Distinguished_Name}}** : コンマで区切られた相対識別名のシーケンスです (*CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com* など)。

           *{{OnPrem_Distinguished_Name}}* 変数を使用するには、[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、*onpremisesdistinguishedname* ユーザー属性をご自分の Azure AD に同期してください。

         - **CN={{onPremisesSamAccountName}}** : 管理者は、Azure AD Connect を使用して、Active Directory の samAccountName 属性を、Azure AD の *onPremisesSamAccountName* という属性に同期できます。 Intune では、証明書のサブジェクト内の証明書発行要求の一部として、その変数を置き換えることができます。 samAccountName 属性は、以前のバージョンの Windows (windows 2000 より前) のクライアントとサーバーをサポートするために使われるユーザー サインイン名です。 ユーザー サインイン名の形式は次のとおりです。*DomainName\testUser*、または *testUser* のみ。

            *{{onPremisesSamAccountName}}* 変数を使用するには、[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、*onPremisesSamAccountName* ユーザー属性をご自分の Azure AD に同期してください。

         これらの変数と静的文字列の 1 つまたは複数を組み合わせて使用することで、次のようなサブジェクト名のカスタム形式を作成できます。  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

         その例には、CN 変数と E 変数に加えて、組織単位、組織、場所、州、国の各値を表す文字列を使用するサブジェクト名形式が含まれています。 [CertStrToName 関数](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)の記事では、この関数とそのサポートされる文字列について説明されています。

      - **デバイス証明書の種類**

        サブジェクト名の形式のフォーマットオプションには、次の変数が含まれます。

        - **{{AAD_Device_ID}}** または **{{AzureADDeviceId}}** - いずれかの変数を使用して、デバイスをその Azure AD ID で識別できます。
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(Windows およびドメインに参加しているデバイスにのみ適用)*
        - **{{MEID}}**

        これらの変数は、テキスト ボックスで指定し、その後に変数のテキストを続けることができます。 たとえば、*Device1* という名前のデバイスの共通名は、**CN={{DeviceName}}Device1** として追加できます。

        > [!IMPORTANT]
        > - 変数を指定する場合は、エラーが発生しないように、例に示すように、変数名を中かっこ { } で囲みます。  
        > - デバイス証明書の "*サブジェクト*" または *SAN* で使用されるデバイス プロパティ (**IMEI**、**SerialNumber**、**FullyQualifiedDomainName** など) は、デバイスへのアクセス権を持つユーザーによってスプーフィングされる可能性のあるプロパティです。
        > - 証明書プロファイルをデバイスにインストールする場合は、そのプロファイルで指定されたすべての変数が該当するデバイスでサポートされている必要があります。  たとえば、 **{{IMEI}}** が SCEP プロファイルのサブジェクト名に使用されていて、IMEI 番号を持たないデバイスに割り当てられている場合、プロファイルのインストールは失敗します。

   - **[サブジェクトの別名]** : Intune が証明書の要求内でサブジェクト代替名 (SAN) を自動的に作成する方法を選択します。 SAN のオプションは、選択した証明書の種類 ( **[ユーザー]** または **[デバイス]** ) によって異なります。

      - **ユーザー証明書の種類**

        次の使用可能な属性から選択します。

        - **電子メール アドレス**
        - **ユーザー プリンシパル名 (UPN)**

        たとえば、ユーザー証明書の種類では、サブジェクトの別名にユーザー プリンシパル名 (UPN) を含めることができます。 クライアント証明書をネットワーク ポリシー サーバーでの認証に使用する場合は、サブジェクトの別名を UPN に設定します。

      - **デバイス証明書の種類**

        **[属性]** ドロップダウンを使用して、属性を選択し、**値**を割り当てて、それを証明書プロファイルに**追加**します。 複数の値を追加するには、追加の属性を選択します。

        使用できる属性は次のとおりです。

        - **電子メール アドレス**
        - **ユーザー プリンシパル名 (UPN)**
        - **DNS**

        *[デバイス]* 証明書の種類を使用すると、値に次のデバイス証明書変数を使用できます。

        - **{{AAD_Device_ID}}** または **{{AzureADDeviceId}}** - いずれかの変数を使用して、デバイスをその Azure AD ID で識別できます。
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        属性の値を指定するには、変数名に中かっこを付け、その後にその変数のテキストを入力します。 たとえば、DNS 属性の値を追加して、 **{{AzureADDeviceId}}.domain.com** とすることができます。ここで、 *.domain.com* はテキストです。 *User1* という名前のユーザーについては、電子メール アドレスが {{FullyQualifiedDomainName}}User1@Contoso.com と表示されることがあります。

        > [!IMPORTANT]
        > - デバイス証明書変数を使用する場合は、変数名を中かっこ { } で囲みます。
        > - 変数の後に続くテキストには、中かっこ **{ }** 、パイプ記号 **|** 、セミコロン **;** を使用しないでください。
        > - デバイス証明書の "*サブジェクト*" または *SAN* で使用されるデバイス プロパティ (**IMEI**、**SerialNumber**、**FullyQualifiedDomainName** など) は、デバイスへのアクセス権を持つユーザーによってスプーフィングされる可能性のあるプロパティです。
        > - 証明書プロファイルをデバイスにインストールする場合は、そのプロファイルで指定されたすべての変数が該当するデバイスでサポートされている必要があります。  たとえば、 **{{IMEI}}** が SCEP プロファイルの SAN で使用されていて、IMEI 番号のないデバイスに割り当てられている場合、プロファイルのインストールに失敗します。

   - **[証明書の有効期間]** :

     証明書テンプレートの有効期限よりも小さい値を入力できますが、大きい値は指定できません。 [Intune コンソール内から設定できるカスタム値をサポート](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template)するように証明書テンプレートを構成した場合、この設定を使用して、証明書の有効期限が切れるまでの残り時間を指定します。

     たとえば、証明書テンプレートで証明書の有効期限が 2 年の場合は、この値を 1 年にすることはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

   - **キー記憶域プロバイダー (KSP)** :

     *(適用対象: Windows 8.1 以降、Windows 10 以降)*

     証明書のキーを格納する場所を指定します。 次の値から選択します。

     - **トラステッド プラットフォーム モジュール (TPM) KSP が存在する場合は TPM KSP に登録する (それ以外はソフトウェア KSP に登録する)**
     - **トラステッド プラットフォーム モジュール (TPM) KSP に登録する (それ以外は失敗)**
     - **Passport に登録する、それ以外は失敗 (Windows 10 以降)**
     - **ソフトウェア KSP に登録する**

   - **[キー使用法]** :

     証明書のキー使用法のオプションを選択します。

     - **[デジタル署名]** : キーがデジタル署名で保護されている場合のみ、キーを交換できます。
     - **[キーの暗号化]** : キーが暗号化されている場合のみ、キーを交換できます。

   - **[キー サイズ (ビット)]** :

     キーに含めるビット数を選択します。

   - **ハッシュ アルゴリズム**:

     *(Android、Android エンタープライズ、Windows Phone 8.1、Windows 8.1 以降、Windows 10 以降に適用されます)*

     この証明書で使用するハッシュ アルゴリズムの種類を 1 つ選択します。 接続しているデバイスをサポートするセキュリティの最も強力なレベルを選択します。

   - **[ルート証明書]** :

     構成済みであって、さらにこの SCEP 証明書プロファイルの適用対象のユーザーとデバイスに割り当ててある "*信頼された証明書プロファイル*" を選択します。 信頼された証明書プロファイルは、信頼されたルート CA 証明書でユーザーとデバイスをプロビジョニングするために使用されます。 信頼された証明書プロファイルの詳細については、*Intune での認証に証明書を使用*に関するページの「[信頼されたルート CA 証明書をエクスポートする](certificates-configure.md#export-the-trusted-root-ca-certificate)」と「[信頼された証明書プロファイルを作成する](certificates-configure.md#create-trusted-certificate-profiles)」を参照してください。 ルート証明機関と発行元の証明機関がある場合は、発行元の証明機関に関連付けられている信頼されたルート証明書プロファイルを選択します。

   - **[拡張キー使用法]** :

     証明書の使用目的に対応する値を追加します。 ほとんどの場合、ユーザーまたはデバイスがサーバーに対して認証できるように、証明書には "*クライアント認証*" が必要です。 必要に応じて、追加のキー使用法を追加できます。

   - **[更新しきい値 (%)]** :

     証明書の有効期間の残りがどの程度 (%) になったら、デバイスが更新を要求するかを入力します。 たとえば、「20」と入力した場合、証明書の更新は、証明書の有効期限が 80% 経過すると試行されます。 更新が成功するまで更新の試行は続行されます。 更新によって新しい証明書が生成され、その結果、公開キーと秘密キーのペアが新しくなります。

   - **[SCEP サーバーの URL]** :

     SCEP 経由で証明書を発行する NDES サーバーの URL を 1 つまたは複数入力します。 たとえば、 *https://ndes.contoso.com/certsrv/mscep/mscep.dll* のようなものを入力します。 URL はプロファイルと共にデバイスにランダムにプッシュされるため、必要に応じて、負荷分散のためにさらに SCEP URL を追加することができます。 SCEP サーバーのいずれか 1 つが利用できない場合、SCEP 要求は失敗し、後でデバイス チェックインをするときに、ダウンしている同じサーバーに対して証明書要求が行われる可能性があります。

8. **[OK]** を選択して、 **[作成]** を選択します。 プロファイルが作成され、 *[デバイス構成 - プロファイル]* リストに表示されます。

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>エスケープされた特殊文字を含む証明書署名要求を回避する

SCEP と PKCS 証明書要求に、以下の特殊文字をエスケープ文字として 1 文字以上含んでいる [サブジェクト名] (CN) が含まれている場合について、既知の問題があります。 サブジェクト名にエスケープ文字として特殊文字が 1 文字含まれていると、CSR のサブジェクト名が不正になります。 サブジェクト名が不正な場合、Intune SCEP チャレンジの検証に失敗し、証明書が発行されません。

その特殊文字は次のとおりです。
- \+
- 、
- ;
- =

使用するサブジェクト名に特殊文字のいずれかが含まれている場合は、次のオプションのいずれかを使用してこの制限を回避してください。

- 特殊文字を含む CN 値を引用符で囲む。  
- CN 値から特殊文字を削除する。

**たとえば**、*Test user (TestCompany, LLC)* として表示される [サブジェクト名] があるとします。  *TestCompany* と *LLC* の間にコンマがある CN を含んでいる CSR で問題が発生します。  この問題を回避するには、CN 全体を引用符で囲むか、*TestCompany* と *LLC* の間のコンマを削除します。

- **引用符を追加する**:*CN=* "Test User (TestCompany, LLC)",OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **コンマを削除する**:*CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 ただし、バックスラッシュ文字を使ってコンマをエスケープしようとすると失敗し、CRP ログにエラーが記録されます。
 
- **エスケープしたコンマ**:*CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

このエラーは次のようなエラーになります。

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>証明書プロファイルを割り当てる

他の目的で[デバイス プロファイルを展開](../configuration/device-profile-assign.md)する場合と同じ方法で、SCEP 証明書プロファイルを割り当てます。 ただし、続行する前に、次の点を考慮してください。

- SCEP 証明書プロファイルをグループに割り当てると、信頼されたルート CA 証明書プロファイル (*信頼された証明書プロファイル*に指定されている) がデバイスにインストールされます。 デバイスでは、SCEP 証明書プロファイルを使用して、その信頼されたルート CA 証明書に対する証明書要求が作成されます。

- SCEP 証明書プロファイルは、証明書プロファイルの作成時に指定されたプラットフォームを実行するデバイス上にのみインストールされます。

- ユーザー コレクションまたはデバイス コレクションに証明書プロファイルを割り当てることができます。

- デバイス登録後すぐに証明書をデバイスに公開するには、証明書プロファイルをデバイス グループではなくユーザー グループに割り当てます。 デバイス グループに割り当てた場合は、デバイスがポリシーを受け取る前に、デバイスの登録を完全に行う必要があります。

- Intune と Configuration Manager に共同管理を使用する場合は、Configuration Manager でリソース アクセス ポリシーの[ワークロード スライダー](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)を **[Intune]** または **[パイロット Intune]** に設定します。 この設定により、Windows 10 クライアントは証明書を要求するプロセスを開始できます。

- 信頼された証明書プロファイルと SCEP 証明書プロファイルを別々に作成して割り当てる場合でも、両方とも割り当てることが必要です。 両方ともデバイス上にインストールされていなければ、SCEP 証明書ポリシーは失敗します。 信頼されたルート証明書プロファイルも確実に SCEP プロファイルと同じグループに展開されるようにします。

> [!NOTE]
> iOS デバイスの場合、SCEP 証明書プロファイルが Wi-fi プロファイルや VPN プロファイルなどの追加のプロファイルに関連付けられている場合、デバイスは、該当する追加のプロファイルの各々に対する証明書を受け取ります。 これにより、SCEP 証明書の要求によって提供される複数の証明書を持つ iOS デバイスが存在するようになります。  単一の証明書が求められている場合は、SCEP 証明書ではなく、PKCS 証明書を使用する必要があります。  SCEP 証明書と PKCS 証明書では、デバイスへの配信方法に違いがあるためです。

## <a name="next-steps"></a>次の手順

[プロファイルの割り当て](../configuration/device-profile-assign.md)
