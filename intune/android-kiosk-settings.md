---
title: Microsoft Intune - Azure での Android 用のキオスクの設定 | Microsoft Docs
description: Android キオスク デバイスをシングル アプリ キオスクおよびマルチ アプリ キオスクとして構成します。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cef98527ee2c281547f8046f3c6f08275d8f0807
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329385"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Intune での Android デバイス向けのキオスク設定

デバイス構成設定を利用し、デバイスをシングルまたはマルチ アプリ キオスク モードに構成できます。 デバイスがキオスク モードのとき、制限プロファイルで定義されているアプリまたは Web リンク以外はデバイスで使用できなくなります。 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Android キオスク デバイスで使えるアプリを 1 つに限定する

キオスク デバイスの制限プロファイルが**キオスク モード** = **シングル アプリ キオスク**に設定されている場合、ユーザーはアクセスできるアプリが 1 つだけになります。 このモードで構成されているデバイスを起動すると、その特定のアプリが起動します。 ユーザーは新しいアプリを開いたり、実行中のアプリを変更したりできません。

1. キオスク デバイスで使用するアプリが[デバイスに展開されている](apps-deploy.md)こと、キオスク デバイスに対して作成したデバイス グループにアプリを割り当てていることを確認してください。
2. [Intune ポータル](https://portal.azure.com)に進み、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. **[プロファイルの作成]** ブレードで、次のフィールドを設定します。
     - **名前**
     - **[プラットフォーム]**: Android エンタープライズ
     - **[プロファイルの種類]**: [Device Owner Only]\(デバイスの所有者のみ\)、[デバイスの制限]
4. **[設定]** > **[キオスク]** の順に選択します。
5. **[キオスク モード]** に **[シングル アプリ キオスク]** を選択します。
6. **[管理対象アプリを選択します]** を選択し、このプロファイルを使用してデバイスで唯一利用できるアプリにする managed Google Play アプリを選択します。
7. **[OK]** > **[OK]** > **[OK]** > **[作成]** の順に選択します。
8. 先ほど作成したプロファイルを選択し、**[割り当て]** を選択します。
9. **[割り当て先]** の下で **[選択したグループ]** を選択します。
10. **[含めるグループを選択]** を選択し、キオスク デバイスに作成したデバイス グループを選択し、**[選択]** を選択します。

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>キオスク デバイスで使用できるアプリまたは Web リンクを制限する

キオスク デバイスの制限プロファイルが**キオスク モード** = **マルチ アプリキオスク**に設定されている場合、限られた数のアプリにのみユーザーはアクセスできます。 ユーザーにアクセスを許可する一連の Web リンクを定義することもできます。 ポリシーが適用されると、ユーザーのホーム画面に許可されたアプリのアイコンが表示されます。

Android キオスク デバイスに複数のアプリを設定するには、次の主な手順を実行します。

1. [managed Google Play から Managed Home Screen アプリをインポートし、展開する](#import-and -deploy-the-managed-home-screen-app)
2. [キオスク モードで使用できるアプリを追加し、割り当てる](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (任意) [キオスク モードで使用できる Web リンクを追加する](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deply-the-managed-home-screen-app"></a>Managed Home Screen アプリをインポートし、展開する

1. [Google Play の Managed Home Screen ページ](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise)に移動し、他の managed Google Play アプリで使用したものと同じアカウントでサインインします。
2. **[承認]** を選択します。
3. [Intune ポータル](https://portal.azure.com)に移動し、**[クライアント アプリ]** > **[Managed Google Play]** > **[同期]** の順に選択します。
4. **[アプリ]** > **[Managed Home Screen]** > **[割り当て]** > **[グループの追加]** の順に選択します。
5. **[割り当ての種類]** の下で **[必須]** を選択します。
6. **[含まれているグループ]**、**[含めるグループを選択]** の順に選択し、キオスク デバイスに作成したデバイス グループを選択し、**[選択]** > **[OK]** > **[OK]** > **[保存]** の順に選択します。

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>キオスク モードで使用できるアプリを追加し、割り当てる

キオスク デバイスで利用できるようにするアプリごとに、以下の手順を行います。

1. [Intune にアプリを追加します](store-apps-android.md)。
2. **[クライアント アプリ]** > **[アプリ]** の順に選択し、アプリを選択して **[割り当て]** > **[グループの追加]** の順に選択します。
3. **[割り当ての種類]** の下で **[必須]** を選択します。
4. **[含まれているグループ]**、**[含めるグループを選択]** の順に選択し、キオスク デバイスに作成したデバイス グループを選択し、**[選択]** > **[OK]** > **[OK]** > **[保存]** の順に選択します。

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>キオスク モードで使用できる Web リンクを追加する

1. [Intune ポータル](https://portal.azure.com)に移動し、**[クライアント アプリ]** > **[アプリ]** > **[追加]** の順に選択します。
2. **[アプリの種類]** の下で **[Web リンク]** を選択します。
3. **[構成]** を選択し、必要な情報を入力します。 ロゴ画像を追加する必要はありません。ロゴ画像は、Web サイトの favicon.ico から自動的に取得されます。
4. **[OK]** > **[追加]** の順に選択します。

[Mobile Apps](apps-add.md) を使用してキオスク デバイスに Web ブラウザー アプリを展開したことを確認してください。

### <a name="create-a-multi-app-kiosk-profile"></a>マルチ アプリ キオスク プロファイルを作成する

1. [Intune ポータル](https://portal.azure.com)に進み、**[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
3. **[プロファイルの作成]** ブレードで、次のフィールドを設定します。
     - **[名前]**: わかりやすい名前を入力します
     - **[プラットフォーム]**: Android エンタープライズ
     - **[プロファイルの種類]**: [Device Owner Only]\(デバイスの所有者のみ\)、[デバイスの制限]
4. **[設定]** > **[キオスク]** の順に選択します。
5. **[キオスク モード]** に **[マルチ アプリ キオスク]** を選択します。
6. **[追加]** を選択し、このプロファイルを使用してデバイスで利用可能にするアプリまたは Web リンクを選択します。
7. **[OK]** > **[OK]** > **[OK]** > **[作成]** の順に選択します。
8. 先ほど作成したプロファイルを選択し、**[割り当て]** を選択します。
9. **[割り当て先]** の下で **[選択したグループ]** を選択します。
10. **[含めるグループを選択]** を選択し、キオスク デバイスに作成したデバイス グループを選択し、**[選択]** > **[保存]** の順に選択します。

## <a name="next-steps"></a>次の手順
[プロファイルを割り当て](device-profile-assign.md)、[その状態を監視](device-profile-monitor.md)します。
