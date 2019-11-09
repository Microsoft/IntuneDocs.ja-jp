---
title: コードの整合性を有効にする必要がある | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 84892bbc-f888-417b-bbeb-978cc7e10028
searchScope:
- User help
ROBOTS: ''
ms.reviewer: scottduf
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bde7fc554496b2ecc6f13c7e1b899d7ff05bfa1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754985"
---
# <a name="enable-code-integrity"></a>コードの整合性を有効にする

組織では、*コード整合性*と呼ばれる脅威保護機能を使用して PC を有効にすることが必要になる場合があります。 コードの整合性では、破損または悪意のあるソフトウェアの署名について、デバイス上のドライバーとシステムファイルをチェックします。 コードの整合性をデバイスで機能させるには、[*セキュアブート*](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process#secure-boot)と呼ばれる別のセキュリティ機能も有効にする必要があります。

コードの整合性が無効になっているために PC が準拠していない場合は、組織の IT サポートチームにお問い合わせください。 セキュアブートを有効にすることができます。これにより、次回デバイスを起動したときにコードの整合性がトリガーされます。

自分自身をアドバンストデバイスユーザーとして識別し、自分で手順を実行する場合は、「[セキュアブートの再有効化](https://docs.microsoft.com/windows-hardware/manufacture/desktop/disabling-secure-boot#re-enable-secure-boot)」を参照してください。

## <a name="additional-resources-for-it-administrators"></a>IT 管理者向けのその他のリソース

Intune 管理者で、Intune のデバイス正常性のコンプライアンス設定の詳細については、「 [intune で Windows 10 デバイス用のデバイスコンプライアンスポリシーを追加](https://docs.microsoft.com/intune/protect/compliance-policy-create-windows)する」を参照してください。 Intune で実行できるコンプライアンスアクションの詳細については、「 [HEALTHATTESTATION CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp#step-8-take-appropriate-policy-action-based-on-evaluation-results)」を参照してください。  

## <a name="next-steps"></a>次の手順

サポートが必要な場合は、 社内サポートに問い合わせてください。 連絡先情報については、[ポータル サイト Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください。
