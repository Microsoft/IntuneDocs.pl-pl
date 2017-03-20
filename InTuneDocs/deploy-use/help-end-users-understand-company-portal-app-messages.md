---
title: "Komunikaty aplikacji Portal firmy, które mogą zobaczyć użytkownicy korzystający z systemu Android | Microsoft Docs"
description: "Opis komunikatów, które mogą zobaczyć użytkownicy końcowi usługi Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0936051b5c33a2e98f275ef7a3a32be2e8f5a8b0
ms.openlocfilehash: 3d5245e809263c2e5d76402ae9adc72baf7c7924
ms.lasthandoff: 03/10/2017


---

# <a name="help-end-users-understand-company-portal-app-messages"></a>Pomaganie użytkownikom końcowym w zrozumieniu komunikatów aplikacji Portal firmy

> [!NOTE]
> Poniższe informacje dotyczą tylko urządzeń z systemem Android 6.0 lub nowszym.

Użytkownicy końcowi zobaczą na różnych etapach procesu rejestracji dwa różne komunikaty, które mogą ich zaniepokoić.

- __Zezwolić aplikacji Portal firmy na połączenia telefoniczne i zarządzanie nimi?__
- __Zezwolić aplikacji Portal firmy na dostęp do zdjęć, multimediów i plików na Twoim urządzeniu?__

## <a name="allow-company-portal-to-make-and-manage-phone-calls"></a>Zezwolić aplikacji Portal firmy na połączenia telefoniczne i zarządzanie nimi?

### <a name="where-it-appears"></a>Gdzie jest dostępny
Komunikat **Zezwolić aplikacji Portal firmy na połączenia telefoniczne i zarządzanie nimi?** jest wyświetlany, gdy użytkownicy wybiorą opcję **Zarejestruj** w aplikacji Portal firmy podczas rejestracji urządzenia.

### <a name="what-it-means"></a>Znaczenie
Akceptując ten monit, użytkownicy zezwalają na przesłanie numeru telefonu i numerów IMEI do usługi Intune. Pojawią się one w konsoli administracyjnej na stronie __Sprzęt__.

> [!NOTE]
> **Aplikacja Portal firmy nigdy nie wykonuje połączeń telefonicznych ani nimi nie zarządza.** Tekst komunikatu jest kontrolowany przez firmę Google i nie można go zmienić.

Aby wyświetlić stronę **Sprzęt**, wybierz pozycję **Grupy** > **Wszystkie urządzenia przenośne** > **Urządzenia**. Wybierz urządzenie użytkownika, a następnie wybierz pozycje **Wyświetl właściwości** > **Sprzęt**.

### <a name="what-happens-if-users-deny-access"></a>Co się stanie, gdy użytkownik nie zezwoli na dostęp
Użytkownicy, którzy wybiorą opcję odmowy dostępu, mogą nadal korzystać z aplikacji Portal firmy i zarejestrować swoje urządzenie. Pola numeru telefonu i numeru IMEI urządzenia pozostaną jednak puste na stronie __Sprzęt__ w konsoli administracyjnej. Podczas drugiego logowania użytkownika do aplikacji Portal firmy po odmowie dostępu w komunikacie zostanie wyświetlone pole wyboru **Nigdy nie pytaj ponownie**. Jego zaznaczenie spowoduje, że komunikat przestanie być wyświetlany.

Jeśli użytkownik zezwoli na dostęp, lecz potem anuluje zezwolenie, komunikat zostanie wyświetlony podczas następnego logowania użytkownika do aplikacji Portal firmy po rejestracji.

Jeśli później użytkownik zdecyduje się zezwolić na dostęp, może wybrać pozycję **Ustawienia** > **Aplikacje** > **Portal firmy** > **Uprawnienia** > **Telefon** i włączyć dostęp.

### <a name="how-to-explain-this-to-your-users"></a>Jak wyjaśnić to użytkownikom
Odeślij użytkowników do sekcji [Rejestrowanie urządzenia z systemem Android w usłudze Intune](/Intune/EndUser/enroll-your-device-in-intune-android), aby umożliwić im uzyskanie szczegółowych informacji.

## <a name="allow-company-portal-to-access-your-contacts"></a>Zezwolić aplikacji Portal firmy na dostęp do Twoich kontaktów?

### <a name="where-it-appears"></a>Gdzie jest dostępny
Komunikat **Zezwolić aplikacji Portal firmy na dostęp do Twoich kontaktów?** jest wyświetlany, gdy użytkownik wybierze opcję **Zarejestruj** w aplikacji Portal firmy podczas rejestracji urządzenia.

