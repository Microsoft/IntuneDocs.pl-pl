---
title: Samouczek — rejestrowanie urządzeń w usłudze Intune przy użyciu rozwiązania Autopilot
titleSuffix: Microsoft Intune
description: W tym samouczku skonfigurujesz rozwiązanie Windows Autopilot do rejestrowania urządzeń w usłudze Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 087f890f84c9bc0ff0c46f129ef84b8a268c738e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187739"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>Samouczek: rejestrowanie urządzeń z systemem Windows w usłudze Intune przy użyciu rozwiązania Autopilot
Rozwiązanie Windows Autopilot upraszcza rejestrowanie urządzeń. Dzięki usłudze Microsoft Intune i rozwiązaniu Autopilot można przekazać nowe urządzenia użytkownikom końcowym bez konieczności tworzenia, konserwowania i stosowania niestandardowych obrazów systemów operacyjnych. 

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
> * Dodawanie urządzeń do usługi Intune
> * Tworzenie grupy urządzeń rozwiązania Autopilot
> * Tworzenie profilu wdrażania rozwiązania Autopilot
> * Przypisywanie profilu wdrażania rozwiązania Autopilot do grupy urządzeń
> * Przekazywanie urządzeń z systemem Windows użytkownikom

Jeśli nie masz subskrypcji usługi Intune, [utwórz konto bezpłatnej wersji próbnej](free-trial-sign-up.md).

