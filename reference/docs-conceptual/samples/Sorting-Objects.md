---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Sortowanie obiektów
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030768"
---
# <a name="sorting-objects"></a><span data-ttu-id="542af-103">Sortowanie obiektów</span><span class="sxs-lookup"><span data-stu-id="542af-103">Sorting Objects</span></span>

<span data-ttu-id="542af-104">Firma Microsoft można organizować wyświetlanych danych, aby ułatwić skanowania za pomocą `Sort-Object` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="542af-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="542af-105">`Sort-Object` pobiera nazwę jedną lub więcej właściwości, które ma być wykonywane sortowanie i zwraca dane posortowane według wartości tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="542af-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="542af-106">Sortowanie podstawowe</span><span class="sxs-lookup"><span data-stu-id="542af-106">Basic sorting</span></span>

<span data-ttu-id="542af-107">Należy wziąć pod uwagę ten problem, wyświetlanie podkatalogów i plików w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="542af-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="542af-108">Jeśli chcemy posortować według **LastWriteTime** a następnie według **nazwa**, możemy to zrobić, wpisując:</span><span class="sxs-lookup"><span data-stu-id="542af-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="542af-109">Możesz również obiekty można sortować w kolejności odwrotnej, określając **Descending** parametr przełącznika.</span><span class="sxs-lookup"><span data-stu-id="542af-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="542af-110">Przy użyciu tabel skrótów</span><span class="sxs-lookup"><span data-stu-id="542af-110">Using hash tables</span></span>

<span data-ttu-id="542af-111">Inne właściwości w różnej kolejności można sortować przy użyciu tabel skrótów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="542af-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="542af-112">Każda tabela skrótów używa **wyrażenie** klawisz, aby określić nazwę właściwości jako ciąg i **rosnąco** lub **Descending** klawisz, aby określić kolejność sortowania według `$true` lub `$false`.</span><span class="sxs-lookup"><span data-stu-id="542af-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="542af-113">**Wyrażenie** klucz jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="542af-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="542af-114">**Ascending** lub **Descending** klucz jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="542af-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="542af-115">Poniższy przykład sortuje obiektów w malejącej **LastWriteTime** kolejności i rosnącej **nazwa** zamówienia.</span><span class="sxs-lookup"><span data-stu-id="542af-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="542af-116">Można również ustawić scriptblock **wyrażenie** klucza.</span><span class="sxs-lookup"><span data-stu-id="542af-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="542af-117">Podczas uruchamiania `Sort-Object` polecenia cmdlet, jest wykonywany blok skryptu, a wynik jest używane do sortowania.</span><span class="sxs-lookup"><span data-stu-id="542af-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="542af-118">Poniższy przykład sortuje obiekty w kolejności malejącej według przedział czasu między **CreationTime** i **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="542af-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="542af-119">Porady</span><span class="sxs-lookup"><span data-stu-id="542af-119">Tips</span></span>

<span data-ttu-id="542af-120">Możesz pominąć **właściwość** Nazwa parametru jako pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="542af-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="542af-121">Ponadto możesz zapoznać się z `Sort-Object` przez jego wbudowanych aliasu `sort`:</span><span class="sxs-lookup"><span data-stu-id="542af-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="542af-122">Klucze w tabelach skrótów do sortowania można stosować skrót, jako pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="542af-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="542af-123">W tym przykładzie **e** oznacza **wyrażenie**, **d** oznacza **Descending**i **a** oznacza **rosnąco**.</span><span class="sxs-lookup"><span data-stu-id="542af-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="542af-124">Aby poprawić czytelność, możesz umieścić tabel skrótów do oddzielnych zmiennej:</span><span class="sxs-lookup"><span data-stu-id="542af-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
