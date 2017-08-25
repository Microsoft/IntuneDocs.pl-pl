---
title: "Rejestracja urządzeń z systemem iOS przy użyciu programu Apple Configurator i Asystenta ustawień"
titleSuffix: Intune on Azure
description: "Informacje dotyczące rejestrowania firmowych urządzeń z systemem iOS przy użyciu programu Apple Configurator i Asystenta ustawień."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb3ea2fbd8d710bcb8eccac9b4512ce8ba941fc2
ms.sourcegitcommit: 7674efb7de5ad54390801165364f5d9c58ccaf84
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Rejestrowanie urządzeń z systemem iOS przy użyciu programu Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usługa Intune obsługuje rejestrowanie urządzeń z systemem iOS przy użyciu narzędzia [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) działającego na komputerze Mac. Rejestrowanie przy użyciu narzędzia Apple Configurator wymaga, aby poszczególne urządzenia z systemem iOS zostały podłączone do komputera Mac za pośrednictwem portu USB w celu skonfigurowania rejestracji firmowej. Urządzenia można zarejestrować w usłudze Intune przy użyciu narzędzia Apple Configurator na dwa sposoby:
- **Rejestracja przy użyciu Asystenta ustawień** — resetuje urządzenie do ustawień fabrycznych i przygotowuje je do rejestracji z wykorzystaniem Asystenta ustawień.
- **Rejestracja bezpośrednia** — nie powoduje przywrócenia ustawień fabrycznych urządzenia i rejestruje je za pośrednictwem ustawień systemu iOS. Ta metoda obsługuje jedynie rejestrowanie urządzeń **bez koligacji użytkownika**.

