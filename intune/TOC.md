# [Wprowadzenie](introduction-intune.md)
## [Co to jest Azure Portal?](what-is-intune.md)
## [Co to jest usługa Intune for Education?](introduction-intune-education.md)
## [Funkcje usługi Intune na platformie Azure](ui-changes.md)
## [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej](free-trial-sign-up.md)
## [Co nowego](whats-new.md)
### [Co nowego w interfejsie użytkownika aplikacji](whats-new-app-ui.md)
### [Archiwum nowości (Azure Portal)](whats-new-archive.md)
### [Archiwum nowości (klasyczny portal)](whats-new-archive-classic.md)

<!--## High-level architecture-->

## [Cykle życia urządzeń i aplikacji](introduction-device-app-lifecycles.md)
### [Cykl wsparcia technicznego urządzenia](device-lifecycle.md)
### [Cykl wsparcia technicznego aplikacji](app-lifecycle.md)
## [Typowe scenariusze](common-scenarios.md)
## [Znane problemy](known-issues.md)
## [Uzyskiwanie pomocy technicznej](get-support.md)
## [Opis usługi Intune](microsoft-intune-service-description.md)

<!--# Get started
## [Manage devices](/intune-classic/understand-explore/mobile-device-management-trial-guide-microsoft-intune?toc=/intune/toc.json)
## [Create policies](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-3?toc=/intune/toc.json)
## [Manage apps](/intune-classic/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune-step-4?toc=/intune/toc.json) -->


# Planowanie wdrożenia
## [Przewodnik planowania](planning-guide.md)
### [Określanie celów](planning-guide-deployment-goals.md)
### [Identyfikowanie scenariuszy](planning-guide-scenarios.md)
### [Określanie wymagań](planning-guide-requirements.md)
### [Opracowywanie planu wdrażania](planning-guide-rollout-plan.md)
### [Opracowywanie planu komunikacji](planning-guide-communication-plan.md)
### [Opracowywanie planu pomocy technicznej](planning-guide-support-plan.md)
### [Projektowanie](planning-guide-design.md)
### [Implementacja](planning-guide-onboarding.md)
### [Testowanie i walidacja](planning-guide-test-validation.md)
### [Dodatkowe zasoby](planning-guide-resources.md)
<!-- ## Scenario implementation guides
### [BYOD](/enterprise-mobility-security/solutions/enable-byod?toc=/intune/toc.json)
### [Protect O365 data](/enterprise-mobility-security/solutions/protect-office365-data-with-intune?toc=/intune/toc.json)
### [Protect on-premises data](/enterprise-mobility-security/solutions/protect-on-premises-data-with-intune?toc=/intune/toc.json)
### [Protect data without enrollment](/enterprise-mobility-security/solutions/protect-company-data-without-managing-devices?toc=/intune/toc.json)
### [Manage company-owned devices](/enterprise-mobility-security/solutions/issue-corp-devices?toc=/intune/toc.json)
### [Manage shared devices](/enterprise-mobility-security/solutions/limited-use-shared-devices?toc=/intune/toc.json) -->
## [Przewodnik po migracji](migration-guide.md)
### [Przygotowanie usługi Intune](migration-guide-prepare.md)
#### [Konfiguracja podstawowa](migration-guide-setup.md)
#### [Konfiguracja zasad zarządzania urządzeniami i aplikacjami](migration-guide-configure-policies.md)
#### [Konfiguracja zasad ochrony aplikacji](migration-guide-app-protection-policies.md)
#### [Zagadnienia dotyczące migracji](migration-guide-considerations.md)
### [Kampania migracji](migration-guide-campaign.md)
#### [Planowanie komunikacji](migration-guide-communication-plan.md)
#### [Wdrożenie dysku](migration-guide-drive-adoption.md)
#### [Typowy cykl migracji](migration-guide-cycle.md)


# Instrukcje

## [Skonfiguruj usługę](setup-steps.md)
### [Wymagania wstępne](supported-devices-browsers.md)
#### [Użycie przepustowości sieci](network-bandwidth-use.md)
### [Logowanie do usługi Intune](account-sign-up.md)
### [Skonfigurowanie domen](custom-domain-name-configure.md)
### [Dodawanie użytkowników](users-permissions-add.md)
### [Przypisywanie licencji](licenses-assign.md)       
### [Dostosowywanie aplikacji Portal firmy](company-portal-customize.md)     
### [Ustawianie urzędu zarządzania urządzeniami przenośnymi](mdm-authority-set.md)

