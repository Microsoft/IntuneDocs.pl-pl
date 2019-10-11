---
title: Co to jest Microsoft Intune
description: Dowiedz się, jak usługa Microsoft Intune pełni rolę składnika zarządzania urządzeniami przenośnymi (MDM, mobile device management) i zarządzania aplikacjami mobilnymi (MAM, mobile app management) rozwiązania Enterprise Mobility + Security oraz jak pomaga w ochronie danych firmy.
keywords: co to jest usługa Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/20/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0ba46314a7c44e8db89d11a2866c86375a4cdfd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726183"
---
# <a name="what-is-microsoft-intune"></a>Co to jest usługa Microsoft Intune?

Microsoft Intune to oparta na chmurze usługa zarządzania mobilnością w przedsiębiorstwie (EMM, enterprise mobility management) ułatwiająca pracownikom utrzymanie produktywności przy jednoczesnej ochronie danych firmy. Podobnie jak inne usługi platformy Azure, usługa Microsoft Intune jest dostępna w witrynie Azure Portal. Usługa Intune umożliwia:

- zarządzanie urządzeniami przenośnymi i komputerami używanymi przez pracowników do uzyskiwania dostępu do danych firmowych,
- zarządzanie aplikacjami mobilnymi używanymi przez pracowników,
- chronienie danych firmowych poprzez kontrolowanie sposobu, w jaki pracownicy uzyskują do nich dostęp i udostępniają je,
- zapewnienie zgodności urządzeń i aplikacji z wymaganiami firmy dotyczącymi bezpieczeństwa.

## <a name="common-business-problems-that-intune-helps-solve"></a>Typowe problemy biznesowe, które pomaga rozwiązywać usługa Intune

