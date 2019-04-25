---
title: Pisanie dostawcy elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080819"
---
# <a name="writing-an-item-provider"></a>Pisanie dostawcy elementów

W tym temacie opisano sposób implementacji metody dostawcy środowiska Windows PowerShell, które dostępu i manipulowania elementów w magazynie danych. Aby móc uzyskiwać dostęp do elementów, dostawca musi pochodzić od klasy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.

Dostawca w przykładach w niniejszym temacie używa bazy danych programu Access, jako jego magazynu danych. Istnieje kilka metod pomocniczych i klas, które są używane do interakcji z bazą danych. Aby uzyskać pełny przykład, który zawiera metody pomocnicze, zobacz [AccessDBProviderSample03](./accessdbprovidersample03.md)

Aby uzyskać więcej informacji na temat dostawcy programu Windows PowerShell, zobacz [Przegląd dostawcy programu Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementacja metody elementu

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasa udostępnia kilka metod, które może służyć do uzyskiwania dostępu i manipulowania elementów w magazynie danych. Aby uzyskać pełną listę tych metod, zobacz [metody ItemCmdletProvider](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). W tym przykładzie wprowadzimy cztery z tych metod. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pobiera element w określonej ścieżce. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) ustawia wartość określonego elementu. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) sprawdza, czy element istnieje w określonej ścieżce. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) sprawdza ścieżkę, aby zobaczyć, jeśli jest on mapowany do lokalizacji w magazynie danych.

> [!NOTE]
> Ten temat opiera się na informacje zawarte w [szybkiego startu programu Windows PowerShell dostawcy](./windows-powershell-provider-quickstart.md). W tym temacie nie opisano podstawowe informacje dotyczące sposobu konfigurowania projektu dostawcy lub odziedziczony sposobie implementacji metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasę, która tworzenie i usuwanie dysków.

### <a name="declaring-the-provider-class"></a>Deklarowanie klasy dostawcy

Zadeklaruj dostawcę aby dziedziczyć [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy, a następnie ją za pomocą dekoracji [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementowanie GetItem

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) jest wywoływana przez aparatu programu PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.Get elementu](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) polecenie cmdlet na użytkownika Dostawca. Metoda ta zwraca element w określonej ścieżce. W tym przykładzie bazy danych programu Access metoda sprawdza, czy element jest dysk i tabelę w bazie danych lub wiersz w bazie danych. Metoda wysyła elementu do aparatu programu PowerShell przez wywołanie metody [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metody.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementowanie SetItem

[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoda jest wywoływana przez wywołania aparatu programu PowerShell, gdy użytkownik wywołuje [elementu Microsoft.PowerShell.Commands.Set](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) polecenia cmdlet . Ustawia wartość elementu w określonej ścieżce.

W tym przykładzie dostęp do bazy danych warto ustawić wartość elementu tylko wtedy, gdy dany element wiersz, więc metoda zgłasza [wyjątek NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) Jeśli element nie jest wiersz.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementowanie ItemExists

[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metoda jest wywoływana przez aparatu programu PowerShell, gdy użytkownik wywołuje [ścieżki Microsoft.PowerShell.Commands.Test](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) polecenia cmdlet. Metoda określa, czy istnieje element w określonej ścieżce. Jeśli element istnieje, metoda przekazuje ją do aparatu programu PowerShell przez wywołanie metody [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementowanie IsValidPath

[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metoda sprawdza, czy podana ścieżka jest syntaktycznie prawidłowy dla bieżącego dostawcy. Nie sprawdza, czy element istnieje w ścieżce.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Następne kroki

Typowe dostawcy rzeczywistych jest w stanie, obsłudze elementów, które zawierają inne elementy oraz przenoszenie elementów z jednej ścieżki do innej na dysku. Na przykład dostawcę, który obsługuje kontenery zobacz [pisanie dostawcy kontenera](./writing-a-container-provider.md). Na przykład dostawca, który obsługuje przenoszenie elementów zobacz [pisanie dostawcy nawigacji](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Zobacz też

[Pisanie dostawcy kontenera](./writing-a-container-provider.md)

[Pisanie dostawcy nawigacji](./writing-a-navigation-provider.md)

[Przegląd dostawcy programu PowerShell Windows](./windows-powershell-provider-overview.md)