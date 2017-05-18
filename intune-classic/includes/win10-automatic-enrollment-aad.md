## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を有効にする

自動登録により、ユーザーは個人所有のデバイスに職場のアカウントを追加したり、会社所有のデバイスを Azure Active Directory に参加させたりして、Windows 10 デバイスを Intune に登録することができます。 バック グラウンドでユーザーのデバイスが登録され、Azure Active Directory に参加します。 登録されると、デバイスは Intune で管理されます。

**必要条件**
- Azure Active Directory Premium サブスクリプション ([試用版サブスクリプション](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune サブスクリプション


### <a name="configure-automatic-mdm-enrollment"></a>自動 MDM 登録の構成

1. [Azure 管理ポータル](https://portal.azure.com) (https://manage.windowsazure.com) にサインインして、**[Azure Active Directory]** をクリックします。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-azure-main.png)

2. **[モビリティ (MDM と MAM)]** を選択します。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-mdm.png)

3. **Microsoft Intune** を選択します。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-intune.png)

4. **[MDM ユーザー スコープ]** を構成します。 どのユーザーのデバイスを Microsoft Intune で管理するのかを指定します。 これらのユーザーの Windows 10 デバイスは、Microsoft Intune の管理対象として自動的に登録されます。

  - **なし**
  - **一部**
  - **すべて**

 ![Azure Portal のスクリーンショット](../media/auto-enroll-scope.png)

5. 次の URL の既定値を使用します。
  - **MDM 使用条件 URL**
  - **MDM 探索 URL**
  - **MDM 準拠 URL**

6. **[保存]** を選択します。

既定では、サービスに対して 2 要素認証は有効になっていません。 ただし、デバイスを登録するときには 2 要素認証をお勧めします。 このサービスの 2 要素認証を要求する前に、Azure Active Directory で 2 要素認証プロバイダーを構成し、多要素認証用にユーザー アカウントを構成する必要があります。 「[クラウドでの Azure Multi-Factor Authentication Server の概要](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)」を参照してください。
