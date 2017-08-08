---
title: "Dostęp warunkowy oparty na aplikacji z użyciem usługi Intune"
description: "Omówienie koncepcji dostępu warunkowego opartego na aplikacji z użyciem usługi Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0893d511c73e4154c61063d96e26937ea2825467
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Dostęp warunkowy oparty na aplikacji z użyciem usługi Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[Zasady ochrony aplikacji w usłudze Intune](app-protection-policy.md) pomagają chronić dane firmy na urządzeniach zarejestrowanych w usłudze Intune. Możesz również korzystać z zasad ochrony aplikacji na urządzeniach należących do pracowników, które nie zostały zarejestrowane na potrzeby zarządzania przez usługę Intune. W takim przypadku, nawet jeśli nie zarządzasz danym urządzeniem, musisz upewnić się, że dane i zasoby firmy zostały odpowiednio zabezpieczone.

Dostęp warunkowy oparty na aplikacji oraz zarządzanie aplikacjami mobilnymi tworzą dodatkową warstwę zabezpieczeń i gwarantują, że tylko aplikacje mobilne, które obsługują zasady ochrony aplikacji usługi Intune, mogą uzyskać dostęp do usługi Exchange Online i innych usług pakietu Office 365.

> [!NOTE]
> Zarządzana aplikacja to taka, dla której zastosowano zasady ochrony aplikacji i która może być zarządzana przez usługę Intune.

Aplikacje poczty wbudowane w systemach iOS i Android można zablokować, zezwalając na dostęp do usługi Exchange Online wyłącznie aplikacji Microsoft Outlook. Ponadto aplikacjom, które nie mają zastosowanych zasad ochrony aplikacji usługi Intune, można zablokować dostęp do usługi SharePoint Online.

## <a name="prerequisites"></a>Wymagania wstępne
Przed utworzeniem zasad dostępu warunkowego opartego na aplikacji muszą zostać spełnione następujące warunki:

- **posiadanie subskrypcji pakietu Enterprise Mobility + Security lub usługi Azure Active Directory w wersji Premium** przy jednoczesnym posiadaniu przez użytkowników licencji na usługi EMS lub Azure AD.
    - Aby uzyskać więcej szczegółowych informacji, zobacz [Cennik pakietu Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) lub [Cennik usługi Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Obsługiwane aplikacje

- **Exchange Online**:
    - Microsoft Outlook dla urządzeń z systemami iOS i Android.
<br></br>
- **SharePoint Online**
    - Microsoft Word dla urządzeń z systemami iOS i Android
    - Microsoft Excel dla urządzeń z systemami iOS i Android
    - Microsoft PowerPoint dla urządzeń z systemami iOS i Android
    - Microsoft OneDrive dla Firm dla urządzeń z systemami iOS i Android
    - Microsoft OneNote dla urządzeń z systemem iOS
<br></br>
- **Microsoft Teams**

    > [!NOTE] 
    > Dostęp warunkowy oparty na aplikacji [obsługuje również aplikacje biznesowe](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication), jednak aplikacje te muszą używać [nowoczesnego uwierzytelniania usługi Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).

## <a name="how-app-based-conditional-access-works"></a>Sposób działania dostępu warunkowego opartego na aplikacji

W tym przykładzie administrator zastosował zasady ochrony aplikacji w odniesieniu do aplikacji Outlook, a następuje zastosował regułę dostępu warunkowego, która powoduje dodanie aplikacji Outlook do listy zatwierdzonych aplikacji, które mogą być używane podczas uzyskiwania dostępu do firmowej poczty e-mail.

> [!NOTE] 
> Struktura poniższego schematu blokowego ma zastosowanie także do innych aplikacji zarządzanych.

![Schemat blokowy: dostęp warunkowy oparty na aplikacji z użyciem usługi Intune](./media/ca-intune-common-ways-3.png)

1.  Użytkownik próbuje przeprowadzić uwierzytelnienie w usłudze Azure Active Directory z aplikacji Outlook.

2.  W ramach pierwszej próby uwierzytelnienia użytkownik zostaje przekierowany do sklepu z aplikacjami w celu przeprowadzenia instalacji aplikacji brokera. Aplikacją brokera jest aplikacja Microsoft Authenticator w przypadku systemu iOS lub aplikacja Portal firmy Microsoft w przypadku urządzeń z systemem Android.

    > [!NOTE]
    > W tym scenariuszu próba użycia natywnej aplikacji poczty e-mail przez użytkownika spowoduje jego przekierowanie do sklepu z aplikacjami, z którego możliwe będzie pobranie aplikacji Outlook i jej zainstalowanie.

3.  Na urządzeniu zostaje zainstalowana aplikacja brokera.

4.  Aplikacja brokera rozpoczyna proces rejestracji usługi Azure AD, która tworzy rekord urządzenia w usłudze Azure AD. Omawiany proces nie jest tym samym co proces rejestracji w usłudze zarządzania urządzeniami mobilnymi (MDM), ale rekord ten jest niezbędny, aby można było wymusić na urządzeniu zasady dostępu warunkowego.

5.  Aplikacja brokera weryfikuje tożsamość aplikacji. Istniejąca warstwa zabezpieczeń umożliwia aplikacji brokera sprawdzenie, czy użytkownik może używać aplikacji.

6.  Aplikacja brokera wysyła identyfikator klienta aplikacji do usługi Azure AD w ramach procesu uwierzytelniania użytkownika w celu sprawdzania, czy został on ujęty na liście pozycji zatwierdzonych z użyciem zasad.

7.  Usługa Azure AD umożliwia użytkownikowi uwierzytelnienie oraz korzystanie z aplikacji na podstawie listy pozycji zatwierdzonych z użyciem zasad. Jeśli aplikacja nie znajduje się na liście aplikacji zatwierdzonych z użyciem zasad, usługa Azure AD nie zezwala na dostęp do aplikacji.

8.  Aplikacja Outlook komunikuje się z usługą Outlook w chmurze w celu zainicjowania komunikacji z usługą Exchange Online.

9.  Usługa Outlook w chmurze komunikuje się z usługą Azure AD w celu pobrania dla użytkownika tokenu dostępu do usługi Exchange Online.

10.  Aplikacja Outlook komunikuje się z usługą Exchange Online w celu pobrania firmowej poczty e-mail użytkownika.

11.  Firmowa poczta e-mail jest dostarczana do skrzynki pocztowej użytkownika.

## <a name="next-steps"></a>Następne kroki
[Tworzenie zasad dostępu warunkowego opartego na aplikacji](app-based-conditional-access-intune-create.md)

[Blokowanie aplikacji, które nie obsługują nowoczesnego uwierzytelniania](app-modern-authentication-block.md)