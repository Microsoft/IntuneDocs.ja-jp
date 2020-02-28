---
title: iOS/iPadOS Classroom アプリの Intune 設定
titleSuffix: Microsoft Intune
description: iOS/iPadOS デバイスの Classroom アプリの設定を制御するために使用できる Intune 設定について説明します。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 74b9e6818de2853ae22a1fa1bb580b32075dcf19
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514423"
---
# <a name="how-to-configure-intune-settings-for-the-iosipados-classroom-app"></a>iOS/iPadOS Classroom アプリの Intune 設定を構成する方法

> [!NOTE]
> 現在、Intune では、Classroom アプリの構成はサポートされていません。 この記事は、Intune に既存の iOS/iPadOS 教育プロファイルがあるユーザーにのみ適用されます。  

## <a name="introduction"></a>概要
[Classroom](https://itunes.apple.com/app/id1085319084) は、教師が教室で学習を指導し、生徒のデバイスを操作するのを支援するアプリです。 たとえば、教師はこのアプリを使用して次のことができます。

- 生徒のデバイスでアプリを起動する
- iPad 画面をロックし、ロックを解除する
- 生徒の iPad の画面を表示する
- 生徒の iPad を操作し、本の中のブックマークや章に移動する
- 生徒の iPad を画面を Apple TV に映す

デバイスで Classroom を設定するには、Intune iOS/iPadOS 教育デバイス プロファイルを作成して設定する必要があります。

## <a name="before-you-start"></a>開始する前に

以上の設定を構成する前に、次の事項について検討してください。

- 教師と生徒の両方の iPad を Intune に登録する必要があります。
- 教師のデバイスに [Apple Classroom](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) アプリがインストールされていることを確認してください。 アプリは手動でインストールすることも、[Intune アプリ管理](../apps/app-management.md)を利用してインストールすることもできます。
- 教師のデバイスと学生のデバイスの間の接続を認証するために証明書を構成する必要があります (手順 2 「Intune で iOS/iPadOS Education プロファイルを作成し、割り当てる」を参照してください)。
- 教師と生徒の iPad を同じ Wi-Fi ネットワークに置き、Bluetooth を有効にする必要があります。
- Classroom アプリは、iOS/iPadOS 9.3 以降が実行されている監視付きの iPad で実行されます。
- 今回のリリースでは、Intune は 1:1 シナリオを管理できます。各生徒に専用の iPad が与えられます。


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>手順 1 - 学校のデータを Azure Active Directory にインポートする

Microsoft の School Data Sync (SDS) を利用し、既存の Student Information System (SIS) から Azure Active Directory (Azure AD) に学校の記録をインポートします。
SDS は SIS の情報を同期し、それを Azure AD に保管します。 Azure AD は、ユーザーやデバイスの整理に役立つ Microsoft の管理システムです。 その後、このデータを生徒やクラスの管理に利用できます。 SDS の展開方法については[ここ](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)をご覧ください。

### <a name="how-to-import-data-using-sds"></a>SDS を利用してデータをインポートする方法

次のいずれかの方法で SDS に情報をインポートできます。

- [CSV ファイル](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - コンマ区切り値 (.csv) ファイルを手動でエクスポートし、コンパイルします
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - Azure AD との同期を簡単にする SIS プロバイダー
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - Azure AD と同期するためにエクスポートし、変換できる CSV 形式

### <a name="find-out-more"></a>詳細は以下のページをご覧ください

- [オンプレミスの学校データを Azure AD に同期する方法](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Microsoft School Data Sync の詳細](https://sds.microsoft.com/)
- [Azure Active Directory のライセンス詳細](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-iosipados-education-profile-in-intune"></a>手順 2 - Intune で iOS/iPadOS Education プロファイルを作成し、割り当てる

### <a name="configure-general-settings"></a>全般的な設定を構成する

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
3. **[Intune]** ウィンドウで、**[デバイス構成]** を選択します。
2. **[デバイス構成]** ウィンドウの **[管理]** セクションで、**[プロファイル]** を選択します。
5. [プロファイル] ウィンドウで **[プロファイルの作成]** を選択します。
6. **[プロファイルの作成]** ウィンドウで、iOS/iPadOS Education プロファイルの **[名前]** と **[説明]** を入力します。
7. **[プラットフォーム]** ドロップダウン リストで、**[iOS]** を選択します。
8. **[プロファイルの種類]** ドロップダウン リストで、**[教育]** を選択します。
9. **[設定]** > **[構成]** の順に選択します。


次のセクションでは、教師の iPad と生徒の iPad の間の信頼関係を確立するための証明書を作成します。 証明書は、ユーザー名とパスワードを入力することなく、デバイス間の接続を速やかに認証するために利用されます。

>[!IMPORTANT]
>教師の証明書と生徒の証明書は、異なる証明書機関 (CA) が発行する必要があります。 既存の証明書インフラストラクチャに接続する下位 CA を新しく 2 つ作成する必要があります。1 つは教師用で、もう 1 つは生徒用です。

iOS 教育プロファイルは、PFX 証明書のみをサポートします。 SCEP 証明書はサポートされていません。

作成する証明書は、サーバー認証とユーザー認証をサポートする必要があります。

### <a name="configure-teacher-certificates"></a>教師の証明書を構成する

**[教育]** ウィンドウで **[教師の証明書]** を選択します。

#### <a name="configure-teacher-root-certificate"></a>教師のルート証明書を構成する

**[教師のルート証明書]** で参照ボタンを選択します。 以下のいずれかのルート証明書を選択します。
- 拡張子 .cer (DER、または Base64 エンコード) 
- 拡張子 .P7B (完全なチェーンあり、またはなし)

#### <a name="configure-teacher-pkcs12-certificate"></a>教師の PKCS#12 証明書を構成する

**[教師の PKCS #12 証明書]** で、次の値を構成します。

- **サブジェクト名の形式** - Intune では、教師の証明書の場合、共通名の先頭に自動的に "**leader**" と付けられます。 学生の証明書の場合、共通名の先頭に "**member**" と付けられます。
- **証明機関**Windows Server 2008 R2 以降の Enterprise エディションで実行するエンタープライズ証明機関 (CA) が必要です。 スタンドアロン CA はサポートされません。 
- **証明機関名** - 証明機関の名前を入力します。
- **証明書テンプレート名** - 発行元 CA に追加されている証明書テンプレートの名前を入力します。 
- **[更新しきい値 (%)]** - 証明書の有効期間の残りがどの程度 (%) になったら、デバイスが更新を要求するかを指定します。
- **証明書の有効期間** - 証明書が失効するまでの残り時間を指定します。
指定した証明書テンプレートの有効期限よりも小さい値を指定できますが、大きい値は指定できません。 たとえば、証明書テンプレートで証明書の有効期限が 2 年になっている場合は、この値を 1 年することはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

証明書の構成が完了したら、**[OK]** を選択します。

### <a name="configure-student-certificates"></a>生徒の証明書を構成する

1. **[教育]** ウィンドウで **[学生の証明書]** を選択します。
2. **[学生の証明書]** ウィンドウで、**[学生用デバイス証明書の種類]** の一覧から **[1:1]** を選択します。

#### <a name="configure-student-root-certificate"></a>生徒のルート証明書を構成する

**[学生のルート証明書]** で参照ボタンを選択します。 以下のいずれかのルート証明書を選択します。
- 拡張子 .cer (DER、または Base64 エンコード) 
- 拡張子 .P7B (完全なチェーンあり、またはなし)

#### <a name="configure-student-pkcs12-certificate"></a>生徒の PKCS #12 証明書を構成する

**[学生の PKCS #12 証明書]** で、次の値を構成します。

- **サブジェクト名の形式** - Intune では、教師の証明書の場合、共通名の先頭に自動的に "**leader**" と付けられます。 学生の証明書の場合、共通名の先頭に "**member**" と付けられます。
- **証明機関**Windows Server 2008 R2 以降の Enterprise エディションで実行するエンタープライズ証明機関 (CA) が必要です。 スタンドアロン CA はサポートされません。 
- **証明機関名** - 証明機関の名前を入力します。
- **証明書テンプレート名** - 発行元 CA に追加されている証明書テンプレートの名前を入力します。 
- **[更新しきい値 (%)]** - 証明書の有効期間の残りがどの程度 (%) になったら、デバイスが更新を要求するかを指定します。
- **証明書の有効期間** - 証明書が失効するまでの残り時間を指定します。
指定した証明書テンプレートの有効期限よりも小さい値を指定できますが、大きい値は指定できません。 たとえば、証明書テンプレートで証明書の有効期限が 2 年になっている場合は、この値を 1 年することはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

証明書の構成が完了したら、**[OK]** を選択します。

## <a name="finish-up"></a>完了

1. **[教育]** ウィンドウで [OK] を選択します。
2. **[プロファイルの作成]** ウィンドウで、**[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ウィンドウに表示されます。

学校データと Azure AD を同期したときに作成された教室グループの生徒用デバイスにプロファイルを割り当てます (「[デバイス プロファイルを割り当てる方法](../configuration/device-profile-assign.md)」参照)。

## <a name="next-steps"></a>次のステップ

これで、教師が Classroom アプリを使用するとき、生徒のデバイスを完全に操作できます。

Classroom アプリの詳細については、Apple Web サイトの [Classroom ヘルプ](https://help.apple.com/classroom/ipad/2.0/)をご覧ください。

受講者に対して共有 iPad デバイスを構成する場合は、[共有 iPad デバイスの Intune 教育設定の構成方法](education-settings-configure-ios-shared.md) に関するページを参照してください。
