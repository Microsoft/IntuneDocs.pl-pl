---
title: Opakowywanie aplikacji systemu Android za pomocą narzędzia opakowującego aplikacje dostępnego w usłudze Intune
description: Dowiedz się, jak opakowywać aplikacje systemu Android bez konieczności zmieniania kodu samej aplikacji. Przygotuj aplikacje tak, aby można było stosować zasady zarządzania aplikacjami mobilnymi.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e9c349c8-51ae-4d73-b74a-6173728a520b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfea74c70b81cadfa06c578dc33cdad401fa9e45
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940072"
---
# <a name="prepare-android-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Przygotowywanie aplikacji systemu Android pod kątem zasad ochrony aplikacji za pomocą narzędzia opakowującego aplikacje usługi Intune

Za pomocą narzędzia opakowującego aplikacje dla systemu Android w usłudze Microsoft Intune można zmieniać działanie wewnętrznych aplikacji dla systemu Android przez ograniczanie ich funkcji bez konieczności zmieniania kodu aplikacji.

Narzędzie to jest aplikacją wiersza polecenia systemu Windows działającą w programie PowerShell i tworzącą otokę wokół aplikacji dla systemu Android. Po opakowaniu wybranej aplikacji można modyfikować jej funkcje, konfigurując [zasady zarządzania aplikacjami mobilnymi](../apps/app-protection-policies.md) usługi Intune.

