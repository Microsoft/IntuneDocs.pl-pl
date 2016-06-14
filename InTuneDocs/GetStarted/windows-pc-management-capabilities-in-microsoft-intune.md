---
# required metadata

title: Możliwości zarządzania komputerami z systemem Windows w usłudze Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Możliwości zarządzania komputerami z systemem Windows (za pomocą komputerowego klienta usługi Microsoft Intune)
W większości przypadków będziesz rejestrować urządzenia w usłudze Microsoft Intune, co zapewnia dostęp do szerszego zestawu możliwości niż w przypadku komputerowego klienta usługi Intune. Niemniej jednak możesz również zarządzać komputerami, korzystając z komputerowego klienta usługi Intune, który zapewnia następujące funkcje:

-   **Zarządzanie aktualizacjami oprogramowania** — aktualizowanie komputerów i zarządzanie harmonogramem stosowania aktualizacji.

-   **Zasady Zapory systemu Windows** — zapewnianie, że żaden komputer używany przez firmę nie ma nieaktywnej ani nieprawidłowo skonfigurowanej Zapory systemu Windows.

-   **Ochrona przed złośliwym oprogramowaniem** — usługa Intune obejmuje program Endpoint Protection, który pomaga chronić komputery przed złośliwym oprogramowaniem.

-   **Pomoc zdalna** — usługa Intune umożliwia użytkownikom kontaktowanie się z pracownikami działu pomocy technicznej IT, którzy mogą udzielić im pomocy przy użyciu funkcji pulpitu zdalnego dostępnej w usłudze Intune.

-   **Zarządzanie licencjami na oprogramowanie** — śledź liczbę dostępnych licencji na oprogramowanie oraz liczbę dostępnych licencji będących w użyciu.
-   **Wdrażanie aplikacji** — wdrażanie oprogramowania na zarządzanych komputerach. Niektóre funkcje zarządzania aplikacjami są niedostępne, jeśli zarządzasz komputerami za pomocą oprogramowania klienckiego.


## Wymagania dotyczące systemu operacyjnego
Usługa Intune może zarządzać komputerami z następującymi wersjami systemu Windows (x86 i x64):


-   **Windows Vista** — wersje Business, Enterprise i Ultimate.

-   **Windows 7** — wersje Professional, Enterprise i Ultimate (bez dodatku Service Pack lub z dodatkiem SP1).

-   **Windows 8** — wersje Professional i Enterprise.

-   **Windows 8.1** — wersje Professional i Enterprise.


## Minimalne wymagania sprzętowe
Poniżej podano minimalne wymagania dotyczące sprzętu w przypadku instalowania komputerowego klienta usługi Intune:

|Wymaganie|Szczegóły|
|---------------|--------------------|
|Sieć|Klient wymaga komputera z połączeniem z Internetem.|
|Procesor i pamięć|Należy zapoznać się z wymaganiami dotyczącymi procesora i pamięci RAM dla systemu operacyjnego komputera.|
|Miejsce na dysku|200 MB dostępnego miejsca na dysku przed zainstalowaniem oprogramowania klienckiego.|

## Dodatkowe wymagania
Poniżej podano wymagania dotyczące oprogramowania w przypadku instalowania komputerowego klienta usługi Intune:

|Wymaganie|Szczegóły|
|---------------|--------------------|
|Uprawnienia administracyjne|Konto używane do instalacji oprogramowania klienckiego musi mieć uprawnienia administratora lokalnego na danym komputerze.|
|Instalator Windows w wersji 3.1|Na komputerze musi być zainstalowany Instalator Windows w wersji 3.1 lub nowszej.|
|Usunięcie niezgodnego oprogramowania klienckiego|Przed zainstalowaniem komputerowego oprogramowania klienckiego usługi Intune należy odinstalować następujące oprogramowanie klienckie z danego komputera:<br /><br />— Wszelkie wersje programu Configuration Manager<br />— Wszelkie wersje programu Microsoft Systems Management Server (SMS)|

### Zobacz także
[Możliwości zarządzania urządzeniami przenośnymi w usłudze Microsoft Intune](/intune/understand/mobile-device-management-capabilties-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->

