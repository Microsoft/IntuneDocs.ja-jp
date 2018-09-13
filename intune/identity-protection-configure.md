---
title: Microsoft Intune で Identity Protection の設定を構成する - Azure | Microsoft Docs
description: デバイス プロファイルを追加して、Microsoft Intune 内の Windows 10 デバイスで Windows Hello for Business を設定します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7012479023ece83ef475431c5cefe150ab2ef342
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317977"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Microsoft Intune で Identity Protection の設定を構成する

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Identity Protection プロファイルによって、Windows Hello for Business が管理対象の Windows 10 デバイスでどのようにプロビジョニングおよび構成されるかを制御します。 このプロファイルを作成して以下を構成します。  
* デバイスとユーザーに対する Windows Hello for Business の可用性
* デバイスの PIN の要件
* デバイスにサインインするためのユーザーによるジェスチャの使用可否  

 このプロファイルをユーザーとデバイス グループを選択して、またはすべてのユーザーとすべてのデバイスに割り当てることができます。 グループは Intune にチェックインするときに、Identity Protection プロファイルを受信します。    

この記事の情報を使用して、Identity Protection プロファイルを作成します。 次に、ユーザーとデバイス グループに[ご自分のプロファイルを割り当てます](device-profile-assign.md)。

この機能は、次を実行しているデバイスに適用されます。  
- Windows 10 以降
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Identity Protection の設定でデバイス プロファイルを作成する

1. [Azure ポータル](https://portal.azure.com)にサインインします。
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. **[デバイス構成]** > **[プロファイル]** > **[プロファイルの作成]** の順に選択します。
4. Identity Protection プロファイルの **[名前]** と **[説明]** を入力します。
5. **[プラットフォーム]** ドロップダウン リストで、**[Windows 10 以降]** を選択します。 Windows Hello for Business は、Windows 10 以降を実行しているデバイスのみでサポートされます。
6. **[プロファイルの種類]** ドロップダウン リストで、**[Identity Protection]** を選択します。
7. [Windows Hello for Business] ウィンドウで、[Windows Hello for Business の構成] のオプションを次から選択します。
    * 無効にします。 Windows Hello for Business を使用しない場合は、この設定を選択します。 画面上の他のすべての設定が使用できなくなります。
    * 有効にします。 Windows Hello for Business の設定を構成する場合は、この設定を選択します。  

8. 前の手順で **[有効]** を選択した場合は、対象となる登録済みの Windows 10 と Windows 10 Mobile のデバイスとユーザーに適用される必須設定を構成します。

> [!NOTE]
> Identity Protection プロファイルをユーザーのみに割り当てた場合は、デバイス コンテキストは既定で **[未構成]** になります。  

   - **[PIN の長さの最小値]**/**[PIN の長さの最大値]**。 サインインをセキュリティで保護するために指定する PIN の最小長と最大長を使用するようにデバイスを構成します。 既定の PIN の長さは 6 文字ですが、最小長を 4 文字にすることができます。 PIN の最大長は 127 文字です。  

   - **[PIN での小文字の使用を必要とする]**/**[PIN での大文字の使用を必要とする]**/**[Special characters in PIN]\(PIN での特殊文字の使用を必要とする\)**。 大文字、小文字、特殊文字を PIN で使用するように要求することで、PIN をより強力にすることができます。 次の中から選択します。

     - **[許可]**。 ユーザーは PIN で文字を使用できますが、使用は必須ではありません。

     - **[必須]**。 ユーザーは PIN に文字を 1 文字以上含める必要があります。 たとえば、一般的なのは、少なくとも 1 つの大文字と 1 つの特殊文字の使用を要求する方法です。

     - **[許可しない]** (既定)。 ユーザーは、これらの文字を PIN で使用することができません  (この動作は、設定が構成されていない場合にも発生します。)<br>特殊文字には次のものが含まれます。**! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **[PIN の有効期間 (日)]**。 その期間が経過したらユーザーが PIN を変更する必要がある有効期間を指定することをお勧めします。 既定は 41 日です。

   - **[PIN の履歴を保存]**。 以前に使用した PIN の再利用を制限します。 既定では、直近 5 回の PIN を再利用することはできません。  
   - **[Enable PIN recovery]\(PIN の回復を有効にします\)**: Windows Hello for Business の PIN の回復サービスを使用して、ユーザーが自分の PIN を変更することを許可します。 
       - **[有効]**。 クラウド サービスで、PIN の回復シークレットが暗号化され、デバイスに保存されます。 必要に応じて、ユーザーは自分の PIN を変更できます。  
       - **[未構成]** (既定)。 PIN の回復シークレットは作成または保存されません。 ユーザーの PIN を忘れてしまった場合、新しい PIN を取得するには、既存の PIN を削除して新しい PIN を作成するのが唯一の方法です。 ユーザーは、古い PIN でアクセスできた任意のサービスに再登録する必要があります。  
   
   - **[トラステッド プラットフォーム モジュール (TPM) の使用]**。 TPM チップは、追加のデータのセキュリティ層を提供します。 次のいずれかの値を選択します。  
     - **[有効]**。 アクセス可能な TPM を装備したデバイスのみが Windows Hello for Business をプロビジョニングできます。
     - **[Not configured]** (未構成)。 使用可能な TPM がない場合も、すべてのデバイスで Windows Hello for Business をプロビジョニングすることができます。 デバイスでは、まず TPM を使用しようとしますが、利用できない場合は、デバイスでソフトウェアの暗号化を使用できます。  

   - **[生体認証を許可]**。 Windows Hello for Business の PIN の代わりとして、顔認識や指紋などの生体認証を有効にします。 ユーザーは、生体認証に失敗した場合のために、Work の PIN も設定する必要があります。 次の中から選択します。

     - **[有効]**。 Windows Hello for Business で生体認証が使用可能になります。
     - **[未構成]** (既定)。 Windows Hello for Business で生体認証を利用できません (すべてのアカウントの種類が対象)。

   - **[拡張スプーフィング対策が使用可能な場合は使用する]**。 Windows Hello のスプーフィング対策機能 (例: 実際の顔の代わりに写真の顔を検出する) をサポートしているデバイスで、その機能を使用するかどうかを構成します。
       - **[有効]**。 Windows のすべてのユーザーは、サポートされている場合に顔の特徴のスプーフィング対策を使用する必要があります。  
       - **[未構成]** (既定)。 Windows では、デバイス上のスプーフィング対策の構成を優先します。

   - **[Certificate for on-premise resources]\(オンプレミスのリソースの証明書\)**。 
       - **[有効]**。 オンプレミスのリソースを認証するために、Windows Hello for Business で証明書を使用することを許可します。
       - **[未構成]** (既定)。 オンプレミスのリソースを認証するために、Windows Hello for Business で証明書を使用できないようにします。  
9. **[OK]** をクリックし、プロファイルを保存します。  

プロファイルが作成され、**[デバイス構成 - プロファイル]** リストに表示されます。 先に進んでこのプロファイルをグループに割り当てるには、「[Microsoft Intune でユーザーおよびデバイス プロファイルを割り当てる](device-profile-assign.md)」を参照してください。  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
