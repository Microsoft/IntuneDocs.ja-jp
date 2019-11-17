---
title: Microsoft Intune - Azure でのデバイス プロファイルの割り当て | Microsoft Docs
description: Azure Portal を使用して、デバイスのプロファイルとポリシーをユーザーとデバイスに割り当てます。 Microsoft Intune でプロファイル割り当てからグループを除外する方法について学習します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50b91251572e45669f197df7ac4e5ff94caf47a1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755337"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Microsoft Intune でユーザーおよびデバイス プロファイルを割り当てる

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

プロファイルを作成します。そこには入力したすべての設定が含まれます。 次の手順では、自分の Azure Active Directory (Azure AD) のユーザーまたはデバイス グループへのプロファイルの展開または "割り当て" を行います。 これが割り当てられると、ユーザーとデバイスでお客様のプロファイルを受け取り、入力した設定が適用されます。

この記事では、プロファイルを割り当てる方法を示し、プロファイルでのスコープのタグの使用についての情報が含まれます。

> [!NOTE]  
> ポリシーが削除された場合、またはデバイスに割り当てられなくなった場合、設定が既存値のままになることがあります。 この設定は既定値に戻りません。 設定を別の値に変更するには、新しいポリシーを作成して割り当てます。

## <a name="before-you-begin"></a>始める前に

ポリシーを割り当てるための適切なロールを持っていることを確認してください。 詳細については、「[Microsoft Intune でのロールベースのアクセス制御 (RBAC)](../fundamentals/role-based-access-control.md)」を参照してください。

## <a name="assign-a-device-profile"></a>デバイス プロファイルを割り当てる

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]** 、 **[構成プロファイル]** の順に選択します。 プロファイルがすべて一覧表示されます。
3. 割り当てるプロファイルを選択して、 **[割り当て]** を選択します。
4. グループを**含める**か**除外する**かを選んでから、自分のグループを選択します。 グループを選択するときに、Azure AD グループを選択します。 複数のグループを選択する場合は、**Ctrl** キーを押しながら自分のグループを選択します。

    ![プロファイル割り当てにグループを含める、またはグループを除外するオプションのスクリーンショット](./media/device-profile-assign/group-include-exclude.png)

5. 変更内容を**保存**します。

### <a name="evaluate-how-many-users-are-targeted"></a>対象となるユーザー数を評価する

プロファイルを割り当てるときに、影響を受けるユーザー数を**評価**することもできます。 この機能によってユーザーが計算されます。デバイスは計算されません。

1. 管理センターで、 **[デバイス]** 、 **[構成プロファイル]** の順に選択します。
2. プロファイル > **[割り当て]**  >  **[評価]** を選択します。 このプロファイルの対象となるユーザー数を示すメッセージが表示されます。

**[評価]** ボタンが灰色表示されている場合は、プロファイルが 1 つまたは複数のグループに割り当てられていることを確認してください。

## <a name="use-scope-tags-or-applicability-rules"></a>スコープのタグまたは適用性ルールを使用する

プロファイルを作成または更新するときに、スコープのタグと適用性ルールをプロファイルに追加することもできます。

**スコープのタグ**は、人事や US-NC の全従業員など、特定のグループにポリシーを割り当てて、フィルター処理するのに最適な方法です。 [分散 IT への RBAC とスコープのタグの使用](../fundamentals/scope-tags.md)に関するページには、詳細情報が含まれます。

Windows 10 デバイスでは、**適用性ルール**を追加して、特定の OS のバージョンまたは特定の Windows のエディションにのみプロファイルが適用されるようにすることができます。 詳細については、「[適用性ルール](device-profile-create.md#applicability-rules)」を参照してください。

## <a name="exclude-groups-from-a-profile-assignment"></a>プロファイル割り当てからグループを除外する

Intune のデバイス構成プロファイルを使うと、ポリシーの割り当てに対してグループを含めたり、除外したりすることができます。

ベスト プラクティスとして、お使いのユーザー グループ専用のポリシーを作成して割り当てることをお勧めします。 また、お使いのデバイス グループ専用に異なるポリシーを作成し、割り当ててください。 グループについて詳しくは、「[ユーザーとデバイスを整理するためのグループを追加する](../fundamentals/groups-add.md)」をご覧ください。

ポリシーを割り当てる場合は、グループを含めたり除外したりするときに、次の表をお使いください。 チェックマークは、割り当てがサポートされていることを意味します。

![プロファイル割り当てに対するグループの追加または除外のサポートされているオプション](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>知っておくべきこと

- 次のグループの種類が同じシナリオでは、除外は包含よりも優先されます。

  - ユーザー グループの包含とユーザー グループの除外
  - デバイス グループの包含とデバイス グループの除外

  たとえば、**すべての会社ユーザー** ユーザー グループにデバイス プロファイルを割り当てるが、**上級管理スタッフ** ユーザー グループのメンバーを除外するとします。 どちらのグループもユーザー グループであるため、**上級管理スタッフ**を除く**すべての会社ユーザー**にポリシーが割り当てられます。

- Intune では、ユーザーとデバイスのグループの関係は評価されません。 混合グループにポリシーを割り当てた場合、必要な結果または予期する結果が得られない場合があります。

  たとえば、**すべてのユーザー** ユーザー グループにデバイス プロファイルを割り当て、**個人所有のすべてのデバイス** デバイス グループを除外するとします。 この混合グループのポリシー割り当てでは、**すべてのユーザー**にポリシーが割り当てられます。 除外は適用されません。

  そのため、混合グループにポリシーを割り当てることはお勧めしません。

## <a name="next-steps"></a>次の手順

ポリシーを監視するガイダンス、およびプロファイルを実行するデバイスについては、[デバイス プロファイルの監視](device-profile-monitor.md)に関するページを参照してください。
