---
# required metadata

title: Ochrona urządzeń z systemem iOS przez obejście blokady aktywacji w usłudze Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ochrona urządzeń z systemem iOS przez obejście blokady aktywacji w usłudze Microsoft Intune
Usługa Microsoft Intune ułatwia zarządzanie blokadą aktywacji systemu iOS — funkcją aplikacji Znajdź mój iPhone dla urządzeń z systemem iOS 7.1 lub nowszym. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Jeśli ta funkcja została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:

-   Wyłączenie aplikacji Znajdź mój iPhone

-   Wymazanie urządzenia

-   Ponowne uaktywnienie urządzenia

## Wpływ blokady aktywacji na Twoje działania
Blokada aktywacji pomaga w zabezpieczaniu urządzeń z systemem iOS i zwiększa szanse na odzyskanie urządzenia w razie jego zgubienia lub kradzieży, jednak może ona powodować problemy dla administratora systemu informatycznego. Na przykład:

-   jeden z użytkowników konfiguruje blokadę aktywacji na urządzeniu. Następnie użytkownik odchodzi z firmy i zwraca urządzenie. Bez identyfikatora Apple ID i hasła użytkownika nie ma możliwości ponownego uaktywnienia urządzenia.

-   Potrzebny jest raport ze wszystkimi urządzeniami, na których włączono blokadę aktywacji.

-   Podczas odświeżania urządzenia w organizacji chcesz ponownie przypisać niektóre urządzenia do innego działu. Możesz przypisywać ponownie tylko urządzenia, na których nie włączono blokady aktywacji.

Aby pomóc w rozwiązaniu tych problemów, firma Apple wprowadziła obejście blokady aktywacji w systemie iOS 7.1. Dzięki temu można usunąć blokadę aktywacji z nadzorowanych urządzeń bez identyfikatora Apple ID i hasła użytkownika. Nadzorowane urządzenie może wygenerować unikatowy kod obejścia blokady aktywacji, który jest przechowywany na serwerze aktywacji firmy Apple.

> [!TIP]
> Tryb nadzorowany dla urządzeń z systemem iOS umożliwia zablokowanie urządzenia za pomocą narzędzia Apple Configurator w celu ograniczenia funkcji urządzenia do określonych celów biznesowych. Tryb nadzorowany jest przeznaczony praktycznie tylko dla urządzeń należących do firm.

## Jak usługa Intune pomaga w zarządzaniu blokadą aktywacji
Usługa Intune może wysłać żądanie dotyczące stanu blokady aktywacji na nadzorowanych i nienadzorowanych urządzeniach z systemem iOS 7.1 lub nowszym. W przypadku urządzeń nadzorowanych usługa Intune może pobrać kod obejścia blokady aktywacji i wystawić go bezpośrednio na urządzeniu. Jeśli zawartość urządzenia została wyczyszczona, możesz bezpośrednio uzyskać dostęp do urządzenia, używając kodu jako nazwy użytkownika i pustego hasła.

**Wiąże się to z następującymi korzyściami dla firmy**:

-   Użytkownik może korzystać z zabezpieczeń oferowanych przez aplikację Znajdź mój iPhone.

-   Możesz umożliwić użytkownikowi normalną pracę, wiedząc, że w razie konieczności zmiany przeznaczenia urządzenia można je wycofać lub odblokować.

## Jak użyć obejścia blokady aktywacji z poziomu konsoli administracyjnej usługi Intune
> [!IMPORTANT]
> Po obejściu blokady aktywacji na urządzeniu zostanie automatycznie zastosowana nowa blokada aktywacji w przypadku otwarcia aplikacji Znajdź mój iPhone. Dlatego **musisz mieć fizyczny dostęp do urządzenia, aby móc wykonać tę procedurę**..

1.  W [konsoli administracyjnej usługi Microsoft Intune](https://manage.microsoft.com) wybierz pozycję **Grupy** &gt; **Wszystkie urządzenia** &gt; **Wszystkie urządzenia należące do firmy**.

2.  Wybierz urządzenie, na którym chcesz obejść blokadę aktywacji. Wybierz pozycję **Obejście blokady aktywacji**..

3.  Przeczytaj komunikat ostrzegawczy. Wybierz przycisk **Tak**, aby kontynuować.

Stan żądania odblokowania można sprawdzić na stronie szczegółów urządzenia.

## Jak sprawdzić, które urządzenia korzystają z blokady aktywacji
Aby sprawdzić, które urządzenia korzystają z blokady aktywacji, użyj jednej z dwóch metod:

-   Uruchom polecenie **Raporty ze spisu urządzeń przenośnych**. Ten raport zawiera kolumny **Stan blokady aktywacji** i **Nadzorowane** , określające stan urządzeń. Kolumna **Nadzorowane** może mieć wartość **Tak** lub **Nie**, a kolumna **Stan blokady aktywacji** może mieć następujące wartości:

    -   Włączona z kodem obejścia

    -   Włączona bez kodu obejścia (urządzenie nie jest nadzorowane)

    -   Włączona bez kodu obejścia (urządzenie jest niedostępne)

    -   Niewłączona

    Pole **Stan blokady aktywacji** jest puste w przypadku urządzeń, które nie korzystają z systemu iOS 7.1 lub nowszego.

-   Wybierz urządzenie w widoku grup. Stan blokady aktywacji jest widoczny w okienku szczegółów urządzenia.

    Wybranie urządzenia w węźle **Wszystkie urządzenia należące do firmy** spowoduje włączenie blokady aktywacji na tym urządzeniu. Zostanie również wyświetlony kod obejścia. Za jego pomocą można ręcznie obejść blokadę aktywacji.

### Zobacz także
[Wycofywanie urządzeń](retire-devices-from-microsoft-intune-management.md)
[Łatwiejsza ochrona urządzeń za pomocą funkcji zdalnego blokowania i resetowania kodu dostępu](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->

