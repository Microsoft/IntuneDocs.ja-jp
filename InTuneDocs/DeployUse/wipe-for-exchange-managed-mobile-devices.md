---
# required metadata

title: Exchange で管理されているモバイル デバイスのワイプ | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Wipe for [Exchange]-managed mobile devices
Microsoft Intune では、Exchange ActiveSync (EAS) と Intune Exchange Connector を使って管理されているモバイル デバイスをワイプまたはリセットすることができます。 次の表に、Exchange ActiveSync で利用できるインベントリからの削除/ワイプを示します。

|ワイプの種類|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|完全なワイプ|メール アカウントとキャッシュ済みメールを削除します|メール アカウントとキャッシュ済みメールを削除します|出荷時の設定に戻す|出荷時の設定に戻す|出荷時の設定に戻す|
|選択的なワイプ/電子メール|電子メール アカウントを削除します|電子メール アカウントを削除します|サポートされていません|サポートされていません|サポートされていません|
|選択的なワイプ/ポリシー|ポリシーの強制は削除されますが、設定は変更されません|ポリシーの強制は削除されますが、設定は変更されません|ポリシーの強制は削除されますが、設定は変更されません|ポリシーの強制は削除されますが、設定は変更されません|ポリシーの強制は削除されますが、設定は変更されません|


<!--HONumber=May16_HO1-->


