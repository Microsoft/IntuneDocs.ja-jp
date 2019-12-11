---
title: Android デバイスが暗号化されているように見える | Microsoft Docs
description: ポータルサイトと Microsoft Intune アプリの暗号化状態を解決する
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: af1c7d1f9d8236fd95413317acefbe8887d90f47
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "72507672"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>デバイスは暗号化されますが、それ以外の場合は

ポータルサイトまたは Microsoft Intune アプリでデバイスが暗号化されていないということがわかっている場合は、この記事の手順を試してください。  

## <a name="add-a-startup-pin"></a>スタートアップ PIN の追加

いくつかの Android デバイスでは、デバイスがセキュリティ保護されていることを確認するためにスタートアップ PIN を作成する必要があります。 この設定の場所は、デバイスの**設定**アプリにあります。 設定の名前と場所が異なる場合があります。 たとえば、Samsung Galaxy S7 では、この設定は "**安全な起動**" と呼ばれます。 これを有効にしてパスコードを作成するには、 **[設定]**  > [**ロック画面とセキュリティ** > のセキュリティ**で保護された起動**] にアクセスします。  

## <a name="encrypt-the-entire-device"></a>デバイス全体を暗号化します

このセクションは、ポータルサイトアプリにのみ適用されます。 一部のデバイスでは、デバイス全体と使用済み領域のみのどちらを暗号化するかを選ぶことができます。 デバイス全体を暗号化するオプションを選択します。 使用済みの領域のみを暗号化するように選択した場合は、次のようにします。

1. [ポータル サイトからこのデバイスを削除します](unenroll-your-device-from-intune-android.md)。
2. 使用済み領域の暗号化を解除します。  
3. デバイス全体を暗号化します。  
4. デバイスを再度登録します。  

## <a name="downgrade-your-version-of-android"></a>Android のバージョンのダウングレード

このセクションは、ポータルサイトアプリにのみ適用されます。 デバイスで Android 6.0 以降にダウングレードできる場合は、ダウングレードします。 デバイスのダウングレードには、データ損失のリスクが伴います。 そのため、会社のサポートに問い合わせて、この問題を解決することをお勧めします。 [ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)から、ご自身の会社のサポートに関する連絡先情報を取得してください。  

## <a name="specific-manufacturer-issues"></a>特定の製造元の問題

バージョン 7.0 以上の一部の Android デバイスでは、特定の Android プラットフォームの標準に準拠していない方法でデータが暗号化されます。 これらの暗号化方法では、デバイス情報が危険にさらされます。 そのため、これらのデバイスはサポートされていません。

サポートされている Android デバイスの完全でない一覧については、「 [Intune でサポートされるオペレーティングシステムとブラウザー](https://docs.microsoft.com/intune/fundamentals/supported-devices-browsers#supported-samsung-knox-standard-devices)」を参照してください。 デバイスが一覧に表示されない場合は、デバイスの製造元を参照するか、サポート担当者に問い合わせてください。

> [!Note]
> Microsoft では、製造元と協力して、テスト中に見つかった問題やユーザーから報告された問題に対処しています。 新しい情報が得られたらこの記事の内容を更新します。

## <a name="update-devices"></a>デバイスの更新

デバイスを最新バージョンの Android に更新していない場合は、デバイスの**設定**アプリにアクセスし、 **[更新]** を選択します。  

## <a name="next-steps"></a>次の手順

サポートが必要な場合は、 会社のサポートに問い合わせるか (連絡先情報については[ポータル Web サイト](https://go.microsoft.com/fwlink/?linkid=2010980)をご確認ください)、または <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android チーム</a>にご連絡ください。  
