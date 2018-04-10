---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Hierarchia modeli obiektów środowiska ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="the-ise-object-model-hierarchy"></a>Hierarchia modeli obiektów środowiska ISE

W tym temacie przedstawiono hierarchię obiektów, które należą do programu Windows PowerShell Integrated Scripting Environment (ISE).
Windows PowerShell ISE znajduje się w środowisku Windows PowerShell 3.0 i Windows PowerShell 4.0.
Kliknij obiekt, aby przejść do dokumentacji dla klasy, który definiuje obiekt.

## <a name="psise-object"></a>Obiekt $psISE

**$PsISE** obiekt jest [główny obiekt](The-ObjectModelRoot-Object.md) hierarchii obiektów programu Windows PowerShell ISE.
Znajduje się na najwyższym poziomie, ułatwia następujące obiekty dostępne dla skryptów:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

**$PsISE.CurrentFile** obiektu jest wystąpieniem [ISEFile](The-ISEFile-Object.md) klasy.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

**$PsISE.CurrentPowerShellTab** obiektu jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

**$PsISE.CurrentVisibleHorizontalTool** obiektu jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.
Reprezentuje narzędzia zainstalowany dodatek, który obecnie jest zadokowany do górnej krawędzi okna programu Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

**$PsISE.CurrentVisibleHorizontalTool** obiektu jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.
Reprezentuje narzędzia zainstalowany dodatek, który obecnie jest zadokowany do prawej krawędzi okna programu Windows PowerShell ISE.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

**$PsISE.Options** obiektu jest wystąpieniem [ISEOptions](The-ISEOptions-Object.md) klasy.
Obiekt ISEOptions reprezentuje różne ustawienia dla programu Windows PowerShell ISE.
To wystąpienie klasy Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

**$PsISE.PowerShellTabs** obiektu jest wystąpieniem [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasy.
Jest to zbiór wszystkich aktualnie otwartych PowerShell kart, które reprezentują dostępne środowiska Windows PowerShell Uruchom środowiskach, na komputerze lokalnym lub komputerach zdalnych połączonych.
Każdy element członkowski w kolekcji jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.

## <a name="see-also"></a>Zobacz też

- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)