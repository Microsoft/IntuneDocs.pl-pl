---
title: Ustawienia poczty e-mail w usłudze Intune dla systemu Windows Phone 8.1
titleSuffix: ''
description: Dowiedz się więcej na temat ustawień usługi Intune służących do konfigurowania połączeń z pocztą e-mail na urządzeniach z systemem Windows Phone 8.1.
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
ms.openlocfilehash: e373f0bc511ee7296820bf161da759dedc18b311
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734560"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Ustawienia profilu poczty e-mail w usłudze Microsoft Intune dla urządzeń z systemem Windows Phone 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

W tym artykule opisano ustawienia profilu poczty e-mail, które możesz skonfigurować dla urządzeń z systemem Windows Phone 8.1.


- **Zastosuj wszystkie ustawienia tylko do systemu Windows Phone 8.1** — to ustawienie można skonfigurować w portalu klasycznym usługi Intune. W witrynie Azure Portal tego ustawienia nie można zmienić. Jeśli jest ono ustawione na wartość **Skonfigurowane**, wszystkie ustawienia zostaną zastosowane tylko do urządzeń z systemem Windows Phone 8.1. Jeśli jest ono ustawione na wartość **Nieskonfigurowane**, te ustawienia zostaną również zastosowane do urządzeń z systemem Windows 10 Mobile.
- **Serwer poczty e-mail** — nazwa hosta serwera programu Exchange.
- **Nazwa konta** — nazwa wyświetlana dla konta e-mail, jaka będzie wyświetlana użytkownikom na ich urządzeniach.
- **Atrybut nazwy użytkownika z usługi AAD** — jest to atrybut usługi Active Directory (AD) lub Azure AD, który jest używany do generowania nazwy użytkownika dla danego profilu e-mail. Uzupełnij pole **Podstawowy adres SMTP**, na przykład **user1@contoso.com** , lub **Główna nazwa użytkownika**, na przykład **użytkownik1** lub **user1@contoso.com** .
- **Atrybut adresu e-mail z usługi AAD** — określa, jak adres e-mail użytkownika jest generowany na poszczególnych urządzeniach. Wybierz pozycję **Podstawowy adres SMTP**, aby użyć podstawowego adresu SMTP do logowania do programu Exchange, lub wybierz pozycję **Główna nazwa użytkownika**, aby użyć pełnej głównej nazwy jako adresu e-mail.


## <a name="security-settings"></a>Ustawienia zabezpieczeń

- **Protokół SSL** — użyj komunikacji SSL (Secure Sockets Layer) podczas wysyłania i otrzymywania wiadomości e-mail oraz komunikacji z serwerem programu Exchange.



## <a name="synchronization-settings"></a>Ustawienia synchronizacji

- **Liczba wiadomości e-mail do synchronizacji** — wybierz liczbę dni, z których chcesz zsynchronizować pocztę e-mail, lub wybierz pozycję **Nieograniczone**, aby synchronizować wszystkie dostępne wiadomości e-mail.
- **Harmonogram synchronizacji** — wybierz harmonogram, według którego urządzenia będą synchronizować dane z serwera programu Exchange. Możesz również wybrać pozycję **W momencie nadejścia nowych wiadomości**, która powoduje synchronizowanie zaraz po odebraniu, lub pozycję **Ręcznie**, jeśli użytkownik urządzenia ma inicjować synchronizację.

## <a name="content-sync-settings"></a>Ustawienia synchronizacji zawartości

- **Typ zawartości do zsynchronizowania** — wybierz typ zawartości, który chcesz zsynchronizować z urządzeniem:
  - **Kontakty**
  - **Kalendarz**
  - **Zadania**