## [Rejestrowanie urządzeń](device-enrollment.md)
### Wymagania wstępne
#### [Konfigurowanie warunków i postanowień](terms-and-conditions-create.md)
#### [Konfigurowanie ograniczeń](enrollment-restrictions-set.md)
#### [Uzyskiwanie certyfikatu wypychania MDM firmy Apple](apple-mdm-push-certificate-get.md)
#### [Dodawanie identyfikatorów firmy](corporate-identifiers-add.md)
#### [Konfigurowanie menedżera rejestracji urządzeń](device-enrollment-manager-enroll.md)
#### [Mapowanie urządzeń na grupy](device-group-mapping.md)
### [Konfigurowanie rejestrowania urządzeń z systemem Windows](windows-enroll.md)
#### [Automatyczne rejestrowanie](windows-enroll.md)
#### [Rejestrowanie zbiorcze](windows-bulk-enroll.md)
### [Konfigurowanie rejestrowania urządzeń z systemem Android](android-enroll.md)
### Konfigurowanie rejestrowania urządzeń z systemem iOS
#### [Przy użyciu programu Device Enrollment Program](device-enrollment-program-enroll-ios.md)
#### [Przy użyciu usługi Apple School Manager](apple-school-manager-set-up-ios.md)
#### [Przy użyciu programu Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md)
### [Konfigurowanie rejestrowania urządzeń z systemem macOS](macos-enroll.md)
### [Informowanie użytkowników](end-user-educate.md)

## [Zarządzanie urządzeniami](device-management.md)
### [Czyszczenie urządzenia](devices-wipe.md)
### [Obchodzenie blokady aktywacji](device-activation-lock-bypass.md)
### [Resetowanie urządzenia do ustawień fabrycznych](device-factory-reset.md)
### [Zarządzanie funkcją Rozpoczęcie od nowa w systemie Windows](device-fresh-start.md)
### [Znajdowanie zgubionego urządzenia z systemem iOS](device-locate.md)
### [Włączanie trybu zgubienia w systemie iOS](device-lost-mode.md)
### [Blokowanie urządzenia](device-remote-lock.md)
### [Usuń dane firmy](device-company-data-remove.md)
### [Zresetuj kod dostępu](device-passcode-reset.md)
### [Ponowne uruchamianie urządzenia](device-restart.md)
### [Zdalne sterowanie w systemie Android](device-profile-android-teamviewer.md)
### [Przeglądanie spisu urządzeń](device-inventory.md)

## [Zarządzanie użytkownikami](user-management.md)
### [Wprowadzenie do grup](groups-get-started.md)
<!--### Add and delete users -->

