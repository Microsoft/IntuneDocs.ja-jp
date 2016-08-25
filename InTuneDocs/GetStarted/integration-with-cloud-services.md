---
title: "Microsoft クラウド サービスと Intune の統合 |Microsoft Intune"
description: "Microsoft クラウド サービスおよび製品やその他の Microsoft 製品と Intune との統合"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 6523c731e8351b121cba46f6c5d2ef46db656c2c


---

# Microsoft クラウド サービスおよび製品と Intune の統合

[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] をセットアップする前に、このトピックと「[What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)」 (Microsoft Intune を開始する前に理解しておくこと) に挙げられているその他の要件を確認してください。
##他の Microsoft クラウド サービスとの統合


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] は、Microsoft の他のクラウド サービスと共通の基盤を共有しています。 複数のクラウド サービスへのサブスクライブで同じアカウントを使用する場合、それらのサービスでは同一の Microsoft Azure AD インフラストラクチャが使用され、Azure AD のテナントになります。 Azure AD は、Microsoft Cloud Services の中核ディレクトリとなり、ID 管理機能を使用できます。

TechNet ライブラリで [Azure AD の管理](http://technet.microsoft.com/library/hh967611.aspx)の詳細について、ご確認ください。

## 他の Microsoft 製品との統合
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] は、スタンドアロンのクラウド サービス、または他の製品と統合するクラウド サービスとして使用できます。 現在、[!INCLUDE[cmshort](../includes/cmshort_md.md)] と直接統合できるのは、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] だけです。

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を [!INCLUDE[cmshort](../includes/cmshort_md.md)] と統合するかどうかは永続的な選択で、[!INCLUDE[cmshort](../includes/cmshort_md.md)]内からではなく、[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] コンソールからモバイル デバイス管理機関を設定する必要があります。 モバイル デバイス管理機関を設定した後で、この構成を変更、または元に戻すことはできません。

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] を [!INCLUDE[cmshort](../includes/cmshort_md.md)] で使用する場合、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] の管理には、[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]ではなく [!INCLUDE[cmshort](../includes/cmshort_md.md)] コンソールを使用してください。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] では、[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] で管理するデバイスに展開するソフトウェアをホストするために、現在も Azure のクラウド ストレージを使用しています。

詳細については、[!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1 のドキュメントで「[Configuration Manager と Microsoft Intune を使用してモバイル デバイスを管理する](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10)」を参照してください。

### 関連項目
[Microsoft Intune を使い始める前に](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


