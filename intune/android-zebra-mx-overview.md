---
title: Microsoft Intune で Android デバイス上の Zebra モビリティ拡張機能を使用する - Azure | Microsoft Docs
description: Microsoft Intune を使用して、Android と一緒に Zebra モビリティ拡張機能 (MX) が稼働している Zebra デバイスを管理および使用します。 ポータル サイト アプリのインストール、アプリのサイドロード、デバイス管理者ロールの割り当て、StageNow プロファイルの作成など、すべての手順を参照してください。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69814b91978aa3cd74c4dc239b099883ae402af9
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764776"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Microsoft Intune で Zebra モビリティ拡張機能を備えた Zebra デバイスを使用および管理する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune には、アプリの管理やデバイス設定の構成など、豊富な機能が含まれています。 これらの組み込みの機能と設定は、Zebra Technologies 社によって製造された Android デバイス ("Zebra デバイス" とも呼ばれる) を管理するのに使用されます。

Android デバイスでは、**モビリティ拡張機能 (MX)** プロファイルを使用して、Zebra 固有の設定をカスタマイズしたり、さらにそれらの設定を追加したりします。

この記事では、Microsoft Intune で Zebra デバイス上の Zebra モビリティ拡張機能 (MX) を使用する方法について説明します。

この機能は、以下に適用されます。

- Android

あなたの会社では、小売や工場の現場などで Zebra デバイスを使用しているかもしれません。 たとえば、あなたの会社は小売業者であり、その環境には販売員が使用する何千台もの Zebra モバイル機器があるとします。 Intune は、ご利用のモバイル デバイス管理 (MDM) ソリューションの一部として、これらのデバイスを管理するのに役立ちます。

Intune を使用すると、Zebra デバイスを登録して、ご利用の基幹業務アプリをデバイスに展開することができます。 "デバイス構成" プロファイルでは、Zebra 固有の設定を管理する MX プロファイルを作成できます。

## <a name="before-you-begin"></a>始める前に