Aby zapoznać się z korzyściami, scenariuszami i wymaganiami wstępnymi rozwiązania Autopilot, zobacz [Overview of Windows Autopilot (Omówienie rozwiązania Windows Autopilot)](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Wymagania wstępne
- [Skonfigurowanie automatycznego rejestrowania urządzeń z systemem Windows](quickstart-setup-auto-enrollment.md)
- [Subskrypcja usługi Azure Active Directory — wersja Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>Dodawanie urządzeń

Pierwszym krokiem procesu konfigurowania rozwiązania Windows Autopilot jest dodanie urządzeń z systemem Windows do usługi Intune. Wszystko, co należy zrobić, to utworzenie pliku CSV i zaimportowanie go do usługi Intune.

1. W dowolnym edytorze tekstów utwórz listę wartości rozdzielonych przecinkami (CSV), które identyfikują urządzenia z systemem Windows. Użyj następującego formatu:
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-order-id*
    
    Pierwsze trzy elementy są wymagane, a identyfikator zamówienia jest opcjonalny.

2. Zapisz plik CSV.

3. W usłudze [Intune w witrynie Azure Portal](https://aka.ms/intuneportal) wybierz kolejno pozycje **Rejestrowanie urządzenia**  >  **Rejestracja w systemie Windows**  >  **Urządzenia**  >  **Import**.

    ![Zrzut ekranu przedstawiający urządzenia rozwiązania Autopilot z systemem Windows](media/enrollment-autopilot/autopilot-import-device.png)

4. W obszarze **Dodawanie urządzeń rozwiązania Windows Autopilot** przejdź do zapisanego pliku CSV.

    ![Zrzut ekranu przedstawiający dodawanie urządzeń rozwiązania Autopilot z systemem Windows](media/enrollment-autopilot/autopilot-import-device2.png)

5. Wybierz pozycję **Importuj**, aby rozpocząć importowanie informacji o urządzeniu. Importowanie może potrwać kilka minut.

4. Po ukończeniu importowania wybierz kolejno pozycje **Rejestrowanie urządzenia** > **Rejestracja w systemie Windows** > **Windows Autopilot** > **Urządzenia** > **Synchronizacja**. Zostanie wyświetlony komunikat o synchronizacji w toku. Proces może potrwać kilka minut, w zależności od liczby synchronizowanych urządzeń.

5. Odśwież widok, aby zobaczyć nowe urządzenia.

## <a name="create-an-autopilot-device-group"></a>Tworzenie grupy urządzeń rozwiązania Autopilot

Następnie utworzysz grupę urządzeń i umieścisz w niej właśnie załadowane urządzenia rozwiązania Autopilot.

1. W usłudze [Intune w witrynie Azure Portal](https://aka.ms/intuneportal) wybierz pozycje **Grupy** > **Nowa grupa**.
2. W bloku **Grupa**:
    1. Dla ustawienia **Typ grupy** wybierz pozycję **Zabezpieczenia**.
    2. W obszarze **Nazwa grupy** wprowadź frazę *Grupa rozwiązania Autopilot*. W obszarze **Opis grupy** wprowadź frazę *Grupa testowa dla urządzeń rozwiązania Autopilot*.
    3. W obszarze **Typ członkostwa** wybierz pozycję **Przypisane**.
3. W bloku **Grupa** wybierz pozycję **Członkowie** i dodaj do grupy urządzenia rozwiązania Autopilot. Urządzenia rozwiązania Autopilot, które nie zostały jeszcze zarejestrowane, to urządzenia, których nazwa jest taka sama jak ich numer seryjny.
4. Wybierz pozycję **Utwórz**.  

## <a name="create-an-autopilot-deployment-profile"></a>Tworzenie profilu wdrażania rozwiązania Autopilot

Po utworzeniu grupy urządzeń musisz utworzyć profil wdrażania, aby umożliwić konfigurowanie urządzeń rozwiązania Autopilot.

1. W usłudze [Intune w witrynie Azure Portal](https://aka.ms/intuneportal) wybierz kolejno pozycje **Rejestrowanie urządzenia**  >  **Rejestracja w systemie Windows**  >  **Profile wdrażania**  >  **Utwórz profil**.
2. W obszarze **Nazwa** wprowadź frazę *Profil rozwiązania Autopilot*. W obszarze **Opis** wprowadź frazę *Profil testowy dla urządzeń rozwiązania Autopilot*.
3. Ustaw pozycję **Konwertuj wszystkie urządzenia docelowe na rozwiązanie Autopilot** na **Tak**. To ustawienie gwarantuje, że wszystkie urządzenia na liście zostaną zarejestrowane przy użyciu usługi wdrażania rozwiązania Autopilot. Przetwarzanie rejestracji może potrwać do 48 godzin.
4. W obszarze **Tryb wdrożenia** wybierz pozycję **Sterowane przez użytkownika**. Urządzenia z tym profilem są skojarzone z użytkownikiem rejestrującym urządzenie. Poświadczenia użytkownika są wymagane do rejestracji urządzenia.
5. W polu **Dołącz do usługi Azure AD jako** wybierz pozycję **Dołączono do usługi Azure AD**.
6. Wybierz pozycję **Środowisko gotowe do użycia (OOBE, Out-of-box experience)**, skonfiguruj poniższe opcje i pozostaw inne ustawione na wartość domyślną, a następnie wybierz przycisk **Zapisz**:
    - **Umowa licencyjna użytkownika oprogramowania (EULA)**: **Ukryj**
    - **Ustawienia prywatności**: **Pokaż**
    - **Typ konta użytkownika**: **Standardowe**

6. Wybierz pozycję **Utwórz**, aby utworzyć profil. Profil wdrażania rozwiązania Autopilot jest teraz dostępny do przypisania do urządzeń.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Przypisywanie profilu wdrażania rozwiązania Autopilot do grupy urządzeń

Teraz, gdy profil wdrażania został utworzony, należy przypisać go do grupy urządzeń.
1. W usłudze [Intune w witrynie Azure Portal](https://aka.ms/intuneportal) wybierz kolejno pozycje **Rejestrowanie urządzenia**  >  **Rejestracja w systemie Windows**  >  **Profile wdrażania**, a następnie wybierz profil.
2. W bloku określonego profilu wybierz pozycję **Przypisania**. 
3. Wybierz pozycję **Wybierz grupy**, a następnie w bloku **Wybieranie grup** wybierz pozycję **Grupa rozwiązania Autopilot** i pozycję **Wybierz**.

## <a name="distribute-devices-to-users"></a>Przekazywanie urządzeń użytkownikom

Teraz możesz przekazać urządzenia z systemem Windows użytkownikom. Gdy po raz pierwszy się zalogują, system rozwiązania Autopilot automatycznie zarejestruje i skonfiguruje urządzenia. 

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Jeśli nie chcesz już używać urządzeń rozwiązania Autopilot, możesz je usunąć.

1. Jeśli urządzenia są zarejestrowane w usłudze Intune, musisz najpierw [usunąć je z portalu usługi Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. W usłudze [Intune w witrynie Azure Portal](https://aka.ms/intuneportal) wybierz kolejno pozycje **Rejestrowanie urządzenia** > **Rejestracja w systemie Windows** > **Urządzenia**.

3. W obszarze **urządzeń rozwiązania Autopilot z systemem Windows** wybierz urządzenia do usunięcia, a następnie wybierz pozycję **Usuń**.

4. Potwierdź usunięcie, wybierając pozycję **Tak**. Proces usuwania może potrwać kilka minut.

## <a name="next-steps"></a>Następne kroki

Możesz zapoznać się z dalszymi informacjami na temat innych opcji dostępnych dla rozwiązania Autopilot w systemie Windows.

> [!div class="nextstepaction"]
> [Szczegółowy artykuł dotyczący rejestracji przy użyciu rozwiązania Autopilot](enrollment-autopilot.md)

