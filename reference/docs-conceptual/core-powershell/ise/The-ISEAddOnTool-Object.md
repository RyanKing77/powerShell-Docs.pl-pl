---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954810"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="86cf4-103">Obiekt ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="86cf4-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="86cf4-104">**ISEAddonTool** obiekt reprezentuje narzędzia zainstalowany dodatek, który zapewnia dodatkowe funkcje toWindows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="86cf4-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="86cf4-105">Na przykład **polecenia** narzędzie, które można wyświetlić, klikając **widoku**, następnie **Pokaż dodatkowe polecenia**.</span><span class="sxs-lookup"><span data-stu-id="86cf4-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="86cf4-106">Narzędzie to jest następnie dostępne dla Ciebie przez różne dostępne operacje **ISEAddOnTool** obiektów.</span><span class="sxs-lookup"><span data-stu-id="86cf4-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="86cf4-107">Dodatkowe narzędzia może być skojarzony z okienka pionowy lub poziomy okienka.</span><span class="sxs-lookup"><span data-stu-id="86cf4-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="86cf4-108">Okienko pionowe jest zadokowany do prawej krawędzi programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="86cf4-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="86cf4-109">Okienko poziome jest zadokowana do dolnej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="86cf4-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="86cf4-110">Każda karta programu PowerShell w środowisku Windows PowerShell ISE może mieć własny zestaw dodatków zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="86cf4-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="86cf4-111">Zobacz [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) i [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) można uzyskać dostępu do kolekcji dostępne narzędzia do aktualnie wybrana karta lub takie same właściwości na dowolnym **PowerShellTab** obiekty w [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) obiektu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86cf4-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="86cf4-112">Metody</span><span class="sxs-lookup"><span data-stu-id="86cf4-112">Methods</span></span>

<span data-ttu-id="86cf4-113">Dla obiektów tej klasy nie ma dostępnych żadnych metod programu PowerShell ISE właściwe dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="86cf4-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="86cf4-114">Właściwości</span><span class="sxs-lookup"><span data-stu-id="86cf4-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="86cf4-115">Kontrola</span><span class="sxs-lookup"><span data-stu-id="86cf4-115">Control</span></span>

<span data-ttu-id="86cf4-116">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="86cf4-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="86cf4-117">**Kontroli** właściwość zapewnia dostęp do odczytu do wielu szczegółów poleceń narzędzia dodatku.</span><span class="sxs-lookup"><span data-stu-id="86cf4-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a><span data-ttu-id="86cf4-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="86cf4-118">IsVisible</span></span>

<span data-ttu-id="86cf4-119">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="86cf4-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="86cf4-120">Właściwości typu Boolean wskazującą, czy narzędzie dodatek jest widoczne w swojej przypisanej okienka.</span><span class="sxs-lookup"><span data-stu-id="86cf4-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="86cf4-121">Jeśli jest on widoczny, można ustawić **IsVisible** właściwości **$false** można ukryć narzędzie lub ustawić **IsVisible** właściwości **$true** Aby Narzędzie dodatek widoczne na karcie środowiska PowerShell. Należy pamiętać, że po narzędzia dodatek jest ukryty, nie jest już dostępny za pośrednictwem **CurrentVisibleHorizontalTool** lub **CurrentVisibleVerticalTool** obiekty i dlatego nie może być widoczne za pomocą Ta właściwość dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="86cf4-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="86cf4-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="86cf4-122">Name</span></span>

<span data-ttu-id="86cf4-123">Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="86cf4-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="86cf4-124">Właściwość tylko do odczytu, która pobiera nazwę narzędzia dodatku.</span><span class="sxs-lookup"><span data-stu-id="86cf4-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="86cf4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86cf4-125">See Also</span></span>

- [<span data-ttu-id="86cf4-126">Obiekt ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="86cf4-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="86cf4-127">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="86cf4-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="86cf4-128">Hierarchia modeli obiektów środowiska ISE</span><span class="sxs-lookup"><span data-stu-id="86cf4-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)