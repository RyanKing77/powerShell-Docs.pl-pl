---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Bezpośrednie wywoływanie metod zasobów DSC"
ms.openlocfilehash: ab00e66d526eda244500a41e450c56b0151274ee
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="5c177-103">Bezpośrednie wywoływanie metod zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="5c177-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="5c177-104">Dotyczy: Środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5c177-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5c177-105">Można użyć [Invoke DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) polecenia cmdlet, aby bezpośrednio wywoływać funkcje i metody zasobu DSC ( **Get-TargetResource**, **TargetResource zestaw**i  **Test-TargetResource** funkcje zasobu na podstawie MOF lub **uzyskać**, **ustawić**, i **testu** metod klasy zasobu).</span><span class="sxs-lookup"><span data-stu-id="5c177-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="5c177-106">To może służyć przez osoby trzecie, które chcą korzystać z zasobów DSC lub jako narzędzia pomocne podczas tworzenia zasobów.</span><span class="sxs-lookup"><span data-stu-id="5c177-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span> 

<span data-ttu-id="5c177-107">To polecenie cmdlet jest zwykle używana w połączeniu z właściwością metakonfigurację `refreshMode = 'Disabled'`, ale mogą być używane niezależnie od tego, co **refreshMode** ma ustawioną wartość.</span><span class="sxs-lookup"><span data-stu-id="5c177-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="5c177-108">Podczas wywoływania metody **Invoke DscResource** polecenia cmdlet, określić metody lub funkcji do wywołania przy użyciu **metody** parametru.</span><span class="sxs-lookup"><span data-stu-id="5c177-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="5c177-109">Określ właściwości zasobu przez przekazanie obiektu hashtable jako wartość **właściwości** parametru.</span><span class="sxs-lookup"><span data-stu-id="5c177-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="5c177-110">Poniżej przedstawiono przykłady bezpośrednio wywołać metody zasobów:</span><span class="sxs-lookup"><span data-stu-id="5c177-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="5c177-111">Upewnij się, że plik istnieje</span><span class="sxs-lookup"><span data-stu-id="5c177-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="5c177-112">Testowanie, czy plik istnieje</span><span class="sxs-lookup"><span data-stu-id="5c177-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="5c177-113">Pobierz zawartość pliku</span><span class="sxs-lookup"><span data-stu-id="5c177-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="5c177-114">**Uwaga:** bezpośrednie wywoływanie metod złożonego zasobu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5c177-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="5c177-115">Zamiast tego należy wywoływać metody zasobów wchodzące w skład złożonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="5c177-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c177-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c177-116">See Also</span></span>
- [<span data-ttu-id="5c177-117">Pisanie niestandardowych zasobów DSC z MOF</span><span class="sxs-lookup"><span data-stu-id="5c177-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="5c177-118">Pisanie niestandardowych zasobów DSC z klasami programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c177-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="5c177-119">Debugowanie zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="5c177-119">Debugging DSC resources</span></span>](debugResource.md)

