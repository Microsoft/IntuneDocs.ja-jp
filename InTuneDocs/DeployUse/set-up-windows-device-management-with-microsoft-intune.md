---
title: "Microsoft Intune を使用して Windows デバイスの管理をセットアップする | Microsoft Intune"
description: "Microsoft Intune を使用して Windows 10 デバイスを含む Windows PC のモバイル デバイス管理 (MDM) を有効にします。"
keywords: 
author: staciebarker
manager: stabar
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d51f34dea3463bec83ea39cdfb79c7bedf9e3926
ms.openlocfilehash: 78137299b1c4e18fe68e1f9720a2111d1794e177


---

# <a name="set-up-windows-device-management"></a>Windows デバイスの管理をセットアップする

Intune 管理者として、以下の 2 つの方法で Windows PC の登録と管理を有効にできます。

- **[Azure Active Directory での自動登録](#azure-active-directory-enrollment)** - Windows 10 および Windows 10 Mobile のユーザーが職場または学校のアカウントを追加することでデバイスを登録します。
- **[ポータル サイト登録](#company-portal-app-enrollment)** - Windows 8.1 以降のユーザーがポータル サイト アプリをダウンロードおよびインストールして、職場または学校のアカウント資格情報を入力することでデバイスを登録します。

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-company-portal-app-enrollment"></a>ポータル サイト アプリの登録を設定する
Intune ポータル サイト アプリをデバイスにインストールして登録することによって、ユーザーはデバイスを登録できます。 DNS の CNAME リソース レコードを作成すると、ユーザーはサーバー名を入力することなく Intune に接続して登録できるようになります。

1. **Intune をセットアップする**<br>
**Microsoft Intune** を[モバイル デバイス管理 (MDM) 機関に設定](prerequisites-for-enrollment.md#set-mobile-device-management-authority)して、MDM の設定を行うことにより、モバイル デバイス管理を準備します (この作業をまだ行っていない場合)。

2. **CNAME を作成する** (省略可能)<br>会社のドメインの **CNAME** DNS リソース レコードを作成すると、簡単に登録できます。 CNAME DNS エントリの作成は省略可能ですが、CNAME レコードにより登録が簡単になります。 CNAME レコードの登録が見つからない場合、ユーザーは手動で MDM サーバー名 `https://manage.microsoft.com` を入力するように求められます。 CNAME リソース レコードには次の情報を含める必要があります。

  |種類:|ホスト名|指定先|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 時間|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 時間|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Intune サービスへのリダイレクトと電子メールのドメイン名によるドメイン認識をサポートします

  `EnterpriseRegistration.windows.net` – 職場または学校のアカウントを使用して Azure Active Directory に登録される Windows 8.1 および Windows 10 Mobile デバイスをサポートします

  会社でユーザーの資格情報に複数のドメインを使用する場合は、各ドメインに CNAME レコードを作成します。

  たとえば、会社の Web サイトが contoso.com の場合、EnterpriseEnrollment.contoso.com を EnterpriseEnrollment-s.manage.microsoft.com にリダイレクトする CNAME を DNS に作成します。 DNS レコードの変更が反映されるまでには、最大で 72 時間かかります。 DNS レコードの変更が反映されるまで、Intune で DNS の変更を確認することはできません。

3.  **CNAME を確認する**<br>[Intune 管理コンソール](http://manage.microsoft.com)で、**[管理]** &gt; **[モバイル デバイス管理]** &gt; **[Windows]** の順に選択します。 **[検証済みドメイン名の指定]** ボックスに会社の Web サイトの検証済みドメインの URL を入力し、**[自動検出のテスト]** を選択します。

  ![Windows デバイスの管理ダイアログ ボックス](../media/enroll-intune-winenr.png)

4.  **オプションの手順**<br>**サイドローディング キーの追加**の手順は、Windows 10 には必要ありません。 **コード署名証明書のアップロード**の手順は、Windows ストアから使用できない基幹業務 (LOB) アプリをデバイスに配信する場合にのみ必要です。

6.  **ユーザーに、デバイスを登録する方法とデバイスが管理されるとどうなるかを伝える**

    エンドユーザー用の登録手順については、「[Intune に Windows デバイスを登録する](../enduser/enroll-your-device-in-intune-windows.md)」を参照してください。

    エンドユーザー タスクの詳細については、次の記事を参照してください。
      - [Microsoft Intune を使用したエンドユーザー エクスペリエンスに関するリソース](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Windows デバイス向けエンド ユーザー ガイダンス](../enduser/using-your-windows-device-with-intune.md)

### <a name="see-also"></a>関連項目
[Microsoft Intune でデバイスを登録するための前提条件](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO2-->