Metody rejestracji z narzędziem Apple Configurator nie można używać z rejestracją korzystającą z [menedżera rejestracji urządzeń](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Fizyczny dostęp do urządzeń z systemem iOS
- [Ustaw urząd MDM](mdm-authority-set.md)
- [Certyfikat wypychania MDM firmy Apple](apple-mdm-push-certificate-get.md)
- Numery seryjne urządzeń (tylko rejestracja z wykorzystaniem Asystenta ustawień)
- Kable połączenia USB
- Komputer Mac z programem [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Tworzenie profilu programu Apple Configurator dla urządzeń

Profil rejestracji urządzeń określa ustawienia stosowane podczas rejestracji. Te ustawienia są stosowane tylko raz. Wykonaj następujące kroki, aby utworzyć profil rejestracji i zarejestrować urządzenia z systemem iOS z wykorzystaniem narzędzia Apple Configurator.

1. Zaloguj się do witryny Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. Wybierz kolejno opcje **Rejestrowanie urządzenia** > **Rejestracja Apple**.
4. W obszarze **Zarządzaj ustawieniami rejestracji programu Apple Configurator** wybierz pozycję **Profile programu AC**.
5. W bloku **Profile rejestracji programu Apple Configurator** wybierz pozycję **Utwórz**.
6. Wprowadź **nazwę** i **opis** dotyczące profilu do celów administracyjnych. Te szczegóły nie są widoczne dla użytkowników. Możesz użyć pola Nazwa, aby utworzyć grupę dynamiczną w usłudze Azure Active Directory. Nazwa profilu umożliwia zdefiniowanie parametru enrollmentProfileName w celu przypisania urządzeń z tym profilem rejestracji. Dowiedz się więcej o grupach dynamicznych usługi Azure Active Directory.

  ![Zrzut ekranu przedstawiający ekran tworzenia profilu z wybraną opcją Zarejestruj z koligacją użytkownika](./media/apple-configurator-profile-create.png)

7. Określ **koligację użytkownika**:
   - **Zarejestruj z koligacją użytkownika** — należy określić przynależność urządzenia do użytkownika za pomocą Asystenta ustawień, po czym urządzenie będzie miało dostęp do firmowych danych i poczty e-mail. Koligacja użytkownika dla urządzeń zarządzanych, które należą do użytkowników i muszą korzystać z portalu firmy na potrzeby usług takich jak instalowanie aplikacji, jest wymagana.
   - **Zarejestruj bez koligacji użytkownika** — przynależność urządzenia do użytkownika nie jest określana. Tego typu przynależności należy użyć w przypadku urządzeń wykonujących zadania bez uzyskiwania dostępu do danych użytkowników lokalnych. Aplikacje wymagające koligacji użytkownika (w tym aplikacja Portal firmy używana do instalowania aplikacji biznesowych) nie będą działać. Wymagane w przypadku rejestracji bezpośredniej.

6. Wybierz pozycję **Utwórz**, aby zapisać profil.

## <a name="setup-assistant-enrollment"></a>Rejestracja Asystenta ustawień

### <a name="add-apple-configurator-serial-numbers"></a>Dodawanie numerów seryjnych programu Apple Configurator

**Aby dodać numery seryjne programu Apple Configurator do usługi Intune**

1. Utwórz listę wartości rozdzielonych przecinkami (.csv) zawierającą dwie kolumny, bez nagłówka. Dodaj numer seryjny w lewej kolumnie i szczegółowe informacje w prawej kolumnie. Obecnie maksymalna liczba wierszy na liście wynosi 500. W edytorze tekstu lista .csv wygląda następująco:

    F7TLWCLBX196, szczegóły urządzenia</br>
    DLXQPCWVGHMJ,szczegóły urządzenia

   [Dowiedz się, jak znaleźć numer seryjny urządzenia z systemem iOS](https://support.apple.com/HT204073).
2. W usłudze Intune w witrynie Azure Portal wybierz pozycję **Rejestrowanie urządzenia**, a następnie pozycję **Rejestracja Apple**.
3. W obszarze **Zarządzanie ustawieniami rejestracji programu Apple Configurator** wybierz pozycję **Urządzenia programu Apple Configurator**.
4. Wybierz pozycję **Dodaj**.
5. Wybierz **profil rejestracji** do zastosowania do importowanych numerów seryjnych. Jeśli importujesz plik z nowymi szczegółami zastępującymi istniejące, wybierz opcję **Zastąp szczegóły dla istniejących identyfikatorów**.
6. Przejdź do pliku csv numerów seryjnych i wybierz przycisk **Dodaj**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Ponowne przypisanie profilu do numerów seryjnych urządzeń

Profil rejestracji przypisuje się po zaimportowaniu numerów seryjnych urządzeń z systemem iOS w ramach rejestracji z wykorzystaniem narzędzia Apple Configurator. Ponadto usługa Intune umożliwia przypisywanie profilów z dwóch miejsc w witrynie Azure Portal:
- **Urządzenia programu Apple Configurator**
- **Profile programu AC**

#### <a name="assign-from-apple-configurator-devices"></a>Przypisywanie z poziomu urządzeń programu Apple Configurator
1. W usłudze Intune w witrynie Azure Portal wybierz pozycję **Rejestrowanie urządzenia**, a następnie pozycję **Rejestracja Apple**.
3. W bloku **Urządzenia programu Apple Configurator** wybierz numery seryjne, do których chcesz przypisać profil, a następnie wybierz pozycję **Przypisz profil**.
4. W bloku **Przypisz profil** wybierz **Nowy profil**, który chcesz przypisać, a następnie wybierz przycisk **Przypisz**.

#### <a name="assign-from-profiles"></a>Przypisywanie z profilów
1. W usłudze Intune w witrynie Azure Portal wybierz pozycję **Rejestrowanie urządzenia**, a następnie pozycję **Rejestracja Apple**.
2. Wybierz **Profile programu AC**, a następnie wybierz profil, który chcesz przypisać do numerów seryjnych.
3. W bloku profilu wybierz opcję **Przypisane urządzenia**, a następnie wybierz opcję **Przypisz**.
4. Filtruj, aby znaleźć numery seryjne urządzeń, które chcesz przypisać do profilu, wybierz urządzenia, a następnie wybierz opcję **Przypisz**.

### <a name="export-the-profile"></a>Eksportowanie profilu
Po utworzeniu profilu i przypisaniu numerów seryjnych musisz wyeksportować profil z usługi Intune jako adres URL. Następnie zaimportuj go do narzędzia Apple Configurator na komputerze Mac w celu wdrożenia na urządzeniach.

1. W usłudze Intune w witrynie Azure Portal wybierz pozycję **Rejestrowanie urządzenia** > Rejestracja Apple** > **Profile programu AC**, a następnie wybierz profil do wyeksportowania.
2. W bloku odpowiedniego profilu zaznacz pozycję **Eksportuj profil**.
3. Skopiuj adres URL profilu. Następnie możesz dodać go później przy użyciu narzędzia Apple Configurator, aby określić profil usługi Intune używany przez urządzenia z systemem iOS.

  Następnie importuje się ten profil do narzędzia Apple Configurator, aby zdefiniować profil usługi Intune używany przez urządzenia z systemem iOS, używając poniższej procedury.

### <a name="enroll-devices-with-setup-assistant"></a>Rejestrowanie urządzeń przy użyciu Asystenta ustawień

1.  Na komputerze Mac otwórz narzędzie **Apple Configurator 2**. Na pasku menu wybierz pozycję **Apple Configurator 2**, a następnie wybierz pozycję **Preferences** (Preferencje).
  > [!WARNING]
  > Podczas procesu rejestracji urządzenia zostają zresetowane do konfiguracji fabrycznych. Jako najlepsze rozwiązanie zalecane jest zresetowanie urządzenia i włączenie go. Zalecane jest również, aby podczas podłączania na urządzeniach był wyświetlany ekran **powitalny**.

2. W okienku **preferencji** wybierz pozycję **Servers** (Serwery), a następnie wybierz symbol plusa (+), aby uruchomić kreatora serwera MDM. Wybierz pozycję **Next** (Dalej).
3. Wprowadź **nazwę lub adres URL hosta** i **adres URL rejestracji** dla serwera MDM w obszarze rejestracji asystenta ustawień dla urządzeń z systemem iOS w usłudze Microsoft Intune. W polu adresu URL rejestracji wprowadź adres URL profilu rejestracji wyeksportowany z usługi Intune. Wybierz pozycję **Next** (Dalej).  

  Możesz bezpiecznie zignorować ostrzeżenie informujące, że adres URL serwera nie został zweryfikowany. Aby kontynuować, wybieraj pozycję **Next** (Dalej), aż do ukończenia pracy kreatora.
4.  Podłącz urządzenia przenośne z systemem iOS do komputera Mac przy użyciu adaptera USB.
5.  Wybierz pozycję **Prepare**(Przygotuj). W okienku **Prepare iOS Device** (Przygotowywanie urządzenia z systemem iOS) wybierz pozycję **Manual** (Ręcznie), a następnie wybierz pozycję **Next** (Dalej).
6. W okienku **Enroll in MDM Server** (Rejestrowanie na serwerze MDM) wybierz utworzoną nazwę serwera, a następnie wybierz pozycję **Next** (Dalej).
7. W okienku **Supervise Devices** (Nadzorowanie urządzeń) wybierz poziom nadzoru, a następnie wybierz pozycję **Next** (Dalej).
8. W okienku **Create an Organization** (Tworzenie organizacji) wybierz pozycję **Organization** (Organizacja) lub utwórz nową organizację, a następnie wybierz pozycję **Next** (Dalej).
9. W okienku **Configure iOS Setup Assistant** (Konfigurowanie Asystenta ustawień systemu iOS) wybierz czynności, które mają zostać wyświetlone użytkownikowi, a następnie wybierz pozycję **Prepare** (Przygotuj). Jeśli zostanie wyświetlony monit, uwierzytelnij się w celu zaktualizowania ustawień zaufania.  
10. Po zakończeniu przygotowywania urządzenia z systemem iOS odłącz kabel USB.  

### <a name="distribute-devices"></a>Dystrybuowanie urządzeń
Urządzenia są teraz gotowe do rejestracji w firmie. Wyłącz urządzenia i przekaż je użytkownikom. Po włączeniu urządzeń przez użytkowników zostanie uruchomiony Asystent ustawień.

Użytkownicy po otrzymaniu urządzeń muszą zakończyć działania w Asystencie ustawień. Urządzenia skonfigurowane z koligacją użytkownika mogą instalować i uruchamiać aplikację Portal firmy w celu pobierania aplikacji i zarządzania urządzeniami.

## <a name="direct-enrollment"></a>Rejestracja bezpośrednia
W przypadku bezpośredniego rejestrowania urządzeń z systemem iOS przy użyciu programu Apple Configurator możesz zarejestrować urządzenie bez uzyskiwania jego numeru seryjnego. Możesz też nazwać urządzenie w celach identyfikacyjnych, zanim usługa Intune przechwyci nazwę urządzenia podczas rejestracji. Aplikacja Portal firmy nie jest obsługiwana w przypadku urządzeń, które zostały zarejestrowane bezpośrednio. Użycie tej metody nie powoduje zresetowania urządzenia do ustawień fabrycznych.

Aplikacje wymagające koligacji użytkownika (w tym aplikacja Portal firmy używana do instalowania aplikacji biznesowych) nie mogą zostać zainstalowane.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Eksportowanie profilu jako pliku .mobileconfig do urządzeń z systemem iOS
1. Zaloguj się do witryny Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku **Eksportuj profil** pobierz profil rejestracji do programu [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) w celu bezpośredniego wypchnięcia go jako profilu zarządzania do urządzeń z systemem iOS.
4. Przygotuj urządzenie z zainstalowanym programem Apple Configurator, wykonując kroki opisane poniżej.
  1. Na komputerze Mac otwórz program Apple Configurator 2.0.
  2. Podłącz urządzenia z systemem iOS do komputera Mac przy użyciu kabla USB. Zamknij aplikacje Photos (Zdjęcia), iTunes i inne aplikacje otwarte na urządzeniu po jego wykryciu.
  3. W programie Apple Configurator wybierz podłączone urządzenie z systemem iOS, a następnie wybierz przycisk **Add** (Dodaj). Opcje, które można dodać do urządzenia, są wyświetlane na liście rozwijanej. Wybierz pozycję **Profiles** (Profile).
  4. Użyj selektora plików w celu wybrania pliku mobileconfig wyeksportowanego za pomocą usługi Intune, a następnie wybierz pozycję **Add** (Dodaj). Profil zostanie dodany do urządzenia. Jeśli urządzenie jest nienadzorowane, instalacja wymaga akceptacji na urządzeniu.
5. Wykonaj poniższe kroki w celu zainstalowania profilu na urządzeniu z systemem iOS. Na urządzeniu musi zostać zakończona praca Asystenta ustawień i musi być one gotowe do użycia. Jeśli rejestracja wiąże się z wdrożeniami aplikacji, urządzenie powinno mieć ustawiony identyfikator firmy Apple, ponieważ wdrożenia aplikacji wymagają posiadania identyfikatora Apple ID powiązanego ze sklepem App Store.
   1. Odblokuj urządzenie z systemem iOS.
   2. W oknie dialogowym **Zainstaluj profil** wybierz dla pozycji **Profil zarządzania** opcję **Zainstaluj**.
   3. W razie potrzeby podaj kod dostępu urządzenia lub identyfikator Apple ID.
   4. Zaakceptuj **ostrzeżenie** i wybierz pozycję **Zainstaluj**.
   5. Zaakceptuj **ostrzeżenie zdalne** i wybierz pozycję **Ufaj**.
   6. Wyświetlenie okna dialogowego **Profil został zainstalowany** oznacza, że profil został zainstalowany. Wybierz pozycję **Gotowe**.

6. Na urządzeniu z systemem iOS otwórz pozycję **Ustawienia** i przejdź do pozycji **Ogólne** > **Zarządzanie urządzeniem** > **Profil zarządzania**. Upewnij się, że instalacja profilu jest wymieniona na liście, a następnie sprawdź ograniczenia zasad systemu iOS i zainstalowane aplikacje. Wyświetlenie ograniczeń zasad i aplikacji na urządzeniu może potrwać do 10 minut.

7. Rozdystrybuuj urządzenia. Urządzenie z systemem iOS jest teraz zarejestrowane w usłudze Intune i zarządzane przez tę usługę.