---
title: "Jak dodawać aplikacje biznesowe dla systemu Windows do usługi Intune"
titleSuffix: Intune on Azure
description: "Informacje o dodawaniu aplikacji biznesowych dla systemu Windows do usługi Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f8be4f6bf47ceb966e9042465dc8839d9aa9119
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Jak dodawać aplikacje biznesowe (LOB) dla systemu Windows do usługi Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Krok 1. Określanie lokalizacji pliku konfiguracji oprogramowania

1. Zaloguj się do portalu Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku **Intune** wybierz opcję **Zarządzaj aplikacjami**.
4. W obciążeniu **Aplikacje mobilne** wybierz kolejno pozycje **Zarządzaj** > **Aplikacje**.
5. Wybierz pozycję **Dodaj** powyżej listy aplikacji.
6. W bloku **Dodaj aplikację** wybierz pozycję **Aplikacja biznesowa**.

## <a name="step-2---configure-the-app-package-file"></a>Krok 2. Konfigurowanie pliku pakietu aplikacji

1. W bloku **Dodaj aplikację** wybierz plik **Pakiet aplikacji**.
2. W bloku pliku **Pakiet aplikacji** wybierz przycisk przeglądania i wybierz plik instalacyjny systemu Windows z rozszerzeniem **.msi** (inne typy plików instalacyjnych nie są obsługiwane).
3. Gdy skończysz, wybierz przycisk **OK**.


## <a name="step-3---configure-app-information"></a>Krok 3. Konfigurowanie informacji o aplikacji

1. W bloku **Dodaj aplikację** wybierz plik **Pakiet aplikacji**.
2. W bloku **Informacje o aplikacji** skonfiguruj następujące informacje. W zależności od wybranej aplikacji niektóre wartości w tym bloku mogą zostać wypełnione automatycznie:
    - **Nazwa** — wprowadź nazwę aplikacji wyświetlaną w portalu firmy. Upewnij się, że wszystkie używane nazwy aplikacji są unikatowe. Jeśli dana nazwa aplikacji występuje dwa razy, użytkownicy Portalu firmy będą widzieć tylko jedną z aplikacji o tej nazwie.
    - **Opis** — wprowadź opis aplikacji. Ta informacja będzie widoczna dla użytkowników w Portalu firmy.
    - **Wydawca** — wprowadź nazwę wydawcy aplikacji.
    - **Kategoria** — wybierz co najmniej jedną wbudowaną lub utworzoną przez siebie kategorię aplikacji. Ułatwi to użytkownikom znajdowanie aplikacji podczas przeglądania Portalu firmy.
    - **Wyświetl jako polecaną aplikację w portalu firmy** — wyróżnij aplikację na stronie głównej portalu firmy dla użytkowników przeglądających aplikacje.
    - **Adres URL informacji** — opcjonalnie wprowadź adres URL witryny sieci Web zawierającej informacje o aplikacji. Adres będzie widoczny dla użytkowników w Portalu firmy.
    - **Adres URL zasad ochrony prywatności** — opcjonalnie wprowadź adres URL witryny sieci Web zawierającej informacje o zasadach ochrony prywatności mających zastosowanie do aplikacji. Adres będzie widoczny dla użytkowników w Portalu firmy.
    - **Argumenty wiersza polecenia** — opcjonalnie wprowadź argumenty wiersza polecenia, które mają zostać zastosowane do pliku .msi po jego uruchomieniu, np. **/q**.
    - **Deweloper** — opcjonalnie wprowadź nazwę dewelopera aplikacji.
    - **Właściciel** — opcjonalnie wprowadź nazwę właściciela aplikacji, na przykład **Dział kadr**.
    - **Uwagi** — wprowadź wszelkie uwagi, które chcesz skojarzyć z aplikacją.
    - **Logo** — przekaż ikonę, która zostanie skojarzona z aplikacją. Będzie ona wyświetlana jako ikona aplikacji podczas przeglądania Portalu firmy.
3. Gdy skończysz, wybierz przycisk **OK**.

## <a name="step-4---finish-up"></a>Krok 4. Zakończenie

1. W bloku **Dodaj aplikację** sprawdź poprawność skonfigurowanych informacji.
2. Wybierz pozycję **Dodaj**, aby przekazać aplikację do usługi Intune.

Utworzona aplikacja będzie wyświetlana na liście aplikacji, skąd można ją przypisać do wybranych grup. Aby uzyskać pomoc, zobacz artykuł [How to assign apps to groups](apps-deploy.md) (Jak przypisać aplikacje do grupy).