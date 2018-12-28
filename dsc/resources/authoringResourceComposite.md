---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasoby złożone — przy użyciu konfiguracji DSC jako zasób
ms.openlocfilehash: 2823d05e0c8feb2933ca691f9ab5149ace2f7ee3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404735"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Zasoby złożone: Przy użyciu konfiguracji DSC jako zasób

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

W rzeczywistych warunkach konfiguracji może stać się długie i złożone, wywołanie wiele różnych zasobów i ustawiania ogromną liczbę właściwości. Do rozwiązywania tę złożoność, można użyć konfiguracji Windows PowerShell Desired State Configuration (DSC) jako zasób w przypadku innych konfiguracji. Nazywamy to złożony zasobów. Zasób złożonego jest konfiguracji DSC, która przyjmuje parametry. Parametry konfiguracji działają jako właściwości zasobu. Konfiguracja zostanie zapisany jako plik o **. schema.psm1** rozszerzenie i zajmuje miejsce schematu pliku MOF i zasobu skryptu w typowych zasobów DSC (Aby uzyskać więcej informacji na temat zasobów DSC, zobacz [Windows Program PowerShell Desired State Configuration zasobów](resources.md).

## <a name="creating-the-composite-resource"></a>Tworzenie złożonego zasobu

W tym przykładzie utworzymy konfiguracji, który wywołuje szereg istniejących zasobów, aby skonfigurować maszyny wirtualne. Zamiast określania wartości, które mają zostać ustawione w blokach konfiguracji, konfiguracji ma liczbę parametrów, które są następnie używane w blokach konfiguracji.

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a>Zapisywanie konfiguracji jako zasoby złożone

Aby użyć sparametryzowanych konfiguracji jako zasób DSC, zapisz go w strukturze katalogów, podobnie jak w przypadku innych zasobów na podstawie pliku MOF i nadaj mu za pomocą **. schema.psm1** rozszerzenia. W tym przykładzie użyjemy nazwy pliku **xVirtualMachine.schema.psm1**. Trzeba będzie również tworzenie manifestu o nazwie **xVirtualMachine.psd1** zawiera następujący wiersz. Należy zauważyć, że jest to uzupełnienie **MyDscResources.psd1**, manifestu modułu dla wszystkich zasobów w ramach **MyDscResources** folderu.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Gdy wszystko będzie gotowe, powinna być następująca strukturę folderów.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Zasób jest teraz wykrywalny za pomocą polecenia cmdlet Get-DscResource i jego właściwości są wykrywalni, albo że danych wyjściowych polecenia cmdlet lub za pomocą **Ctrl + spacja** automatycznego uzupełniania w środowisku Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Przy użyciu złożonego zasobu

Następnie możemy utworzyć konfigurację, która wywołuje złożonego zasobu. Ta konfiguracja wywołuje xVirtualMachine złożonego zasobu do utworzenia maszyny wirtualnej, a następnie wywołuje **xComputer** zasobów, aby zmienić jego nazwę.

```powershell

configuration RenameVM
{

    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a>Obsługa PsDscRunAsCredential

>**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.

**PsDscRunAsCredential** właściwości mogą być używane w [konfiguracje DSC](../configurations/configurations.md) bloku zasobów, aby określić, że zasób powinien być wykonywany w ramach określonego zestawu poświadczeń.
Aby uzyskać więcej informacji, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](../configurations/runAsUser.md).

Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć zmiennej automatyczne `$PsDscContext`.

Na przykład poniższy kod napisać kontekstu użytkownika, pod którym jest uruchamiany zasób w strumieniu pełne dane wyjściowe:

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zobacz też
### <a name="concepts"></a>Pojęcia
* [Pisanie zasobu DSC niestandardowych z pliku MOF](authoringResourceMOF.md)
* [Rozpoczynanie pracy z usługą Windows PowerShell Desired State Configuration](../overview/overview.md)