- Zebra Technologies 社から提供されている最新バージョンの StageNow デスクトップ アプリを必ずご用意ください。
- [Zebra の完全な MX 機能マトリックス](http://techdocs.zebra.com/mx/compatibility) (Zebra の Web サイトが開かれる) を調べて、作成するプロファイルがデバイスの MX バージョン、OS バージョン、およびモデルと互換性があることを必ず確認してください。
- TC20/25 デバイスなどの特定のデバイスでは、StageNow で提供されている MX 機能がすべてサポートされているわけではありません。 [Zebra の機能マトリックス](http://techdocs.zebra.com/mx/tc2x/) (Zebra の Web サイトが開きます) を調べて、最新のサポート情報を必ず確認してください。

## <a name="step-1-install-the-latest-company-portal-app"></a>ステップ 1: 最新のポータル サイト アプリをインストールする

デバイス上で Google Play ストアに移動し、Microsoft からの Intune ポータル サイト アプリをダウンロードしてインストールします。 Google Play からポータル サイト アプリをインストールすると、このアプリでは更新プログラムと修正プログラムが自動的に取得されます。

Google Play が利用できない場合は、[Android 用 Microsoft Intune ポータル サイト](https://www.microsoft.com/download/details.aspx?id=49140) (別の Microsoft Web サイトが開きます) をダウンロードし、(この記事内の説明に従って) [それをサイドロードします](#sideload-the-company-portal-app)。 この方法でインストールした場合、アプリに更新プログラムまたは修正プログラムは自動的に提供されません。 通常は、定期的に手動でアプリに更新プログラムおよび修正プログラムを適用する必要があります。

### <a name="sideload-the-company-portal-app"></a>ポータル サイト アプリをサイドロードする

"サイドロード" するのは、アプリのインストールに Google Play を使用しない場合です。 ポータル サイト アプリをサイドロードするには、StageNow を使用します。 

次の手順で概要を示します。 特定の詳細については、Zebra のドキュメントを参照してください。 [StageNow を使用して MDM に登録する](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (Zebra の Web サイトが開きます) を参照することをお勧めします。

1. StageNow で、 **[Enroll in an MDM]\(MDM に登録する\)** 用のプロファイルを作成します。
2. **[Deployment]\(展開\)** で、MDM エージェント ファイルのダウンロードを選択します。
3. **[Support App]\(アプリをサポート\)** および **[Download Configuration]\(構成をダウンロード\)** 手順を **[No]\(いいえ\)** に設定します。
4. **[Download MDM]\(MDM をダウンロード\)** で、 **[Transfer/Copy File]\(ファイルの転送/コピー\)** を選択します。 Android ポータル サイト パッケージ (APK) の送信元と送信先を追加します。
5. **[Launch MDM]\(MDM の起動\)** では、既定値をそのままにします。 次の詳細を追加します。

    - **[パッケージ名]** : `com.microsoft.windowsintune.companyportal`
    - **[クラス名]** : `com.microsoft.windowsintune.companyportal.views.SplashActivity`

引き続きプロファイルを公開し、デバイス上でそれを StageNow アプリと一緒に使用します。 ポータル サイト アプリがデバイスにインストールされ、開かれます。

> [!TIP]
> StageNow とその機能の詳細については、「[StageNow Android デバイスのステージング](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html)」 (Zebra の Web サイトが開きます) を参照してください。

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>手順 2: ポータル サイト アプリにデバイス管理者の役割があることを確認する

ポータル サイト アプリでは、Android デバイスを管理するデバイス管理者が必要です。 デバイス管理者の役割を有効にするために、一部の Zebra デバイスは、デバイス用のユーザー インターフェイス (UI) を備えています。 デバイスが UI を備えている場合、(この記事内で説明する) [登録](#step-3-enroll-the-device-in-to-intune)時にデバイス管理者を許可するように求めるメッセージがポータル サイト アプリからエンドユーザーに表示されます。

UI が利用できない場合は、StageNow の **DevAdmin Manager** を使用して、デバイス管理者をポータル サイト アプリに手動で付与するプロファイルを作成します。

次の手順で概要を示します。 特定の詳細については、Zebra のドキュメントを参照してください。 
[デバイス管理者としてバッテリ スワップ モードを設定](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (Zebra の Web サイトが開きます) に関するページを参照することをお勧めします。

1. StageNow で、プロファイルを作成し、 **[Xpert Mode]\(Xpert モード\)** を選択します。
2. プロファイルに **[DevAdmin Manager]** を追加します。
3. **[Device Administration Action]\(デバイス管理アクション\)** を **[Turn On as Device Administrator]\(デバイス管理者としてオンにする\)** に設定します。
4. **[Device Admin Package Name]\(デバイス管理パッケージ名\)** を `com.microsoft.windowsintune.companyportal` に設定します。
5. **[Device Admin Class Name]\(デバイス管理クラス名\)** を `com.microsoft.omadm.client.PolicyManagerReceiver` に設定します。

引き続きプロファイルを公開し、デバイス上でそれを StageNow アプリと一緒に使用します。 ポータル サイト アプリにデバイス管理者の役割が付与されます。

## <a name="step-3-enroll-the-device-in-to-intune"></a>手順 3: Intune にデバイスを登録する

最初の 2 つの手順が完了したら、ポータル サイト アプリがデバイスにインストールされます。 Intune にデバイスを登録する準備が整いました。

「[Android デバイスの登録](android-enroll.md)」に手順が説明されています。 Zebra デバイスが多数ある場合は、[デバイス登録マネージャー (DEM) アカウント](device-enrollment-manager-enroll.md)の使用をお勧めします。 DEM アカウントを使用すると、ポータル サイト アプリから登録解除するオプションも削除されるため、ユーザーはデバイスを簡単に登録解除できなくなります。

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>手順 4: StageNow でデバイス管理プロファイルを作成する

StageNow を使用して、デバイス上で管理したい設定を構成するプロファイルを作成します。 特定の詳細については、Zebra のドキュメントを参照してください。 「[Profiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/)」 (プロファイル) (Zebra の Web サイトが開きます) を参照することをお勧めします。

StageNow でプロファイルを作成するときの最後の手順で、 **[Export to MDM]\(MDM へのエクスポート\)** を選択します。 これにより XML ファイルが生成されます。 このファイルを保存します。 後の手順で必要になります。

> [!TIP]
> 組織内のデバイスに展開する前に、プロファイルをテストすることをお勧めします。 テストするには、ご利用のコンピューター上で StageNow を使用してプロファイルを作成するときの最後の手順で、 **[Test]\(テスト\)** オプションを使用します。 次に、StageNow で生成されたファイルをデバイス上の StageNow アプリで使用します。 
> 
> デバイス上の StageNow アプリによって、プロファイルをテストしたときに生成されたログが表示されます。 [Android が稼働している Zebra デバイスに対する StageNow ログを Intune で使用](android-zebra-mx-logs-troubleshoot.md)に関するページに、StageNow ログを使用してエラーを理解するための情報があります。

> [!NOTE]
> StageNow プロファイル内のアプリを参照したり、パッケージを更新したり、他のファイルを更新したりする場合は、デバイスによってこれらの更新プログラムを取得します。 更新プログラムを取得するには、プロファイルの適用時にデバイスが StageNow 展開サーバーに接続されている必要があります。 
> 
> あるいは、これらの変更情報を、Intune の次のような組み込み機能を使用して取得します。 
> - アプリを[追加](apps-add.md)、[展開](apps-deploy.md)、更新、および[監視](apps-monitor.md)するためのアプリ管理機能。
> - Android エンタープライズが稼働しているデバイス上で[システムおよびアプリの更新プログラム](device-restrictions-android-for-work.md#device-owner-only)を管理する

ファイルをテストしたら、次のステップとして、Intune を使用してプロファイルをデバイスに展開します。

> [!NOTE]
> 各デバイスにプロファイルを 1 つ展開します。 デバイスに展開する StageNow プロファイルが複数ある場合は、それらの StageNow プロファイルをエクスポートし、設定を 1 つの XML ファイルにまとめてから Intune に追加します。 
> 
> 同じ XML ファイル内に同じプロパティを構成する設定が 2 つ必要だと思う人はいません。 この目的は、デバイス上で設定間の競合を防ぐことにあります。

## <a name="step-5-create-a-profile-in-intune"></a>手順 5: Intune でプロファイルを作成する

Intune で、デバイス構成プロファイルを作成します。

1. [Azure portal](https://portal.azure.com) で、 **[すべてのサービス]** を選択し、**Intune** でフィルター処理して、 **[Intune]** を選択します。
2. **[デバイス構成]**  >  **[プロファイル]**  >  **[プロファイルの作成]** の順に選択します。
3. 次のプロパティを入力します。

    - **名前**: 新しいプロファイルのわかりやすい名前を入力します。
    - **説明**: プロファイルの説明を入力します この設定は省略可能ですが、推奨されます。
    - **[プラットフォーム]** : **[Android]** を選択します。
    - **[プロファイルの種類]** : **[MX profile (Zebra only)]\(MX プロファイル (Zebra のみ)\)** を選択します。

4. **.xml 形式の MX プロファイル**に、(この記事の説明に従って) [StageNow からエクスポート](#step-4-create-a-device-management-profile-in-stagenow)した XML プロファイル ファイルを追加します。
5. **[OK]**  >  **[作成]** を選択して変更を保存します。 ポリシーが作成され、一覧に表示されます。

プロファイルは作成されましたが、まだ何も行われていません。 次に、[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。

次回デバイスによって構成の更新の有無が確認されたとき、MX プロファイルがデバイスに展開されます。 デバイスは登録時に Intune と同期し、その後は約 8 時間ごとに同期します。 [Intune で強制的に同期させる](device-sync.md)こともできます。 または、デバイス上で **[ポータル サイト アプリ]**  >  **[設定]**  >  **[同期]** の順に開きます。 

> [!TIP]
> - セキュリティ上の理由から、プロファイルの XML テキストは、保存すると、表示されなくなります。 テキストは暗号化され、アスタリスク (`****`) しか表示されません。 参考用に、MX プロファイルを Intune に追加する前にそのコピーを保存しておくことをお勧めします。
> 
> - Zebra デバイスに割り当てられた後にプロファイルを更新するには、更新された StageNow XML ファイルを作成し、既存の Intune プロファイルを編集して、新しい StageNow XML ファイルを追加します。 この新しいファイルによって、プロファイル内の前の StageNow ポリシーは上書きされます。

## <a name="next-steps"></a>次の手順

- [プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
- [StageNow ログを使用して Zebra デバイスのトラブルシューティングを行う](android-zebra-mx-logs-troubleshoot.md)します。
