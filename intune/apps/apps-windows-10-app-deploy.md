---
title: Microsoft Intune を使用する Windows 10 アプリの展開
titleSuffix: ''
description: Microsoft Intune で使用できる Windows 10 アプリの展開シナリオについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c853608f46bb01263ddd08193f729cdfb018fed9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724972"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Microsoft Intune を使用する Windows 10 アプリの展開 

現在、Microsoft Intune では、Windows 10 デバイスでのさまざまなアプリの種類と展開のシナリオがサポートされています。 アプリを Intune に追加した後、そのアプリをユーザーとデバイスに割り当てることができます。 ここでは、サポートされている Windows 10 シナリオに関連する詳細情報を示します。 さらに、Windows へのアプリの展開時に注意する必要がある主な詳細情報を示します。 

基幹業務 (LOB) アプリとビジネス向け Microsoft Store アプリは、Windows 10 デバイスでサポートされているアプリの種類です。 Windows アプリのファイル拡張子には、 **.msi**、 **.appx**、 **.appxbundle** があります。  

> [!Note]
> 最新のアプリを展開するのに必要な最小の Windows 10 の更新プログラムは、次のとおりです。
> - Windows 10 1803 の場合、[2018 年 5 月 23 日 —KB4100403 (OS ビルド 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)。
> - Windows 10 1709 の場合、[2018 年 6 月 21 日—KB4284822 (OS ビルド 16299.522)](https://support.microsoft.com/help/4284822).
>
> プライマリ ユーザーが関連付けられていないとき、アプリのインストールは Windows 10 1803 以降でのみサポートされます。

## <a name="windows-10-line-of-business-apps"></a>Windows 10 の基幹業務アプリ

Windows 10 の基幹業務アプリは署名され、Intune 管理コンソールにアップロードされます。これには、ユニバーサル Windows プラットフォーム (UWP) アプリや Windows アプリケーション パッケージ (AppX) などの最新のアプリと、シンプルな Microsoft インストーラー パッケージ ファイル (MSI) などの Win 32 アプリの両方が含まれる場合があります。 LOB アプリの更新プログラムは、管理者によって毎回、手動でアップロードされ、展開されます。展開された更新プログラムは、ユーザーの介入なしでアプリがインストールされたエンド ユーザー デバイスに自動的にインストールされます。 ユーザーが更新プログラムを制御することはできません。 

## <a name="microsoft-store-for-business-apps"></a>ビジネス向け Microsoft ストア アプリ

ビジネス向け Microsoft Store アプリは、ビジネス向け Microsoft Store の管理ポータルから購入できる最新のアプリであり、管理のために Microsoft Intune に同期されます。 アプリは、**オンライン ライセンス付き**か**オフライン ライセンス付き**のいずれかです。 ビジネス向け Microsoft Store アプリの更新プログラムは Microsoft Store によって直接管理され、お客様 (管理者) が追加の操作を行う必要はありません。また、カスタムの Uniform Resource Identifier (URI) を使用して、特定のアプリが更新されないようにすることもできます。 詳細については、「[Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates)」 (「エンタープライズ アプリの管理」の「アプリが自動更新されないようにする」) を参照してください。 デバイス上では、エンド ユーザーがすべてのビジネス向け Microsoft Store アプリの更新を無効にすることもできます。 

### <a name="categorize-microsoft-store-for-business-apps"></a>ビジネス向け Microsoft Store アプリの分類 
ビジネス向け Microsoft ストア アプリを分類するには、次の手順を使用します。 

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) にサインインします。
2. **[クライアント アプリ]**  >  **[アプリ]** > [Select a Microsoft Store for Business app]\(ビジネス向け Microsoft ストア アプリを選択する\) > **[アプリ情報]**  >  **[カテゴリ]** の順に選択します。 
3. ドロップ ダウン メニューからカテゴリを選択します。

## <a name="installing-apps-on-windows-10-devices"></a>Windows 10 デバイスでのアプリのインストール
アプリの種類に応じて、次の 2 つの方法のいずれかで Windows 10 デバイスにアプリをインストールすることができます。

- **ユーザー コンテキスト**:アプリがユーザー コンテキストで展開されている場合、ユーザーがデバイスにサインインしたときにデバイス上でそのユーザーに対してマネージド アプリがインストールされます。 ユーザーがデバイスにサインインするまでは、アプリのインストールが正常に行われないことに注意してください。 
  - 最新の基幹業務アプリとビジネス向け Microsoft Store アプリ (オンラインとオフラインの両方) はユーザー コンテキストで展開することができ、必須インテントと利用可能インテントの両方をサポートします。
  - **ユーザー モード**または**デュアル モード**で構築されている Win32 アプリは、ユーザー コンテキストでデプロイでき、**必須**と**利用可能**インテントの両方をサポートします。 
- **デバイス コンテキスト**:アプリがデバイス コンテキストで展開されている場合、マネージド アプリは Intune によってデバイスに直接インストールされます。
  - 最新の基幹業務アプリと、オフライン ライセンス付きのビジネス向け Microsoft Store アプリのみがデバイス コンテキストで展開でき、必須インテントのみをサポートします。
  - **マシン モード**または**デュアル モード**で構築されている Win32 アプリは、ユーザー コンテキストでデプロイでき、**必須**インテントのみサポートします。

> [!NOTE]
> **デュアル モード** アプリとして構築された Win32 アプリは、そのインスタンスに関連付けられているすべての割り当てで、アプリが**ユーザー モード**または**マシン モード** アプリとして機能するかどうかを、管理者が選択する必要があります。 開発コンテキストは、割り当てごとに変更することはできません。  

アプリがデバイス コンテキストで展開されている場合、デバイス コンテキストがサポートされているデバイスをターゲットとするときにのみ、正常にインストールされます。 さらに、デバイス コンテキストでの展開では、次の条件がサポートされます。
- アプリがデバイス コンテキストで展開されており、ユーザーをターゲットとする場合、管理コンソールに次の状態とエラーが表示され、インストールは失敗します。
  - 状態:失敗。
  - エラー:デバイス コンテキストのインストールでユーザーを対象とすることはできません。
- アプリはデバイス コンテキストで展開されているが、デバイス コンテキストがサポートされていないデバイスをターゲットとする場合、管理コンソールに次の状態とエラーが表示され、インストールは失敗します。
  - 状態:失敗。
  - エラー:このプラットフォームはデバイス コンテキストのインストールをサポートしていません。 

> [!Note]
> 特定の展開でアプリの割り当てが保存されると、最新のアプリの場合を除き、その割り当てに対するコンテキストを変更することはできません。 最新のアプリの場合、コンテキストをユーザー コンテキストからデバイス コンテキストに変更することができます。 

単一ユーザーおよびデバイスでポリシーが競合している場合、最終的なポリシーを決定するために使用されるポリシーの優先順位は次のとおりです。
- デバイス コンテキストのポリシーの優先順位は、ユーザー コンテキストのポリシーよりも高くなります。 
- インストール ポリシーの優先順位は、アンインストール ポリシーよりも高くなります。

Microsoft Intune を使用するアプリの割り当ての詳細については、「[Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)」と「[Microsoft Intune でのアプリ割り当ての組み込みと除外](apps-inc-exl-assignments.md)」を参照してください。 Intune のアプリの種類の詳細については、「[Microsoft Intune にアプリを追加する](apps-add.md)」を参照してください。

## <a name="next-steps"></a>次の手順

- グループへのアプリの割り当てに関する詳細については、「[Microsoft Intune を使用してアプリをグループに割り当てる](apps-deploy.md)」を参照してください。
- アプリ割り当ての監視について詳しくは、[アプリを監視する方法](apps-monitor.md)に関するページをご覧ください。