## [Zarządzanie aplikacjami](app-management.md)
### [Dodawanie aplikacji](apps-add.md)
#### [Aplikacje ze sklepu dla systemu Android](store-apps-android.md)
#### [Aplikacje LOB dla systemu Android](lob-apps-android.md)
#### [Aplikacje ze sklepu dla systemu iOS](store-apps-ios.md)
#### [Aplikacje LOB dla systemu iOS](lob-apps-ios.md)
#### [Aplikacje sieci Web](web-app.md)
#### [Aplikacje ze sklepu dla systemu Windows Phone 8.1](store-apps-windows-phone-8-1.md)
#### [Aplikacje LOB dla systemu Windows Phone](lob-apps-windows-phone.md)
#### [Aplikacje ze sklepu dla systemu Windows](store-apps-windows.md)
#### [Aplikacje LOB dla systemu Windows](lob-apps-windows.md)
#### [Aplikacje programu Android for Work](apps-add-android-for-work.md)
### [Przypisywanie aplikacji](apps-deploy.md)
### [Monitorowanie aplikacji](apps-monitor.md)
### [Profile konfiguracji aplikacji systemu iOS](app-configuration-policies-use-ios.md)
### [Profile konfiguracji aplikacji systemu Android](app-configuration-policies-use-android.md)
### [Korzystanie z profilów aprowizacji aplikacji systemu iOS](app-provisioning-profile-ios.md)
### [Czyszczenie selektywne aplikacje](apps-selective-wipe.md)
### [Praca z aplikacjami i książkami nabytymi w ramach zakupów zbiorczych](vpp-apps.md)
#### [Aplikacje VPP dla systemu iOS](vpp-apps-ios.md)
#### [Aplikacje ze Sklepu Windows dla firm](windows-store-for-business.md)
#### [Książki elektroniczne dla systemu iOS](vpp-ebooks-ios.md)
### [Konfigurowanie aplikacji Portal firmy](company-portal-app.md)
### [Konfigurowanie programu Managed Browser](app-configuration-managed-browser.md)
## [Korzystanie z zasad ochrony aplikacji](app-protection-policies.md)
### [Przygotowywanie do konfigurowania zasad ochrony aplikacji WIP](app-protection-policies-configure-windows-10.md)
### [Tworzenie i przypisywanie zasad ochrony aplikacji WIP](windows-information-protection-policy-create.md)
### [Ustawienia systemu Android](app-protection-policy-settings-android.md)
### [Ustawienia systemu iOS](app-protection-policy-settings-ios.md)
### [Weryfikowanie zasad ochrony aplikacji](app-protection-policies-validate.md)
### [Monitorowanie stanu użytkownika ochrony aplikacji](app-protection-policies-monitor.md)
### [Przygotowywanie do konfigurowania zasad ochrony aplikacji WIP](app-protection-policies-configure-windows-10.md)
### [Tworzenie i przypisywanie zasad ochrony aplikacji WIP](windows-information-protection-policy-create.md)
### [Zarządzanie przesyłaniem danych między aplikacjami systemu iOS](data-transfer-between-apps-manage-ios.md)

## [Konfigurowanie urządzeń](device-profiles.md)
### [Konfigurowanie profilów urządzeń](device-profile-create.md)
### [Konfigurowanie funkcji urządzeń](device-features-configure.md)
#### [Funkcja AirPrint dla systemów iOS i MacOS](air-print-settings-ios-macos.md)
#### [Funkcja AirPlay dla systemu iOS](airplay-settings-ios.md)
#### [Układ ekranu głównego dla systemu iOS](home-screen-settings-ios.md)
#### [Powiadomienia aplikacji dla systemu iOS](app-notification-settings-ios.md)
#### [Urządzenia udostępnione dla systemu iOS](shared-device-settings-ios.md)
#### [Ustawienia filtru zawartości sieci Web dla urządzeń z systemem iOS](web-content-filter-settings-ios.md)
### [Konfigurowanie ograniczeń dotyczących urządzeń](device-restrictions-configure.md)
#### [Android](device-restrictions-android.md)
#### [iOS](device-restrictions-ios.md)
#### [macOS](device-restrictions-macos.md)
#### [Windows 8.1](device-restrictions-windows-8-1.md)
#### [Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
#### [Windows 10](device-restrictions-windows-10.md)
#### [Windows 10 Team](device-restrictions-windows-10-teams.md)
#### [Android for Work](device-restrictions-android-for-work.md)
### [Konfigurowanie ustawień poczty e-mail](email-settings-configure.md)
#### [Android](email-settings-android.md)
#### [iOS](email-settings-ios.md)
#### [Windows Phone 8.1](email-settings-windows-phone-8-1.md)
#### [Windows 10](email-settings-windows-10.md)
### [Konfigurowanie ustawień sieci VPN](vpn-settings-configure.md)
#### [Android](vpn-settings-android.md)
#### [iOS](vpn-settings-ios.md)
#### [macOS](vpn-settings-macos.md)
#### [Windows 8.1](vpn-settings-windows-8-1.md)
#### [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
#### [Windows 10](vpn-settings-windows-10.md)
### [Konfigurowanie ustawień sieci Wi-Fi](wi-fi-settings-configure.md)
#### [Android](wi-fi-settings-android.md)
#### [iOS](wi-fi-settings-ios.md)
#### [macOS](wi-fi-settings-macos.md)
#### [Windows 8.1 i Windows 10](wi-fi-settings-import-windows-8-1.md)
### [Konfigurowanie ustawień uaktualniania systemu Windows 10](edition-upgrade-configure-windows-10.md)
### [Konfigurowanie ustawień edukacyjnych systemu Windows 10](education-settings-configure.md)
### [Konfigurowanie ustawień usług edukacyjnych dla urządzeń z systemem iOS](education-settings-configure-ios.md)
### [Konfigurowanie ustawień usługi Windows Update dla firm](windows-update-for-business-configure.md)
### [Konfigurowanie certyfikatów](certificates-configure.md)
#### [SCEP](certificates-scep-configure.md)
#### [PKCS](certficates-pfx-configure.md)
### [Konfigurowanie ustawień usługi Windows Information Protection](windows-information-protection-configure.md)
### [Przypisywanie profilów](device-profile-assign.md)
### [Monitorowanie profilów](device-profile-monitor.md)
### [Rozwiązywanie problemów z profilami](device-profile-troubleshoot.md)

