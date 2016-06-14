---
# required metadata

title: Konfigurowanie niestandardowej nazwy domeny | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Konfigurowanie niestandardowej nazwy domeny

Domyślnie usługa Intune używa nazwy domeny **<domain>.onmicrosoft.com** utworzonej podczas subskrybowania usługi. Jeśli organizacja ma niestandardową domenę, możesz skonfigurować wystąpienie usługi Intune do korzystania z tej domeny zamiast nazwy domeny zapewnionej w ramach subskrypcji.

Przed utworzeniem nowych kont użytkowników lub zsynchronizowaniem kont z lokalnej usługi Active Directory zdecydowanie zalecane jest określenie, czy używana będzie tylko domena .onmicrosoft.com, czy też zostanie dodana co najmniej jedna niestandardowa nazwa domeny. Skonfigurowanie domeny niestandardowej przed dodaniem użytkowników może ułatwić zarządzanie tożsamościami użytkowników subskrypcji przez umożliwienie użytkownikom logowania się przy użyciu poświadczeń, których używają do uzyskiwania dostępu do innych zasobów domeny.

Po zasubskrybowaniu usługi firmy Microsoft w chmurze Twoje wystąpienie tej usługi staje się [dzierżawą usługi Microsoft Azure Active Directory](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), która zapewnia usługi tożsamości i usługi katalogowe na potrzeby usługi w chmurze. Ponieważ zadania związane z konfiguracją usługi Intune do korzystania z niestandardowej nazwy domeny organizacji są takie same jak w przypadku pozostałych dzierżaw usługi Azure AD, skorzystaj z informacji i procedur dostępnych w temacie [Dodawanie domeny](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)..

> [!TIP]
> Aby uzyskać więcej informacji na temat używania domeny niestandardowej z usługą firmy Microsoft w chmurze, zobacz [Poglądowe omówienie niestandardowych nazw domen w usłudze Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)..

### Następne kroki
Gratulacje! Krok 2 *przewodnika Szybki start dotyczącego usługi Intune* został ukończony..

>[!div class="step-by-step"]

>[&larr; **Logowanie się do usługi Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Dodawanie użytkowników do usługi Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO1-->

