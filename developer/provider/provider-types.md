---
title: Typy dostawców | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 25b604621c90f1aa88bc1eea365e47db66e98c3d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848496"
---
# <a name="provider-types"></a>Typy dostawców

Dostawców zdefiniować swoje podstawowe funkcje, zmieniając działanie ich działania polecenia cmdlet dostawcy (udostępnione przez środowisko Windows PowerShell). Na przykład dostawcy mogą wykorzystywać funkcje domyślne metody `Get-Item` polecenia cmdlet lub ich można zmienić sposób działania tego polecenia cmdlet, podczas pobierania elementów z magazynu danych. Funkcje dostawcy, opisane w tym temacie obejmują funkcje zdefiniowane przez zastąpienie metody z klasy bazowej określonego dostawcy i interfejsy.

> [!NOTE]
> W przypadku funkcji dostawcy, które są wstępnie zdefiniowane przez środowisko Windows PowerShell, zobacz [możliwości dostawcy](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Z włączoną obsługą dostawcy

Z włączoną obsługą dostawcy określić domyślne dyski dostępne dla użytkownika i Zezwalaj użytkownikowi na dodawanie lub usuwanie dysków. W większości przypadków dostawcy są włączone dysku dostawcy, ponieważ wymagają one niektóre domyślnym dysku do uzyskania dostępu do magazynu danych. Jednak podczas pisania własnego dostawcę możesz może lub nie chcieć umożliwić użytkownikowi tworzenie i usuwanie dysków.

Aby utworzyć dostawcę z włączonym na dysku, klasa dostawcy musi pochodzić od klasy [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy lub innej klasy, która wynika z tej klasy. [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasa definiuje następujące metody dysków domyślnego dostawcę implementujących i obsługujących `New-PSDrive` i `Remove-PSDrive` polecenia cmdlet. W większości przypadków do obsługi polecenia cmdlet dostawcy użytkownik musi zastąpić metodę, która wywołuje aparatu programu Windows PowerShell w celu wywołania polecenia cmdlet, takich jak `NewDrive` metodę `New-PSDrive` polecenia cmdlet, na które opcjonalnie można zastąpić drugiej metody, takie jak `NewDriveDynamicParameters`, dodawania parametrów dynamicznych do polecenia cmdlet.

- [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metoda definiuje stacji domyślne, które są dostępne dla użytkownika, zawsze wtedy, gdy jest używana przez dostawcę.

- [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) i [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) metody Definiuje, jak dostawca obsługuje `New-PSDrive` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi tworzenie dysków można uzyskać dostępu do magazynu danych.

- [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Metoda określa, jak dostawca obsługuje `Remove-PSDrive` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usuwanie dysków z magazynu danych.

## <a name="item-enabled-providers"></a>Element dostępny dostawców

Element włączony dostawców Zezwalaj użytkownikowi na pobieranie, ustawianie lub wyczyść elementy w magazynie danych. "Element" jest elementem magazynu danych, który użytkownik może uzyskać dostęp, lub niezależnie zarządzać. Aby utworzyć dostawcę element jest włączony, klasa dostawcy musi pochodzić od klasy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy lub innej klasy, która wynika z tej klasy.

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy definiuje następujące metody wykonywania polecenia cmdlet określonego dostawcy. W większości przypadków do obsługi polecenia cmdlet dostawcy użytkownik musi zastąpić metodę, która wywołuje aparatu programu Windows PowerShell w celu wywołania polecenia cmdlet, takich jak `ClearItem` metodę `Clear-Item` polecenia cmdlet, na które opcjonalnie można zastąpić drugiej metody, takie jak `ClearItemDynamicParameters`, dodawania parametrów dynamicznych do polecenia cmdlet.

- [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metody Zdefiniuj, jak dostawca obsługuje `Clear-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usuwanie wartości elementu w magazynie danych.

- [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metod określa sposób obsługuje usługi dostawcy `Get-Item` polecenia cmdlet dostawcy. To polecenie cmdlet pozwala użytkownikowi na pobieranie danych z magazynu danych.

- [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) i [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metod określa sposób obsługuje usługi dostawcy `Set-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi zaktualizowanie wartości elementów w magazynie danych.

- [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) i [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metody Zdefiniuj, jak dostawca obsługuje `Invoke-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi wykonaj akcję domyślną, określony przez element.

- [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) i [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metody Zdefiniuj, jak dostawca obsługuje `Test-Path` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownika w celu ustalenia, czy istnieją wszystkie elementy ścieżki.

  Oprócz metod używaną do zaimplementowania w przypadku polecenia cmdlet dostawcy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasa definiuje również następujące metody:

- [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) metoda umożliwia użytkownikowi używać symboli wieloznacznych, określając ścieżkę dostawcy.

- [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) służy do określania, czy ścieżka jest składniowo i semantycznie prawidłowa dla dostawcy.

## <a name="container-enabled-providers"></a>Dostawców z włączoną funkcją kontenera

Włączone kontenera dostawców Zezwalaj użytkownikowi na zarządzanie elementy, które są kontenery. Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego. Aby utworzyć dostawcę z obsługą kontenerów, klasa dostawcy musi pochodzić od klasy [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy lub innej klasy, która wynika z tej klasy.

> [!IMPORTANT]
> Dostawców z włączoną funkcją kontenera nie może uzyskać dostęp do magazynów danych zawierających zagnieżdżone kontenery. Element podrzędny kontenera w przypadku innego kontenera, należy zaimplementować dostawcę włączone nawigacji.

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy definiuje następujące metody wykonywania polecenia cmdlet określonego dostawcy. W większości przypadków do obsługi polecenia cmdlet dostawcy użytkownik musi zastąpić metodę, która wywołuje aparatu programu Windows PowerShell w celu wywołania polecenia cmdlet, takich jak `CopyItem` metodę `Copy-Item` polecenia cmdlet, na które opcjonalnie można zastąpić drugiej metody, takie jak `CopyItemDynamicParameters`, dodawania parametrów dynamicznych do polecenia cmdlet.

- [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) i [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) Definiowanie metody, jak dostawca obsługuje `Copy-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi kopiowanie elementu z jednej lokalizacji do innej.

- [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) i [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) metod Określa, jak dostawca obsługuje `Get-ChildItem` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikom pobieranie elementów podrzędnych elementu nadrzędnego.

- [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) i [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metod Określa, jak dostawca obsługuje `Get-ChildItem` polecenia cmdlet dostawcy jeśli jego `Name` określono parametr.

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) i [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) Definiowanie metody, jak dostawca obsługuje `New-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi tworzenie nowych elementów w magazynie danych.

- [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) i [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) Definiowanie metody, jak dostawca obsługuje `Remove-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usuwanie elementów z magazynu danych.

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) i [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) Definiowanie metody, jak dostawca obsługuje `Rename-Item` polecenia cmdlet dostawcy. To polecenie cmdlet pozwala użytkownikowi zmienić nazwy elementów w magazynie danych.

  Oprócz metod używaną do zaimplementowania w przypadku polecenia cmdlet dostawcy [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasa definiuje również następujące metody:

- [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metoda może służyć przez klasę dostawcy, aby określić, czy element ma elementy podrzędne.

- [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) metoda może służyć przez klasę dostawcy do utworzenia nowej ścieżki specyficznego dla dostawcy z określonej ścieżki.

## <a name="navigation-enabled-providers"></a>Nawigacja włączona dostawców

Nawigacja włączona dostawców umożliwia użytkownikowi przenoszenie elementów w magazynie danych. Aby utworzyć dostawcę z obsługą nawigacji, klasa dostawcy musi pochodzić od klasy [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy definiuje następujące metody wykonywania polecenia cmdlet określonego dostawcy. W większości przypadków do obsługi polecenia cmdlet dostawcy użytkownik musi zastąpić metodę, która wywołuje aparatu programu Windows PowerShell w celu wywołania polecenia cmdlet, takich jak `MoveItem` metodę `Move-Item` polecenia cmdlet, na które opcjonalnie można zastąpić drugiej metody, takie jak `MoveItemDynamicParameters`, dodawania parametrów dynamicznych do polecenia cmdlet.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) i [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) Definiowanie metody, jak dostawca obsługuje `Move-Item` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi przenoszenie elementu z jednej lokalizacji w magazynie do innej lokalizacji.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) Metoda określa, jak dostawca obsługuje `Join-Path` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi łączenie segmentu ścieżki nadrzędnej i podrzędnej utworzyć wewnętrzna dostawcy ścieżki.

  Oprócz metod używaną do zaimplementowania w przypadku polecenia cmdlet dostawcy [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasa definiuje również następujące metody:

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metoda wyodrębnia nazwę węzła podrzędnego ścieżki.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoda wyodrębnia nadrzędnej części ścieżki.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) Metoda określa, czy element jest elementem kontenera. W tym kontekście kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metoda zwraca ścieżkę do elementu, który jest określana względem określonej ścieżki podstawowej.

## <a name="content-enabled-providers"></a>Dostawcy zawartości, włączone

Zawartość włączona dostawców umożliwia użytkownikowi Wyczyść, pobrać lub ustawić zawartość elementów w magazynie danych. Na przykład dostawcy FileSystem umożliwia wyczyszczenie, pobieranie i ustawianie zawartości plików w systemie plików. Aby utworzyć dostawcę zawartości włączone, klasa dostawcy musi implementować metody [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu.

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejs definiuje następujące metody wykonywania polecenia cmdlet określonego dostawcy. W większości przypadków do obsługi polecenia cmdlet dostawcy użytkownik musi zastąpić metodę, która wywołuje aparatu programu Windows PowerShell w celu wywołania polecenia cmdlet, takich jak `ClearContent` metodę `Clear-Content` polecenia cmdlet, na które opcjonalnie można zastąpić drugiej metody, takie jak `ClearContentDynamicParameters`, dodawania parametrów dynamicznych do polecenia cmdlet.

- [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) i [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)metod Określa, jak dostawca obsługuje `Clear-Content` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usuwanie zawartość elementu, bez usuwania elementu.

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) i [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metod Określa, jak dostawca obsługuje `Get-Content` polecenia cmdlet dostawcy. To polecenie cmdlet pozwala użytkownikowi na pobieranie zawartości elementu. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metoda zwraca [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interfejsu, który definiuje metody używane do odczytywania zawartości.

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) i [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metod Określa, jak dostawca obsługuje `Set-Content` polecenia cmdlet dostawcy. To polecenie cmdlet pozwala użytkownikowi na aktualizowanie zawartości elementu. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metoda zwraca [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interfejsu, który definiuje metody używane do zapisywania zawartości.

## <a name="property-enabled-providers"></a>Włączona właściwość dostawcy

Włączona właściwość dostawcy Zezwalaj użytkownikowi na zarządzanie właściwości elementów w magazynie danych. Aby utworzyć dostawcę właściwość włączona, klasa dostawcy musi implementować metody [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfejsów. W większości przypadków do obsługi polecenia cmdlet dostawcy użytkownik musi zastąpić metodę, która wywołuje aparatu programu Windows PowerShell w celu wywołania polecenia cmdlet, takich jak `ClearProperty` metodę dla polecenia cmdlet wyczyść właściwości i opcjonalnie może spowodować zastąpienie drugiej metody, takie jak `ClearPropertyDynamicParameters`, dodawania parametrów dynamicznych do polecenia cmdlet.

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfejs definiuje następujące metody wykonywania polecenia cmdlet określonego dostawcy:

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) i [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) metod Określa, jak dostawca obsługuje `Clear-ItemProperty` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usuwanie wartości właściwości.

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) i [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)metod Określa, jak dostawca obsługuje `Get-ItemProperty` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikom pobieranie właściwości elementu.

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) i [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)metod Określa, jak dostawca obsługuje `Set-ItemProperty` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi zaktualizowanie właściwości elementu.

  [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfejs definiuje następujące metody wykonywania polecenia cmdlet określonego dostawcy:

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) metod Określa, jak dostawca obsługuje `Copy-ItemProperty` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi kopiowanie właściwości i jego wartość z jednej lokalizacji do innej.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) metod Określa, jak dostawca obsługuje `Move-ItemProperty` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi przenoszenie właściwości i jego wartość z jednej lokalizacji do innej.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) metod Określa, jak dostawca obsługuje `New-ItemProperty` polecenia cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi tworzenie nowych właściwości i określanie jego wartości.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) metod Określa, jak dostawca obsługuje `Remove-ItemProperty` polecenia cmdlet. To polecenie cmdlet umożliwia użytkownikowi usuwanie właściwości i jego wartość.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) i [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) metod Określa, jak dostawca obsługuje `Rename-ItemProperty` polecenia cmdlet. To polecenie cmdlet pozwala użytkownikowi na zmianę nazwy właściwości.

## <a name="see-also"></a>Zobacz też

[Pisanie dostawcy programu PowerShell Windows](./writing-a-windows-powershell-provider.md)