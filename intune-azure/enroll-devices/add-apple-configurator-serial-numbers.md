---
title: "Apple Configurator のシリアル番号を追加する | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: Apple Configurator を使用して企業所有の iOS デバイスにシリアル番号を追加する方法について説明します。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d408aa38-7d1e-40df-9067-246e53f6e26f
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 65a6b2e22359bdcb9b0c15a84c6b3586dafe4d6c
ms.openlocfilehash: 71d29a245f8f900a7427528167bae0b52565d42b


---

# <a name="add-apple-configurator-serial-numbers"></a>Apple Configurator のシリアル番号を追加する 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

以下の手順を使用して、[セットアップ アシスタントで Apple Configurator を使用して企業所有の iOS デバイスを登録]((enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)する必要がある場合に、シリアル番号を Intune に追加します。 シリアル番号は&1; つずつ追加することも、シリアル番号が含まれるコンマ区切り値 (CSV) ファイルをアップロードすることもできます。 追加したシリアル番号にはプロファイルを割り当てることができます。 プロファイルには、デバイスに適用する特定の管理設定が含まれています。 

iOS デバイスの他の登録方法については、[Intune での iOS デバイスの登録方法の選択](choose-ios-enrollment-method.md)に関するページを参照してください。

**Apple Configurator のシリアル番号を Intune に追加するには**

1. ヘッダーなしで&2; 列のコンマ区切り値 (.csv) リストを作成します。 IMEI 識別子を左側の列に、詳細を右側の列に追加します。 リストで許可されている現在の最大行数は 500 行です。 この .csv リストをテキスト エディターで表示すると次のようになります。

    F7TLWCLBX196,デバイスの詳細</br>
    DLXQPCWVGHMJ,デバイスの詳細

2. Azure Portal で、**[その他のサービス]** を選択し、テキスト ボックスに「**Intune**」と入力して、**[その他]** > **[Intune]** の順に選択します。

3.  [Intune] ブレードで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。

4. **[Apple Configurator 登録設定の管理]** で **[Apple Configurator のシリアル番号]** を選択します。

5. **[Apple Configurator のシリアル番号]** ブレードで **[追加]** を選択します。

6. **[シリアル番号の追加]** ブレードで、プロファイルを選択して、インポートするシリアル番号に適用するプロファイルを選択します。 新しい詳細情報が含まれるファイルをインポートする場合、そしてその情報で既存の情報が上書きされる場合は、[既存の ID の詳細を上書きします] を選択して、既存の詳細情報が、新しい詳細情報で置き換えられるようにします。

7. シリアル番号の .csv ファイルに移動して、**[追加]** を選択します。

## <a name="assign-a-profile-to-specific-serial-numbers"></a>特定のシリアル番号へのプロファイルの割り当て

Intune を使用すると、Azure Portal の&2; つの異なる場所からプロファイルを割り当てることができます。 以下の手順を使用するか、[Apple Configurator の登録プロファイル] ブレードからプロファイルを割り当てることができます。このブレードではプロファイルを作成できます ([Apple Configurator によるセットアップ アシスタントを使用した iOS デバイスの登録](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)に関するページを参照してください)。 次の手順は、作成済みのプロファイルを割り当てる場合にのみ使用できます。

1. [Intune] ブレードで **[デバイスの登録]** を選択し、**[Apple の登録]** を選択します。

2. **[Apple Configurator のシリアル番号]** ブレードで、プロファイルの割り当て先シリアル番号を選択し、**[プロファイルの割り当て]** を選択します。

3. **[プロファイルの割り当て]** ブレードで、割り当てるプロファイルを選択し、**[割り当て]** を選択します。

## <a name="delete-serial-numbers"></a>シリアル番号の削除
前にインポートしたシリアル番号を削除できます。 シリアル番号を削除するには、デバイスを最初に登録解除しておく必要があります。 シリアル番号を削除すると、シリアル番号を再度追加しない限り、セットアップ アシスタントで Apple Configurator を使用することはできません。

## <a name="view-the-state-of-a-device"></a>デバイスの状態の表示
デバイスのシリアル番号の状態は次のいずれかになります。

- 登録済み - デバイスが登録され、Intune サービスに接続されています
- 未接続 - デバイスが Intune サービスに接続されたことがありません。
- リセット待ち - デバイスは登録されていますが、変更が加えられました (登録の設定や適用済み DEP プロファイルの変更など)。 デバイスの DEP プロファイルを変更した場合、その変更は、デバイスの登録が解除された後、再登録されるまで適用されません。

**シリアル番号の状態を表示するには**

**[Apple Configurator のシリアル番号]** ブレードで、状態を確認するシリアル番号を選択し、**[状態]** 項目を確認します。



<!--HONumber=Feb17_HO1-->


