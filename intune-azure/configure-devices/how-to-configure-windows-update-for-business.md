---
title: "Konfigurowanie ustawień funkcji Windows Update dla firm — usługa Intune | Wersja zapoznawcza usługi Intune Azure | Dokumentacja firmy Microsoft"
description: "Wersja zapoznawcza usługi Intune Azure: dowiedz się, jak skonfigurować ustawienia usługi Windows Update dla firm w usłudze Intune w celu kontrolowania aktualizacji urządzeń z systemem Windows 10."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08f659cf-715e-4e10-9ab2-1bac3c6f2366
ms.reviewer: coryfe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 911d2887791cf16d4290c3ac5189aa44086f4603
ms.openlocfilehash: 5e2516611b933bb9c74c2b8dc973f85e1d82237f
ms.lasthandoff: 03/11/2017


---

# <a name="how-to-configure-windows-update-for-business-settings-with-microsoft-intune"></a>Jak konfigurować ustawienia usługi Windows Update dla firm za pomocą usługi Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="introduction"></a>Wprowadzenie
Windows jako usługa to nowy sposób udostępniania aktualizacji dla systemu Windows 10. Począwszy od systemu Windows 10, wszystkie nowe funkcjonalne i jakościowe aktualizacje będą obejmować zawartość wszystkich poprzednich aktualizacji. Oznacza to, że po zainstalowaniu najnowszej aktualizacji masz pewność, iż urządzenia systemu Windows 10 są całkowicie aktualne. W odróżnieniu od wcześniejszych wersji systemu Windows teraz musisz zainstalować całą aktualizację, a nie tylko jej część.

Za pomocą usługi Windows Update dla firm można uprościć zarządzanie aktualizacjami, dzięki czemu nie trzeba zatwierdzać poszczególnych aktualizacji dla grup urządzeń. Nadal możesz zarządzać ryzykiem w swoich środowiskach, konfigurując strategię wdrażania aktualizacji, dzięki czemu usługa Windows Update zagwarantuje zainstalowanie aktualizacji w odpowiednim czasie. Usługa Microsoft Intune zapewnia możliwość konfigurowania ustawień aktualizacji na urządzeniach oraz odroczenia instalacji aktualizacji. Usługa Intune nie przechowuje aktualizacji, a jedynie przypisanie zasad aktualizacji. W celu aktualizacji urządzenia uzyskują dostęp bezpośrednio do witryny Windows Update. Użyj usługi Intune do konfigurowania **pierścieni aktualizacji systemu Windows 10** i zarządzania nimi. Pierścień aktualizacji zawiera grupę ustawień, które konfigurują, kiedy i w jaki sposób aktualizacje systemu Windows 10 mają zostać zainstalowane. Na przykład można skonfigurować następujące ustawienia:

- **Windows 10 Servicing Branch**: wybierz, czy grupy urządzeń mają otrzymywać aktualizacje od usługi Current Branch, czy też od usługi Current Branch for Business.  
- **Ustawienia opóźnień**: skonfiguruj ustawienia opóźnień aktualizacji w celu opóźnienia instalacji aktualizacji grup urządzeń. Wdrażanie aktualizacji nastąpi w etapach, których postęp będzie można śledzić.
- **Wstrzymywanie**: odłóż instalację aktualizacji, jeśli zostanie wykryty problem w dowolnym momencie wdrażania aktualizacji.
- **Okno obsługi**: skonfiguruj godziny, w których można instalować aktualizacje.
- **Typ aktualizacji**: wybierz typy aktualizacji przeznaczone do zainstalowania. Na przykład aktualizacje dotyczące jakości, aktualizacje dotyczące funkcji lub aktualizacje sterowników.
- **Zachowanie podczas instalacji**: określa sposób przeprowadzania instalacji aktualizacji. To ustawienie określa na przykład, czy urządzenie jest automatycznie ponownie uruchamiane po zakończeniu instalacji.
- **Pobieranie elementów równorzędnych**: określ, czy należy konfigurować pobieranie elementów równorzędnych. W przypadku skonfigurowania tej opcji po zakończeniu pobierania przez urządzenie aktualizacji inne urządzenia mogą pobierać aktualizację z tego urządzenia. Przyspiesza to proces pobierania.

