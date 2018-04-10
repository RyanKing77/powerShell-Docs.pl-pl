---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="e17ad-103">Obiekt ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="e17ad-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="e17ad-104">**ISEMenuItem** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="e17ad-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="e17ad-105">Wszystkie obiekty menu na **dodatki** menu są wystąpieniami klasy **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasy.</span><span class="sxs-lookup"><span data-stu-id="e17ad-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="e17ad-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e17ad-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="e17ad-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e17ad-107">DisplayName</span></span>

<span data-ttu-id="e17ad-108">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="e17ad-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e17ad-109">Właściwość tylko do odczytu, który pobiera nazwę wyświetlaną elementu menu.</span><span class="sxs-lookup"><span data-stu-id="e17ad-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="e17ad-110">Akcja</span><span class="sxs-lookup"><span data-stu-id="e17ad-110">Action</span></span>

<span data-ttu-id="e17ad-111">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="e17ad-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e17ad-112">Właściwość tylko do odczytu, która pobiera blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="e17ad-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="e17ad-113">Po kliknięciu elementu menu, wywołuje akcję.</span><span class="sxs-lookup"><span data-stu-id="e17ad-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="e17ad-114">Skrót</span><span class="sxs-lookup"><span data-stu-id="e17ad-114">Shortcut</span></span>

<span data-ttu-id="e17ad-115">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="e17ad-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e17ad-116">Właściwość tylko do odczytu, która pobiera systemu Windows wprowadź skrót klawiaturowy do elementu menu.</span><span class="sxs-lookup"><span data-stu-id="e17ad-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="e17ad-117">Podmenu</span><span class="sxs-lookup"><span data-stu-id="e17ad-117">Submenus</span></span>

<span data-ttu-id="e17ad-118">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="e17ad-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e17ad-119">Właściwość tylko do odczytu, która pobiera [listy podmenu](The-ISEMenuItemCollection-Object.md) elementu menu.</span><span class="sxs-lookup"><span data-stu-id="e17ad-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="e17ad-120">Przykład skryptów</span><span class="sxs-lookup"><span data-stu-id="e17ad-120">Scripting example</span></span>

<span data-ttu-id="e17ad-121">Aby lepiej zrozumieć użycie menu dodatków i jego właściwości skryptowe, zapoznaj się z artykułem poniższy przykład skryptów.</span><span class="sxs-lookup"><span data-stu-id="e17ad-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e17ad-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e17ad-122">See Also</span></span>

- [<span data-ttu-id="e17ad-123">Obiekt ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="e17ad-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="e17ad-124">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="e17ad-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e17ad-125">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="e17ad-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)