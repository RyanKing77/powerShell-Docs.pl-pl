---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Złożone zasobów — za pomocą konfiguracji DSC jako zasób"
ms.openlocfilehash: d889384c8d9c0746200ad424c6ab448a0e41d66c
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>Zasoby złożonego: jako zasób przy użyciu konfiguracji DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

W sytuacjach rzeczywistych konfiguracji może stać się długich i złożonych, wywołanie wielu różnych zasobów i ustawiania przeważająca wiele właściwości. Mogą pomóc w pokonywaniu tego złożoności, służy konfiguracji systemu Windows PowerShell Desired stan konfiguracji (DSC) jako zasób dla innych ustawień. Nazywamy to złożony zasobów. Zasób złożonego jest konfiguracji DSC, która przyjmuje parametry. Parametry konfiguracji działają jako właściwości zasobu. Konfiguracja jest zapisywana jako plik z **. schema.psm1** rozszerzenie i ma miejsce zarówno schematu MOF i zasobu skryptu w typowych zasobów DSC (Aby uzyskać więcej informacji o zasobach DSC, zobacz [systemu Windows Stan konfiguracji zasobów żądanego programu PowerShell](resources.md).

## <a name="creating-the-composite-resource"></a>Tworzenie złożonego zasobu

W naszym przykładzie tworzymy konfigurację, która wywołuje szereg istniejących zasobów, aby skonfigurować maszyn wirtualnych. Zamiast określania wartości, które można ustawić w blokach konfiguracji, konfiguracji przyjmuje kilka parametrów, które są następnie używane w blokach konfiguracji.

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

### <a name="saving-the-configuration-as-a-composite-resource"></a>Zapisywanie konfiguracji jako zasób złożone

Do korzystania z konfiguracji sparametryzowane jako zasób DSC, zapisać go w strukturze katalogów, takich jak z innych zasobów na podstawie MOF i nazywa je z **. schema.psm1** rozszerzenia. Na przykład możemy Nazwij plik **xVirtualMachine.schema.psm1**. Należy także utworzyć manifestu o nazwie **xVirtualMachine.psd1** zawiera następujący wiersz. Należy pamiętać, że jest to dodatkowe **MyDscResources.psd1**, manifestu modułu dla wszystkich zasobów w obszarze **MyDscResources** folderu.

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

Gdy wszystko będzie gotowe, powinien być następujący strukturę folderów.

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

Zasób jest teraz wykrywalny za pomocą polecenia cmdlet Get-DscResource i jego właściwości są wykrywalny, albo to polecenie cmdlet lub używając **klawisze Ctrl + spacja** funkcja automatycznego uzupełniania w środowisku Windows PowerShell ISE.

## <a name="using-the-composite-resource"></a>Przy użyciu złożonego zasobów

Następnie utworzyć konfigurację, która wywołuje złożonego zasobów. Ta konfiguracja wymaga xVirtualMachine złożonego zasobu do utworzenia maszyny wirtualnej, a następnie wywołuje **xComputer** zasobów, aby zmienić jego nazwę.

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
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

**PsDscRunAsCredential** właściwość może być używana w [konfiguracji DSC](configurations.md) bloku zasobów, aby określić, że zasób powinny być uruchamiane w określonym zestawie poświadczeń.
Aby uzyskać więcej informacji, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).

Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć automatycznego zmiennej `$PsDscContext`.

Na przykład następujący kod zapisać kontekstu użytkownika, na którym uruchomiono zasobu w strumieniu pełne dane wyjściowe:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>Zobacz też
### <a name="concepts"></a>Pojęcia
* [Pisanie niestandardowych zasobów DSC z MOF](authoringResourceMOF.md)
* [Wprowadzenie do konfiguracji żądanego stanu programu PowerShell systemu Windows](overview.md)

