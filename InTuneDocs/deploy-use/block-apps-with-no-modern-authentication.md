---
title: "Blokowanie aplikacji niekorzystających z nowoczesnego uwierzytelniania | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5083cb49e7a98f19ff21c1972149b00aee4ec93e
ms.openlocfilehash: 8c2718da6f90f18ffbaa6a977dfca7fbc9a1bb09


---

# Blokowanie aplikacji, które nie korzystają z nowoczesnego uwierzytelniania (ADAL)
Dostęp warunkowy do aplikacji przy użyciu zasad zarządzania aplikacjami mobilnymi (MAM CA) bazuje na aplikacjach korzystających z [nowoczesnego uwierzytelniania](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), które jest implementacją protokołu OAuth2. Większość obecnych mobilnych i klasycznych aplikacji pakietu Office korzysta z nowoczesnego uwierzytelniania. Istnieją jednak aplikacje innych firm oraz starsze aplikacje pakietu Office, które korzystają z innych metod uwierzytelniania, takich jak uwierzytelnianie podstawowe i uwierzytelnianie za pomocą formularzy.

Aby zablokować dostęp do tych aplikacji zalecamy wykonanie poniższych czynności:

* Aby zablokować nienowoczesne protokoły uwierzytelniania, należy skonfigurować reguły oświadczeń ADFS. Szczegółowe instrukcje zostały przedstawione w scenariuszu 3 — [całkowite blokowanie dostępu do usługi O365 z wyjątkiem aplikacji opartych na przeglądarce](https://technet.microsoft.com/library/dn592182.aspx).

>[!IMPORTANT]
>Dostęp warunkowy do zarządzania aplikacjami mobilnymi nie może być używany za pomocą uwierzytelniania na podstawie certyfikatu usługi Azure Active Directory (Azure AD). Użytkownik może mieć skonfigurowaną tylko jedną z tych opcji.



### Zobacz też
[Zezwalanie na dostęp do usług Office 365 tylko aplikacjom obsługiwanym przez usługę Intune](allow-policy-managed-apps-access-to-o365.md)



<!--HONumber=Oct16_HO4-->

