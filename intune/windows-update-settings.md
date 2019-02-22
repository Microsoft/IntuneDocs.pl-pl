---
title: Ustawienia usługi Windows Update dla Firm w usłudze Microsoft Intune — Azure | Microsoft Docs
description: Ustawienia usługi Windows Update dla Firm na urządzeniach z systemem Windows 10, które można wdrożyć przy użyciu usługi Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98c3425c58b6039c8a1c3b5750f9473c74a78634
ms.sourcegitcommit: 93de3423d2d8f0019e676a63784edeb3daf47cb7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56325473"
---
# <a name="windows-update-settings-for-intune"></a>Ustawienia aktualizacji systemu Windows dla usługi Intune  

Zapoznaj się z ustawieniami aktualizacji systemu Windows 10 [konfigurowanymi i zarządzanymi](windows-update-for-business-configure.md) przy użyciu usługi Microsoft Intune.  

W przypadku konfigurowania ustawień pierścieni aktualizacji systemu Windows 10 w usłudze Intune konfigurujesz ustawienia usługi Windows Update.  Jeśli ustawienie aktualizacji systemu Windows ma zależność wersji systemu Windows 10, zależność wersji jest zapisywana w obszarze szczegółów ustawień.  

## <a name="update-settings"></a>Ustawienia aktualizacji  

Ustawienia aktualizacji umożliwiają kontrolowanie elementów pobieranych przez urządzenie oraz momentu ich pobrania. Zapoznaj się z dokumentacją systemu Windows, aby uzyskać dalsze informacje na temat zachowania poszczególnych ustawień.  

### <a name="servicing-channel"></a>Kanał obsługi  

- **Ustawienie domyślne**: Półroczny kanał dystrybucji (kierowany)  
- **Dokumentacja dotycząca systemu Windows**: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Ustaw kanał (gałąź), z którego urządzenie ma otrzymywać aktualizacje systemu Windows. Różne kanały mogą używać innych okresów odroczenia przed dostarczeniem aktualizacji.  

Na przykład opcja *Półroczny kanał* ma odroczenie o długości sześciu miesięcy. Oznacza to, że jeśli używasz tego kanału bez dodatkowych odroczeń związanych z ustawieniem, urządzenie instaluje aktualizację sześć miesięcy po jej wydaniu.  

Obsługiwane kanały aktualizacji:  

- Półroczny kanał  
- Półroczny kanał (kierowany)  
- Niejawny program testów systemu Windows — szybki  
- Niejawny program testów systemu Windows — wolny  
- Wydanie w ramach niejawnego programu testów systemu Windows  

Jeśli wybierzesz kanał niejawnego programu testów, usługa Intune automatycznie konfiguruje ustawienie aktualizacji Windows [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds), aby kompilacja niejawnego programu testów działała.  


> [!IMPORTANT]  
> Począwszy od systemu Windows w wersji 1903, opcja *Półroczny kanał (kierowany)* (SAC-T) została wycofana z użytku. Po tej zmianie opcja SAC-T połączyła się z opcją *Półroczny kanał*. Aby dowiedzieć się więcej na temat tej zmiany oraz jej wpływu na usługę Windows Update dla Firm, zobacz wpis w blogu dla profesjonalistów IT zajmujących się systemem Windows: [Windows Update for Business and the retirement of SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523) (Windows Update dla Firm i wycofanie opcji SAC-T).
 


### <a name="microsoft-product-updates"></a>Aktualizacje produktów firmy Microsoft  

