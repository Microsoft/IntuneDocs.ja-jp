---
title: ガイド付きシナリオ - クラウド マネージド モダン デスクトップ
titleSuffix: Microsoft Intune
description: Microsoft 365 デバイス管理ポータルから基本的なモダン デスクトップを設定および構成するためのガイド付きシナリオについて説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ddd59715a0730a52738088700a1f2b9166bfa80
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216213"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>ガイド付きシナリオ - クラウド マネージド モダン デスクトップ

モダン デスクトップは、インフォメーション ワーカー向けの最先端の生産性向上プラットフォームです。 Office 365 ProPlus および Windows 10 は、モダン デスクトップの主要なコンポーネントであり、Windows 10 および Microsoft Defender Advanced Threat Protection 用の最新のセキュリティ ベースラインと共に使用されます。 

モダン デスクトップをクラウドから管理することで、インターネット全体でのリモート操作の利点を活用できます。 クラウド管理では、組み込みの Windows モバイル デバイス管理ポリシーが利用され、ローカルの Active Directory グループ ポリシーに対する依存関係が削除されます。 

ご自分の組織でクラウド マネージド モダン デスクトップを評価する場合、基本的なデプロイに必要なすべての構成については、このガイド付きシナリオで事前に定義されています。 このガイド付きシナリオでは、Intune のデバイス管理機能を試すことができる安全な環境を作成します。 

## <a name="prerequisites"></a>[前提条件]
- [MDM 機関を Intune に設定する](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) - モバイル デバイス管理 (MDM) 機関の設定によって、デバイスの管理方法が決まります。 IT 管理者が MDM 機関を設定してからでないと、ユーザーは管理対象のデバイスを登録できません。
- 最低でも M365 E3 (最良のセキュリティのためには M365 E5)
- Windows 10 1903 デバイス (Windows Autopilot に登録することで最適なエンドユーザー エクスペリエンスを実現)
- このガイド付きシナリオを完了するために必要な Intune 管理者のアクセス許可:
  - デバイスの構成の読み取り、作成、削除、割り当て、および更新
  - 登録プログラムのデバイスの読み取り、プロファイルの読み取り、プロファイルの作成、プロファイルの割り当て、およびプロファイルの削除
  - モバイル アプリの読み取り、作成、削除、割り当て、および更新
  - 組織の読み取りおよび更新
  - セキュリティ ベースラインの読み取り、作成、削除、割り当て、および更新
  - ポリシー セットの読み取り、作成、削除、割り当て、および更新

## <a name="step-1---introduction"></a>ステップ 1 - 概要

Windows 10 および Office ProPlus と同様に、このガイド付きシナリオを使用して、テスト ユーザーを設定し、Intune にデバイスを登録し、Intune で推奨されている設定を使用してデバイスを展開します。 また、[Intune でこの保護を有効にする](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune)ことを選択した場合、ご利用のデバイスは Microsoft Defender Advanced Threat Protection 用に構成されます。 設定したユーザーおよび登録したデバイスは、新しいセキュリティ グループに追加され、さらにセキュリティと生産性のために推奨されている設定で構成されます。 

### <a name="what-you-will-need-to-continue"></a>続けるために必要なこと

