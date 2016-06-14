---
# required metadata

title: Wybieranie sposobu przygotowania aplikacji do zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Wybieranie sposobu przygotowania aplikacji do zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune
W aplikacjach można włączyć opcję użycia zasad zarządzania aplikacjami mobilnymi za pomocą narzędzia opakowującego aplikacje usługi Intune lub zestawu SDK aplikacji usługi Intune. Poniżej przedstawiono informacje dotyczące tych dwóch metod oraz sytuacji, w których należy je stosować.

## Narzędzia opakowujące aplikacje usługi Intune
Narzędzia opakowujące aplikacje jest używane głównie dla wewnętrznych aplikacji biznesowych. To narzędzie jest aplikacją wiersza polecenia tworzącą otoku aplikacji, która następnie umożliwia zarządzanie aplikacją za pośrednictwem zasad zarządzania aplikacjami mobilnymi usługi Intune. Do korzystania z narzędzia nie potrzeba kodu źródłowego, ale potrzebne będą poświadczenia podpisywania.  Aby uzyskać więcej informacji na temat poświadczeń podpisywania, zobacz [blog usługi Intune](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx). Aby uzyskać informacje na temat dokumentacji dotyczącej narzędzia opakowującego aplikacje, zobacz [Narzędzie opakowujące aplikacje systemu Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) i [Narzędzie opakowujące aplikacje systemu iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

Narzędzie opakowujące aplikacje nie obsługuje aplikacji w sklepie App Store i Sklepie Play ani funkcji, które wymagają integracji czasu programowania (zobacz porównanie funkcji w poniższej tabeli).

Jeśli aplikacja została już napisana lub jeśli kod źródłowy jest niedostępny, należy użyć narzędzia opakowującego aplikacje, a nie zestawu SDK.

## Zestaw SDK aplikacji usługi Intune
Zestaw SDK aplikacji jest przeznaczony głównie dla klientów, których aplikacje znajdują się w sklepie App Store lub Sklepie Play i którzy chcą zarządzać aplikacjami w usłudze Intune. Korzyści wynikające z integracji zestawu SDK są jednak dostępne w przypadku wszystkich aplikacji, nawet aplikacji biznesowych.

Do zintegrowania zestawu SDK niezbędny jest dostęp do kodu źródłowego aplikacji. Aby uzyskać instrukcje dotyczące integrowania zestawu SDK, zobacz [Zestaw SDK aplikacji usługi Microsoft Intune](https://msdn.microsoft.com/library/mt627769.aspx).

## Porównanie funkcji
W tej tabeli przedstawiono ustawienia do użycia w przypadku zestawu SDK aplikacji i narzędzia opakowującego aplikacje.

> [!NOTE]
> Narzędzie opakowujące aplikacje może być stosowane z autonomiczną usługą Intune lub usługą Intune z programem Configuration Manager.

|Funkcja|Zestaw SDK aplikacji|Narzędzie opakowujące aplikacje|
|-----------|---------------------|-----------|
|Ogranicz zawartość sieci Web wyświetlaną w zarządzanej przeglądarce firmowej|X|X|
|Nie zezwalaj na kopie zapasowe systemu Android, programu iTunes i usługi iCloud|X|X|
|Zezwalaj aplikacji na transfer danych do innych aplikacji|X|X|
|Zezwalaj aplikacji na odbieranie danych z innych aplikacji|X|X|
|Ogranicz wycinanie, kopiowanie i wklejanie w innych aplikacjach|X|X|
|Wymagaj prostego numeru PIN w celu udzielenia dostępu|X|X|
|Zastąp numer PIN wbudowanej aplikacji numerem PIN usługi Intune|X||
|Określ liczbę prób przed zresetowaniem numeru PIN|X|X|
|Wymagaj odcisku palca zamiast numeru PIN (tylko system iOS)<br></br>**Uwaga:** dostępne tylko w środowiskach obsługujących wyłącznie zarządzanie aplikacjami mobilnymi.|X||
|Wymagaj poświadczeń firmowych w celu udzielenia dostępu|X|X|
|Blokuj uruchamianie aplikacji zarządzanych na urządzeniach, na których zdjęto zabezpieczenia systemu lub uzyskano dostęp do konta root|X|X|
|Szyfruj dane aplikacji|X|X|
|Ponownie sprawdź wymagania dostępu po upływie określonej liczby minut|X|X|
|Wybierz okres karencji w trybie offline|X|X|
|Zablokuj przechwytywanie ekranu (tylko system Android)|X|X|
|Pełne czyszczenie|X|X|
|Selektywne czyszczenie <br></br>**Uwaga:** w systemie iOS usunięcie profilu zarządzania spowoduje również usunięcie aplikacji.|X||
|Nie zezwalaj na używanie polecenia „Zapisz jako” |X||
|Obsługa wielu tożsamości|X||

### Zobacz także
[Narzędzie opakowujące aplikacje systemu Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Narzędzie opakowujące aplikacje systemu iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Używanie zestawu SDK w celu przygotowania aplikacji do zarządzania aplikacjami mobilnymi](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO1-->

