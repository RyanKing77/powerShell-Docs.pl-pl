---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685564"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="cff91-103">Obiekt ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="cff91-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="cff91-104">**ISEAddOnToolCollection** obiektu jest kolekcją **ISEAddOnTool** obiektów.</span><span class="sxs-lookup"><span data-stu-id="cff91-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="cff91-105">Na przykład **$psISE.CurrentPowerShellTab.VerticalAddOnTools** obiektu.</span><span class="sxs-lookup"><span data-stu-id="cff91-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="cff91-106">Metody</span><span class="sxs-lookup"><span data-stu-id="cff91-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="cff91-107">Dodaj\( nazwę, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="cff91-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="cff91-108">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="cff91-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cff91-109">Dodaje nowe narzędzie dodatek do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cff91-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="cff91-110">Zwraca narzędzie nowo dodanych dodatku.</span><span class="sxs-lookup"><span data-stu-id="cff91-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="cff91-111">Przed uruchomieniem tego polecenia, należy zainstalować narzędzie dodatku na komputerze lokalnym i załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="cff91-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="cff91-112">**Nazwa** — ciąg Określa nazwę wyświetlaną narzędzia dodatek, który zostanie dodany do programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cff91-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="cff91-113">**ControlType** — typ Określa formant, który zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="cff91-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="cff91-114">**\[IsVisible\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, narzędzie dodatek jest natychmiast widoczne w okienku narzędzi skojarzone.</span><span class="sxs-lookup"><span data-stu-id="cff91-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="cff91-115">Usuń\( elementu \)</span><span class="sxs-lookup"><span data-stu-id="cff91-115">Remove\( Item \)</span></span>

<span data-ttu-id="cff91-116">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="cff91-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cff91-117">Usuwa narzędzie określonego dodatku z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cff91-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="cff91-118">**Element** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool określa obiekt, który ma zostać usunięty z programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cff91-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="cff91-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="cff91-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="cff91-120">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="cff91-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cff91-121">Karty programu PowerShell wybiera **psTab** określa parametr.</span><span class="sxs-lookup"><span data-stu-id="cff91-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="cff91-122">**psTab** -kartę Microsoft.PowerShell.Host.ISE.PowerShellTab programu PowerShell, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="cff91-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="cff91-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="cff91-123">Remove\( psTab \)</span></span>

<span data-ttu-id="cff91-124">Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="cff91-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cff91-125">Usuwa programu PowerShell karty **psTab** określa parametr.</span><span class="sxs-lookup"><span data-stu-id="cff91-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="cff91-126">**psTab** — karta Microsoft.PowerShell.Host.ISE.PowerShellTab programu PowerShell do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="cff91-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="cff91-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cff91-127">See Also</span></span>

- [<span data-ttu-id="cff91-128">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="cff91-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="cff91-129">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cff91-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cff91-130">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="cff91-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)