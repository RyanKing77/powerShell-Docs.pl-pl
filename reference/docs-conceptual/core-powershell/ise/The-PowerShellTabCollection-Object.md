---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="d972a-103">Obiekt PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="d972a-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="d972a-104">**PowerShellTab** obiektu kolekcji jest kolekcją **PowerShellTab** obiektów.</span><span class="sxs-lookup"><span data-stu-id="d972a-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="d972a-105">Każdy **PowerShellTab** obiektu działa jako oddzielne środowiska.</span><span class="sxs-lookup"><span data-stu-id="d972a-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="d972a-106">To wystąpienie klasy Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="d972a-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="d972a-107">Na przykład **$psISE.PowerShellTabs** obiektu.</span><span class="sxs-lookup"><span data-stu-id="d972a-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="d972a-108">Metody</span><span class="sxs-lookup"><span data-stu-id="d972a-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="d972a-109">Dodaj\(\)</span><span class="sxs-lookup"><span data-stu-id="d972a-109">Add\(\)</span></span>
  <span data-ttu-id="d972a-110">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="d972a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="d972a-111">Dodaje nową kartę programu PowerShell do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d972a-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="d972a-112">Zwraca nowo dodanego kartę.</span><span class="sxs-lookup"><span data-stu-id="d972a-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d972a-113">Usuń\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d972a-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="d972a-114">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="d972a-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="d972a-115">Usuwa określoną przez kartę **psTab** parametru.</span><span class="sxs-lookup"><span data-stu-id="d972a-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="d972a-116">**psTab** kartę programu PowerShell do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="d972a-116">**psTab** The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d972a-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d972a-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="d972a-118">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="d972a-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="d972a-119">Wybiera karcie programu PowerShell, która jest określona przez **psTab** parametr, aby stał się aktywne kartę programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d972a-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="d972a-120">**psTab** kartę programu PowerShell, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="d972a-120">**psTab** The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="d972a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d972a-121">See Also</span></span>
- [<span data-ttu-id="d972a-122">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="d972a-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="d972a-123">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="d972a-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="d972a-124">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d972a-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="d972a-125">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="d972a-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
