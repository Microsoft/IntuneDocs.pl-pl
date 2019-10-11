---
title: Ograniczenia urządzeń w usłudze Microsoft Intune dotyczące systemu Windows 10 Team
titleSuffix: ''
description: Dowiedz się więcej na temat ograniczeń dotyczących urządzeń z systemem Windows 10 Team.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35dbc39d01780f23dcc325a203d7a9c33b98e296
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734807"
---
# <a name="microsoft-intune-windows-10-team-device-restriction-settings"></a>Ustawienia ograniczeń urządzeń z systemem Windows 10 Team w usłudze Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

W tym artykule opisano ustawienia ograniczeń urządzeń w usłudze Microsoft Intune, które można skonfigurować dla urządzeń z systemem Windows 10 Team.


## <a name="apps-and-experience"></a>Aplikacje i środowisko

- **Włącz ekran, gdy ktoś jest w pokoju** — umożliwia automatyczne wyjście urządzenia z trybu uśpienia, gdy czujnik wykryje czyjąś obecność w pomieszczeniu.
- **Informacje o spotkaniu wyświetlane na ekranie powitalnym** — włącz tę opcję, aby wybrać informacje wyświetlane na kafelku Spotkania na ekranie powitalnym. Można:
  - wybrać opcję **Pokaż tylko organizatora i czas**;
  - wybrać opcję **Pokaż organizatora, czas i temat (temat jest ukryty w przypadku spotkań prywatnych)** .
- **Adres URL obrazu tła ekranu powitalnego** — włącz to ustawienie, aby na ekranie **Witamy** urządzeń z systemem Windows 10 Team wyświetlić niestandardowe tło z określonego adresu URL.<br>Obraz musi być w formacie PNG, a adres URL musi rozpoczynać się od **https://** .

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights** — usługa Azure Operational Insights, która wchodzi w skład pakietu Microsoft Operations Manager, umożliwia zbieranie, przechowywanie i analizowanie danych pliku dziennika z urządzeń z systemem Windows 10 Team.
Aby połączyć z usługą Azure Operational Insights, należy określić **identyfikator obszaru roboczego** i **klucz obszaru roboczego**.

## <a name="maintenance"></a>Konserwacja

- **Okno konserwacji dla aktualizacji** — konfiguruje okno czasowe, w którym można przeprowadzać aktualizacje na urządzeniu. Dla tego okresu możesz skonfigurować **czas rozpoczęcia** i **czas trwania w godzinach** (od 1 do 5 godzin).

## <a name="wireless-projection"></a>Projekcja bezprzewodowa

- **Numer PIN projekcji bezprzewodowej** — określa, czy przed korzystaniem z funkcji projekcji bezprzewodowej na urządzeniu jest wymagane wprowadzenie numeru PIN.
- **Projekcja bezprzewodowa Miracast** — jeśli chcesz zezwolić urządzeniu z systemem Windows 10 Team na korzystanie z projekcji przy użyciu urządzeń z funkcją Miracast, wybierz tę opcję.
- **Kanał projekcji bezprzewodowej Miracast** — wybierz kanał Miracast, który jest używany do nawiązywania połączenia.


## <a name="next-steps"></a>Następne kroki

Skorzystaj z informacji w artykule [Jak skonfigurować ustawienia ograniczeń urządzeń](../device-restrictions-configure.md), aby zapisać i przypisać profil do użytkowników i urządzeń.