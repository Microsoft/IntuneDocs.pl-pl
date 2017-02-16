---
title: "Monitorowanie wdrożeń aplikacji | Microsoft Docs"
description: "Dowiedz się, jak monitorować aplikacje wdrożone za pomocą usługi Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ee0d10f9b86b1122d0f16568b71b087c341e88df


---


# <a name="monitor-app-deployments-in-microsoft-intune"></a>Monitorowanie wdrożeń aplikacji w usłudze Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>Monitorowanie wdrożenia aplikacji
W konsoli administracyjnej usługi Intune widoczne są aplikacje, którymi zarządzasz, a także stan wszystkich wdrożeń. <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>Aby wyświetlić zarządzane aplikacje i ich stan
W obszarze roboczym **Aplikacje** wybierz węzeł **Aplikacje** węzeł, a następnie wybierz pozycję **Aplikacje**.

Zostanie wyświetlona lista aplikacji, którymi zarządzasz. Możesz wybrać dowolną aplikację, aby wyświetlić stan instalacji w dolnym okienku w oknie konsoli. Kliknij ten stan, aby zobaczyć więcej informacji. Jeśli na przykład jest wyświetlany stan **1 użytkownik ma dostępne to oprogramowanie**, możesz kliknąć komunikat, aby zobaczyć nazwę tego użytkownika.

> [!TIP]
> Lista rozwijana **Filtry** umożliwia wyświetlanie tylko aplikacji spełniających określone kryteria, takich jak aplikacje, których nie udało się zainstalować, lub pomyślnie wdrożone aplikacje.
>
> ![Przykład filtrów aplikacji](./media/app-filters.png)

Ponadto w obszarze roboczym **Pulpit nawigacyjny** jest wyświetlany przegląd stanu aplikacji. Kliknięcie w dowolnym miejscu przeglądu spowoduje przekierowanie do listy aplikacji.

## <a name="to-view-more-detailed-information-about-an-app"></a>Aby wyświetlić bardziej szczegółowe informacje o aplikacji
Na liście aplikacji zaznacz dowolną aplikację, a następnie wybierz pozycję **Wyświetl właściwości**.

Na stronie aplikacji **Właściwości oprogramowania** wybierz jedną z tych kart: **Ogólne** — przedstawia ogólne informacje na temat aplikacji oraz na temat stanu jej instalacji; **Urządzenia** — przedstawia urządzenia, na których pomyślnie zainstalowano docelowe wdrożenie aplikacji; **Użytkownicy** — przedstawia użytkowników, na których urządzeniach pomyślnie zainstalowano docelowe wdrożenie aplikacji.

Tak jak wcześniej można użyć listy rozwijanej **Filtry**, aby skonfigurować wartości wyświetlane na poszczególnych kartach.



<!--HONumber=Dec16_HO2-->

