---
title: Pisanie dostawcy nawigacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: f449c17e4c373c42f8a1d96fa9075940111c65bc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056597"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="8ed15-102">Pisanie dostawcy nawigacji</span><span class="sxs-lookup"><span data-stu-id="8ed15-102">Writing a navigation provider</span></span>

<span data-ttu-id="8ed15-103">W tym temacie opisano sposób implementacji metody dostawcy środowiska Windows PowerShell, które obsługuje zagnieżdżone kontenery (magazyny danych wielopoziomowe), przenoszenie elementów i ścieżek względnych.</span><span class="sxs-lookup"><span data-stu-id="8ed15-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="8ed15-104">Dostawca nawigacji muszą pochodzić od [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8ed15-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="8ed15-105">Dostawca w przykładach w niniejszym temacie używa bazy danych programu Access, jako jego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="8ed15-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="8ed15-106">Istnieje kilka metod pomocniczych i klas, które są używane do interakcji z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="8ed15-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="8ed15-107">Aby uzyskać pełny przykład, który zawiera metody pomocnicze, zobacz [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="8ed15-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="8ed15-108">Aby uzyskać więcej informacji na temat dostawcy programu Windows PowerShell, zobacz [Przegląd dostawcy programu Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ed15-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="8ed15-109">Implementowanie metod nawigacji</span><span class="sxs-lookup"><span data-stu-id="8ed15-109">Implementing navigation methods</span></span>

<span data-ttu-id="8ed15-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasa implementuje metody, które obsługują zagnieżdżone kontenery, ścieżki względne i przenoszenie elementów.</span><span class="sxs-lookup"><span data-stu-id="8ed15-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="8ed15-111">Aby uzyskać pełną listę tych metod, zobacz [metody NavigationCmdletProvider](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="8ed15-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="8ed15-112">Ten temat opiera się na informacje zawarte w [szybkiego startu programu Windows PowerShell dostawcy](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="8ed15-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="8ed15-113">W tym temacie nie opisano podstawowe informacje dotyczące sposobu konfigurowania projektu dostawcy lub odziedziczony sposobie implementacji metody [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasę, która tworzenie i usuwanie dysków.</span><span class="sxs-lookup"><span data-stu-id="8ed15-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="8ed15-114">W tym temacie nie obejmują również sposób implementacji metod udostępnianych przez [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) lub [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8ed15-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="8ed15-115">Aby uzyskać przykład pokazujący sposób implementacji poleceń cmdlet elementów, zobacz [pisania dostawcę elementu](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8ed15-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="8ed15-116">Przykład pokazujący sposób implementacji poleceń cmdlet kontenera, zobacz [pisanie dostawcy kontenera](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8ed15-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="8ed15-117">Deklarowanie klasy dostawcy</span><span class="sxs-lookup"><span data-stu-id="8ed15-117">Declaring the provider class</span></span>

<span data-ttu-id="8ed15-118">Zadeklaruj dostawcę aby dziedziczyć [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy, a następnie ją za pomocą dekoracji [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="8ed15-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="8ed15-119">Implementowanie IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="8ed15-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="8ed15-120">[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metoda sprawdza, czy element w określonej ścieżce jest kontenerem.</span><span class="sxs-lookup"><span data-stu-id="8ed15-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="8ed15-121">Implementowanie GetChildName</span><span class="sxs-lookup"><span data-stu-id="8ed15-121">Implementing GetChildName</span></span>

<span data-ttu-id="8ed15-122">[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metoda pobiera właściwości name obiektu podrzędnego elementu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8ed15-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="8ed15-123">Jeśli element w określonej ścieżce nie jest elementem podrzędnym kontenera, ta metoda powinna zwrócić ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8ed15-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="8ed15-124">Implementowanie GetParentPath</span><span class="sxs-lookup"><span data-stu-id="8ed15-124">Implementing GetParentPath</span></span>

<span data-ttu-id="8ed15-125">[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoda pobiera ścieżkę elementu nadrzędnego elementu w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8ed15-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="8ed15-126">Jeśli element w określonej ścieżce katalogu głównego magazynu danych (tak, aby go nie ma elementu nadrzędnego), ta metoda powinna zwracać ścieżka katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="8ed15-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="8ed15-127">Implementowanie makepath —</span><span class="sxs-lookup"><span data-stu-id="8ed15-127">Implementing MakePath</span></span>

<span data-ttu-id="8ed15-128">[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metoda dołącza ścieżka określonego elementu nadrzędnego i określony podrzędny można utworzyć ścieżkę wewnętrzna dostawcy (informacje o ścieżce typy, które dostawców może obsługiwać, zobacz [Przegląd dostawcy programu Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ed15-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="8ed15-129">Aparat programu PowerShell wywołuje tę metodę, gdy użytkownik wywołuje [ścieżki Microsoft.PowerShell.Commands.Join](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ed15-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="8ed15-130">Implementing NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="8ed15-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="8ed15-131">[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metoda przyjmuje `path` i `basepath` parametrów i zwraca ścieżkę znormalizowaną, który jest odpowiednikiem `path`parametr i względem `basepath` parametru.</span><span class="sxs-lookup"><span data-stu-id="8ed15-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="8ed15-132">Implementowanie MoveItem</span><span class="sxs-lookup"><span data-stu-id="8ed15-132">Implementing MoveItem</span></span>

<span data-ttu-id="8ed15-133">[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metoda przenosi elementu z określonej ścieżki do określona ścieżka docelowa.</span><span class="sxs-lookup"><span data-stu-id="8ed15-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="8ed15-134">Aparat programu PowerShell wywołuje tę metodę, gdy użytkownik wywołuje [elementu Microsoft.PowerShell.Commands.Move](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ed15-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="8ed15-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ed15-135">See Also</span></span>

[<span data-ttu-id="8ed15-136">Pisanie dostawcy kontenera</span><span class="sxs-lookup"><span data-stu-id="8ed15-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="8ed15-137">Przegląd dostawcy programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="8ed15-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)