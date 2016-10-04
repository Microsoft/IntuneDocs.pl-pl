---
title: "Konfigurowanie subskrypcji przy użyciu usługi Lookout MTP | Microsoft Intune"
description: "Ten temat zawiera szczegółowe informacje dotyczące sposobu konfigurowania usługi Lookout MTP."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2196ff03975df1f8969e1522f7af459343694d
ms.openlocfilehash: 530a34c7c75a4fa73cbb62873e2d28883b91b57e


---

# Konfigurowanie subskrypcji dla usługi Lookout do ochrony urządzeń przenośnych przed zagrożeniami
Aby przygotować subskrypcję dla usługi Lookout MTP, pomoc techniczna firmy Lookout (enterprisesupport@lookout.com) potrzebuje następujących informacji na temat subskrypcji usługi Azure Active Directory (Azure AD). 

* **Identyfikator dzierżawy usługi Azure AD**
* **Identyfikator obiektu grupy usługi Active AD** dla **pełnego** dostępu do konsoli usługi Lookout MTP
* **Identyfikator obiektu grupy usługi Active AD** dla **ograniczonego** dostępu do konsoli usługi Lookout MTP (opcjonalnie)

Użyj poniższej sekcji w celu zebrania informacji potrzebnych do przekazania zespołowi pomocy technicznej firmy Lookout.  

