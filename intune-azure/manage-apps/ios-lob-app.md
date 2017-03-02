---
title: "Dodawanie aplikacji biznesowych ze sklepu z aplikacjami dla systemu iOS do usługi Intune | Wersja zapoznawcza usługi Intune Azure | Dokumentacja firmy Microsoft"
description: "Wersja zapoznawcza usługi Intune Azure: informacje o dodawaniu aplikacji biznesowych (LOB) dla systemu iOS do usługi Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 6d41adabfab178daa7f6fce3d86bc8216bf4ab29
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>Jak dodawać aplikacje biznesowe dla systemu iOS do usługi Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Krok 1. Określanie lokalizacji pliku konfiguracji oprogramowania

1. Zaloguj się do portalu Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku usługi Intune wybierz opcję **Zarządzaj aplikacjami**.
4. W obciążeniu **Aplikacje mobilne** wybierz kolejno pozycje Zarządzaj > **Aplikacje**.
5. Wybierz pozycję **Dodaj** powyżej listy aplikacji.
6. W bloku **Dodaj aplikację** wybierz **Plik konfiguracji oprogramowania**.
7. W bloku **Wybieranie pliku konfiguracji** kliknij przycisk Przeglądaj i przejdź do pliku konfiguracji aplikacji systemu iOS (z rozszerzeniem .ipa), a następnie kliknij przycisk **OK**.

## <a name="step-2---configure-app-information"></a>Krok 2 — Konfigurowanie informacji o aplikacji

1. W bloku **Edytuj aplikację** skonfiguruj następujące informacje. Gdy wszystko będzie gotowe, kliknij pozycję **Dodaj**. W zależności od wybranej aplikacji niektóre wartości w tym bloku mogą zostać wypełnione automatycznie:
    - **Nazwa aplikacji** — wprowadź nazwę aplikacji, która będzie wyświetlana w Portalu firmy. Upewnij się, że wszystkie używane nazwy aplikacji są unikatowe. Jeśli dana nazwa aplikacji występuje dwa razy, użytkownicy Portalu firmy będą widzieć tylko jedną z aplikacji o tej nazwie.
    - **Opis aplikacji** — wprowadź opis aplikacji. Ta informacja będzie widoczna dla użytkowników w Portalu firmy.
    - **Wydawca** — wprowadź nazwę wydawcy aplikacji.
    - **Odpowiedni typ urządzenia** — określ, czy ta aplikacja może zostać zainstalowana w urządzeniu iPad, zgodnym urządzeniu iPod lub telefonie iPhone.
    - **Minimalna wersja systemu operacyjnego** — wybierz z listy minimalną wersję systemu operacyjnego, na którym można zainstalować aplikację. W przypadku przypisania aplikacji do urządzenia z wcześniejszą wersją systemu operacyjnego instalacja nie będzie możliwa.
    - **Kategoria** (opcjonalnie) — wybierz co najmniej jedną wbudowaną lub utworzoną przez siebie kategorię aplikacji. Ułatwi to użytkownikom znajdowanie aplikacji podczas przeglądania Portalu firmy.
    - **Wyświetl jako polecaną aplikację w portalu firmy** — wyróżnij aplikację na stronie głównej portalu firmy dla użytkowników przeglądających aplikacje.
    - **Adres URL informacji** — opcjonalnie wprowadź adres URL witryny sieci Web zawierającej informacje o aplikacji. Adres będzie widoczny dla użytkowników w Portalu firmy.
    - **Adres URL zasad ochrony prywatności** — opcjonalnie wprowadź adres URL witryny sieci Web zawierającej informacje o zasadach ochrony prywatności mających zastosowanie do aplikacji. Adres będzie widoczny dla użytkowników w Portalu firmy.
    - **Deweloper** — opcjonalnie wprowadź nazwę dewelopera aplikacji.
    - **Właściciel** — opcjonalnie wprowadź nazwę właściciela aplikacji, na przykład **Dział kadr**.
    - **Uwagi** — wprowadź wszelkie uwagi, które chcesz skojarzyć z aplikacją.
    - **Przekaż ikonę** — przekaż ikonę, która zostanie skojarzona z aplikacją. Będzie ona wyświetlana jako ikona aplikacji podczas przeglądania Portalu firmy.
2. Gdy wszystko będzie gotowe, w bloku **Dodaj aplikację** wybierz pozycję **Zapisz**.

Utworzona aplikacja będzie wyświetlana na liście aplikacji, skąd można ją przypisać do wybranych grup. Aby uzyskać pomoc, zobacz artykuł [How to assign apps to groups](/intune-azure/manage-apps/deploy-apps) (Jak przypisać aplikacje do grupy).