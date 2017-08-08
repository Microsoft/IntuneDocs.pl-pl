---
title: "Włączanie łącznika Mobile Threat Defense przy użyciu usługi Intune"
titleSuffix: Intune on Azure
description: "Włącz łącznik Mobile Threat Defense w usłudze Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a5dfef35c9f2d2fa543d8b19c2566b25d47b8f72
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Włączanie łącznika Mobile Threat Defense w usłudze Intune

> [!NOTE] 
> Niniejszy temat dotyczy wszystkich partnerów narzędzi Mobile Threat Defense.

Aby włączyć połączenie z usługą Mobile Threat Defense (MTD) w usłudze Intune, należy wcześniej skonfigurować łącznik usługi Intune w konsoli rozwiązania MTD.

## <a name="to-enable-the-mtd-connector"></a>Aby włączyć łącznik MTD

1. Przejdź do witryny [Azure Portal](https://portal.azure.com) i zaloguj się przy użyciu swoich poświadczeń usługi Intune. Po pomyślnym zalogowaniu zostanie wyświetlona strona **Pulpit nawigacyjny Azure**.

2. Na stronie **Pulpit nawigacyjny Azure** w menu po lewej stronie wybierz opcję **Więcej usług**, a następnie w filtrze pola tekstowego wpisz **Intune**.

3. Wybierz pozycję **Intune**. Zostanie otwarty **Pulpit nawigacyjny Intune**.

4. Na stronie **Pulpit nawigacyjny usługi Intune** wybierz opcję **Zgodność urządzeń**, a następnie wybierz opcję **Mobile Threat Defense** pod sekcją **Instalator**.

5. W bloku **Mobile Threat Defense** wybierz opcję **Dodaj**.

6. Z listy rozwijanej wybierz rozwiązanie MTD jako wartość pola **Łącznik usługi Mobile Threat Defense do instalacji**.

    ![Konfiguracja usługi MTD w witrynie Azure Portal usługi Intune](./media/enable-mtd-connector-1.png)

7. Włącz opcje przełącznika zgodnie z wymaganiami organizacji.

## <a name="mtd-toggle-options"></a>Opcje przełącznika usługi MTD

Zgodnie z wymaganiami danej organizacji można określić, które opcje przełącznika usługi MTD należy włączyć. Poniżej znajdziesz więcej szczegółów:

- **Połącz urządzenia z systemem Android 4.1 lub nowszym z usługą [nazwa partnera MTD]**: po włączeniu tej opcji urządzenia z systemem Android 4.1 lub nowszym mogą zgłaszać zagrożenie bezpieczeństwa do usługi Intune.
    - **Oznacz jako niezgodne w przypadku nieodebrania żadnych danych**: jeśli usługa Intune nie odbiera danych dotyczących urządzenia na tej platformie od partnera MTD, należy uznać to urządzenie za niezgodne.
<br></br>
- **Połącz urządzenia z systemem iOS 8.0 lub nowszym z usługą [nazwa partnera MTD]**: po włączeniu tej opcji urządzenia z systemem iOS 8.0 lub nowszym mogą zgłaszać zagrożenie bezpieczeństwa do usługi Intune.
    - **Oznacz jako niezgodne w przypadku nieodebrania żadnych danych**: jeśli usługa Intune nie odbiera danych dotyczących urządzenia na tej platformie od partnera MTD, należy uznać to urządzenie za niezgodne.
<br></br>
- **Blokuj nieobsługiwane wersje systemu operacyjnego**: blokowanie, gdy na urządzeniu jest zainstalowany system operacyjny o niższym numerze wersji niż minimalna obsługiwana wersja.

- **Liczba dni, po których partner otrzyma stan „brak odpowiedzi”** : liczba dni braku aktywności, zanim usługa Intune uzna partnera za nieodpowiadającego z powodu utraty połączenia. Usługa Intune ignoruje stan zgodności dla partnerów MTD w stanie „brak odpowiedzi”.

> [!IMPORTANT] 
> Aplikacje MTD należy dodać i przypisać przed utworzeniem reguł zasad dotyczących zgodności urządzeń oraz dostępu warunkowego. Dzięki temu dana aplikacja MTD będzie gotowa i dostępna do zainstalowania dla użytkowników końcowych, zanim będą oni mogli uzyskać dostęp do poczty e-mail lub innych zasobów firmy.

> [!TIP]
> W bloku usługi Mobile Threat Defense widać **Stan połączenia** i czas **ostatniej synchronizacji** między usługą Intune a partnerem MTD.

## <a name="next-steps"></a>Następne kroki

[Tworzenie zasad zgodności urządzeń usługi Mobile Threat Defense w usłudze Intune](mtd-device-compliance-policy-create.md)