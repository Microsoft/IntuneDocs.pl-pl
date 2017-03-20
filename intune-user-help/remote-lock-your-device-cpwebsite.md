---
title: "Blokowanie urządzenia z poziomu aplikacji Portal firmy | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
searchScope:
- User help
ROBOTS: 
ms.reviewer: mamoriss
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 10c7bc5461c746ab50e83c2ffc590b89efe75e5f
ms.openlocfilehash: 6910fd7b67fcd934b35a81cdbd372b2069fb3493
ms.lasthandoff: 03/13/2017


---

# <a name="remotely-lock-your-device-from-the-company-portal-website"></a>Zdalne blokowanie urządzenia z poziomu witryny sieci Web Portal firmy

Wypadki się zdarzają, a urządzenia czasem giną lub się gubią. Jeśli urządzenie zostanie skradzione lub zagubione, podstawowe obawy będą wiązać się z możliwością uzyskania przez dowolne osoby dostępu do zapisanych na nim informacji — bez względu na lokalizację urządzenia.

[!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

Aby zapewnić sobie bezpieczeństwo danych, można zablokować urządzenie przy użyciu opcji zdalnego blokowania dostępnej z poziomu [witryny sieci Web Portal firmy](http://portal.manage.microsoft.com). Zdalne blokowanie działa w urządzeniach z systemem operacyjnym:

* Android
* iOS
* macOS
* Windows 10 Mobile (jeśli w urządzeniu był już ustawiony kod dostępu)
* Windows Phone 8.1 (jeśli w urządzeniu był już ustawiony kod dostępu)

## <a name="to-use-remote-lock-to-lock-your-device"></a>Aby zablokować urządzenie przy użyciu funkcji zdalnego blokowania:

1.    W [witrynie sieci Web Portal firmy](http://portal.manage.microsoft.com) naciśnij przycisk __menu__ ![Mały obrazek przycisku menu, trzy poziome paski ułożone równolegle do siebie.](/Intune/whats-new/media/CP_hamburger_menu.png), a następnie wybierz pozycję __Moje urządzenia__.

  ![Obraz witryny sieci Web Portal firmy ze znajdującym się po lewej stronie ekranu rozwiniętym menu bocznym oraz przyciskami Strona główna, Wszystkie aplikacje, Moje urządzenia, Pomoc techniczna i Wyloguj.](/media/iwp-expanded-sidebar.png)

2. Na stronie __Moje urządzenia__ wybierz nazwę urządzenia, które chcesz zablokować.

  ![Zrzut ekranu strony Moje urządzenia przedstawiający kilka niezidentyfikowanych urządzeń oraz znajdujący się poniżej transparent z monitem o zarejestrowanie urządzeń nieznajdujących się na liście lub zidentyfikowanie tych niezidentyfikowanych.](./media/macOS_enroll_002_tap_here_banner.png)

3.    Urządzenie wyświetli się w oknie podręcznym. Naciśnij przycisk **Zdalne blokowanie**.

    ![Wszystkie opcje dla wybranego urządzenia w witrynie sieci Web Portal firmy, w tym Zmień nazwę, Usuń, Resetuj urządzenie, Resetuj kod dostępu i Zdalne blokowanie. ](./media/iwp-screen-with-all-options.png)

4.    Zostanie wyświetlone powiadomienie z informacją, że masz zamiar zablokować urządzenie. Wybierz opcję **Zdalne blokowanie**. Witryna sieci Web Portal firmy podejmie próbę zablokowania urządzenia.

    Po wybraniu opcji **Zdalne blokowanie** zostanie wyświetlony komunikat „Zdalne blokowanie oczekuje”.  Gdy zdalne blokowanie zakończy się powodzeniem, stan zmieni się na „Zdalne blokowanie pomyślne”.

    Stan zdalnego blokowania jest wyświetlany w trzech miejscach:

    * Obszar powiadomień witryny sieci Web.
    * Strona **Szczegóły** urządzenia.
    * Kafelek, na którym jest wyświetlana nazwa urządzenia, w sekcji **Moje urządzenia**.

> [!Note]
> Jeśli zostanie wyświetlone powiadomienie „Zdalne blokowanie nie powiodło się”, zaczekaj kilka minut, a następnie spróbuj ponownie zablokować urządzenie. Po podjęciu kolejnej próby stan zmieni się ponownie na „Zdalne blokowanie oczekuje”. Jeśli ponowienie próby nie rozwiąże problemu, konieczny będzie kontakt z administratorem IT organizacji.

Jeśli po użyciu opcji zdalnego blokowania odnajdziesz swoje urządzenie i zechcesz je odblokować, po prostu wprowadź kod dostępu.

Nadal potrzebujesz pomocy? Skontaktuj się z administratorem IT. Informacje kontaktowe są dostępne w [witrynie sieci Web Portal firmy](http://portal.manage.microsoft.com).
