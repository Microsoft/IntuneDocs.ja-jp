---
title: Intune ポータル サイトでの Windows デバイスの登録 | Microsoft Docs
description: ポータル サイトでの Windows デバイスの登録の概要です
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 86c158f73d820fa2e719fe92b884c77f315fcb94
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858813"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Intune ポータル サイトでの Windows デバイスの登録  

Intune ポータル サイト アプリで Windows デバイスを登録し、職場と学校のアプリ、電子メール、ファイルに安全にアクセスできるようにします。 組織で Office や OneDrive などの特定のアプリが要求または推奨されている場合は、登録中に受け取るか、または登録後にポータル サイトで入手できます。  

Windows 10 デバイスの登録は、ポータル サイトの Web サイト "*または*" アプリで行うことができます。 以前のバージョンの Windows が使用されているデバイスを登録する場合は、ポータル サイトの Web サイトで登録する必要があります。  

## <a name="install-company-portal-app"></a>ポータル サイト アプリをインストールする  
デバイスにはポータル サイト アプリが既にインストールされている可能性があります。 __[すべてのアプリ]__ の一覧でアプリを確認してください。  アプリの一覧で、[ポータル サイト] が表示されない場合は、次の手順に従ってインストールします。  

1. デバイスで **Microsoft Store** を開きます。

2. **[検索]** フィールドに、「**ポータル サイト**」と入力します。

3. 結果のリストで、 **[ポータル サイト]**  >  **[インストール]** の順に選択します。

4. **[インストール]** または **[無料]** を選択します。 これら 2 つのオプションに違いはありません。表示の違いは組織でのアプリの設定方法によるものです。  

## <a name="find-windows-10-version-number"></a>Windows 10 のバージョン番号を調べる  
登録手順は、Windows 10 デバイスのバージョンによって異なります。 以下の手順では、Windows 10 のデスクトップおよびモバイル デバイスでバージョン番号を調べる方法を説明します。 バージョンを確認した後、推奨される登録手順を続けます。  

### <a name="windows-10-desktop-devices"></a>Windows 10 Desktop デバイス  

1. **[スタート]** メニューに移動します。

2. 検索バーで、「PC 情報」と入力します。 結果から __[PC 情報]__ を選択します。  


   ![PC 情報の検索設定](media/searching_for_about_your_pc.png)  

3. **[Windows の仕様]** まで下にスクロールし、PC にインストールされている Windows 10 の **[バージョン]** を確認します。  


   ![Windows 10 Desktop の PC 情報](media/settings_about_pc.png)  

4. お使いのバージョンが  

    * __1607 以降の場合__:[ **[設定]**  >  **[アカウント]**  >  **[職場または学校へのアクセス]** の順に選択](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)して、デバイスを登録します。   
    * __1511 以前の場合__:[ **[設定]**  >  **[アカウント]**  >  **[お客様のアカウント]** の順に選択](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)して、デバイスを登録します。  

### <a name="windows-10-mobile-devices"></a>Windows 10 Mobile デバイス

1. __[すべてのアプリ]__ に移動して、 __[設定]__ アプリを選択します。
2. __[システム]__  >  __[バージョン情報]__ を選択します。
3. __[デバイス情報]__ で、__バージョン__を確認します。  
4. お使いのバージョンが  

    * __1607 以降の場合__:[ **[設定]**  >  **[職場または学校へのアクセス]** の順に選択](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device)して、デバイスを登録します。   
    * __1511 以前の場合__:[ **[設定]**  >  **[アカウント]** の順に選択](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device)して、デバイスを登録します。  

## <a name="enroll-non-windows-10-devices"></a>Windows 10 以外のデバイスを登録する  
ポータル サイト Web サイトで他のサポートされている Windows デバイスを登録するには、次の記事を使用してください。   
* [Windows 8.1 または Windows RT 8.1 デバイス](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1 デバイス](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>IT 管理者のサポート  
デバイス登録中に問題に遭遇した IT 管理者は、「[Microsoft Intune の Windows デバイスの登録に関する問題のトラブルシューティング](https://support.microsoft.com/help/4469913)」を参照してください。 この記事では、一般的なエラー、その原因、解決する手順の一覧が示されています。  

## <a name="next-steps"></a>次のステップ  
サポートされているデバイスと、お使いの Windows 10 のバージョン番号がわかったので、推奨される登録の記事に進んでください。  
 
デバイスの管理、ポータル サイト、および学校と職場での両方の使用方法の詳細については、次の記事を参照してください。  
* [管理対象デバイスを使用して職場または学校のリソースにアクセスする](use-managed-devices-to-get-work-done.md)  
* [ポータル サイト アプリをインストールし、Intune に iOS または Mac OS X デバイスを登録するとどうなりますか](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [デバイスを登録した場合に組織が確認できる情報](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

サポートが必要な場合は、 社内サポートに問い合わせてください。 組織の IT 部門の連絡先情報を検索するには、[ポータル サイトの Web サイトに移動してください](https://go.microsoft.com/fwlink/?linkid=2010980)。  
