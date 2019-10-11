---
title: Dodawanie ustawień niestandardowych do urządzeń z systemem Android Enterprise w usłudze Microsoft Intune — Azure | Microsoft Docs
description: Dodaj lub utwórz profil niestandardowy dla urządzeń z system Android Enterprise do tworzenia w usłudze Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: baa202ba5fdb554af56724279456cf43961ff82d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735171"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Używanie ustawień niestandardowych dla urządzeń z systemem Android Enterprise w usłudze Microsoft Intune

Za pomocą usługi Microsoft Intune można dodawać lub tworzyć ustawienia niestandardowe dla urządzeń z profilem roboczym Android Enterprise przy użyciu „profilu niestandardowego”. Profile niestandardowe to funkcja w usłudze Intune. Służą one do dodawania ustawień i funkcji urządzeń, które nie są wbudowane w usłudze Intune.

Profile niestandardowe systemu Android Enterprise używają ustawień jednolitego identyfikatora zasobów Open Mobile Alliance (OMA-URI, Open Mobile Alliance Uniform Resource Identifier) w celu kontrolowania funkcji na urządzeniach z systemem Android Enterprise. Te ustawienia są zwykle używane przez producentów urządzeń przenośnych w celu kontrolowania tych funkcji.

Usługa Intune obsługuje ograniczoną liczbę profilów niestandardowych przedsiębiorstwa systemu Android, w tym:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [Tworzenie profilu sieci Wi-Fi z użyciem klucza wstępnego](wi-fi-profile-shared-key.md) ma kilka przykładów.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [Tworzenie profilu sieci VPN dla aplikacji](android-pulse-secure-per-app-vpn.md) zawiera kilka przykładów.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: zobacz [przykład](#example) (w tym artykule).

Jeśli potrzebujesz dodatkowych ustawień, zobacz [OEMConfig for Android Enterprise](android-oem-configuration-overview.md).

W tym artykule pokazano, jak utworzyć profil niestandardowy dla urządzeń z systemem Android Enterprise. Zawiera także przykład profilu niestandardowego, który blokuje kopiowanie i wklejanie.

## <a name="create-the-profile"></a>Tworzenie profilu

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Wybierz pozycję **Konfiguracja urządzeń** > **Profile** > **Utwórz profil**.
3. Podaj następujące ustawienia:

    - **Nazwa**: wprowadź nazwę profilu, na przykład `android enterprise custom profile`
    - **Opis**: wprowadź opis profilu
    - **Platforma**: wybierz system **Android Enterprise**
    - **Typ profilu**: wybierz pozycję **Niestandardowy**

4. W obszarze **Niestandardowe ustawienia OMA-URI** wybierz pozycję **Dodaj**. Podaj następujące ustawienia:

    - **Nazwa**: wprowadź unikatową nazwę dla ustawienia identyfikatora OMA-URI, aby możne je było łatwo odnaleźć.
    - **Opis elementu**: wprowadź opis ułatwiający identyfikację ustawienia oraz zawierający inne ważne szczegóły.
    - **OMA-URI**: wprowadź identyfikator OMA-URI, którego chcesz używać jako ustawienia.
    - **Typ danych**: wprowadź typ danych używany w przypadku tego ustawienia identyfikatora OMA-URI. Dostępne opcje:

      - String
      - Ciąg (plik XML)
      - Data i godzina
      - Integer
      - Liczba zmiennoprzecinkowa
      - Boolean
      - Base64 (plik)

    - **Wartość**: wprowadź wartość danych, którą chcesz skojarzyć z wprowadzonym identyfikatorem OMA-URI. Wartość zależy od wybranego typu danych. Jeśli na przykład wybrano opcję **Data i godzina**, wybierz wartość za pomocą selektora daty.

    Po dodaniu ustawień możesz wybrać pozycję **Eksportuj**. Wybranie pozycji **Eksportuj** spowoduje utworzenie listy wszystkich dodanych wartości w pliku wartości rozdzielanych przecinkami (CSV).

5. Wybierz przycisk **OK**, aby zapisać zmiany. W razie potrzeby kontynuuj dodawanie ustawień.
6. Po zakończeniu wybierz pozycję **OK** > **Utwórz**, aby utworzyć profil usługi Intune. Po utworzeniu profil będzie widoczny na liście **Konfiguracja urządzenia — profile**.

## <a name="example"></a>Przykład

W tym przykładzie utworzysz profil niestandardowy, który ogranicza możliwość wykonywania akcji kopiowania i wklejania między aplikacjami służbowymi i osobistymi na urządzeniach z systemem Android Enterprise.

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Wybierz pozycję **Konfiguracja urządzeń** > **Profile** > **Utwórz profil**.
3. Podaj następujące ustawienia:

    - **Nazwa**: wprowadź nazwę profilu, na przykład `android ent block copy paste custom profile`.
    - **Opis:** wprowadź opis profilu.
    - **Platforma**: wybierz system **Android Enterprise**.
    - **Typ profilu**: wybierz pozycję **Niestandardowy**.

4. W obszarze **Niestandardowe ustawienia OMA-URI** wybierz pozycję **Dodaj**. Podaj następujące ustawienia:

    - **Nazwa**: wprowadź na przykład nazwę `Block copy and paste`.
    - **Opis**: wprowadź na przykład opis `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: wprowadź wartość `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Typ danych**: wybierz **wartość logiczną**, aby wartość identyfikatora OMA-URI była równa **True** lub **False**.
    - **Wartość**: wybierz wartość **True**.

5. Po wprowadzeniu ustawień środowisko powinno wyglądać podobnie do przedstawionego na poniższym obrazie:

    ![Blokowanie kopiowania i wklejania dla profilu służbowego systemu Android.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Po przypisaniu tego profilu do zarządzanych urządzeń z systemem Android Enterprise kopiowanie i wklejanie danych między aplikacjami z profilu służbowego i osobistego będzie zablokowane.

## <a name="next-steps"></a>Następne kroki

Profil został utworzony, ale nie wykonuje jeszcze żadnych czynności. Teraz należy [przypisać profil](device-profile-assign.md).

Zobacz jak [utworzyć profil na urządzeniach z systemem Android](../custom-settings-android.md).