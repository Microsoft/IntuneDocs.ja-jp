---
title: Windows 10 ポータル サイト アプリを手動で追加する
titleSuffix: Microsoft Intune
description: 従業員が Microsoft Store から自分の PC へ Windows 10 ポータル サイト アプリを手動で追加できる方法について説明します。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 755e836c5954b9cbbf3c7729755aaa25062710d8
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642593"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Microsoft Intune を使用して Windows 10 ポータル サイト アプリを手動で追加する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

デバイスを管理し、アプリをインストールするために、エンド ユーザーは Microsoft Store からポータル サイト アプリをインストールすることができます。 ただし、ビジネスでポータル サイト アプリを割り当てる必要がある場合は、Intune から直接 Windows 10 ポータル サイト アプリを手動で割り当てることができます。 Intune をビジネス向け Microsoft Store と統合していない場合でも、同様に割り当てることができます。

 > [!NOTE]
 > この記事で説明されたオプションでは、アプリの更新プログラムがリリースされるたびに、手動で更新プログラムを割り当てる必要があります。

## <a name="configure-settings-to-show-offline-apps"></a>オフライン アプリ表示するように設定を構成する
1. 自分の管理アカウントを使って[ビジネス向け Microsoft Store](https://www.microsoft.com/business-store) にサインインします。
2. ウィンドウの上部付近にある **[管理]** タブを選択します。
3. 左側のウィンドウで、**[設定]** を選択します。
4. **[Shopping experience]\(ショッピング体験\)** の **[Show offline apps]\(オフライン アプリの表示\)** を **[オン]** に設定します。  
    オフラインのライセンスされたアプリが表示されます。

## <a name="download-the-offline-company-portal-app"></a>オフラインのポータル サイト アプリをダウンロードする
1. **ポータル サイト** アプリを検索して選択します。
2. **[ライセンスの種類]** を **[オフライン]** に設定します。
3. **[アプリの取得]** を選択し、オフラインのポータル サイト アプリを取得して、インベントリに追加します。
4. **[ポータル サイト]** アプリ ページの **[管理]** を選択します。
5. **プラットフォーム**に **[Windows 10 *all devices*]\(Windows 10 の*すべてのデバイス*\)** を選択し、適切な**最小バージョン**、**アーキテクチャ**、**アプリ メタデータのダウンロード**の各値を選択します。 
6. **[ダウンロード]** を選択して、ローカル コンピューターにファイルを保存します。

    ![ダウンロードに "Windows 10 のすべてのデバイス" とアーキテクチャ X86 のパッケージ詳細が選択されています](./media/Win10CP-all-devices.png)

7. **[ダウンロード]** を選択して、[必要なフレームワーク] の下のすべてのパッケージをダウンロードします。  
    このアクションは x86、x64、ARM アーキテクチャ用に実行する必要があります (パッケージは合計で 12 個)。
8. ポータル サイト アプリを Intune にアップロードする前に、パッケージを次のように構成してフォルダー (C:\Company Portal など) を作成します。
   - C:\ポータル サイトにポータル サイト パッケージを配置します。 また、この場所に*依存関係*サブフォルダーも作成します。  

     ![APPXBUN ファイルと共に保存された依存関係フォルダー](./media/Win10CP-Dependencies-save.png)

   - *依存関係*フォルダーに依存関係パッケージを配置します。 

     > [!NOTE]
     > 依存関係が正しい形式で配置されていない場合、Intune はパッケージのアップロード時にファイルを認識してアップロードできなくなり、アップロードは失敗し、エラーが表示されます。

9. Azure Portal の Microsoft Intune で、新しいアプリとしてポータル サイト アプリをアップロードします。 
10. 選択したターゲット ユーザーのセットに対して必要なアプリとして、ポータル サイト アプリを割り当てます。  

Intune がユニバーサル アプリ用に依存関係をどのように処理するかについて詳しくは、「[Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/)」 (Microsoft Intune MDM 経由で依存関係を使用して appxbundle を展開する) をご覧ください。  

## <a name="frequently-asked-questions"></a>よく寄せられる質問 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>ユーザーがストアから古いアプリを既にインストールしている場合に、ユーザーのデバイスのポータル サイト アプリを更新する方法
ユーザーが Microsoft Store から Windows 8.1 または Windows Phone 8.1 ポータル サイト アプリを既にインストールしている場合は、お客様またはお客様のユーザーが特に操作を行わなくても、ご利用のアプリは最新バージョンに自動的に更新されます。 更新が実行されない場合は、デバイスでストア アプリの自動更新を有効にしているかどうかをユーザーに確認してください。   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>サイドロードした Windows 8.1 のポータル サイト アプリを Windows 10 のポータル サイト アプリにアップグレードする方法
推奨される移行パスとして、割り当てアクションを **[アンインストール]** に設定して、Windows 8.1 ポータル サイト アプリの割り当てを削除します。 この設定を選択したら、前述のオプションのいずれかを使用して、Windows 10 ポータル サイト アプリを割り当てることができます。  

アプリをサイドロードする必要があり、Symantec 証明書で署名せずに Windows 8.1 ポータル サイトを割り当てた場合は、この記事の前のセクションの手順を実行してアップグレードを完了します。

アプリをサイドロードする必要があり、Symantec コード署名証明書で Windows 8.1 ポータル サイト アプリに署名し割り当てた場合は、次のセクションの手順に従ってください。

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>署名およびサイドロードした Windows Phone 8.1 ポータル サイト アプリまたは Windows 8.1 ポータル サイト アプリを Windows 10 ポータル サイト アプリにアップグレードする方法
推奨される移行パスとして、割り当てアクションを **[アンインストール]** に設定して、Windows Phone 8.1 ポータル サイト アプリまたは Windows 8.1 ポータル サイト アプリの既存の割り当てを削除します。 この設定を選択したら、通常、Windows 10 ポータル サイト アプリを割り当てることができます。  

これ以外の場合は、アップグレードのパスが確実に考慮されるように、Windows 10 ポータル サイト アプリを適切に更新し、署名する必要があります。  

この方法で Windows 10 ポータル サイト アプリに署名し割り当てた場合、ストアで入手可能になった新しいアプリの更新プログラムごとにこのプロセスを繰り返す必要があります。 ストアが更新されたときに、アプリは自動的に更新されません。  

この場合のアプリへの署名および割り当て方法は、次のとおりです。

1. [Microsoft Intune Windows 10 ポータル サイト アプリの署名スクリプト](https://aka.ms/win10cpscript)をダウンロードします。  
    このスクリプトでは、Windows SDK for Windows 10 をホスト コンピューターにインストールする必要があります。 [Windows SDK for Windows 10 をダウンロードします](https://go.microsoft.com/fwlink/?LinkId=619296)。
2. 上記の説明のように、ビジネス向け Microsoft Store から Windows 10 ポータル サイト アプリをダウンロードします。  
3. Windows 10 ポータル サイト アプリに署名するには、次の表のように、スクリプト ヘッダーに記載された入力パラメーターを使用してスクリプトを実行します。  
    スクリプトに依存関係を渡す必要はありません。 依存関係は、アプリが Intune 管理コンソールにアップロードされる場合にのみ必要です。

| パラメーター |  説明  |
|---|---|
| InputWin10AppxBundle  |  ソース appxbundle ファイルへのパス |
| OutputWin10AppxBundle | 署名された appxbundle ファイルの出力パス 
| Win81Appx  | Windows 8.1 または Windows Phone 8.1 ポータル サイト (.APPX) ファイルへのパス |
| PfxFilePath  |  Symantec エンタープライズ モバイル コード署名証明書 (.PFX) ファイルへのパス  |
| PfxPassword  | Symantec エンタープライズ モバイル コード署名証明書のパスワード |
| PublisherId | エンタープライズの発行者 ID 指定しない場合、Symantec エンタープライズ モバイル コード署名証明書の Subject フィールドが使用されます。 |
| SdkPath | Windows SDK for Windows 10 のルート フォルダーへのパス この引数は省略可能で、既定値は ${env:ProgramFiles(x86)}\Windows Kits\10 です。  |

スクリプトの実行が終了したら、スクリプトにより Windows 10 ポータル サイト アプリの署名されたバージョンが出力されます。 その後、アプリの署名されたバージョンを Intune 経由で基幹業務 (LOB) アプリとして割り当てることができます。これにより、現在割り当てられているバージョンがこの新しいアプリにアップグレードされます。  

## <a name="next-steps"></a>次の手順

- [アプリをグループに割り当てる](apps-deploy.md)

