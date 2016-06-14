---
# required metadata

title: Ograniczanie dostępu do poczty e-mail i usług O365 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ograniczanie dostępu do poczty e-mail i usług O365 przy użyciu usługi Microsoft Intune
Możliwe jest ograniczenie dostępu do poczty e-mail i usług O365 firmy za pomocą dostępu warunkowego usługi Microsoft Intune. Możliwość dostępu warunkowego usługi Intune pozwala na zapewnienie, że dostęp do poczty e-mail i usług O365 w Twojej firmie jest ograniczony do urządzeń, które są zgodne z ustawionymi zasadami.
## W jaki sposób działa dostęp warunkowy?
Ustawienia zasad zgodności są używane do oceny zgodności urządzenia. Zasady dostępu warunkowego używają tej oceny do ograniczenia dostępu do określonej usługi lub zezwolenia na taki dostęp. Jeśli zasady dostępu warunkowego są stosowane w połączeniu z zasadami zgodności, to tylko zgodne urządzenia będą miały dostęp do usługi.

Należy pamiętać, że użytkownik używający urządzenia musi również mieć w nim wdrożone zasady zgodności, aby urządzenie mogło zostać ocenione pod kątem zgodności.
Jeśli na urządzeniu nie wdrożono żadnych zasad zgodności dla użytkownika, to urządzenie będzie traktowane jako zgodne i nie będą stosowane żadne ograniczenia dostępu.

Gdy urządzenia nie spełniają warunków ustawionych w zasadach, użytkownik końcowy jest przeprowadzany przez procedurę rejestracji urządzenia i rozwiązywania problemu, w związku z którym urządzenie nie może być zgodne.

Typowy przepływ dostępu warunkowego:

![Diagram przedstawiający punkty decyzyjne używane do określenia, czy urządzenie ma mieć dostęp do usługi, czy ma być blokowane](./media/ConditionalAccess4.png)

## Jak skonfigurować dostęp warunkowy?
Użyj warunkowego dostępu do zarządzania dostępem do następujących programów i usług firmy Microsoft: **lokalny program Exchange**, **usługa Exchange Online**, **usługa Exchange Online w wersji dedykowanej**, **usługa SharePoint Online** i **usługa Skype dla firm Online**.

Aby skonfigurować dostęp warunkowy, skonfiguruj zasady zgodności urządzeń i zasady dostępu warunkowego.

Zasady zgodności zawierają ustawienia, takie jak kod dostępu i szyfrowanie, oraz określają, czy urządzenie nie ma zdjętych zabezpieczeń. Urządzenie musi spełniać te reguły, aby można je było uważać za zgodne.

Możliwe jest ustawienie zasad dostępu warunkowego w celu ograniczenia dostępu w oparciu o:
- Stan zgodności urządzenia.
- Platformę, na której działa urządzenie.
- Typ aplikacji używanych do uzyskiwania dostępu do usług.

W odróżnieniu od innych zasad usługi Intune, zasady dostępu warunkowego nie są wdrażane przez Ciebie. Zamiast tego po skonfigurowaniu zasad i wybraniu użytkowników, którzy powinni je posiadać, zasady są stosowane do wszystkich użytkowników docelowych. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.


## Następne kroki
1. [Dowiedz się więcej o zasadach zgodności urządzenia i sposobie ich działania ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [Tworzenie zasad zgodności](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  Utwórz zasady dostępu warunkowego dla jednego z następujących przypadków:
> [!div class="op_single_selector"]
  - [Tworzenie zasad dostępu warunkowego dla usługi Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Tworzenie zasad dostępu warunkowego dla lokalnego programu Exchange](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Tworzenie zasad dostępu warunkowego dla nowej usługi Exchange Online w wersji dedykowanej](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Tworzenie zasad dostępu warunkowego dla starszej usługi Exchange Online w wersji dedykowanej](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Tworzenie zasad dostępu warunkowego dla usługi SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Tworzenie zasad dostępu warunkowego dla usługi Skype dla firm Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->

