---
title: Przenoszenie danych konta z magazynu danych usługi Intune
titlesuffix: Microsoft Intune
description: Zrozumienie sposobu tworzenia kopii zapasowej danych z magazynu danych w usłudze Intune podczas przenoszenia konta.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: f1b2af2723ddb4c89f7f3d6409ced12f7a16883a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Przenoszenie danych konta z magazynu danych usługi Intune 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Żądanie przeniesienia konta oznacza również żądanie przeniesienia centrum danych do innej lokalizacji. Po przeniesieniu magazyn danych zostanie zresetowany i rozpocznie się rejestrowanie danych w nowej lokalizacji (na podstawie dnia rozpoczęcia przeniesienia). Aby utworzyć kopię zapasową danych z poprzedniego magazynu danych, **przed** przeniesieniem konta wykonaj następujące kroki. W większości tabel magazynu danych dane są przechowywane przez 30 dni, dlatego żadne przerwy danych w tych tabelach nie będą dostępne 30 dni po przeniesieniu konta. Aby dowiedzieć się więcej na temat okresów przechowywania dla określonych tabel, zobacz temat [Model danych magazynu danych](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Tworzenie kopii zapasowych danych z magazynu danych 

Aby utworzyć kopię zapasową danych z magazynu danych, należy za pomocą interfejsu API magazynu danych zapisać dane z magazynu danych w pliku *CSV*:  

1. Jeśli korzystasz z interfejsu API magazynu danych po raz pierwszy, wykonaj jednorazowy proces opisany w artykule, [Pobieranie danych z interfejsu API magazynu danych usługi Intune za pomocą klienta REST](reports-proc-data-rest.md).
2. Aby pobrać wszystkie dane do plików CSV, skorzystaj z przykładu dotyczącego programu PowerShell zatytułowanego [Dostęp do magazynu danych usługi Intune za pomocą programu PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell). 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Tworzenie kopii zapasowej wykresów trendu z portalu Azure

Niektóre wykresy trendów w widoku portalu Azure zostaną zresetowane. Można utworzyć ich kopię zapasową, uruchamiając następujący skrypt w programie **Graph**:   

### <a name="terms--conditions-acceptance-reports"></a>Raporty akceptacji warunków użytkowania
1. W portalu Azure przejdź do opcji **Microsoft Intune** -> **Rejestracja urządzeń** -> **Warunki użytkowania**.
2. Dla każdego elementu **Warunki użytkowania** wybierz opcję **Raport akceptacji**, a następnie **Eksportuj**.
3. Zapisz raport lokalnie.
 
### <a name="app-protection-reports"></a>Raporty ochrony aplikacji  
1. W portalu Azure przejdź do opcji **Microsoft Intune** -> **Aplikacje mobilne** -> **Stan ochrony aplikacji**.
2. Aby zapisać każdy raport, kliknij ikonę pobierania (⤓).

### <a name="device-configuration-charts"></a>Wykresy konfiguracji urządzeń 
1. W portalu Azure przejdź do opcji **Microsoft Intune** -> **Konfiguracja urządzenia**.
2. Za pomocą programu Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) pobierz dane źródłowe wykresów. 
    - Aby dla każdego urządzenia uzyskać informacje na temat stanu wdrożenia profili konfiguracji wszystkich urządzeń, zobacz temat [Stan wdrożenia urządzenia](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content).

    - Aby dla każdego użytkownika uzyskać informacje na temat stanu wdrożenia profili konfiguracji wszystkich urządzeń, zobacz temat [Stan wdrożenia użytkownika](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content).

    - Aby uzyskać informacje na temat stanu wdrożenia profilu, zobacz temat [Udostępnianie stanu wdrożenia](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview).
  
    > [!NOTE]
    > Aby uzyskać dostęp do konfiguracji urządzenia i informacji o stanie wdrożenia, należy mieć prawidłowy token uwierzytelniania.

## <a name="device-enrollment-charts"></a>Wykresy rejestrowania urządzeń
1. W portalu Azure przejdź do opcji **Microsoft Intune** -> **Rejestrowanie urządzeń**.
2. Za pomocą programu Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) pobierz dane źródłowe wykresów.
    - Aby uzyskać informacje na temat stanu rejestracji, zobacz 
    - Aby uzyskać informacje na temat głównych błędów dotyczących rejestrowania w tym tygodniu, 
    - Aby uzyskać informacje na temat stanu rejestrowania, skopiuj to [zapytanie dotyczące stanu rejestracji](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content) i wklej je do programu [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
    - Aby uzyskać informacje na temat głównych błędów dotyczących rejestrowania w tym tygodniu, skopiuj to [zapytanie dotyczące błędów rejestracji](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content) i wklej je do programu [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

    > [!NOTE]
    > Aby uzyskać dostęp do danych dotyczących rejestracji urządzeń, należy mieć prawidłowy token uwierzytelniania. 

## <a name="after-a-data-warehouse-account-move"></a>Po przeniesieniu konta magazynu danych

Po przeniesieniu konta magazynu danych w usłudze Intune będzie widoczna informacja o tym, że magazyn danych został zresetowany, a dane są teraz przechowywane w nowej lokalizacji. Wykresy i opcje eksportu zostaną zresetowane oraz zostanie wyświetlone powiadomienie, po kliknięciu którego nastąpi bezpośrednie przekierowanie do artykułu wyjaśniającego, dlaczego wykresy zostały zresetowane.  

## <a name="data-warehouse-move-example"></a>Przykład przenoszenia magazynu danych 

Klient X składa żądanie rozpoczęcia przenoszenia konta w dniu 6 stycznia 2018 roku. W odpowiedzi na to żądanie klient otrzyma łącze do dokumentacji, w której szczegółowo opisano czynności wymagane do utworzenia kopii zapasowej swojego poprzedniego magazynu danych. W dniu 6 stycznia 2018 roku magazyn danych i obsługiwane wykresy zostaną zresetowane i rozpocznie się przechowywanie danych w nowym centrum danych. 

## <a name="next-steps"></a>Następne kroki

 - Dowiedz się, [co nowego w usłudze Intune w każdym tygodniu](whats-new.md). Możesz również sprawdzić informacje o nadchodzących zmianach, ważnych powiadomieniach dotyczących usługi oraz poprzednich wersjach.
 - Zapoznaj się z [blogiem usługi Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).