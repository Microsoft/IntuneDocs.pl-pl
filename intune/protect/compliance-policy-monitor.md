---
title: Monitorowanie zasad zgodności urządzeń w usłudze Microsoft Intune — Azure | Microsoft Docs
description: Pulpit nawigacyjny zgodności urządzeń służy do monitorowania ogólnej zgodności urządzeń, wyświetlania raportów i wyświetlania zgodności urządzeń z poszczególnymi zasadami i ustawieniami.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05a4b6cac61bf7dc76ba80862d562e93dadbd533
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721516"
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorowanie zasad zgodności urządzeń Intune

Raporty zgodności pomagają w weryfikowaniu zgodności urządzeń oraz rozwiązywaniu problemów związanych ze zgodnością w organizacji. Korzystanie z tych raportów zapewnia następujące informacje:

- Ogólny stan zgodności urządzeń
- Stan zgodności poszczególnych ustawień
- Stan zgodności poszczególnych zasad
- Przechodzenie do szczegółów dotyczących poszczególnych urządzeń w celu wyświetlenia konkretnych ustawień i zasad wpływających na te urządzenia

## <a name="open-the-compliance-dashboard"></a>Otwieranie pulpitu nawigacyjnego zgodności

Otwórz **pulpit nawigacyjny zgodności urządzeń w usłudze Intune**:

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Wybierz pozycję **Zgodność urządzenia** > **Przegląd**. Zostanie otwarty **pulpit nawigacyjny zgodności urządzeń**.

> [!IMPORTANT]
> Aby otrzymać zasady zgodności urządzeń, urządzenia muszą być zarejestrowane w usłudze Intune.

## <a name="dashboard-overview"></a>Pulpit nawigacyjny — omówienie

Po otwarciu pulpitu nawigacyjnego możesz uzyskać omówienie zawierające wszystkie raporty zgodności. W tych raportach możesz zobaczyć i sprawdzić następujące elementy:

- Ogólna zgodność urządzenia
- Zgodność urządzeń wg zasady
- Zgodność urządzeń wg ustawienia
- Stan ochrony urządzenia
- Stan agenta zagrożeń

![Obraz pulpitu nawigacyjnego przedstawiający pulpit nawigacyjny zgodności urządzeń oraz różne raporty](./media/compliance-policy-monitor/idc-1.png)

Podczas przechodzenia do szczegółów raportów możesz też zobaczyć konkretne zasady zgodności i ustawienia mające zastosowanie do określonego urządzenia, w tym stan zgodności dla każdego ustawienia.

### <a name="device-compliance-status-report"></a>Raport stanu zgodności urządzenia

Wykres przedstawia stany zgodności dla wszystkich urządzeń zarejestrowanych w usłudze Intune. Stany zgodności urządzeń są przechowywane w dwóch różnych bazach danych: Intune i Azure Active Directory. 

