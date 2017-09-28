---
title: "iOS Classroom アプリの Intune 共有デバイス設定"
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
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9b24ee84d339b728addd753cb309b4d8572e5582
ms.sourcegitcommit: e5501cdf08d3e79bc51dc726697606be02110e57
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2017
---
# <a name="how-to-configure-intune-education-settings-for-shared-ipad-devices"></a>共有 iPad デバイスの Intune 教育設定を構成する方法

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune は iOS Classroom をサポートしています。このアプリは、教師が教室で学習を指導し、生徒のデバイスを操作するのを支援するアプリです。 Classroom アプリに加え、Apple では、複数の生徒が 1 台のデバイスを共有できるように、生徒の iPad デバイスを構成できます。 本書では、Intune でこの目標を達成する方法を紹介します。

専用 (1:1) iPad デバイスを構成し、Classroom アプリを使用する方法については、「[iOS Classroom アプリの Intune 設定を構成する方法](education-settings-configure-ios.md)」を参照してください。

## <a name="before-you-start"></a>アップグレードを開始する前に

共有 iPad 機能を使用するための前提条件:

- [Apple School Manager](apple-school-manager-set-up-ios.md) と [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617) の設定。
- Apple School Manager 設定の一環として、生徒の[管理対象 Apple ID](http://help.apple.com/schoolmanager/#/tes78b477c81) を設定します。 管理対象 Apple ID の詳細については、[こちら](https://support.apple.com/en-us/HT205918)をご覧ください。
- Apple School Manager から同期されたデバイス シリアル番号の登録プロファイルを作成します。

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
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
4. **[デバイス構成]** ブレードで、**[管理]** > **[プロファイル]** の順に選択します。
5. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
6. **[プロファイルを作成します]** ブレードで、iOS Education プロファイルの**名前**と**説明**を入力します。
7. **[プラットフォーム]** ドロップダウン リストで、**[iOS]** を選択します。
8. **[プロファイルの種類]** ドロップダウン リストで、**[教育]** を選択します。
9. **[設定]** > **[構成]** の順に選択します。

次に、教師の iPad と生徒の iPad の間の信頼関係を確立するための証明書が必要になります。 証明書は、ユーザー名とパスワードを入力することなく、デバイス間の接続を速やかに認証するために利用されます。

>[!Important]
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
- **証明書の有効期間** - 証明書が失効するまでの残り時間を指定します。 指定した証明書テンプレートの有効期限よりも小さい値を指定できますが、大きい値は指定できません。 たとえば、証明書テンプレートで証明書の有効期限が 2 年になっている場合は、この値を 1 年することはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

教師の証明書の構成が完了したら、**[OK]** を選択します。

### <a name="configure-student-certificates"></a>生徒の証明書を構成する

1. **[教育]** ブレードで **[学生の証明書]** を選択します。
2. **[学生の証明書]** ブレードで、**[学生用デバイス証明書]** の種類の一覧から **[共有 iPad]** を選択します。

#### <a name="configure-student-root-certificate"></a>生徒のルート証明書を構成する

**[デバイスのルート証明書]** で、閲覧ボタンを選択し、拡張子が .cer (DER または Base64 エンコード) または .P7B (完全なチェーンあり/なし) の学生のルート証明書を選択します。

#### <a name="configure-device-pkcs12-certificate"></a>デバイスの PKCS #12 証明書を構成する

**[学生の PKCS #12 証明書]** で、次の値を構成します。

- **サブジェクト名の形式** - Intune は証明書の共通名に自動的に接頭辞を追加します。教師の証明書の場合は leader で、デバイスの証明書の場合は member です。
- **証明機関**Windows Server 2008 R2 以降の Enterprise エディションで実行するエンタープライズ証明機関 (CA) が必要です。 スタンドアロン CA はサポートされません。
- **証明機関名** - 証明機関の名前を入力します。
- **証明書テンプレート名** - 発行元 CA に追加されている証明書テンプレートの名前を入力します。
- **[更新しきい値 (%)]** - 証明書の有効期間の残りがどの程度 (%) になったら、デバイスが更新を要求するかを指定します。
- **証明書の有効期間** - 証明書が失効するまでの残り時間を指定します。 指定した証明書テンプレートの有効期限よりも小さい値を指定できますが、大きい値は指定できません。 たとえば、証明書テンプレートで証明書の有効期限が 2 年になっている場合は、この値を 1 年することはできますが、5 年にすることはできません。 また、発行元の CA の証明書の残りの有効期限よりも小さい値を指定する必要があります。

証明書の構成が完了したら、**[OK]** を選択します。

### <a name="complete-certificate-setup"></a>証明書の設定を完了する

1. **[教育]** ブレードで **[OK]** を選択します。
2. **[プロファイルの作成]** ブレードで、**[作成]** を選択します。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。

## <a name="step-3---create-a-device-category"></a>手順 3 - デバイス カテゴリを作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの登録]** を選択します。
4. **[登録 - 概要]** ブレードで、**[デバイス カテゴリ]** を選択します。
5. **[登録 - デバイス カテゴリ]** ブレードで、**[作成]** を選択します。
6. **[デバイス カテゴリの作成]** ブレードで、カスタム プロファイルの**名前**と**説明**を入力します。
7. **[デバイス カテゴリの作成]** ブレードで、**[作成]** を選択します。

**[登録 - デバイス カテゴリ]** ブレードにデバイス カテゴリが作成されます。

## <a name="step-4--create-a-dynamic-group"></a>手順 4 – 動的グループを作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[グループ]** を選択します。
4. **[ユーザーとグループ - すべてのグループ]** ブレードで、**[新しいグループ]** を選択します。
5. **[グループ]** ブレードで、グループの**名前**と**説明**を入力します。
6. **[メンバーシップの種類]** ドロップダウン リストから、**[動的デバイス]** を選択します。
7. **[動的デバイス メンバー]** を選択し、メンバーシップ ルールを作成します。
8. **[動的メンバーシップ ルール]** ブレードで:
1. **[追加するデバイスの場所]** ドロップダウン リストから **[デバイス カテゴリ]** を選択します。
2. **[等しい]** を選択します。
3. 作成したデバイス カテゴリを空のテキスト ボックスに入力します。
9. **[動的メンバーシップ ルール]** ブレードで、**[クエリの追加]** を選択します。
10. **[グループ]** ブレードで、**[作成]** を選択します。

**[ユーザーとグループ - すべてのグループ]** ブレードで動的グループが作成されます。

## <a name="step-5--assign-a-device-to-a-category-carts"></a>手順 5 – デバイスをカテゴリに割り当てる (カート)

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイス]** を選択します。
4. **[デバイス]** ブレードで、**[すべてのデバイス]** を選択します。
5. **[デバイス - すべてのデバイス]** ブレードで、デバイスを選択します。
6. [デバイス] ブレードで、**[プロパティ]** を選択します。
7. デバイスのプロパティ ブレードで、**[デバイス カテゴリ]** テキスト ボックスにデバイス カテゴリを入力します。
8. [デバイス] ブレードで、**[保存]** を選択します。

これでデバイスがデバイス カテゴリに関連付けられます。 作成したデバイス カテゴリに関連付けるすべてのデバイスにこの過程を繰り返します。

## <a name="step-6--create-classroom-profiles"></a>手順 6 – 教室プロファイルを作成する

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
4. **[デバイス構成]** ブレードで、**[管理]** > **[カート プロファイル]** の順に選択します。
5. [プロファイル] ブレードで、**[プロファイルを作成します]** を選択します。
6. **[関連付けの作成]** ブレードで、**名前**と**説明**を入力します。
7. **[クラスの選択]** > **[構成]** の順に選択し、カート プロファイルにグループを関連付けます。
8. カート プロファイルに追加するクラスを選択し、**[選択]** を選択します。 
9. **[クラスの選択]** > **[構成]** の順に選択し、カート プロファイルにグループを関連付けます。
10. カート プロファイルに追加するグループを選択し、**[選択]** を選択します。
11. **[関連付けの作成]** ブレードで、**[保存]** を選択してカート プロファイルを保存します。

プロファイルが作成され、プロファイルの一覧ブレードに表示されます。

## <a name="step-7---assign-the-cart-profile-to-classes"></a>手順 7 - カート プロファイルをクラスに割り当てる

1. Azure ポータルにサインインします。
2. **[その他のサービス]** > **[その他]** > **[Intune]** の順に選択します。
3. **[Intune]** ブレードで、**[デバイスの構成]** を選択します。
4. **[デバイス構成]** ブレードで、**[モニター]** > **[割り当ての状態]** の順に選択します。
5. **[割り当ての状態]** ブレードで、作成した **[カート プロファイル]** を選択します。
6. **[カート プロファイル]** ブレードで **[割り当て]** を選択し、**[含める]** で **[含めるグループを選択]** を選択します。
7. カート プロファイルのターゲットにするクラスを選択し (グループを選択しないでください)、**[選択]** を選択します。 
8. 終了したら、**[保存]** を選択します。

割り当てが完了します。教室の割り当てに基づき、教室プロファイルがターゲットのデバイスに展開されます。

## <a name="next-steps"></a>次の手順

これで生徒は生徒間でデバイスを共有できます。また、教室にある iPad を選択し、PIN でログインし、自分のコンテンツでパーソナル化できます。 共有 iPad に関する情報については、[Apple の Web サイト](https://www.apple.com/education/it/)をご覧ください。
