---
# required metadata

title: Ochrona urządzeń z systemem Windows za pomocą usługi Multi-Factor Authentication | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Protect Windows devices with multi-factor authentication
Usługę Microsoft Intune można integrować z usługą Multi-Factor Authentication (MFA), aby zabezpieczyć zasoby firmowe. Usługa MFA wymaga — oprócz nazw użytkowników i haseł— składników uwierzytelniania, takich jak uwierzytelnianie tekstowe. Usługa Intune obsługuje korzystanie z usługi MFA w przypadku rejestracji urządzeń z systemem Windows 8.1 lub nowszym, Windows Phone 8.1 lub Windows 10 Desktop i Mobile. 

## Wymagania uwierzytelniania wieloskładnikowego usług AD FS dotyczące infrastruktury lokalnej
Aby skonfigurować uwierzytelnianie wieloskładnikowe, konieczna jest:

-   **domena usługi Active Directory, do której jest dołączony serwer AD FS,**

-   **serwer Active Directory Federation Services (AD FS) skonfigurowany na potrzeby uwierzytelniania wieloskładnikowego.** Serwer z systemem Windows Server 2012 R2 skonfigurowany jako serwer AD FS. Aby uzyskać więcej informacji, zobacz: [Zabezpieczenia chmury i zasobów lokalnych za pomocą serwera usługi Azure Multi-Factor Authentication z usługami AD FS systemu Windows Server 2012 R2](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/).

Wszystkie wymienione powyżej serwery muszą spełniać wymagania systemowe podane w temacie [Wymagania systemowe i informacje dotyczące instalacji systemu Windows Server 2012 R2](http://technet.microsoft.com/library/dn303418.aspx)..

#### Usługa MFA z usługą Intune
Jeśli organizacja ma lokalną infrastrukturę IT, która obejmuje domenę usługi Active Directory z usługami Active Directory Federation Services (AD FS), możesz skonfigurować usługę MFA na serwerze federacyjnym, a następnie włączyć ją na potrzeby rejestracji w usłudze Intune. Konfigurując usługę MFA w usłudze Intune, umożliwiasz użytkownikom jednokrotne uwierzytelnianie podczas rejestracji, a następnie uzyskiwanie dostępu do zasobów firmy bez konieczności użycia za każdym razem usługi MFA.

>[!NOTE]
>Użycie usługi MFA na serwerze usługi AD FS może być wymagane dla poszczególnych użytkowników lub grup.  

#### Usługa MFA bez usługi Intune
Jeśli skonfigurujesz usługę MFA na serwerze federacyjnym, ale nie włączysz jej na potrzeby rejestracji w usłudze Intune, użytkownicy będą musieli używać usługi MFA za każdym razem, gdy urządzenia będą uzyskiwać dostęp do zasobów firmy (nie tylko podczas rejestracji urządzenia).

Za pomocą usługi Azure Active Directory (AAD) MFA można również żądać uwierzytelniania MFA za każdym razem, gdy użytkownicy uzyskują dostęp do zasobów firmy (to wymaganie można włączyć dla poszczególnych użytkowników). Usługa Azure Active Directory Multi-Factor Authentication to usługa w chmurze, która nie wymaga żadnej lokalnej infrastruktury IT. Aby dowiedzieć się, jak skonfigurować usługę AAD MFA, zobacz [Wprowadzenie do korzystania z usługi Azure Multi-Factor Authentication w chmurze](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)..

## Wymagania uwierzytelniania wieloskładnikowego usług AD FS podczas rejestrowania urządzeń z systemem Windows
Aby dowiedzieć się, jak włączyć usługę MFA w usługach AD FS, zobacz [Zarządzanie ryzykiem przy użyciu dodatkowej usługi Multi-Factor Authentication w przypadku aplikacji poufnych](http://technet.microsoft.com/library/dn280949.aspx)..

## Konfigurowanie usługi MFA na potrzeby rejestracji urządzeń w usłudze Intune
>[!Important]  
>Włącz uwierzytelnianie wieloskładnikowe w dzierżawie usługi Azure AD lub w środowisku lokalnym przed wymaganiem uwierzytelniania wieloskładnikowego dla rejestracji w usłudze Intune urządzeń z systemem Windows. W przeciwnym razie użytkownicy będą otrzymywać komunikat o błędzie podczas próby rejestracji urządzeń z systemem Windows lub próby dołączenia urządzeń do usługi Azure AD, jeśli skonfigurowano automatyczną rejestrację podczas dołączania do usługi Azure AD.

1.  W konsoli administracyjnej usługi Intune kliknij polecenie **Administracja** &gt; **Zarządzanie urządzeniami przenośnymi** &gt; **Usługa Multi-factor Authentication**..

2.  Kliknij pozycję **Skonfiguruj usługę Multi-factor Authentication**, a następnie kliknij pozycję **Włącz usługę Multi-factor Authentication**..



<!--HONumber=May16_HO1-->

