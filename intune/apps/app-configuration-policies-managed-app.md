---
title: Zasady konfiguracji zarządzanych aplikacji bez rejestracji urządzeń
titleSuffix: Microsoft Intune
description: Dowiedz się, jak konfigurować zasady dla zarządzanych aplikacji bez rejestracji urządzeń.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7716eeb496567eb4e4a35a703b66597ed47e87a6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725845"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Dodawanie zasad konfiguracji aplikacji dla zarządzanych aplikacji bez rejestracji urządzeń

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Zasad konfiguracji aplikacji można używać z zarządzanymi aplikacjami, które obsługują zestaw SDK aplikacji usługi Intune, nawet na niezarejestrowanych urządzeniach. 

> [!NOTE]
> Aplikacje muszą zostać objęte zasadami Intune App Protection w celu odbierania zasad usługi App Configuration. Aby uzyskać więcej informacji na temat tworzenia zasad ochrony aplikacji usługi Intune, zobacz [Co to są zasady ochrony aplikacji?](app-protection-policy.md)

1. Zaloguj się do usługi [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Wybierz obciążenie **Aplikacje klienckie**.
4. Wybierz pozycję **Zasady konfiguracji aplikacji** w grupie **Zarządzaj**, a następnie wybierz przycisk **Dodaj**.
5. Ustaw następujące szczegóły:
    - **Nazwa**  
      — nazwa profilu, która będzie wyświetlana w witrynie Azure Portal
    - **Opis**  
      — opis profilu, który będzie wyświetlany w witrynie Azure Portal
    - **Typ rejestracji urządzenia**  
      Wybierz pozycję **Zarządzaj aplikacjami**.
6. Wybierz pozycję **Skojarzona aplikacja**, aby wybrać aplikację, którą chcesz skonfigurować. Wybierz aplikację z listy aplikacji zatwierdzonych i zsynchronizowanych z usługą Intune.
7. Dla każdego ustawienia konfiguracji obsługiwanego przez aplikację wpisz wartości w polach **Nazwa** i **Wartość**, a następnie wybierz przycisk wielokropka ( **...** ).  
    Aby usunąć konfigurację, wybierz przycisk wielokropka ( **...** ) i wybierz pozycję **Usuń**.  
    
Aplikacje współdziałające z zestawem SDK aplikacji usługi Intune obsługują konfiguracje oparte na parach klucz-wartość. Dodatkowe informacje na temat obsługiwanych konfiguracji klucz-wartość można znaleźć w dokumentacji dotyczącej poszczególnych aplikacji. Należy pamiętać, że można użyć tokenów dynamicznie wypełnianych danymi wygenerowanymi przez aplikację. Aby uzyskać informacje o programie Outlook dotyczące ustawień zasad konfiguracji aplikacji dla systemu iOS, zobacz temat [Manage Outlook for iOS app configuration with Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx) (Zarządzanie programem Outlook w celu konfiguracji aplikacji dla systemu iOS w usłudze Microsoft Intune).

## <a name="configuration-values-for-using-tokens"></a>Wartości konfiguracji na potrzeby używania tokenów

Usługa Intune może generować pewne tokeny i wysyłać je do aplikacji zarządzanej. Na przykład jeśli konfiguracja aplikacji obejmuje użycie ustawienia poczty e-mail, można dynamicznie dodać wiadomość e-mail przy użyciu tokenu. Wpisz nazwę oczekiwaną przez aplikację w polu **Nazwa**, a następnie wpisz `\{\{mail\}\}` w polu **Wartość**.

Usługa Intune obsługuje następujące typy tokenów w ustawieniach konfiguracji. Inne niestandardowe pary klucz/wartość nie są obsługiwane.

- \{\{userprincipalname\}\} — na przykład John@contoso.com
- \{\{mail\}\} — na przykład John@contoso.com
- \{\{partialupn\}\} — na przykład Jan
- \{\{accountid\}\} — na przykład fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} — na przykład 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} — na przykład Jan Nowak
- \{\{PrimarySMTPAddress\}\} — na przykład testuser@ad.domain.com


> [!Note]  
> Znaki \{\{ i \}\} są używane tylko przez typy tokenów i nie mogą być używane do innych celów.

## <a name="next-steps"></a>Następne kroki

Kontynuuj [przypisywanie](apps-deploy.md) i [monitorowanie](apps-monitor.md) aplikacji tak jak dotychczas.