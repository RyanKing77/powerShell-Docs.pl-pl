---
title: Polecenia cmdlet dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080955"
---
# <a name="provider-cmdlets"></a>Polecenia cmdlet dostawców

Polecenia cmdlet, które użytkownik może uruchomić w celu zarządzania magazynu danych są określane jako polecenia cmdlet dostawcy. Aby zapewnić obsługę tych poleceń cmdlet, należy zastąpić niektóre metody zdefiniowane przez klasy bazowej dostawcy i interfejsy.

## <a name="provider-cmdlets"></a>Polecenia cmdlet dostawcy

Poniżej przedstawiono polecenia cmdlet dostawcy, które mogą być uruchamiane przez użytkownika:

### <a name="psdrive-cmdlets"></a>Polecenia cmdlet PSDrive

- `Get-PSDrive`: To polecenie cmdlet zwraca programu Windows PowerShell dysków w bieżącej sesji. Nie trzeba zastąpić żadnych metod do obsługi tego polecenia cmdlet.

- `New-PSDrive`: To polecenie cmdlet umożliwia użytkownikowi tworzenie dysków programu Windows PowerShell można uzyskać dostępu do magazynu danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) i [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metody.

- `Remove-PSDrive`: To polecenie cmdlet umożliwia użytkownikowi usuwanie dysków programu Windows PowerShell, uzyskujących dostęp do magazynu danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metody.

### <a name="item-cmdlets"></a>Poleceń cmdlet elementów

- `Clear-Item`: To polecenie cmdlet umożliwia użytkownikowi usuwanie wartość elementu w magazynie danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) i [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metody.

- `Copy-Item`: To polecenie cmdlet umożliwia użytkownikowi kopiowanie elementu z jednej lokalizacji do innej. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) i [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metody.

- `Get-Item`: To polecenie cmdlet pozwala użytkownikowi na pobieranie danych z magazynu danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metody.

- `Get-ChildItem`: To polecenie cmdlet umożliwia użytkownikom pobieranie elementów podrzędnych elementu nadrzędnego. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić następujące metody:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: To polecenie cmdlet umożliwia użytkownikowi wykonaj akcję domyślną, określony przez element. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) i [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metody.

- `Move-Item`: To polecenie cmdlet umożliwia użytkownikowi przenoszenie elementu z jednej lokalizacji do innej lokalizacji. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) i [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)metody s.

- `New-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi utworzenie nowego elementu w magazynie danych.

- `Remove-Item`: To polecenie cmdlet umożliwia użytkownikowi usuwanie elementów z magazynu danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) i [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metody.

- `Rename-Item`: To polecenie cmdlet pozwala użytkownikowi zmienić nazwy elementów w magazynie danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) i [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metody.

- `Set-Item`: To polecenie cmdlet umożliwia użytkownikowi zaktualizowanie wartości elementów w magazynie danych. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metody.

### <a name="item-content-cmdlets"></a>Zawartość poleceń cmdlet elementów

- `Add-Content`: To polecenie cmdlet umożliwia użytkownikowi dodawanie zawartości do elementu.

- `Clear-Content`: To polecenie cmdlet umożliwia użytkownikowi usuwanie zawartości z elementu bez usuwania elementu. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) i [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metody.

- `Get-Content`: To polecenie cmdlet pozwala użytkownikowi na pobieranie zawartości elementu. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) i [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metody. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metoda zwraca [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interfejsu, który definiuje metody używane do odczytywania zawartości.

- `Set-Content`: To polecenie cmdlet pozwala użytkownikowi na aktualizowanie zawartości elementu. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) i [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metody. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metoda zwraca [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interfejsu, który definiuje metody używane do zapisywania zawartości.

### <a name="item-property-cmdlets"></a>Poleceń cmdlet właściwości elementów

- `Clear-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi usuwanie wartości właściwości. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) i [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metody.

- `Copy-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi kopiowanie właściwości i jego wartość z jednej lokalizacji do innej. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) metody.

- `Get-ItemProperty`: To polecenie cmdlet pobiera właściwości elementu. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) i [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) metody.

- `Move-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi przenoszenie właściwości i jego wartość z jednej lokalizacji do innej. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) metody.

- `New-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi tworzenie nowych właściwości i określanie jego wartości. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metody.

- `Remove-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi usuwanie właściwości i jego wartość. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metody.

- `Rename-ItemProperty`: To polecenie cmdlet pozwala użytkownikowi na zmianę nazwy właściwości. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metody.

- `Set-ItemProperty`: To polecenie cmdlet umożliwia użytkownikowi zaktualizowanie właściwości elementu. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) i [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) metody.

### <a name="location-cmdlets"></a>Polecenia cmdlet lokalizacji

- `Get-Location`: Pobiera informacje o bieżącej lokalizacji pracy. Nie trzeba zastąpić żadnych metod do obsługi tego polecenia cmdlet.

- `Pop-Location`: To polecenie cmdlet zmienia bieżącą lokalizację do lokalizacji ostatnio wypychane na stosie. Nie trzeba zastąpić żadnych metod do obsługi tego polecenia cmdlet.

- `Push-Location`: To polecenie cmdlet dodaje bieżącej lokalizacji do góry listy lokalizacji ("stos"). Nie trzeba zastąpić żadnych metod do obsługi tego polecenia cmdlet.

- `Set-Location`: To polecenie cmdlet Ustawia bieżącą lokalizację pracy w określonej lokalizacji. Nie trzeba zastąpić żadnych metod do obsługi tego polecenia cmdlet.

### <a name="path-cmdlets"></a>Polecenia cmdlet ścieżki

- `Join-Path`: To polecenie cmdlet umożliwia użytkownikowi łączenie segmentu ścieżki nadrzędnej i podrzędnej utworzyć wewnętrzna dostawcy ścieżki. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metody.

- `Convert-Path`: To polecenie cmdlet konwertuje ścieżki ze ścieżki programu Windows PowerShell do ścieżki dostawcy środowiska Windows PowerShell.

- `Split-Path`: Zwraca określoną część ścieżki.

- `Resolve-Path`: Usuwa znaki symboli wieloznacznych w ścieżce i wyświetla zawartość ścieżki.

- `Test-Path`: To polecenie cmdlet Określa, czy istnieją wszystkie elementy ścieżki. Aby zapewnić obsługę tego polecenia cmdlet, należy zastąpić [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) i [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metody.

### <a name="psprovider-cmdlets"></a>Polecenia cmdlet PSProvider

- `Get-PSProvider`: To polecenie cmdlet zwraca informacje o dostawcy, które są dostępne w sesji. Nie trzeba zastąpić żadnych metod do obsługi tego polecenia cmdlet.