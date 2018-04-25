---
title: Windows 10 ポータル サイト アプリを手動で追加する
titleSuffix: Microsoft Intune
description: Windows 10 ポータル サイト アプリを手動で追加する方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f2c7e449e9931bccd5e736bd09c33e0b42c623e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>Microsoft Intune を使用して Windows 10 ポータル サイト アプリを手動で追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

エンド ユーザーは Microsoft ストアからポータル サイト アプリをインストールすることで、デバイスを管理し、アプリをインストールすることができます。 ただし、ビジネスでポータル サイト アプリを割り当てる必要がある場合は、Intune をビジネス向け Microsoft ストアと統合していない場合でも、Intune から直接 Windows 10 ポータル サイト アプリを手動で割り当てることができます。

 > [!NOTE]
 > このオプションでは、アプリの更新プログラムがリリースされるたびに、手動更新を割り当てる必要があります。

## <a name="configure-settings-to-show-offline-apps"></a>オフライン アプリ表示するように設定を構成する
1. [[ビジネス向け Microsoft ストア]](https://www.microsoft.com/business-store) に移動して、管理者アカウントでサインインしたことを確認します。
2. ウィンドウの上部付近にある **[管理]** タブを選択します。
3. 左側のナビゲーション列の **[設定]** を選択します。
4. **[Shopping experience]\(ショッピング体験\)** セクションの **[Show offline apps]\(オフライン アプリの表示\)** を **[オン]** に設定します。 これで、ビジネス向け Microsoft ストアにオフラインのライセンスされたアプリが表示されます。

## <a name="download-the-offline-company-portal-app"></a>オフラインのポータル サイト アプリをダウンロードする
1. **ポータル サイト** アプリを検索して選択します。
2. **[ライセンスの種類]** を **[オフライン]** に設定します。
3. **[アプリの取得]** をクリックし、オフラインのポータル サイト アプリを取得して、インベントリに追加します。
4. **[ポータル サイト]** アプリ ページの **[管理]** をクリックします。
5. **プラットフォーム**として **[Windows 10 *all devices*]\(Windows 10 の*すべてのデバイス*\)** を選択し、適切な**最小バージョン**、**アーキテクチャ**、アプリ メタデータのダウンロードの各値を選択します。 
6. **[ダウンロード]** をクリックして、ローカル コンピューターにファイルを保存します。

    ![ダウンロードする Windows 10 のすべてのデバイスとアーキテクチャ X86 のパッケージ詳細のイメージ](./media/Win10CP-all-devices.png)

7. [必要なフレームワーク] の下のすべてのパッケージをダウンロードします。 これは x86、x64、ARM アーキテクチャ用に実行する必要があります (パッケージは合計で 12 個になります)。
8. ポータル サイト アプリを Intune にアップロードする前に、パッケージを次のように構成してフォルダー (C:&#92;ポータル サイトなど) を作成します。
   - C:\ポータル サイトにポータル サイト パッケージを配置します。 また、この場所に依存関係サブフォルダーも作成します。  

     ![APPXBUN ファイルと共に保存された依存関係フォルダーのイメージ](./media/Win10CP-Dependencies-save.png)

   - *依存関係*フォルダーに依存関係パッケージを配置します。 

     > [!NOTE]
     > 依存関係が正しい形式で配置されていない場合、Intune はパッケージのアップロード時にファイルを認識してアップロードできなくなり、アップロードは失敗し、エラーが表示されます。

9. Azure Portal の Microsoft Intune に戻ります。
10. ポータル サイト アプリを新しいアプリとしてアップロードします。 これを必要なアプリとして対象の一連のターゲット ユーザーに割り当てます。  

Intune がユニバーサル アプリ用に依存関係をどのように処理するかについて詳しくは、「[Deploying an appxbundle with dependencies via Microsoft Intune MDM (Microsoft Intune MDM 経由で依存関係を使用して appxbundle を展開する)](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)」ご覧ください。  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>ユーザーがストアから古いアプリを既にインストールしている場合に、ユーザーのデバイスのポータル サイトを更新する方法
貴社のユーザーがストアから Windows 8.1 または Windows Phone 8.1 ポータル サイト アプリを既にインストールしている場合は、お客様またはお客様のユーザーが特に操作を行わなくても新しいバージョンに自動的に更新されます。 更新が実行されない場合は、デバイスでストア アプリの自動更新を有効にしているかどうかをユーザーに確認してください。   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>サイドロードした Windows 8.1 のポータル サイト アプリを Windows 10 のポータル サイト アプリにアップグレードする方法
推奨される移行パスとして、割り当てアクションを "アンインストール" に設定して、Windows 8.1 ポータル サイト アプリの割り当てを削除します。 この設定が完了したら、上記のいずれかのオプションを使用して、Windows 10 ポータル サイト アプリを割り当てることができます。  

アプリをサイドロードする必要があり、Symantec 証明書で署名せずに Windows 8.1 ポータル サイトを割り当てた場合は、上の Intune セクションから直接、割り当てに関する手順に従ってアップグレードを完了します。

アプリをサイドロードする必要があり、Symantec コード署名証明書で Windows 8.1 ポータル サイトに署名し割り当てた場合は、以下のセクションの手順に従ってください。  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>署名およびサイドロードした Windows Phone 8.1 ポータル サイト アプリまたは Windows 8.1 ポータル サイト アプリを Windows 10 ポータル サイト アプリにアップグレードする方法
推奨される移行パスとして、割り当てアクションを "アンインストール" に設定して、Windows Phone 8.1 ポータル サイト アプリまたは Windows 8.1 ポータル サイト アプリの既存の割り当てを削除します。 設定が完了したら、通常どおり Windows 10 ポータル サイト アプリを割り当てることができます。  

これ以外の場合は、アップグレードのパスが確実に考慮されるように Windows 10 ポータル サイト アプリを適切に更新し、署名する必要があります。  

この方法で Windows 10 ポータル サイト アプリに署名し割り当てた場合、ストアで入手可能になった新しいアプリの更新プログラムごとにこのプロセスを繰り返す必要があります。 ストアが更新されたときに、アプリは自動的に更新されません。  

この場合のアプリへの署名および割り当て方法は、次のとおりです。

1. Microsoft Intune Windows 10 ポータル サイト アプリの署名スクリプトを [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) からダウンロードします。  このスクリプトでは、Windows SDK for Windows 10 をホスト コンピューターにインストールする必要があります。 Windows 10 用 Windows SDK をダウンロードするには、[https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296) にアクセスします。
2. 上記の説明のように、ビジネス向け Microsoft ストアから Windows 10 ポータル サイト アプリをダウンロードします。  
3. スクリプト ヘッダーに記載された入力パラメーターを使用してスクリプトを実行し、Windows 10 ポータル サイト アプリに署名します (以下に抜粋)。 スクリプトに依存関係を渡す必要はありません。 依存関係は、アプリが Intune 管理コンソールにアップロードされる場合にのみ必要です。

|       パラメーター       |                                                                        説明                                                                        |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                                  ソース appxbundle ファイルが配置されるパス                                                  |
| OutputWin10AppxBundle | 署名された appxbundle ファイルの出力パス  Win81Appx Windows 8.1 または Windows Phone 8.1 ポータル サイト (.APPX) ファイルが配置されるパス |
|      PfxFilePath      |                                       Symantec エンタープライズ モバイル コード署名証明書 (.PFX) ファイルへのパス                                        |
|      PfxPassword      |                                         Symantec エンタープライズ モバイル コード署名証明書のパスワード                                          |
|      PublisherId      |          エンタープライズの発行者 ID 指定しない場合、Symantec エンタープライズ モバイル コード署名証明書の 'Subject' フィールドが使用されます。           |
|        SdkPath        |     Windows SDK for Windows 10 のルート フォルダーへのパス この引数は省略可能で、既定値は ${env:ProgramFiles(x86)}\Windows Kits\10 です。     |

実行が終了したら、スクリプトにより Windows 10 ポータル サイト アプリの署名されたバージョンが出力されます。 その後、アプリの署名されたバージョンを Intune 経由で LOB アプリとして割り当てることができます。これにより、現在割り当てられているバージョンがこの新しいアプリにアップグレードされます。  

## <a name="next-steps"></a>次の手順

- [アプリをグループに割り当てる方法](apps-deploy.md)