- [Zabezpieczanie lokalnej poczty e-mail i danych na potrzeby uzyskiwania dostępu przez urządzenia przenośne](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
- [Zabezpieczanie poczty e-mail i danych w usłudze Office 365 na potrzeby uzyskiwania bezpiecznego dostępu przez urządzenia przenośne](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
- [Wydawanie firmowych telefonów pracownikom](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
- [Oferowanie programu „Przynieś własne urządzenie” (BYOD, bring your own device) lub urządzeń osobistych wszystkim pracownikom](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
- [Umożliwianie pracownikom bezpiecznego dostępu do usługi Office 365 z niezarządzanego kiosku publicznego](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
- [Wydawanie wspólnych tabletów do ograniczonego użytku pracownikom wykonującym zadania](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="how-does-intune-work"></a>Jak działa usługa Intune?

Usługa Intune jest składnikiem pakietu Enterprise Mobility + Security (EMS) firmy Microsoft, który zarządza urządzeniami przenośnymi i aplikacjami mobilnymi. Usługa ta jest ściśle zintegrowana z innymi składnikami pakietu EMS, np. usługą Azure Active Directory (Azure AD), która umożliwia kontrolowanie tożsamości i dostępu, oraz usługą Azure Information Protection na potrzeby ochrony danych. Używając jej wraz z usługą Office 365, możesz zapewnić produktywność pracowników na wszystkich urządzeniach, z których korzystają, przy jednoczesnym zachowaniu bezpieczeństwa informacji należących do organizacji.

![Obraz architektury usługi Intune](./media/what-is-intune/intunearch_sm.png)

Wyświetl [powiększony](./media/intunearchitecture.svg) diagram architektury usługi Intune.

Sposób użycia funkcji zarządzania urządzeniami i aplikacjami usługi Intune oraz ochrony danych pakietu EMS zależy od [problemu biznesowego, który próbujesz rozwiązać](#common-business-problems-that-intune-helps-solve). Przykład:
* Funkcja zarządzania urządzeniami znajdzie zastosowanie przy tworzeniu puli urządzeń współdzielonych przez pracowników zmianowych w sklepie detalicznym.
* Funkcja zarządzania aplikacjami i ochrona danych jest przydatna w sytuacji, gdy pracownicy uzyskują dostęp do danych firmowych za pomocą urządzeń osobistych (Przynieś własne urządzenie).  
* Będziesz polegać na wszystkich tych technologiach, jeśli wydajesz telefony firmowe pracownikom przetwarzającym informacje.

## <a name="intune-device-management-explained"></a>Objaśnienie funkcji zarządzania urządzeniami usługi Intune
Funkcja zarządzania urządzeniami usługi Intune działa przy użyciu protokołów lub interfejsów API, które są dostępne w systemach operacyjnych urządzeń przenośnych. Obejmuje takie zadania jak:
* Rejestrowanie urządzeń do zarządzania, aby dział IT miał spis urządzeń uzyskujących dostęp do usług firmowych
* Konfigurowanie urządzeń w celu upewnienia się, że spełniają standardy firmy dotyczące kondycji i zabezpieczeń
* Dostarczanie certyfikatów i profilów sieci Wi-Fi/VPN w celu uzyskania dostępu do usług firmowych
* Raportowanie i pomiar zgodności urządzenia ze standardami firmy
* Usuwanie danych firmowych z zarządzanych urządzeń  

Niektórzy sądzą, że **kontrolowanie dostępu do danych firmowych** jest funkcją zarządzania urządzeniami. Nie należy myśleć o tym w ten sposób, ponieważ to nie jest funkcja dostarczana przez system operacyjny urządzeń przenośnych. Jest to raczej funkcja dostarczana przez dostawcę tożsamości. W tym przypadku dostawcą tożsamości jest usługa Azure Active Directory (Azure AD) — system zarządzania dostępem i tożsamością firmy Microsoft.  

Usługa Intune integruje się z usługą Azure AD, aby udostępnić szeroką gamę scenariuszy kontroli dostępu. Na przykład można wymagać, aby przed uzyskaniem dostępu do usług firmowych, takich jak program Exchange, urządzenie przenośne spełniało standardy firmy zdefiniowane w usłudze Intune. Podobnie można zablokować dostęp do usług firmowych określonemu zestawowi aplikacji mobilnych. Na przykład można zablokować usługę Exchange Online tak, aby dostęp do niej był możliwy tylko za pomocą programu Outlook lub Outlook Mobile.

## <a name="intune-app-management-explained"></a>Objaśnienie funkcji zarządzania aplikacjami usługi Intune
Zarządzanie aplikacjami obejmuje następujące możliwości:
* Przypisywanie aplikacji mobilnych dla pracowników
* Konfigurowanie standardowych ustawień aplikacji, które są używane po jej uruchomieniu
* Kontrolowanie sposobu używania i udostępniania danych firmowych w aplikacjach mobilnych
* Usuwanie danych firmowych z aplikacji mobilnych   
* Aktualizowanie aplikacji
* Raportowanie dotyczące spisu aplikacji mobilnych
* Śledzenie użycia aplikacji mobilnej

Termin „zarządzanie aplikacjami mobilnymi” jest często używany jako oznaczenie jednej z powyższych czynności lub konkretnej ich kombinacji. Szczególnie powszechne jest łączenie koncepcji konfiguracji aplikacji z koncepcją zabezpieczania danych firmowych w aplikacjach mobilnych. Wynika to z faktu, że niektóre aplikacje mobilne uwidaczniają ustawienia, które umożliwiają skonfigurowanie funkcji zabezpieczeń danych.

Omawiając konfigurację aplikacji i usługę Intune, odnosimy się w szczególności do technologii takich jak [konfiguracja aplikacji zarządzanych w systemie iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Korzystając z usługi Intune w połączeniu z innymi usługami pakietu EMS, możesz zapewnić swojej organizacji lepsze bezpieczeństwo aplikacji mobilnych niż to dostarczane przez system operacyjny urządzeń przenośnych i same aplikacje mobilne za pośrednictwem konfiguracji aplikacji. Aplikacja zarządzana za pomocą pakietu EMS ma dostęp do szerszego zakresu funkcji zabezpieczeń aplikacji mobilnych i danych, który obejmuje następujące funkcje:

* [Logowanie jednokrotne](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
* [Uwierzytelnianie wieloskładnikowe](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [Warunkowy dostęp do aplikacji — dostęp jest możliwy, jeśli aplikacja mobilna zawiera dane firmy](../protect/app-based-conditional-access-intune.md)
* [Izolowanie danych firmowych od danych osobistych w ramach tej samej aplikacji](../apps/app-protection-policy.md)
* [Zasady ochrony aplikacji (numer PIN, szyfrowanie, funkcja „Zapisz jako”, schowek itp.)](../apps/app-protection-policies.md)
* [Czyszczenie danych firmowych z aplikacji mobilnej](../apps/apps-selective-wipe.md)
* [Obsługę usługi Rights Management](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Obraz zawierający poziomy zabezpieczeń danych zarządzania aplikacją](./media/what-is-intune/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Bezpieczeństwo aplikacji w usłudze Intune
Zapewnianie bezpieczeństwa aplikacji stanowi element zarządzania aplikacjami. Omawiając bezpieczeństwo aplikacji mobilnych w usłudze Intune, odnosimy się do następujących czynności:
* Przechowywanie informacji osobistych z dala od informatycznych danych firmowych
* Ograniczanie działań, jakie mogą podjąć użytkownicy wobec informacji firmowych, na przykład kopiowania, wycinania, wklejania, zapisywania i wyświetlania
* Usuwanie danych firmy z aplikacji mobilnych, nazywane również selektywnym czyszczeniem lub czyszczeniem firmowym

Jednym ze sposobów zapewniania bezpieczeństwa aplikacji mobilnych przez usługę Intune jest użycie funkcji **zasad ochrony aplikacji**. Zasady ochrony aplikacji wykorzystują tożsamość usługi Azure AD do izolowania danych firmowych od danych osobistych. Dane, do których dostęp jest uzyskiwany za pomocą poświadczeń firmowych, zostaną objęte dodatkowymi zabezpieczeniami firmowymi.

Gdy na przykład użytkownik loguje się do swojego urządzenia za pomocą poświadczeń firmowych, jego tożsamość firmowa umożliwia mu uzyskanie dostępu do danych, do których dostęp przy użyciu tożsamości osobistej nie jest możliwy. Podczas używania danych firmowych zasady ochrony aplikacji kontrolują sposób ich zapisywania i udostępniania. Te zabezpieczenia nie są stosowane względem danych, do których użytkownik uzyskuje dostęp, logując się do urządzenia za pomocą tożsamości osobistej. W ten sposób dział IT sprawuje kontrolę nad danymi firmowymi, a użytkownik końcowy kontroluje swoje dane osobiste i utrzymuje ich prywatność.

## <a name="emm-with-and-without-device-enrollment"></a>Usługa EMM z rejestracją urządzenia i bez niej
Większość rozwiązań do zarządzania mobilnością w przedsiębiorstwie obsługuje podstawowe technologie związane z urządzeniami przenośnymi i aplikacjami mobilnymi. Są one zazwyczaj powiązane z urządzeniami, które zostały zarejestrowane w rozwiązaniu do zarządzania urządzeniami przenośnymi organizacji. Usługa Intune obsługuje te scenariusze, a dodatkowo obsługuje wiele scenariuszy „bez rejestracji”.  

Organizacje różnią się pod względem zakresu, w jakim przyjmują scenariusze „bez rejestracji”. Niektóre organizacje standaryzują ten scenariusz. Niektóre dopuszczają go na urządzeniach towarzyszących, takich jak tablety osobiste. Inne w ogóle go nie obsługują. Nawet w ostatnim przypadku, w którym organizacja wymaga, aby wszystkie urządzenia pracowników były zarejestrowane w rozwiązaniu MDM, zwykle obsługują one scenariusze „bez rejestracji” na potrzeby podwykonawców, dostawców i innych urządzeń objętych specjalnym zwolnieniem.

Technologia „bez rejestracji” usługi Intune może być nawet używana na zarejestrowanych urządzeniach. Urządzenie zarejestrowane w rozwiązaniu MDM może mieć na przykład zabezpieczenia typu „Otwórz w” dostarczone przez system operacyjny urządzenia przenośnego. Ochrona pozycji „Otwórz w” to funkcja systemu iOS firmy Apple, która uniemożliwia otwarcie dokumentu z jednej aplikacji, takiej jak program Outlook, w innej aplikacji, takiej jak program Word. Wyjątek stanowi sytuacja, w której obie aplikacje są zarządzane przez tego samego dostawcę rozwiązania MDM. Ponadto dział IT może stosować zasady ochrony aplikacji względem aplikacji mobilnych zarządzanych przez pakiet EMS w celu kontrolowania funkcji „Zapisz jako” oraz udostępniania uwierzytelniania wieloskładnikowego.

Niezależnie od stanowiska organizacji względem zarejestrowanych i niezarejestrowanych urządzeń przenośnych oraz aplikacji mobilnych usługa Intune, jako część pakietu EMS, dysponuje narzędziami, które pomagają zwiększyć produktywność pracowników przy jednoczesnej ochronie danych firmowych.

## <a name="microsoft-intune-in-the-azure-portal"></a>Usługa Microsoft Intune w witrynie Azure Portal

Usługę Microsoft Intune można znaleźć w witrynie [Azure Portal](https://portal.azure.com).

Najważniejsze funkcje środowiska usługi Microsoft Intune w witrynie Azure Portal obejmują:

- Zintegrowana konsola dla wszystkich składników Enterprise Mobility + Security (EMS)
- Konsola oparta na języku HTML, skonstruowana zgodnie ze standardami sieci Web
- Obsługa interfejsu API programu Microsoft Graph w celu zautomatyzowania wielu działań
- Grupy usługi Azure Active Directory (AD) w celu zapewnienia zgodności wszystkich aplikacji Azure
- Obsługa większości nowoczesnych przeglądarek sieci Web

Aby uzyskać krótki przewodnik po dostosowywaniu środowiska portalu, zobacz [Wprowadzenie do usługi Intune w witrynie Azure Portal](tutorial-walkthrough-intune-portal.md).

> [!NOTE]
> Jeśli używano poprzedniej wersji usługi Microsoft Intune, przydatne mogą być następujące informacje:
> * [Dokąd została przeniesiona funkcja usługi Intune na platformie Azure?](../ui-changes.md) to artykuł, w którym można znaleźć opis określonych przepływów pracy i interfejsów użytkownika, które zmieniły się wraz z przejściem na platformę Azure.
> * [Klasyczne grupy usługi Intune w witrynie Azure Portal](groups-get-started.md) to artykuł, w którym opisano wpływ przejścia do grup zabezpieczeń usługi Azure Active Directory na potrzeby zarządzania grupami.

### <a name="before-you-start"></a>Przed rozpoczęciem

Aby skorzystać z usługi Intune w portalu Azure Portal, musisz mieć konto administratora i konto dzierżawy usługi Intune. [Utwórz konto](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20), jeśli jeszcze go nie masz.

### <a name="supported-web-browsers-for-the-azure-portal"></a>Obsługiwane przeglądarki internetowe w portalu Azure

Portal Azure działa na większości współczesnych komputerów osobistych, komputerów Mac i tabletów. Telefony komórkowe nie są obsługiwane.
Obecnie obsługiwane są następujące przeglądarki:

- Microsoft Edge (najnowsza wersja)
- Microsoft Internet Explorer 11
- Safari (najnowsza wersja, tylko Mac)
- Chrome (najnowsza wersja)
- Firefox (najnowsza wersja)

Sprawdź najnowsze informacje o obsługiwanych przeglądarkach w witrynie [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="next-steps"></a>Następne kroki
* Przeczytaj o pewnych [typowych sposobach korzystania z usługi Intune](common-scenarios.md).
* Zapoznaj się z produktem, korzystając [z 30-dniowej wersji próbnej usługi Intune](free-trial-sign-up.md).
* Poznaj [wymagania techniczne i możliwości](supported-devices-browsers.md) usługi Intune.