---
title: Tworzenie dostawcy kontenera Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: de75e19abc0ee440e724fba7bf578ce240fbf2df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795457"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Tworzenie dostawcy kontenerów programu Windows PowerShell

W tym temacie opisano sposób tworzenia dostawcy środowiska Windows PowerShell, którego można używać w magazynach danych wielowarstwową. Dla tego typu magazynu danych najwyższy poziom magazynu zawiera elementy katalogu głównego, a każdy kolejnych poziom jest określany jako węzeł elementów podrzędnych. Przez umożliwienie użytkownikowi pracować nad tych węzłów podrzędnych, użytkownik może wchodzić hierarchicznie przez Magazyn danych.

Dostawców, którzy mogą pracować na magazyny danych wielopoziomowe są określane jako dostawcy kontenera programu Windows PowerShell. Należy jednak pamiętać, że dostawcy kontenera programu Windows PowerShell, mogą być używane tylko wtedy, gdy jeden kontener (nie zagnieżdżone kontenery) przy użyciu elementów. W przypadku zagnieżdżone kontenery należy zaimplementować dostawcę nawigacji programu Windows PowerShell. Aby uzyskać więcej informacji na temat implementowania dostawcy nawigacji programu Windows PowerShell, zobacz [tworzenia dostawcy usługi Windows PowerShell nawigacji](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Możesz pobrać C# pliku źródłowego (AccessDBSampleProvider04.cs) dla tego dostawcy, za pomocą programu Microsoft Windows oprogramowania Development Kit dla Windows Vista i składników środowiska uruchomieniowego programu .NET Framework 3.0. Aby uzyskać instrukcje pobierania, zobacz [jak instalowanie programu Windows PowerShell i pobierania zestawu SDK programu Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Pliki pobrane źródło są dostępne w  **\<przykłady programu PowerShell >** katalogu.
>
> Aby uzyskać więcej informacji na temat innych implementacji dostawcy środowiska Windows PowerShell, zobacz [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md).

Dostawcy kontenera programu Windows PowerShell, które są opisane w tym miejscu definiuje bazy danych jako jej jeden kontener za pomocą tabel i wiersze obiektu bazy danych, zdefiniowane jako elementy kontenera.

> [!CAUTION]
> Należy pamiętać, zakłada, że ten projekt bazy danych, które zawiera pole o identyfikatorze nazwa i typ pola to LongInteger.

Oto lista sekcje w tym temacie. Jeśli nie jesteś zaznajomiony z pisaniem dostawcy kontenera programu Windows PowerShell, zapoznaj się z tych informacji w kolejności, która wygląda na to. Jednak jeśli i dopiero zaczynasz pisanie dostawcy kontenera programu Windows PowerShell, przejdź bezpośrednio do potrzebnych informacji.

- [Definiowanie klasy dostawcy kontenera Windows PowerShell](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Definiowanie podstawowe funkcje](#defining-base-functionality)

- [Trwa pobieranie elementów podrzędnych](#Retrieving-Child-Items)

- [Dołączanie parametrów dynamicznych do `Get-ChildItem` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Podczas pobierania nazw elementów podrzędnych](#Retrieving-Child-Item-Names)

- [Dołączanie parametrów dynamicznych do `Get-ChildItem` polecenia Cmdlet (nazwa)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Zmienianie nazw elementów](#Renaming-Items)

- [Dołączanie parametrów dynamicznych do `Rename-Item` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Tworzenie nowych elementów](#Creating-New-Items)

- [Dołączanie parametrów dynamicznych do `New-Item` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Usuwanie elementów](#Removing-Items)

- [Dołączanie parametrów dynamicznych do `Remove-Item` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Wykonywanie zapytań dotyczących elementów podrzędnych](#Querying-for-Child-Items)

- [Kopiowaniu elementów](#Copying-Items)

- [Dołączanie parametrów dynamicznych do `Copy-Item` polecenia Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Przykładowy kod](#Code-Sample)

- [Tworzenie dostawcy programu Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Testowanie dostawcy programu Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definiowanie klasy dostawcy kontenera Windows PowerShell

Dostawcy kontenera programu Windows PowerShell, należy zdefiniować klasę .NET, która pochodzi od klasy [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy bazowej. Poniżej przedstawiono w definicji klasy dla dostawcy kontenera programu Windows PowerShell, które są opisane w tej sekcji.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Należy zauważyć, że w tej definicji klasy [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atrybut zawiera dwa parametry. Pierwszy parametr określa przyjazną dla użytkownika nazwę dostawcy, który jest używany przez program Windows PowerShell. Drugi parametr określa specyficzne możliwości programu Windows PowerShell, które dostawca udostępnia do środowiska wykonawczego programu Windows PowerShell podczas przetwarzania polecenia. Dla tego dostawcy istnieją nie konkretne funkcje programu Windows PowerShell, które są dodawane.

## <a name="defining-base-functionality"></a>Definiowanie podstawowe funkcje

Zgodnie z opisem w [projektowania Your Windows PowerShell dostawcy](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasa pochodzi od innych klas, które podano funkcje innego dostawcy. Dostawcy kontenera programu Windows PowerShell, w związku z tym, musi zdefiniować wszystkie funkcje udostępniane przez te klasy.

Aby zaimplementować funkcje dodawania informacji specyficznych dla sesji inicjowania i zwalniania zasobów, które są używane przez dostawcę, zobacz [tworzenia podstawowego dostawcy programu PowerShell Windows](./creating-a-basic-windows-powershell-provider.md). Jednak większość dostawców (w tym dostawcy opisane w tym miejscu) można użyć Domyślna implementacja tej funkcji, które są dostarczane przez środowisko Windows PowerShell.

Aby uzyskać dostęp do magazynu danych, dostawca musi implementować metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy dysk programu Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Do modyfikowania elementów magazynu danych, takich jak wprowadzenie, ustawienia i czyszczenie elementów, dostawca musi implementować metod dostarczonych przez [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy bazowej. Aby uzyskać więcej informacji na temat implementowania tych metod, zobacz [Tworzenie dostawcy usługi Windows PowerShell elementu](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Trwa pobieranie elementów podrzędnych

Aby pobrać element podrzędny, należy zastąpić dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metody w celu obsługi wywołania z `Get-ChildItem` polecenia cmdlet. Ta metoda umożliwia pobranie elementów podrzędnych z magazynu danych i zapisuje je do potoku jako obiekty. Jeśli `recurse` parametru polecenia cmdlet jest określony, metoda pobiera wszystkie elementy podrzędne, niezależnie od tego, jaki poziom znajdują się w. Jeśli `recurse` parametr nie zostanie określony, metoda pobiera tylko jeden poziom elementów podrzędnych.

Oto implementacja [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metody dla tego dostawcy. Należy zauważyć, że ta metoda umożliwia pobranie podrzędnych elementów we wszystkich tabelach bazy danych po ścieżce wskazuje bazy danych programu Access, a następnie pobiera elementy podrzędne z wiersze tej tabeli, jeśli ścieżka wskazuje tabeli danych.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Warto zapamiętać o implementowaniu GetChildItems

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Podczas definiowania klasy dostawcy, dostawcy kontenera programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Implementacja tej metody należy wziąć pod uwagę dowolnego rodzaju dostępu do elementu, że element jest widoczny dla użytkownika. Na przykład, jeśli użytkownik ma dostęp do zapisu do pliku za pośrednictwem dostawcy systemu plików (dostarczonych przez program Windows PowerShell), ale nie dostęp do odczytu, plik nadal istnieje i [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) zwraca `true`. Wdrożenie może wymagać sprawdzenia elementu nadrzędnego, dziecka mogą być wyliczane.

- Podczas zapisywania wielu elementów [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metoda może zająć trochę czasu. Można zaprojektować dostawcą, aby zapisać elementów za pomocą [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metodą w danym momencie. Przy użyciu tej metody spowoduje wyświetlenie elementów do użytkownika w strumieniu.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) jest odpowiedzialny za przypadku łączy cyklicznych i podobnych, co uniemożliwia nieskończoną rekursję. Odpowiednie kończący należy zgłosić wyjątek do uwzględnienia tych warunków.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Get-ChildItem

Czasami `Get-ChildItem` polecenia cmdlet, który wywołuje [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, należy zaimplementować dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Get-ChildItem` polecenia cmdlet.

Ten dostawca kontenera programu Windows PowerShell nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Podczas pobierania nazw elementów podrzędnych

Aby pobrać nazwy elementów podrzędnych, należy zastąpić dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metody w celu obsługi wywołania z `Get-ChildItem`polecenia cmdlet podczas jego `Name` określono parametr. Ta metoda umożliwia pobranie nazwy elementów podrzędnych dla określonej nazwy elementu ścieżkę lub podrzędny wszystkich kontenerów, jeśli `returnAllContainers` określono parametr polecenia cmdlet. Nazwa podrzędnej jest częścią liścia ścieżki. Na przykład nazwę podrzędnej c:\windows\system32\abc.dll ścieżki to "abc.dll". Nazwa podrzędnej c:\windows\system32 katalogu jest "system32".

Oto implementacja [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metody dla tego dostawcy. Należy zauważyć, że metoda pobiera nazwy tabel, jeśli określona ścieżka wskazuje bazy danych programu Access (dysku) i numery wierszy, jeśli ścieżka wskazuje tabelę.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Warto zapamiętać o implementowaniu GetChildNames

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Podczas definiowania klasy dostawcy, dostawcy kontenera programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

  > [!NOTE]
  > Wyjątkiem od tej reguły występuje, gdy `returnAllContainers` określono parametr polecenia cmdlet. W tym przypadku metoda Pobierz dowolną nazwę podrzędnych dla kontenera, nawet jeśli nie odpowiada wartości [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), lub [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) właściwości.

- Domyślnie przesłonięcia tej metody nie powinna pobrać nazwy obiektów, które zazwyczaj są ukryte przed użytkownikiem, chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) określono właściwości. Jeśli określona ścieżka wskazuje kontener [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość nie jest wymagane.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) jest odpowiedzialny za przypadku łączy cyklicznych i podobnych, co uniemożliwia nieskończoną rekursję. Odpowiednie kończący należy zgłosić wyjątek do uwzględnienia tych warunków.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Get-ChildItem (nazwa)

Czasami `Get-ChildItem` polecenia cmdlet (przy użyciu `Name` parametr) wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, należy zaimplementować dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metody. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Get-ChildItem` polecenia cmdlet.

Ten dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Zmienianie nazw elementów

Aby zmienić nazwę elementu, należy zastąpić dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metody w celu obsługi wywołania z `Rename-Item` polecenia cmdlet. Ta metoda zmiany nazwy elementu w określonej ścieżce na nową nazwę, pod warunkiem. Nowa nazwa musi być zawsze względem elementu nadrzędnego (kontenera).

Ten dostawca nie zastępuje [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metody. Jednakże Oto domyślną implementację.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Warto zapamiętać o implementowaniu RenameItem

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Podczas definiowania klasy dostawcy, dostawcy kontenera programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metoda jest przeznaczona do zmiany nazwy elementu tylko, a nie operacji przenoszenia. Implementacja metody powinien zapisać błąd, jeśli `newName` parametr zawiera separatorami ścieżki lub w przeciwnym razie może spowodować element, aby zmienić jego lokalizacji nadrzędnej.

- Domyślnie przesłonięcia tej metody powinna nie zmianę nazw obiektów chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) określono właściwości. Jeśli określona ścieżka wskazuje kontener [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość nie jest wymagane.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Ta metoda jest używana, aby potwierdzić wykonanie operacji, podczas wprowadzania zmian do stanu systemu, na przykład zmiana nazw plików. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wysyła nazwę zasobu był zmieniany na użytkownika, ze środowiskiem uruchomieniowym programu Windows PowerShell, biorąc pod uwagę wszystkie ustawienia wiersza polecenia lub zmienne preferencji w Określanie, co powinno być wyświetlane.

  Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metody. Ta metoda wysyła komunikat potwierdzenia dla użytkownika, aby zezwolić na dodatkową opinię powiedzieć, jeśli operacja powinna być kontynuowana. Dostawca powinien wywoływać [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) jako dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Zmień nazwę elementu

Czasami `Rename-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, programu Windows PowerShell kontenera dostawca musi implementować [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metody. Ta metoda pobiera parametry dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Rename-Item` polecenia cmdlet.

Ten dostawca kontenera nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Tworzenie nowych elementów

Aby utworzyć nowe elementy, należy zaimplementować dostawcy kontenera [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metody w celu obsługi wywołania z `New-Item` polecenia cmdlet. Ta metoda tworzy element danych znajdujących się w określonej ścieżce. `type` Parametru polecenia cmdlet zawiera typ zdefiniowany przez dostawcę dla nowego elementu. Na przykład używa dostawcy FileSystem `type` parametru o wartości "file" lub "directory". `newItemValue` Parametru polecenia cmdlet określa wartość specyficzne dla dostawcy dla nowego elementu.

Oto implementacja [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metody dla tego dostawcy.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Warto zapamiętać o implementowaniu NewItem

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoda powinna dokonać porównania bez uwzględniania wielkości przekazany ciąg `type` parametru. Powinien także zezwalać na co najmniej niejednoznaczne dopasowania. Na przykład dla typów "file" i "directory", tylko pierwsza litera jest wymagany do odróżniania. Jeśli `type` parametr wskazuje typ dostawcy nie można utworzyć, [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoda powinien zapisać ArgumentException komunikatem wskazujący typy można utworzyć dostawcy.

- Aby uzyskać `newItemValue` parametr, wdrażanie [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoda jest zalecana do akceptowania ciągów co najmniej. Typ obiektu, który jest pobierany przez powinien również akceptować [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metodę dla tej samej ścieżce. [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoda może używać [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) metodę, aby przekonwertować typy do żądany typ.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca wartość true, [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) Metoda powinna wywoływać [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodę jako dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet nowy element

Czasami `New-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, dostawca kontenera musi implementować [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) metody. Ta metoda pobiera parametry dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `New-Item` polecenia cmdlet.

Ten dostawca nie implementuje tej metody. Jednakże poniższy kod jest domyślna implementacja tej metody.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Usuwanie elementów

Aby usunąć elementy, należy zastąpić dostawcy programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metody w celu obsługi wywołania z `Remove-Item` polecenia cmdlet. Ta metoda usuwa element z magazynu danych w określonej ścieżce. Jeśli `recurse` parametru `Remove-Item` polecenia cmdlet jest ustawiona na `true`, metoda usuwa wszystkie elementy podrzędne, niezależnie od ich poziomu. Jeśli parametr jest ustawiony na `false`, metoda usuwa tylko jeden element w określonej ścieżce.

Ten dostawca nie obsługuje usuwania elementu. Jednakże, poniższy kod jest domyślna Implementacja klasy [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Warto zapamiętać o implementowaniu RemoveItem

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Podczas definiowania klasy dostawcy, dostawcy kontenera programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie należy usuwać obiektów chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na wartość true. Jeśli określona ścieżka wskazuje kontener [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość nie jest wymagane.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) jest odpowiedzialny za przypadku łączy cyklicznych i podobnych, co uniemożliwia nieskończoną rekursję. Odpowiednie kończący należy zgłosić wyjątek do uwzględnienia tych warunków.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca `true`, [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodę jako dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Remove element

Czasami `Remove-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, dostawca kontenera musi implementować [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metodę, aby obsługiwać te parametry. Ta metoda pobiera parametry dynamiczne dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Remove-Item` polecenia cmdlet.

Ten dostawca kontenera nie implementuje tej metody. Jednakże, poniższy kod jest domyślna Implementacja klasy [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Wykonywanie zapytań dotyczących elementów podrzędnych

Aby sprawdzić, czy elementy podrzędne istnieją w określonej ścieżce, musisz przesłonić dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metody. Ta metoda zwraca `true` Jeśli element ma elementy podrzędne, a `false` inaczej. Dla ścieżki o wartości null ani być pusta, metoda uwzględnia wszystkie elementy w magazynie danych jako elementy podrzędne i zwraca `true`.

Poniżej przedstawiono zastąpienie dla [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metody. Jeśli istnieje więcej niż dwóch części ścieżki tworzone przez metodę pomocnika ChunkPath, metoda zwraca `false`, ponieważ tylko kontenerach bazy danych i tabeli są zdefiniowane. Aby uzyskać więcej informacji na temat tej metody pomocnika, zobacz metodę ChunkPath została omówiona w [tworzenia dostawcy usługi Windows PowerShell elementu](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Warto zapamiętać o implementowaniu HasChildItems

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Jeśli dostawcy kontenera udostępnia głównego, zawierający interesujących punktów instalacji, implementacja [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metoda powinna zwrócić `true`po o wartości null lub pusty ciąg jest przekazywana do ścieżki.

## <a name="copying-items"></a>Kopiowanie elementów

Aby skopiować elementy, należy zaimplementować dostawcy kontenera [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metody w celu obsługi wywołania z `Copy-Item` polecenia cmdlet. Ta metoda kopiuje element danych z lokalizacji wskazanej przez `path` parametru polecenia cmdlet do lokalizacji wskazanej przez `copyPath` parametru. Jeśli `recurse` parametr jest określony, metoda kopiuje wszystkich kontenerów podrzędnych. Jeśli nie określono parametrów, metody Kopiuje jeden poziom elementów.

Ten dostawca nie implementuje tej metody. Jednakże, poniższy kod jest domyślna Implementacja klasy [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Warto zapamiętać o implementowaniu CopyItem

Następujące warunki mogą dotyczyć implementacji [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Podczas definiowania klasy dostawcy, dostawcy kontenera programu Windows PowerShell może deklarować możliwości dostawcy ExpandWildcards, filtr, Dołącz lub Wyklucz, z [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) wyliczenia. W takich przypadkach wykonania [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metoda musi upewnij się, że ścieżka przekazywany do metody spełnia wymagania określonego możliwości. Aby to zrobić, metoda powinien uzyskiwać dostęp do odpowiedniej właściwości, na przykład, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) i [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) właściwości.

- Domyślnie przesłonięcia tej metody nie należy kopiować obiekty za pośrednictwem istniejących obiektów chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Na przykład dostawcy FileSystem nie skopiuje c:\temp\abc.txt przez istniejący plik c:\abc.txt chyba że [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość jest ustawiona na `true`. Jeśli ścieżka określona w `copyPath` parametru istnieje i wskazuje kontener [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) właściwość nie jest wymagane. W tym przypadku [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) należy skopiować element wskazywany przez `path` parametru do kontenera wskazywanym przez `copyPath` parametr jako element podrzędny.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) jest odpowiedzialny za przypadku łączy cyklicznych i podobnych, co uniemożliwia nieskończoną rekursję. Odpowiednie kończący należy zgłosić wyjątek do uwzględnienia tych warunków.

- Implementacja [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) powinny wywoływać metodę [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) i sprawdź wartość zwracaną przed wprowadzeniem jakichkolwiek zmian w magazynie danych. Po wywołaniu [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) zwraca wartość true, [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) Metoda powinna wywoływać [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metodę jako dodatkowe sprawdzenie modyfikacji potencjalnie niebezpiecznych systemu. Aby uzyskać więcej informacji na temat wywoływanie tych metod, zobacz [zmiany nazwy elementów](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Dołączanie parametrów dynamicznych do polecenia cmdlet Copy-Item

Czasami `Copy-Item` polecenie cmdlet wymaga dodatkowych parametrów, które są określone dynamicznie w czasie wykonywania. Aby zapewnić te parametry dynamiczne, należy zaimplementować dostawcy kontenera programu Windows PowerShell [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metody, aby obsłużyć te Parametry. Ta metoda pobiera parametry dla elementu w ścieżce wskazany i zwraca obiekt zawierający właściwości i pola za pomocą analizy atrybuty podobna do klasy polecenia cmdlet lub [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) obiektu. Środowisko wykonawcze programu Windows PowerShell korzysta zwrócony obiekt można dodać parametry do `Copy-Item` polecenia cmdlet.

Ten dostawca nie implementuje tej metody. Jednakże, poniższy kod jest domyślna Implementacja klasy [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Przykładowy kod

Aby uzyskać kompletny przykładowy kod, zobacz [przykładowy kod AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Tworzenie dostawcy programu Windows PowerShell

Zobacz [sposobu rejestrowania poleceń cmdlet, dostawców i hostowanie aplikacji](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testowanie dostawcy programu Windows PowerShell

Jeśli Twój dostawca programu Windows PowerShell został zarejestrowany za pomocą programu Windows PowerShell, można ją przetestować, uruchamiając obsługiwanych poleceń cmdlet w wierszu polecenia. Należy pamiętać, że następujące przykładowe dane wyjściowe korzysta z fikcyjnych dostępu do bazy danych.

1. Uruchom `Get-ChildItem` polecenie cmdlet do pobierania listy elementów podrzędnych z tabeli Klienci w bazie danych programu Access.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   Zostanie wyświetlone następujące dane wyjściowe.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Uruchom `Get-ChildItem` polecenie cmdlet ponownie, aby pobrać dane z tabeli.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   Zostanie wyświetlone następujące dane wyjściowe.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Teraz za pomocą `Get-Item` polecenie cmdlet do pobierania elementów w wierszu 0 w tabeli danych.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   Zostanie wyświetlone następujące dane wyjściowe.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Ponowne użycie `Get-Item` można pobrać danych dla elementów w wierszu 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   Zostanie wyświetlone następujące dane wyjściowe.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Teraz za pomocą `New-Item` polecenia cmdlet, aby dodać wiersz do istniejącej tabeli. `Path` Parametr określa pełną ścieżkę do wiersza i musi wskazywać, numer wiersza jest większa niż liczba istniejących wierszy w tabeli. `Type` Parametr wskazuje "wiersz", aby określić typu elementu Dodawanie. Na koniec `Value` parametr określa rozdzielana przecinkami lista wartości kolumn dla wiersza.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAdress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Sprawdź poprawność nowej operacji elementu w następujący sposób.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   Zostanie wyświetlone następujące dane wyjściowe.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Zobacz też

[Tworzenie programu Windows PowerShell dostawców](./how-to-create-a-windows-powershell-provider.md)

[Projektowanie dostawcą Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementowanie dostawcy elementu Windows PowerShell](./creating-a-windows-powershell-item-provider.md)

[Implementowanie dostawcy nawigacji Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)

[Windows PowerShell przewodnik](./windows-powershell-programmer-s-guide.md)