---
title: Android Enterprise 専用デバイスの Intune 登録を設定する
titleSuffix: Microsoft Intune
description: Intune に Android Enterprise 専用デバイスを登録する方法について説明します。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: edc884850b70ff7621224c5b01a68d016f27504e
ms.sourcegitcommit: 5932da3ed8f52c7b0f0d71c1801f81c85952cf0c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72923391"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Android Enterprise 専用デバイスの Intune 登録を設定する

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android Enterprise では、専用デバイスのソリューションが設定された企業所有、単一用途、キオスク スタイルのデバイスがサポートされています。 そのようなデバイスは、デジタル サイネージ、チケット印刷、在庫管理など、1 つの目的のために使用されます。 管理者はデバイスの使用を厳しく管理し、限られたアプリと Web リンクのみ許可します。 また、ユーザーがデバイスに他のアプリを追加したり、他の操作を行ったりできないようになっています。

Intune では、Android Enterprise 専用デバイスにアプリや設定を展開できます。 Android Enterprise に関する特定の詳細については、[Android Enterprise の要件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)に関するページを参照してください。

この方法で管理するデバイスはユーザー アカウントなしで Intune に登録され、エンド ユーザーとは関連付けられません。 個人向けアプリや、Outlook や Gmail など、ユーザー固有アカウント データに対して厳密な要件のあるアプリの使用を意図していません。

## <a name="device-requirements"></a>デバイスの要件

デバイスを Android Enterprise 専用デバイスとして管理するには、以下の要件を満たす必要があります。

- Android OS バージョン 5.1 以降。
- デバイスは、Google Mobile Services (GMS) に接続できる Android ディストリビューションを実行する必要があります。 デバイスで GMS が利用できて、GMS に接続できる必要があります。

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Android Enterprise 専用デバイスの管理を設定する

Android Enterprise 専用デバイスの管理を設定するには、次の手順を行います。

1. モバイル デバイス管理の準備として、[MDM (モバイル デバイス管理) 機関を **Microsoft Intune** に設定](../fundamentals/mdm-authority-set.md)し、そこに指示を求める必要があります。 この項目は、モバイル デバイス管理について初めて Intune を設定するときに一度だけ設定します。
2. [managed Google Play アカウントに Intune テナント アカウントを接続します](connect-intune-android-enterprise.md)。
3. [登録プロファイルを作成します](#create-an-enrollment-profile)。
4. [デバイス グループを作成します](#create-a-device-group)。
5. [専用デバイスを登録します](#enroll-the-dedicated-devices)。

### <a name="create-an-enrollment-profile"></a>登録プロファイルの作成

> [!NOTE]
> トークンの有効期限が切れている場合、それに関連付けられているプロファイルが **[デバイスの登録]**  >  **[Android の登録]**  >  **[会社が所有する専用デバイス]** に表示されることはありません。 アクティブと非アクティブの両方のトークンに関連付けられているすべてのプロファイルを表示するには、 **[フィルター]** をクリックし、[アクティブ] と [非アクティブ] の両方のポリシーの状態のチェックボックスをオンにします。 

専用デバイスを登録できるように、登録プロファイルを作成する必要があります。 プロファイルが作成されると、登録トークン (ランダムな文字列) と QR コードが与えられます。 デバイスの Android OS とバージョンに基づき、トークンか QR コードのいずれかを使って[専用デバイスを登録](#enroll-the-dedicated-devices)できます。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイスの登録]**  >  **[Android の登録]**  >  **[会社が所有する専用デバイス]** を選択します。
2. **[作成]** を選択し、必須フィールドに入力します。
    - **[名前]** :動的デバイス グループにプロファイルを割り当てるときに使用する名前を入力します。
    - **[トークンの有効期限]** :トークンの有効期限が切れる日付。 Google は最大 90 日間を強制します。
3. **[作成]** を選択してプロファイルを保存します。

### <a name="create-a-device-group"></a>デバイス グループを作成する

アプリとポリシーの対象を、割り当てたデバイス グループか動的デバイス グループに設定できます。 特定の登録プロファイルで登録されているデバイスに自動でデータを入力するように、次の手順で動的 AAD デバイス グループを構成できます。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[グループ]**  >  **[すべてのグループ]**  >  **[新しいグループ]** を選択します。
2. **[グループ]** ブレードで、次のように必須フィールドに入力します。
    - **[グループの種類]** :セキュリティ
    - **[グループ名]** :わかりやすい名前を入力します (Factory 1 デバイスなど)
    - **[メンバーシップの種類]** :動的デバイス
3. **[動的クエリの追加]** を選択します。
4. **[動的メンバーシップ ルール]** ブレードで、次のようにフィールドに入力します。
    - **[動的メンバーシップ ルールの追加]** :簡易ルール
    - **[追加するデバイスの場所]** : enrollmentProfileName
    - 中央のボックスで **[等しい]** を選択します。
    - 最後のフィールドには、先ほど作成した登録プロファイル名を入力します。
    動的メンバーシップ ルールの詳細については、[AAD 内のグループに対する動的メンバーシップ ルール](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)に関する記事を参照してください。 
5. **[クエリの追加]**  >  **[作成]** を選択します。

### <a name="replace-or-remove-tokens"></a>トークンを置換または削除する

- **[トークンの置換]** :[トークンの置換] を利用することで、有効期限が近づいたとき、新しいトークン/QR コードを生成できます。
- **[トークンの取り消し]** :トークン/QR コードをただちに失効させることができます。 取り消した時点から、トークンまたは QR コードは使用できなくなります。 次の場合にこのオプションを使用できます。
  - 認められていない団体と誤ってトークン/QR コードを共有した
  - 登録がすべて完了し、トークン/QR コードが不要になった

トークン/QR コードを取り替えたり、取り消したりしても、登録済みにデバイスに影響が出ることはありません。

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインし、 **[デバイスの登録]**  >  **[Android の登録]**  >  **[会社が所有する専用デバイス]** を選択します。
2. 置き換えるか取り消すプロファイルを選択します。
3. **[トークン]** を選択します。
4. トークンを置換するには、 **[トークンの置換]** を選択します。
5. トークンを取り消すには、 **[トークンの取り消し]** を選択します。

## <a name="enroll-the-dedicated-devices"></a>専用デバイスを登録する

これで[専用デバイスを登録](android-dedicated-devices-fully-managed-enroll.md)できるようになりました。

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Android Enterprise 専用デバイスでアプリを管理する

割り当ての種類が [[必須] に設定されている](../apps/apps-deploy.md#assign-an-app)アプリのみ、Android Enterprise 専用デバイスにインストールできます。 アプリは、Android Enterprise 仕事用プロファイル デバイスと同じ方法で managed Google Play ストアからインストールされます。

アプリは、アプリ開発者が更新版を Google Play に公開したとき、管理対象デバイスで自動的に更新されます。

Android Enterprise 専用デバイスからアプリを削除するには、次のいずれかの操作を行います。
- 要求されたアプリの展開を削除します。
- アプリのアンインストール展開を作成します。

## <a name="next-steps"></a>次の手順
- [Android アプリを展開する](../apps/apps-deploy.md)
- [Android 構成ポリシーを追加する](../configuration/device-profiles.md)
