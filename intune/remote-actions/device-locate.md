---
title: Znajdowanie zgubionych urządzeń z systemem iOS za pomocą usługi Microsoft Intune — Azure | Microsoft Docs
description: Znajdź zagubione lub skradzione urządzenia z systemem iOS przy użyciu funkcji lokalizacji urządzenia w usłudze Microsoft Intune. Uzyskaj szczegółowe informacje dotyczące zabezpieczeń i ochrony prywatności podczas korzystania z akcji Zlokalizuj urządzenie.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e3ab83c282c1e97e80a783f569410253bdf7d42
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727951"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Znajdowanie zgubionych lub skradzionych urządzeń z systemem iOS przy użyciu usługi Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Akcja **Zlokalizuj urządzenie** umożliwia wyświetlenie na mapie lokalizacji zgubionego lub skradzionego urządzenia z systemem iOS. Urządzenie musi działać w trybie nadzorowanym. Przed użyciem tej akcji należy się upewnić, że urządzenie jest w [trybie zgubienia](device-lost-mode.md).

## <a name="supported-platforms"></a>Obsługiwane platformy

- iOS 9.3 i nowsze

Ta funkcja nie jest obsługiwana w następujących systemach: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Lokalizowanie zgubionego lub skradzionego urządzenia

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Wybierz pozycję **Urządzenia**, a następnie wybierz pozycję **Wszystkie urządzenia**.
4. Z listy zarządzanych urządzeń wybierz urządzenie z systemem iOS, a następnie wybierz pozycję **...więcej**. Następnie wybierz zdalną akcję **Zlokalizuj urządzenie**.
5. Po zlokalizowaniu urządzenia jego lokalizacja będzie wyświetlana w bloku **Zlokalizuj urządzenie**.
    ![Zrzut ekranu lokalizowania urządzenia przy użyciu usługi Intune na platformie Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Aktywowanie alertu dźwiękowego trybu utraty na urządzeniu z systemem iOS

Jeśli użytkownik zgubi urządzenie z systemem iOS 9.3 lub nowszym, można zdalnie wyzwolić odtwarzanie dźwięku alertu w urządzeniu, aby ułatwić jego znalezienie. Urządzenie musi działać w [trybie utraty](device-lost-mode.md).

W obszarze usługi [Intune w witrynie Azure Portal](https://aka.ms/intuneportal) wybierz kolejno pozycje **Urządzenia** > **Wszystkie urządzenia** > wybierz urządzenie z systemem iOS > **Omówienie** > **Więcej** > **Odtwórz dźwięk trybu utraty (tylko tryb nadzorowany)** .

Ten dźwięk będzie odtwarzany aż do wyłączenia przez użytkownika dźwięku na urządzeniu lub zakończenia trybu utraty na urządzeniu.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Informacje o zabezpieczeniach i prywatności w trybie zgubienia oraz akcjach lokalizowania urządzenia
- Do momentu włączenia tej akcji żadne informacje o lokalizacji urządzenia nie są wysyłane do usługi Intune.
- Po użyciu akcji lokalizacji urządzenia współrzędne geograficzne urządzenia można pobrać za pomocą interfejsu API programu Graph.
- Dane są przechowywane przez 24 godziny, a następnie usuwane. Nie można ręcznie usunąć danych lokalizacji.
- Dane lokalizacji są szyfrowane zarówno podczas przechowywania, jak i podczas przesyłania.
- Podczas konfigurowania trybu zgubienia można dostosować komunikat wyświetlany na ekranie blokady. W tym komunikacie, aby pomóc znalazcy urządzenia, należy podać szczegółowe informacje umożliwiające zwrot zgubionego urządzenia.

## <a name="next-steps"></a>Następne kroki

Aby wyświetlić stan włączania lokalizowania urządzenia, otwórz obszar **Urządzenia** i wybierz pozycję **Akcje urządzenia**.