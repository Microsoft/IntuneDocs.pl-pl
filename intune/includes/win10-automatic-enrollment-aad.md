## <a name="enable-windows-10-automatic-enrollment"></a>Włączanie automatycznej rejestracji urządzeń z systemem Windows 10

Automatyczna rejestracja umożliwia użytkownikom rejestrowanie ich urządzeń z systemem Windows 10 w usłudze Intune podczas dodawania kont służbowych na urządzeniach prywatnych lub dołączania urządzeń stanowiących własność firmy do usługi Azure Active Directory. W tle urządzenie użytkownika zostaje zarejestrowane i przyłączone do usługi Azure Active Directory. Po zarejestrowaniu urządzenie jest zarządzane za pomocą usługi Intune.

**Wymagania wstępne**
- Subskrypcja usługi Azure Active Directory — wersja Premium ([subskrypcja wersji próbnej](http://go.microsoft.com/fwlink/?LinkID=816845))
- Subskrypcja usługi Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurowanie automatycznej rejestracji w usłudze MDM

1. Zaloguj się do [Portalu zarządzania Azure](https://portal.azure.com) (https://manage.windowsazure.com) i wybierz usługę **Azure Active Directory**.

  ![Zrzut ekranu witryny Azure Portal](../media/auto-enroll-azure-main.png)

2. Wybierz pozycję **Mobilność (MDM i MAM)**.

  ![Zrzut ekranu witryny Azure Portal](../media/auto-enroll-mdm.png)

3. Wybierz pozycję **Microsoft Intune**.

  ![Zrzut ekranu witryny Azure Portal](../media/auto-enroll-intune.png)

4. Skonfiguruj **zakres użytkownika oprogramowania MDM**. Określ użytkowników, których urządzenia powinny być zarządzane przez usługę Microsoft Intune. Urządzenia z systemem Windows 10 tych użytkowników zostaną automatycznie zarejestrowane w usłudze Microsoft Intune.

  - **Brak**
  - **Niektóre**
  - **Wszystkie**

   ![Zrzut ekranu witryny Azure Portal](../media/auto-enroll-scope.png)

5. Użyj wartości domyślnych dla następujących adresów URL:
    - **Adres URL Warunków użytkowania zarządzania urządzeniami mobilnymi**
    - **Adres URL odnajdywania zarządzania urządzeniami przenośnymi**
    - **Adres URL zgodności oprogramowania MDM**

6. Wybierz pozycję **Zapisz**.

Uwierzytelnianie dwuskładnikowe nie jest domyślnie włączone dla usługi. Zaleca się jednak korzystanie z uwierzytelniania dwuskładnikowego podczas rejestrowania urządzenia. Przed ustawieniem wymagania zastosowania uwierzytelniania dwuskładnikowego dla tej usługi należy skonfigurować dostawcę usługi uwierzytelniania dwuskładnikowego w usłudze Active Directory Azure i skonfigurować konta użytkowników do uwierzytelniania wieloskładnikowego. Zobacz temat [Wprowadzenie do usługi Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).