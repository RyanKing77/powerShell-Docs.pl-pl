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
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734717"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="8241d-102">Pisanie dostawcy elementów</span><span class="sxs-lookup"><span data-stu-id="8241d-102">Writing an item provider</span></span>

<span data-ttu-id="8241d-103">W tym temacie opisano sposób implementacji metody dostawcy środowiska Windows PowerShell, które dostępu i manipulowania elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="8241d-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="8241d-104">Aby móc uzyskiwać dostęp do elementów, dostawca musi pochodzić od klasy [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8241d-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="8241d-105">Dostawca w przykładach w niniejszym temacie używa bazy danych programu Access, jako jego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="8241d-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="8241d-106">Istnieje kilka metod pomocniczych i klas, które są używane do interakcji z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="8241d-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="8241d-107">Aby uzyskać pełny przykład, który zawiera metody pomocnicze, zobacz [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="8241d-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="8241d-108">Aby uzyskać więcej informacji na temat dostawcy programu Windows PowerShell, zobacz [Przegląd dostawcy programu Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8241d-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="8241d-109">Implementacja metody elementu</span><span class="sxs-lookup"><span data-stu-id="8241d-109">Implementing item methods</span></span>

<span data-ttu-id="8241d-110">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasa udostępnia kilka metod, które może służyć do uzyskiwania dostępu i manipulowania elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="8241d-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="8241d-111">Aby uzyskać pełną listę tych metod, zobacz [metody ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="8241d-111">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span></span> <span data-ttu-id="8241d-112">W tym przykładzie wprowadzimy cztery z tych metod.</span><span class="sxs-lookup"><span data-stu-id="8241d-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="8241d-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) pobiera element w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8241d-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="8241d-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) ustawia wartość określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="8241d-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="8241d-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) sprawdza, czy element istnieje w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8241d-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="8241d-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) sprawdza ścieżkę, aby zobaczyć, jeśli jest on mapowany do lokalizacji w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="8241d-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="8241d-117">Ten temat opiera się na informacje zawarte w [szybkiego startu programu Windows PowerShell dostawcy](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="8241d-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="8241d-118">W tym temacie nie opisano podstawowe informacje dotyczące sposobu konfigurowania projektu dostawcy lub odziedziczony sposobie implementacji metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasę, która tworzenie i usuwanie dysków.</span><span class="sxs-lookup"><span data-stu-id="8241d-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="8241d-119">Deklarowanie klasy dostawcy</span><span class="sxs-lookup"><span data-stu-id="8241d-119">Declaring the provider class</span></span>

<span data-ttu-id="8241d-120">Zadeklaruj dostawcę aby dziedziczyć [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy, a następnie ją za pomocą dekoracji [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="8241d-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="8241d-121">Implementowanie GetItem</span><span class="sxs-lookup"><span data-stu-id="8241d-121">Implementing GetItem</span></span>

<span data-ttu-id="8241d-122">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) jest wywoływana przez aparatu programu PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) polecenie cmdlet na Twój dostawca.</span><span class="sxs-lookup"><span data-stu-id="8241d-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="8241d-123">Metoda ta zwraca element w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8241d-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="8241d-124">W tym przykładzie bazy danych programu Access metoda sprawdza, czy element jest dysk i tabelę w bazie danych lub wiersz w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8241d-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="8241d-125">Metoda wysyła elementu do aparatu programu PowerShell przez wywołanie metody [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metody.</span><span class="sxs-lookup"><span data-stu-id="8241d-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="8241d-126">Implementowanie SetItem</span><span class="sxs-lookup"><span data-stu-id="8241d-126">Implementing SetItem</span></span>

<span data-ttu-id="8241d-127">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoda jest wywoływana przez wywołania aparatu programu PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8241d-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="8241d-128">Ustawia wartość elementu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8241d-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="8241d-129">W tym przykładzie dostęp do bazy danych warto ustawić wartość elementu tylko wtedy, gdy dany element wiersz, więc metoda zgłasza [wyjątek NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) Jeśli element nie jest wiersz.</span><span class="sxs-lookup"><span data-stu-id="8241d-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="8241d-130">Implementowanie ItemExists</span><span class="sxs-lookup"><span data-stu-id="8241d-130">Implementing ItemExists</span></span>

<span data-ttu-id="8241d-131">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metoda jest wywoływana przez aparatu programu PowerShell, gdy użytkownik wywołuje [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8241d-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="8241d-132">Metoda określa, czy istnieje element w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8241d-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="8241d-133">Jeśli element istnieje, metoda przekazuje ją do aparatu programu PowerShell przez wywołanie metody [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="8241d-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="8241d-134">Implementowanie IsValidPath</span><span class="sxs-lookup"><span data-stu-id="8241d-134">Implementing IsValidPath</span></span>

<span data-ttu-id="8241d-135">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metoda sprawdza, czy podana ścieżka jest syntaktycznie prawidłowy dla bieżącego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="8241d-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="8241d-136">Nie sprawdza, czy element istnieje w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8241d-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="8241d-137">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8241d-137">Next steps</span></span>

<span data-ttu-id="8241d-138">Typowe dostawcy rzeczywistych jest w stanie, obsłudze elementów, które zawierają inne elementy oraz przenoszenie elementów z jednej ścieżki do innej na dysku.</span><span class="sxs-lookup"><span data-stu-id="8241d-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="8241d-139">Na przykład dostawcę, który obsługuje kontenery zobacz [pisanie dostawcy kontenera](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8241d-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="8241d-140">Na przykład dostawca, który obsługuje przenoszenie elementów zobacz [pisanie dostawcy nawigacji](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8241d-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8241d-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8241d-141">See Also</span></span>

[<span data-ttu-id="8241d-142">Pisanie dostawcy kontenera</span><span class="sxs-lookup"><span data-stu-id="8241d-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="8241d-143">Pisanie dostawcy nawigacji</span><span class="sxs-lookup"><span data-stu-id="8241d-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="8241d-144">Przegląd dostawcy programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="8241d-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
