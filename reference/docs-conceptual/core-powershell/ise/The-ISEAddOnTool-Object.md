---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: b813fcac547c8069e84741081a3ceb00044bab87
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseaddontool-object"></a>Obiekt ISEAddOnTool
  **ISEAddonTool** obiekt reprezentuje narzędzia zainstalowany dodatek, który zapewnia dodatkowe funkcje toWindows PowerShell ISE. Na przykład **polecenia** narzędzie, które można wyświetlić, klikając **widoku**, następnie **Pokaż dodatkowe polecenia**. Narzędzie to jest następnie dostępne dla Ciebie przez różne dostępne operacje **ISEAddOnTool** obiektów.

 Dodatkowe narzędzia może być skojarzony z okienka pionowy lub poziomy okienka. Okienko pionowe jest zadokowany do prawej krawędzi programu Windows PowerShell ISE. Okienko poziome jest zadokowana do dolnej krawędzi.

 Każda karta programu PowerShell w środowisku Windows PowerShell ISE może mieć własny zestaw dodatków zainstalowane. Zobacz [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) i [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) można uzyskać dostępu do kolekcji dostępne narzędzia do aktualnie wybrana karta lub takie same właściwości na dowolnym **PowerShellTab** obiekty w [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) obiektu kolekcji.

## <a name="methods"></a>Metody
 Dla obiektów tej klasy nie ma dostępnych żadnych metod programu PowerShell ISE właściwe dla systemu Windows.

## <a name="properties"></a>Właściwości

### <a name="control"></a>Kontrola
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

 **Kontroli** właściwość zapewnia dostęp do odczytu do wielu szczegółów poleceń narzędzia dodatku.

```
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
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

 Właściwości typu Boolean wskazującą, czy narzędzie dodatek jest widoczne w swojej przypisanej okienka. Jeśli jest on widoczny, można ustawić **IsVisible** właściwości **$false** można ukryć narzędzie lub ustawić **IsVisible** właściwości **$true** Aby Narzędzie dodatek widoczne na karcie środowiska PowerShell. Należy pamiętać, że po narzędzia dodatek jest ukryty, nie jest już dostępny za pośrednictwem **CurrentVisibleHorizontalTool** lub **CurrentVisibleVerticalTool** obiekty i dlatego nie może być widoczne za pomocą Ta właściwość dla tego obiektu.

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

### <a name="name"></a>Nazwa
  Obsługiwane w programie Windows PowerShell ISE 3.0 i nowszych i nie znajduje się w starszych wersjach.

 Właściwość tylko do odczytu, która pobiera nazwę narzędzia dodatku.

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a>Zobacz też
- [Obiekt ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Windows PowerShell ISE skryptów modelu obiektów](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Hierarchia modelu obiektów ISE](The-ISE-Object-Model-Hierarchy.md)

