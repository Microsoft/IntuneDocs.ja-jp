# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>MAM とアプリの保護に関してよく寄せられる質問

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

この記事では、Intune モバイル アプリケーション管理 (MAM) と Intune アプリ保護に関してよく寄せられる質問に対する回答を示します。

## <a name="mam-basics"></a>MAM の基礎


**MAM とは何ですか。** [Intune モバイル アプリケーション管理](overview-of-app-lifecycle-in-microsoft-intune.md)とは、ユーザーのモバイル アプリの公開、プッシュ、構成、セキュリティ保護、監視、および更新を可能にする一連の Intune 管理機能のことです。

**MAM のアプリ保護の利点は何ですか。** MAM は、アプリケーション内の組織のデータを保護します。 MAM-WE を使用すれば、機密データが含まれる職場または学校関連のアプリを、Bring Your Own Device (BYOD) シナリオにおける個人所有デバイスを含むほぼすべてのデバイスで管理できます。 Microsoft Office アプリなどの多くの仕事効率化アプリを、Intune MAM で管理することができます。 一般使用が可能な [Intune 対応アプリ](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)の公式の一覧を参照してください。

**MAM でサポートされるのはどのようなデバイス構成ですか。** Intune MAM では次の 2 つの構成をサポートしています。
  1. **Intune MDM と MAM**: これは MAM の初回起動時にサポートされる 1 つ目の構成です。 IT 管理者は、Intune モバイル デバイス管理 (MDM) に登録されているデバイスで MAM とアプリ保護ポリシーを使用したアプリの管理のみを行うことができます。 MDM と MAM を使ってアプリを管理するには、Intune スタンドアロン コンソール (http://manage.microsoft.com) を使用する必要があります。

  2. **デバイス登録なしの MAM**: デバイス登録なしの MAM (MAM-WE) では、IT 管理者は Intune MDM に登録されていないデバイスで MAM とアプリ保護ポリシーを使ってアプリを管理できます。 つまり、サードパーティ EMM プロバイダーに登録されているデバイスで Intune によりアプリを管理できます。 MAM-WE でアプリを管理するには、Azure Portal (http://portal.azure.com) の Intune コンソールを使用する必要があります。


## <a name="app-protection-policies"></a>アプリ保護ポリシー

**アプリ保護ポリシーとは何ですか。** アプリ保護ポリシーは、管理対象アプリで組織のデータがセキュリティ保護または保持されるようにするルールです。 ポリシーの例としては、ユーザーが "企業" データへのアクセスまたは移動を試みた場合や、アプリ内で禁止または監視されている一連の操作を試みた場合に適用されるルールがあります。

**アプリ保護ポリシーにはどのようなものがありますか。** 各アプリ保護ポリシーの設定の詳細については、[Android アプリ保護ポリシーの設定](android-mam-policy-settings.md)と [iOS アプリ保護ポリシーの設定](ios-mam-policy-settings.md)に関する各記事を参照してください。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>アプリ保護ポリシーで管理できるアプリ

**どのアプリをアプリ保護ポリシーで管理できますか。** Intune アプリ保護ポリシーでは、[Intune アプリ SDK](../develop/intune-app-sdk.md) で有効化されたアプリや [Intune アプリ ラッピング ツール](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)によってラップされたアプリを管理できます。 一般使用が可能な [Intune 対応アプリ](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps)の公式の一覧を参照してください。

**Intune 対応アプリでアプリ保護ポリシーを使用するための基本要件は何ですか。**
  1. エンドユーザーに、Azure Active Directory (AAD) アカウントが必要です。 Azure Active Directory で Intune ユーザーを作成する方法については、「[Intune にユーザーを追加して管理権限を付与する](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md)」を参照してください。

  2. エンドユーザーに、Azure Active Directory アカウントに割り当てられた Microsoft Intune のライセンスが必要です。 Intune ライセンスをエンドユーザーに割り当てる方法については、「[Intune のライセンスを管理する](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4.md)」を参照してください。

  3. エンドユーザーは、アプリ保護ポリシーの対象となるセキュリティ グループに属している必要があります。 同一のアプリ保護ポリシーでは、使用中の特定のアプリを対象とする必要があります。 アプリ保護ポリシーは、[Azure Portal](http://portal.azure.com) の Intune コンソールで作成して展開できます。 セキュリティ グループは、現在 [Office ポータル](http://portal.office.com)で作成できます。

  4. エンドユーザーは、AAD アカウントを使用してアプリにサインインする必要があります。

**[Outlook モバイル アプリ](https://www.microsoft.com/en-us/outlook-com/mobile/)を使用するための追加要件は何ですか。**

  1. エンドユーザーが、Outlook モバイル アプリをデバイスにインストールしている必要があります。

  2. エンド ユーザーに、[Office 365 Exchange Online](https://products.office.com/en-us/exchange/exchange-online) メールボックスと Azure Active Directory アカウントにリンクされたライセンスが必要です。

  >[!NOTE]
  > 現段階では、Outlook モバイル アプリは Microsoft Exchange Online のみをサポートし、Exchange On-Premises と Office 365 専用の Exchange はサポートされていません。

**[Word、Excel、PowerPoint](https://products.office.com/business/office) のアプリを使用するための追加要件は何ですか。**

  1. エンドユーザーに、Azure Active Directory アカウントにリンクされた [Office 365 Business または Office 365 Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) のライセンスが必要です。 サブスクリプションには、モバイル デバイスの Office アプリと [OneDrive for Business](https://onedrive.live.com/about/business/) のクラウド ストレージ アカウントが含まれている必要があります。 Office 365 のライセンスは、[Office ポータル](http://portal.office.com)でこちらの[手順](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc?ui=en-US&rs=en-US&ad=US)を実行して割り当てることができます。

  2. エンドユーザーは、[OneDrive](https://onedrive.live.com/about/) アプリをデバイスにインストールし、AAD アカウントを使用してサインインする必要があります。

  3. OneDrive アプリは、エンドユーザーに展開されているアプリ保護ポリシーの対象にする必要があります。

  >[!NOTE]
  > 現段階では、Office モバイル アプリは SharePoint Online のみをサポートし、オンプレミスの SharePoint はサポートされていません。

**Office に OneDrive が必要なのはなぜですか。** Intune は、アプリ内のすべてのデータを "企業" データまたは "個人用" データのいずれかとしてマークします。 勤務地から送信されたデータは "企業" データと見なされます。 Office アプリについては、Intune では電子メール (Exchange) またはクラウド ストレージ (OneDrive for Business アカウントを使用した OneDrive アプリ) が勤務地と見なされます。

**Skype for Business を使用するための追加要件は何ですか。** [Skype for Business](https://products.office.com/skype-for-business/it-pros) のライセンス要件を参照してください。
  >[!NOTE]
  > 現在、Skype for Business モバイル アプリは、Skype for Business Online のみをサポートしています。

## <a name="app-protection-features"></a>アプリ保護機能

**複数 ID サポートとは何ですか。** 複数 ID サポートは、アプリにサインインしている職場または学校のアカウントにのみアプリ保護ポリシーを適用する Intune アプリ SDK の機能です。 個人用アカウントでアプリにサインインした場合、データは管理されません。

**複数 ID サポートの目的は何ですか。** 複数 ID サポートを使用すると、"企業" および消費者の両方に利用されるアプリ (Office アプリなど) に "企業" アカウント用の Intune アプリ保護機能を付けて公開することができます。

**PIN 画面はいつ表示されますか。** Intune の PIN 画面は、ユーザーがアプリで "企業" データにアクセスしようとしたときにのみ表示されます。 たとえば、Word、Excel、PowerPoint のアプリでは、(PIN を適用するアプリ保護ポリシーが正常に展開されている場合) エンドユーザーが OneDrive for Business からドキュメントを開こうとすると表示されます。

**Outlook と複数 ID についてはどうですか。** Outlook では個人用電子メールと "企業" 電子メールの両方が一緒に表示されるため、Outlook アプリの起動時に Intune の PIN が要求されます。

**Intune アプリの PIN とは何ですか。** 暗証番号 (PIN) は、アプリケーションで適切なユーザーが組織のデータにアクセスしていることを確認するために使用されるパスコードです。

  1. **PIN の入力を要求されるのはいつですか。** Intune では、ユーザーが "企業" データにアクセスしようとした場合にのみアプリの PIN が要求されます。 Word、Excel、PowerPoint などの複数 ID アプリでは、"企業" のドキュメントやファイルを開こうとすると PIN の入力を求めるメッセージが表示されます。 Intune アプリ ラッピング ツールを使用して有効化された基幹業務アプリなどの単一 ID アプリでは、Intune アプリ SDK によってアプリでのユーザーのエクスペリエンスが常に "企業" であることが把握されているため、起動時に PIN が要求されます。

  2. **PIN は安全ですか。** PIN は、アプリで適切なユーザーのみが組織のデータにアクセスできるようにするためのものです。 そのため、エンドユーザーが Intune アプリの PIN を設定またはリセットするには、職場または学校のアカウントを使用してサインインする必要があります。 この認証は Azure Active Directory によってセキュリティ トークンの交換を通じて処理され、Intune アプリ SDK に対して透過的ではありません。 セキュリティの観点からは、職場または学校のデータを保護する最も効果的な方法は暗号化です。 暗号化はアプリの PIN とは関係しませんが、独自のアプリ保護ポリシーと関係があります。

  3. **Intune ではブルート フォース攻撃から PIN はどのように保護されますか。** IT 管理者は、アプリの PIN ポリシーの一環として、アプリがロックされるまでにユーザーが PIN の認証を試みることのできる最大回数を設定できます。 試行回数に達すると、Intune アプリ SDK によってアプリ内の "企業" データがワイプされます。

**暗号化についてはどうですか。** IT 管理者は、アプリ データの暗号化を必須にするアプリ保護ポリシーを展開できます。 ポリシーの一環として、IT 管理者はコンテンツがいつ暗号化されるかを指定することもできます。

  1. **Intune ではデータはどのように暗号化されますか。** 暗号化のアプリ保護ポリシー設定の詳細については、[Android アプリ保護ポリシーの設定](android-mam-policy-settings.md)と [iOS アプリ保護ポリシーの設定](ios-mam-policy-settings.md)に関する各記事を参照してください。

  2. **何が暗号化されますか。** IT 管理者のアプリ保護ポリシーに従い、"企業" データとしてマークされたデータのみが暗号化されます。 勤務地から送信されたデータは "企業" データと見なされます。 Office アプリについては、Intune では電子メール (Exchange) またはクラウド ストレージ (OneDrive for Business アカウントを使用した OneDrive アプリ) が勤務地と見なされます。 Intune アプリ ラッピング ツールによって有効化された基幹業務アプリでは、すべてのアプリ データが "企業" データと見なされます。

**Intune でのデータのリモート ワイプはどのように行われますか。** Intune では、アプリ データはフル ワイプおよび選択的ワイプの 2 つの異なる方法でワイプできます。 リモート ワイプの詳細については、「[Microsoft Intune のフル ワイプまたは選択的ワイプを使用してデータを保護する](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)」を参照してください。

  1. **フル ワイプとは何ですか。** [フル ワイプ](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe)では、デバイスを出荷時の既定の設定に戻すことにより、すべてのユーザー データと設定が**デバイス**から削除されます。 デバイスは Intune から削除されません。
  >[!NOTE]
  > フル ワイプは、Intune モバイル デバイス管理 (MDM) に登録済みのデバイスでのみ行うことができます。

  2. **選択的ワイプとは何ですか。** 選択的ワイプの詳細については、「[Microsoft Intune のフル ワイプまたは選択的ワイプを使用してデータを保護する](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe)」を参照してください。

  3. **選択的ワイプはどれくらいの間隔で行われますか。** 選択的ワイプの開始時にユーザーがアプリを使用している場合は、Intune アプリ SDK によって Intune MAM サービスからの選択的ワイプの要求が 30 分ごとにチェックされます。 ユーザーがアプリを初めて起動し職場または学校のアカウントを使ってサインインした場合も、選択的ワイプがチェックされます。

**オンプレミス サービスが Intune の保護対象アプリと連携しないのはなぜですか。** Intune アプリ保護は、アプリケーションと Intune アプリ SDK の間で一貫性を保つためにユーザーの ID に依存しています。 これを保証する唯一の方法は、最新の認証を使用することです。 アプリをオンプレミス構成と連携させるシナリオはありますが、一貫性がなく保証されていません。

**管理対象アプリから Web リンクを開く安全な方法はありますか。** はい、ご利用いただけます。 IT 管理者は、Microsoft Intune によって開発された、Intune で簡単に管理可能な Web ブラウザーである [Intune Managed Browser アプリ](manage-internet-access-using-managed-browser-policies.md)のアプリ保護ポリシーを展開および設定することができます。 IT 管理者は、Intune 対応アプリ内のすべての Web リンクが Managed Browser アプリで開かれるように指定することができます。


## <a name="app-experience-on-android"></a>Android でのアプリのエクスペリエンス

**Intune アプリ保護を Android デバイスで使用するのにポータル サイト アプリが必要なのはなぜですか。** アプリ保護機能の多くはポータル サイト アプリに組み込まれています。 デバイスの登録が_不要_な場合でも、ポータル サイト アプリは常に必要です。 MAM-WE では、エンドユーザーはデバイスにポータル サイト アプリをインストールするだけで済みます。

## <a name="app-experience-on-ios"></a>iOS でのアプリのエクスペリエンス

**データ転送ポリシーが "管理対象アプリのみ" または "アプリなし" に設定されている場合でも、iOS 共有拡張機能を使って、管理対象ではないアプリの職場または学校のデータを開くことができます。これはデータのリークではないのですか。** Intune アプリ保護ポリシーでは、デバイスを管理せずに iOS 共有拡張機能を制御することはできません。 したがって、Intune は _**"企業" データがアプリの外部で共有される前に、データを暗号化します**_。 これは、管理対象アプリの外部で "企業" ファイルを開いてみることによって確認できます。 ファイルは暗号化されていて、管理対象アプリの外部では開くことができないはずです。


<!--HONumber=Jan17_HO1-->


