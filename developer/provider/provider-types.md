---
title: Typy dostawców | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986659"
---
# <a name="provider-types"></a>Typy dostawców

Dostawcy definiują podstawowe funkcje, zmieniając sposób działania poleceń cmdlet dostawcy udostępnianych przez program PowerShell. Na przykład dostawcy mogą korzystać z domyślnej funkcji `Get-Item` polecenia cmdlet lub zmieniać sposób działania tego polecenia cmdlet podczas pobierania elementów z magazynu danych. Funkcja dostawcy opisana w tym dokumencie obejmuje funkcje zdefiniowane przez zastąpienie metod z określonych klas podstawowych i interfejsów dostawcy.

> [!NOTE]
> W przypadku funkcji dostawcy, które są wstępnie zdefiniowane przez program PowerShell, zobacz [możliwości dostawcy](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Dostawcy z obsługą stacji

Dostawcy obsługujący dyski określają domyślne stacje dostępne dla użytkownika i zezwalają użytkownikowi na dodawanie lub usuwanie dysków. W większości przypadków dostawcy są dostawcami obsługującymi dyski, ponieważ wymagają pewnego dysku domyślnego, aby uzyskać dostęp do magazynu danych. Jednak podczas pisania własnego dostawcy możesz lub nie chcieć zezwolić użytkownikowi na tworzenie i usuwanie dysków.

Aby utworzyć dostawcę z włączoną obsługą stacji dysków, Klasa dostawcy musi pochodzić od klasy [System. Management. Automation. Provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) lub innej klasy, która jest pochodną tej klasy. Klasa **System. Management. Automation. Provider. DriveCmdletProvider** definiuje następujące metody wdrażania domyślnych dysków dostawcy i obsługi `New-PSDrive` poleceń cmdlet i. `Remove-PSDrive` W większości przypadków aby obsłużyć polecenie cmdlet dostawcy, należy zastąpić metodę, którą aparat programu PowerShell wywołuje do wywołania polecenia cmdlet, takiego jak `NewDrive` Metoda `New-PSDrive` polecenia cmdlet, i opcjonalnie można zastąpić drugą metodę, taką jak `NewDriveDynamicParameters` , aby dodać parametry dynamiczne do polecenia cmdlet.

- Metoda [System. Management. Automation. Provider. DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) definiuje domyślne stacje, które są dostępne dla użytkownika za każdym razem, gdy jest używany dostawca.

- Metody [System. Management. Automation. Provider. DriveCmdletProvider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) i [System. Management. Automation. Provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) definiują sposób, w `New-PSDrive`jakidostawcaobsługujepolecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi tworzenie dysków w celu uzyskania dostępu do magazynu danych.

- Metoda [System. Management. Automation. Provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) definiuje, w `Remove-PSDrive` jaki sposób dostawca obsługuje polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usuwanie dysków z magazynu danych.

## <a name="item-enabled-providers"></a>Dostawcy obsługujący elementy

Dostawcy obsługujący elementy umożliwiają użytkownikowi pobieranie, Ustawianie lub Czyszczenie elementów w magazynie danych. "Element" to element magazynu danych, do którego użytkownik może uzyskać dostęp lub niezależnie zarządzać nimi. Aby utworzyć dostawcę z włączoną obsługą elementów, Klasa dostawcy musi pochodzić od klasy [System. Management. Automation. Provider. ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) lub innej klasy, która jest pochodną tej klasy.

Klasa **System. Management. Automation. Provider. ItemCmdletProvider** definiuje następujące metody implementowania określonych poleceń cmdlet dostawcy. W większości przypadków aby obsłużyć polecenie cmdlet dostawcy, należy zastąpić metodę, którą aparat programu PowerShell wywołuje do wywołania polecenia cmdlet, takiego jak `ClearItem` Metoda `Clear-Item` polecenia cmdlet, i opcjonalnie można zastąpić drugą metodę, taką jak `ClearItemDynamicParameters` , aby dodać parametry dynamiczne do polecenia cmdlet.

- Metody [System. Management. Automation. Provider. ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) i [System. Management. Automation. Provider. ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) definiują sposób, w `Clear-Item`jakidostawcaobsługujepolecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usunięcie wartości elementu w magazynie danych.

- Metody [System. Management. Automation. Provider. ItemCmdletProvider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) i [System. Management. Automation. Provider. ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definiują sposób, w `Get-Item` jaki dostawca obsługuje polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi pobieranie danych z magazynu danych.

- Metody [System. Management. Automation. Provider. ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) i [System. Management. Automation. Provider. ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definiują sposób, w `Set-Item` jaki dostawca obsługuje polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi aktualizowanie wartości elementów w magazynie danych.

- Metody [System. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) i [System. Management. Automation. Provider. Itemcmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) definiują, jak Twój dostawca obsługuje polecenie cmdlet dostawcy. `Invoke-Item` To polecenie cmdlet umożliwia użytkownikowi wykonanie domyślnej akcji określonej przez element.

- Metody [System. Management. Automation. Provider. ItemCmdletProvider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) i [System. Management. Automation. Provider. ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) definiują sposób, w `Test-Path`jakidostawcaobsługujepolecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi określenie, czy istnieją wszystkie elementy ścieżki.

Oprócz metod używanych do implementowania poleceń cmdlet dostawcy Klasa **System. Management. Automation. Provider. ItemCmdletProvider** również definiuje następujące metody:

- Metoda [System. Management. Automation. Provider. ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) umożliwia użytkownikowi korzystanie z symboli wieloznacznych podczas określania ścieżki dostawcy.

- Obiekt [System. Management. Automation. Provider. ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) jest używany do określenia, czy ścieżka jest syntaktycznie i semantycznie ważna dla dostawcy.

## <a name="container-enabled-providers"></a>Dostawcy obsługujący kontenery

Dostawcy obsługujący kontenery umożliwiają użytkownikowi zarządzanie elementami, które są kontenerami. Kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego. Aby utworzyć dostawcę z włączoną obsługą kontenerów, Klasa dostawcy musi pochodzić od klasy [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) lub innej klasy, która jest pochodną tej klasy.

> [!IMPORTANT]
> Dostawcy obsługujący kontenery nie mogą uzyskać dostępu do magazynów danych zawierających zagnieżdżone kontenery. Jeśli element podrzędny kontenera jest innym kontenerem, należy zaimplementować dostawcę z włączoną nawigacją.

Klasa **System. Management. Automation. Provider. ContainerCmdletProvider** definiuje następujące metody implementowania określonych poleceń cmdlet dostawcy. W większości przypadków aby obsłużyć polecenie cmdlet dostawcy, należy zastąpić metodę, którą aparat programu PowerShell wywołuje do wywołania polecenia cmdlet, takiego jak `CopyItem` Metoda `Copy-Item` polecenia cmdlet, i opcjonalnie można zastąpić drugą metodę, taką jak `CopyItemDynamicParameters` , aby dodać parametry dynamiczne do polecenia cmdlet.

- Metody [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) i [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definiują sposób, w jakidostawcaobsługuje`Copy-Item` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi skopiowanie elementu z jednej lokalizacji do innej.

- Metody [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) i [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) definiują, jak Twój dostawca obsługuje polecenie cmdlet dostawcy. `Get-ChildItem` To polecenie cmdlet umożliwia użytkownikowi pobieranie elementów podrzędnych elementu nadrzędnego.

- Metody [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) i [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) definiują, jak Twój dostawca obsługuje polecenie `Get-ChildItem` cmdlet dostawcy, jeśli `Name` jego parametr jest określony.

- Metody [System. Management. Automation. Provider. ContainerCmdletProvider. newItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) i [System. Management. Automation. Provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definiują sposób, w jakidostawcaobsługuje`New-Item` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi tworzenie nowych elementów w magazynie danych.

- Metody [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) i [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definiują sposób, w jaki dostawca obsługuje `Remove-Item` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usunięcie elementów z magazynu danych.

- Metody [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) i [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definiują sposób, w jaki dostawca obsługuje `Rename-Item` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi zmianę nazwy elementów w magazynie danych.

Oprócz metod używanych do implementowania poleceń cmdlet dostawcy Klasa **System. Management. Automation. Provider. ContainerCmdletProvider** również definiuje następujące metody:

- Metoda [System. Management. Automation. Provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) może być używana przez klasę dostawcy w celu określenia, czy element ma elementy podrzędne.

- Metoda [System. Management. Automation. Provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) może być używana przez klasę Provider do tworzenia nowej ścieżki specyficznej dla dostawcy z określonej ścieżki.

## <a name="navigation-enabled-providers"></a>Dostawcy obsługujący nawigację

Dostawcy obsługujący nawigację umożliwiają użytkownikowi przenoszenie elementów w magazynie danych. Aby utworzyć dostawcę z włączoną nawigacją, Klasa dostawcy musi pochodzić od klasy [System. Management. Automation. Provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Klasa **System. Management. Automation. Provider. NavigationCmdletProvider** definiuje następujące metody implementowania określonych poleceń cmdlet dostawcy. W większości przypadków aby obsłużyć polecenie cmdlet dostawcy, należy zastąpić metodę, którą aparat programu PowerShell wywołuje do wywołania polecenia cmdlet, takiego jak `MoveItem` Metoda `Move-Item` polecenia cmdlet, i opcjonalnie można zastąpić drugą metodę, taką jak `MoveItemDynamicParameters` , aby dodać parametry dynamiczne do polecenia cmdlet.

- Metody [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) i [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definiują sposób, w jaki dostawca obsługuje `Move-Item` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi przeniesienie elementu z jednej lokalizacji w magazynie do innej lokalizacji.

- Metoda [System. Management. Automation. Provider. NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) definiuje, w `Join-Path` jaki sposób dostawca obsługuje polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi łączenie segmentu ścieżki nadrzędnej i podrzędnej w celu utworzenia ścieżki wewnętrznej dostawcy.

Oprócz metod używanych do implementowania poleceń cmdlet dostawcy Klasa **System. Management. Automation. Provider. NavigationCmdletProvider** również definiuje następujące metody:

- Metoda [System. Management. Automation. Provider. NavigationCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) getchildname wyodrębnia nazwę węzła podrzędnego ścieżki.

- Metoda [System. Management. Automation. Provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) Wyodrębnia element nadrzędny ścieżki.

- Metoda [System. Management. Automation. Provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) określa, czy element jest elementem kontenera. W tym kontekście kontener jest grupą elementów podrzędnych w ramach wspólnego elementu nadrzędnego.

- Metoda [System. Management. Automation. Provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) zwraca ścieżkę do elementu odnoszącego się do określonej ścieżki bazowej.

## <a name="content-enabled-providers"></a>Dostawcy obsługujący zawartość

Dostawcy obsługujący zawartość zezwalają użytkownikowi na czyszczenie, pobieranie lub Ustawianie zawartości elementów w magazynie danych.
Na przykład dostawca systemu plików umożliwia wyczyszczenie, pobieranie i Ustawianie zawartości plików w systemie plików. Aby utworzyć dostawcę z włączoną obsługą zawartości, Klasa dostawcy musi implementować metody interfejsu [System. Management. Automation. Provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

Interfejs **System. Management. Automation. Provider. IContentCmdletProvider** definiuje następujące metody implementowania określonych poleceń cmdlet dostawcy. W większości przypadków aby obsłużyć polecenie cmdlet dostawcy, należy zastąpić metodę, którą aparat programu PowerShell wywołuje do wywołania polecenia cmdlet, takiego jak `ClearContent` Metoda `Clear-Content` polecenia cmdlet, i opcjonalnie można zastąpić drugą metodę, taką jak `ClearContentDynamicParameters` , aby dodać parametry dynamiczne do polecenia cmdlet.

- Metody [System. Management. Automation. Provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) i [System. Management. Automation. Provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) definiują sposób obsługi dostawcy polecenie `Clear-Content` cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi usunięcie zawartości elementu bez usuwania elementu.

- Metody [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) i [System. Management. Automation. Provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) definiują, jak Twój dostawca obsługuje polecenie cmdlet dostawcy. `Get-Content` To polecenie cmdlet umożliwia użytkownikowi pobranie zawartości elementu. Metoda zwraca interfejs [System. Management. Automation. Provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) , który definiuje metody używane do odczytywania zawartości. `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader`

- Metody [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) i [System. Management. Automation. Provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) definiują, jak Twój dostawca obsługuje polecenie cmdlet dostawcy. `Set-Content` To polecenie cmdlet umożliwia użytkownikowi zaktualizowanie zawartości elementu. Metoda zwraca interfejs [System. Management. Automation. Provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) , który definiuje metody używane do zapisywania zawartości. `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`

## <a name="property-enabled-providers"></a>Dostawcy z włączoną obsługą właściwości

Dostawcy z włączonymi właściwościami umożliwiają użytkownikowi zarządzanie właściwościami elementów w magazynie danych.
Aby utworzyć dostawcę z włączoną obsługą właściwości, Klasa dostawcy musi implementować metody [System. Management. Automation. Provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) i [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)interfejsy. W większości przypadków aby obsłużyć polecenie cmdlet dostawcy, należy zastąpić metodę, którą aparat programu PowerShell wywołuje do wywołania polecenia cmdlet, takiego jak `ClearProperty` Metoda polecenia cmdlet Clear-Property i opcjonalnie można zastąpić drugą metodę, taką jak `ClearPropertyDynamicParameters` , aby dodać parametry dynamiczne do polecenia cmdlet.

Interfejs **System. Management. Automation. Provider. IPropertyCmdletProvider** definiuje następujące metody implementowania określonych poleceń cmdlet dostawcy:

- Metody [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) i [System. Management. Automation. Provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) definiują, jak Twój dostawca obsługuje polecenie cmdlet dostawcy. `Clear-ItemProperty` To polecenie cmdlet umożliwia użytkownikowi usunięcie wartości właściwości.

- Metody [System. Management. Automation. Provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) i [System. Management. Automation. Provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) definiują sposób obsługi dostawcy polecenie `Get-ItemProperty` cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi pobranie właściwości elementu.

- Metody [System. Management. Automation. Provider. IPropertyCmdletProvider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) i [System. Management. Automation. Provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) definiują sposób obsługi dostawcy polecenie `Set-ItemProperty` cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi zaktualizowanie właściwości elementu.

  Interfejs **System. Management. Automation. Provider. IDynamicPropertyCmdletProvider** definiuje następujące metody implementowania określonych poleceń cmdlet dostawcy:

- Metody [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) i [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) definiują sposób dostawca obsługuje `Copy-ItemProperty` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi kopiowanie właściwości i jej wartości z jednej lokalizacji do innej.

- Metody [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) i [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) definiują sposób dostawca obsługuje `Move-ItemProperty` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi przeniesienie właściwości i jej wartości z jednej lokalizacji do innej.

- Metody [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) i [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) definiują sposób dostawca obsługuje `New-ItemProperty` polecenie cmdlet dostawcy. To polecenie cmdlet umożliwia użytkownikowi utworzenie nowej właściwości i ustawienie jej wartości.

- Metody [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) i [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) definiują sposób dostawca obsługuje `Remove-ItemProperty` polecenie cmdlet. To polecenie cmdlet umożliwia użytkownikowi usunięcie właściwości i jej wartości.

- Metody [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) i [System. Management. Automation. Provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) definiują sposób dostawca obsługuje `Rename-ItemProperty` polecenie cmdlet. To polecenie cmdlet umożliwia użytkownikowi zmianę nazwy właściwości.

## <a name="see-also"></a>Zobacz też

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Pisanie dostawcy środowiska Windows PowerShell](./writing-a-windows-powershell-provider.md)
