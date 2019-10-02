---
title: Microsoft Intune がお客様の会社のためにできること
titleSuffix: ''
description: Microsoft Intune が解決に役立つ一般的なビジネス問題。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/26/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 845eb22522895e04f6ec4f46eda7a817e27a830c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726532"
---
# <a name="what-can-intune-do-for-my-company"></a>Intune が会社のためにできることとは。
Microsoft Intune はクラウドベースのエンタープライズ モビリティ管理 (EMM) サービスであり、これでは、会社のデータを守りながら、社員に生産的に働いてもらうことができます。

Intune では次のことができます。

- 社員が会社のデータにアクセスするために利用するモバイル デバイスを管理します。
- 社員が利用するモバイル アプリを管理します。
- 社員が会社の情報にアクセスし、共有する方法を制御し、会社の情報を保護します。
- デバイスやアプリが会社のセキュリティ要件に準拠するように管理します。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune が解決に役立つ一般的なビジネス問題

* [モバイル デバイスでアクセスできるようにオンプレミスの電子メールとデータを保護する](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [モバイル デバイスで安全にアクセスできるように Office 365 の電子メールとデータを保護する](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [社員向けに企業所有の携帯電話を用意する](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [すべての従業員に "Bring your own device" (BYOD) プログラムという個人デバイス プログラムを提供する](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [公共の場所から Office 365 に安全にアクセスできるようにする](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [タスク ワーカー向けに制限付きの共有タブレットを用意する](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="quickstarts"></a>クイックスタート

モバイル デバイスの管理の開始が困難な場合があることがわかりました。 ご自身の会社の代わりに、さまざまな決定を多数行う必要があります。 次のクイックスタートでは、Intune の概要を説明すると共に、いくつかの一般的なタスクをわずかな時間で完了させます。

ページの左側にある目次を使って、**クイック スタート**の意図された順番に従うことができます。

- [Intune の無料試用](free-trial-sign-up.md) - Intune をテスト環境で使用する無料のサブスクリプションを作成できます。    
- [ユーザーの作成](quickstart-create-user.md) - Intune にユーザーを追加して、モバイル デバイスから会社のリソースにアクセスできるようにします。
- [グループの作成](quickstart-create-group.md) - ユーザーをグループにまとめ、ユーザーがアクセスできるポリシーやアプリを管理しやすくします。
- [自動登録の設定](../enrollment/quickstart-setup-auto-enrollment.md) - 特定のユーザーが Windows 10 デバイスにサインインしたとき、Intune がデバイスを自動的に登録するように設定します。
- [デバイスの登録](../enrollment/quickstart-enroll-windows-device.md) - Intune ユーザーのロールで、ご自分のデバイスを Intune に登録します。 次に、Intune に戻ってデバイスが正常に登録されたことを確認します。
- [デバイスのコンプライアンス ポリシーの作成](../protect/quickstart-set-password-length-android.md) - デバイスのコンプライアンス ポリシーを作成し、そのポリシーにグループを割り当てます。
- [非対応のデバイスへの通知の送信](../protect/quickstart-send-notification.md) - コンプライアンス ポリシーを作成して割り当てることで、デバイスが非対応である従業員メンバーにメール通知を送信します。
- [アプリの追加および割り当て](../apps/quickstart-add-assign-app.md) - 職場の従業員に、クライアント アプリを追加および割り当てます。
- [アプリ保護ポリシーの作成および割り当て](../apps/quickstart-create-assign-app-policy.md) - エンド ユーザーのデバイス上のクライアント アプリに対し、アプリ保護ポリシーを作成および割り当てます。
- [カスタム ロールの作成および割り当て](create-custom-role.md) - セキュリティ オペレーション部門用に特定のアクセス許可のあるカスタム ロールを作成および割り当てます。 
- [iOS 用の電子メール デバイス プロファイルの作成](../configuration/quickstart-email-profile.md) - iOS デバイス用の電子メール デバイス プロファイルを作成します。

## <a name="prerequisites"></a>必要条件

始める前に、Intune の管理者/テナント アカウントをアクティブにしておく必要があります。 テスト環境で [Intune を無料で試す](free-trial-sign-up.md)無料のサブスクリプションを作成します。 現行のサブスクライバーも、各自のライブ テナントでこれらのアクティビティを完了できます。 これらの概要の記事は、テスト デバイス上で作業することを前提としています。

また、すべての入門タスクを完了するためには、自分が組織のグローバル管理者になっていることを確認する必要があります。

## <a name="intune-architecture"></a>Intune アーキテクチャ

Intune は Enterprise Mobility + Security (EMS) に含まれ、モバイル デバイスとモバイル アプリを管理します。 ID とアクセス制御のために Azure Active Directory (Azure AD) のような他の EMS コンポーネントと、データ保護のために Azure Information Protection と密接に統合されます。 これを Office 365 と共に使う場合、従業員が各自のデバイスを生産的に活用できるようにしながら、同時に組織の情報を保護することができます。

![Microsoft Intune の概要的アーキテクチャ図](./media/get-started-evaluation/intunearchitecture.svg)

## <a name="next-steps"></a>次の手順

[Azure 使用の概要](tutorial-walkthrough-intune-portal.md) - Azure Portal の構造とページ レイアウトの変更方法について理解します。

## <a name="learn-more"></a>詳細情報

- [Intune とは](what-is-intune.md)
- [Azure Portal とは](what-is-intune.md)
- [デバイスとアプリのライフサイクル](device-lifecycle.md)
