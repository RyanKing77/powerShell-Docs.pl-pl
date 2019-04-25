---
title: Rozszerzanie danych wyjściowych obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068168"
---
# <a name="extending-output-objects"></a><span data-ttu-id="e763b-102">Rozszerzanie obiektów danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="e763b-102">Extending Output Objects</span></span>

<span data-ttu-id="e763b-103">Możesz rozszerzyć obiektów .NET Framework, które są zwracane przez polecenia cmdlet, funkcji i skryptów przy użyciu typów plików (.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="e763b-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="e763b-104">Typy plików są plikami XML, umożliwiające dodawanie właściwości i metod do istniejących obiektów.</span><span class="sxs-lookup"><span data-stu-id="e763b-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="e763b-105">Na przykład programu Windows PowerShell udostępnia plik Types.ps1xml, który dodaje elementy do wielu istniejących obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e763b-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="e763b-106">Plik Types.ps1xml znajduje się w katalogu instalacyjnym programu Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="e763b-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="e763b-107">Można utworzyć własny plik typów, aby dodatkowo rozszerzać te obiekty, albo aby rozszerzyć innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="e763b-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="e763b-108">Rozszerzając obiektu przy użyciu pliku typów, dowolne wystąpienie obiektu jest rozszerzona o nowe elementy.</span><span class="sxs-lookup"><span data-stu-id="e763b-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="e763b-109">Rozszerzanie obiektu System.Array</span><span class="sxs-lookup"><span data-stu-id="e763b-109">Extending the System.Array Object</span></span>

<span data-ttu-id="e763b-110">W poniższym przykładzie pokazano, jak rozszerza środowisko Windows PowerShell [System.Array](/dotnet/api/System.Array) obiektu w pliku Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e763b-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="e763b-111">Domyślnie [System.Array](/dotnet/api/System.Array) obiekty mają `Length` właściwość, która wyświetla liczbę obiektów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e763b-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="e763b-112">Jednak ponieważ wyraźnie "długość nazwy" nie zawiera opisu właściwości, programu Windows PowerShell zwiększa `Count` alias właściwość, która wyświetla taką samą wartość jak `Length` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e763b-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="e763b-113">Dodaje następujący kod XML `Count` właściwości [System.Array](/dotnet/api/System.Array) typu.</span><span class="sxs-lookup"><span data-stu-id="e763b-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

<span data-ttu-id="e763b-114">Aby wyświetlić tej nowej właściwości alias, należy użyć [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) polecenia w dowolnej macierzy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e763b-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="e763b-115">Polecenie zwraca następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="e763b-115">The command returns the following results.</span></span>
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
<span data-ttu-id="e763b-116">Można użyć dowolnego `Count` właściwości lub `Length` właściwość, aby określić liczbę obiektów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e763b-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="e763b-117">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e763b-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="e763b-118">Niestandardowe typy plików</span><span class="sxs-lookup"><span data-stu-id="e763b-118">Custom Types Files</span></span>

<span data-ttu-id="e763b-119">Aby utworzyć plik niestandardowych typów, zacznij od skopiowania istniejący plik typów.</span><span class="sxs-lookup"><span data-stu-id="e763b-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="e763b-120">Nowy plik może mieć dowolną nazwę, ale musi mieć rozszerzenie nazwy pliku .ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e763b-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="e763b-121">Skopiuj plik, nowy plik zostanie umieszczony w dowolnym katalogu, który jest dostępny dla programu Windows PowerShell, ale warto umieścić pliki w katalogu instalacyjnym programu Windows PowerShell (`$pshome`) lub w podkatalogu katalogu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e763b-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="e763b-122">Aby dodać własne typy rozszerzonych do pliku, należy dodać element typy dla każdego obiektu, który ma zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="e763b-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="e763b-123">Przykłady można znaleźć w następujących tematach.</span><span class="sxs-lookup"><span data-stu-id="e763b-123">The following topics provide examples.</span></span>

- <span data-ttu-id="e763b-124">Aby uzyskać więcej informacji na temat dodawania właściwości i ustawia właściwość zobacz [właściwości rozszerzone](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="e763b-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="e763b-125">Aby uzyskać więcej informacji na temat dodawania metod, zobacz [rozszerzone metody](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="e763b-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="e763b-126">Aby uzyskać więcej informacji na temat dodawania zestawów elementów członkowskich, zobacz [rozszerzone zestawów elementów członkowskich](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="e763b-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="e763b-127">Po zdefiniowaniu typów rozszerzonej, użyj jedną z następujących metod udostępniania rozszerzonych obiektów:</span><span class="sxs-lookup"><span data-stu-id="e763b-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="e763b-128">Aby jednak udostępnić plik rozszerzone typy bieżącej sesji, należy użyć [TypeData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) polecenia cmdlet, aby dodać nowy plik.</span><span class="sxs-lookup"><span data-stu-id="e763b-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="e763b-129">Jeśli chcesz, aby typów na mają pierwszeństwo względem typów, które są zdefiniowane w innych typów plików (w tym pliku Types.ps1xml), należy użyć `PrependData` parametru [TypeData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e763b-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="e763b-130">Aby udostępnić plik rozszerzone typy do wszystkich przyszłych sesji, Dodaj plik typów do modułu, eksportu w bieżącej sesji lub Dodaj [TypeData aktualizacji](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) polecenia do Twojego profilu programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e763b-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="e763b-131">Podpisywanie typów plików</span><span class="sxs-lookup"><span data-stu-id="e763b-131">Signing Types Files</span></span>

<span data-ttu-id="e763b-132">Typy plików powinny podpisane cyfrowo, aby zapobiec modyfikowaniu, ponieważ kod XML może zawierać Bloki skryptu.</span><span class="sxs-lookup"><span data-stu-id="e763b-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="e763b-133">Aby uzyskać więcej informacji na temat dodawania podpisów cyfrowych, zobacz [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="e763b-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="e763b-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e763b-134">See Also</span></span>

[<span data-ttu-id="e763b-135">Definiowanie domyślnych właściwości dla obiektów</span><span class="sxs-lookup"><span data-stu-id="e763b-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="e763b-136">Definiowanie domyślnych metod dla obiektów</span><span class="sxs-lookup"><span data-stu-id="e763b-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="e763b-137">Definiowanie domyślnego zestawów elementów członkowskich dla obiektów</span><span class="sxs-lookup"><span data-stu-id="e763b-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="e763b-138">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e763b-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
