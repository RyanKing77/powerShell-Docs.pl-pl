---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405531"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="af448-103">Obiekt ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="af448-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="af448-104">**ISEMenuItem** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="af448-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="af448-105">Wszystkie obiekty menu na **dodatki** menu są wystąpieniami **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasy.</span><span class="sxs-lookup"><span data-stu-id="af448-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="af448-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="af448-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="af448-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af448-107">DisplayName</span></span>

<span data-ttu-id="af448-108">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="af448-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="af448-109">Właściwość tylko do odczytu, który pobiera nazwę wyświetlaną elementu menu.</span><span class="sxs-lookup"><span data-stu-id="af448-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="af448-110">Akcja</span><span class="sxs-lookup"><span data-stu-id="af448-110">Action</span></span>

<span data-ttu-id="af448-111">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="af448-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="af448-112">Właściwość tylko do odczytu, która bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="af448-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="af448-113">Wywołuje akcję, po kliknięciu elementu menu.</span><span class="sxs-lookup"><span data-stu-id="af448-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="af448-114">Skrót</span><span class="sxs-lookup"><span data-stu-id="af448-114">Shortcut</span></span>

<span data-ttu-id="af448-115">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="af448-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="af448-116">Właściwość tylko do odczytu, która pobiera Windows wprowadź skrót klawiaturowy dla tego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="af448-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="af448-117">Podmenu</span><span class="sxs-lookup"><span data-stu-id="af448-117">Submenus</span></span>

<span data-ttu-id="af448-118">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="af448-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="af448-119">Właściwość tylko do odczytu, która pobiera [listę podmenu](The-ISEMenuItemCollection-Object.md) elementu menu.</span><span class="sxs-lookup"><span data-stu-id="af448-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="af448-120">Przykład skryptu</span><span class="sxs-lookup"><span data-stu-id="af448-120">Scripting example</span></span>

<span data-ttu-id="af448-121">Aby lepiej zrozumieć użycie menu dodatki i jego właściwości za pomocą skryptów, zapoznaj się z artykułem poniższy przykład skryptów.</span><span class="sxs-lookup"><span data-stu-id="af448-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="af448-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af448-122">See Also</span></span>

- [<span data-ttu-id="af448-123">Obiekt ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="af448-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="af448-124">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="af448-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="af448-125">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="af448-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)