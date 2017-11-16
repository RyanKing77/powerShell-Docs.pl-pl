---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="d864c-103">Obiekt ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="d864c-103">The ISEAddOnToolCollection Object</span></span>
  <span data-ttu-id="d864c-104">**ISEAddOnToolCollection** obiektu jest kolekcją **ISEAddOnTool** obiektów.</span><span class="sxs-lookup"><span data-stu-id="d864c-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="d864c-105">Na przykład **$psISE.CurrentPowerShellTab.VerticalAddOnTools** obiektu.</span><span class="sxs-lookup"><span data-stu-id="d864c-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="d864c-106">Metody</span><span class="sxs-lookup"><span data-stu-id="d864c-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="d864c-107">Dodaj\( nazwę, ControlType, \[IsVisible\]\)</span><span class="sxs-lookup"><span data-stu-id="d864c-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>
  <span data-ttu-id="d864c-108">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d864c-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d864c-109">Dodaje nowe narzędzie dodatek do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d864c-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="d864c-110">Zwraca narzędzie nowo dodanego dodatek.</span><span class="sxs-lookup"><span data-stu-id="d864c-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="d864c-111">Przed uruchomieniem tego polecenia, należy zainstalować narzędzie dodatku na komputerze lokalnym i załadować zestawu.</span><span class="sxs-lookup"><span data-stu-id="d864c-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

 <span data-ttu-id="d864c-112">**Nazwa** — ciąg Określa nazwę wyświetlaną narzędzia dodatek, który jest dodawany do programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d864c-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

 <span data-ttu-id="d864c-113">**ControlType** — typ Określa formant, który zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="d864c-113">**ControlType** -Type Specifies the control that is added.</span></span>

 <span data-ttu-id="d864c-114">**\[IsVisible\]**  -opcjonalna wartość logiczna Jeśli równa **$true**, narzędzie dodatek jest od razu widoczne w okienku skojarzone narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d864c-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="d864c-115">Usuń\( elementu\)</span><span class="sxs-lookup"><span data-stu-id="d864c-115">Remove\( Item \)</span></span>
  <span data-ttu-id="d864c-116">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d864c-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d864c-117">Usuwa dodatek określonego narzędzia z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d864c-117">Removes the specified add-on tool from the collection.</span></span>

 <span data-ttu-id="d864c-118">**Element** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool określa obiekt, który ma zostać usunięty z programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d864c-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="d864c-119">SetSelectedPowerShellTab\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="d864c-119">SetSelectedPowerShellTab\( psTab \)</span></span>
  <span data-ttu-id="d864c-120">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d864c-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d864c-121">Karta wybiera programu PowerShell, który **psTab** określa parametr.</span><span class="sxs-lookup"><span data-stu-id="d864c-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="d864c-122">**psTab** -PowerShell Microsoft.PowerShell.Host.ISE.PowerShellTab kartę, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="d864c-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a><span data-ttu-id="d864c-123">Usuń\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="d864c-123">Remove\( psTab \)</span></span>
  <span data-ttu-id="d864c-124">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="d864c-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="d864c-125">Karta usuwa programu PowerShell, który **psTab** określa parametr.</span><span class="sxs-lookup"><span data-stu-id="d864c-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="d864c-126">**psTab** — karta Microsoft.PowerShell.Host.ISE.PowerShellTab programu PowerShell do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="d864c-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="d864c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d864c-127">See Also</span></span>
- [<span data-ttu-id="d864c-128">Obiekt PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="d864c-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="d864c-129">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="d864c-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="d864c-130">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d864c-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="d864c-131">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="d864c-131">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
