---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Hierarchia modeli obiektów środowiska ISE
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057727"
---
# <a name="the-ise-object-model-hierarchy"></a>Hierarchia modeli obiektów środowiska ISE

W tym temacie przedstawiono hierarchię obiektów, które są dostępne w ramach programu Windows PowerShell zintegrowane Scripting Environment (ISE).
Windows PowerShell ISE i jest dołączone w środowisku Windows PowerShell 3.0 w programie Windows PowerShell 4.0.
Kliknij obiekt, aby przejść do dokumentacji dla klasy, która definiuje obiekt.

## <a name="psise-object"></a>$psISE Object

**$PsISE** obiekt jest [główny obiekt](The-ObjectModelRoot-Object.md) hierarchii obiektów programu Windows PowerShell ISE.
Znajduje się na najwyższym poziomie, zapewnia następujące obiekty dostępne dla skryptów:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

**$PsISE.CurrentFile** obiekt jest wystąpieniem [ISEFile](The-ISEFile-Object.md) klasy.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

**$PsISE.CurrentPowerShellTab** obiekt jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

**$PsISE.CurrentVisibleHorizontalTool** obiekt jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.
Reprezentuje narzędzie zainstalowany dodatek, który aktualnie jest zadokowany do górnej krawędzi okna środowiska Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

**$PsISE.CurrentVisibleHorizontalTool** obiekt jest wystąpieniem [ISEAddOnTool](The-ISEAddOnTool-Object.md) klasy.
Reprezentuje narzędzie zainstalowany dodatek, który aktualnie jest zadokowany na prawej krawędzi okna środowiska Windows PowerShell ISE.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

**$PsISE.Options** obiekt jest wystąpieniem [ISEOptions](The-ISEOptions-Object.md) klasy.
Obiekt ISEOptions reprezentuje różne ustawienia dla środowiska Windows PowerShell ISE.
Jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

**$PsISE.PowerShellTabs** obiekt jest wystąpieniem [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) klasy.
Jest to kolekcja wszystkie aktualnie otwarte PowerShell karty, które reprezentują dostępne programu Windows PowerShell środowiska są uruchomione na komputerze lokalnym lub połączonych komputerów zdalnych.
Każdy element członkowski w kolekcji jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.

## <a name="see-also"></a>Zobacz też

- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)