## [Ustawianie zgodności urządzenia](device-compliance.md)
### [Wymagania wstępne](device-compliance-get-started.md)
### [Tworzenie zasad dla systemu Android](compliance-policy-create-android.md)
### [Tworzenie zasad dla programu Android for Work](compliance-policy-create-android-for-work.md)
### [Tworzenie zasad dla systemu iOS](compliance-policy-create-ios.md)
### [Tworzenie zasad dla systemu Windows](compliance-policy-create-windows.md)
<!--### Create Actions for noncompliance-->
### [Monitorowanie zgodności urządzenia](compliance-policy-monitor.md)

## [Zarządzanie dostępem warunkowym](conditional-access.md)
### [Typowe sposoby korzystania z dostępu warunkowego](conditional-access-intune-common-ways-use.md)
### [Dostęp warunkowy oparty na aplikacji](app-based-conditional-access-intune.md)
### [Instalowanie lokalnego łącznika programu Exchange](exchange-connector-install.md)
### [Tworzenie i przypisz zasady dostępu warunkowego](conditional-access-exchange-create.md)
### [Konfigurowanie dostępu warunkowego opartego na aplikacji dla usługi Exchange Online](app-based-conditional-access-intune-exchange-online-create.md)
### [Konfigurowanie dostępu warunkowego opartego na aplikacji dla usługi SharePoint Online](app-based-conditional-access-intune-sharepoint-online-create.md)
### [Biblioteki ADAL i usługa Intune](app-modern-authentication-block.md)
### [Monitorowanie zgodność z dostępem warunkowym](conditional-access-exchange-monitor.md)

## Ochrona danych i urządzeń

### [Usługa Mobile Threat Defense](mobile-threat-defense.md)

#### [Konfigurowanie usługi Lookout](lookout-mobile-threat-defense-connector.md)
##### [Konfigurowanie integracji usług Lookout i Intune](lookout-mtd-subscription-setup.md)
##### [Włączanie obsługi rozwiązania Lookout w usłudze Intune](lookout-mtd-connector-enable.md)
##### [Wdrażanie aplikacji do użycia z rozwiązaniem Lookout](lookout-for-work-app-configure-deploy.md)
##### [Zasady zgodności urządzeń w usłudze Lookout](lookout-device-compliance-policy-create.md)

#### [Konfigurowanie programu Skycure](skycure-mobile-threat-defense-connector.md)
##### [Konfigurowanie rejestracji jednokrotnej w usłudze Azure AD](skycure-azure-sso-configure.md)
##### [Pobieranie zasad konfiguracji aplikacji systemu iOS](skycure-ios-app-configuration-policy-download.md)
##### [Dodawanie i konfigurowanie aplikacji](skycure-microsoft-authenticator-app-ios-app-configuration-policy-add.md)
##### [Wdrażanie aplikacji do użycia z rozwiązaniem Skycure](skycure-microsoft-authenticator-app-ios-app-configuration-policy-deploy.md)
##### [Integrowanie programu Skycure i usługi Intune](skycure-mtd-connector-integration.md)
##### [Włączanie programu Skycure w usłudze Intune](skycure-mtd-connector-enable.md)
##### [Zasady zgodności urządzeń w programie Skycure](skycure-device-compliance-policy-create.md)

