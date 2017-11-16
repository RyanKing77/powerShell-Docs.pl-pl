---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Konfigurowanie maszyn wirtualnych na początkowego rozruchu w górę przy użyciu usługi Konfiguracja DSC"
ms.openlocfilehash: a3592c50fa7f2232538fbec07129fac86c1d00b5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
>Dotyczy: Środowiska Windows PowerShell 5.0

>**Uwaga:** **DSCAutomationHostEnabled** klucz rejestru opisany w tym temacie nie jest dostępna w programie PowerShell 4.0.
Aby uzyskać informacje na temat konfigurowania nowych maszyn wirtualnych w początkowej up rozruchu w środowisku PowerShell w wersji 4.0, zobacz [chcesz automatycznie skonfigurować swój maszyny przy użyciu usługi Konfiguracja DSC w początkowego rozruchu w górę?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Konfigurowanie maszyn wirtualnych na początkowego rozruchu w górę przy użyciu usługi Konfiguracja DSC

## <a name="requirements"></a>Wymagania

Aby uruchomić te przykłady, będą potrzebne:

- Rozruchowy dysk VHD do pracy z. Możesz pobrać plik ISO z wersję ewaluacyjną programu Windows Server 2016 na   [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Instrukcje można znaleźć na temat tworzenia dysku VHD z obrazu ISO w [tworzenie rozruchowych wirtualnych dysków twardych](https://technet.microsoft.com/en-us/library/gg318049.aspx).
- Komputer hosta, który ma włączoną funkcją Hyper-V. Aby uzyskać informacje, zobacz [omówienie funkcji Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).

Przy użyciu usługi Konfiguracja DSC, można zautomatyzować instalację oprogramowania i konfiguracji na komputerze w początkowej rozruchu w górę.
W tym celu albo wstrzykiwania metakonfigurację lub dokumentu MOF konfiguracji do nośnika rozruchowego (np. dysk VHD), dzięki czemu są one uruchamiane podczas początkowego procesu rozruchu w górę.
To zachowanie jest określona przez [klucza rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucza rejestru w kluczu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.
Domyślnie wartość tego klucza jest 2, dzięki czemu DSC w czasie rozruchu.

Jeśli nie chcesz, aby DSC w czasie rozruchu, ustaw wartość [klucza rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) klucza rejestru na 0.

- Wstaw dokument MOF konfiguracji do dysku VHD
- Wstaw metakonfigurację DSC do dysku VHD
- Wyłącz usługi Konfiguracja DSC w czasie rozruchu

>**Uwaga:** można wprowadzić obu `Pending.mof` i `MetaConfig.mof` do komputera, w tym samym czasie.
Jeśli oba pliki są obecne, ustawienia określone w `MetaConfig.mof` pierwszeństwo.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Wstaw dokument MOF konfiguracji do dysku VHD

Wprowadzenie konfiguracji w początkowej rozruchu w górę, można wstrzyknąć dokumentu MOF skompilowanych konfiguracji do wirtualnego dysku twardego jako jego `Pending.mof` pliku.
Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiona na 2 (wartość domyślna), DSC zostaną zastosowane konfiguracji zdefiniowanej `Pending.mof` gdy komputer jest uruchamiany dla po raz pierwszy.

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Aby wstawić dokument MOF konfiguracji na dysku VHD

1. Zainstalowanie dysku VHD, do którego chcesz wstrzyknąć konfiguracji przez wywołanie metody [Instalowanie wirtualnego dysku twardego](https://technet.microsoft.com/library/hh848551.aspx) polecenia cmdlet. Przykład:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. Na komputerze z uruchomionym programu PowerShell w wersji 5.0 lub nowszy, Zapisz powyższej konfiguracji (**SampleIISInstall**) jako pliku skryptu (ps1) programu PowerShell.

3. W konsoli programu PowerShell przejdź do folderu, w której zapisano plik .ps1.

4. Uruchom następujące polecenia programu PowerShell, aby skompilować pliku MOF (informacje o kompilacji konfiguracji DSC znajdują się w temacie [konfiguracji DSC](configurations.md):

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. Spowoduje to utworzenie `localhost.mof` plik w nowym folderze o nazwie `SampleIISInstall`.
Zmień nazwę i przenieść ten plik do właściwego położenia na wirtualny dysk twardy jako `Pending.mof` za pomocą [Przenieś element](https://technet.microsoft.comlibrary/hh849852.aspx) polecenia cmdlet. Przykład:

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\Sytem32\Configuration\Pending.mof
    ```
6. Odinstalować dysku VHD, wywołując [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) polecenia cmdlet. Przykład:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. Utwórz maszynę Wirtualną przy użyciu dysku VHD, w którym zainstalowano pliku MOF usługi Konfiguracja DSC. Po początkowe up rozruchu i instalacji systemu operacyjnego zostaną zainstalowane usługi IIS.
Można to sprawdzić, wywołując [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) polecenia cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Wstaw metakonfigurację DSC do dysku VHD

Można również skonfigurować komputer w celu ściągania konfiguracji na początkowe up rozruchu przez wstrzykiwanie metakonfigurację (zobacz [Konfigurowanie lokalnego Menedżera konfiguracji (LCM)](metaConfig.md)) do wirtualnego dysku twardego jako jego `MetaConfig.mof` pliku.
Jeśli **DSCAutomationHostEnabled** klucz rejestru jest ustawiona na 2 (wartość domyślna), DSC zostaną zastosowane metakonfigurację zdefiniowane przez `MetaConfig.mof` do LCM, gdy komputer jest uruchamiany dla po raz pierwszy.
Jeśli metakonfigurację Określa, że LCM powinien pobierać konfiguracji z serwera ściągania, komputer podejmie próbę ściągania konfiguracji z tego serwera ściągania w początkowej rozruchu w górę.
Aby uzyskać informacje dotyczące konfigurowania serwera ściągania usługi Konfiguracja DSC, zobacz [ustawienie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md).

W tym przykładzie używamy konfiguracji opisanych w poprzedniej sekcji (**SampleIISInstall**), a metakonfigurację następujące:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Można wstawić dokument MOF metakonfigurację na wirtualny dysk twardy

1. Zainstalowanie dysku VHD, do którego chcesz wstrzyknąć metakonfigurację przez wywołanie metody [Instalowanie wirtualnego dysku twardego](https://technet.microsoft.com/library/hh848551.aspx) polecenia cmdlet. Przykład:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [Konfigurowanie serwera ściągania usługi Konfiguracja DSC](pullServer.md)i Zapisz **SampleIISInistall** konfiguracji do odpowiedniego folderu.

3. Na komputerze z uruchomionym programu PowerShell w wersji 5.0 lub później, Zapisz powyżej metakonfigurację (**PullClientBootstrap**) jako pliku skryptu (ps1) programu PowerShell.

4. W konsoli programu PowerShell przejdź do folderu, w której zapisano plik .ps1.

5. Uruchom następujące polecenia programu PowerShell, aby skompilować pliku MOF metakonfigurację (informacje o kompilacji konfiguracji DSC znajdują się w temacie [konfiguracji DSC](configurations.md):

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. Spowoduje to utworzenie `localhost.meta.mof` plik w nowym folderze o nazwie `PullClientBootstrap`.
Zmień nazwę i przenieść ten plik do właściwego położenia na wirtualny dysk twardy jako `MetaConfig.mof` za pomocą [Przenieś element](https://technet.microsoft.comlibrary/hh849852.aspx) polecenia cmdlet.

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. Odinstalować dysku VHD, wywołując [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) polecenia cmdlet. Przykład:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. Utwórz maszynę Wirtualną przy użyciu dysku VHD, w którym zainstalowano pliku MOF usługi Konfiguracja DSC.
Po początkowe up rozruchu i instalacji systemu operacyjnego DSC będzie pobierać konfiguracji z serwera ściągania i będzie można zainstalować usług IIS.
Można to sprawdzić, wywołując [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) polecenia cmdlet.

## <a name="disable-dsc-at-boot-time"></a>Wyłącz usługi Konfiguracja DSC w czasie rozruchu

Domyślnie wartość **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** klucza wynosi 2, dzięki czemu konfiguracji DSC do uruchomienia, jeśli komputer znajduje się w oczekujące lub bieżącego Stan. Jeśli nie chcesz, aby konfiguracji, aby były uruchamiane po początkowej rozruchu w górę, należy więc ustaw wartość tego klucza na 0:

1. Zainstalować dysk VHD, wywołując [Instalowanie wirtualnego dysku twardego](https://technet.microsoft.com/library/hh848551.aspx) polecenia cmdlet. Przykład:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. Załadować rejestru **kluczu HKLM\Software** podkluczy z wirtualnego dysku twardego, wywołując `reg load`.

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  przy użyciu dostawcy rejestru programu PowerShell.

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. Zmień wartość `DSCAutomationHostEnabled` na 0.

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. Zwolnienia rejestru, uruchamiając następujące polecenia:

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a>Zobacz też

- [Konfiguracji DSC](configurations.md)
- [Klucz rejestru DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)
- [Konfigurowanie lokalnego programu Configuration Manager (LCM)](metaConfig.md)
- [Konfigurowanie serwera ściągania usługi Konfiguracja DSC sieci web](pullServer.md)

