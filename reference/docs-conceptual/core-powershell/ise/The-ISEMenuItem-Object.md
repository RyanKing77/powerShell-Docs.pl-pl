---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="9fd3d-103">Obiekt ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="9fd3d-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="9fd3d-104">**ISEMenuItem** obiekt jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="9fd3d-105">Wszystkie obiekty menu na **dodatki** menu są wystąpieniami klasy **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasy.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="9fd3d-106">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9fd3d-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="9fd3d-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9fd3d-107">DisplayName</span></span>
  <span data-ttu-id="9fd3d-108">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9fd3d-109">Właściwość tylko do odczytu, który pobiera nazwę wyświetlaną elementu menu.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="9fd3d-110">Akcja</span><span class="sxs-lookup"><span data-stu-id="9fd3d-110">Action</span></span>
  <span data-ttu-id="9fd3d-111">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9fd3d-112">Właściwość tylko do odczytu, która pobiera blok skryptu.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="9fd3d-113">Po kliknięciu elementu menu, wywołuje akcję.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="9fd3d-114">Skrót</span><span class="sxs-lookup"><span data-stu-id="9fd3d-114">Shortcut</span></span>
  <span data-ttu-id="9fd3d-115">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9fd3d-116">Właściwość tylko do odczytu, która pobiera systemu Windows wprowadź skrót klawiaturowy do elementu menu.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="9fd3d-117">Podmenu</span><span class="sxs-lookup"><span data-stu-id="9fd3d-117">Submenus</span></span>
  <span data-ttu-id="9fd3d-118">Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="9fd3d-119">Właściwość tylko do odczytu, która pobiera [listy podmenu](The-ISEMenuItemCollection-Object.md) elementu menu.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="9fd3d-120">Przykład skryptów</span><span class="sxs-lookup"><span data-stu-id="9fd3d-120">Scripting example</span></span>
 <span data-ttu-id="9fd3d-121">Aby lepiej zrozumieć użycie menu dodatków i jego właściwości skryptowe, zapoznaj się z artykułem poniższy przykład skryptów.</span><span class="sxs-lookup"><span data-stu-id="9fd3d-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="9fd3d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fd3d-122">See Also</span></span>
- [<span data-ttu-id="9fd3d-123">Obiekt ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="9fd3d-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="9fd3d-124">Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="9fd3d-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="9fd3d-125">Dotyczące modelu obiektów programu Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9fd3d-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="9fd3d-126">Hierarchia modelu obiektów ISE</span><span class="sxs-lookup"><span data-stu-id="9fd3d-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