### [Konfigurowanie funkcji Windows Hello](windows-hello.md)        
<!-- ### Protect devices with remote actions        -->

## [Zarządzanie rolami](role-based-access-control.md)
<!-- ### Create a custom role
### Assign a role -->
### [Korzystanie z roli pracownika pomocy technicznej](help-desk-operators.md)
<!-- ### Custom role settings -->

## [Zarządzanie komputerami przy użyciu oprogramowania agenta](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune?toc=/intune/toc.json)
### [Instalowanie klienta komputera](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune?toc=/intune/toc.json)
### [Typowe zadania związane z zarządzaniem komputerami](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client?toc=/intune/toc.json)
#### [Zasady dotyczące komputerów](/intune-classic/deploy-use/use-policies-to-simplify-windows-pc-management?toc=/intune/toc.json)
#### [Wyświetlanie spisu](/intune-classic/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
#### [Wycofywanie komputerów](/intune-classic/deploy-use/retire-a-windows-pc-with-microsoft-intune?toc=/intune/toc.json)
#### [Łączenie komputerów z użytkownikami](/intune-classic/deploy-use/manage-user-device-linking-for-windows-pcs-with-microsoft-intune?toc=/intune/toc.json)
#### [Pomoc zdalna](/intune-classic/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
### [Zasady ochrony komputerów z systemem Windows](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
#### [Aktualizacje oprogramowania](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune?toc=/intune/toc.json)
#### [Zapora systemu Windows](/intune-classic/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune?toc=/intune/toc.json)
#### [Program Endpoint Protection](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune?toc=/intune/toc.json)
### [Dodawanie aplikacji dla komputerów klienckich usługi Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune?toc=/intune/toc.json)
### [Zarządzanie umowami licencyjnymi](/intune-classic/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune?toc=/intune/toc.json)
### [Rozwiązywanie konfliktów zasad](/intune-classic/deploy-use/resolve-gpo-and-microsoft-intune-policy-conflicts?toc=/intune/toc.json)


# Monitorowanie i rozwiązywanie problemów
## [Monitorowanie wydatków telekomunikacyjnych](telecom-expenses-monitor.md)


# Programowanie i dostosowywanie
## [Konfigurowanie niestandardowych ustawień urządzenia](custom-settings-configure.md)
### [Android](custom-settings-android.md)
#### [Profil sieci Wi-Fi z kluczem wstępnym](wi-fi-profile-shared-key.md)
#### [Profil sieci VPN dla aplikacji](android-pulse-secure-per-app-vpn.md)
#### [Zezwalanie na aplikacje dla systemu Samsung KNOX Standard lub blokowanie ich](samsung-knox-apps-allow-block.md)
### [iOS](custom-settings-ios.md)
### [macOS](custom-settings-macos.md)
### [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
### [Windows 10](custom-settings-windows-10.md)
### [Android for Work](custom-settings-android-for-work.md)
## [Przygotowanie aplikacji biznesowych do zarządzania aplikacjami mobilnymi](apps-prepare-mobile-application-management.md)
### [Narzędzie opakowujące aplikacje dla systemu iOS](app-wrapper-prepare-ios.md)
### [Narzędzie opakowujące aplikacje dla systemu Android](app-wrapper-prepare-android.md)
## [Ładowanie bezpośrednie aplikacji systemu Windows](app-sideload-windows.md)
## [Zestaw SDK aplikacji usługi Intune](app-sdk.md)
### [Wprowadzenie do zestawu SDK aplikacji usługi Intune](app-sdk-get-started.md)
### [Zestaw SDK aplikacji usługi Intune dla systemu iOS](app-sdk-ios.md)
### [Zestaw SDK aplikacji usługi Intune dla systemu Android](app-sdk-android.md)
### [Wtyczka Cordova zestawu SDK aplikacji usługi Intune](app-sdk-cordova.md)
### [Składnik Xamarin zestawu SDK aplikacji usługi Intune](app-sdk-xamarin.md)
## [Korzystanie z interfejsów API programu Intune Graph](intune-graph-apis.md)
## [Interfejs API programu Intune Graph](https://graph.microsoft.io/docs/api-reference/beta/resources/intune_graph_overview)


# [Słownik](intune-glossary.md)