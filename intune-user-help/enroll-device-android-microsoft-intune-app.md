---
title: Microsoft Intune アプリで会社のデバイスを登録する | Microsoft Docs
description: Intune で会社の Android デバイスを登録する方法について説明します
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/07/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef7ec650c65206eeab69d8f666dc4fb39052bbdb
ms.sourcegitcommit: 549352bdea93cc2809e3e0010bfcc10bd44dc728
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68862183"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Microsoft Intune アプリで会社のデバイスを登録する

会社が所有する Android デバイスを登録し、組織で使用可能な会社のメール、アプリ、その他のデータに安全にアクセスします。 Microsoft Intune アプリでは、Android 6.0 以降が実行されている会社所有のデバイスがサポートされます。 登録中に、新しいデバイスおよび工場出荷時の状態にリセットされたデバイスに、自動的にインストールされます。 

登録には、次の 4 つの方法があります。 どのオプションを使用するかは、組織から指示があるはずです。
 
* 近距離無線通信 (NFC)  
* トークン  
* QR コード   
* Google Zero Touch  

## <a name="enroll-device"></a>デバイスを登録する 
デバイスをセットアップして登録するには、次の手順のようにします。  

> [!NOTE]
> Android のバージョンまたはデバイスの製造元によっては、この手順には含まれない追加の手順の実施が必要となる場合があります。 また、スクリーンショットで示されている色とテキストは、お使いのデバイスの表示と異なる可能性があります。  

1. 新しいデバイスまたは出荷時の設定に戻したデバイスの電源を入れます。  
2. **[ようこそ]** 画面で、言語を選択します。   QR コードまたは NFC で登録するように指示されている場合は、方法に一致する以下の手順に従います。  
     * NFC: お使いの NFC 対応デバイスをプログラマー デバイスに対してタップし、組織のネットワークに接続します。 画面の指示に従います。 Chrome のサービス利用規約の画面が表示されたら、ステップ 5 に進みます。  

     * QR コード: 「[QR コードでの登録](#qr-code-enrollment)」の手順を完了します。  

     別の方法を使用するように指示されている場合は、ステップ 3 に進みます。    

3. Wi-Fi に接続し、 **[次へ]** をタップします。 登録方法と一致する手順に従います。 

    * トークン: Google のサインイン画面が表示されたら、「[トークンでの登録](#token-enrollment)」の手順を完了します。  
    * Google Zero Touch: Wi-Fi に接続すると、組織によってデバイスが認識されます。 ステップ 4 に進み、画面の指示に従ってセットアップを完了します。    
 
       ![Google Zero Touch を使用した場合に表示される Google 契約条件画面の例の画像。[Accept & Continue]\(同意して続行\) ボタンが強調表示されている。](./media/google-zero-touch-intune-app-01.png)   
   
4. Google の契約条件を確認します。 次に、 **[ACCEPT & CONTINUE]\(同意して続行\)** をタップします。  

      ![Google 契約条件画面の例の画像。[Accept & Continue]\(同意して続行\) ボタンが強調表示されている。](./media/fully-managed-intune-app-04.png)   

6. Chrome のサービス利用規約を確認します。 次に、 **[ACCEPT & CONTINUE]\(同意して続行\)** をタップします。  

   ![Chrome サービス利用規約画面の例の画像。[Accept & Continue]\(同意して続行\) ボタンが強調表示されている。](./media/fully-managed-intune-app-06.png)   

7. サインイン画面で、職場または学校アカウントを使用してサインインします。   

    」を参照します。 メール アドレスを入力し、 **[次へ]** をタップします。      
    b. パスワードを入力し、 **[サインイン]** をタップします。  

8. 組織の要件によっては、画面のロックや暗号化などの設定の更新を求められる場合があります。 これらのプロンプトが表示された場合は、 **[設定]** をタップして、画面の指示に従います。  

   ![職場の携帯電話の設定画面の例の画像。[設定] ボタンが強調表示されている。](./media/fully-managed-intune-app-10.png)   

9. 仕事用アプリをデバイスにインストールするには、 **[インストール]** をタップします。 インストールが完了したら、 **[次へ]** をタップします。  

   ![職場の携帯電話の設定画面の例の画像。[インストール] ボタンが強調表示されている。](./media/fully-managed-intune-app-11.png)   

10. **[スタート]** をタップして Microsoft Intune アプリを開き、デバイスを登録します。 

    ![[スタート] ボタンが強調表示されている職場の携帯電話の設定画面の例の画像。](./media/fully-managed-intune-app-17.png)   

11. [**サインイン **] をタップし、[** 次へ**] をタップして登録を開始します。 [登録が完了しました] というメッセージ**が**表示されたら、[完了] をタップします。  

    ![[アクセスの設定]、[デバイスの登録] 画面、[完了] ボタンの強調表示の画像の例。](./media/fully-managed-intune-app-19.png)   

10. デバイスの準備ができたことを示すメッセージが表示されたら、 **[完了]** をタップします。  

    ![[完了] ボタンが強調表示されている職場の携帯電話の設定画面の例の画像。](./media/fully-managed-intune-app-18.png)   

組織のリソースにアクセスできない場合は、デバイスの追加設定を更新することが必要になる場合があります。 Microsoft Intune アプリにサインインして、必要な更新プログラムがないかどうかを確認します。   


## <a name="qr-code-enrollment"></a>QR コードでの登録  
このセクションでは、会社から提供された QR コードをスキャンします。  完了すると、デバイス登録手順に戻ります。     
  
1. **[ようこそ]** 画面で、画面を 5 回タップして QR コードのセットアップを起動します。  

   ![デバイス セットアップの [ようこそ] 画面の例の画像。画面タップ指示が強調表示されている。](./media/qr-code-intune-app-01.png)  

2. 画面の指示に従って Wi-Fi に接続します。  
3. お使いのデバイスに QR コード スキャナーがない場合、セットアップ画面にスキャナーのインストールの進行状況が表示されます。 インストールが完了するまで待ちます。  
4. メッセージが表示されたら、組織から提供されている登録プロファイル QR コードをスキャンします。  
5. ステップ 4 の「[デバイスを登録する](#enroll-device)」に戻り、セットアップを続けます。  

## <a name="token-enrollment"></a>トークンでの登録  
このセクションでは、会社から提供されたトークンを入力します。 完了すると、デバイス登録手順に戻ります。  

1. Google サインイン画面の **[メールまたは電話]** ボックスに、「**afw#setup**」と入力します。 **[次へ]** をタップします。 

   ![Google サインイン画面の例の画像。"afw#setup" がフィールドに入力されている。](./media/token-intune-app-01.png)   

2. **[Android Device Policy]\(Android デバイス ポリシー\)** アプリの **[インストール]** を選択します。 インストールを続けます。 お使いのデバイスによっては、追加の条件を確認して同意する必要があります。    

3. **[このデバイスの登録]** 画面で、 **[次へ]** を選択します。  

4. **[コードの入力]** を選択します。  

5. **[Scan or enter code]\(コードのスキャンまたは入力\)** 画面で、組織から提供されたコードを入力します。  **[次へ]** をクリックします。  

   ![[Scan or enter code]\(コードのスキャンまたは入力\) 画面の例の画像。強調表示された [次へ] ボタン。](./media/token-intune-app-04.png)  

6. ステップ 4 の「[デバイスを登録する](#enroll-device)」に戻り、セットアップを続けます。  



## <a name="next-steps"></a>次の手順   
サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。  
