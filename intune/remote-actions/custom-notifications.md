---
title: Wysyłanie powiadomień niestandardowych do użytkowników za pomocą usługi Microsoft Intune
titleSuffix: Microsoft Intune
description: Tworzenie i wysyłanie niestandardowych powiadomień push do użytkowników urządzeń z systemami iOS i Android przy użyciu usługi Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3c21e255db1142ec5ab15c99e8da6bc41de01cf
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728055"
---
# <a name="send-custom-notifications-in-intune"></a>Wysyłanie powiadomień niestandardowych w usłudze Intune  

Za pomocą usługi Microsoft Intune można wysyłać niestandardowe powiadomienia do użytkowników urządzeń zarządzanych z systemami iOS i Android. Te komunikaty są wyświetlane w postaci standardowych powiadomień push z aplikacji Portal firmy i aplikacji Microsoft Intune na urządzeniu użytkownika, podobnie jak powiadomienia z innych aplikacji wyświetlane na urządzeniu. Powiadomienia niestandardowe usługi Intune nie są obsługiwane na urządzeniach z systemem macOS ani Windows.   

Niestandardowe komunikaty powiadomień zawierają krótki tytuł i treść komunikatu składającą się maksymalnie z 500 znaków. Te komunikaty można dostosować do wszelkich celów komunikacji ogólnej.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Typowe scenariusze wysyłania powiadomień niestandardowych  

- Można również powiadomić wszystkich pracowników o zmianie harmonogramu, na przykład o zamknięciach budynków z powodu niesprzyjających warunków pogodowych.
- Wyślij powiadomienie do użytkownika pojedynczego urządzenia w celu przekazania pilnego żądania, takiego jak ponowne uruchomienie urządzenia w celu ukończenia instalacji aktualizacji. 

## <a name="considerations-for-using-custom-notifications"></a>Zagadnienia dotyczące korzystania z powiadomień niestandardowych

**Konfiguracja urządzeń** 

- Aby użytkownicy mogli odbierać powiadomienia niestandardowe, na urządzeniach musi być zainstalowana aplikacja Portal firmy lub aplikacja Microsoft Intune. Użytkownicy muszą także mieć skonfigurowane uprawnienia, aby umożliwić aplikacji Portal firmy lub aplikacji Microsoft Intune wysyłanie powiadomień push. W razie potrzeby aplikacje Portal firmy i Microsoft Intune mogą monitować użytkowników o zezwolenie na powiadomienia.  
- W systemie Android Usługi Google Play są wymaganą zależnością.  
- Urządzenie musi być zarejestrowane w usłudze MDM.

**Uprawnienia**:
- Aby wysyłać powiadomienia do grup, Twoje konto musi mieć następujące uprawnienia RBAC w usłudze Intune: *Organizacja ***Aktualizowanie **
- Aby wysyłać powiadomienia do urządzenia, Twoje konto musi mieć następujące uprawnienia RBAC w usłudze Intune: *Zadania zdalne* > **Wysyłanie powiadomień niestandardowych**.

