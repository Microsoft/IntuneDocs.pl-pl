---
title: "Obejście blokady aktywacji systemu iOS przy użyciu usługi Intune"
titleSuffix: Intune on Azure
description: "Informacje dotyczące użycia usługi Intune w celu obejścia blokady aktywacji systemu iOS, by uzyskać dostęp do zablokowanych urządzeń."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b92949efca2e4dac5836755e2f32b0527d4762d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2017
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Obejście blokady aktywacji na nadzorowanych urządzeniach z systemem iOS przy użyciu usługi Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usługa Microsoft Intune ułatwia zarządzanie blokadą aktywacji systemu iOS — funkcją aplikacji Znajdź mój iPhone dla urządzeń z systemem iOS 8.0 lub nowszym. Blokada aktywacji jest włączana automatycznie w przypadku otwarcia przez użytkownika aplikacji Znajdź mój iPhone na urządzeniu. Jeśli ta funkcja została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:

- Wyłączenie aplikacji Znajdź mój iPhone
- Wymazanie urządzenia
- Ponowne uaktywnienie urządzenia

## <a name="how-activation-lock-affects-you"></a>Wpływ blokady aktywacji na Twoje działania

Blokada aktywacji pomaga w zabezpieczaniu urządzeń z systemem iOS i zwiększa szanse na odzyskanie urządzenia w razie jego zgubienia lub kradzieży, jednak może ona powodować problemy dla administratora systemu informatycznego. Na przykład:

- Użytkownik konfiguruje blokadę aktywacji na urządzeniu. Następnie użytkownik odchodzi z firmy i zwraca urządzenie. Bez identyfikatora Apple ID i hasła użytkownika nie ma możliwości ponownego uaktywnienia urządzenia.
- Potrzebny jest raport ze wszystkimi urządzeniami, na których włączono blokadę aktywacji.
- Podczas odświeżania urządzenia w organizacji chcesz ponownie przypisać niektóre urządzenia do innego działu. Możesz przypisywać ponownie tylko urządzenia, na których nie włączono blokady aktywacji.

Aby pomóc w rozwiązaniu tych problemów, firma Apple wprowadziła obejście blokady aktywacji w systemie iOS 7.1. Dzięki temu można usunąć blokadę aktywacji z nadzorowanych urządzeń bez identyfikatora Apple ID i hasła użytkownika. Nadzorowane urządzenie może wygenerować unikatowy kod obejścia blokady aktywacji, który jest przechowywany na serwerze aktywacji firmy Apple.

>[!TIP]
>Tryb nadzorowany dla urządzeń z systemem iOS umożliwia zablokowanie urządzenia za pomocą programu Apple Configurator w celu ograniczenia funkcji urządzenia do określonych celów biznesowych. Tryb nadzorowany jest przeznaczony praktycznie tylko dla urządzeń należących do firm.

Więcej informacji o blokadzie aktywacji można znaleźć w [witrynie internetowej firmy Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Jak usługa Intune pomaga w zarządzaniu blokadą aktywacji
Usługa Intune może wysłać żądanie dotyczące stanu blokady aktywacji na nadzorowanych urządzeniach z systemem iOS 8.0 lub nowszym. Tylko w przypadku urządzeń nadzorowanych usługa Intune może pobrać kod obejścia blokady aktywacji i wystawić go bezpośrednio na urządzeniu. Jeśli zawartość urządzenia została wyczyszczona, możesz bezpośrednio uzyskać dostęp do urządzenia, używając pustej nazwy użytkownika i kodu jako hasła.

**Wiąże się to z następującymi korzyściami dla firmy:**

- Użytkownik może korzystać z zabezpieczeń oferowanych przez aplikację Znajdź mój iPhone.
- Możesz umożliwić użytkownikom normalną pracę, wiedząc, że w razie konieczności zmiany przeznaczenia urządzenia można je wycofać lub odblokować.

## <a name="before-you-start"></a>Przed rozpoczęciem
Aby obejść blokadę aktywacji na urządzeniach, trzeba ją najpierw włączyć. Wykonaj następujące czynności:

1. Skonfiguruj profil ograniczeń dotyczących urządzeń w usłudze Intune dla systemu iOS przy użyciu informacji w temacie [Jak skonfigurować ustawienia ograniczeń dotyczących urządzeń w usłudze Microsoft Intune](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Włącz ustawienie trybu **Kiosk** dla opcji **Blokada aktywacji**.
3. Zapisz profil, a następnie przypisz go do urządzeń, na których chcesz zarządzać obejściem blokady aktywacji.


## <a name="how-to-use-activation-lock-bypass"></a>Jak korzystać z obejścia blokady aktywacji

>[!IMPORTANT]
>Po obejściu blokady aktywacji na urządzeniu zostanie automatycznie zastosowana nowa blokada aktywacji w przypadku otwarcia aplikacji Znajdź mój iPhone. Dlatego **musisz mieć fizyczny dostęp do urządzenia, aby móc wykonać tę procedurę**.

Akcja zdalna **Zastosuj obejście blokady aktywacji** dotycząca urządzenia w usłudze Intune powoduje usunięcie blokady aktywacji z urządzenia z systemem iOS bez identyfikatora Apple ID i hasła użytkownika. Po zastosowaniu obejścia blokady aktywacji urządzenie ponownie przejdzie w stan blokady aktywacji, gdy zostanie uruchomiona aplikacja Znajdź mój iPhone. Stosuj obejście blokady aktywacji tylko w sytuacji, gdy masz fizyczny dostęp do urządzenia.

1. Zaloguj się do portalu Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku **Intune** wybierz opcję **Urządzenia**.
4. W bloku **Urządzenia i grupy** wybierz pozycję **Wszystkie urządzenia**.
5. Z listy zarządzanych urządzeń wybierz nadzorowane urządzenie z systemem iOS, a następnie wybierz akcję zdalną **Zastosuj obejście blokady aktywacji** dla urządzenia.

Stan żądania odblokowania można sprawdzić na stronie szczegółów urządzenia w obciążeniu **Zarządzaj urządzeniami**.