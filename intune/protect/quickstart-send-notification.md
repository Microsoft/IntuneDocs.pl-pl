---
title: Szybki start — wysyłanie powiadomień do niezgodnych urządzeń
titleSuffix: Microsoft Intune
description: W tym przewodniku Szybki start użyjesz usługi Microsoft Intune w celu wysyłania powiadomień e-mail do niezgodnych urządzeń.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5fe05152b2221f17df4497d30e6a028523b878fd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721945"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Szybki start: Wysyłanie powiadomień do niezgodnych urządzeń

W tym przewodniku Szybki start użyjesz usługi Microsoft Intune w celu wysyłania powiadomień e-mail do pracowników, którzy mają niezgodne urządzenia.

Domyślnie po wykryciu przez usługę Intune urządzenia, które nie jest zgodne, usługa Intune natychmiast oznacza to urządzenie jako niezgodne. [Dostęp warunkowy](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) usługi Azure Active Directory (AAD) blokuje wtedy dane urządzenie. Gdy urządzenie jest niezgodne, usługa Intune umożliwia dodanie akcji dotyczących niezgodności, co zapewnia elastyczność podejmowania decyzji. Możesz na przykład przez zablokowaniem niezgodnych urządzeń wyznaczyć użytkownikom okres prolongaty, w trakcie którego będą mieli czas na zapewnienie zgodności urządzenia.

Jedną z czynności, które można wykonać, gdy urządzenia nie są zgodne, jest wysłanie wiadomości e-mail do użytkowników końcowych. Można również dostosować powiadomienie e-mail przed wysłaniem go do użytkowników końcowych. Możesz dostosować adresatów, temat oraz treść wiadomości, w tym logo firmy oraz informacje kontaktowe. Ponadto usługa Intune dołącza do powiadomienia e-mail szczegółowe informacje dotyczące niezgodnych urządzeń.

