---
title: Tworzenie profilu sieci WiFi z użyciem klucza wstępnego — Microsoft Intune — Azure | Micrososft Docs
description: Użyj profilu niestandardowego, aby utworzyć profil sieci Wi-Fi z użyciem klucza wstępnego i pobrać przykładowy kod XML dla systemu Android lub Windows albo profile sieci Wi-Fi z użyciem protokołu EAP w usłudze Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 175be4d51b034745ce6fab050f68be277f1d4858
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723765"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key---intune"></a>Użycie niestandardowego profilu urządzenia do tworzenia profilu sieci Wi-Fi z użyciem klucza wstępnego — usługa Intune
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Klucze wstępne (PSK) są zazwyczaj używane do uwierzytelniania użytkowników w sieciach Wi-Fi lub bezprzewodowych sieciach LAN. Za pomocą usługi Intune można utworzyć profil sieci Wi-Fi z użyciem klucza wstępnego. Aby utworzyć profil, skorzystaj z funkcji **Niestandardowe profile urządzenia** w usłudze Intune. Ten artykuł zawiera także przykłady sposobu tworzenia profilu sieci Wi-Fi z użyciem protokołu EAP.

> [!IMPORTANT]
>- Użycie klucza wstępnego w systemie Windows 10 powoduje wystąpienie błędu korygowania w usłudze Intune. W takim przypadku profil sieci Wi-Fi zostanie prawidłowo przypisany do urządzenia i będzie działać zgodnie z oczekiwaniami.
>- Jeśli eksportujesz profil sieci Wi-Fi, który zawiera klucz wstępny, upewnij się, że plik jest chroniony. Klucz ma postać zwykłego tekstu, więc odpowiedzialność za jego ochronę spoczywa na Tobie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Być może łatwiej będzie skopiować kod z komputera, który łączy się z tą siecią, zgodnie z opisem w dalszej części tego artykułu.
- Można dodać wiele sieci i kluczy, dodając więcej ustawień OMA-URI.
- W przypadku urządzeń z systemem iOS należy skonfigurować profil przy użyciu programu Apple Configurator na komputerze Mac.
- Klucz wstępny wymaga ciągu 64 cyfr szesnastkowych lub hasła o długości 8–63 drukowalnych znaków ASCII. Niektóre znaki, takie jak znak gwiazdki (*), nie są obsługiwane.

## <a name="create-a-custom-profile"></a>Tworzenie profilu niestandardowego
Możesz utworzyć profil niestandardowy z użyciem klucza wstępnego dla systemu Android lub Windows albo profilu Wi-Fi z użyciem protokołu EAP. Aby utworzyć profil za pomocą witryny Azure Portal, zobacz [Tworzenie niestandardowych ustawień urządzenia](custom-settings-configure.md). Podczas tworzenia profilu urządzenia wybierz opcję **Niestandardowe** dla platformy urządzenia. Nie wybieraj profilu sieci Wi-Fi. Po wybraniu profilu niestandardowego należy: 

