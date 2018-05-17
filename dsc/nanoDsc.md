---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Korzystanie z platformy DSC na serwerze Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="using-dsc-on-nano-server"></a>Korzystanie z platformy DSC na serwerze Nano Server

> Dotyczy: Środowiska Windows PowerShell 5.0

**DSC na serwerze Nano** jest opcjonalny pakiet w `NanoServer\Packages` folderu nośnika systemu Windows Server 2016. Pakiet można zainstalować podczas tworzenia dysku VHD dla Nano Server określając **Microsoft-NanoServer-DSC-Package** jako wartość **pakiety** parametr **NanoServerImage nowy**  funkcji. Na przykład w przypadku tworzenia dysku VHD dla maszyny wirtualnej, polecenie będzie wyglądać podobne do poniższych:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Aby uzyskać informacje o instalowaniu i używaniu Nano Server, a także sposobu zarządzania Nano Server z usługi zdalne środowiska PowerShell, zobacz [wprowadzenie Nano Server](https://technet.microsoft.com/library/mt126167.aspx).


## <a name="dsc-features-available-on-nano-server"></a>Dostępne na serwerze Nano funkcje DSC

 Ponieważ Nano Server obsługuje tylko ograniczony zestaw interfejsów API w porównaniu do pełnej wersji systemu Windows Server, usłudze Konfiguracja DSC systemem pełnej wersji produktu w chwili obecnej DSC na serwerze Nano nie ma pełnej funkcjonalności parzystości. DSC na serwerze Nano trwa opracowywanie aktywne i nie jest jeszcze funkcja, pełny.

 Następujące funkcje usługi Konfiguracja DSC są obecnie dostępne na serwerze Nano:


* Trybach wypychania i ściągania

* Wszystkie polecenia cmdlet DSC, które istnieją w pełnej wersji systemu Windows Server, w tym następujące:
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn521621.aspx)
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* Konfiguracje kompilacji (zobacz [konfiguracji DSC](configurations.md))

  **Problem:** hasła szyfrowania (zobacz [Zabezpieczanie pliku MOF](securemof.md)) podczas konfigurowania kompilacji nie działa.

* Kompilowanie metaconfigurations (zobacz [Konfigurowanie lokalny program Configuration Manager](metaConfig.md))

* Z zasobów w kontekście użytkownika (zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika (Uruchom jako)](runAsUser.md))

* Zasoby oparte na klasie (zobacz [pisania niestandardowego zasobu DSC środowiska PowerShell klasy](authoringResourceClass.md))

* Debugowanie zasobów DSC (zobacz [zasobów debugowania DSC](debugresource.md))

  **Problem:** nie działa, jeśli zasób jest za pomocą PsDscRunAsCredential (zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md))

* [Określanie zależności między węzłami](crossNodeDependencies.md)

* [Wersjonowanie zasobów](sxsResource.md)

* Klient ściągania (konfiguracje i zasobów) (zobacz [Konfigurowanie klienta ściągania przy użyciu nazwy konfiguracji](pullClientConfigNames.md))

* [Konfiguracje częściowe (ściągania i wypychania)](partialConfigs.md)

* [Raportowania na serwerze ściągania](reportServer.md)

* Szyfrowanie MOF

* Rejestrowanie zdarzeń

* Raportowanie usługi Konfiguracja DSC automatyzacji Azure

* Zasoby, które są w pełni funkcjonalne
  * [Archiwum](archiveResource.md)
  * [Środowisko](environmentResource.md)
  * [Plik](fileResource.md)
  * [Dziennik](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Skrypt](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (zobacz [określania zależności między węzłami](crossNodeDependencies.md))
  * WaitForAny (zobacz [określania zależności między węzłami](crossNodeDependencies.md))
  * WaitForSome (zobacz [określania zależności między węzłami](crossNodeDependencies.md))

* Zasoby, które działają częściowo
  * [Grupa](groupResource.md)
  * GroupSet

  **Problem:** powyżej zasobów się niepowodzeniem, jeśli określone wystąpienie jest wywoływana dwukrotnie (uruchomiony dwukrotnie tę samą konfigurację)

  * [Usługi](serviceResource.md)
  * ServiceSet

  **Problem:** działa tylko w przypadku uruchamiania/zatrzymywania usługi (stan). Kończy się niepowodzeniem, jeśli jeden próbuje zmienić innych atrybutów usługi, takich jak startuptype, poświadczenia, opis itp. Zgłoszono błąd jest podobny do:

  *Nie można odnaleźć typu [management.managementobject]: Sprawdź, czy zestaw zawierający ten typ jest załadowany.*

* Zasoby, które nie działają
  * [Użytkownika](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a>Nie jest dostępny na serwerze Nano funkcje DSC

Następujące funkcje usługi Konfiguracja DSC nie są obecnie dostępne na serwerze Nano:

* Odszyfrowywanie MOF dokument z zaszyfrowane hasło
* Serwerem ściągania — nie można obecnie skonfigurować serwera ściągania, na serwerze Nano
* Wszystko, co nie jest na liście działania funkcji

## <a name="using-custom-dsc-resources-on-nano-server"></a>Na serwerze Nano przy użyciu niestandardowych zasobów DSC

Z powodu ograniczonej zestawów interfejsów API systemu Windows i bibliotek CLR dostępne na serwerze Nano DSC zasoby, które działają w pełnej wersji środowiska CLR systemu Windows nie działać na serwerze Nano.
Ukończ testowanie end-to-end przed wdrożeniem wszystkich zasobów niestandardowych DSC w środowisku produkcyjnym.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do korzystania z Nano Server](https://technet.microsoft.com/library/mt126167.aspx)