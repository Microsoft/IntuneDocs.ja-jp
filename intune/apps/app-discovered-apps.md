---
title: 検出されたアプリ
titleSuffix: Microsoft Intune
description: Intune によってデバイスで検出されたアプリの詳細について理解します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: eff4ccdc8b40da4d72394001b88446653ff71bd0
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564242"
---
# <a name="intune-discovered-apps"></a>Intune で検出されたアプリ

Intune で**検出されたアプリ**は、テナント内の Intune に登録されているデバイスで検出されたアプリの一覧です。 これはテナントのソフトウェア インベントリとして機能します。 **検出されたアプリ**は、[アプリのインストール](apps-monitor.md) レポートとは別のレポートです。 個人用デバイスの場合、アンマネージド アプリケーションに関する情報が Intune で収集されることはありません。 企業デバイスでは、マネージド アプリであるかどうかにかかわらず、このレポートのためにすべてのアプリが収集されます。 予想される動作をマッピングするテーブルを次に示します。 一般に、レポートは登録時から 7 日おきに更新されます (テナント全体の週次の更新ではありません)。 この更新期間の唯一の例外は、Win32 アプリ用 Intune 管理拡張機能を通じて 24 時間ごとに収集されるアプリケーション情報です。

## <a name="monitor-discovered-apps-with-intune"></a>検出されたアプリを Intune で監視する

Intune では、テナント内の Intune に登録されているデバイス上で検出されたアプリを集計した一覧が提供されます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[アプリ]**  >  **[監視]**  >  **[検出されたアプリ]** を選択します。

>[!NOTE]
>**[検出されたアプリ]** ウィンドウの **[エクスポート]** を選択することで、検出されたアプリの一覧を .csv ファイルにエクスポートできます。
>
>検出された Win32 アプリについては、現在は集計にカウントされません。 この種類のデータは、デバイスごとにのみ表示できます。

Intune では、テナント内の個々のデバイスについて検出されたアプリの一覧も提供されます。

1. [Microsoft Endpoint Manager 管理センター](https://go.microsoft.com/fwlink/?linkid=2109431)にサインインします。
2. **[デバイス]**  >  **[すべてのデバイス]** を選択します。
3. デバイスを選択します。
4. このデバイスで検出されたアプリを表示するには、 **[監視]** セクションで **[検出されたアプリ]** を選択します。

## <a name="details-of-discovered-apps"></a>検出されたアプリの詳細

次の一覧に、アプリ プラットフォームの種類、個人用デバイスに対して監視されるアプリ、会社所有のデバイスに対して監視されるアプリ、および更新サイクルを示します。 Intune でサポートされるアプリの種類の詳細については、「[Microsoft Intune のアプリの種類](apps-add.md#app-types-in-microsoft-intune)」を参照してください。

| プラットフォーム | 個人所有のデバイス | 会社所有のデバイス | 更新サイクル |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32 アプリ) メモ:デバイスに [Intune 管理拡張が必要](intune-management-extension.md) | 適用しない | [プログラムの追加と削除] の一覧にあるすべての Win32 アプリ | デバイス登録から 24 時間ごと |
| Windows 10 (モダン アプリ) | マネージド モダン アプリのみ | デバイスにインストールされているすべてのモダン アプリ | デバイス登録から 7 日おき |
| Windows 8.1 | 管理対象アプリのみ | 管理対象アプリのみ | デバイス登録から 7 日おき |
| Windows Phone 8 | 管理対象アプリのみ | 管理対象アプリのみ | デバイス登録から 7 日おき |
| Windows RT | 管理対象アプリのみ | 管理対象アプリのみ | デバイス登録から 7 日おき |
| iOS | 管理対象アプリのみ | デバイスにインストールされているすべてのアプリ | デバイス登録から 7 日おき |
| macOS | デバイスにインストールされているすべてのアプリ | デバイスにインストールされているすべてのアプリ | デバイス登録から 7 日おき |
| Android | 管理対象アプリのみ | デバイスにインストールされているすべてのアプリ | デバイス登録から 7 日おき |
| Android エンタープライズ | 管理対象アプリのみ | 仕事用プロファイル内にインストールされているアプリのみ | デバイス登録から 7 日おき |

> [!NOTE]
> Configuration Manager のアプリ管理ワークロードに示されているように、Windows 10 Hybrid Azure AD の参加済みデバイスでは現在、前述のスケジュールに従って Intune 管理拡張機能 (IME) 経由でアプリ インベントリは収集されません。 この問題を軽減するには、IME がデバイス上にインストールされるように、Configuration Manager 内のアプリ管理ワークロードを Intune に切り替える必要があります (Win32 インベントリと PowerShell の展開には、IME が必要です)。 この動作に対する変更や更新はすべて、[開発中](../fundamentals/in-development.md)や[新機能](../fundamentals/whats-new.md)に関する記事に発表されることに注意してください。

検出されたアプリの数が、インストール状態のアプリの数と一致しない場合があります。 一致しないケースとしては次の可能性があります。

- インストールされているマネージド アプリのターゲットの変更によって、[状態] ウィンドウのインストール数が減少するが、検出されたアプリには報告されたままになることがあります。
- テナント内の同一アプリの複数インスタンスをターゲットにすると、ユーザーまたはデバイスが重複する可能性があり、結果として件数が異なることがあります。 アプリの各インスタンスが重複するユーザーをカウントし、検出されたアプリが重複したカウントを含んでいることがあります。
- 検出されたアプリとアプリの状態が異なる間隔で収集されるため、アプリ数の不一致が引き起こされることがあります。

## <a name="next-steps"></a>次の手順

- [Microsoft Intune のアプリの種類](apps-add.md#app-types-in-microsoft-intune)
- [Microsoft Intune でアプリの情報と割り当てを監視する](apps-monitor.md)
