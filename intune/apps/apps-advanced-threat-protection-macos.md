---
title: Microsoft Intune を使用して Microsoft Defender ATP を macOS デバイスに追加する
titleSuffix: ''
description: Microsoft Intune を使用して Microsoft Defender ATP を macOS デバイスに追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569561"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Microsoft Intune を使用して Microsoft Defender ATP を macOS デバイスに追加する

アプリの展開、構成、監視、または保護を行うには、対象のアプリを事前に Intune に追加しておく必要があります。 使用可能な[アプリの種類](~/apps/apps-add.md#app-types-in-microsoft-intune)の 1 つに、Microsoft Defender Advanced Threat Protection (ATP) があります。 Intune でこの種類のアプリを選択することで、macOS が実行され、自分で管理しているデバイスに Microsoft Defender ATP を割り当てて、インストールすることができます。 このアプリの種類を使用すると、macOS アプリ ラッピング ツールを使用しなくても、macOS デバイスに Microsoft Defender ATP を簡単に割り当てることができます。 アプリのセキュリティを強化し、最新の状態に保つために、これらのアプリには Microsoft AutoUpdate (MAU) が付属しています。

## <a name="prerequisites"></a>[前提条件]
- macOS デバイスで macOS 10.13 以降が実行されている必要があります。
- macOS デバイスには、650 MB 以上のディスク領域が必要です。
- Intune でカーネル拡張機能を展開します。 詳細については、「[Intune で macOS カーネル拡張機能を追加する](~/configuration/kernel-extensions-overview-macos.md)」を参照してください。

> [!IMPORTANT]
> カーネル拡張機能は、Microsoft Defender ATP アプリをインストールする前にデバイスに存在している場合のみ自動的に承認されます。 それ以外の場合、Macs に "システム拡張はブロックされました" というメッセージが表示され、ユーザーは、 **[セキュリティ] 環境設定**に移動するか、または **[システム環境設定]**  >  **[セキュリティとプライバシー]** の順に移動し、 **[許可]** を選択して拡張機能を承認する必要があります。 詳細については、「[Microsoft Defender ATP for Mac でのカーネル拡張の問題のトラブルシューティング](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext)」を参照してください。

## <a name="add-microsoft-defender-atp-to-intune"></a>Microsoft Defender ATP を Intune に追加する
Microsoft Defender ATP を Intune に追加するには、次の手順を行います。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[すべてのアプリ]**  >  **[追加]** の順に選択します。
3. **[Microsoft Defender ATP]** の **[アプリの種類]** の一覧で、 **[macOS]** を選択します。

## <a name="configure-app-information"></a>アプリ情報の構成
この手順では、このアプリの展開に関する情報を指定します。 この情報は、Intune でアプリを識別する場合に役立ち、会社のポータルでユーザーがアプリを探す場合にも役立ちます。

1. **[アプリ情報]** をクリックして **[アプリ情報]** ウィンドウを表示します。
2. **[アプリ情報]** ウィンドウで、このアプリの展開に関する情報を指定します。 この情報は、Intune でアプリを識別する場合に役立ち、会社のポータルでユーザーがアプリを探す場合にも役立ちます。
    - **名前**:アプリの名前を入力します。この名前は会社のポータルに表示されます。 すべての名前が一意であることを確認します。 同じアプリ名が 2 つ存在する場合、会社のポータルではそのいずれかのみがユーザーに表示されます。
    - **説明**:アプリの説明を入力します。 たとえば、説明にターゲット ユーザーを一覧表示することができます。
    - **[発行元]** : Microsoft が発行者として表示されます。
    - **[カテゴリ]** : (省略可能) 1 つ以上の組み込みアプリ カテゴリ、または作成したカテゴリを選択します。 この設定を行うと、会社のポータルを閲覧するときに、ユーザーがアプリを探しやすくなります。
    - **[会社のポータルでおすすめアプリとして表示します]** : ユーザーがアプリを参照するとき、会社のポータルのメイン ページにアプリが目立つように表示するには、このオプションを選びます。
    - **[情報 URL]** : このアプリに関する情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[プライバシー URL]** : このアプリのプライバシー情報が含まれる Web サイトの URL を入力することもできます。 この URL は会社のポータルでユーザーに表示されます。
    - **[開発者]** : Microsoft が開発者として表示されます。
    - **[所有者]** : Microsoft が所有者として表示されます。
    - **[メモ]** : (省略可能) このアプリに関連付けるメモを入力します。
3. **[OK]** を選択します。

## <a name="select-scope-tags-optional"></a>スコープのタグを選択する (省略可能)
スコープのタグを使って、Intune のクライアント アプリの情報を表示できるユーザーを決定することができます。 スコープのタグの詳細については、分散 IT のためのロールベースのアクセス制御とスコープのタグの使用に関するページをご覧ください。
1.  **[スコープ (タグ)]**  >  **[追加]** を選択します。
2.  **[選択]** ボックスを使ってスコープのタグを検索します。
3.  このアプリに割り当てるスコープのタグの横にあるチェック ボックスをオンにします。
4.  **[選択]**  >  **[OK]** の順に選択します。

## <a name="add-the-app"></a>アプリを追加する
構成が完了したら、 **[アプリの追加]** ウィンドウから **[追加]** を選択します。 

作成したアプリはアプリの一覧に表示され、選択したグループに割り当てることができるようになります。 

> [!NOTE]
> 現在、Apple では、Intune で macOS デバイス上の Microsoft Defender ATP をアンインストールする方法を提供していません。

## <a name="next-steps"></a>次のステップ
- macOS デバイスで Microsoft Defender ATP を構成する方法については、[macOS デバイスでの Microsoft Defender ATP の構成](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences)に関するページを参照してください。
- アプリ割り当てをユーザーのグループに追加したり、除外したりする方法については、「[アプリ割り当ての組み込みと除外](~/apps/apps-inc-exl-assignments.md)」を参照してください。
- [アプリをグループに割り当てる](~/apps/apps-deploy.md)

