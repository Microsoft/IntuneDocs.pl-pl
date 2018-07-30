---
title: Inspekcja, eksportowanie i usuwanie danych osobowych
description: Dowiedz się, jak przeprowadzać inspekcję, eksportować i usuwać dane osobowe.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bea51227798e239bb74154e4d97e3efd6d55f807
ms.sourcegitcommit: cefa84efd3003fa5a0ef0c2dce6206a6a411a1ec
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35232271"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Inspekcja, eksportowanie i usuwanie danych osobowych w usłudze Intune

Administratorzy usługi Intune mogą śledzić działania dotyczące danych osobowych za pomocą dzienników inspekcji. Administratorzy mogą również eksportować i usuwać dane osobowe.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Inspekcja danych osobowych

Dzienniki inspekcji zapewniają administratorom dzierżawy rekordy działań generujących zmiany w usłudze Microsoft Intune. Dzienniki inspekcji są dostępne dla wielu działań zarządzania oraz zazwyczaj dla akcji tworzenia, aktualizowania (edytowania), usuwania i przypisywania. Można również przeglądać zadania zdalne, które generują zdarzenia inspekcji. Te dzienniki inspekcji mogą zawierać dane osobowe użytkowników, których urządzenia są zarejestrowane w usłudze Intune.  

Ze względów bezpieczeństwa usługa Intune może przechowywać dzienniki inspekcji dla działań użytkowników i urządzeń przez okres jednego roku. Te dzienniki są automatycznie usuwane po upływie jednorocznego okresu przechowywania.

Aby przeglądać dzienniki inspekcji, zobacz [Dzienniki inspekcji dla działań usługi Intune](monitor-audit-logs.md). 

Administratorzy nie mogą usuwać dzienników inspekcji.

