---
title: Microsoft Intune を使用する Windows 10 アプリの展開
titleSuffix: ''
description: Microsoft Intune で使用できる Windows 10 アプリの展開シナリオについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8ce24081eae1808d3db0c5078026b306fd209d5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507241"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Microsoft Intune を使用する Windows 10 アプリの展開 

Microsoft Intune は、Windows 10 デバイス上のさまざまな種類のアプリと展開シナリオをサポートしています。 アプリを Intune に追加した後、そのアプリをユーザーとデバイスに割り当てることができます。 この記事では、サポートされている Windows 10 のシナリオについて詳しく説明します。また、Windows にアプリを展開する際に注意する必要がある重要な詳細事項についても説明します。 

基幹業務 (LOB) アプリとビジネス向け Microsoft Store アプリは、Windows 10 デバイスでサポートされているアプリの種類です。 Windows アプリのファイル拡張子には、.msi、.appx、.appxbundle があります。  

> [!Note]
> モダン アプリを展開するには、少なくとも以下が必要です。
> - Windows 10 1803 の場合、[2018 年 5 月 23 日 —KB4100403 (OS ビルド 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)。
> - Windows 10 1709 の場合、[2018 年 6 月 21 日—KB4284822 (OS ビルド 16299.522)](https://support.microsoft.com/help/4284822).
>
> プライマリ ユーザーが関連付けられていないとき、アプリのインストールは Windows 10 1803 以降でのみサポートされます。
>
> LOB アプリの展開は、Windows 10 Home エディションを実行しているデバイスではサポートされていません。

## <a name="windows-10-lob-apps"></a>Windows 10 LOB アプリ

Windows 10 LOB アプリに署名して、Intune 管理コンソールにアップロードすることができます。 これには、ユニバーサル Windows プラットフォーム (UWP) アプリや Windows アプリ パッケージ (AppX) などのモダン アプリに加え、シンプルな Microsoft インストーラー パッケージ ファイル (MSI) などの Win 32 アプリが含まれます。 管理者は、LOB アプリの更新プログラムを手動でアップロードし、展開する必要があります。 これらの更新プログラムは、アプリがインストールされているユーザー デバイスに自動的にインストールされます。 ユーザーの操作は必要ありません。また、ユーザーは更新プログラムを制御できません。 

## <a name="microsoft-store-for-business-apps"></a>ビジネス向け Microsoft ストア アプリ

ビジネス向け Microsoft Store アプリは、ビジネス向け Microsoft Store 管理ポータルから購入したモダン アプリです。 これらは、管理のために Microsoft Intune に同期されます。 アプリは、オンライン ライセンス付きかオフライン ライセンス付きのいずれかです。 Microsoft Store では更新プログラムが直接管理されます。管理者による追加の操作は必要ありません。また、カスタムの Uniform Resource Identifier (URI) を使用して、特定のアプリが更新されないようにすることもできます。 詳細については、「[Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)」 (「エンタープライズ アプリの管理」の「アプリが自動更新されないようにする」) を参照してください。 ユーザーがすべてのビジネス向け Microsoft Store アプリの更新プログラムを無効にすることもできます。 

### <a name="categorize-microsoft-store-for-business-apps"></a>ビジネス向け Microsoft Store アプリの分類 
ビジネス向け Microsoft Store アプリを分類するには: 

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[クライアント アプリ]**  >  **[アプリ]** を選択します。 ビジネス向け Microsoft Store アプリを選択します。 次に、 **[アプリ情報]**  >  **[カテゴリ]** を選択します。 
3. カテゴリを選択します。

## <a name="install-apps-on-windows-10-devices"></a>Windows 10 デバイスにアプリをインストールする
アプリの種類によっては、次の 2 つの方法のいずれかで Windows 10 デバイスにアプリをインストールできます。

- **ユーザー コンテキスト**:アプリがユーザー コンテキストで展開されている場合、ユーザーがデバイスにサインインしたときにデバイス上でそのユーザーに対してマネージド アプリがインストールされます。 ユーザーがデバイスにサインインするまでは、アプリのインストールが正常に行われないことに注意してください。 
  - モダン基幹業務アプリとビジネス向け Microsoft Store アプリ (オンラインとオフラインの両方) は、ユーザー コンテキストで展開できます。 アプリは、必須と利用可能インテントの両方をサポートします。
  - ユーザー モードまたはデュアル モードで構築されている Win32 アプリは、ユーザー コンテキストでデプロイでき、必須と利用可能インテントの両方をサポートします。 
- **デバイス コンテキスト**:アプリがデバイス コンテキストで展開されている場合、マネージド アプリは Intune によってデバイスに直接インストールされます。
  - デバイス コンテキストで展開できるのは、モダン基幹業務アプリとオフライン ライセンスが付与されたビジネス向け Microsoft Store アプリのみです。 このようなアプリは、必須インテントのみをサポートします。
  - マシン モードまたはデュアル モードで構築されている Win32 アプリは、デバイス コンテキストでデプロイでき、必須インテントのみサポートします。

> [!NOTE]
> デュアル モード アプリとして構築された Win32 アプリは、そのインスタンスに関連付けられているすべての割り当てで、アプリがユーザー モードまたはマシン モード アプリとして機能するかどうかを、管理者が選択する必要があります。 開発コンテキストは、割り当てごとに変更することはできません。  

アプリがデバイス コンテキストで展開されている場合、デバイス コンテキストがサポートされているデバイスをターゲットとするときにのみ、正常にインストールされます。 さらに、デバイス コンテキストでの展開では、次の条件がサポートされます。
- アプリがデバイス コンテキストで展開され、ユーザーを対象としている場合、インストールは失敗します。 管理コンソールには、次の状態とエラーが表示されます。
  - 状態:失敗。
  - エラー:デバイス コンテキストのインストールでユーザーを対象とすることはできません。
- アプリがデバイス コンテキストで展開されていても、デバイス コンテキストをサポートしていないデバイスを対象としている場合、インストールは失敗します。 管理コンソールには、次の状態とエラーが表示されます。
  - 状態:失敗。
  - エラー:このプラットフォームはデバイス コンテキストのインストールをサポートしていません。 

> [!Note]
> 特定の展開を使用してアプリの割り当てを保存した後は、モダン アプリを除き、その割り当てのコンテキストを変更することはできません。 モダン アプリの場合、コンテキストをユーザー コンテキストからデバイス コンテキストに変更できます。 

1 人のユーザーまたはデバイスのポリシーに競合がある場合は、次の優先順位が適用されます。
- デバイス コンテキストのポリシーの優先順位は、ユーザー コンテキストのポリシーよりも高くなります。 
- インストール ポリシーの優先順位は、アンインストール ポリシーよりも高くなります。

詳細については、「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。 Intune のアプリの種類の詳細については、「[Microsoft Intune にアプリを追加する](apps-add.md)」を参照してください。

## <a name="next-steps"></a>次の手順

- [Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)
- [アプリを監視する方法](apps-monitor.md)