このガイド付きシナリオでは、ご利用のテスト デバイスとテスト ユーザーを指定する必要があります。 次のタスクを必ず完了してください。
- Azure Active Directory でテスト ユーザー アカウントが設定します。
- Windows 10 バージョン 1903 以降が稼働するテスト デバイスを作成します。
- (省略可能) [Windows Autopilot にテスト デバイスを登録します](~/enrollment/enrollment-autopilot.md#add-devices)。
- (省略可能) [組織の Azure Active Directory サインイン ページに対してブランド化](https://go.microsoft.com/fwlink/?linkid=2102455)を有効にします。

## <a name="step-2---user"></a>ステップ 2 - ユーザー

デバイス上で設定するユーザーを選択します。 このユーザーは、デバイスのプライマリ ユーザーとなります。

この構成にさらにユーザーまたはデバイスを追加する場合は、ウィザードによって生成された AAD セキュリティ グループにユーザーとデバイスを追加するだけです。 他のガイド付きシナリオとは異なり、構成をカスタマイズすることはできないため、ウィザードを複数回実行する必要はありません。 作成された AAD グループにユーザーとデバイスをさらに追加するだけです。 ウィザードを完了したら、展開した推奨ポリシーで生成されたグループを表示できるようになります。 

## <a name="step-3---device"></a>ステップ 3 - デバイス

ご利用のデバイスで Windows 10 バージョン 1903 以降が稼働していることを確認します。  プライマリ ユーザーは、デバイスを受け取ったら、それを設定する必要があります。 ユーザーが使用できる設定オプションは 2 つあります。 

### <a name="option-a--windows-autopilot"></a>オプション A - Windows Autopilot
Windows Autopilot では新しいデバイスの構成が自動化されているため、ユーザーは IT 部門のサポートがなくても新しいデバイスの設定をすぐに行うことができます。 デバイスが Windows Autopilot に既に登録されている場合は、シリアル番号によって選択します。 Windows Autopilot の使用方法の詳細については、「[Windows Autopilot へのデバイスの登録 (省略可能)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional)」を参照してください。

### <a name="option-b--manual-device-enrollment"></a>オプション B – 手動でのデバイスの登録
ユーザーはモバイル デバイス管理で自分の新しいデバイスを手動で設定して登録します。 このシナリオを完了したら、デバイスをリセットし、Windows デバイス用の登録手順をプライマリ ユーザーに示します。 詳細については、[初回実行時の Windows 10 デバイスの Azure AD への参加](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device)に関するページを参照してください。

## <a name="step-4---review--create"></a>ステップ 4 - 確認と作成

最後のステップでは、構成した設定の概要を確認できます。 ご自分の選択内容を確認したら、 **[展開]** をクリックしてガイド付きシナリオを完了します。 ガイド付きシナリオが完了すると、リソースのテーブルが表示されます。 これらのリソースは後で編集できますが、いったん概要ビューを終了すると、テーブルは保存されません。

> [!IMPORTANT]
> ガイド付きシナリオが完了すると、概要が表示されます。 概要に一覧されているリソースは後で変更できますが、これらのリソースを表示しているテーブルは保存されません。

### <a name="verification"></a>検証
1. 選択した内容が MDM ユーザー スコープに割り当てられていることを確認する
    - [[MDM ユーザー スコープ]](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) を次のように確実に設定します。
        - **Microsoft Intune** アプリの場合は **[すべて]** に設定します。または、
        - **[一部]** に設定します。 また、このガイド付きシナリオで作成したユーザー グループを追加します。
2. 選択したユーザーがデバイスを Azure Active Directory に参加させることができることを確認します。
    - AAD への参加を次のように確実に設定します。
        - **[すべて]** に設定します。または、
        - **[一部]** に設定します。 また、このガイド付きシナリオで作成したユーザー グループを追加します。
3. 次の条件に基づいて Azure AD にデバイスを参加させるには、デバイスに対する適切な手順に従います。
    - Autopilot を使用する場合: 詳細については、「[Windows Autopilot ユーザー駆動モード](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)」を参照してください。
    - Autopilot を使用しない場合: 詳細については、[初回実行時の Windows 10 デバイスの Azure AD への参加](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device)に関するページを参照してください。

### <a name="what-happens-when-i-click-deploy"></a>[展開] をクリックするとどうなりますか?
ユーザーとデバイスが新しいセキュリティ グループに追加されます。 それらはまた、職場または学校でのセキュリティと生産性のために Intune で推奨される設定を使用して構成されます。 ユーザーがデバイスを Azure AD に参加させると、追加のアプリと設定がデバイスに追加されます。 このような追加の構成の詳細については、「[クイックスタート: Windows 10 デバイスを登録する](~/enrollment/quickstart-enroll-windows-device.md)」を参照してください。

## <a name="additional-information"></a>追加情報

### <a name="register-device-with-windows-autopilot-optional"></a>デバイスを Windows Autopilot に登録する (省略可能)

必要に応じて、登録されている Autopilot デバイスを使用することもできます。 Autopilot の場合、このガイド付きシナリオでは、Autopilot 展開プロファイルと登録状態ページ プロファイルが割り当てられます。 Autopilot 展開プロファイルは、次のように構成されます。
- ユーザー駆動モード - つまり、エンドユーザーは Windows 設定時にユーザー名とパスワードを入力する必要があります。
- Azure AD への参加。
- Windows 設定を次のようにカスタマイズします。
  - Microsoft ソフトウェア ライセンス条項の画面を非表示にする
  - プライバシーの設定を非表示にする 
  - ローカル管理者特権を使用せずにユーザーのローカル プロファイルを作成する
  - 会社のサインイン ページでアカウントの変更オプションを非表示にする

登録状態ページは、Autopilot デバイスに対してのみ有効になるように構成されますが、すべてのアプリがインストールされるまで待機するのを止めるわけではありません。

このガイド付きシナリオではまた、設定エクスペリエンスのパーソナライズのために、選択した Autopilot デバイスにユーザーが割り当てられます。

#### <a name="post-requisites"></a>事後条件
ユーザーがデバイスを Azure Active Directory に参加させると、デバイスには次の構成が適用されます。
1. Office 365 ProPlus がクラウド マネージド PC に自動的にインストールされます。 これには、Access、Excel、OneNote、Outlook、PowerPoint、Publisher、Skype for Business、Word など、馴染みのあるアプリケーションが含まれます。 これらのアプリケーションを使用して、SharePoint Online、Exchange Online、Skype for Business Online などの Office 365 サービスに接続することができます。 Office 365 ProPlus は、サブスクリプション以外のバージョンの Office とは異なり、定期的に新しい機能で更新されます。 新機能の一覧については、「Office 365 の新機能」を参照してください。
2. Windows セキュリティ ベースラインがクラウド マネージド PC にインストールされます。 Microsoft Defender Advanced Threat Protection が設定されている場合、ガイド付きシナリオでは、Defender に対してベースライン設定も構成されます。 Defender Advanced Threat Protection により、Windows 10 セキュリティ スタックに新しい侵害後保護レイヤーが提供されます。 Windows 10 に組み込まれたクライアント テクノロジと堅牢なクラウド サービスとの組み合わせにより、他の防御を通過した脅威を容易に検出できるようになります。 

## <a name="next-steps"></a>次のステップ

- Microsoft Defender Advanced Threat Detection を使用する場合は、[Intune コンプライアンス ポリシー](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy)を作成して、Defender 脅威分析がコンプライアンスを満たすようにする必要があります。
- デバイスが Intune コンプライアンスを満たしていない場合は、[デバイスベースの条件付きアクセス ポリシー](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy)を作成してアクセスをブロックします。