Po utworzeniu pierścieni aktualizacji należy je przypisać do grup urządzeń. Za pomocą pierścieni aktualizacji można utworzyć strategię aktualizacji, która uwzględnia potrzeby biznesowe. Aby uzyskać więcej informacji, zobacz artykuł [Manage updates using Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb) (Zarządzanie aktualizacjami za pomocą usługi Windows Update dla firm).

## <a name="before-you-start"></a>Przed rozpoczęciem

- Aby można było zaktualizować komputery z systemem Windows 10, musi na nich być uruchomiony co najmniej system Windows 10 Pro z Rocznicową aktualizacją.

- Usługa Windows Update obsługuje następujące wersje systemu Windows 10:
    - Windows 10
    - Windows 10 Team (dla urządzeń Surface Hub)

 Urządzenia z systemem Windows 10 Mobile i Windows 10 Holographic nie są obsługiwane.

- Na urządzeniach z systemem Windows opcja **Opinia i diagnostyka** > **Dane diagnostyczne i dane użycia** musi mieć co najmniej wartość **Podstawowa**.

    ![Ustawienie systemu Windows dla danych diagnostycznych i danych dotyczących użycia](./media/telemetry-basic.png)

    To ustawienie można skonfigurować ręcznie lub też można użyć profilu ograniczeń urządzenia usługi Intune dla systemu Windows 10 i nowszych. Aby to zrobić, należy skonfigurować ustawienie **Ogólne** > **Przesłanie danych diagnostycznych** do wartości co najmniej **Podstawowe**. Aby uzyskać więcej informacji o profilach urządzenia, zobacz artykuł [Jak skonfigurować ustawienia ograniczeń dotyczących urządzeń w usłudze Microsoft Intune](/intune-azure/configure-devices/how-to-configure-device-restrictions).

- W klasycznej konsoli administracyjnej usługi Intune istnieją cztery ustawienia, które określają zachowanie aktualizacji oprogramowania. Te ustawienia są częścią ogólnych zasad konfiguracji systemu Windows 10 dla komputerów stacjonarnych oraz urządzeń przenośnych:
    - **Zezwalaj na aktualizacje automatyczne**
    - **Zezwalaj na funkcje wersji wstępnej**
    - **Planowany dzień instalacji**
    - **Planowana godzina instalacji**

  Konsola klasyczna zawiera również w swoim profilu konfiguracji urządzenia ograniczoną liczbę innych ustawień aktualizacji systemu Windows 10. Jeśli dowolne z tych ustawień jest skonfigurowane w klasycznej konsoli administracyjnej usługi Intune, zdecydowanie zalecamy, aby podczas migracji do witryny Azure Portal wykonać następujące czynności:

1. Utwórz pierścienie aktualizacji systemu Windows 10 w witrynie Azure Portal, używając niezbędnych ustawień. Ustawienie **Zezwolenia na funkcje wersji wstępnej** nie jest obsługiwane w witrynie Azure Portal, ponieważ nie jest już stosowane w najnowszych wersjach systemu Windows 10. Podczas tworzenia pierścieni aktualizacji możesz skonfigurować trzy pozostałe ustawienia, jak również inne ustawienia aktualizacji systemu Windows 10.

  > [!NOTE]
  > Aktualizacje systemu Windows 10 utworzone w klasycznej konsoli nie są wyświetlane w witrynie Azure Portal po migracji. Te ustawienia są jednak nadal stosowane. Ustawienie, które po migracji zostało poddane edycji w witrynie Azure Portal, zostanie usunięte z zasad.

2. Ustawienia aktualizacji należy usuwać w konsoli klasycznej. Po migracji do witryny Azure Portal i dodaniu tego samego ustawienia do pierścienia aktualizacji należy usunąć ustawienie z portalu klasycznego, aby uniknąć potencjalnych konfliktów zasad. Na przykład jeśli to samo ustawienie jest skonfigurowane z różnymi wartościami, wystąpi konflikt, który pozostanie niewidoczny, ponieważ ustawienie skonfigurowane w konsoli klasycznej nie jest wyświetlane w witrynie Azure Portal.

## <a name="how-to-create-and-assign-update-rings"></a>Jak tworzyć i przypisywać pierścienie aktualizacji

