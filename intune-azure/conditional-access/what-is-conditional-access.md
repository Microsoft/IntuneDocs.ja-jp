---
title: "条件付きアクセスとは | Intune Azure プレビュー | Microsoft Docs"
description: "Intune Azure プレビュー: 会社のリソースにアクセスするためにユーザーおよびデバイスで満たす必要のある条件を Microsoft Intune Azure プレビューで定義する方法について説明します。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 41931f64db969c82f79e007c4be9e68b7caf4ce9
ms.openlocfilehash: 20696fb2dc0126aa224e779738cedb4f95f666e8


---

# <a name="what-is-conditional-access"></a>条件付きアクセスとは


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


このトピックでは、Enterprise Mobility + Security に適用される条件付きアクセスについて説明し、さらに Intune での条件付きアクセス機能についても取り上げます。

Enterprise Mobility + Security (EMS) からの条件付きアクセスでは、Azure Active Directory Premium と Microsoft Intune の機能を利用することにより、会社のデータの安全性を保つために必要な制御を提供する一方で、どのようなデバイスからでも最適に作業ができるユーザー エクスペリエンスを実現しています。

条件付きアクセスを利用すると、会社のデータへのアクセスを場所、デバイス、ユーザーの状態、アプリケーションの機密度に基づき制限する条件を定義できます。

デバイスの観点から見ると、Intune と Azure Active Directory が連携することで、管理対象デバイスと準拠デバイスのみが電子メールおよび Office 365 サービスにアクセスできるようになっています。 たとえば、Azure Active Directory では、ドメインに参加しているコンピューターや、Intune のようなモバイル デバイス管理アプリケーションに登録されているモバイル デバイスのみが Office 365 サービスにアクセスできるようにするポリシーを設定できます。 Intune を使用すると、デバイスのコンプライアンス対応状態を評価するデバイス コンプライアンス プロファイルを設定できます。 コンプライアンス対応状態は Azure Active Directory に報告され、ユーザーが会社のリソースにアクセスしようとしたときに Azure Active Directory 内でポリシーを適用するために使用されます。 Intune でのデバイス コンプライアンスについては、[デバイス コンプライアンス](/intune-azure/set-device-compliance/what-is-device-compliance)に関するページを参照してください。

Exchange Online などのクラウド アプリ向けの条件付きアクセスは、Azure Active Directory を介して構成できます。 詳細については、[こちらの記事](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal)を参照してください。

## <a name="on-premises-conditional-access-in-intune"></a>Intune のオンプレミス条件付きアクセス

Intune の条件付きアクセスを使用すると、デバイスの管理と登録に基づき **Exchange On-Premises** へのアクセスを許可またはブロックすることができます。

デバイスのコンプライアンスを評価するために、デバイス コンプライアンス プロファイルの設定が使用されます。 条件付きアクセスでは、この評価を使用して Exchange On-Premises へのアクセスを許可またはブロックします。 条件付きアクセスをデバイス コンプライアンス プロファイルと組み合わせて使用した場合は、準拠デバイスのみが Exchange On-Premises へのアクセスを許可されます。 特定のプラットフォームを許可またはブロックする、Intune で管理されていないデバイスを直ちにブロックするなど、さらにきめ細かい制御を行うには、条件付きアクセスで詳細設定を構成できます。

デバイス コンプライアンス プロファイルと条件付きアクセスは、ユーザーに割り当てられます。 Exchange On-Premises へのアクセスにユーザーが使用するすべてのデバイスに対して、コンプライアンスのチェックが行われます。 デバイスを使用しているユーザーには、そのデバイスのコンプライアンスを評価するために、コンプライアンス プロファイルが割り当てられている必要があるという点に注意してください。 コンプライアンス ポリシーがユーザーに展開されていない場合、デバイスは準拠したものと見なされ、アクセス制限は適用されません。

デバイスが条件を満たしていない場合、デバイスの登録と、デバイスが準拠デバイスとなることを妨げている問題の修正を行うプロセスがエンド ユーザーに案内されます。

## <a name="next-steps"></a>次のステップ

[Exchange On-Premises の条件付きアクセス ポリシーを作成する方法](create-conditional-access-policy-for-exchange-on-premises.md)

[Azure Active Directory で条件付きアクセスを構成する方法](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal)



<!--HONumber=Feb17_HO1-->


