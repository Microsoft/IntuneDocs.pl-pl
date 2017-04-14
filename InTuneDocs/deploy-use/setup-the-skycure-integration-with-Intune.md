---
title: "Konfiguracja integracji z programem Skycure w usłudze Intune | Dokumentacja firmy Microsoft"
description: "Skonfiguruj integrację z programem Skycure w usłudze Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93722f66-7641-4a3f-b1fb-3a0a58a36675
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: 6ff56f736c289dbc9a8340ad76e044363acbfea5
ms.lasthandoff: 03/22/2017


---

# <a name="setup-the-skycure-integration-with-intune"></a>Konfiguracja integracji z programem Skycure w usłudze Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Aby uzyskać możliwości rejestracji jednokrotnej, do usługi Azure AD należy dodać aplikacje Skycure.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="azure-ad-account-used-to-integrate-intune-and-skycure"></a>Konto usługi Azure AD używane do integracji usługi Intune i programu Skycure

-   Przed rozpoczęciem procesu instalacji podstawowej programu Skycure upewnij się, że konto usługi Azure AD jest poprawnie skonfigurowane w [konsoli zarządzania Skycure](https://aad.skycure.com).

### <a name="full-integration-vs-read-only"></a>Pełna integracja a integracja tylko do odczytu

Program Skycure obsługuje dwa tryby integracji z usługą Intune:

-   **Integracja tylko do odczytu (konfiguracja podstawowa):** dokonuje tylko inwentaryzacji urządzeń z usługi Azure Active Directory i umieszcza je w konsoli Skycure.
<br>
    -   Jeśli opcje **Przekaż kondycję i ryzyko urządzeń do usługi Intune** oraz **Zgłoś również zdarzenia związane z bezpieczeństwem do usługi Intune** nie są zaznaczone w konsoli zarządzania Skycure, integracja jest tylko do odczytu i w związku z tym nigdy nie spowoduje zmiany stanu urządzeń (zgodnych lub niezgodnych) w usłudze Intune.
<br></br>
-   **Pełna integracja:** umożliwia raportowanie do usługi Intune ryzyka i szczegółowych informacji dotyczących incydentów zabezpieczeń na urządzeniach w programie Skycure, co powoduje utworzenie dwukierunkowej komunikacji między obiema usługami w chmurze.

### <a name="how-the-skycure-apps-are-used-with-azure-ad-and-intune"></a>W jaki sposób aplikacje Skycure są używane z usługą Azure AD i usługą Intune?

-   **Aplikacja systemu iOS:** umożliwia użytkownikom końcowym logowanie się do usługi Azure AD za pomocą aplikacji dla systemu iOS.

-   **Aplikacja systemu Android:** umożliwia użytkownikom końcowym logowanie się do usługi Azure AD za pomocą aplikacji dla systemu Android.

-   **Aplikacja zarządzania:** jest to wielodostępna aplikacja Skycure usługi Azure AD umożliwiająca komunikację usługa do usługi z usługą Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-skycure"></a>Aby skonfigurować integrację tylko do odczytu między usługą Intune i programem Skycure

> [!IMPORTANT] 
> Poświadczenia administratora programu Skycure to wiadomość e-mail, która musi należeć do prawidłowego użytkownika w usłudze Azure Active Directory. W przeciwnym razie logowanie zakończy się niepowodzeniem. Program Skycure używa usługi Azure Active Directory do uwierzytelniania swojego administratora za pomocą funkcji logowania jednokrotnego (SSO, Single Sign On).

1.  Przejdź do [konsoli zarządzania Skycure](https://aad.skycure.com).

2.  Wprowadź swoje **poświadczenia administratora programu Skycure**, a następnie kliknij przycisk **Kontynuuj**.

3.  W obszarze **Integracja z usługą Intune** przejdź do opcji **Ustawienia** i wybierz opcję **Konfiguracja podstawowa**.

4.  Na etykiecie **Aplikacja systemu iOS** kliknij opcję **Dodaj do usługi Active Directory**.

    ![Aplikacja systemu iOS w konsoli zarządzania programu Skycure](../media/mtp/skycure-setup-1.png)

5.  Po otwarciu strony logowania wprowadź swoje poświadczenia usługi Intune, a następnie kliknij przycisk **Akceptuj**.

    ![Monit logowania usługi Intune aplikacji systemu iOS](../media/mtp/skycure-setup-2.png)

6.  Po dodaniu aplikacji w usłudze Azure AD można zauważyć wskaźnik oznaczający, że aplikacja została pomyślnie dodana do usługi Azure AD w konsoli zarządzania Skycure.

    ![Ekran końcowy aplikacji dla systemu iOS](../media/mtp/skycure-setup-3.png)

> [!NOTE] 
> Powtórz ten sam proces dla aplikacji **Skycure systemu Android** i aplikacji **zarządzania**.

### <a name="add-an-azure-ad-security-group-into-skycure"></a>Dodanie grupy zabezpieczeń usługi Azure AD do programu Skycure

Należy dodać grupę zabezpieczeń usługi Azure AD, która zawiera wszystkie urządzenia z uruchomionym programem Skycure.

1.  Wprowadź i wybierz wszystkie grupy zabezpieczeń urządzeń z uruchomionym programem Skycure, a następnie kliknij opcję **Zastosuj zmiany**.

    ![Konfigurowanie konsoli zarządzania Skycure grupy zabezpieczeń](../media/mtp/skycure-setup-4.png)

Program Skycure synchronizuje urządzenia z uruchomioną jego usługą Mobile Threat Defense z grupami zabezpieczeń usługi Azure AD.

![Konfiguracja grupy zabezpieczeń na konsoli zarządzania Skycure została ukończona](../media/mtp/skycure-setup-5.png)

## <a name="set-up-the-full-integration-between-intune-and-skycure"></a>Konfigurowanie pełnej integracji między usługą Intune i programem Skycure

1.  Przejdź do [konsoli zarządzania Skycure](https://aad.skycure.com).

2.  Wprowadź swoje **poświadczenia administratora programu Skycure**, a następnie kliknij przycisk **Kontynuuj**.

3.  W obszarze **Integracja z usługą Intune** przejdź do opcji **Ustawienia** i wybierz opcję **Pełna integracja**.

4.  Zaznacz następujące ustawienia:

    a.  Przekaż kondycję i ryzyko urządzeń do usługi Intune

    b.  Zgłoś również zdarzenia związane z bezpieczeństwem do usługi Intune

5.  Kliknij opcję **Zastosuj zmiany**.

    ![Pełna integracja Skycure została ukończona](../media/mtp/skycure-setup-6.png)

## <a name="next-steps"></a>Następne kroki

[Włączanie usługi Skycure Mobile Threat Defense w usłudze Intune](https://docs.microsoft.com/intune/deploy-use/enable-skycure-mobile-threat-defense-in-intune)
