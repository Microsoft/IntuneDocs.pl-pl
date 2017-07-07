---
title: "Wybieranie sposobu rejestrowania urządzeń z systemem iOS w usłudze Intune"
titleSuffix: Intune Azure preview
description: "Wersja zapoznawcza usługi Intune Azure: informacje dotyczące konfigurowania rejestracji urządzeń z systemem iOS w usłudze Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ee0ecf26a333ec441eb95e79473a9bf405e4120c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/23/2017


---

# <a name="choose-how-to-enroll-ios-devices"></a>Wybieranie sposobu rejestrowania urządzeń z systemem iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

W tym temacie opisano metody rejestrowania urządzeń z systemem iOS i wymagania wstępne dotyczące rejestracji.

Poniższe informacje pomogą zdecydować, której metody rejestracji urządzeń z systemem iOS użyć. Wszystkie poniższe metody, z wyjątkiem BYOD, służą do rejestrowania urządzeń firmowych.

**Wymaganie wstępne:** wymagany jest [certyfikat usługi Apple Push Notification Service](apple-mdm-push-certificate-get.md).

## <a name="user-owned-ios-devices-byod"></a>Urządzenia z systemem iOS należące do użytkownika (BYOD)

Jeśli użytkownik chce zarejestrować własne urządzenie BYOD (Bring Your Own Device, przynieś własne urządzenie), jedyna dostępna metoda rejestracji dla użytkowników polega na pobraniu aplikacji dla systemu iOS z portalu Portal firmy ze sklepu z aplikacjami i postępowaniu zgodnie z instrukcjami rejestracji w aplikacji. Po zarejestrowaniu użytkownicy mogą nawiązać połączenie z siecią firmową, przyłączyć się do domeny lub usługi Azure Active Directory i uzyskać dostęp do zasobów firmy. Możesz zablokować możliwość rejestrowania urządzeń z systemem iOS będących własnością użytkowników. Instrukcje zawiera temat [Ustawianie ograniczeń typu urządzeń](enrollment-restrictions-set.md#set-device-type-restrictions).

## <a name="apple-configurator"></a>Program Apple Configurator

W celu zarejestrowania urządzeń z systemem iOS można wyeksportować firmowy profil wdrażania, a następnie podłączyć te urządzenia przenośne do komputera Mac, na którym działa program [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017). Program Apple Configurator obsługuje dwa rodzaje rejestracji:

- **Rejestracja przy użyciu Asystenta ustawień**: przywracanie ustawień fabrycznych urządzenia i przygotowanie do konfiguracji przez nowego użytkownika. Ta metoda wymaga od administratora podłączenia urządzenia z systemem iOS przez port USB do komputera Mac z programem Apple Configurator w celu wstępnego skonfigurowania rejestracji. Urządzenia są następnie dostarczane do ich użytkowników, którzy korzystają z procesu Asystenta ustawień. W ramach tego procesu następuje konfiguracja urządzenia z poświadczeniami firmy lub szkoły użytkownika i ukończenie procesu rejestracji. Aby uzyskać więcej informacji, zobacz artykuł [Rejestracja urządzeń z systemem iOS za pomocą narzędzia Apple Configurator przy użyciu Asystenta ustawień](apple-configurator-setup-assistant-enroll-ios.md).

- **Rejestracja bezpośrednia**: tworzenie pliku zgodnego z programem Apple Configurator do użytku podczas przygotowywania urządzenia. Zarejestrowane urządzenie nie jest resetowane do ustawień fabrycznych i nie ma określonej przynależności do użytkownika. Aby zarejestrować urządzenia, administrator musi podłączyć urządzenie z systemem iOS przez port USB do komputera Mac z uruchomionym programem Apple Configurator. Aby uzyskać więcej informacji, zobacz artykuł [Bezpośrednie rejestrowanie urządzeń z systemem iOS przy użyciu programu Apple Configurator](apple-configurator-direct-enroll-ios.md).

## <a name="use-the-device-enrollment-program-dep"></a>Użycie programu Device Enrollment Program (DEP)

Program DEP wdraża bezprzewodowo profil rejestracji na urządzeniach zakupionych w ramach tego programu. Gdy użytkownik uruchamia na urządzeniu Asystenta ustawień, jest ono rejestrowane w usłudze Intune. Użytkownicy nie mogą wyrejestrowywać urządzeń zarejestrowanych w programie DEP. Aby uzyskać więcej informacji, zobacz artykuł [Enroll iOS devices using Device Enrollment Program](device-enrollment-program-enroll-ios.md) (Rejestracja urządzeń z systemem iOS przy użyciu programu Device Enrollment Program).

## <a name="use-the-device-enrollment-manager-dem"></a>Korzystanie z menedżera rejestracji urządzeń (DEM)
Menedżer rejestracji urządzeń jest typem konta użytkownika, które umożliwia rejestrację maksymalnie 1000 urządzeń oraz zarządzanie nimi. Istniejących użytkowników dodaje się do konta menedżera rejestracji urządzeń w celu nadania im tych funkcji. Każde urządzenie, które rejestruje użytkownik DEM, korzysta z pojedynczej licencji usługi Intune. Aby uzyskać więcej informacji, zobacz artykuł [Enroll devices using device enrollment manager](device-enrollment-manager-enroll.md) (Rejestracja urządzeń przy użyciu menedżera rejestracji urządzeń).
