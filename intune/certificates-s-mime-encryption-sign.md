---
title: S/MIME メールの署名と暗号化 - Azure | Microsoft Docs
description: Microsoft Intune で S/MIME を使用または有効にして、電子メールの署名または暗号化を行います
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eaa85870b289bb3b65ce997d8610324f43d69452
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185646"
---
# <a name="smime-email-signing-and-encryption-in-intune"></a>Intune での S/MIME メールの署名と暗号化

> [!IMPORTANT]
> この記事で説明する S/MIME 機能を改善しています。 そのため、S/MIME 機能は一時的に Intune から除去されています。 この機能がリリースされたときに、この記述を削除します。

S/MIME は、暗号化と解読を使用することにより、メール通信のセキュリティを強化します。 Microsoft Intune は、S/MIME を使用して、iOS、Windows、Windows Phone、Android、macOS を実行しているモバイル デバイスに送信される電子メールの署名および暗号化を行うことができます。

iOS デバイスでは、S/MIME と証明書を使用して送受信されるメールの署名と暗号化を行う、Intune で管理されたメール プロファイルを作成できます。 他のプラットフォームでは、S/MIME はサポートされている場合とサポートされていない場合があります。 サポートされている場合は、S/MIME の署名と暗号化を使用する証明書をインストールできます。 その後、エンド ユーザーは電子メール アプリケーションで S/MIME を有効にできます。

S/MIME メールの署名と暗号化について詳しくは、「[S/MIME for message signing and encryption](https://docs.microsoft.com/Exchange/policy-and-compliance/smime)」(S/MIME によるメッセージの署名と暗号化) をご覧ください。

## <a name="signing-certificates"></a>署名証明書

署名に使われる証明書を使用することで、クライアントのメール アプリはメール サーバーと安全に通信できます。

署名証明書を使うには、証明機関で署名用のテンプレートを作成します。 Microsoft Active Directory 証明機関の場合は、「[Configure the server certificate template](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template)」(サーバー証明書テンプレートを構成する) で証明書テンプレートの作成手順が示されています。

Intune での署名証明書は、PKCS 証明書を使います。 「[Intune で PKCS 証明書を構成して使用する](certficates-pfx-configure.md)」では、Intune 環境に PKCS 証明書を展開して使う方法が説明されています。 次のステップが含まれます。

- PKCS 証明書の要求をサポートするための Microsoft Intune Certificate Connector をダウンロードしてインストールします。
- お使いのデバイス用の信頼されたルート証明書プロファイルを作成します。 このステップには、お使いの証明機関に対する信頼されたルート証明書と中間証明書の使用と、デバイスへのプロファイルの展開が含まれます。
- 作成した証明書テンプレートを使って、PKCS 証明書プロファイルを作成します。 このプロファイルは、署名証明書をデバイスに発行し、PKCS 証明書プロファイルをデバイスに展開します。

特定のユーザーに対する署名証明書をインポートすることもできます。 署名証明書は、ユーザーが登録するすべてのデバイスに展開されます。 証明書を Intune にインポートするには、[GitHub にある PowerShell コマンドレット](https://github.com/Microsoft/Intune-Resource-Access)を使います。 Intune にインポートされた PKCS 証明書をメールの署名に使われるように展開するには、「[Intune で PKCS 証明書を構成して使用する](certficates-pfx-configure.md)」の手順に従います。 次のステップが含まれます。

- PFX Certificate Connector for Microsoft Intune をダウンロードしてインストールします。 このコネクタは、インポートされた PKCS 証明書をデバイスに提供します。
- S/MIME メール署名証明書を Intune にインポートします。
- PKCS インポート済み証明書プロファイルを作成します。 このプロファイルは、インポートされた PKCS 証明書を適切なユーザーのデバイスに提供します。

## <a name="encryption-certificates"></a>暗号化証明書

暗号化に使われる証明書により、意図された受信者のみが暗号化されたメールを解読できることが保証されます。 S/MIME 暗号化は、メール通信で使うことができる追加セキュリティ レイヤーです。

暗号化されたメールを別のユーザーに送信するときは、そのユーザーの暗号化証明書の公開キーが取得されて、送信されるメールが暗号化されます。 受信者は、自分のデバイスの秘密キーを使ってメールを解読します。 ユーザーは、電子メールの暗号化に使用される証明書の履歴を持つことができます。 メールが正常に解読されるためには、これらの各証明書を特定のユーザーのすべてのデバイスに展開する必要があります。

Intune ではメール暗号化証明書を作成しないことをお勧めします。 Intune は暗号化をサポートする PKCS 証明書の発行をサポートしますが、Intune はデバイスごとに一意証明書を作成します。 S/MIME 暗号化のシナリオでは、暗号化証明書をユーザーのすべてのデバイスで共有する必要があるため、デバイスごとの一意証明書は適していません。

Intune を使って S/MIME 証明書を展開するには、ユーザーのすべての暗号化証明書を Intune にインポートする必要があります。 その後、Intune はユーザーが登録する各デバイスにすべての証明書を展開します。 証明書を Intune にインポートするには、[GitHub にある PowerShell コマンドレット](https://github.com/Microsoft/Intune-Resource-Access)を使います。

Intune にインポートされた、メールの暗号化に使われる PKCS 証明書を展開するには、「[Intune で PKCS 証明書を構成して使用する](certficates-pfx-configure.md)」の手順に従います。 次のステップが含まれます。

- PFX Certificate Connector for Microsoft Intune をダウンロードしてインストールします。 このコネクタは、インポートされた PKCS 証明書をデバイスに提供します。
- S/MIME メール暗号化証明書を Intune にインポートします。
- PKCS インポート済み証明書プロファイルを作成します。 このプロファイルは、インポートされた PKCS 証明書を適切なユーザーのデバイスに提供します。

 > [!NOTE]
 > 会社のデータが削除されると、またはユーザーが管理から登録解除されると、インポートされた S/MIME 暗号化証明書は Intune によって削除されます。 ただし、証明書は証明機関では取り消されません。

## <a name="smime-email-profiles"></a>S/MIME メール プロファイル

S/MIME の署名証明書と暗号化証明書のプロファイルを作成した後は、[iOS のネイティブ メールに対して S/MIME を有効にする](email-settings-ios.md)ことができます。