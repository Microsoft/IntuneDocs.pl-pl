---
title: "Rozpoczynanie pracy z użytkownikami"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc1c4f6d18fd78f455be8e333bb765080184c908
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-users"></a>Rozpoczynanie pracy z użytkownikami

![Ogólny użytkownik na platformie Azure](/intune/media/generic-intune-user.png)

Usługa Azure AD służy do zarządzania grupami obiektów należących do organizacji, takimi jak urządzenia i aplikacje, a także grupami użytkowników. Możliwe jest grupowanie użytkowników lub urządzeń, dzięki czemu nie będzie konieczne indywidualne zarządzanie każdym urządzeniem. Pozwoli to w łatwy sposób przypisać aplikacje i ustawienia do dużej liczby użytkowników i urządzeń.

## <a name="how-do-i-create-a-user"></a>Jak utworzyć użytkownika?

1. Zaloguj się do [portalu Azure](https://portal.azure.com).
2. Przy użyciu funkcji **Wyszukiwanie zasobów** wyszukaj **użytkowników i grupy**.
3. Po otwarciu bloku **Użytkownicy i grupy** wybierz pozycję **Wszyscy użytkownicy**, a następnie wybierz pozycję **+Nowy użytkownik**.
4. Wprowadź szczegółowe informacje dotyczące użytkownika, takie jak **nazwa** i **nazwa użytkownika**. Część nazwy użytkownika stanowiąca nazwę domeny musi być początkową, domyślną nazwą domeny, „contoso.onmicrosoft.com”, lub zweryfikowaną, niefederacyjną nazwą domeny, na przykład „contoso.com”.
5. W obszarze **Grupy** wybierz grupę testową, do której zostanie dodany użytkownik.
6. Zapisz automatycznie wygenerowane hasło użytkownika, aby użyć go do zalogowania się na urządzeniu testowym. To hasło należy przekazać użytkownikom, aby mogli zmienić je na normalne, łatwiejsze do zapamiętania hasło.
7. W bloku **Użytkownik** wybierz pozycję **Utwórz**.

## <a name="assigning-licenses-to-users"></a>Przypisywanie licencji użytkownikom

Po utworzeniu użytkownika należy użyć [portalu usługi Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), aby przypisać licencję usługi Intune do tego użytkownika. Jeśli użytkownikom nie zostanie przypisana licencja, nie będą oni mogli zarejestrować swojego urządzenia w systemie zarządzania.

1. Zaloguj się do [portalu usługi Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) przy użyciu tych samych poświadczeń, które zostały użyte do zalogowania się do usługi Intune.
2. Wybierz pozycję **Użytkownicy** > **Aktywni użytkownicy**, a następnie wybierz wcześniej utworzonego użytkownika.
3. Może chwilę potrwać, aż wszystkie informacje dotyczące użytkownika zostaną załadowane. Po ich załadowaniu wybierz pozycję **Edytuj** dla **licencji produktu** użytkownika.
4. Przypisz użytkownikowi **lokalizację**, a następnie przełącz usługę Intune na wartość **Włączona**.

 > [!NOTE]
 > Spowoduje to użycie jednej z Twoich licencji na potrzeby tego użytkownika. Jeśli używasz swojego działającego środowiska, możesz później wyłączyć używanie tej licencji, aby przypisać ją ponownie do rzeczywistego użytkownika.

5. Wybierz pozycję **Zapisz**.