Przed uruchomieniem tego narzędzia należy zapoznać się z sekcją [Uwagi dotyczące zabezpieczeń przy uruchamianiu narzędzia opakowującego aplikacje](#security-considerations-for-running-the-app-wrapping-tool). Aby pobrać to narzędzie, przejdź do strony [Microsoft Intune App Wrapping Tool for Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) (Narzędzie opakowujące aplikacje dla systemu Android w usłudze Microsoft Intune) w witrynie GitHub.

## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Spełnianie wymagań wstępnych do używania narzędzia opakowującego aplikacje

- Narzędzie opakowujące aplikacje musi zostać uruchomione na komputerze z systemem Windows 7 lub nowszym.

- Aplikacja wejściowa musi być prawidłowym pakietem aplikacji Android z rozszerzeniem pliku apk oraz:

  - nie może być szyfrowana,
  - nie może być wcześniej opakowana przez narzędzie opakowujące aplikacje usługi Intune,
  - musi być napisana dla systemu Android 4.0 lub nowszego.

- Aplikacja musi być opracowana przez Twoją firmę lub dla niej. To narzędzie nie może być używane do przetwarzania aplikacji pobranych ze sklepu Google Play.

- Aby uruchomić narzędzie opakowujące aplikacje, należy zainstalować najnowszą wersję środowiska [Java Runtime Environment](https://java.com/download/) i upewnić się, że w zmiennych środowiskowych systemu Windows została ustawiona zmienna ścieżki Java C:\ProgramData\Oracle\Java\javapath. Aby uzyskać więcej informacji, zobacz [dokumentację środowiska Java](https://java.com/download/help/).

    > [!NOTE]
    > W pewnych sytuacjach 32-bitowa wersja programu Java może spowodować problemy z pamięcią. Warto zainstalować wersję 64-bitową.

- System Android wymaga, aby wszystkie pakiety aplikacji (apk) były podpisane. Aby uzyskać informacje dotyczące **ponownego używania** istniejących certyfikatów i ogólne wskazówki dotyczące certyfikatów podpisywania, zobacz [Ponowne używanie certyfikatów podpisywania i opakowywanie aplikacji](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps). Plik wykonywalny Java keytool.exe służy do generowania **nowych** poświadczeń wymaganych do podpisania opakowanej aplikacji wyjściowej. Wszelkie ustawiane hasła muszą być bezpieczne, ale zanotuj je, ponieważ będą potrzebne do uruchomienia narzędzia opakowującego aplikacje.

    > [!NOTE]
    > Narzędzie opakowujące aplikacje usługi Intune nie obsługuje podpisywania aplikacji za pomocą schematów podpisów firmy Google w wersji v2 i w przyszłej wersji v3. Zaleca się, aby po opakowaniu pliku apk przy użyciu narzędzia opakowującego aplikacje usługi Intune skorzystać z [narzędzia Apksigner dostarczanego przez firmę Google]( https://developer.android.com/studio/command-line/apksigner). Pozwoli to zagwarantować, że po pobraniu aplikacji na urządzeniach użytkowników końcowych będzie można ją uruchomić poprawnie zgodnie ze standardami systemu Android. 

- (Opcjonalnie) Czasami aplikacja może osiągnąć limit rozmiaru pliku wykonywalnego Dalvik (DEX) z powodu klas zestawu Intune MAM SDK, które są dodawane podczas opakowywania. Pliki DEX są częścią kompilacji aplikacji systemu Android. Narzędzie opakowującego aplikacje w usłudze Intune automatycznie obsługuje przepełnienie pliku DEX podczas zawijania dla aplikacji o minimalnym poziomie interfejsu API równym 21 lub wyższym (w przypadku [V. 1.0.2501.1 W przypadku aplikacji o minimalnym poziomie interfejsu API wynoszącym < 21 najlepszym rozwiązaniem jest zwiększenie minimalnego poziomu interfejsu API przy użyciu flagi `-UseMinAPILevelForNativeMultiDex` otoki. Aby klienci nie mogli zwiększyć minimalnego poziomu interfejsu API aplikacji, dostępne są następujące obejścia przepełnienia DEX. W niektórych organizacjach może to wymagać współpracy z osobami kompilującymi aplikację (tj. zespołem zajmującym się kompilacją aplikacji):
* Użyj funkcji Guard w celu wyeliminowania nieużywanych odwołań do klas z podstawowego pliku DEX aplikacji.
* W przypadku klientów korzystających z programu v 3.1.0 lub nowszej wtyczki z systemem Android Gradle należy wyłączyć [Dexer D8](https://android-developers.googleblog.com/2018/04/android-studio-switching-to-d8-dexer.html).  

## <a name="install-the-app-wrapping-tool"></a>Instalacja narzędzia opakowującego aplikacje

1. Pobierz plik instalacyjny narzędzia opakowującego aplikacje dla systemu Android w usłudze Intune, InstallAWT.exe, z [repozytorium w witrynie GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android) na komputer z systemem Windows. Otwórz plik instalacyjny.

2. Zaakceptuj umowę licencyjną, a następnie zakończ instalację.

Zwróć uwagę na folder, w którym zostało zainstalowane narzędzie. Domyślna lokalizacja: C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool.

## <a name="run-the-app-wrapping-tool"></a>Uruchamianie narzędzia opakowującego aplikacje

1. Na komputerze z systemem Windows z zainstalowanym narzędziem opakowującym aplikacje otwórz okno programu PowerShell.

2. Z folderu, w którym zostało zainstalowane narzędzie, zaimportuj moduł programu PowerShell narzędzia opakowującego aplikacje:

   ```PowerShell
   Import-Module .\IntuneAppWrappingTool.psm1
   ```

3. Uruchom narzędzie za pomocą polecenia **invoke-AppWrappingTool**, używając następującej składni:

   ```PowerShell
   Invoke-AppWrappingTool [-InputPath] <String> [-OutputPath] <String> -KeyStorePath <String> -KeyStorePassword <SecureString>
   -KeyAlias <String> -KeyPassword <SecureString> [-SigAlg <String>] [<CommonParameters>]
   ```

   W poniższej tabeli przedstawiono szczegółowo właściwości polecenia **invoke-AppWrappingTool**:

|Właściwość|Informacje|Przykład|
|-------------|--------------------|---------|
|**-InputPath**&lt;ciąg&gt;|Ścieżka źródłowej aplikacji systemu Android (.apk).| |
 |**-OutputPath**&lt;ciąg&gt;|Ścieżka do wyjściowej aplikacji systemu Android. Jeśli ta ścieżka katalogu będzie taka sama jak określona w parametrze InputPath, opakowywanie nie powiedzie się.| |
|**-KeyStorePath**&lt;ciąg&gt;|Ścieżka do pliku magazynu kluczy, który zawiera pary kluczy publicznych/prywatnych do podpisania.|Domyślnie pliki magazynu kluczy są przechowywane w folderze „C:\Program Files (x86)\Java\jreX.X.X_XX\bin”. |
|**-KeyStorePassword**&lt;ciąg_bezpieczny&gt;|Hasło używane do odszyfrowywania magazynu kluczy. System Android wymaga, aby wszystkie pakiety aplikacji (apk) były podpisane. Użyj narzędzia Java keytool do wygenerowania wartości KeyStorePassword. Uzyskaj więcej informacji o [magazynie kluczy](https://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html) środowiska Java.| |
|**-KeyAlias**&lt;ciąg&gt;|Nazwa klucza, który ma być używany do podpisywania.| |
|**-KeyPassword**&lt;ciąg_bezpieczny&gt;|Hasło używane do odszyfrowania klucza prywatnego, który zostanie użyty do podpisywania.| |
|**-SigAlg**&lt;ciąg_bezpieczny&gt;| (Opcjonalnie) Nazwa algorytmu sygnatury używanego do podpisywania. Algorytm musi być zgodny z kluczem prywatnym.|Przykłady: SHA256withRSA, SHA1withRSA|
|**-UseMinAPILevelForNativeMultiDex**| Obowiązkowe Użyj tej flagi, aby zwiększyć minimalny poziom interfejsu API źródłowej aplikacji systemu Android do 21. Ta flaga wyświetli monit o potwierdzenie, ponieważ będzie ograniczać, kto może zainstalować tę aplikację. Użytkownicy mogą pominąć okno dialogowe potwierdzenia, dołączając parametr "-confirm: $false" do polecenia programu PowerShell. Flaga powinna być używana tylko przez klientów w aplikacjach z minimalnym interfejsem API < 21, co nie powiodło się z powodu błędów przepełnienia DEX. | |
| **&lt;typowe_parametry&gt;** | (Opcjonalnie) To polecenie obsługuje typowe parametry programu PowerShell, takie jak verbose i debug. |


- Listę typowych parametrów można znaleźć w [Centrum skryptów Microsoft](https://technet.microsoft.com/library/hh847884.aspx).

- Aby uzyskać szczegółowe informacje dotyczące używania tego narzędzia, wpisz polecenie:

    ```PowerShell
    Help Invoke-AppWrappingTool
    ```

**Przykład:**

Zaimportuj moduł programu PowerShell.

```PowerShell
Import-Module "C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool\IntuneAppWrappingTool.psm1"
```

Uruchom narzędzie opakowujące aplikacje z aplikacją natywną HelloWorld.apk.

```PowerShell
invoke-AppWrappingTool -InputPath .\app\HelloWorld.apk -OutputPath .\app_wrapped\HelloWorld_wrapped.apk -KeyStorePath "C:\Program Files (x86)\Java\jre1.8.0_91\bin\mykeystorefile" -keyAlias mykeyalias -SigAlg SHA1withRSA -Verbose
```

Zostanie wyświetlony monit o hasła **KeyStorePassword** i **KeyPassword**. Wprowadź poświadczenia użyte do utworzenia pliku magazynu kluczy.

Opakowana aplikacja zostanie wygenerowana i zapisana wraz z plikiem dziennika w określonej ścieżce danych wyjściowych.

## <a name="how-often-should-i-rewrap-my-android-application-with-the-intune-app-wrapping-tool"></a>Jak często należy ponownie opakowywać aplikację systemu Android za pomocą narzędzia opakowującego aplikacje usługi Intune?
Główne scenariusze, w których trzeba będzie ponownie opakować aplikacje:
* Sama aplikacja wydała nową wersję. Poprzednia wersja aplikacji została opakowana i przekazana do konsoli usługi Intune.
* Narzędzie opakowujące aplikacje usługi Intune dla systemu Android wydało nową wersję, która oferuje kluczowe poprawki usterek i nowe funkcje zasad ochrony aplikacji, przeznaczone specjalnie dla usługi Intune. Taka sytuacja występuje co 6–8 tygodni za pośrednictwem repozytorium GitHub dla [narzędzia opakowującego aplikacje usługi Intune dla systemu Android](https://github.com/msintuneappsdk/intune-app-wrapping-tool-android).

Niektóre najlepsze rozwiązania dotyczące ponownego opakowywania: 
* Obsługa certyfikatów podpisywania używanych podczas procesu kompilacji, zobacz [Ponowne używanie certyfikatów podpisywania i opakowywanie aplikacji](app-wrapper-prepare-android.md#reusing-signing-certificates-and-wrapping-apps)

## <a name="reusing-signing-certificates-and-wrapping-apps"></a>Ponowne używanie certyfikatów podpisywania i opakowywanie aplikacji
System Android wymaga podpisania wszystkich aplikacji za pomocą ważnego certyfikatu przed zainstalowaniem ich na urządzeniach z systemem Android.

Opakowane aplikacje mogą zostać podpisane podczas procesu opakowywania lub *po* tym procesie przy użyciu istniejących narzędzi do podpisywania. Wszystkie informacje dotyczące podpisywania znajdujące się w aplikacji przed jej opakowaniem zostaną odrzucone. Jeśli to możliwe, podczas procesu opakowywania należy użyć informacji dotyczących podpisywania, które zostały wcześniej użyte podczas procesu kompilacji. W niektórych organizacjach może to wymagać współpracy z właścicielami informacji o magazynie kluczy (tj. zespołem zajmującym się kompilacją aplikacji). 

Jeśli poprzedni certyfikat podpisywania nie może zostać użyty lub aplikacja nie została wcześniej wdrożona, możliwe jest utworzenie nowego certyfikatu podpisywania, zgodnie z instrukcjami znajdującymi się w [przewodniku dewelopera systemu Android](https://developer.android.com/studio/publish/app-signing.html#signing-manually).

Jeśli aplikacja została wcześniej wdrożona za pomocą innego certyfikatu podpisywania, nie można przekazać jej do usługi Intune po uaktualnieniu. Scenariusze uaktualniania aplikacji nie będą miały zastosowania, jeśli aplikacja została podpisana za pomocą innego certyfikatu niż ten, który został użyty podczas jej kompilacji. W związku z tym wszelkie nowe certyfikaty podpisywania powinny zostać zachowane na potrzeby uaktualnień aplikacji. 

## <a name="security-considerations-for-running-the-app-wrapping-tool"></a>Uwagi dotyczące zabezpieczeń przy uruchamianiu narzędzia opakowującego aplikacje
Aby uniknąć potencjalnego fałszowania, ujawnienia informacji i ataków opartych na podniesieniu uprawnień:

- Upewnij się, że wejściowa aplikacja biznesowa, aplikacja wyjściowa i magazyn kluczy środowiska Java są na tym samym komputerze, na którym jest uruchamiane narzędzie opakowujące aplikacje.

- Zaimportuj aplikację wyjściową do usługi Intune na tym samym komputerze, na którym uruchomiono to narzędzie. Zobacz temat [keytool](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html), aby uzyskać więcej informacji o narzędziu Java keytool.

- Jeśli aplikacja wyjściowa i narzędzie znajdują się w ścieżce Universal Naming Convention (UNC), a narzędzie i pliki wejściowe nie zostały uruchomione na tym samym komputerze, skonfiguruj zabezpieczenia środowiska, używając [zabezpieczeń protokołu internetowego (IPsec)](https://wikipedia.org/wiki/IPsec) lub [podpisywania bloku komunikatów serwera (SMB)](https://support.microsoft.com/kb/887429).

- Upewnij się, że aplikacja pochodzi z zaufanego źródła.

- Zabezpiecz katalog wyjściowy, który zawiera opakowaną aplikację. Rozważ użycie katalogu poziomu użytkownika dla produktu wyjściowego.

## <a name="see-also"></a>Zobacz także
- [Wybieranie sposobu przygotowania aplikacji do zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](../developer/apps-prepare-mobile-application-management.md)

- [Przewodnik dewelopera po zestawie SDK aplikacji usługi Microsoft Intune dla systemu Android](../developer/app-sdk-android.md)