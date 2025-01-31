---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnTool
ms.openlocfilehash: c71602d200b941ed4fb142b9c35f0fe68982e3e9
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028984"
---
# <a name="the-iseaddontool-object"></a>Obiekt ISEAddOnTool

**ISEAddonTool** obiekt reprezentuje narzędzie zainstalowany dodatek, który zapewnia dodatkowe funkcje toWindows PowerShell ISE. Na przykład **polecenia** narzędzie, które można wyświetlić, klikając **widoku**, następnie **Pokaż polecenia dodatku**. To narzędzie jest dostępne dla Ciebie przez operacje dostępne różne **ISEAddOnTool** obiektów.

Każde narzędzie dodatek może być skojarzony z okienka pionowej lub okienko poziome. Okienko pionowe jest zadokowany na prawej krawędzi środowiska Windows PowerShell ISE. Okienko poziome jest zadokowana do dolnej krawędzi.

Każda karta środowiska PowerShell w środowisku Windows PowerShell ISE może mieć własny zestaw dodatku narzędzia są zainstalowane. Zobacz [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) i [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) można uzyskać dostęp do kolekcji dostępne narzędzia do aktualnie wybrana karta lub tymi samymi właściwościami na dowolnym **PowerShellTab** obiekty w [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) obiektu kolekcji.

## <a name="methods"></a>Metody

Brak dostępnych żadnych metod Windows PowerShell ISE specyficzne dla obiektów tej klasy.

## <a name="properties"></a>Właściwości

### <a name="control"></a>Kontrola

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

**Kontroli** właściwość zapewnia dostęp do odczytu do wielu szczegółowe informacje o narzędziu poleceń dodatków.

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

### <a name="isvisible"></a>IsVisible

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość logiczna, która wskazuje, czy narzędzie dodatek jest aktualnie widoczne w jej okienku przypisane. Jeśli jest widoczny, możesz ustawić **IsVisible** właściwości **$false** można ukryć narzędzie lub ustawić **IsVisible** właściwości **$true** się Narzędzie dodatek jest widoczne na karcie programu PowerShell. Należy pamiętać, że po narzędziem dodatek jest ukryta, nie jest już dostępny za pośrednictwem **CurrentVisibleHorizontalTool** lub **CurrentVisibleVerticalTool** obiektów i dlatego nie może być widoczne przy użyciu Ta właściwość dla tego obiektu.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Nazwa

Obsługiwane w środowisku Windows PowerShell ISE 3.0 i nowszych, a nie znajduje się w starszych wersjach.

Właściwość tylko do odczytu, który pobiera nazwę narzędzia dodatku.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Zobacz też

- [Obiekt ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)
