---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086701"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="ea2eb-103">Obiekt ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="ea2eb-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="ea2eb-104">**ISEMenuItemCollection** obiektu jest kolekcją **ISEMenuItem** obiektów.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="ea2eb-105">Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="ea2eb-106">Na przykład **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** obiekt, który jest używany do dostosowywania **dodatek** menu w Windows PowerShell® zintegrowane Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="ea2eb-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="ea2eb-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="ea2eb-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="ea2eb-108">Dodaj\(DisplayName, akcja System.Management.Automation.ScriptBlock System.Windows.Input.KeyGesture skrótu ciągu \)</span><span class="sxs-lookup"><span data-stu-id="ea2eb-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="ea2eb-109">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ea2eb-110">Dodaje element menu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="ea2eb-111">**DisplayName** nazwę wyświetlaną w menu, które mają zostać dodane.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="ea2eb-112">**Akcja** **System.Management.Automation.ScriptBlock** obiekt, który określa akcję, która jest skojarzona z tego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="ea2eb-113">**Skrót** skrótu klawiaturowego dla akcji.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="ea2eb-114">**Zwraca** obiekt ISEMenuItem, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="ea2eb-115">Usuń zaznaczenie\(\)</span><span class="sxs-lookup"><span data-stu-id="ea2eb-115">Clear\(\)</span></span>

<span data-ttu-id="ea2eb-116">Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ea2eb-117">Usuwa wszystkie podmenu z elementu menu.</span><span class="sxs-lookup"><span data-stu-id="ea2eb-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="ea2eb-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea2eb-118">See Also</span></span>

- [<span data-ttu-id="ea2eb-119">Obiekt ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="ea2eb-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="ea2eb-120">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ea2eb-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ea2eb-121">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="ea2eb-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)