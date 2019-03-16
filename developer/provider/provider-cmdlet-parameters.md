---
title: Parametry polecenia cmdlet dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057046"
---
# <a name="provider-cmdlet-parameters"></a>Parametry poleceń cmdlet dostawców

Polecenia cmdlet dostawcy pochodzą z zestawem parametry statyczne, które są dostępne dla wszystkich dostawców, które obsługują polecenia cmdlet, a także jako dynamiczne parametry, które są dodawane, gdy użytkownik określi określonej wartości dla niektórych statycznych parametrów polecenia cmdlet dostawcy.

## <a name="provider-cmdlet-static-parameters"></a>Parametry statyczne polecenia Cmdlet dostawcy

Parametry statyczne są definiowane przez środowisko Windows PowerShell. Duży zestaw parametrów jest implementowany przez środowisko Windows PowerShell w celu zapewnienia spójności wszystkich dostawców i zapewnienia prostsze środowisko programistyczne. Przykłady te parametry `literalPath`, `exclude`, i `include` parametry `Get-Item` polecenia cmdlet. Mniejszy zestaw te parametry można zastąpić zapewnienie akcje, które są specyficzne dla dostawcy. Przykłady te parametry `Path` i `Value` parametru `Set-Item` polecenia cmdlet. Poniżej przedstawiono listę parametrów, które mogą zostać zastąpione dla polecenia cmdlet dostawcy.

`Clear-Content` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Clear-Content` polecenia cmdlet, implementując [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)metody.

`Clear-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Clear-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) Metoda.

`Clear-ItemProperty` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` i `Name` parametry `Clear-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) metody.

`Copy-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path`, `Destination`, i `Recurse` parametry `Copy-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metody.

Polecenie cmdlet Get-ChildItems można określić, jak Twój dostawca użyje wartości przekazywanych do `Path` i `Recurse` parametry `Get-ChildItem` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) i [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metody.

`Get-Content` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Get-Content` polecenia cmdlet, implementując [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metody.

`Get-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Get-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metody.

`Get-ItemProperty` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` i `Name` parametry `Get-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) metody.

`Invoke-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Invoke-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)metody.

`Move-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` i `Destination` parametry `Move-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metody.

`New-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path`, `ItemType`, i `Value` parametry `New-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metody.

`New-ItemProperty` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path`, `Name`, `PropertyType`, i `Value` parametry `New-ItemProperty` polecenia cmdlet, implementując [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) metody.

`Remove-Item` Można określić, jak Twój dostawca użyje wartości przekazywanych do `Path` i `Recurse` parametry `Remove-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metody.

`Remove-ItemProperty` Można określić, jak Twój dostawca użyje wartości przekazywanych do `Path` i `Name` parametry `Remove-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) metody.

`Rename-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` i `NewName` parametry `Rename-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metody.

`Rename-ItemProperty` Można określić, jak Twój dostawca użyje wartości przekazywanych do `Path`, `NewName`, i `Name` parametry `Rename-ItemProperty` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) metody.

`Set-Content` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Set-Content` polecenia cmdlet, implementując [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metody.

`Set-Item` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` i `Value` parametry `Set-Item` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metody.

`Set-ItemProperty` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` i `Value` parametry `Set-Item` polecenia cmdlet, implementując [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) metody.

`Test-Path` można określić, jak Twój dostawca użyje wartości przekazywane do polecenia cmdlet `Path` parametru `Test-Path` polecenia cmdlet, implementując [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)metody.

Ponadto nie można określić właściwości tych parametrów, na przykład tego, czy są one opcjonalne lub wymagane, ani nie może możesz nadać te parametry aliasu, jak lub określić dowolne atrybutów sprawdzania poprawności. Z kolei można określić właściwości parametru w poleceniach cmdlet autonomicznego przy użyciu atrybutów, takich jak `Parameters` atrybutu.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parametry dynamiczne polecenia Cmdlet dostawcy

Parametry dynamiczne dla dostawców polecenia cmdlet są podobne do dynamicznego dostawców dla autonomicznych poleceń cmdlet. W obu przypadkach parametry są dodawane do polecenia cmdlet, po użytkownik określa określoną wartość dla jednego z parametrów domyślnych `path` parametru. Jednak nie wszystkie parametry statyczne może służyć do wyzwolenia Dodawanie parametrów dynamicznych. Aby uzyskać więcej informacji na temat parametrów dynamicznych, zobacz [parametrów dynamicznych polecenia Cmdlet dostawcy](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Zobacz też

[Parametry dynamiczne polecenia Cmdlet dostawcy](./provider-cmdlet-dynamic-parameters.md)

[Pisanie dostawcy programu PowerShell Windows](./writing-a-windows-powershell-provider.md)