---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405396"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="7c350-103">Obiekt PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="7c350-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="7c350-104">**PowerShellTab** obiekt kolekcji jest kolekcją **PowerShellTab** obiektów.</span><span class="sxs-lookup"><span data-stu-id="7c350-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="7c350-105">Każdy **PowerShellTab** obiektu działa jako oddzielne środowiska.</span><span class="sxs-lookup"><span data-stu-id="7c350-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="7c350-106">Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="7c350-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="7c350-107">Na przykład **$psISE.PowerShellTabs** obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c350-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="7c350-108">Metody</span><span class="sxs-lookup"><span data-stu-id="7c350-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="7c350-109">Dodaj\(\)</span><span class="sxs-lookup"><span data-stu-id="7c350-109">Add\(\)</span></span>

<span data-ttu-id="7c350-110">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="7c350-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7c350-111">Dodaje nową kartę programu PowerShell do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7c350-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="7c350-112">Zwraca nowo dodanych kartę.</span><span class="sxs-lookup"><span data-stu-id="7c350-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="7c350-113">Usuń\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="7c350-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="7c350-114">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="7c350-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7c350-115">Usuwa kartę, która jest określona przez **psTab** parametru.</span><span class="sxs-lookup"><span data-stu-id="7c350-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="7c350-116">**psTab** kartę programu PowerShell do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="7c350-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="7c350-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="7c350-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="7c350-118">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="7c350-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7c350-119">Wybiera kartę programu PowerShell, który jest określony przez **psTab** parametr, aby utworzyć obecnie aktywną kartę programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c350-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="7c350-120">**psTab** kartę programu PowerShell, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="7c350-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="7c350-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c350-121">See Also</span></span>

- [<span data-ttu-id="7c350-122">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="7c350-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="7c350-123">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="7c350-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7c350-124">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="7c350-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)