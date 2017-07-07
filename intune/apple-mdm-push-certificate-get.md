---
title: Uzyskiwanie certyfikatu wypychania MDM firmy Apple
titleSuffix: Intune on Azure
description: "Opis czynności niezbędnych w celu uzyskania certyfikatu wypychania MDM firmy Apple przeznaczonego do zarządzania urządzeniami z systemem iOS za pomocą usługi Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3df23e1f29543701cf3806a8fecc132ef3ac4f43
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2017
---
# <a name="get-an-apple-mdm-push-certificate"></a>Uzyskiwanie certyfikatu wypychania MDM firmy Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usługa Intune umożliwia zarządzanie urządzeniami przenośnymi typu iPad, iPhone oraz komputerami Mac i zapewnia użytkownikom dostęp do poczty e-mail oraz aplikacji firmy. Aby zarządzać urządzeniami z systemem iOS i komputerami Mac, wymagany jest certyfikat usługi wypychania MDM. Po dodaniu certyfikatu do usługi Intune użytkownicy mogą zainstalować aplikację Portal firmy, aby zarejestrować swoje urządzenia. Możesz również skonfigurować zarządzanie urządzeniami iOS należącymi do firmy za pomocą programu rejestracji urządzeń firmy Apple lub zarejestrować urządzenia, na przykład przy użyciu programu Apple Configurator. Aby uzyskać więcej informacji o opcjach rejestracji, zobacz [Wybieranie sposobu rejestracji urządzenia z systemem iOS](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Procedura uzyskiwania certyfikatu
W portalu usługi Intune wybierz kolejno pozycje **Rejestracja urządzenia** > **Rejestracja Apple** **Certyfikat wypychania Apple MDM**, a następnie wykonaj w witrynie Azure Portal kroki wymienione poniżej.

**Krok 1. Pobierz żądanie podpisania certyfikatu usługi Intune wymagane do utworzenia certyfikatu wypychania MDM firmy Apple.**<br>
Wybierz pozycję **Pobierz żądanie CSR**, aby pobrać plik .csr i zapisać go lokalnie. Plik CSR jest używany na potrzeby żądania certyfikatu relacji zaufania w portalu Apple Push Certficates.

**Krok 2. Tworzenie certyfikatu wypychania MDM firmy Apple**<br>
Wybierz pozycję **Utwórz swój certyfikat push MDM**, aby przejść do portalu Apple Push Certificates. Zaloguj się przy użyciu firmowego identyfikatora Apple ID, aby utworzyć certyfikat wypychania z użyciem pliku csr. Po kliknięciu przycisku **Upload** (Przekaż) w witrynie Apple Push Certificates Portal otrzymasz plik z rozszerzeniem .json. Użyj tego pliku w odniesieniu do certyfikatu wypychania. Ukończ pobieranie, wróć do portalu wypychania certyfikatu firmy Apple, przejdź do obszaru Certificates for Third-Party Servers (Certyfikaty dla serwerów innych firm) i wybierz polecenie **Download** (Pobierz). Pobierz certyfikat wypychania (plik pem) i zapisz plik lokalnie.

> [!NOTE]
> Certyfikat jest skojarzony z identyfikatorem firmy Apple użytym do jego utworzenia. Najlepszym rozwiązaniem jest użycie firmowego identyfikatora firmy Apple na potrzeby zadań zarządzania. Nigdy nie należy używać osobistego identyfikatora firmy Apple.

**Krok 3. Wprowadź identyfikator firmy Apple użyty do utworzenia certyfikatu wypychania MDM firmy Apple.**

**Krok 4. Przejdź do pliku certyfikatu wypychania MDM firmy Apple, aby go przekazać.**<br>
Przejdź do pliku certyfikatu (.pem) i wybierz pozycję **Otwórz**, a następnie wybierz pozycję **Przekaż**. Dzięki certyfikatowi wypychania usługa Intune może rejestrować urządzenia z systemem iOS i zarządzać nimi, wypychając zasady do zarejestrowanych urządzeń przenośnych.

## <a name="renew-apple-mdm-push-certificate"></a>Odnawianie certyfikatu wypychania MDM firmy Apple
Certyfikat wypychania MDM firmy Apple jest ważny przez rok i musi być odnawiany co roku, aby zachować możliwość zarządzania urządzeniami z systemami iOS i macOS. Jeśli certyfikat wygaśnie, nie będzie można skontaktować się z zarejestrowanymi urządzeniami firmy Apple.

Certyfikat jest skojarzony z identyfikatorem firmy Apple użytym do jego utworzenia. Certyfikat wypychania MDM odnów przy użyciu tego samego identyfikatora firmy Apple, którego użyto do jego utworzenia.

> [!NOTE]
> Certyfikat jest skojarzony z identyfikatorem firmy Apple użytym do jego utworzenia. Najlepszym rozwiązaniem jest użycie firmowego identyfikatora firmy Apple na potrzeby zadań zarządzania. Nigdy nie należy używać osobistego identyfikatora firmy Apple.

1. W portalu usługi Intune wybierz pozycję **Rejestracja urządzenia** > **Rejestracja Apple**, a następnie wybierz pozycję **Certyfikat wypychania Apple MDM**.
2. Wybierz pozycję **Pobierz żądanie CSR**, aby pobrać plik .csr i zapisać go lokalnie. Plik CSR jest używany na potrzeby żądania certyfikatu relacji zaufania w portalu Apple Push Certficates.
3. Znajdź certyfikat, który chcesz odnowić, i wybierz opcję **Odnów**.
4. Na ekranie **Odnawianie certyfikatu wypychania** wpisz notatki, aby w przyszłości łatwiej zidentyfikować certyfikat, wybierz pozycję **Wybierz plik**, aby wskazać nowo pobrany plik csr i wybierz opcję **Przekaż**.
5. Na ekranie **Potwierdzenie** wybierz pozycję **Pobierz** i zapisz plik pem na urządzeniu lokalnym.
6. W portalu usługi Intune na platformie Azure wybierz ikonę przeglądania **Certyfikat wypychania Apple MDM**, wybierz plik pem pobrany od firmy Apple, a następnie wybierz opcję **Przekaż**.

Twój certyfikat wypychania MDM firmy Apple będzie mieć stan **Aktywny** i 365 dni do wygaśnięcia.