**Tworzenie powiadomień**:  
- Aby utworzyć komunikat, użyj konta z przypisaną rolą usługi Intune obejmującą uprawnienie do **aktualizowania** w **organizacji**. Aby przypisać uprawnienia użytkownikowi, zobacz [Przypisania ról](../fundamentals/role-based-access-control.md#role-assignments)  
- Powiadomienia niestandardowe mają ograniczenia do 50 znaków w tytule i 500 znaków w treści komunikatu.  
- Usługa Intune nie zapisuje wysłanych komunikatów. Aby ponownie wysłać komunikat, należy go ponownie utworzyć.  
- Można wysłać maksymalnie 25 komunikatów do grup na godzinę. To ograniczenie obowiązuje na poziomie dzierżawy. To ograniczenie nie ma zastosowania w przypadku wysyłania powiadomień do użytkowników indywidualnych.
- Podczas wysyłania komunikatów do poszczególnych urządzeń można wysłać do tego samego urządzenia maksymalnie 10 komunikatów na godzinę. 
- Powiadomienia można wysyłać do wielu użytkowników lub urządzeń, przypisując powiadomienie do grup. W przypadku korzystania z grup każde powiadomienie można kierować bezpośrednio do maksymalnie 25 grup. Grupy zagnieżdżone nie są wliczane do tej liczby.  

  Grupy mogą obejmować użytkowników lub urządzenia, ale komunikaty są wysyłane tylko do użytkowników i do poszczególnych urządzeń z systemem iOS lub Android, które zostały zarejestrowane przez użytkownika.  
- Powiadomienia można wysyłać do pojedynczego urządzenia. Zamiast korzystać z grup wybiera się urządzenie, a następnie używa zdalnej [akcji urządzenia](device-management.md#available-device-actions) w celu wysłania powiadomienia niestandardowego.  

**Dostarczanie**:  
- Usługa Intune wysyła komunikaty do aplikacji Portal firmy lub aplikacji Microsoft Intune użytkowników, która następnie tworzy powiadomienie push. Użytkownicy nie muszą być zalogowani do aplikacji, aby powiadomienie zostało wypchnięte do urządzenia.  
- Usługa Intune oraz aplikacje Portal firmy i Microsoft Intune nie mogą zagwarantować dostarczania powiadomienia niestandardowego. Powiadomienia niestandardowe mogą pojawiać się nawet z kilkugodzinnym opóźnieniem, dlatego nie powinny być używane do przesyłania pilnych komunikatów.  
- Komunikaty powiadomień niestandardowych z usługi Intune są wyświetlane na urządzeniach jako standardowe powiadomienia push. Jeśli aplikacja Portal firmy jest otwarta na urządzeniu z systemem iOS w momencie odebrania powiadomienia, zostanie ono wyświetlone w aplikacji zamiast w postaci powiadomienia push.  
- W zależności od ustawień urządzenia powiadomienia niestandardowe mogą być widoczne na ekranach blokady na urządzeniach z systemami iOS i Android.  
- Na urządzeniach z systemem Android inne aplikacje mogą mieć dostęp do danych powiadomień niestandardowych. Nie używaj ich do przesyłania poufnych komunikatów.  
- Użytkownicy urządzenia, które zostało ostatnio wyrejestrowane, lub użytkownicy usunięci z grupy mogą nadal otrzymywać powiadomienia niestandardowe, które są następnie wysyłane do tej grupy.  Podobnie jeśli dodasz użytkownika do grupy po wysłaniu powiadomienia niestandardowego do tej grupy, nowo dodany użytkownik może otrzymać ten wysłany wcześniej komunikat powiadomienia.  

## <a name="send-a-custom-notification-to-groups"></a>Wysyłanie powiadomień niestandardowych do grup  

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) przy użyciu konta z uprawnieniami do tworzenia i wysyłania powiadomień, a następnie przejdź do pozycji **Urządzenia** > **Wysyłaj niestandardowe powiadomienia**.  

2. Na karcie Podstawy określ poniższe opcje, a następnie wybierz przycisk **Dalej**, aby kontynuować.  
   - **Tytuł** — określ tytuł powiadomienia. Tytuły mogą zawierać maksymalnie 50 znaków.  
   - **Treść** — wpisz komunikat. Komunikaty mogą zawierać maksymalnie 500 znaków.

   ![Tworzenie powiadomienia niestandardowego](./media/custom-notifications/custom-notifications.png)  

3. Na karcie **Przypisania** wybierz grupy, do których chcesz wysłać powiadomienie niestandardowe, a następnie wybierz przycisk Dalej, aby kontynuować.  

4. Na karcie **Przeglądanie + tworzenie** przejrzyj informacje, a następnie wybierz pozycję **Utwórz**, aby wysłać powiadomienie.  

Usługa Intune natychmiast przetwarza tworzone komunikaty. Jedynym potwierdzeniem wysłania komunikatu jest powiadomienie wyświetlane w usłudze Intune potwierdzające wysłanie powiadomienia niestandardowego.  

![Potwierdzenie wysłania powiadomienia](./media/custom-notifications/notification-sent.png)  

Usługa Intune nie śledzi wysyłanych powiadomień niestandardowych, a urządzenia nie rejestrują odbioru poza centrum powiadomień urządzenia.  

## <a name="send-a-custom-notification-to-a-single-device"></a>Wysyłanie powiadomień niestandardowych do pojedynczego urządzenia  

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) przy użyciu konta z uprawnieniami do tworzenia i wysyłania powiadomień, a następnie przejdź do pozycji **Urządzenia** > **Wszystkie urządzenia**.  

2. Wybierz urządzenie, do którego chcesz wysłać powiadomienie.  

3. Na stronie **Omówienie** urządzenia wybierz opcję **…Więcej** w lewym górnym rogu strony.  

4. Wybierz akcję urządzenia **Wyślij powiadomienie niestandardowe**, aby otworzyć okienko *Wyślij powiadomienie niestandardowe*, w którym można określić następujące szczegóły komunikatu:  

   - **Tytuł** — określ tytuł powiadomienia. Tytuły mogą zawierać maksymalnie 50 znaków.  
   - **Treść** — wpisz komunikat. Komunikaty mogą zawierać maksymalnie 500 znaków.  

5. Wybierz pozycję **Wyślij**, aby wysłać powiadomienie niestandardowe do urządzenia. W przeciwieństwie do powiadomień wysyłanych do grup nie następuje konfigurowanie przypisania ani przeglądanie komunikatu przed jego wysłaniem.  

Usługa Intune natychmiast przetwarza komunikat. Jedynym potwierdzeniem wysłania komunikatu jest powiadomienie usługi Intune, które otrzymasz w konsoli, zawierające tekst wysyłanego komunikatu.  

## <a name="receive-a-custom-notification"></a>Odbieranie powiadomień niestandardowych  

Na urządzeniu użytkownicy widzą komunikaty powiadomień niestandardowych wysyłanych przez usługę Intune jako standardowe powiadomienia push z aplikacji Portal firmy lub aplikacji Microsoft Intune. Te powiadomienia są podobne do powiadomień push otrzymywanych przez użytkowników z innych aplikacji na urządzeniu.  

Jeśli na urządzeniu z systemem iOS aplikacja Portal firmy jest otwarta w momencie odebrania powiadomienia, zostanie ono wyświetlone w aplikacji zamiast w postaci powiadomienia push.  

Powiadomienie pozostaje widoczne do momentu jego odrzucenia przez użytkownika.  

## <a name="next-steps"></a>Następne kroki  

[Zarządzanie urządzeniami](device-management.md)