## Uzyskiwanie informacji z usługi Azure AD
### Identyfikator dzierżawy usługi Azure AD
Zaloguj się do [portalu zarządzania usługi Azure AD](https://manage.windowsazure.com) i wybierz swoją subskrypcję. 

![Zrzut ekranu przedstawiający stronę usługi Azure AD z nazwą dzierżawy](../media/mtp/aad_tenant_name.png) Po wybraniu nazwy subskrypcji wynikowy adres URL zawiera identyfikator subskrypcji.  Jeśli masz problemy ze znalezieniem identyfikatora subskrypcji, zobacz ten [artykuł pomocy technicznej firmy Microsoft](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US), aby uzyskać wskazówki dotyczące znajdowania identyfikatora subskrypcji.   
### Uzyskiwanie identyfikatora grupy usługi Azure AD
Konsola usługi Lookout MTP obsługuje 2 poziomy dostępu:  
* **Pełny dostęp:** administrator usługi Azure AD może utworzyć grupę użytkowników, którzy będą mieć pełny dostęp i opcjonalnie utworzyć grupę użytkowników z ograniczonym dostępem.  Tylko użytkownicy w ramach tych grup będą mogli logować się do **konsoli usługi Lookout MTP**.
* **Ograniczony dostęp:** użytkownicy w tej grupie nie będą mieć dostępu do kilku modułów konsoli usługi Lookout MTP związanych z konfiguracją oraz rejestracją i będą mieć dostęp tylko do odczytu do modułu **Security Policy** (Zasady zabezpieczeń) konsoli usługi Lookout MTP.  

Więcej informacji dotyczących uprawnień znajduje się w witrynie sieci Web [w tym artykule](https://personal.support.lookout.com/hc/en-us/articles/114094105653).

**Identyfikator obiektu grupy** można znaleźć na stronie **Właściwości** grupy w **konsoli zarządzania usługi Azure AD**.

![Zrzut ekranu strony właściwości z wyróżnionym polem Identyfikator grupy](../media/mtp/aad_group_object_id.png)

Po zgromadzeniu tych informacji skontaktuj się z pomocą techniczną firmy Lookout (adres e-mail: enterprisesupport@lookout.com).

Pomoc techniczna firmy Lookout będzie korzystać z kontaktu podstawowego, aby dodać subskrypcję i utworzyć konto przedsiębiorstwa w usłudze Lookout MTP przy pomocy zebranych wcześniej informacji.


## Konfigurowanie subskrypcji przy użyciu usługi Lookout MTP
### Krok 1. Konfigurowanie usługi MTP
Po utworzeniu konta przedsiębiorstwa przez pomoc techniczną możesz zalogować się do konsoli usługi Lookout MTP.   Do głównej osoby kontaktowej w firmie zostanie wysłana wiadomość e-mail zawierająca link do adresu URL logowania: https://aad.lookout.com/les?action=consent

Podczas pierwszego logowania do konsoli usługi Lookout MTP należy użyć konta użytkownika w roli administratora globalnego usługi Azure AD. Jest to czynność wymagana przez usługę Lookout MTP, aby móc zarejestrować dzierżawę usługi Azure AD.   Kolejne logowanie nie będzie wymagało od użytkownika posiadania tego poziomu uprawnień dla usługi Azure AD.  Podczas pierwszego logowania pojawi się strona zgody użytkownika. Wybierz przycisk **Accept** (Akceptuj) w celu ukończenia rejestracji.

![Zrzut ekranu strony pierwszego logowania do konsoli aplikacji Lookout MTP](../media/mtp/lookout_mtp_initial_login.png) Po zaakceptowaniu i wyrażeniu zgody nastąpi przekierowanie do konsoli usługi Lookout MTP. Po wstępnej rejestracji kolejne logowania można wykonać przy użyciu adresu URL: https://aad.lookout.com

Jeśli wystąpią problemy podczas logowania, zobacz [artykuł na temat rozwiązywania problemów](https://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration).

Następne kroki opisują zadania, które muszą być wykonane w celu ukończenia konfiguracji usługi Lookout MTP w ramach [konsoli usługi Lookout MTP](https://aad.lookout.com).

### Krok 2. Konfigurowanie łącznika usługi Intune

1.  W konsoli usługi Lookout MTP przejdź do modułu **System** (System), wybierz kartę **Connectors** (Łączniki), a następnie wybierz pozycję **Intune** (Intune).

  ![Zrzut ekranu konsoli usługi Lookout MTP z otwartą kartą łączników i wyróżnioną opcją Intune](../media/mtp/lookout_mtp_setup-intune-connector.png)

2.  W opcji ustawienia połączenia skonfiguruj częstotliwość pulsu w minutach.  Łącznik usługi Intune będzie gotowy.  

  ![Zrzut ekranu przedstawiający kartę ustawień połączenia i skonfigurowaną częstotliwość pulsu](../media/mtp/lookout-mtp-connection-settings.png)

### Krok 3. Konfigurowanie grup rejestracji
W opcji **Enrollment Management** (Zarządzanie rejestracją) zdefiniuj zestaw użytkowników, których urządzenia powinny być zarejestrowane w usłudze Lookout. Najlepszym rozwiązaniem jest rozpoczęcie testowania od małej grupy użytkowników i zapoznanie się z działaniem integracji.  Jeśli testy okażą się satysfakcjonujące, można rozszerzyć rejestrację o dodatkowe grupy użytkowników.

Aby rozpocząć pracę z grupami rejestracji, należy najpierw zdefiniować grupę zabezpieczeń usługi Azure AD, która może stać się pierwszym zestawem użytkowników do zarejestrowania w usłudze Lookout MTP. Po utworzeniu grupy w usłudze Azure AD dla konsoli usługi Lookout MTP przejdź do opcji **Enrollment Management** (Zarządzanie rejestracją) i dodaj grupę zabezpieczeń **Display Name(s)** (Nazwy wyświetlane) usługi Azure AD w celu przeprowadzenia rejestracji.

Jeśli użytkownik znajduje się w grupie rejestracji, wszystkie jego urządzenia, które zostały zidentyfikowane w usłudze Azure AD i są przez nią obsługiwane, zostają zarejestrowane i uprawnione do aktywacji w usłudze Lookout MTP.  Przy pierwszym otwarciu aplikacji Lookout for Work na obsługiwanym urządzeniu jest ono aktywowane w usłudze Lookout MTP.
![Zrzut ekranu strony rejestracji łącznika usługi Intune](../media/mtp/lookout-mtp-enrollment.png)

Najlepszym rozwiązaniem jest użycie domyślnej wartości (5 minut) określającej, ile czasu ma upłynąć między kolejnymi próbami wykrywania nowego urządzenia.

>[!IMPORTANT]
> Wyświetlana nazwa uwzględnia wielkość liter.  Użyj wartości **Nazwa wyświetlana**, jak pokazano na stronie **Właściwości** grupy zabezpieczeń w witrynie Azure Portal. Zwróć uwagę, że na poniższej ilustracji, która przedstawia stronę **Właściwości** grupy zabezpieczeń, wartość Nazwa wyświetlana ma format CamelCase.  Jednak tytuł jest wyświetlany małymi literami i nie powinien być wprowadzany do konsoli usługi Lookout MTP.
>![Zrzut ekranu przedstawiający witrynę Azure Portal, usługę Azure Active Directory i stronę właściwości](../media/mtp/aad-group-display-name.png)

Obecna wersja ma następujące ograniczenia:  
* Nie ma możliwości weryfikacji nazw wyświetlanych grupy.  Upewnij się, że została użyta wartość pola **NAZWA WYŚWIETLANA** widoczna w witrynie Azure Portal dla grupy zabezpieczeń usługi Azure AD.
* Tworzenie grupy w ramach innej grupy nie jest obecnie obsługiwane.  Podane grupy zabezpieczeń usługi Azure AD mogą zawierać tylko użytkowników, a nie grupy zagnieżdżone.


### Krok 4. Konfigurowanie synchronizacji stanu
W opcji **State Sync** (Synchronizacja stanu) określ typ danych, które powinny być przesyłane do usługi Intune.  Obecnie należy włączyć zarówno stan urządzeń, jak i stan zagrożenia, aby integracja usług Lookout i Intune działała prawidłowo.  Oba są domyślnie włączone.
### Krok 5. Konfigurowanie informacji o adresie e-mail odbiorcy raportów o błędach
W opcji **Error Management** (Zarządzanie błędami) wpisz adres e-mail, na który mają być wysyłane raporty o błędach.

![Zrzut ekranu strony zarządzania błędami łącznika usługi Intune](../media/mtp/lookout-mtp-connector-error-notifications.png)

### Krok 6. Konfigurowanie powiadomień e-mail
Jeśli chcesz otrzymywać alerty e-mail dotyczące zagrożeń, zaloguj się do [konsoli usługi Lookout MTP](https://aad.lookout.com) przy użyciu konta użytkownika, który powinien otrzymywać powiadomienia. Na karcie **Preferences** (Preferencje) modułu **System** wybierz żądane powiadomienia i ustaw je na wartość **ON** (Włącz). Zapisz zmiany.

![Zrzut ekranu strony preferencji z wyświetlonym kontem użytkownika](../media/mtp/lookout-mtp-email-notifications.png) Jeśli nie chcesz już otrzymywać powiadomień pocztą e-mail, ustaw wartość **OFF** (Wyłącz) i zapisz zmiany.
### Krok 7. Konfigurowanie klasyfikacji zagrożeń
Usługa Lookout MTP klasyfikuje różne typy zagrożeń dla urządzeń przenośnych. [Klasyfikacje zagrożeń w usłudze Lookout MTP](http://personal.support.lookout.com/hc/en-us/articles/114094130693) mają domyślne poziomy ryzyka, które są z nimi związane. Można je zmienić w dowolnym momencie zależnie od potrzeb firmy.

![Zrzut ekranu przedstawiający stronę zasad wraz z zagrożeniem i klasyfikacjami](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> Poziomy ryzyka, które zostały tutaj określone, są istotnym elementem usługi MTP, ponieważ integracja usługi Intune oblicza zgodność urządzenia na podstawie tych poziomów ryzyka w czasie wykonywania. Innymi słowy administrator usługi Intune ustawia regułę w zasadach, aby uznawać urządzenie za niezgodne, jeśli zawiera ono aktywne zagrożenie, które osiąga poziom ryzyka wysoki, średni lub niski. Obliczanie zgodności urządzenia w usłudze Intune zależy bezpośrednio od zasady klasyfikacji zagrożeń w usłudze MTP.

## Obserwowanie rejestracji
Po zakończeniu konfiguracji usługa Lookout MTP rozpoczyna sondowanie usługi Azure AD pod kątem urządzeń, które odpowiadają określonym grupom rejestracji.  Informacje o zarejestrowanych urządzeniach znajdują się w module Devices (Urządzenia).  Początkowy stan urządzeń jest wyświetlany jako oczekujący.  Stan urządzenia ulega zmianie po zainstalowaniu, otwarciu i aktywowaniu aplikacji Lookout for Work na danym urządzeniu.  Aby uzyskać szczegółowe informacje na temat sposobu wypychania aplikacji Lookout for Work do urządzenia, zobacz temat [Configure and deploy Lookout for work apps](configure-and-deploy-lookout-for-work-apps.md) (Konfigurowanie i wdrażanie aplikacji Lookout for Work).
## Następne kroki
[Włączanie połączenia Lookout MTP dla usługi Intune](enable-lookout-mtp-connection-in-intune.md)



<!--HONumber=Sep16_HO3-->