Jeśli nie masz subskrypcji usługi Intune, [utwórz konto bezpłatnej wersji próbnej](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Wymagania wstępne
- Jeśli blokujesz urządzeniom dostęp do zasobów firmowych przy użyciu zasad zgodności urządzeń, musisz mieć skonfigurowany dostęp warunkowy usługi AAD. Ukończenie przewodnika Szybki start [Tworzenie zasad zgodności urządzenia](quickstart-set-password-length-android.md) oznacza, że używasz usługi Azure Active Directory. Aby uzyskać więcej informacji na temat usługi AAD, zobacz [Dostęp warunkowy w usłudze Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) oraz [Typowe sposoby korzystania z dostępu warunkowego przy użyciu usługi Intune](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Logowanie się do usługi Intune

Zaloguj się w usłudze [Intune](https://aka.ms/intuneportal) jako [administrator globalny](../fundamentals/users-add.md#types-of-administrators) lub [administrator usługi](../fundamentals/users-add.md#types-of-administrators) Intune. Jeśli utworzono subskrypcję wersji próbnej usługi Intune, konto, którego użyto do utworzenia subskrypcji, jest administratorem globalnym.

## <a name="create-a-notification-message-template"></a>Tworzenie szablonu wiadomości z powiadomieniem

Aby wysyłać wiadomości e-mail do użytkowników, należy utworzyć szablon wiadomości z powiadomieniem. Gdy urządzenie jest niezgodne, szczegółowe informacje wprowadzone w szablonie są wyświetlane w wiadomości e-mail wysyłanej do użytkowników.

1. W usłudze Intune wybierz kolejno pozycje **Zgodność urządzenia** > **Powiadomienia** > **Utwórz powiadomienie**. 
2. Wprowadź następujące informacje:

   - **Nazwa**: *Administrator firmy Contoso*
   - **Temat**: *Zgodność urządzeń*
   - **Wiadomość**: *Urządzenie obecnie nie spełnia wymogów zgodności w organizacji.*
   - **Nagłówek wiadomości e-mail — dołącz logo firmy**: Ustaw opcję **Włączone**, aby pokazać logo organizacji.
   - **Stopka wiadomości e-mail — dołącz nazwę firmy**: Ustaw opcję **Włączone**, aby pokazać nazwę organizacji.
   - **Stopka wiadomości e-mail — dołącz informacje kontaktowe**: Ustaw opcję **Włączone**, aby pokazać informacje kontaktowe firmy.

   ![Przykład powiadomienia dotyczącego zgodności w usłudze Intune](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Gdy skończysz dodawać informacje, wybierz pozycję **Utwórz**. Szablon wiadomości z powiadomieniem jest gotowy do użytku.

    > [!NOTE]
    > Możesz również edytować wcześniej utworzony szablon powiadomienia.

Aby uzyskać szczegółowe informacje dotyczące konfigurowania nazwy firmy, danych kontaktowych firmy oraz logo firmy, zobacz [Informacje o firmie i zasady zachowania poufności informacji](../apps/company-portal-app.md#company-information-and-privacy-statement), [Informacje dotyczące pomocy technicznej](../apps/company-portal-app.md#support-information) oraz [Dostosowywanie znakowania tożsamości firmy](../apps/company-portal-app.md#company-identity-branding-customization). 

## <a name="add-a-noncompliance-policy"></a>Dodawanie zasad niezgodności

Podczas tworzenia zasad zgodności urządzeń usługa Intune automatycznie tworzy akcję w przypadku niezgodności. Jeśli dane urządzenie nie jest zgodne z zasadami zgodności, zostanie automatycznie oznaczone przez usługę Intune jako niezgodne. Możesz dostosować czas, przez jaki urządzenie będzie oznaczone jako niezgodne. Podczas tworzenia zasad zgodności lub aktualizowania istniejących zasad możesz także dodać kolejną akcję. 

Poniższe kroki umożliwiają utworzenie zasad zgodności dla urządzeń z systemem Windows 10.

1. W usłudze Intune wybierz pozycję **Zgodność urządzenia**.
2. Wybierz pozycję **Zasady** > **Utwórz zasady**.
3. Wprowadź następujące informacje:

   - **Nazwa**: *Zgodność systemu Windows 10*
   - **Opis**: *Zasady zgodności systemu Windows 10*
   - **Platforma**: System Windows 10 lub nowszy

4. Wybierz kolejno pozycje **Ustawienia** > **Zabezpieczenia systemu**, aby wyświetlić ustawienia dotyczące zabezpieczeń urządzenia.
5. W obszarze **Wymagaj hasła do odblokowania urządzeń przenośnych** wybierz pozycję **Wymagaj**. To ustawienie określa, czy użytkownicy mają wpisywać hasło przed uzyskaniem dostępu do informacji zapisanych na urządzeniu przenośnym. 
6. Ustaw **minimalną długość hasła** na **6**. To ustawienie określa minimalną liczbę cyfr lub znaków hasła.

    <img alt="System Security settings for a new compliance policy" src="./media/quickstart-send-notification/quickstart-send-notification-01.png" width="600">

7. Kliknij kolejno pozycje **OK** > **OK** > **Utwórz**, aby utworzyć zasady zgodności.
8. Wybierz kolejno pozycje **Właściwości** > **Akcja dotycząca niezgodności** > **Dodaj**.
9. W polu listy rozwijanej **Akcja** sprawdź, czy wybrano pozycję **Wyślij wiadomość e-mail do użytkowników końcowych**.
10. Wybierz kolejno pozycje **Szablon wiadomości** > **Administrator firmy Contoso** > **Wybierz**, aby wybrać szablon wiadomości utworzony we wcześniejszej części tego tematu.
11. Wybierz kolejno pozycje **DODAJ** > **OK** > **Zapisz**, aby zapisać zmiany.

## <a name="assign-the-policy"></a>Przypisywanie zasad

Zasady zgodności można przypisać do konkretnej grupy użytkowników lub do wszystkich użytkowników. Gdy usługa Intune rozpozna niezgodne urządzenie, użytkownik zostanie powiadomiony, że musi zaktualizować urządzenie, aby spełniało zasady zgodności. W poniższych krokach opisano przypisywanie zasad.

1. Wybierz utworzone wcześniej zasady **Zgodność dla systemu Windows 10**.
2. Wybierz pozycję **Przypisania**.
3. W polu listy rozwijanej **Przypisz do** wybierz pozycję **Wszyscy użytkownicy**. Dzięki temu wybrani zostaną wszyscy użytkownicy. Każdy użytkownik mający urządzenie z systemem **Windows 10 lub nowszym**, które nie spełnia zasad zgodności, zostanie o tym powiadomiony.

    > [!NOTE]
    > Możesz dołączać lub wykluczać grupy podczas przypisywania zasad zgodności.

4. Kliknij polecenie **Zapisz**.

Jeśli zasady zostały pomyślnie utworzone i zapisane, pojawią się na liście **Zgodność urządzenia — zasady**. Zwróć uwagę, że opcja **Przypisane** na liście jest ustawiona na **Tak**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki start użyto usługi Intune do utworzenia i przypisania zasad zgodności dla urządzeń z systemem Windows 10 pracowników, które będą wymagać wprowadzenia hasła składającego się z co najmniej sześciu znaków. Aby uzyskać więcej informacji na temat tworzenia zasad zgodności dla urządzeń z systemem Windows, zobacz [Dodawanie zasad zgodności urządzeń z systemem Windows w usłudze Intune](compliance-policy-create-windows.md).

Aby zapoznać się kolejnymi przewodnikami Szybki start dotyczącymi usługi Intune, przejdź do kolejnego przewodnika Szybki start.

> [!div class="nextstepaction"]
> [Szybki start: Dodawanie i przypisywanie aplikacji klienckiej](../apps/quickstart-add-assign-app.md)