Te zdarzenia inspekcji są przechowywane przez jeden rok. Administratorzy dzierżawy mogą zażądać dzienników inspekcji, korzystając z [tego formularza żądania obsługi](https://privacy.microsoft.com/en-US/privacy-questions?).

## <a name="export-personal-data"></a>Eksportowanie danych osobowych

Administratorzy mogą eksportować dane osobowe użytkownika końcowego, w tym konta, dane usługi i skojarzone dzienniki, aby spełniać żądania wynikające z praw osób, których dane dotyczą. To Ty i Twoja organizacja decydujecie, czy udostępnić osobie, której dane dotyczą, kopię jej danych osobowych, czy istnieje zgodny z prawem powód biznesowy, aby ich nie udostępniać. Jeśli zdecydujesz się na udostępnienie tych informacji, możesz dostarczyć osobie kopię oryginalnego dokumentu, odpowiednio zredagowaną wersję lub zrzut ekranu przedstawiający fragmenty, które uznasz za stosowne do udostępnienia.

Dane osobowe użytkownika można wyeksportować w następujący sposób: 
- Używając bloku urządzeń usługi Intune MDM w celu wyeksportowania listy urządzeń. Dane urządzenia można także skopiować bezpośrednio.
- Używając [skryptu Export-IntuneData.ps1](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Usuwanie danych osobowych użytkownika końcowego

Istnieją trzy sposoby usuwania danych osobowych z zarządzania usługi Intune:
- Usuwanie użytkownika z usługi Azure Active Directory
- Resetowanie urządzenia do ustawień fabrycznych
- Samodzielne usunięcie się użytkownika

### <a name="delete-a-user-from-intune"></a>Usuwanie użytkownika z usługi Intune

Aby usunąć dane osobowe użytkownika końcowego z usługi Intune, administrator musi [usunąć użytkownika z usługi Azure Active Directory (AAD)](https://docs.microsoft.com/en-us/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad). Gdy użytkownik zostanie usunięty z usługi AAD (całkowicie usunięty), usługa Intune otrzyma sygnał o usunięciu od usługi AAD, a następnie automatycznie rozpocznie czyszczenie wszystkich danych osobowych tego użytkownika z usługi Intune. Informacje użytkownika zostaną usunięte z usługi Intune w ciągu 30 dni od akcji usunięcia.

### <a name="reset-device-to-factory-settings"></a>Resetowanie urządzenia do ustawień fabrycznych
Zresetowanie do ustawień fabrycznych powoduje przywrócenie oryginalnych ustawień fabrycznych dla wszystkich danych firmy i danych osobowych oraz ustawień. Jest to przydatne podczas przekazywania urządzenia następnemu pracownikowi. Usuwane są pliki użytkownika, aplikacje zainstalowane przez użytkownika i ustawienia inne niż domyślne. Te dane są usuwane z usługi Intune w ciągu 30 dni od akcji usunięcia.

### <a name="user-self-removal-from-intune-management"></a>Samodzielne usunięcie się użytkownika z zarządzania usługi Intune
Użytkownik może usunąć swoje urządzenie osobiste z systemem [Android lub Windows albo systemem firmy Apple](https://docs.microsoft.com/en-us/intune-user-help/unenroll-your-device-from-intune-android.md) z zarządzania usługi Intune bez pomocy administratora.   

### <a name="remove-company-data"></a>Usuwanie danych firmy
Usunięcie danych firmy powoduje usunięcie danych aprowizowanych przez usługę Intune, takich jak aplikacje firmy, dane dotyczące aplikacji, którymi zarządza usługa Intune, ustawienia zasad i profile poczty e-mail aprowizowane za pośrednictwem usługi Intune. Ta akcja nie powoduje usunięcia osobistych danych użytkownika z urządzenia.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Usuwanie dzierżawy z usługi Microsoft Intune

Jeśli klient dzierżawy usługi Intune anuluje swoje konto usługi Intune, wszystkie dane dzierżawy są usuwane w ciągu 180 dni od zamknięcia konta usługi Intune przez klienta. Jeśli dzierżawa usługi AAD jest skojarzona z innymi subskrypcjami dla przedsiębiorstw firmy Microsoft (platforma Azure, usługa Office 365), usuwane są tylko dane klienta usługi Intune. Zasób dzierżawy usługi AAD jest zachowywany do użytku przez inne subskrypcje. Jeśli konto usługi Intune jest jedyną subskrypcją skojarzoną z dzierżawą usługi AAD, dzierżawa zostanie usunięta wraz z wszystkimi zasobami i danymi klienta.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Usuwanie użytkownika w hybrydowym środowisku zarządzania urządzeniami mobilnymi (MDM)
Jeśli masz hybrydowe środowisko MDM (usługa Intune zintegrowana z programem Configuration Manager), musisz wykonać następujące czynności (w podanej kolejności), aby całkowicie usunąć użytkownika i jego dane z lokalnej usługi Active Directory, programu Configuration Manager i usługi Intune.

1. Usuń użytkownika z lokalnej usługi Active Directory (AD). Dzięki temu użytkownik przestanie być synchronizowany z usługą Azure AD, a także nie będzie już wykrywany przez funkcję odnajdywania programu Configuration Manager. 
2. Usuń użytkownika z poziomu konsoli programu Configuration Manager, aby usunąć użytkownika i powiązane dane z programu Configuration Manager. W konsoli przejdź do obszaru **Zasoby i zgodność** > **Użytkownicy**, kliknij prawym przyciskiem myszy użytkownika, którego chcesz usunąć, a następnie kliknij polecenie **Usuń**.
3. [Usuń użytkownika z usługi AAD](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad), co spowoduje usunięcie użytkownika i powiązanych z nim danych jednocześnie z usługi Azure Active Directory i z usługi Intune. Gdy użytkownik zostanie usunięty z usługi AAD (całkowicie usunięty), usługa Intune otrzyma sygnał o usunięciu od usługi AAD, a następnie automatycznie rozpocznie czyszczenie wszystkich danych osobowych tego użytkownika z usługi Intune. Informacje użytkownika zostaną usunięte z usługi Intune w ciągu 30 dni od akcji usunięcia.

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak [przeprowadzać inspekcję danych osobowych oraz eksportować i usuwać je](privacy-data-audit-export-delete.md) w usłudze Intune.