## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 の自動登録を有効にする

ユーザーは自動登録を使用して、職場または学校のアカウントを追加し、管理することに同意して、Intune に会社所有または個人の Windows 10 PC および Windows 10 Mobile デバイスを登録できます。 簡単にできます。 バック グラウンドでユーザーのデバイスが登録され、Azure Active Directory に参加します。 登録されると、デバイスは Intune で管理されます。

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

4. 自動的に登録するユーザーを構成します。

  ![Azure Portal のスクリーンショット](../media/auto-enroll-scope.png)

  次の URL の既定値を使用します。
  - **MDM 登録**
  - **MDM 使用条件**
  - **MDM コンプライアンス**

5. どのユーザーのデバイスを Microsoft Intune で管理するのかを指定します。 これらのユーザーの Windows 10 デバイスは、Microsoft Intune の管理対象として自動的に登録されます。

  - **すべて**
  - **グループ**
  - **なし**

6. **[保存]** を選択します。
