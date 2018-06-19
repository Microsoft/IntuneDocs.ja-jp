---
title: Microsoft Intune で Android デバイス向けのカスタム設定を追加する - Azure | Microsoft Docs
description: 事前共有キーを使った WiFi プロファイルの作成、アプリごとの VPN プロファイルの作成、Samsung Knox Standard デバイスのアプリの許可/拒否などを Microsoft Intune で行うには、Android デバイス用のカスタム プロファイルを追加または作成します
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0195e138b59fae019fa2bc02aadf211257a65cac
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022052"
---
# <a name="custom-settings-for-android-devices---intune"></a>Android デバイス向けのカスタム設定 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

カスタム プロファイルでは、Open Mobile Alliance Uniform Resource Identifier (OMA-URI) 設定を使って、Android デバイスのさまざまな機能を構成します。 通常、これらの設定は、デバイスの機能を制御するためにモバイル デバイスの製造元によって使われます。

カスタム プロファイルを使うと、以下の Android 設定を構成して割り当てることができます。 これらの設定は、Intune ポリシーには組み込まれていません。

- [事前共有キーを使用した Wi-Fi プロファイルの作成](/intune/wi-fi-profile-shared-key)
- [アプリごとの VPN プロファイルを作成する](/intune/android-pulse-secure-per-app-vpn)
- [Samsung Knox Standard デバイス用のアプリを許可またはブロックする](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> このプロファイルの種類では、上に挙げた設定のみを構成できます。 Android デバイスでは、構成できる OMA-URI 設定の完全な一覧が表示されません。 他の設定が表示されるようにしたい場合は、[Intune Uservoice サイト](https://microsoftintune.uservoice.com/forums/291681-ideas)で他の設定に投票してください。

## <a name="custom-profile-settings-for-android-devices"></a>Android デバイス向けのカスタム プロファイル設定

1. [Azure ポータル](https://portal.azure.com)にサインインします。 
2. **[すべてのサービス]** を選択し、**[Intune]** をフィルターとして適用し、**[Microsoft Intune]** を選択します。
3. Android プラットフォームを使ってカスタム プロファイルを作成します。 手順については、[Microsoft Intune でカスタム デバイス設定を構成する方法](custom-settings-configure.md)に関するページをご覧ください。
4. **[OMA-URI のカスタム設定]** で **[追加]** を選択し、**[行の追加]** を選択します。
5. 次のプロパティを入力します。

   - **[名前]** - 簡単に見つけられるように、OMA-URI 設定の一意の名前を入力します。
   - **[説明]** - 設定の概要および他の重要な詳細がわかる説明を入力します。
   - **[データ型]** - この OMA-URI 設定に使うデータ型を入力します。 **[文字列]**、**[文字列 (XML)]**、**[日付と時刻]**、**[整数]**、**[浮動小数点]**、または **[ブール値]** から選択します。
   - **[OMA-URI]** - 必要な OMA-URI を入力します。
   - **[値]** - 入力した OMA-URI に関連付ける値を入力します。

6. **[OK]** を選択して変更を保存します。 必要に応じて他の設定の追加を続けます。

## <a name="next-steps"></a>次の手順

設定が完了すると、プロファイルが作成されて、一覧に表示されます。 このプロファイルをグループに割り当てるには、[デバイス プロファイルを割り当てる方法](device-profile-assign.md)に関する記事を参照してください。
