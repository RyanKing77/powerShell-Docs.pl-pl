---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Hierarchia modelu obiektów ISE"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>Hierarchia modelu obiektów ISE
W tym temacie przedstawiono hierarchię obiektów, które należą do programu Windows PowerShell Integrated Scripting Environment (ISE). Windows PowerShell ISE znajduje się w środowisku Windows PowerShell 3.0 i Windows PowerShell 4.0. Kliknij obiekt, aby przejść do dokumentacji dla klasy, który definiuje obiekt.

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
Jest to zbiór wszystkich aktualnie otwartych PowerShell kart, które reprezentują dostępne środowiska Windows PowerShell Uruchom środowiskach, na komputerze lokalnym lub komputerach zdalnych połączonych. Każdy element członkowski w kolekcji jest wystąpieniem [PowerShellTab](The-PowerShellTab-Object.md) klasy.

## <a name="see-also"></a>Zobacz też
- [Windows PowerShell ISE skryptów modelu obiektów](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Dotyczące modelu obiektów programu Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md)
