---
title: Dane wysyłane do usługi Intune przez narzędzie JAMF Pro
titleSuffix: Microsoft Intune
description: Przejrzyj listę danych wysyłanych przez narzędzie Jamf Pro do usługi Microsoft Intune podczas integrowania narzędzia Jamf Pro w celu zarządzania komputerami Mac w usłudze Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce9a92a9fffad13c6723504735b1b1cb9442f61f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721464"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Dane wysyłane do usługi Intune przez narzędzie Jamf Pro

Kiedy używasz narzędzia [Jamf Pro](https://www.jamf.com) do zarządzania komputerami Mac użytkowników końcowych w usłudze Intune, narzędzie Jamf Pro przechwytuje informacje dotyczące spisu zarządzanych urządzeń z systemem macOS. 

## <a name="data"></a>Dane  
Narzędzie Jamf Pro zgłasza do usługi Intune następujące informacje:  

* Identyfikator urządzenia w usłudze Azure Active Directory
* Stan spisu JAMF (stan spisu komputera zaewidencjonowanego w oprogramowaniu Jamf Pro w ciągu ostatnich 24 godzin)
* Wersja systemu operacyjnego
* Identyfikator użytkownika w usłudze Azure Active Directory
* Zaszyfrowane (FileVault 2)
* Stan programu Gatekeeper
* Hasło: minimalna liczba zestawów znaków
* Wygaśnięcie hasła w dniach
* Typ hasła — prosty, alfanumeryczny lub nieznany
* Zapobieganie automatycznemu logowaniu
* Wymagana długość kodu dostępu
* Hasło: liczba poprzednich haseł, których nie można użyć ponownie
* Ochrona integralności systemu
* Czas ostatniego zaewidencjonowania
* Typ architektury
* Dostępne gniazda pamięci RAM
* Pojemność baterii
* Pamięć rozruchowa ROM
* Szybkość magistrali
* Rozmiar pamięci podręcznej
* Nazwa urządzenia
* Przyłączanie do domeny
* Identyfikator Jamf
* Adres MAC
* Marka
* Model
* Identyfikator modelu
* Szybkość karty sieciowej
* Liczba rdzeni
* Liczba procesorów
* System operacyjny
* Platforma
* Szybkość procesora
* Typ procesora
* Dodatkowy adres MAC
* Numer seryjny
* Wersja SMC
* Całkowita ilość pamięci RAM
* Identyfikator UDID
* Adres e-mail użytkownika

Urządzenie zarządzane za pomocą narzędzia Jamf można usunąć z konsoli usługi Intune, wybierając pozycję **Usuń** w widoku **Wszystkie urządzenia**. Zbiorcze usuwanie urządzeń można włączyć, zaznaczając wiele urządzeń i klikając pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki
Zapoznaj się z informacjami na temat [usuwania urządzenia zarządzanego za pomocą narzędzia Jamf w dokumentacji programu Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Możesz również wypełnić bilet pomocy technicznej dla [obsługi Jamf](https://www.jamf.com/support/) w celu uzyskania dodatkowej pomocy. 
