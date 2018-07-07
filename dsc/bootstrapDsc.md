---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Konfigurowanie maszyny wirtualnej podczas początkowego rozruchu — za pomocą DSC
ms.openlocfilehash: 2f228a38379d1e65b31c03594e876f7226474fc3
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893356"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Konfigurowanie maszyny wirtualnej podczas początkowego rozruchu — za pomocą DSC

> [!IMPORTANT]
> Dotyczy: Windows PowerShell 5.0

## <a name="requirements"></a>Wymagania

> [!NOTE] 
> **DSCAutomationHostEnabled** klucz rejestru opisany w tym temacie nie jest dostępna w programie PowerShell 4.0.
> Aby uzyskać informacje na temat konfigurowania nowych maszyn wirtualnych podczas początkowego rozruchu w programie PowerShell 4.0 zobacz [chcesz automatycznie skonfigurować swój maszyn za pomocą DSC podczas rozruchu początkowego?] > ()https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Aby uruchomić te przykłady, są potrzebne:

- Rozruchowy wirtualny dysk twardy chcesz pracować. Możesz pobrać obrazu ISO z kopię ewaluacyjną systemu Windows Server 2016 na [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Instrukcje można znaleźć na temat sposobu tworzenia dysku VHD z obrazu ISO w [tworzenie rozruchowych wirtualnych dysków twardych](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Komputer hosta, który ma włączoną funkcją Hyper-V. Aby uzyskać informacje, zobacz [omówienie funkcji Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Za pomocą DSC, możesz zautomatyzować instalację oprogramowania i konfiguracji na komputerze podczas początkowego rozruchu.
  Można to zrobić, należy albo wstrzykiwania dokument MOF konfiguracji lub metaconfiguration do nośnika rozruchowego (np. dysk VHD), dzięki czemu są uruchamiane podczas początkowego procesu rozruchu.
  To zachowanie jest określony przez [klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucza rejestru w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`.
  Domyślnie wartość tego klucza jest 2, co pozwala DSC w czasie rozruchu.

  Jeśli użytkownik nie chce DSC w czasie rozruchu, ustaw wartość [klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucz rejestru na 0.

- Wstawić dokument MOF konfiguracji do wirtualnego dysku twardego
- Wstrzyknięcie DSC metaconfiguration do wirtualnego dysku twardego
- Wyłącz DSC w czasie rozruchu

> [!NOTE]
> Można wprowadzić zarówno `Pending.mof` i `MetaConfig.mof` do komputera, w tym samym czasie.
> Jeśli obecne są oba pliki, ustawienia określone w `MetaConfig.mof` wyższy priorytet.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Wstawić dokument MOF konfiguracji do wirtualnego dysku twardego

Wprowadzenie konfiguracji podczas początkowego rozruchu, można wstawić dokument MOF skompilowaną konfigurację do wirtualnego dysku twardego jako jego `Pending.mof` pliku.
Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiony na 2 (wartość domyślna), DSC zastosuje konfiguracją zdefiniowaną przez `Pending.mof` po rozruchu komputera dla po raz pierwszy.

W tym przykładzie używamy następującej konfiguracji, co spowoduje zainstalowanie usług IIS na nowym komputerze:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Aby wstawić dokument MOF konfiguracji do wirtualnego dysku twardego

1. Zainstalować dysk VHD, do którego chcesz wstawić konfiguracji przez wywołanie metody [Instalowanie wirtualnego dysku twardego](/powershell/module/hyper-v/mount-vhd) polecenia cmdlet. Przykład:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Na komputerze z uruchomionym PowerShell 5.0 lub nowszy, Zapisz konfigurację powyżej (**SampleIISInstall**) jako plik skryptu (ps1) programu PowerShell.

3. W konsoli programu PowerShell przejdź do folderu, w którym został zapisany plik .ps1.

4. Uruchom następujące polecenia programu PowerShell, aby skompilować pliku MOF (Aby dowiedzieć się, jak kompilowanie konfiguracji DSC, zobacz [konfiguracje DSC](configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Spowoduje to utworzenie `localhost.mof` plik w nowym folderze o nazwie `SampleIISInstall`.
   Zmień nazwę, a następnie przenieść ten plik do właściwego położenia wirtualnego dysku twardego jako `Pending.mof` przy użyciu [Przenieś element](https://technet.microsoft.comlibrary/hh849852.aspx) polecenia cmdlet. Przykład:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Odinstaluj wirtualny dysk twardy, wywołując [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) polecenia cmdlet. Przykład:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Tworzenie maszyny Wirtualnej przy użyciu dysku VHD, w którym zainstalowano dokument DSC MOF.

Po wstępnej rozruchu i instalacji systemu operacyjnego zostaną zainstalowane usługi IIS.
Można to sprawdzić przez wywołanie metody [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) polecenia cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Wstrzyknięcie DSC metaconfiguration do wirtualnego dysku twardego

Możesz również skonfigurować komputer w celu ściągania konfiguracji podczas wstępnej rozruchu przez iniekcję metaconfiguration (zobacz [Konfigurowanie lokalnego Configuration Manager (LCM)](metaConfig.md)) do wirtualnego dysku twardego jako jego `MetaConfig.mof` pliku.
Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiony na 2 (wartość domyślna), DSC zastosuje metaconfiguration definicją `MetaConfig.mof` do LCM, gdy komputer uruchamia się potrzeby po raz pierwszy.
Jeśli metaconfiguration Określa, że LCM należy ściągnąć konfiguracji z serwera ściągania, komputer będzie podejmować próby ściągania konfiguracji z tego serwera ściągania podczas początkowego rozruchu.
Aby uzyskać informacje o konfigurowaniu serwera ściągania DSC, zobacz [Konfigurowanie internetowego serwera ściągania DSC](pullServer.md).

W tym przykładzie użyjemy konfiguracji opisanych w poprzedniej sekcji (**SampleIISInstall**), a metaconfiguration następujące:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Aby wstawić dokument MOF metaconfiguration do wirtualnego dysku twardego

1. Zainstalować dysk VHD, do którego chcesz wstawić metaconfiguration przez wywołanie metody [Instalowanie wirtualnego dysku twardego](/powershell/module/hyper-v/mount-vhd) polecenia cmdlet. Przykład:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Konfigurowanie internetowego serwera ściągania DSC](pullServer.md)i Zapisz **SampleIISInistall** konfiguracji do odpowiedniego folderu.

3. Na komputerze z uruchomionym PowerShell 5.0 lub nowszy, Zapisz metaconfiguration powyżej (**PullClientBootstrap**) jako plik skryptu (ps1) programu PowerShell.

4. W konsoli programu PowerShell przejdź do folderu, w którym został zapisany plik .ps1.

5. Uruchom następujące polecenia programu PowerShell, aby skompilować dokument MOF metaconfiguration (Aby dowiedzieć się, jak kompilowanie konfiguracji DSC, zobacz [konfiguracje DSC](configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Spowoduje to utworzenie `localhost.meta.mof` plik w nowym folderze o nazwie `PullClientBootstrap`.
   Zmień nazwę, a następnie przenieść ten plik do właściwego położenia wirtualnego dysku twardego jako `MetaConfig.mof` przy użyciu [Przenieś element](https://technet.microsoft.comlibrary/hh849852.aspx) polecenia cmdlet.

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Odinstaluj wirtualny dysk twardy, wywołując [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) polecenia cmdlet. Przykład:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Tworzenie maszyny Wirtualnej przy użyciu dysku VHD, w którym zainstalowano dokument DSC MOF.

Po wstępnej rozruchu i instalacji systemu operacyjnego DSC będzie pobierać konfiguracji z serwera ściągania oraz zostaną zainstalowane usługi IIS.
Można to sprawdzić przez wywołanie metody [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) polecenia cmdlet.

## <a name="disable-dsc-at-boot-time"></a>Wyłącz DSC w czasie rozruchu

Domyślnie wartość `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled` klucza jest równa 2, co pozwala konfiguracji DSC do uruchomienia, jeśli komputer jest w stanie Oczekujące na zatwierdzenie lub bieżącego. Jeśli nie mają konfiguracji do uruchomienia podczas początkowego rozruchu, należy więc ustawić wartość tego klucza na 0:

1. Zainstalować dysk VHD, wywołując [Instalowanie wirtualnego dysku twardego](/powershell/module/hyper-v/mount-vhd) polecenia cmdlet. Przykład:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Ładowanie rejestru `HKLM\Software` podkluczy z wirtualnego dysku twardego, wywołując `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Przejdź do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*` przy użyciu dostawcy rejestru programu PowerShell.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
   ```

4. Zmień wartość właściwości `DSCAutomationHostEnabled` na 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Zwolnij rejestru, uruchamiając następujące polecenia:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Zobacz też

[Konfiguracje DSC](configurations.md)

[Klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[Konfigurowanie programu Local Configuration Manager (LCM)](metaConfig.md)

[Konfigurowanie internetowego serwera ściągania DSC](pullServer.md)