> [!IMPORTANT]
> Usługa Intune wykonuje wszystkie oceny zgodności na urządzeniu zgodnie z jego harmonogramem ewidencjonowania. [Dowiedz się więcej o harmonogramie ewidencjonowania urządzenia](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Opisy różnych stanów zasad zgodności urządzeń:

- **Zgodne**: urządzenie pomyślnie zastosowało co najmniej jedno ustawienie zasady zgodności urządzenia.

- **Okres prolongaty:** urządzenie jest urządzeniem docelowym dla co najmniej jednego ustawienia zasad zgodności urządzeń. Jednak użytkownik jeszcze nie zastosował zasad. Oznacza to, że urządzenie nie jest zgodne, ale jest w okresie prolongaty zdefiniowanym przez administratora.

  - Dowiedz się więcej o [akcjach dla niezgodnych urządzeń](actions-for-noncompliance.md).

- **Nie oceniono**: wstępny stan dla nowo zarejestrowanych urządzeń. Inne możliwe przyczyny tego stanu to między innymi:

  - Urządzenia, którym nie przypisano zasad zgodności i które nie mają wyzwalacza umożliwiającego sprawdzenie zgodności
  - Urządzenia, które nie zostały zaewidencjonowane od momentu ostatniej aktualizacji zasad zgodności
  - Urządzenia nieskojarzone z określonym użytkownikiem, takie jak:
    - Urządzenia z systemem iOS zakupione w ramach programu Device Enrollment Program (DEP) firmy Apple bez koligacji użytkownika
    - Urządzenia kiosku systemu Android lub dedykowane urządzenia z systemem Android Enterprise
  - Urządzenia zarejestrowane przy użyciu konta menedżera rejestracji urządzeń (DEM)

- **Niezgodne:** urządzenie nie zastosowało pomyślnie co najmniej jednego ustawienia zasad zgodności urządzenia. Lub użytkownik nie zapewnił zgodności z zasadami.

- **Urządzenie nie jest zsynchronizowane:** urządzenie nie zgłosiło stanu zasad zgodności urządzenia z jednej z następujących przyczyn:

  - **Nieznane**: urządzenie jest w trybie offline lub nie nawiązało łączności z usługą Intune lub Azure AD z innych przyczyn.

  - **Błąd**: urządzenie nie skomunikowało się z usługami Intune i Azure AD i otrzymało komunikat o błędzie wraz z powodem.

> [!IMPORTANT]
> Urządzenia, które są zarejestrowane w usłudze Intune, ale nie są objęte żadnymi zasadami zgodności urządzeń, są uwzględnione w raporcie w obszarze **Zgodne**.

#### <a name="drill-down-for-more-details"></a>Przechodzenie do szczegółów

Na wykresie **Stan zgodności urządzenia** wybierz stan. Na przykład wybierz stan **Niezgodne**:

![Wybieranie stanu braku zgodności](./media/compliance-policy-monitor/select-not-compliant-status.png)

Opcja umożliwia wyświetlenie bardziej szczegółowych informacji dotyczących urządzeń w tym stanie, w tym platformy systemu operacyjnego, daty ostatniego zameldowania i innych. 

![Obraz pulpitu nawigacyjnego przedstawiający bardziej szczegółowe informacje dotyczące urządzenia w określonym stanie](./media/compliance-policy-monitor/drill-down-details.png)

Jeśli chcesz zobaczyć wszystkie urządzenia stanowiące własność konkretnego użytkownika, możesz też filtrować raport z wykresem poprzez wpisanie adresu e-mail użytkownika.

#### <a name="filter-and-columns"></a>Filtr i kolumny

![Wybierz opcje Filtr i Kolumna, aby zmienić wyniki na wykresie](./media/compliance-policy-monitor/filter-columns.png)

Po wybraniu przycisku **Filtr** zostanie otworzone okno z większą liczbą opcji, w tym stanem zgodności, urządzeniami ze zdjętymi zabezpieczeniami systemu i innymi. **Zastosuj** filtr, aby zaktualizować wyniki.

Użyj właściwości **Kolumny**, aby dodać lub usunąć kolumny z danych wyjściowych wykresu. Przykładowo **Główna nazwa użytkownika** może pokazywać adres e-mail zarejestrowany na urządzeniu. **Zastosuj** kolumny, aby zaktualizować wyniki.

#### <a name="device-details"></a>Szczegóły urządzenia

Na wykresie wybierz konkretne urządzenie, a następnie wybierz opcję **Zgodność urządzenia**:

![Wybierz konkretne urządzenie, a następnie wybierz opcję Zgodność urządzenia, aby zobaczyć zastosowane zasady zgodności](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

Dzięki temu jest dostępnych więcej szczegółów dotyczących ustawienia zasad zgodności urządzenia zastosowanego na danym urządzeniu. Po wybraniu określonych zasad zostaną wyświetlone wszystkie ustawienia w zasadach.

### <a name="devices-without-compliance-policy"></a>Urządzenia bez zasad zgodności
W pozycji **Zgodność urządzenia** > **Omówienie** raport wskazuje również urządzenia, które nie mają przypisanych żadnych zasad zgodności:

![Wyświetlanie urządzeń bez żadnych zasad zgodności](./media/compliance-policy-monitor/devices-without-policies.png)

Po wybraniu kafelka zostaną wyświetlone wszystkie urządzenia bez zasad zgodności. Ponadto opcja pokazuje użytkownika urządzenia, stan wdrożenia zasad oraz model urządzenia.

#### <a name="what-you-need-to-know"></a>Co musisz wiedzieć

- W przypadku ustawienia zabezpieczeń **Oznaczaj urządzenia bez przypisanych zasad zgodności jako** należy zidentyfikować urządzenia bez zasad zgodności. Następnie możesz im przypisać co najmniej jedne zasady zgodności.

  Ustawienie zabezpieczeń można skonfigurować w portalu usługi Intune. Wybierz pozycję **Zgodność urządzenia** > **Ustawienia zasad zgodności**. Następnie ustaw opcję **Oznaczaj urządzenia bez przypisanych zasad zgodności jako** na wartość **Zgodne** lub **Niezgodne**. 

  Dowiedz się więcej o tym [ulepszeniu zabezpieczeń w usłudze Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Użytkownicy z przypisanymi zasadami zgodności dowolnego typu nie są wyświetlani w raporcie, niezależnie od platformy urządzeń. Jeśli na przykład przypiszesz zasady zgodności systemu Windows do użytkownika z systemem Android, urządzenie nie zostanie ujęte w raporcie. Jednak usługa Intune uzna urządzenie z systemem Android za niezgodne. Aby uniknąć problemów, firma Microsoft zaleca utworzenie zasad dla każdej platformy urządzeń i wdrożenie ich do wszystkich użytkowników.

### <a name="per-policy-device-compliance-report"></a>Raport zgodności urządzeń wg zasady

Raport **Zgodność urządzenia** > **Zgodność z zasadami** przedstawia zasady oraz liczbę zgodnych i niezgodnych urządzeń. 

![Wyświetlanie listy zasad oraz liczby urządzeń zgodnych i niezgodnych z tymi zasadami](./media/compliance-policy-monitor/idc-8.png)

Po wybraniu określonych zasad możesz zobaczyć **stan zgodności**, **alias e-mail użytkownika**, **model urządzenia** oraz **lokalizację** dla każdego urządzenia objętego danymi zasadami zgodności.

## <a name="setting-compliance-report"></a>Raport o zgodności ustawień

Raport **Zgodność urządzenia** > **Zgodność ustawienia** przedstawia łączną liczbę urządzeń znajdujących się w poszczególnych stanach zgodności dla każdego ustawienia zgodności. Pokazuje wszystkie ustawienia zasad zgodności urządzeń ze wszystkich zasad zgodności, platformy, dla których zastosowano ustawienia zasad, a także liczbę niezgodnych urządzeń.

![Wyświetlanie listy wszystkich urządzeń w różnych zasadach](./media/compliance-policy-monitor/idc-10.png)

Po wybraniu określonego ustawienia możesz zobaczyć **stan zgodności**, **alias e-mail użytkownika**, **model urządzenia** oraz **lokalizację** dla każdego urządzenia objętego danym ustawieniem.

> [!NOTE]
> Zasady można przypisać do urządzenia i użytkownika na tym samym urządzeniu. W niektórych scenariuszach urządzenie może zostać zsynchronizowane przed zalogowaniem użytkownika, na przykład po ponownym uruchomieniu urządzenia. Może nastąpić ocena zgodności tego użytkownika i wyświetlenie urządzenia jako niezgodnego. Takie zachowanie może również wyświetlać konto systemowe jako niezgodnego użytkownika.
>
> Jest to znany problem dotyczący urządzeń z systemem Windows 10 z obsługą wielu użytkowników. Wszelkie zmiany i aktualizacje dotyczące tego zachowania są ogłaszane w sekcjach dotyczących [rozwiązań w trakcie opracowywania](../fundamentals/in-development.md) i/lub [nowości](../fundamentals/whats-new.md).

## <a name="view-status-of-device-policies"></a>Wyświetlanie stanu zasad dotyczących urządzenia

Różne stany zasad można sprawdzać według platformy. Na przykład masz zasady zgodności systemu macOS. Chcesz wyświetlić urządzenia, na które wpływają te zasady, i dowiedzieć się, czy występują konflikty lub błędy.

Ta funkcja jest uwzględniana w obszarze raportowania stanu urządzenia:

1. Wybierz kolejno pozycje **Zgodność urządzenia** > **Zasady**. Zostanie wyświetlona lista zasad, w tym platforma, informacja o przypisaniu zasad i dalsze szczegóły.
2. Wybierz zasadę > **Omówienie**. W tym widoku przypisanie zasad uwzględnia następujące stany:

    - Powodzenie: zasady zostały zastosowane.
    - Błąd: nie można zastosować zasad. Ten komunikat jest przeważnie wyświetlany z kodem błędu stanowiącym link do wyjaśnienia. 
    - Konflikt: na tym samym urządzeniu zostały zastosowane dwa ustawienia, a usługa Intune nie może rozwiązać konfliktu. Administrator powinien zapoznać się z tą sytuacją.
    - Oczekuje: urządzenie nie zostało jeszcze zaewidencjonowane w usłudze Intune w celu odebrania zasad. 
    - Nie dotyczy: urządzenie nie może odebrać zasad. Na przykład zasady aktualizują ustawienie specyficzne dla systemu iOS 11.1, ale urządzenie używa systemu iOS 10. 

3. Aby wyświetlić szczegóły urządzeń używających danych zasad, wybierz jeden z stanów. Na przykład wybierz pozycję **Powodzenie**. W następnym oknie jest wyświetlana lista szczegółów określonego urządzenia, w tym nazwa i stan jego wdrażania.

## <a name="how-intune-resolves-policy-conflicts"></a>Jak są rozwiązywane konflikty zasad usługi Intune
Konflikty zasad mogą wystąpić, gdy na urządzeniu stosuje się wiele zasad usługi Intune. Jeśli ustawienia zasad nakładają się na siebie, usługa Intune rozwiązuje konflikty, używając następujących reguł:

- Jeżeli sprzeczne ustawienia pochodzą z zasad konfiguracji usługi Intune i zasad zgodności, ustawienia w zasadach zgodności mają pierwszeństwo względem ustawień w zasadach konfiguracji. Dzieje się tak nawet wtedy, gdy ustawienia w zasadach konfiguracji są bardziej bezpieczne.

- Jeśli wdrożono wiele zasad zgodności, usługa Intune używa najbezpieczniejszych z nich.