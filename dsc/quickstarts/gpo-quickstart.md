---
ms.date: 07/09/2019
keywords: DSC, obiekt zasad grupy, programu powershell, konfiguracji, ustawienia
title: Przewodnik Szybki Start — zasady grupy konwersji do DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67785138"
---
> <span data-ttu-id="1494f-103">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1494f-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="1494f-104">Szybki Start: Zasady grupy konwersji do DSC</span><span class="sxs-lookup"><span data-stu-id="1494f-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="1494f-105">Konfiguracja DSC można wygenerować z linii bazowej, zasady grupy lub usługi Azure Security Center.</span><span class="sxs-lookup"><span data-stu-id="1494f-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="1494f-106">[BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) moduł zawiera następujące polecenia do wykonywania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="1494f-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="1494f-107">`ConvertFrom-GPO` — Przechowywane jako pliki grupy konwertuje zasad.</span><span class="sxs-lookup"><span data-stu-id="1494f-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="1494f-108">Można również określić katalogu zawierającego wiele zasad, które mają zostać połączone w jedną konfigurację.</span><span class="sxs-lookup"><span data-stu-id="1494f-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="1494f-109">Aby wyeksportować zasady grupy w danym środowisku, należy użyć [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) polecenia cmdlet, lub postępować zgodnie z instrukcjami wyświetlanymi w [Wyeksportuj obiekt zasad grupy do pliku](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="1494f-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="1494f-110">`ConvertFrom-SCM` — Konwertuje odniesienia Menedżera zgodności zabezpieczeń, przechowywane jako `.xml` plików.</span><span class="sxs-lookup"><span data-stu-id="1494f-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="1494f-111">`ConvertFrom-ASC` — Centrum zabezpieczeń Azure konwertuje odniesienia, przechowywane jako `.json` plików.</span><span class="sxs-lookup"><span data-stu-id="1494f-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="1494f-112">`Merge-GPOs` — Grupy konwertuje zasady są stosowane do komputera docelowego.</span><span class="sxs-lookup"><span data-stu-id="1494f-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="1494f-113">Polecenia cmdlet wymienione powyżej konwertowanie linię bazową na DSC `.mof` pliku.</span><span class="sxs-lookup"><span data-stu-id="1494f-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="1494f-114">Możesz również dane wyjściowe skryptu konfiguracji (`.ps1`), który można edytować i ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="1494f-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="1494f-115">Polecenia cmdlet wykryć błędy kompilacji dla brakujących zasobów lub zasobu zduplikowanych bloków.</span><span class="sxs-lookup"><span data-stu-id="1494f-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="1494f-116">Bloki zasobów, które mogłoby spowodować błędy kompilacji są oznaczone jako komentarz.</span><span class="sxs-lookup"><span data-stu-id="1494f-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="1494f-117">Poniższy przykład konwertuje [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) do skryptu konfiguracji DSC (`.ps1`) i `.mof` pliku.</span><span class="sxs-lookup"><span data-stu-id="1494f-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="1494f-118">Po uruchomieniu polecenia, zostaną wyświetlone dwa pliki w domyślnym katalogu "Wyjście" utworzonych w ramach Twojej bieżącej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="1494f-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="1494f-119">Każdy węzeł zarządzanych muszą także następujące dwa moduły:</span><span class="sxs-lookup"><span data-stu-id="1494f-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="1494f-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="1494f-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="1494f-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="1494f-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="1494f-122">**BaselineManagement** jest rozwiązanie opracowane przez społeczność, aby dla członków społeczności pochodzą z maintainers projektu, a nie od firmy Microsoft mogą szybciej odnajdywać obsługi DSC.</span><span class="sxs-lookup"><span data-stu-id="1494f-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="1494f-123">Można otworzyć nowego problemu dla **BaselineManagement** na [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="1494f-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1494f-124">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1494f-124">Next steps</span></span>

- <span data-ttu-id="1494f-125">Przekazywanie skryptu konfiguracji do usługi Azure Automation stan konfiguracji, zobacz [wprowadzenie](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="1494f-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="1494f-126">Dodaj **SecurityPolicyDSC** i **AuditPolicyDSC** modułów, aby Twoje [konta usługi Automation](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="1494f-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="1494f-127">Konfiguracje DSC i zasoby w [galerii programu PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="1494f-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
