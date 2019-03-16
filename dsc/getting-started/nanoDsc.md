---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z platformy DSC na serwerze Nano Server
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054666"
---
# <a name="using-dsc-on-nano-server"></a>Korzystanie z platformy DSC na serwerze Nano Server

> Dotyczy: Windows PowerShell 5.0

**DSC na serwerze Nano Server** jest opcjonalny pakiet w `NanoServer\Packages` folderu nośników systemu Windows Server 2016. Po utworzeniu wirtualnego dysku twardego, określając dla serwera Nano Server można zainstalować pakietu **Microsoft-NanoServer-DSC-Package** jako wartość **pakietów** parametru **New-NanoServerImage**  funkcji. Na przykład w przypadku tworzenia dysku VHD dla maszyny wirtualnej, polecenie będzie wyglądać następująco:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Aby uzyskać informacje o instalowaniu i używaniu serwera Nano Server, a także jak zarządzać serwerem Nano Server przy użyciu komunikacji zdalnej programu PowerShell, zobacz [wprowadzenie Nano Server](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>Funkcji DSC, które są dostępne na serwerze Nano Server

Ponieważ serwer Nano Server obsługuje tylko ograniczony zestaw interfejsów API w porównaniu do pełnej wersji systemu Windows Server, DSC na serwerze Nano Server nie ma pełnych parzystość za pomocą DSC uruchomionych na pełne jednostki SKU dla przez pewien czas. DSC na serwerze Nano Server jest aktywnie i nie jest jeszcze funkcji ukończone.

Następujące funkcje DSC są obecnie dostępne na serwerze Nano Server:

Trybach wypychania i ściągania

- Wszystkie polecenia cmdlet DSC, które istnieją w pełnej wersji systemu Windows Server, w tym następujące:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Kompilowanie konfiguracji (zobacz [konfiguracje DSC](../configurations/configurations.md))

  **Problem:** Hasło szyfrowania (zobacz [Zabezpieczanie pliku MOF](../pull-server/secureMOF.md)) podczas konfiguracji kompilacji nie działa.

- Kompilowanie metaconfigurations (zobacz [Konfigurowanie programu Local Configuration Manager](../managing-nodes/metaConfig.md))

- Uruchamianie zasobami dostępnymi w ramach kontekstu użytkownika (zobacz [systemem DSC przy użyciu poświadczeń użytkownika (Uruchom jako)](../configurations/runAsUser.md))

- Zasoby oparte na klasach (zobacz [pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell](../resources/authoringResourceClass.md))

- Debugowanie zasobów DSC (zobacz [zasoby DSC debugowania](../troubleshooting/debugResource.md))

  **Problem:** Nie działa, jeśli zasób jest za pomocą PsDscRunAsCredential (zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md))

- [Określanie zależności między węzłami](../configurations/crossNodeDependencies.md)

- [Przechowywanie wersji zasobu](../configurations/sxsResource.md)

- Klienta ściągania (konfiguracji i zasobów) (zobacz [Konfigurowanie klienta ściągania przy użyciu nazw konfiguracji](../pull-server/pullClientConfigNames.md))

- [Konfiguracje częściowe (ściągania i wypychania)](../pull-server/partialConfigs.md)

- [Raportowanie do serwera ściągania](../pull-server/reportServer.md)

- Szyfrowanie pliku MOF

- Rejestrowanie zdarzeń

- Raporty usługi Azure Automation DSC

- Zasoby, które są w pełni funkcjonalne

- **Archiwizowanie**
- **Środowisko**
- **Plik**
- **Dziennik**
- **ProcessSet**
- **Registry**
- **Skrypt**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))
- **WaitForAny** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))
- **WaitForSome** (zobacz [określanie zależności między węzłami](../configurations/crossNodeDependencies.md))

- Zasoby, które są częściowo funkcjonalności
- **Grupa**
- **GroupSet**

  **Problem:** Powyżej zasobów się niepowodzeniem, jeśli określone wystąpienie jest wywoływana dwa razy (uruchomione dwa razy tę samą konfigurację)

- **Usługa**
- **ServiceSet**

  **Problem:** Działa tylko w przypadku uruchamiania/zatrzymywania usługi (stan). Kończy się niepowodzeniem, jeśli jeden próbuje zmienić inne atrybuty usługi, takie jak startuptype poświadczeń, opis itp. Podobnie jak zostaje zgłoszony błąd:

  *Nie można odnaleźć typu [management.managementobject]: Sprawdź, czy zestaw zawierający ten typ jest ładowany.*

- Zasoby, które nie działają
- **Użytkownik**

## <a name="dsc-features-not-available-on-nano-server"></a>Funkcji DSC nie są dostępne na serwerze Nano Server

Następujące funkcje DSC nie są obecnie dostępne na serwerze Nano Server:

- Odszyfrowywanie dokument MOF przy użyciu zaszyfrowane hasło
- Serwerze ściągania — nie można obecnie skonfigurować serwer ściągania na serwerze Nano Server
- Wszystko, co nie ma na liście prac funkcji

## <a name="using-custom-dsc-resources-on-nano-server"></a>Korzystanie z niestandardowych zasobów DSC na serwerze Nano Server

Ze względu na ograniczone zestawy interfejsów API Windows i biblioteki CLR dostępne na serwerze Nano Server zasoby DSC, które działają na pełną wersję środowiska CLR programu Windows nie działać na serwerze Nano Server.
Ukończ testowanie end-to-end, przed wdrożeniem wszelkie niestandardowe zasoby DSC w środowisku produkcyjnym.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do systemu Nano Server](/windows-server/get-started/getting-started-with-nano-server)