### <a name="what-it-means"></a>Znaczenie
Akceptując ten monit, użytkownicy zezwalają usłudze Intune na utworzenie konta służbowego i zarządzanie tożsamością usługi Azure Active Directory, która jest zarejestrowana dla użytkownika na tym urządzeniu.

> [!NOTE]
> **Firma Microsoft nigdy nie uzyskuje dostępu do Twoich kontaktów!** Tekst komunikatu jest kontrolowany przez firmę Google i nie można go zmienić.

### <a name="what-happens-if-users-deny-access"></a>Co się stanie, gdy użytkownik nie zezwoli na dostęp
Jeśli użytkownik nie zezwoli na dostęp, jego urządzenie nie zostanie zarejestrowane w usłudze Intune i nie będzie można nim zarządzać. Podczas drugiego logowania użytkownika do aplikacji Portal firmy po odmowie dostępu w komunikacie zostanie wyświetlone pole wyboru **Nigdy nie pytaj ponownie**. Jego zaznaczenie spowoduje, że komunikat przestanie być wyświetlany.

Jeśli użytkownik zezwoli na dostęp, lecz potem anuluje zezwolenie, komunikat zostanie wyświetlony podczas następnego logowania użytkownika do aplikacji Portal firmy po rejestracji.

Jeśli później użytkownik zdecyduje się zezwolić na dostęp, może wybrać pozycję **Ustawienia** > **Aplikacje** > **Portal firmy** > **Uprawnienia** > **Telefon** i włączyć dostęp.

### <a name="how-to-explain-this-to-your-users"></a>Jak wyjaśnić to użytkownikom
Odeślij użytkowników do sekcji [Rejestrowanie urządzenia z systemem Android w usłudze Intune](/Intune/EndUser/enroll-your-device-in-intune-android), aby umożliwić im uzyskanie szczegółowych informacji.

## <a name="allow-company-portal-to-access-photos-media-and-files-on-your-device"></a>Zezwolić aplikacji Portal firmy na dostęp do zdjęć, multimediów i plików na Twoim urządzeniu?

### <a name="where-it-appears"></a>Gdzie jest dostępny
Komunikat **Zezwolić aplikacji Portal firmy na dostęp do zdjęć, multimediów i plików na Twoim urządzeniu?** jest wyświetlany, gdy użytkownik wybierze opcję **Wyślij dane**, aby wysłać dzienniki do administratora IT.

### <a name="what-it-means"></a>Znaczenie
Akceptując ten monit, użytkownicy zezwalają swoim urządzeniom na zapisywanie dzienników danych na kartach SD oraz umożliwiają przenoszenie tych dzienników za pośrednictwem kabla USB.   

> [!NOTE]
> **Aplikacja Portal firmy nigdy nie uzyskuje dostępu do zdjęć, multimediów ani plików użytkownika.** Tekst komunikatu jest kontrolowany przez firmę Google i nie można go zmienić.

### <a name="what-happens-if-users-deny-access"></a>Co się stanie, gdy użytkownik nie zezwoli na dostęp
Jeśli użytkownik nie zezwoli na dostęp, nadal może wysyłać dzienniki danych za pośrednictwem poczty e-mail, ale dzienniki nie będą kopiowane na kartę SD urządzenia.

Podczas drugiego logowania użytkownika do aplikacji Portal firmy po odmowie dostępu w komunikacie zostanie wyświetlone pole wyboru **Nigdy nie pytaj ponownie**. Jego zaznaczenie spowoduje, że komunikat nigdy nie zostanie wyświetlony ponownie. Jeśli użytkownik zezwoli na dostęp, lecz potem anuluje zezwolenie, komunikat zostanie wyświetlony podczas następnej próby wysłania dzienników przez użytkownika. Jeśli później użytkownik zdecyduje się zezwolić na dostęp, może wybrać pozycję **Ustawienia** > **Aplikacje** > **Portal firmy** > **Uprawnienia** > **Pamięć** i włączyć uprawnienie.


### <a name="how-to-explain-this-to-your-users"></a>Jak wyjaśnić to użytkownikom
Odeślij użytkowników do sekcji [Wysyłanie dzienników do administratora IT pocztą e-mail](/Intune/EndUser/send-logs-to-your-it-admin-by-email-android). Możesz także odesłać ich do sekcji [Wysyłanie dzienników do administratora IT za pomocą kabla](/Intune/EndUser/send-logs-to-your-it-admin-by-cable-android), aby umożliwić im porównanie obu metod.


### <a name="see-also"></a>Zobacz także
[Co powinni wiedzieć użytkownicy końcowi na temat korzystania z usługi Intune](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
