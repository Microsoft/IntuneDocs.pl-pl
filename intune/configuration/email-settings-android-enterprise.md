---
title: Ustawienia poczty e-mail dla urządzeń z systemem Android Enterprise w usłudze Microsoft Intune — Azure | Microsoft Docs
description: Twórz profile konfiguracji poczty e-mail urządzeń, które korzystają z serwerów programu Exchange i pobierają atrybuty z usługi Azure Active Directory. Włącz protokół SSL lub SMIME, uwierzytelniaj użytkowników przy użyciu certyfikatów lub nazwy użytkownika/hasła oraz synchronizuj pocztę e-mail i harmonogramy w urządzeniach z profilami służbowymi systemu Android za pomocą usługi Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62fad2a881332470a6c3e95b7cdcab0403ba1839
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734664"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Ustawienia urządzeń z systemem Android Enterprise do konfigurowania poczty e-mail, uwierzytelniania i synchronizacji w usłudze Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

W tym artykule wymieniono i opisano różne ustawienia poczty e-mail, którymi można sterować na urządzeniach z systemem Android Enterprise. W ramach rozwiązania do zarządzania urządzeniami mobilnymi (MDM) możesz skorzystać z tych ustawień, aby skonfigurować serwer poczty e-mail lub użyć protokołu SSL do szyfrowania wiadomości e-mail oraz określić inne elementy.

Jako administrator usługi Intune możesz utworzyć i przypisać ustawienia poczty e-mail do urządzeń z systemem Android Enterprise w profilu służbowym.

Aby dowiedzieć się więcej na temat profilów poczty e-mail w usłudze Intune, zobacz temat [Konfigurowanie ustawień poczty e-mail](email-settings-configure.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Utwórz [profil konfiguracji urządzenia](email-settings-configure.md#create-a-device-profile) (Wybierz profil służbowy) lub Utwórz [zasady konfiguracji aplikacji](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android Enterprise

- **Aplikacja poczty e-mail**: wybierz pozycję **Gmail** lub **Nine Work**
- **Serwer poczty e-mail**: nazwa hosta serwera programu Exchange. Na przykład wprowadź `outlook.office365.com`.
- **Atrybut nazwy użytkownika z usługi AAD**: ta nazwa to atrybut pobierany przez usługę Intune z usługi Azure Active Directory (Azure AD). Usługa Intune dynamicznie generuje nazwę użytkownika używaną przez ten profil. Dostępne opcje:

  - **Główna nazwa użytkownika**: pobiera nazwę, taką jak `user1` lub `user1@contoso.com`
  - **Nazwa użytkownika**: pobiera tylko nazwę, taką jak `user1`

- **Atrybut adresu e-mail z usługi AAD**: ta nazwa to atrybut adresu e-mail pobierany przez usługę Intune z usługi Azure AD. Usługa Intune dynamicznie generuje adres e-mail używany przez ten profil. Dostępne opcje:
  - **Główna nazwa użytkownika**: używa pełnej nazwy głównej, takiej jak `user1@contoso.com` lub `user1`, jako adresu e-mail.
  - **Podstawowy adres SMTP**: używa podstawowego adresu SMTP, takiego jak `user1@contoso.com`, do logowania się do programu Exchange.

- **Metoda uwierzytelniania** — wybierz metodę uwierzytelniania stosowaną w profilu e-mail: **Certyfikaty** lub **Nazwa użytkownika i hasło**.
  - W przypadku wybrania opcji **Certyfikat** wybierz wcześniej utworzony profil certyfikatu SCEP lub PKCS klienta, który będzie używany do uwierzytelniania połączenia z programem Exchange.
- **Protokół SSL**: wybierz pozycję **Włącz**, aby użyć komunikacji SSL (Secure Sockets Layer) podczas wysyłania i odbierania wiadomości e-mail oraz komunikacji z serwerem programu Exchange.
- **Liczba wiadomości e-mail do synchronizacji**: wybierz czas, z którego chcesz zsynchronizować pocztę e-mail. Możesz też wybrać pozycję **Nieograniczone**, aby zsynchronizować wszystkie dostępne wiadomości e-mail.
- **Typ zawartości do synchronizowania** (tylko aplikacja Nine Work): wybierz dane, które chcesz zsynchronizować na urządzeniach. Dostępne opcje:
  - **Kontakty**: wybierz pozycję **Włącz**, aby zezwolić użytkownikom końcowym na synchronizowanie kontaktów z urządzeniami.
  - **Kalendarz**: wybierz pozycję **Włącz**, aby zezwolić użytkownikom końcowym na synchronizowanie kalendarza z urządzeniami.
  - **Zadania**: wybierz pozycję **Włącz**, aby zezwolić użytkownikom końcowym na synchronizowanie dowolnych zadań z urządzeniami.

## <a name="next-steps"></a>Następne kroki

[Przypisywanie profilu](device-profile-assign.md) i [monitorowanie jego stanu](device-profile-monitor.md).

Można również utworzyć profile poczty e-mail dla urządzeń z systemem [Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 i nowszym](email-settings-windows-10.md) oraz [Windows Phone 8.1](email-settings-windows-phone-8-1.md).