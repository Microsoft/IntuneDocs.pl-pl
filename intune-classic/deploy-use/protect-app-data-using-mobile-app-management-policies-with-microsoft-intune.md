---
title: "Ochrona danych aplikacji za pomocą zasad zarządzania aplikacjami mobilnymi"
description: "W tym temacie opisano, jak zasady zarządzania aplikacjami mobilnymi mogą pomagać w ochronie danych firmowych, zapobieganiu utracie danych i przechowywaniu osobno informacji osobistych i służbowych."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 40a6badf072c254f635a2656189d626e4f13a320
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2017
---
# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>Ochrona danych aplikacji przy użyciu zasad ochrony aplikacji w usłudze Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>Jak możesz chronić dane aplikacji
Pracownicy używają urządzeń przenośnych zarówno do celów służbowych, jak i prywatnych. Umożliwiając pracownikom wydajną pracę, warto jednocześnie zapobiegać nieumyślnej lub umyślnej utracie danych.  Dobrze też mieć możliwość ochrony danych firmowych, do których pracownicy uzyskują dostęp za pomocą urządzeń, którymi nie zarządzamy.

Aby lepiej chronić dane firmy, możesz skorzystać z zasad ochrony aplikacji w usłudze Intune. Ponieważ zasady ochrony aplikacji w usłudze Intune są **niezależne od wszelkich rozwiązań do zarządzania urządzeniami przenośnymi (MDM, mobile device management)**, możesz użyć zasad zarządzania aplikacjami mobilnymi (MAM, mobile application management) do ochrony danych firmy bez względu na to, czy urządzenia zostały zarejestrowane w rozwiązaniach do zarządzania urządzeniami. Wdrażając **zasady na poziomie aplikacji**, można ograniczyć dostęp do zasobów firmy i objęcia danych kontrolą działu IT.

Zasady ochrony aplikacji można skonfigurować dla aplikacji uruchomionej na urządzeniach, które są:

-   **Zarejestrowane w usłudze Microsoft Intune:** urządzenia w tej kategorii są przeważnie urządzeniami należącymi do firmy.

-   **Zarejestrowane w rozwiązaniu do zarządzania urządzeniami przenośnymi (MDM) innej firmy:** urządzenia w tej kategorii są przeważnie urządzeniami należącymi do firmy.

    > [!NOTE]
    > Nie zaleca się stosowania zasad ochrony aplikacji w połączeniu z rozwiązaniami do zarządzania aplikacjami mobilnymi lub rozwiązań z bezpiecznym kontenerem innych firm.

-   **Niezarejestrowane w żadnym rozwiązaniu do zarządzania urządzeniami przenośnymi:** urządzenia w tej kategorii są zazwyczaj urządzeniami należącymi do pracowników, które nie są zarządzane lub nie zostały zarejestrowane w usłudze Intune ani innych rozwiązaniach MDM.

> [!IMPORTANT]
> Możesz tworzyć zasady ochrony aplikacji dla aplikacji mobilnych pakietu Office łączących się z usługą Office 365. Zasady ochrony aplikacji nie są obsługiwane w przypadku aplikacji łączących się z lokalnymi usługami Exchange, Skype dla firm lub SharePoint.

## <a name="benefits-of-using-app-protection-policies"></a>Zalety stosowania zasad ochrony aplikacji

-   **Pomagają chronić dane firmy na poziomie aplikacji.** Ponieważ zarządzanie aplikacjami mobilnymi nie wymaga zarządzania urządzeniami, dane firmy można chronić zarówno na urządzeniach zarządzanych, jak i niezarządzanych. Zarządzanie skupia się na tożsamości użytkownika, co eliminuje konieczność zarządzania urządzeniem.

-   **Zasady nie mają wpływu na produktywność użytkownika i nie są stosowane podczas korzystania z aplikacji w kontekście prywatnym.** Zasady są stosowane wyłącznie w kontekście służbowym, co daje możliwość ochrony danych firmowych bez ingerowania w dane prywatne.

Stosowanie rozwiązań MDM jednocześnie z zasadami ochrony aplikacji jest możliwe i daje dodatkowe korzyści. Firmy mogą równocześnie korzystać z zasad MAM z rozwiązaniem MDM lub bez niego. Na przykład pracownik może korzystać z telefonu otrzymanego od firmy oraz z prywatnego tabletu. W takiej sytuacji telefon firmowy jest zarejestrowany w rozwiązaniu MDM i chroniony przez zasady ochrony aplikacji, natomiast urządzenie prywatne jest chronione tylko przez zasady ochrony aplikacji.

- **Rozwiązanie MDM zapewnia ochronę urządzenia.** Możesz na przykład zastosować zabezpieczenie dostępu do urządzenia numerem PIN lub wdrożyć na urządzeniu aplikacje zarządzane. Możesz również wdrażać aplikacje na urządzeniach za pośrednictwem rozwiązania MDM, aby mieć lepszą kontrolę nad zarządzaniem aplikacjami.

- **Zasady ochrony aplikacji zapewniają ochronę warstwy aplikacji.** Na przykład możesz mieć zasadę, która wymaga zastosowania numeru PIN w celu otwarcia aplikacji w kontekście służbowym, chroni dane przed udostępnieniem innym aplikacjom i uniemożliwia zapisywanie firmowych danych aplikacji w prywatnej lokalizacji magazynu.

## <a name="devices-that-support-mam"></a>Urządzenia, które obsługują zasady MAM
Zasady ochrony aplikacji są obecnie obsługiwane w następujących systemach operacyjnych:
-   System iOS 8.1 lub nowszy
-   System Android 4 lub nowszy