1. Zaloguj się do portalu Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku **Intune** wybierz opcję **Aktualizacje oprogramowania**.
4. W bloku **Aktualizacje oprogramowania** wybierz kolejno opcje **Zarządzaj** > **Pierścienie aktualizacji systemu Windows 10**.
5. W bloku z listą pierścieni aktualizacji wybierz pozycję **Utwórz**.
6. W bloku **Tworzenie pierścienia aktualizacji** podaj nazwę i opcjonalny opis pierścienia aktualizacji, a następnie wybierz opcję **Ustawienia**.
7. W bloku **Ustawienia** skonfiguruj następujące informacje:
    - **Gałąź obsługi**: ustaw gałąź, dla której urządzenie będą otrzymywać aktualizacje systemu Windows (Current Branch lub Current Branch for Business).
    - **Aktualizacje firmy Microsoft**: określ, czy używać skanowania przy poszukiwaniu aktualizacji aplikacji w witrynie Microsoft Update.
    - **Sterowniki systemu Windows**: wybierz, czy podczas aktualizacji chcesz wykluczyć aktualizację sterowników z witryny Windows Update.
    - **Zachowanie podczas automatycznej aktualizacji**: wybierz sposób zarządzania automatyczną aktualizacją podczas skanowania, pobierania i instalowania aktualizacji. Aby uzyskać szczegółowe informacje, zobacz sekcję [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Okres opóźnienia aktualizacji dotyczących jakości (dni)** — określ, o ile dni będą opóźniane aktualizacje dotyczące jakości. Okres opóźnienia aktualizacji dotyczących jakości może wynosić do 30 dni od daty wydania aktualizacji.  

      Aktualizacje dotyczące jakości są zazwyczaj poprawkami i ulepszeniami istniejących funkcji systemu Windows i najczęściej są publikowane w pierwszy wtorek każdego miesiąca, choć firma Microsoft może je udostępnić w dowolnym momencie. Możesz zdefiniować, czy i na jak długo chcesz odłożyć otrzymywanie aktualizacji dotyczących jakości po dniu ich udostępnienia.
    - **Okres opóźnienia aktualizacji dotyczących funkcji (dni)** — określ, o ile dni będą opóźniane aktualizacje dotyczące funkcji. Okres opóźnienia aktualizacji dotyczących funkcji może wynosić do 180 dni od daty wydania aktualizacji.

    Aktualizacje dotyczące funkcji są zazwyczaj nowymi funkcjami systemu Windows. Po skonfigurowaniu ustawienia **Gałąź obsługi** (**CB** lub **CBB**) można zdefiniować, czy i na jak długo chcesz odłożyć otrzymywanie aktualizacji dotyczących funkcji po ich udostępnieniu przez firmę Microsoft w usłudze Windows Update.

    Na przykład:  
    **Jeśli ustawiono wartość gałęzi obsługi równą CB i okres opóźnienia wynosi 30 dni**: załóżmy, że aktualizacja dotycząca funkcji X została udostępniona w usłudze Windows Update jako CB w styczniu. Urządzenie nie będzie otrzymywać tej aktualizacji do lutego — 30 dni później.

    **Jeśli ustawiono wartość gałęzi obsługi równą CBB i okres opóźnienia wynosi 30 dni**: załóżmy, że aktualizacja dotycząca funkcji X została udostępniona w usłudze Windows Update jako CB w styczniu. Cztery miesiące później, w kwietniu, aktualizacja dotycząca funkcji X zostaje opublikowana jako CBB. Urządzenie otrzyma aktualizację dotyczącą funkcji po 30 dniach od opublikowania wersji CBB i aktualizacja nastąpi w maju.

    - **Optymalizacja dostarczania** — wybór metody używanej przez urządzenie do pobierania aktualizacji systemu Windows. Aby uzyskać szczegółowe informacje, zobacz sekcję [DeliveryOptimization/DEDownloadMode](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#deliveryoptimization-dodownloadmode).
8. Gdy skończysz, kliknij przycisk **OK**, a następnie w bloku **Tworzenie pierścienia aktualizacji** kliknij przycisk **Utwórz**.

Nowy pierścień aktualizacji jest wyświetlany na liście pierścieni aktualizacji.

1. Aby przypisać pierścień, wybierz go na liście, a następnie na karcie <*nazwa pierścienia*> wybierz opcję **Przypisania**.
2. Na następnej karcie wybierz opcję **Wybierz grupy**, a następnie wybierz grupy, do których chcesz przypisać ten pierścień.
3. Gdy skończysz, wybierz opcję **Wybierz** w celu zakończenia przypisywania.



## <a name="update-compliance-reporting"></a>Raportowanie zgodności aktualizacji
Wdrożenia aktualizacji systemu Windows 10 można monitorować za pomocą bezpłatnego rozwiązanie wchodzącego w skład usługi OMS (Operations Management Service) o nazwie Update Compliance. Aby uzyskać szczegółowe informacje, zobacz artykuł [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Monitorowanie aktualizacji systemu Windows za pomocą aplikacji Update Compliance). Dzięki temu rozwiązaniu można nadać komercyjny identyfikator dowolnemu urządzeniu z systemem Windows 10 zarządzanemu przez usługę Intune, dla którego chcesz otrzymywać raport zgodności aktualizacji.

W konsoli usługi Intune możesz użyć ustawień ścieżki OMA-URI dla niestandardowych zasad do skonfigurowania identyfikatora komercyjnego. Szczegółowe informacje można znaleźć w artykule [Ustawienia zasad usługi Intune dla urządzeń z systemem Windows 10 w usłudze Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Ścieżka OMA-URI (wielkość liter jest istotna) służąca do konfigurowania komercyjnego identyfikatora to: ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

Na przykład można użyć następujących wartości w obszarze **Dodaj lub edytuj ustawienie OMA-URI**:

- **Nazwa ustawienia**: identyfikator komercyjny programu Windows Analytics
- **Opis ustawienia**: konfigurowanie komercyjnych identyfikatorów rozwiązań programu Windows Analytics
- **Typ danych:**: ciąg
- **OMA-URI** (wielkość liter jest istotna): ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID
- **Wartość**: <*użyj identyfikatora GUID wyświetlanego na karcie Telemetria systemu Windows w obszarze roboczym usługi OMS*>

![Ustawienie systemu Windows dla danych diagnostycznych i danych dotyczących użycia](./media/commID.png)

<!--
1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Software Updates**.
4. On the **Software Updates** blade, choose **Overview**. From here you can see general information about the status of any update rings you assigned.
4. On the **Windows 10 Updates** blade, choose **Monitor** > **Update ring deployment for devices**, **Update ring deployment for users**, or **Per-setting deployment state** to view more detailed information about update ring assignments.
-->





## <a name="how-to-pause-updates"></a>Jak wstrzymywać aktualizacje
Można wstrzymać otrzymywanie przez urządzenia aktualizacji dotyczących funkcji lub aktualizacji dotyczących jakości przez okres do 35 dni od chwili wstrzymania aktualizacji. Po upływie maksymalnej liczby dni automatycznie wygasa działanie funkcji wstrzymania i urządzenie rozpoczyna skanowanie usługi Windows Update w poszukiwaniu odpowiednich aktualizacji. Po tym skanowaniu można ponownie wstrzymać aktualizacje.
1. Zaloguj się do portalu Azure Portal.
2. Wybierz kolejno opcje **Więcej usług** > **Monitorowanie i zarządzanie** > **Intune**.
3. W bloku **Intune** wybierz opcję **Aktualizacje oprogramowania**.
4. W bloku **Aktualizacje oprogramowania** wybierz kolejno opcje **Zarządzaj** > **Pierścienie aktualizacji systemu Windows 10**.
5. W bloku z wyświetloną listą pierścieni aktualizacji wybierz pierścień, który chcesz wstrzymać, a następnie wybierz kolejno opcje **...**  >  **Wstrzymaj aktualizacje dotyczące jakości** > lub **Wstrzymaj aktualizacje dotyczące funkcji** w zależności od typu aktualizacji, który należy wstrzymać.

> [!IMPORTANT]
> Wydane polecenie wstrzymania urządzenia otrzymują przy następnym zarejestrowaniu się w usłudze. Istnieje możliwość, że urządzenia mogą zainstalować zaplanowaną aktualizację przed zarejestrowaniem.
> Ponadto jeśli urządzenie docelowe jest wyłączone w momencie wydania polecenia wstrzymania, może ono po włączeniu pobrać i zainstalować zaplanowane aktualizacje przed zarejestrowaniem się w usłudze Intune.
