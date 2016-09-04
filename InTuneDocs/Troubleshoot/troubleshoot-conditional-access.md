---
title: "Rozwiązywanie problemów z dostępem warunkowym | Microsoft Intune"
description: "Co zrobić, gdy użytkownicy nie mogą uzyskać dostępu do zasobów za pomocą dostępu warunkowego usługi Intune."
keywords: 
author: karaman
manager: angrobe
ms.date: 07/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7b16c19c95384655e170c199597dd6bd31afb90d
ms.openlocfilehash: a04037453382420540dbec721179ccb623df0829


---

# Rozwiązywanie problemów z dostępem warunkowym

Zazwyczaj użytkownik próbuje uzyskać dostęp do poczty e-mail lub programu SharePoint i otrzymuje monit o rejestrację. Ten monit doprowadzi użytkownika do portalu firmy.

W tym temacie opisano, co należy zrobić, gdy użytkownicy nie mogą uzyskać dostępu do zasobów za pomocą dostępu warunkowego usługi Intune.


## Podstawy pomyślnego działania dostępu warunkowego

Aby dostęp warunkowy działał, niezbędne są następujące warunki:

-   Urządzenie musi być zarządzane przez usługę Intune
-   Urządzenie musi zostać zarejestrowane w usłudze Azure Active Directory (AAD). W normalnych okolicznościach rejestracja odbywa się automatycznie podczas rejestracji w usłudze Intune
-   Urządzenie musi być zgodne z zasadami zgodności usługi Intune dla urządzenia i jego użytkownika.  Jeśli nie obowiązują zasady zgodności, wystarczy rejestracja w usłudze Intune.
-   Na urządzeniu musi być aktywowany program Exchange ActiveSync, jeśli użytkownik pobiera pocztę za pomocą natywnego klienta poczty, a nie za pomocą programu Outlook.     Dzieje się to automatycznie w przypadku urządzeń z systemem iOS, Windows Phone i Android/KNOX.
-   Program Intune Exchange Connector musi być prawidłowo skonfigurowany. Więcej informacji można znaleźć w artykule [Rozwiązywanie problemów z programem Exchange Connector w usłudze Microsoft Intune](troubleshoot-exchange-connector.md).

Te warunki można wyświetlić dla każdego urządzenia w portalu zarządzania Azure i w raporcie ze spisu urządzeń.

## Problemy dotyczące rejestracji

 -  Urządzenie nie jest zarejestrowane, więc rejestracja rozwiąże problem.
 -  Użytkownik zarejestrował urządzenie, ale dołączanie w miejscu pracy nie powiodło się. Użytkownik powinien zaktualizować rejestrację w portalu firmy.