1. Wprowadzić nazwę i opis profilu.
2. Dodać nowe ustawienie OMA-URI z następującymi właściwościami: 

   a. Wprowadź nazwę dla tego ustawienia sieci Wi-Fi.

   b. (Opcjonalnie) Wprowadź opis ustawienia OMA-URI lub pozostaw puste pole.

   c. Ustaw w polu **Typ danych** wartość **Ciąg**.

   d. **OMA-URI**:

   - **System Android**: ./Vendor/MSFT/WiFi/Profile/SSID/Settings
   - **System Windows**: ./Vendor/MSFT/WiFi/Profile/SSID/WlanXml

     > [!NOTE]
     > Należy pamiętać o kropce na początku.

     Identyfikator SSID jest identyfikatorem SSID, dla którego tworzysz zasady. Na przykład jeśli sieć Wi-Fi ma nazwę `Hotspot-1`, wprowadź `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

   e. **Pole wartości**: w tym miejscu należy wkleić kod XML. Zobacz przykłady w tym artykule. Zaktualizuj każdą wartość w celu dopasowania do ustawień sieci. Wskazówki można znaleźć w sekcji komentarzy w kodzie.
3. Wybierz przycisk **OK**, zapisz, a następnie przypisz zasady.

    > [!NOTE]
    > Te zasady można przypisać tylko do grup użytkowników.

Po następnym zameldowaniu się urządzenia zasady zostaną zastosowane, a profil sieci Wi-Fi zostanie utworzony na urządzeniu. Urządzenie może następnie łączyć się z siecią automatycznie.

## <a name="android-or-windows-wi-fi-profile-example"></a>Przykład profilu sieci Wi-Fi systemu Android lub Windows

Poniższy przykład zawiera kod XML dla profilu sieci Wi-Fi systemu Android lub Windows. W przykładzie przedstawiono odpowiedni format i więcej szczegółowych informacji. Jest to tylko przykład, który nie stanowi zalecanej konfiguracji w Twoim środowisku.

### <a name="important-considerations"></a>Ważne zagadnienia

- `<protected>false</protected>` należy ustawić na wartość **false**. Ustawienie wartości **true** może spowodować, że urządzenie będzie oczekiwać zaszyfrowanego hasła i spróbuje je odszyfrować, co z kolei może skutkować tym, że połączenie nie zostanie nawiązane.

- `<hex>53534944</hex>` musi mieć ustawioną wartość szesnastkową `<name><SSID of wifi profile></name>`. Urządzenia z systemem Windows 10 mogą zwracać fałszywy błąd `x87D1FDE8 Remediation failed`, ale urządzenie nadal zawiera profil.

- Plik XML zawiera znaki specjalne, takie jak `&` (handlowe „i”). Użycie znaków specjalnych może sprawić, że kod XML nie będzie działać w oczekiwany sposób. 

### <a name="example"></a>Przykład

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile-example"></a>Przykład profilu sieci Wi-Fi z użyciem protokołu EAP
Poniższy przykład zawiera kod XML dla profilu sieci Wi-Fi z użyciem protokołu EAP: W przykładzie przedstawiono odpowiedni format i więcej szczegółowych informacji. Jest to tylko przykład, który nie stanowi zalecanej konfiguracji w Twoim środowisku.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Tworzenie pliku XML z istniejącego połączenia sieci Wi-Fi

Można również utworzyć plik XML z istniejącego połączenia sieci Wi-Fi. Na komputerze z systemem Windows wykonaj następujące czynności:

1. Utwórz folder lokalny dla wyeksportowanych profilów sieci Wi-Fi, np. c:\WiFi.
2. Otwórz wiersz polecenia jako administrator (kliknij prawym przyciskiem myszy polecenie `cmd` > **Uruchom jako administrator**)
3. Uruchom polecenie `netsh wlan show profiles`. Zostanie wyświetlona lista wszystkich profilów.
4. Uruchom polecenie `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. To polecenie tworzy plik o nazwie `Wi-Fi-YourProfileName.xml` w folderze c:\WiFi.

    - Jeśli eksportujesz profil sieci Wi-Fi, który zawiera klucz wstępny, dodaj parametr `key=clear` do polecenia:
  
      `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

      `key=clear` eksportuje klucz w postaci zwykłego tekstu, który jest wymagany do pomyślnego użycia profilu.

Po utworzeniu pliku XML skopiuj i wklej składnię XML w ustawieniach OMA-URI > **Typ danych**. Lista czynności znajduje się w sekcji [Tworzenie profilu niestandardowego](#create-a-custom-profile).

> [!TIP]
> Folder `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` zawiera również wszystkie profile w formacie XML.

## <a name="best-practices"></a>Najlepsze rozwiązania

- Przed utworzeniem profilu sieci Wi-Fi z użyciem klucza wstępnego należy sprawdzić, czy urządzenie może połączyć się bezpośrednio z punktem końcowym.

- W przypadku rotacji kluczy (haseł lub kodów dostępu) należy spodziewać się przestoju i odpowiednio zaplanować wdrożenia. Rozważ wypchnięcie nowych profilów sieci Wi-Fi w czasie poza godzinami pracy. Ponadto należy ostrzec użytkowników, że może to mieć wpływ na łączność.

- W celu zapewnienia bezproblemowego przejścia upewnij się, że urządzenie użytkownika końcowego ma alternatywne połączenie z Internetem. Na przykład użytkownik końcowy musi mieć możliwość skorzystania z sieci Wi-Fi gościa (lub innej sieci Wi-Fi) albo mieć łączność komórkową na potrzeby komunikowania się z usługą Intune. Dzięki dodatkowemu połączeniu użytkownik będzie otrzymywać aktualizacje zasad podczas aktualizowania profilu firmowej sieci WiFi na urządzeniu.