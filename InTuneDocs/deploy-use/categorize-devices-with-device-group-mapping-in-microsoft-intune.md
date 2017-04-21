---
title: "デバイス グループのマッピングを使用してデバイスを分類する | Microsoft Docs"
description: "Microsoft Intune のデバイス グループ マッピングを使用して、ユーザー定義のカテゴリにデバイスをグループ化することで、それらのデバイスの管理が容易になります。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8b8c06a3-6b6c-4cf1-8646-b24fa9b1a39e
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 57c739444c18d12a6d7ee8ca591f9a1dd72985d7
ms.lasthandoff: 04/14/2017

---

# <a name="categorize-devices-with-device-group-mapping-in-microsoft-intune"></a>Microsoft Intune でデバイス グループのマッピングを使用してデバイスを分類する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune の**デバイス グループ マッピング**を使用して、ユーザー定義のカテゴリに基づいてデバイスを自動的にグループに追加することで、デバイスの管理が容易になります。 

デバイス グループ マッピングでは、次のワークフローを使用します。
1. デバイス登録時の選択肢として表示するカテゴリを作成する
2. 使用するカテゴリごとに、グループを作成するか、既存のグループを使用します。 使用している Intune のバージョンに応じて、Intune グループまたは Azure Active Directory セキュリティ グループの場合があります。
2. 作成したデバイス グループに選択したカテゴリを対応付けるルールを構成します。
3. デバイスを登録するエンド ユーザーは、構成されているカテゴリの一覧からカテゴリを選択する必要があります。 エンド ユーザーがカテゴリを選択すると、デバイスは自動的に対応するグループに追加されます。 デバイスが既に登録されている場合、エンド ユーザーは、次にポータル サイト アプリにアクセスしたときにカテゴリを選択するように求められます。
4. 次に、ポリシーとアプリをグループに展開します。

次のように、任意のデバイス カテゴリを作成できます。
* 販売時点管理デバイス
* デモンストレーション デバイス
* 営業
* アカウンティング
* Manager

## <a name="important-information-about-a-change-in-group-management-for-intune"></a>Intune のグループ管理の変更に関する重要な情報

お客様のフィードバックに基づいて、Enterprise Mobility + Security 全体のグループ化およびターゲット設定を統合する作業を進めています。 そのため、間もなく Intune のグループを Azure Active Directory ベースのセキュリティ グループに変換します。 この変更後は、Intune を使用してグループを作成しません。 代わりに、Azure ポータルでグループを作成するようになります。 この変更は段階的に行う予定です。変更内容の詳細とタイムラインについては、[このトピック](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)を参照してください。

### <a name="which-procedure-in-this-topic-should-you-use-to-configure-device-group-mapping"></a>デバイス グループ マッピングを構成する際にこのトピックで使用する手順

Azure Active Directory ベースのセキュリティ グループは段階的に実装されるため、使用する手順を特定するには、[Intune 管理コンソール](https://manage.microsoft.com)の **[グループ]** ワークスペースを開く必要があります。

-  Azure ポータルへのリンクが表示される場合、Intune グループが使用されなくなったことを示します。 後述する「[デバイス グループ マッピングの構成方法 (Azure Active Directory グループ)](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-azure-active-directory-groups)」の手順に従ってください。
-  Azure ポータルへのリンクが表示されない場合、まだ Intune グループが使用されていることを示します。 後述する「[デバイス グループ マッピングの構成方法 (Intune グループ)](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune#how-to-configure-device-group-mapping-for-intune-groups)」の手順に従ってください。

## <a name="how-to-configure-device-group-mapping-for-intune-groups"></a>デバイス グループ マッピングの構成方法 (Intune グループ)
1. 使用するデバイス カテゴリごとに、Intune のデバイス グループを作成するか、既存のグループを指定します。 グループの作成方法については、「[Microsoft Intune でユーザーとデバイスの管理にグループを使用する](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)」を参照してください。
2. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理者]** を選択します。
3. **[管理]** ワークスペースで、**[モバイル デバイス管理]** を展開してから、**[デバイス グループ マッピング]** を選択します。
4. **[デバイス グループ マッピング]** ページで、デバイス グループ マッピングを有効にします。
5. **[追加]** を選択し、新しいマッピング ルールを作成します。
6. **[デバイス グループ マッピング ルールの追加]** ダイアログ ボックスで、作成するカテゴリの名前を入力し、このカテゴリをマップするデバイスのコレクションをドロップダウン リストから選択します。 選択が完了したら、**[追加]** を選択します。
7. カテゴリとグループの追加が完了したら、**[保存]** を選択します。



## <a name="how-to-configure-device-group-mapping-for-azure-active-directory-groups"></a>デバイス グループ マッピングの構成方法 (Azure Active Directory グループ)

### <a name="step-1---create-device-categories-in-the-intune-administration-console"></a>手順 1 - Intune 管理コンソールでデバイス カテゴリを作成する
1. [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[管理者]** を選択します。
3. **[管理]** ワークスペースで、**[モバイル デバイス管理]** を展開してから、**[デバイス カテゴリ]** を選択します。
4. **[デバイス カテゴリ]** ページには、デバイス カテゴリを構成できる一覧が表示されます。 
- 名前を入力し、**[追加]** をクリックすると、新しいデバイス カテゴリとして追加されます。
- カテゴリを選択し、**[削除]** をクリックして削除することもできます。

デバイス カテゴリ名は、手順 2 で Azure Active Directory セキュリティ グループを作成するときに使用します。

### <a name="step-2---create-azure-active-directory-security-groups"></a>手順 2 - Azure Active Directory セキュリティ グループを作成する

この手順では、デバイス カテゴリとデバイス カテゴリ名に基づいて、Azure ポータルで動的グループを作成します。

次に進む前に、Azure Active Directory ドキュメントのトピック「[属性を利用した高度なルールの作成](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)」を参照してください。
このトピックの情報を参考にして、**deviceCategory** 属性を使用して高度なルールのデバイス グループを作成します。
たとえば、次のようなグループを作成します。(**device.deviceCategory -eq** "<*Intune 管理コンソールで確認したデバイス カテゴリ名*>")


## <a name="after-you-configure-device-groups"></a>デバイス グループの構成後

デバイスを登録すると、構成したカテゴリの一覧が表示されます。 ユーザーがカテゴリを選択して登録を完了すると、選択したカテゴリに対応する Intune デバイス グループまたは Active Directory セキュリティ グループにデバイスが追加されます。

### <a name="see-also"></a>関連項目
[Microsoft Intune でユーザーとデバイスの管理にグループを使用する](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

