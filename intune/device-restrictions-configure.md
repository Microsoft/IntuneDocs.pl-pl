---
title: "Konfigurowanie ustawień ograniczeń dotyczących urządzeń w usłudze Intune"
titleSuffix: Intune on Azure
description: "Informacje dotyczące konfigurowania ustawień i funkcji na zarządzanych urządzeniach przy użyciu usługi Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8652b2b6db340f3b0cddcf538fa418c8774b1d6c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Jak skonfigurować ustawienia ograniczeń dotyczących urządzeń w usłudze Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Ograniczenia dotyczące urządzeń pozwalają na kontrolę szerokiego zakresu ustawień i funkcji, którymi można zarządzać w ramach wielu kategorii, w tym dotyczących zabezpieczeń, przeglądarki, sprzętu i ustawień związanych z udostępnianiem danych. Na przykład można utworzyć profil ograniczenia dotyczącego urządzeń, który uniemożliwia użytkownikom urządzeń z systemem iOS dostęp do aparatu urządzenia.

Skorzystaj z informacji zawartych w tym temacie, aby uzyskać podstawową wiedzę z zakresu konfigurowania profilów ograniczeń dotyczących urządzeń, a następnie zapoznaj się z tematami dotyczącymi poszczególnych platform, aby dowiedzieć się więcej o charakterystyce urządzeń.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Tworzenie profilu urządzenia zawierającego ustawienia ograniczeń dotyczących urządzeń

1. Zaloguj się do portalu Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku **Intune** wybierz pozycję **Konfiguruj urządzenia**.
2. W bloku **Konfiguracja urządzeń** wybierz kolejno pozycje **Zarządzaj** > **Profile**.
3. W bloku profilów wybierz pozycję **Utwórz profil**.
4. W bloku **Utwórz profil** uzupełnij pola **Nazwa** i **Opis** odnoszące się do profilu ograniczeń urządzenia.
5. Z listy rozwijanej **Platforma** wybierz platformę urządzenia, do której chcesz zastosować ustawienia niestandardowe. Obecnie dla ustawień ograniczeń dotyczących urządzeń można wybrać jedną z następujących platform:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 lub nowszy**
    - **Windows 10 lub nowszy**
6. Z listy rozwijanej **Typ profilu** wybierz pozycję **Ograniczenia dotyczące urządzeń**. Aby utworzyć profil ograniczeń dotyczących urządzeń z systemem Windows 10 Team, np. urządzeń Surface Hub, wybierz pozycję **Ograniczenia dotyczące urządzeń (Windows 10 Team)**.
7. Ustawienia, które można skonfigurować, różnią się w zależności od wybranej platformy. Szczegółowe informacje na temat ustawień każdej z platform podano w następujących tematach:
    - [Ustawienia systemu Android](device-restrictions-android.md)
    - [Ustawienia systemu iOS](device-restrictions-ios.md)
    - [macOS settings](device-restrictions-macos.md) (Ustawienia systemu macOS)
    - [Ustawienia systemu Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 settings](device-restrictions-windows-10.md) (Ustawienia systemu Windows 10)
    - [Windows 10 Team settings](device-restrictions-windows-10-teams.md) (Ustawienia systemu Windows 10 Team)
    - [Ustawienia programu Android for Work](device-restrictions-android-for-work.md)
8. Gdy skończysz, wróć do bloku **Utwórz profil** i wybierz pozycję **Utwórz**.

Profil zostanie utworzony i wyświetlony w bloku listy profilów.
Wskazówki umożliwiające przypisanie tego profilu do grup znajdują się w artykule [How to assign device profiles](device-profile-assign.md) (Sposoby przypisywania profilów urządzeń).

## <a name="example-of-device-restriction-settings"></a>Przykład ustawienia ograniczeń dotyczących urządzenia

W tym przykładzie ogólnym utworzysz zasadę ograniczeń dotyczących urządzeń, która będzie blokowała w urządzeniach użycie wbudowanej aplikacji aparatu.

![Wyłączanie aparatu urządzenia z systemem Android](./media/disable-android-camera.png)