## Problemy ze zgodnością

 -  Urządzenie nie jest zgodne z zasadami usługi Intune. Typowymi problemami są wymagania dotyczące szyfrowania i hasła. Użytkownik zostanie przekierowany do portalu firmy, w którym może skonfigurować swoje urządzenie tak, aby było zgodne.
 -  Może upłynąć trochę czasu, zanim informacje o zgodności zostaną zarejestrowane dla urządzenia. Odczekaj kilka minut i spróbuj ponownie.
 -  Urządzenia z systemem iOS:
     -   Istniejący profil e-mail utworzony przez użytkownika blokuje wdrożenie profilu utworzonego przez administratora usługi Intune. Jest to powszechny problem, ponieważ użytkownicy systemu iOS zwykle najpierw tworzą profil poczty e-mail, a potem rejestrują urządzenie. Portal firmy poinformuje użytkownika, że nie urządzenie nie jest zgodne z powodu ręcznie skonfigurowanego profilu poczty e-mail i wyświetli monit o usunięcie tego profilu. Użytkownik powinien usunąć swój profil poczty e-mail, aby umożliwić wdrożenie profilu z usługi Intune. Aby uniknąć problemu, poinstruuj użytkowników, aby dokonali rejestracji bez instalowana profilu poczty e-mail i pozwolili usłudze Intune na wdrożenie profilu.
     -   Urządzenie z systemem iOS może zostać zablokowane w stanie sprawdzania zgodności, co uniemożliwia zainicjowanie innego ewidencjonowania użytkownika. Ponowne uruchomienie portalu firmy może naprawić ten problem, a stan zgodności będzie odpowiadał stanowi urządzenia w usłudze Intune. Po pobraniu wszystkich danych z synchronizacji urządzenia sprawdzanie zgodności trwa bardzo krótko — średnio pół sekundy.

        Zazwyczaj przyczyną pozostawania urządzeń w tym stanie są problemy z połączeniem z usługą lub długi czas trwania synchronizacji.  Jeśli problem będzie nadal występował w różnych konfiguracjach sieci (komórkowych, Wi-Fi, VPN), pomimo ponownego uruchomienia urządzeń i po sprawdzeniu aktualności dostawcy SSP na urządzeniu, należy skontaktować się z pomocą techniczną firmy Microsoft zgodnie z opisem w artykule [Jak uzyskać pomoc techniczną dla usługi Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## Problemy dotyczące zasad

W przypadku tworzenia zasad zgodności i łączenia ich z zasadami poczty e-mail obie zasady muszą być wdrożone dla tego samego użytkownika, więc należy uważać podczas planowania, które zasady są wdrażane dla których grup. Użytkownicy, dla których stosowane są tylko jedne zasady, prawdopodobnie stwierdzą, że ich urządzenia nie są zgodne.


## Problemy z programem Exchange ActiveSync

### Zgodne urządzenia Android otrzymują powiadomienia o kwarantannie
- Urządzenie Android, które jest zarejestrowane i zgodne, może nadal otrzymywać powiadomienie o kwarantannie podczas próby uzyskania dostępu do zasobów firmy. Przed wybraniem linku **Rozpocznij** użytkownik powinien upewnić się, że portal firmy nie był otwarty podczas próby uzyskania dostępu do zasobów. Użytkownicy powinni zamknąć portal firmy, ponownie spróbować uzyskać dostęp do zasobów, a następnie wybrać link **Rozpocznij**.

### Wycofane urządzenie w dalszym ciągu ma dostęp.
- W przypadku korzystania z usługi Exchange Online wycofane urządzenie może nadal mieć dostęp przez kilka godzin po wycofaniu. Jest to spowodowane tym, że program Exchange buforuje prawa dostępu przez 6 godzin. Należy rozważyć inne sposoby ochrony danych na wycofanych urządzeniach w tym scenariuszu.

### Urządzenie jest zgodne i zarejestrowane w usłudze AAD, ale nadal jest zablokowane
- Czasami udostępnianie identyfikatora ActiveSync programu Exchange (EASID) usłudze AAD może być opóźnione. Typową przyczyną tego problemu jest ograniczanie, więc odczekaj kilka minut i spróbuj ponownie.

### Urządzenie zablokowane

Dostęp warunkowy urządzenia może zostać zablokowany bez otrzymania wiadomości e-mail o aktywacji.

- Czy występuje domyślna reguła programu Exchange, która poddaje urządzenia kwarantannie lub blokuje je? Jeśli domyślna reguła blokuje urządzenia lub poddaje je kwarantannie, urządzenia nie mogą otrzymać wiadomości e-mail o aktywacji z programu Exchange Connector. To jest celowe.
- Czy konto powiadomień jest prawidłowo skonfigurowane, zgodnie z opisem w konfiguracji podstawowej?
- Czy urządzenie jest obecne w konsoli administracyjnej usługi Intune jako urządzenie Exchange ActiveSync? Jeśli nie, prawdopodobnie odnajdywanie urządzeń kończy się niepowodzeniem, zazwyczaj z powodu problemu z synchronizacją programu Exchange Connector. Patrz Urządzenie z programem Exchange ActiveSync nie zostało wykryte za pomocą programu Exchange.
- Sprawdź dzienniki programu Exchange Connector pod kątem działań związanych z wysyłaniem wiadomości e-mail i sprawdzaniem błędów. Przykład polecenia do wyszukiwania to SendEmail z konta powiadomień na konto użytkownika.
- Przed zablokowaniem urządzenia przez program Exchange Connector wysyła on wiadomość e-mail dotyczącą aktywacji. Jeśli urządzenie jest w trybie offline, może nie otrzymać wiadomości e-mail dotyczącej aktywacji. Sprawdź, czy klient poczty e-mail urządzenia został skonfigurowany do pobierania poczty w trybie wypychania zamiast sondowania, ponieważ może to spowodować przeoczenie wiadomości e-mail przez użytkownika. Zmień tryb na sondowanie i sprawdź, czy urządzenie otrzyma wiadomość e-mail.

## Niezgodne urządzenie nie zostało zablokowane

W przypadku napotkania niezgodnego urządzenia, które nadal posiada dostęp, należy wykonać następujące działania.

- Sprawdź grupy docelowe i wykluczenia. Jeśli użytkownik nie znajduje się w odpowiedniej grupie docelowej lub znajduje się w grupie wykluczenia, nie zostanie zablokowany. Tylko urządzenia użytkowników w grupie docelowej są sprawdzane pod kątem zgodności.
- Upewnij się, że urządzenie jest wykrywane. Czy program Exchange Connector wskazuje urzędy certyfikacji Exchange 2010, gdy użytkownik korzysta z serwera programu Exchange 2013? W tym przypadku, jeśli domyślna reguła programu Exchange to Zezwalaj, nawet jeśli użytkownik znajduje się w grupie docelowej, usługa Intune nie monitoruje połączenia urządzenia z usługą Exchange.
- Sprawdź występowanie urządzenia/stan dostępu w programie Exchange:
    - Użyj następującego polecenia cmdlet programu PowerShell, aby wyświetlić listę wszystkich urządzeń przenośnych skrzynki pocztowej: „Get-ActiveSyncDeviceStatistics -mailbox mbx”. Jeśli urządzenia nie ma na liście, nie ma ono dostępu do programu Exchange.
    - Jeśli urządzenie znajduje się na liście, użyj polecenia cmdlet „Get-CASmailbox -identity:’upn’ | fl”, aby uzyskać szczegółowe informacje na temat stanu jego dostępu, oraz przekaż te informacje do pomocy technicznej firmy Microsoft.

## Przed otwarciem biletu pomocy technicznej
Jeśli powyższe procedury nie rozwiążą problemu, pomoc techniczna firmy Microsoft może poprosić o podanie dodatkowych informacji, takich jak dzienniki skrzynek pocztowych usługi OWA i programu Exchange Connector.

### Zbieranie dzienników skrzynki pocztowej usługi OWA

1. Zaloguj się za pośrednictwem usługi OWA i wybierz symbol ustawień (koło zębate) obok swojej nazwy w prawym górnym rogu.
2. Wybierz pozycję **Opcje**.
3. Wybierz pozycję **Telefon** (**Urządzenie przenośne**) w kolumnie po lewej stronie.
4. Z górnego menu wybierz pozycję **Urządzenia przenośne**.
5. Wybierz swoje urządzenie z listy, a następnie wybierz pozycję **Rozpocznij rejestrowanie**.
6. Po wyświetleniu monitu wybierz **Tak** w wyskakującym oknie dialogowym.
7. Wykonaj akcję, która spowodowała problem, aby go odtworzyć.
8. Poczekaj 1-2 minuty, a następnie wróć do listy telefonów w programie OWA. Upewnij się, że Twój telefon jest zaznaczony na liście i wybierz z górnego menu polecenie **Pobierz dziennik**.
9. Otrzymasz od samego siebie wiadomość e-mail z załącznikiem. Po otwarciu biletu pomocy technicznej udostępnij zawartość wiadomości e-mail pomocy technicznej firmy Microsoft.

### Dzienniki programu Exchange Connector

#### Ogólne informacje o dziennikach
Aby wyświetlić dzienniki programu Exchange Connector, użyj [Server Trace Viewer Tool] narzędzia podglądu śledzenia serwera (https://msdn.microsoft.com/en-us/library/ms732023(v=vs.110).aspx). To narzędzie wymaga pobrania zestawu SDK systemu Windows Server.

>[!NOTE]
>Dzienniki znajdują się w folderze C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs. Dzienniki są grupowane w serie 30 plików dzienników, od *Connector0.log* do *Connector29.log*. Dzienniki są zmieniane po zebraniu w jednym dzienniku 10 MB danych. Po zapełnieniu pliku Connector29 następuje powrót do pliku Connector0 i zastąpienie starszych plików dzienników.

#### Lokalizowanie dzienników synchronizacji

-    Pełną synchronizację w dziennikach można zlokalizować, wyszukując termin **full sync**. Początek synchronizacji jest oznaczony następującym zdaniem:

    'Handling command: Getting the mobile device list without a time filter (full sync) for <number> users`

    Koniec dziennika pełnej synchronizacji wygląda następująco:

    Getting the mobile device list without a time filter (full sync) for 4 users completed successfully. Details: Inventory command result - Devices synced: 0 Commmand ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected','

-   Szybką synchronizację (delta) można odnaleźć w dziennikach, wyszukując termin **quick sync**.

##### Wyjątki w poleceniu Get next
Sprawdź dzienniki programu Exchange Connector pod katem wyjątków w **poleceniu Get next** i przekaż je pomocy technicznej firmy Microsoft.

#### Pełne rejestrowanie

Aby włączyć pełne rejestrowanie:

1.  Otwórz plik konfiguracji śledzenia programu Exchange Connector. Ścieżka pliku jest następująca: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml.
2.  Odszukaj wiersz TraceSourceLine z następującym kluczem: OnPremisesExchangeConnectorService
3.  Zmień wartość węzła **SourceLevel** z **Warning ActivityTracing** (wartość domyślna) na **Verbose ActivityTracing**, jak pokazano poniżej.

    <TraceSourceLine>
          <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key>
          <Value xsi:type="TraceSource">
            <SourceLevel>All</SourceLevel>
            <Listeners>
              <Listener>
                <ListenerType>CircularTraceListener</ListenerType>
                <SourceLevel>Verbose ActivityTracing</SourceLevel>
                <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes>
                <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName>
                <FileQuota>30</FileQuota>
              </Listener>
            </Listeners>
          </Value>
    </TraceSourceLine>



### Następne kroki
Jeśli te informacje dotyczące rozwiązywania problemów nie pomogły, skontaktuj się z pomocą techniczną firmy Microsoft zgodnie z opisem w temacie [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Jak uzyskać pomoc techniczną dotyczącą usługi Microsoft Intune).



<!--HONumber=Aug16_HO1-->

