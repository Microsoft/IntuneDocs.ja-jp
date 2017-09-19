---
title: "iOS Classroom アプリの Intune 設定"
titlesuffix: Azure portal
description: "iOS デバイスの Classroom アプリの設定を制御するために使用できる Intune 設定について説明します。\""
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f31ad2226052b4a681bc79e366e7d1def01c3cc4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>iOS Classroom アプリの Intune 設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>概要
[Classroom](https://itunes.apple.com/app/id1085319084) は、教師が教室で学習を指導し、生徒のデバイスを操作するのを支援するアプリです。 たとえば、教師はこのアプリを利用して次のことができます。

- 生徒のデバイスでアプリを起動する
- iPad 画面をロックし、ロックを解除する
- 生徒の iPad の画面を表示する
- 生徒の iPad を操作し、本の中のブックマークや章に移動する
- 生徒の iPad を画面を Apple TV に映す

Intune iOS **Education** デバイス プロファイルとこのトピックの情報を利用し、Classroom アプリやそれを使用するデバイスを設定できます。

## <a name="before-you-start"></a>アップグレードを開始する前に

以上の設定を構成する前に、次の事項について検討してください。

- 教師と生徒の両方の iPad を Intune に登録する必要があります
- 教師のデバイスに [Apple Classroom](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) アプリがインストールされていることを確認してください。 アプリは手動でインストールすることも、[Intune アプリ管理](app-management.md)を利用してインストールすることもできます。
- 教師のデバイスと生徒のデバイスの間の接続を認証するために証明書を構成する必要があります (手順 2 参照)
- 教師と生徒の iPad を同じ Wi-Fi ネットワークに置き、Bluetooth を有効にする必要があります
- iOS 9.3 以降が内蔵され、監視付きの iPad で Classroom アプリを実行します
- 今回のリリースでは、Intune は 1:1 シナリオを管理できます。各生徒に専用の iPad が与えられます


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>手順 1 - 学校のデータを Azure Active Directory にインポートする

Microsoft の School Data Sync (SDS) を利用し、既存の Student Information System (SIS) から Azure Active Directory (Azure AD) に学校の記録をインポートします。
SDS は SIS の情報を同期し、それを Azure AD に保管します。 Azure AD は、ユーザーやデバイスの整理に役立つ Microsoft の管理システムです。 その後、このデータを生徒やクラスの管理に利用できます。 SDS の展開方法については[ここ](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)をご覧ください。

### <a name="how-to-import-data-using-sds"></a>SDS を利用してデータをインポートする方法

次のいずれかの方法で SDS に情報をインポートできます。

- [CSV ファイル](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - コンマ区切り値 (.csv) ファイルを手動でエクスポートし、コンパイルします
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - Azure AD との同期を簡単にする SIS プロバイダー
- [Clever API](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) - Azure AD と直接同期する ID 管理ソリューション
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - Azure AD と同期するためにエクスポートし、変換できる CSV 形式

### <a name="find-out-more"></a>詳細は以下のページをご覧ください

- [オンプレミスの学校データを Azure AD に同期する方法](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Microsoft School Data Sync の詳細](https://sds.microsoft.com/)
- [Azure Active Directory のライセンス詳細](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>手順 2 - Intune で iOS Education プロファイルを作成し、割り当てる

### <a name="configure-general-settings"></a>全般的な設定を構成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[監視 + 管理]** > **[Intune]** の順に選択します。
3.  **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
4.  **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
5.  [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
6.  **[プロファイルを作成します]** ブレードで、iOS Education プロファイルの**名前**と**説明**を入力します。
7.  **[プラットフォーム]** ドロップダウン リストで、**[iOS]** を選択します。
8.  **[プロファイルの種類]** ドロップダウン リストで、**[教育]** を選択します。
9.  **[設定]** > **[構成]** の順に選択します。


次に、教師の iPad と生徒の iPad の間の信頼関係を確立するための証明書が必要になります。 証明書は、ユーザー名とパスワードを入力することなく、デバイス間の接続を速やかに認証するために利用されます。

>[!IMPORTANT]
>教師の証明書と生徒の証明書は、異なる証明書機関 (CA) が発行する必要があります。 既存の証明書インフラストラクチャに接続する下位 CA を新しく 2 つ作成する必要があります。1 つは教師用で、もう 1 つは生徒用です。

iOS 教育プロファイルは、PFX 証明書のみをサポートします。 SCEP 証明書はサポートされていません。

作成する証明書は、ユーザー認証に加え、サーバー認証に対応している必要があります。

### <a name="configure-teacher-certificates"></a>教師の証明書を構成する

**[教育]** ブレードで **[教師の証明書]** を選択します。

#### <a name="configure-teacher-root-certificate"></a>教師のルート証明書を構成する

**[教師のルート証明書]** で、閲覧ボタンを選択し、拡張子が .cer (DER または Base64 エンコード) または .P7B (完全なチェーンあり/なし) の教師のルート証明書を選択します。

#### <a name="configure-teacher-pkcs12-certificate"></a>教師の PKCS#12 証明書を構成する

**[教師の PKCS #12 証明書]** で、次の値を構成します。

- **サブジェクト名の形式** - Intune は証明書の共通名に自動的に接頭辞を追加します。教師の証明書の場合は **leader** で、生徒の証明書の場合は **member** です。
- **証明機関**Windows Server 2008 R2 以降の Enterprise エディションで実行するエンタープライズ証明機関 (CA) が必要です。 スタンドアロン CA はサポートされません。 
- **証明機関名** - 証明機関の名前を入力します。
- **証明書テンプレート名** - 発行元 CA に追加されている証明書テンプレートの名前を入力します。 
- **[更新しきい値 (%)]** - 証明書の有効期間の残りがどの程度 (%) になったら、デバイスが更新を要求するかを指定します。
- **証明書の有効期間** - 証明書が失効するまでの残り時間を指定します。
指定した証明書テンプレートの有効期限よりも小さい値を指定できますが、大きい値は指定できません。 たとえば、証明書テンプレートで証明書の有効期限が 2 年になっている場合は、この値を 1 年することはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

証明書の構成が完了したら、**[OK]** を選択します。

### <a name="configure-student-certificates"></a>生徒の証明書を構成する

1.  **[教育]** ブレードで **[学生の証明書]** を選択します。
2.  **[学生の証明書]** ブレードで、**[Student device certificates (学生デバイス証明書)]** の種類の一覧から **[1:1]** を選択します。

#### <a name="configure-student-root-certificate"></a>生徒のルート証明書を構成する

**[学生のルート証明書]** で、閲覧ボタンを選択し、拡張子が .cer (DER または Base64 エンコード) または .P7B (完全なチェーンあり/なし) の学生のルート証明書を選択します。

#### <a name="configure-student-pkcs12-certificate"></a>生徒の PKCS #12 証明書を構成する

**[学生の PKCS #12 証明書]** で、次の値を構成します。

- **サブジェクト名の形式** - Intune は証明書の共通名に自動的に接頭辞を追加します。教師の証明書の場合は **leader** で、生徒の証明書の場合は **member** です。
- **証明機関**Windows Server 2008 R2 以降の Enterprise エディションで実行するエンタープライズ証明機関 (CA) が必要です。 スタンドアロン CA はサポートされません。 
- **証明機関名** - 証明機関の名前を入力します。
- **証明書テンプレート名** - 発行元 CA に追加されている証明書テンプレートの名前を入力します。 
- **[更新しきい値 (%)]** - 証明書の有効期間の残りがどの程度 (%) になったら、デバイスが更新を要求するかを指定します。
- **証明書の有効期間** - 証明書が失効するまでの残り時間を指定します。
指定した証明書テンプレートの有効期限よりも小さい値を指定できますが、大きい値は指定できません。 たとえば、証明書テンプレートで証明書の有効期限が 2 年になっている場合は、この値を 1 年することはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

証明書の構成が完了したら、**[OK]** を選択します。

## <a name="finish-up"></a>完了

1.  **[教育]** ブレードで [OK] を選択します。
2.  **[プロファイルの作成]** ブレードで、**[作成]** を選択します。
    
プロファイルが作成され、プロファイルの一覧ブレードに表示されます。

学校データと Azure AD を同期したときに作成された教室グループの生徒用デバイスにプロファイルを割り当てます (「[デバイス プロファイルを割り当てる方法](device-profile-assign.md)」参照)。

## <a name="next-steps"></a>次のステップ

これで、教師が Classroom アプリを使用するとき、生徒のデバイスを完全に操作できます。

Classroom アプリの詳細については、Apple Web サイトの [Classroom ヘルプ](https://help.apple.com/classroom/ipad/2.0/)をご覧ください。

受講者に対して共有 iPad デバイスを構成する場合は、[共有 iPad デバイスの Intune 教育設定の構成方法](education-settings-configure-ios-shared.md) に関するページを参照してください。