- **Ustawienie domyślne**:  Zezwalaj
- **Dokumentacja dotycząca systemu Windows**: [Update/AllowMUUpdateService](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Wybierz pozycję *Zezwalaj*, aby skanować w poszukiwaniu aktualizacji aplikacji z usługi Microsoft Update.    

### <a name="windows-drivers"></a>Sterowniki systemu Windows  

- **Ustawienie domyślne**:  Zezwalaj
- **Dokumentacja dotycząca systemu Windows**: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Wybierz pozycję *Zezwalaj*, aby uwzględniać sterowniki z usługi Windows Update podczas aktualizacji

### <a name="quality-update-deferral-period-days"></a>Okres odroczenia aktualizacji dotyczących jakości (dni)  

- **Ustawienie domyślne**: 0  
- **Dokumentacja dotycząca systemu Windows**: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Określ liczbę dni odroczenia aktualizacji dotyczących jakości: od 0 do 30. Jest to okres stosowany oprócz każdego okresu odroczenia stanowiącego część wybranego kanału usługi. Okres odroczenia rozpoczyna się po odebraniu zasad przez urządzenie.  

Aktualizacje dotyczące jakości są zazwyczaj poprawkami oraz ulepszeniami istniejących funkcji systemu Windows.  

### <a name="feature-update-deferral-period-days"></a>Okres odroczenia aktualizacji funkcji (dni)  

- **Ustawienie domyślne**: 0  
- **Dokumentacja dotycząca systemu Windows**: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Określ liczbę dni odroczenia aktualizacji funkcji. Jest to okres stosowany oprócz każdego okresu odroczenia stanowiącego część wybranego kanału usługi. Okres odroczenia rozpoczyna się po odebraniu zasad przez urządzenie.  
Obsługiwany okres odroczenia:  

- *System Windows w wersji 1709 lub nowszej*: od 0 do 365 dni  
- *System Windows w wersji 1703*:  od 0 do 180 dni  

Aktualizacje dotyczące funkcji są zazwyczaj nowymi funkcjami systemu Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Ustawianie okresu odinstalowywania aktualizacji funkcji (2–60 dni)  

- **Ustawienie domyślne**: 10  
- **Dokumentacja dotycząca systemu Windows**:  [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Skonfiguruj czas, po którym nie można odinstalować aktualizacji funkcji.  

Po upływie tego okresu elementy poprzedniej aktualizacji są usuwane z urządzenia i nie można odinstalować w celu przywrócenia poprzedniej wersji aktualizacji.  

Na przykład rozważ użycie pierścienia aktualizacji z okresem odinstalowywania aktualizacji funkcji o długości 20 dni. Po 25 dniach decydujesz się na wycofanie najnowszej aktualizacji funkcji i użycie opcji Odinstaluj.  Urządzenia, na których aktualizacja funkcji została zainstalowana ponad 20 dni temu, nie mogą jej odinstalować, ponieważ niezbędne elementy zostały usunięte w ramach konserwacji urządzenia. Natomiast urządzenia, na których aktualizacja funkcji została zainstalowana maksymalnie 19 dni temu, mogą odinstalować aktualizację, jeśli zostaną pomyślnie zaewidencjonowane w celu odebrania polecenia odinstalowania przed przekroczeniem 20-dniowego okresu odinstalowywania.  


## <a name="user-experience-settings"></a>Ustawienia środowiska użytkownika  

Ustawienia środowiska użytkownika umożliwiają kontrolowanie środowiska użytkownika końcowego pod kątem ponownego uruchamiania urządzenia i przypomnień. Zapoznaj się z dokumentacją systemu Windows, aby uzyskać dalsze informacje na temat zachowania poszczególnych ustawień.  

### <a name="automatic-update-behavior"></a>Zachowanie automatycznych aktualizacji  

- **Ustawienie domyślne**: Automatycznie instaluj i uruchamiaj ponownie w zaplanowanym czasie  
- **Dokumentacja dotycząca systemu Windows**: [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Wybierz sposób instalowania automatycznych aktualizacji oraz — w razie potrzeby — moment ponownego uruchomienia urządzenia.  

Zapoznaj się z dokumentacją dotyczącą systemu Windows, aby uzyskać pełne informacje na temat następujących obsługiwanych opcji:  

- **Powiadamiaj o pobieraniu** — powiadamianie użytkownika przed pobraniem aktualizacji. Użytkownicy wybierają opcję pobierania i instalowania aplikacji.  

- **Automatycznie instaluj podczas konserwacji** — aktualizacje są pobierane automatycznie, a następnie instalowane podczas automatycznej konserwacji, gdy urządzenie nie jest używane ani zasilane za pomocą baterii. Jeśli ponowne uruchomienie jest wymagane, użytkownicy są monitowani o wykonanie tej czynności przez maksymalnie siedem dni, a następnie ponowne uruchomienie jest wymuszane.  

  Ta opcja może powodować automatyczne ponowne uruchamianie urządzenia po zainstalowaniu aktualizacji. Użyj ustawień **godzin aktywnego użytkowania**, aby zdefiniować okres, podczas którego operacje automatycznego ponownego uruchamiania są blokowane:  

  - **Początek godzin aktywnego użytkowania**: Określ godzinę rozpoczęcia pomijania ponownych uruchomień z powodu instalacji aktualizacji.  
    **Dokumentacja dotycząca systemu Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Ustawienie domyślne**: 8:00  
  
  - **Koniec godzin aktywnego użytkowania**: Określ godzinę zakończenia pomijania ponownych uruchomień z powodu instalacji aktualizacji.  
    **Dokumentacja dotycząca systemu Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Ustawienie domyślne**: 17:00  

- **Automatycznie instaluj i ponownie uruchamiaj podczas konserwacji** — aktualizacje są pobierane automatycznie, a następnie instalowane podczas automatycznej konserwacji, gdy urządzenie nie jest używane ani zasilane za pomocą baterii. Jeśli ponowne uruchomienie urządzenia jest wymagane, jest ono wykonywane, gdy urządzenie nie jest używane. (Jest to wartość domyślna w przypadku urządzeń niezarządzanych).  

  Ta opcja może powodować automatyczne ponowne uruchamianie urządzenia po zainstalowaniu aktualizacji. Sposób korzystania z ustawień **godzin aktywnego użytkowania** nie został opisany w ustawieniach usługi Windows Update, ale są one używane przez usługę Intune do zdefiniowania okresu, w trakcie którego operacje automatycznego ponownego uruchamiania są blokowane:  

  - **Początek godzin aktywnego użytkowania**: Określ godzinę rozpoczęcia pomijania ponownych uruchomień z powodu instalacji aktualizacji.  
    **Dokumentacja dotycząca systemu Windows**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Ustawienie domyślne**: 8:00  

  - **Koniec godzin aktywnego użytkowania**: Określ godzinę zakończenia pomijania ponownych uruchomień z powodu instalacji aktualizacji.  
    **Dokumentacja dotycząca systemu Windows**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Ustawienie domyślne**: 17:00  

- **Automatycznie instaluj i uruchamiaj ponownie w zaplanowanym czasie** — określ dzień i godzinę instalacji. Jeśli nie zostaną one podane, instalacja będzie uruchamiana codziennie o 3:00, po czym nastąpi 15-minutowe odliczanie do ponownego uruchomienia. Zarejestrowane użycia mogą opóźnić odliczanie i ponowne uruchamianie.  
  
  Ta opcja obsługuje dodatkowe ustawienia.  
  **Dokumentacja dotycząca systemu Windows**:  [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Częstotliwość automatycznego zachowania**: Za pomocą tego ustawienia możesz planować instalowanie aktualizacji, w tym tydzień, dzień i godzinę.  
    **Ustawienie domyślne**: Co tydzień

  - **Planowany dzień instalacji**:  Określ dzień tygodnia, w którym chcesz instalować aktualizacje.  
    **Ustawienie domyślne**: Dowolny dzień  

  - **Planowana godzina instalacji**:  Określ godzinę, o której chcesz instalować aktualizacje.  
    **Ustawienie domyślne**: 3:00  

- **Automatycznie instaluj i uruchamiaj ponownie bez kontroli użytkownika końcowego** — aktualizacje są pobierane automatycznie, a następnie instalowane podczas automatycznej konserwacji, gdy urządzenie nie jest używane ani zasilane za pomocą baterii. Jeśli ponowne uruchomienie urządzenia jest wymagane, jest ono wykonywane, gdy urządzenie nie jest używane. Ta opcja powoduje ustawienie okienka sterowania dla użytkowników końcowych na typ „tylko do odczytu”.  

- **Resetuj do domyślnych** — przywracanie pierwotnych ustawień automatycznych aktualizacji na maszynach z systemem Windows 10 z aktualizacją z października 2018 r. lub nowszą.  


### <a name="restart-checks"></a>Testy po ponownym uruchomieniu  

- **Ustawienie domyślne**: Zezwalaj  
- **Dokumentacja dotycząca systemu Windows**: [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

To ustawienie ma różne wyniki w zależności od wersji systemu Windows na urządzeniach:  

- System Windows w wersji 1703 lub starszej: Po ponownym uruchomieniu urządzenia przeprowadzane są testy obejmujące aktywnych użytkowników, poziom naładowania baterii, uruchomione gry oraz inne. Aby pominąć te testy po ponownym uruchomieniu urządzenia, wybierz pozycję **Pomiń**.  
- Od systemu Windows w wersji 1709: W trakcie godzin aktywnego użytkowania następujące procesy nie są uruchamiane w przypadku aktualizacji: skanowanie, pobieranie, instalowanie i ponowne uruchamianie. Po godzinach aktywnego użytkowania procesy aktualizacji są uruchamiane i mogą wybudzić urządzenie ze stanu uśpienia oraz skanować, pobierać, instalować i ponownie uruchamiać urządzenie, o ile sprawdzanie baterii i zasilania zakończy się wynikiem pozytywnym. Aby uzyskać więcej informacji, zobacz [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Blokowanie wstrzymywania aktualizacji systemu Windows przez użytkownika  

- **Ustawienie domyślne**: Zezwalaj  
- **Dokumentacja dotycząca systemu Windows**: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Zezwala użytkownikowi na wstrzymywanie instalacji aktualizacji lub blokuje tę możliwość.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Wymaganie zatwierdzenia przez użytkownika w przypadku ponownego uruchamiania poza godzinami pracy  

- **Ustawienie domyślne**: Nieskonfigurowane  
- **Dokumentacja dotycząca systemu Windows**: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Wybierz pozycję *Wymagaj*, aby wymagać od użytkownika zatwierdzenia ponownego uruchomienia urządzenia poza godzinami pracy.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Przypominanie użytkownikowi o wymaganym automatycznym ponownym uruchomieniu przy użyciu przypomnienia możliwego do odrzucenia (godziny)  

- **Ustawienie domyślne**: *nie jest ono konfigurowane domyślnie, a użytkownicy nie otrzymują powiadomienia*.  
- **Dokumentacja dotycząca systemu Windows**: [Update/ScheduleRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Określ, jak długo przed automatycznym ponownym uruchomieniem powiadomienie możliwe do odrzucenia ma być wyświetlane na urządzeniu użytkownika w celu przypomnienia mu o tym ponownym uruchomieniu. Obsługiwane są następujące wartości godzin: **2**, **4**, **8**, **12** lub **24**.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Przypominanie użytkownikowi o wymaganym automatycznym ponownym uruchomieniu przy użyciu przypomnienia trwałego (minuty)  

- **Ustawienie domyślne**: *nie jest ono konfigurowane domyślnie, a użytkownicy nie otrzymują powiadomienia*.  
- **Dokumentacja dotycząca systemu Windows**: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Określ, jak długo przed automatycznym ponownym uruchomieniem ostrzeżenie niemożliwe do odrzucenia ma być wyświetlane na urządzeniu użytkownika w celu przypomnienia mu o tym ponownym uruchomieniu. Obsługiwane są następujące wartości minut: **15**, **30** lub **60**.  
 
### <a name="allow-user-to-restart-engaged-restart"></a>Zezwalanie użytkownikowi na ponowne uruchamianie (ponowne uruchomienie wymagające interwencji użytkownika)  

- **Ustawienie domyślne**: Nieskonfigurowane  
- **Dokumentacja dotycząca systemu Windows**: *nie dotyczy*  
- **Wersja systemu Windows**: ustawienie obsługiwane w systemie Windows 10 w wersji 1803 i nowszych  

  > [!NOTE]  
  > W systemie Windows 10 w wersji 1809 wprowadzono dodatkowe ustawienia ponownego uruchamiania wymagającego interwencji użytkownika, które umożliwiają stosowanie oddzielnych ustawień aktualizacji dotyczących funkcji i jakości. Natomiast ustawienia zarządzane przez usługę Intune nie są oddzielnie stosowane do różnych typów aktualizacji. W zamian usługa Intune stosuje te same wartości w przypadku aktualizacje dotyczące funkcji i jakości.  

Wybranie wartości **Wymagane** powoduje włączenie opcji ponownego uruchomienia wymagającego interwencji użytkownika dla aktualizacji systemu Windows 10. Te opcje angażują użytkownika urządzenia, aby pomagał w zarządzaniu czasem ponownego uruchamiania urządzenia po zainstalowaniu aktualizacji, która wymaga ponownego uruchomienia.  

Aby uzyskać więcej informacji na temat tej opcji, zobacz sekcję [Engaged restart](https://docs.microsoft.com/en-us/windows/deployment/update/waas-restart#engaged-restart) (Ponowne uruchomienie wymagające interwencji użytkownika) w dokumentacji systemu Windows 10 dotyczącej wdrażania aktualizacji.  

Poniższe ustawienia są używane do kontrolowania czasu wykonywania akcji ponownego uruchomienia wymagającego interwencji użytkownika.  

- **Przenoś użytkowników do ponownego uruchomienia wymagającego interwencji użytkownika po automatycznym ponownym uruchomieniu (dni)**  
  - **Ustawienie domyślne**:  Domyślnie ta opcja nie jest konfigurowana, ale obsługuje wartość z zakresu od **2** do **30**.  
  - **Dokumentacja dotycząca systemu Windows**: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Określ, jak długo po zainstalowaniu aktualizacji na urządzeniu ma rozpocząć się zachowanie ponownego uruchomienia wymagającego interwencji użytkownika. Po skonfigurowanej liczbie dni użytkownicy otrzymają monit o ponowne uruchomienie urządzenia.  

- **Odłóż przypomnienie o ponownym uruchomieniu wymagającym interwencji użytkownika (dni)**  
  - **Ustawienie domyślne**:  Domyślnie ta opcja nie jest konfigurowana, ale obsługuje wartość z zakresu od **1** do **3**.  
  - **Dokumentacja dotycząca systemu Windows**: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Określ, o ile można odłożyć monit o ponowne uruchomienie.  Po zakończeniu okresu odłożenia monit o ponowne uruchomienie pojawi się jeszcze raz. Użytkownik może nadal odkładać przypomnienie do momentu osiągnięcia terminu instalacji.  

- **Ustaw termin oczekujących ponownych uruchomień (dni)**  
  - **Ustawienie domyślne**:  Domyślnie ta opcja nie jest konfigurowana, ale obsługuje wartość z zakresu od **2** do **30**.  
  - **Dokumentacja dotycząca systemu Windows**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Określ maksymalną liczbę dni oczekiwania po rozpoczęciu zachowania ponownego uruchomienia wymagającego interwencji użytkownika, aż urządzenie wymusi wymagane ponowne uruchomienie. To ponowne uruchomienie spowoduje monitowanie użytkowników o zapisanie pracy

### <a name="delivery-optimization-download-mode"></a>Tryb pobierania optymalizacji dostarczania  

- **Ustawienie domyślne**:  Nie dotyczy
- **Dokumentacja dotycząca systemu Windows**: *nie dotyczy*

Optymalizacja dostarczania nie jest już skonfigurowana w ramach pierścienia aktualizacji systemu Windows 10 w obszarze Aktualizacje oprogramowania. Optymalizacja dostarczania jest teraz konfigurowana za pośrednictwem konfiguracji urządzenia. Poprzednie konfiguracje są nadal dostępne w konsoli. Możesz usunąć poprzednie konfiguracje, edytując je tak, aby były *Nieskonfigurowane*, ale poza tym nie mogą być modyfikowane. 

Aby uniknąć konfliktu pomiędzy nowymi i starymi zasadami, zobacz [Przechodzenie z istniejących pierścieni aktualizacji do optymalizacji dostarczania](https://docs.microsoft.com/en-us/intune/delivery-optimization-windows#move-from-existing-update-rings-to-delivery-optimization), a następnie przenieś ustawienia do profilu optymalizacji dostarczania.

