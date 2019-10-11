---
title: Dodawanie identyfikatorów firmy do usługi Intune
titleSuffix: ''
description: Informacje dotyczące dodawania identyfikatorów urządzeń firmowych (metody rejestracji, numerów IMEI i numerów seryjnych) do usługi Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac86e9155f08683ab073ae0b46ea3f2780060c90
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723349"
---
# <a name="identify-devices-as-corporate-owned"></a>Określanie urządzeń jako firmowe

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Jako administrator usługi Intune możesz określić urządzenia jako należące do firmy, aby doprecyzować zarządzanie i identyfikację. Usługa Intune może wykonywać dodatkowe zadania zarządzania i zbierać dodatkowe informacje, takie jak pełny numer telefonu i spis aplikacji z urządzeń należących do firmy. Można również ustawić ograniczenia urządzenia, aby zablokować rejestrację przez urządzenia, które nie należą do firmy.

Podczas rejestracji usługa Intune automatycznie przypisuje stan „należące do firmy” do urządzeń spełniających następujące warunki:

- Zarejestrowano je przy użyciu konta [menedżera rejestracji urządzeń](device-enrollment-manager-enroll.md) (wszystkie platformy)
- Zarejestrowano je przy użyciu programu [Device Enrollment Program](device-enrollment-program-enroll-ios.md) firmy Apple lub przy użyciu narzędzi [Apple School Manager](apple-school-manager-set-up-ios.md) albo [Apple Configurator](apple-configurator-enroll-ios.md) (tylko system iOS)
- [Zidentyfikowano je jako należące do firmy przed zarejestrowaniem](#identify-corporate-owned-devices-with-imei-or-serial-number) przy użyciu międzynarodowego identyfikatora urządzenia przenośnego (IMEI) (wszystkie platformy z numerami IMEI) lub numeru seryjnego (system iOS i Android)
- Przyłączono je do usługi Azure Active Directory jako urządzenie z systemem Windows 10 Enterprise
- Na [liście właściwości urządzenia](#change-device-ownership) ustawiono je jako firmowe

Po zarejestrowaniu można [zmieniać ustawienie własności](#change-device-ownership) z **Osobiste** na **Firmowe**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identyfikowanie urządzeń należących do firmy przy użyciu numeru IMEI lub numeru seryjnego

Jako administrator usługi Intune możesz utworzyć i zaimportować plik z wartościami rozdzielanymi przecinkami (CSV) zawierający listę 14-cyfrowych numerów IMEI lub numerów seryjnych. Usługa Intune używa tych identyfikatorów, aby określić własność urządzeń jako firmowe podczas ich rejestracji. Każdy numer IMEI lub numer seryjny może zawierać szczegółowe informacje określone na liście do celów administracyjnych.

Ta funkcja jest obsługiwana na następujących platformach:

| Platforma | Numery IMEI | Numery seryjne |
|---|---|---|
| Windows | Obsługiwane (Windows Phone) | Nieobsługiwane |
| iOS/macOS | Nieobsługiwane | Obsługiwane |
| System operacyjny Android w wersji 10 zarządzany przez administratora urządzenia | Nieobsługiwane | Nieobsługiwane |
| Inne systemy Android | Nieobsługiwane | Obsługiwane |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Dowiedz się, jak znaleźć numer seryjny urządzenia marki Apple](https://support.apple.com/HT204308).<br>
[Dowiedz się, jak znaleźć numer seryjny urządzenia z systemem Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Dodawanie identyfikatorów firmy przy użyciu pliku CSV
Aby utworzyć listę, utwórz listę wartości rozdzielonych przecinkami (.csv) zawierającą dwie kolumny, bez nagłówka. Dodaj 14-cyfrowe numery IMEI lub numery seryjne w lewej kolumnie i szczegółowe informacje w prawej kolumnie. W jednym pliku csv można zaimportować tylko jeden typ identyfikatora: numer IMEI lub numer seryjny. Długość szczegółowych informacji nie może przekraczać 128 znaków. Są one przeznaczone tylko do użytku administracyjnego. Szczegóły nie są wyświetlane na urządzeniu. Aktualne ograniczenie wynosi 5000 wierszy na plik csv.

**Przekaż plik csv zawierający numery seryjne** — utwórz listę wartości rozdzielanych przecinkami (csv) w dwóch kolumnach bez nagłówka i ogranicz listę do 5000 urządzeń lub 5 MB na plik csv.

|||
|-|-|
|&lt;Identyfikator 1&gt;|&lt;Szczegóły urządzenia 1&gt;|
|&lt;Identyfikator 2&gt;|&lt;Szczegóły urządzenia 2&gt;|

Ten plik CSV wyświetlony w edytorze tekstu wygląda następująco:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Niektóre urządzenia z systemem Android i iOS mają wiele numerów IMEI. Usługa Intune odczytuje tylko jeden numer IMEI dla każdego zarejestrowanego urządzenia. Jeśli zaimportujesz numer IMEI inny niż numer zarejestrowany w spisie usługi Intune, urządzenie będzie klasyfikowane jako urządzenie osobiste, a nie należące do firmy. Zaimportowanie wielu numerów IMEI urządzenia spowoduje, że dla numerów niezarejestrowanych w spisie wyświetlany będzie stan rejestracji **Nieznany**.<br>
>Należy również pamiętać, że: Numery seryjne to zalecana forma identyfikacji urządzeń z systemem iOS.
>nie ma gwarancji, że numery seryjne systemu Android są unikatowe albo że istnieją. Aby ustalić, czy numer seryjny jest niezawodnym identyfikatorem urządzenia, skontaktuj się z dostawcą urządzenia.
>Numery seryjne zgłaszane przez urządzenie do usługi Intune mogą być niezgodne z identyfikatorami wyświetlanymi w menu Ustawienia/Informacje o systemie Android na urządzeniu. Sprawdź typ numeru seryjnego podanego przez producenta urządzenia.
>Próba przekazania pliku z numerami seryjnymi zawierającymi kropki (.) spowoduje niepowodzenie przekazywania. Numery seryjne z kropkami nie są obsługiwane.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Przekazywanie listy CSV identyfikatorów firmy

1. Zaloguj się w usłudze [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), wybierz kolejno pozycje **Rejestrowanie urządzenia** > **Identyfikatory urządzeń firmowych** > **Dodaj** > **Przekaż plik CSV**.

   ![Obszar roboczy identyfikatorów urządzeń firmowych z wyróżnionym przyciskiem Dodaj](./media/corporate-identifiers-add/add-corp-id.png)

2. W bloku **Dodawanie identyfikatorów** określ typ identyfikatora: **IMEI** lub **Numer seryjny**.

3. Kliknij ikonę folderu i określ ścieżkę do listy, którą chcesz zaimportować. Przejdź do pliku CSV i wybierz pozycję **Dodaj**. 

4. Jeśli plik CSV zawiera identyfikatory firmy, które znajdują się już w usłudze Intune, ale mają różne szczegóły, pojawi się okno podręczne **Przeglądanie zduplikowanych identyfikatorów**. Wybierz identyfikatory, które chcesz zastąpić w usłudze Intune, i wybierz przycisk **OK** w celu dodania identyfikatorów. Dla każdego identyfikatora zostanie porównany tylko pierwszy duplikat.

## <a name="manually-enter-corporate-identifiers"></a>Ręczne wprowadzanie identyfikatorów firmy

1. Zaloguj się w usłudze [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) i wybierz kolejno pozycje **Rejestrowanie urządzenia** > **Identyfikatory urządzeń firmowych** > **Dodaj** > **Wprowadź ręcznie**.

2. W bloku **Dodawanie identyfikatorów** określ typ identyfikatora: **IMEI** lub **Numer seryjny**.

3. Wprowadź **identyfikator** i **szczegóły** dla każdego identyfikatora, który chcesz dodać. Po zakończeniu wprowadzania identyfikatorów wybierz pozycję **Dodaj**.

5. Jeśli wprowadzono identyfikatory firmy, które znajdują się już w usłudze Intune, ale mają różne szczegóły, pojawi się okno podręczne **Przeglądanie zduplikowanych identyfikatorów**. Wybierz identyfikatory, które chcesz zastąpić w usłudze Intune, i wybierz przycisk **OK** w celu dodania identyfikatorów. Dla każdego identyfikatora zostanie porównany tylko pierwszy duplikat.

Aby zobaczyć nowe identyfikatory urządzeń, możesz kliknąć pozycję **Odśwież**.

Importowane urządzenia nie są zawsze zarejestrowane. Urządzenia mogą mieć stan **Zarejestrowane** lub **Nie kontaktowano się**. Wartość **Nie kontaktowano się** oznacza, że z urządzeniem nigdy nie nawiązano połączenia w usłudze Intune.

## <a name="delete-corporate-identifiers"></a>Usuwanie identyfikatorów firmy

1. Zaloguj się w usłudze [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) i wybierz kolejno pozycje **Rejestrowanie urządzenia** > **Identyfikatory urządzeń firmowych**.
2. Wybierz identyfikatory urządzeń do usunięcia, a następnie wybierz pozycję **Usuń**.
3. Potwierdzenie usunięcia.

Usunięcie identyfikatora firmy zarejestrowanego urządzenia nie zmienia własności tego urządzenia. Aby zmienić własność urządzenia, przejdź do pozycji **Urządzenia**, wybierz urządzenie, wybierz pozycję **Właściwości** i zmień ustawienie **Własność urządzenia**.

## <a name="imei-specifications"></a>Specyfikacje IMEI
Szczegółowe specyfikacje dotyczące identyfikatorów IMEI (International Mobile Equipment Identifier) można znaleźć w portalu [3GPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Zmienianie własności urządzeń

We właściwościach urządzeń jest wyświetlana **Własność** dla rekordów każdego urządzenia w usłudze Intune. Jako administrator możesz określić urządzenia jako **Osobiste** lub **Firmowe**.

**Aby zmienić własność urządzeń:**
1. Zaloguj się w usłudze [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), przejdź do pozycji **Urządzenia** i wybierz urządzenie.
2. Wybierz pozycję **Właściwości**.
3. Określ **Własność urządzeń** jako **Osobiste** lub **Firmowe**.

   ![Właściwości urządzenia z opcjami Kategoria urządzenia i Własność urządzeń](./media/corporate-identifiers-add/device-properties.png)