>[!NOTE]
>Urządzenia z systemem Windows nie są obsługiwane w rozwiązaniu do zarządzania aplikacjami mobilnymi bez scenariusza rejestracji. Jednak podczas rejestrowania urządzeń z systemem Windows 10 w usłudze Intune możesz użyć rozwiązania Windows Information Protection, które oferuje podobne funkcje. Aby uzyskać szczegółowe informacje, zobacz [Protect your enterprise data using Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip) (Chronienie danych przedsiębiorstwa przy użyciu rozwiązania Windows Information Protection).


##  <a name="how-app-protection-policies-protect-app-data"></a>W jaki sposób zasady ochrony aplikacji chronią dane aplikacji

###  <a name="apps-without-app-protection-policies"></a>Aplikacje bez zasad ochrony aplikacji

![Obraz pokazujący, że dane mogą swobodnie przemieszczać się między aplikacjami, jeśli nie wdrożono zasad ochrony aplikacji](../media/Apps_without_MAM_policies.png)

Jeśli korzystasz z aplikacji bez ograniczeń, dane firmowe i prywatne mogą ulec wymieszaniu. Dane firmowe mogą więc trafić na przykład do magazynu osobistego lub zostać przesłane do aplikacji pozostających poza Twoją kontrolą, co może grozić utratą danych. Strzałki na rysunku oznaczają nieograniczone przemieszczanie się danych między aplikacjami (firmowymi i prywatnymi) oraz do lokalizacji magazynu.

### <a name="data-protection-with-app-protection-policies"></a>Ochrona danych za pomocą zasad ochrony aplikacji

![Obraz pokazujący sposób ochrony danych firmowych po zastosowaniu zasad ochrony aplikacji](../media/Apps_with_mobile_app_policies.png)

Zasady ochrony aplikacji umożliwiają zapobieganie zapisywaniu danych firmy w lokalnym magazynie urządzenia i ograniczanie ruchu danych do innych aplikacji, które nie są chronione przy użyciu zasad ochrony aplikacji. Ustawienia zasad ochrony aplikacji obejmują:
- Zasady przenoszenia danych, takie jak **Nie zezwalaj na używanie polecenia Zapisz jako** i **Ogranicz wycinanie, kopiowanie i wklejanie**.
- Ustawienia zasad dostępu, takie jak **Wymagaj prostego numeru PIN w celu udzielenia dostępu** i **Blokuj uruchamianie aplikacji zarządzanych na urządzeniach ze zdjętymi zabezpieczeniami systemu lub odblokowanym dostępem do konta administratora**.

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>Ochrona danych za pomocą zasad ochrony aplikacji na urządzeniach zarządzanych przez rozwiązanie MDM

![Obraz pokazujący sposób działania zasad ochrony aplikacji na urządzeniach BYOD](../media/MAM_BYOD_November.png)

**Dla urządzeń przenośnych zarejestrowanych w rozwiązaniu MDM**: na powyższym diagramie przedstawiono warstwy ochrony oferowane łącznie przez rozwiązanie do zarządzania urządzeniami przenośnymi i zasady ochrony aplikacji.

Rozwiązanie MDM:

-   Rejestruje urządzenie.

-   Wdraża aplikacje na urządzeniu.

-   Na bieżąco zapewnia zgodność urządzenia i zarządzanie nim.

**Korzyści wynikające ze stosowania zasad ochrony aplikacji:**

-   Wspomagają ochronę danych firmy przed wyciekiem do aplikacji i usług dla konsumentów.

-   Stosują ograniczenia (zapisz jako, schowek, numer PIN itp.) do aplikacji mobilnych.

-   Wymazują dane firmowe z aplikacji, nie usuwając tych aplikacji z urządzenia.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Ochrona danych za pomocą zasad ochrony aplikacji dla urządzeń bez rejestracji

![Obraz pokazujący sposób działania zasad ochrony aplikacji na urządzeniach zarządzanych](../media/MAM_ManagedDevices_November.png)

Kolejny rysunek przedstawia sposób działania zasad ochrony danych na poziomie aplikacji bez rozwiązania MDM.

W przypadku urządzeń BYOD niezarejestrowanych w żadnym rozwiązaniu MDM zasady ochrony aplikacji mogą pomóc w ochronie danych firmowych na poziomie aplikacji.

Należy jednak wziąć pod uwagę następujące ograniczenia:

-   Na urządzeniach nie można wdrażać aplikacji. Użytkownik musi uzyskać aplikacje ze sklepu.

-   Na urządzeniach nie można dostarczać profili certyfikatów.

-   Na urządzeniach nie można wprowadzać ustawień firmowych sieci Wi-Fi i VPN.


## <a name="multi-identity"></a>Wiele tożsamości

Aplikacje, które obsługują wiele tożsamości, umożliwiają uzyskiwanie dostępu do tych samych aplikacji przy użyciu różnych kont (służbowych i osobistych), podczas gdy zasady ochrony aplikacji są stosowane tylko wtedy, gdy aplikacje są używane w kontekście służbowym.  

Jeśli na przykład użytkownik uruchamia aplikację OneDrive przy użyciu konta służbowego, nie może przenieść plików do lokalizacji magazynu osobistego. Jeśli jednak użytkownik korzysta z usługi OneDrive przy użyciu konta osobistego, może bez ograniczeń kopiować i przenosić dane z usługi OneDrive w wersji do użytku osobistego.  

- Dowiedz się więcej o aplikacjach, które obsługują [zarządzanie aplikacjami mobilnymi (MAM) i wiele tożsamości](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) za pomocą usługi Intune.

##  <a name="next-steps"></a>Następne kroki
- [Przygotowywanie do konfigurowania zasad ochrony aplikacji](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Tworzenie i wdrażanie zasad ochrony aplikacji przy użyciu usługi Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)