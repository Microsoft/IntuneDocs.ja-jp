## <a name="set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium"></a>Azure Active Directory Premium による Windows 10 と Windows 10 Mobile の自動登録の設定

ユーザーは自動登録を使用して、職場または学校のアカウントを追加し、管理することに同意して、Intune に会社所有または個人の Windows 10 PC および Windows 10 Mobile デバイスを登録できます。 簡単にできます。 バック グラウンドでユーザーのデバイスが登録され、Azure Active Directory に参加します。 登録されると、デバイスは Intune で管理されます。

**必要条件**
- Azure Active Directory Premium サブスクリプション ([試用版サブスクリプション](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune サブスクリプション


### <a name="configure-automatic-mdm-enrollment"></a>自動 MDM 登録の構成

1. [Azure 管理ポータル](https://portal.azure.com) (https://manage.WindowsAzure.com) で、**[Active Directory]** ノードに移動し、ディレクトリを選択します。

2. **[アプリケーション]** タブを選択します。 **Microsoft Intune** がアプリケーションの一覧に表示されます。

    ![Microsoft Intune での Azure AD アプリ](../media/aad-intune-app.png)

3. **Microsoft Intune** の矢印を選択します。 Microsoft Intune を構成できるページが開きます。

4. **[構成]** を選択すると、Microsoft Intune での自動 MDM 登録の構成を開始します。

5. Intune の URL 指定

  - **MDM 登録 URL** – 既定値を使用します。
  - **MDM 使用条件 URL** – 既定値を使用します。 この URL は、デバイスを登録すると、ユーザーの使用条件を表示します。
  - **MDM 準拠 URL** – 既定値を使用します。 デバイスが非対応だと分かった場合、**[アクセスが拒否されました]** というメッセージがこの URL に表示されます。 この URL からアクセスできるページで、ユーザーは、自身のデバイスがポリシーに準拠していない理由と、デバイスをポリシーに準拠させる方法について理解することができます。

6.  どのユーザーのデバイスを Microsoft Intune で管理するのかを指定します。 これらのユーザーの Windows 10 デバイスは、Microsoft Intune の管理対象として自動的に登録されます。

  - **すべて**
  - **グループ**
  - **なし**

7. **[保存]** を選びます。


<!--HONumber=Feb17_HO2-->


