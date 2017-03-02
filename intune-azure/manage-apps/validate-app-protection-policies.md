---
title: Weryfikowanie zasad ochrony aplikacji
titleSuffix: Intune Azure preview
description: "Wersja zapoznawcza usługi Intune Azure: w tym temacie opisano sposób testowania i sprawdzania, czy zasady ochrony aplikacji są poprawnie skonfigurowane i działają zgodnie z oczekiwaniami."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 086ea61de3423be254d3d8f2224c4ad96d90385d
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-validate-your-app-protection-policy-setup"></a>Sposób sprawdzania poprawności ustawień zasad ochrony aplikacji

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Ten temat zawiera informacje dotyczące sprawdzania występowania problemów po skonfigurowaniu zasad ochrony aplikacji. Te wskazówki dotyczą zasad ochrony aplikacji w **wersji zapoznawczej** portalu Azure Portal.

### <a name="checking-for-symptoms"></a>Sprawdzanie pod kątem objawów
Zgłaszanie problemów przez użytkowników jest mało prawdopodobne, ponieważ ochrona aplikacji to narzędzie ochrony danych. W przypadku problemu z konfiguracją ochrony aplikacji użytkownik będzie mieć nieograniczony dostęp, taki jaki miałby bez stosowania ochrony aplikacji, i nie będzie świadomy wystąpienia problemu. Z tego powodu zaleca się sprawdzenie poprawności konfiguracji ochrony aplikacji przez pilotażowe wdrożenie zasad ochrony aplikacji dla małej grupy użytkowników, którzy celowo przetestują ograniczenia związane z ochroną aplikacji.


### <a name="what-to-check"></a>Co należy sprawdzić

Jeśli wyniki testów pokazują, że zachowanie zasad ochrony aplikacji nie jest zgodne z oczekiwanym, zaleca się sprawdzenie następujących kwestii:

- Czy użytkownicy mają licencje na ochronę aplikacji?
- Czy użytkownicy mają licencje usługi O365?
- Stan każdej aplikacji użytkowników objętej ochroną aplikacji. Możliwe stany aplikacji to **Zaewidencjonowano** i **Nie zaewidencjonowano**.

#### <a name="user-app-protection-status"></a>Stan ochrony aplikacji użytkownika
1. W portalu Azure Portal wybierz pozycję **Zarządzaj aplikacjami** > **Monitoruj** >  **Stan użytkownika ochrony aplikacji** > **użytkownicy**.

2. Wybierz użytkownika z listy lub wyszukaj i wybierz użytkownika, a następnie wybierz pozycję **Wybierz użytkownika**. W górnej części kolumny **Zgłaszanie aplikacji** widoczna będzie informacja, czy użytkownik ma licencję na ochronę aplikacji. Poniżej zobaczysz, czy użytkownik ma licencję usługi O365 i sprawdzisz stan aplikacji dla wszystkich urządzeń użytkownika.



### <a name="what-to-do"></a>Co należy zrobić
Poniżej przedstawiono akcje do wykonania na podstawie stanu użytkownika:

- Jeśli użytkownik nie ma licencji na ochronę aplikacji, przypisz licencję usługi Intune do użytkownika.
- Jeśli użytkownik nie ma licencji usługi O365, uzyskaj licencję dla użytkownika.
- Jeśli aplikacja użytkownika ma stan **Niezaewidencjonowane**, sprawdź, czy zasady ochrony aplikacji zostały poprawnie skonfigurowane dla tej aplikacji.
- Upewnij się, że te warunki są stosowane do wszystkich użytkowników, do których mają być stosowane zasady ochrony aplikacji.

### <a name="see-also"></a>Zobacz także

[Co to są zasady ochrony aplikacji w usłudze Intune?](app-protection-policies.md)
