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
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="78acb-103">Zasoby złożonego: jako zasób przy użyciu konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="78acb-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="78acb-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="78acb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="78acb-105">W sytuacjach rzeczywistych konfiguracji może stać się długich i złożonych, wywołanie wielu różnych zasobów i ustawiania przeważająca wiele właściwości.</span><span class="sxs-lookup"><span data-stu-id="78acb-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="78acb-106">Mogą pomóc w pokonywaniu tego złożoności, służy konfiguracji systemu Windows PowerShell Desired stan konfiguracji (DSC) jako zasób dla innych ustawień.</span><span class="sxs-lookup"><span data-stu-id="78acb-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="78acb-107">Nazywamy to złożony zasobów.</span><span class="sxs-lookup"><span data-stu-id="78acb-107">We call this a composite resource.</span></span> <span data-ttu-id="78acb-108">Zasób złożonego jest konfiguracji DSC, która przyjmuje parametry.</span><span class="sxs-lookup"><span data-stu-id="78acb-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="78acb-109">Parametry konfiguracji działają jako właściwości zasobu.</span><span class="sxs-lookup"><span data-stu-id="78acb-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="78acb-110">Konfiguracja jest zapisywana jako plik z **. schema.psm1** rozszerzenie i ma miejsce zarówno schematu MOF i zasobu skryptu w typowych zasobów DSC (Aby uzyskać więcej informacji o zasobach DSC, zobacz [systemu Windows Stan konfiguracji zasobów żądanego programu PowerShell](resources.md).</span><span class="sxs-lookup"><span data-stu-id="78acb-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="78acb-111">Tworzenie złożonego zasobu</span><span class="sxs-lookup"><span data-stu-id="78acb-111">Creating the composite resource</span></span>

<span data-ttu-id="78acb-112">W naszym przykładzie tworzymy konfigurację, która wywołuje szereg istniejących zasobów, aby skonfigurować maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="78acb-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="78acb-113">Zamiast określania wartości, które można ustawić w blokach konfiguracji, konfiguracji przyjmuje kilka parametrów, które są następnie używane w blokach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="78acb-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="78acb-114">Zapisywanie konfiguracji jako zasób złożone</span><span class="sxs-lookup"><span data-stu-id="78acb-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="78acb-115">Do korzystania z konfiguracji sparametryzowane jako zasób DSC, zapisać go w strukturze katalogów, takich jak z innych zasobów na podstawie MOF i nazywa je z **. schema.psm1** rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="78acb-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="78acb-116">Na przykład możemy Nazwij plik **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="78acb-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="78acb-117">Należy także utworzyć manifestu o nazwie **xVirtualMachine.psd1** zawiera następujący wiersz.</span><span class="sxs-lookup"><span data-stu-id="78acb-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="78acb-118">Należy pamiętać, że jest to dodatkowe **MyDscResources.psd1**, manifestu modułu dla wszystkich zasobów w obszarze **MyDscResources** folderu.</span><span class="sxs-lookup"><span data-stu-id="78acb-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="78acb-119">Gdy wszystko będzie gotowe, powinien być następujący strukturę folderów.</span><span class="sxs-lookup"><span data-stu-id="78acb-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="78acb-120">Zasób jest teraz wykrywalny za pomocą polecenia cmdlet Get-DscResource i jego właściwości są wykrywalny, albo to polecenie cmdlet lub używając **klawisze Ctrl + spacja** funkcja automatycznego uzupełniania w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="78acb-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="78acb-121">Przy użyciu złożonego zasobów</span><span class="sxs-lookup"><span data-stu-id="78acb-121">Using the composite resource</span></span>

<span data-ttu-id="78acb-122">Następnie utworzyć konfigurację, która wywołuje złożonego zasobów.</span><span class="sxs-lookup"><span data-stu-id="78acb-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="78acb-123">Ta konfiguracja wymaga xVirtualMachine złożonego zasobu do utworzenia maszyny wirtualnej, a następnie wywołuje **xComputer** zasobów, aby zmienić jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="78acb-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="78acb-124">Obsługa PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="78acb-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="78acb-125">**Uwaga:** **PsDscRunAsCredential** jest obsługiwana w programie PowerShell 5.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="78acb-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="78acb-126">**PsDscRunAsCredential** właściwość może być używana w [konfiguracji DSC](configurations.md) bloku zasobów, aby określić, że zasób powinny być uruchamiane w określonym zestawie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="78acb-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="78acb-127">Aby uzyskać więcej informacji, zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="78acb-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="78acb-128">Aby uzyskać dostęp z kontekstu użytkownika, w ramach zasobów niestandardowych, można użyć automatycznego zmiennej `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="78acb-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="78acb-129">Na przykład następujący kod zapisać kontekstu użytkownika, na którym uruchomiono zasobu w strumieniu pełne dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="78acb-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="78acb-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78acb-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="78acb-131">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="78acb-131">Concepts</span></span>
* [<span data-ttu-id="78acb-132">Pisanie niestandardowych zasobów DSC z MOF</span><span class="sxs-lookup"><span data-stu-id="78acb-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="78acb-133">Wprowadzenie do konfiguracji żądanego stanu programu PowerShell systemu Windows</span><span class="sxs-lookup"><span data-stu-id="78acb-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)

