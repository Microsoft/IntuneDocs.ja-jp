---
title: Office 365 モバイル アプリから会社のデータが漏えいすることを防止する
description: Intune を使用して、Office 365 モバイル アプリやその他の基幹業務 (LOB) アプリから会社のデータが漏洩することを防止するために役立つモバイル アプリ管理 (MAM) ポリシーを使用して、組織のデータをセキュリティで保護できます。
keywords: ''
author: jeffgilb
ms.author: jeffgilb
manager: dougeby
ms.date: 11/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b0117ef734a8549593992108105192ce1c4de5b0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>クイック スタート ガイド: Office 365 モバイル アプリから会社のデータが漏洩することを防止する

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune では、Office 365 モバイル アプリやその他の基幹業務 (LOB) アプリから会社のデータが漏洩することを防止するために役立つモバイル アプリケーション管理 (MAM) ポリシーを使用して、組織のデータをセキュリティで保護できます。 Intune MAM ポリシーは、エンドユーザーによる Intune モバイル デバイス管理 (MDM) へのデバイスの登録なしで使用できます。 したがって、Microsoft MDM ソリューション (Intune、Configuration Manager、または EAS) に BYOD iOS または Android モバイル デバイスを登録しないユーザーがいる場合でも、エンド ユーザーのデバイスの管理なしで会社のデータを保護することができます。また、Microsoft 以外の MDM ソリューションを既に使用している場合は、Intune で会社のデータ セキュリティを強化できます。   

## <a name="is-this-quick-start-guide-right-for-me"></a>このクイック スタート ガイドの対象読者
iOS および Android デバイスをモバイル デバイス管理 (MDM) ソリューションに登録せずに Office 365 および LOB アプリ データにアクセスすることをエンド ユーザーに許可するが、エンド ユーザーが何を実行でき、何を実行できないか (個人のアプリへのデータのコピーや貼り付けなど) を制御したいと考えていますか。

そう考えているのであれば、Microsoft Intune を使用して、iOS と Android 上の Office 365 モバイル アプリに適用する MAM ポリシー (切り取り/コピー/貼り付け制限、[名前を付けて保存] の使用不可、PIN 要件の設定など) を設定し、MAM 保護対象データをリモートで削除できます。  これによって、MDM ソリューションへのデバイスの登録をユーザーに要求しなくても会社のデータを保護することができ、Office モバイル アプリの優れたエンド ユーザー エクスペリエンスを維持できます。

## <a name="how-do-i-do-it"></a>実行方法
1.  [Intune モバイル アプリケーション管理 (MAM)](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) がどのように機能するかについて、その基本を理解します。
2.  Azure ポータルで [MAM ポリシーを作成する前に実行する必要があること](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)を確認します。
3.  Intune で [MAM ポリシーを作成して展開](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)します。

### <a name="additional-information"></a>追加情報:
- MAM 対応アプリでの[エンド ユーザー エクスペリエンス](/intune-classic/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune)
- [Intune で MAM 用に LOB アプリを準備する](/intune/apps-prepare-mobile-application-management)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank"> Microsoft Intune アプリケーション パートナー一覧 &rarr;</a> MAM 対応アプリの提供

## <a name="what-should-i-do-next"></a>次にすべきこと
[Microsoft MDM 以外のソリューションから Microsoft Intune に移行する](/intune-classic/deploy-use/migrate-to-intune)

[Intune MDM にデバイスを登録する](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)
