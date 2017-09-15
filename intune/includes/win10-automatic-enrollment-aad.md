## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を有効にする

自動登録により、Intune に Windows 10 デバイスを登録できます。 登録するには、ユーザーが職場アカウントを個人所有のデバイスを追加するか、会社所有のデバイスを Azure Active Directory に参加させます。 バック グラウンドでデバイスが登録され、Azure Active Directory に参加します。 登録されると、デバイスは Intune で管理されます。

**必要条件**
- Azure Active Directory Premium サブスクリプション ([試用版サブスクリプション](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune サブスクリプション


### <a name="configure-automatic-mdm-enrollment"></a>自動 MDM 登録の構成

1. [Azure Portal](https://portal.azure.com) にサインインして、 **[Azure Active Directory]** を選択します。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-azure-main.png)

2. **[モビリティ (MDM と MAM)]** を選択します。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-mdm.png)

3. **Microsoft Intune** を選択します。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-intune.png)

4. **[MDM ユーザー スコープ]** を構成します。 どのユーザーのデバイスを Microsoft Intune で管理するのかを指定します。 これらの Windows 10 デバイスは、Microsoft Intune の管理対象として自動的に登録されます。

  - **[なし]** - MDM の自動登録が無効になります
  - **[Some]\(一部\)** - **[グループ]** を選びます。そのグループの Windows 10 デバイスを自動的に登録できます
  - **[すべて]** - すべてのユーザーが自分の Windows 10 デバイスを自動的に登録できます

      > [!IMPORTANT]
      > **MAM ユーザー スコープ**と自動 MDM 登録 (**MDM ユーザー スコープ**) の両方が有効になっている場合、MAM のみが有効になります。 個人用デバイスをワークプレースに参加させると、MAM のみがそのグループのユーザーに追加されます。 デバイスは、自動的には MDM に登録されません。

   ![Azure Portal のスクリーンショット](../media/auto-enroll-scope.png)

5. 次の URL の既定値を使用します。
    - **MDM 使用条件 URL**
    - **MDM 探索 URL**
    - **MDM 準拠 URL**

6. **[保存]** を選択します。

既定では、サービスに対して 2 要素認証は有効になっていません。 ただし、デバイスを登録するときには 2 要素認証をお勧めします。 2 要素認証を有効にするには、Azure AD で 2 要素認証プロバイダーを構成し、多要素認証用にユーザー アカウントを構成します。 「[クラウドでの Azure Multi-Factor Authentication Server の概要](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)」を参照してください。
