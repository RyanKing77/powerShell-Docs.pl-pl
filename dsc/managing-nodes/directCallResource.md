---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Bezpośrednie wywoływanie metod zasobów DSC
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685676"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="24475-103">Bezpośrednie wywoływanie metod zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="24475-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="24475-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24475-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="24475-105">Możesz użyć [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) polecenia cmdlet, aby bezpośrednio wywoływać funkcje lub metod zasobów DSC ( **Get TargetResource**, **TargetResource zestaw**i  **Test-TargetResource** funkcje zasób oparty na pliku MOF lub **uzyskać**, **ustaw**, i **testu** metody oparte na klasach zasobów).</span><span class="sxs-lookup"><span data-stu-id="24475-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="24475-106">To może służyć przez osoby trzecie, które mają być używane zasoby DSC lub jako narzędzia pomocne podczas tworzenia zasobów.</span><span class="sxs-lookup"><span data-stu-id="24475-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="24475-107">To polecenie cmdlet jest zwykle używana w połączeniu z właściwością metaconfiguration `refreshMode = 'Disabled'`, ale można ich używać niezależnie od tego, co **refreshMode** jest równa.</span><span class="sxs-lookup"><span data-stu-id="24475-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="24475-108">Podczas wywoływania **Invoke-DscResource** polecenia cmdlet, określ metoda lub funkcja do wywołania przy użyciu **metoda** parametru.</span><span class="sxs-lookup"><span data-stu-id="24475-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="24475-109">Określ właściwości zasobu przez przekazanie skrótów jako wartość **właściwość** parametru.</span><span class="sxs-lookup"><span data-stu-id="24475-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="24475-110">Poniżej przedstawiono przykłady bezpośrednie wywoływanie metod zasobów:</span><span class="sxs-lookup"><span data-stu-id="24475-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="24475-111">Upewnij się, że plik znajduje się</span><span class="sxs-lookup"><span data-stu-id="24475-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="24475-112">Testowanie, czy plik istnieje</span><span class="sxs-lookup"><span data-stu-id="24475-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="24475-113">Pobierz zawartość pliku</span><span class="sxs-lookup"><span data-stu-id="24475-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="24475-114">**Uwaga:** Bezpośrednie wywoływanie metod zasobów złożonego nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="24475-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="24475-115">Zamiast tego należy wywołać metodę zasobów, które tworzą złożonego zasobów.</span><span class="sxs-lookup"><span data-stu-id="24475-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="24475-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24475-116">See Also</span></span>
- [<span data-ttu-id="24475-117">Pisanie zasobu DSC niestandardowych z pliku MOF</span><span class="sxs-lookup"><span data-stu-id="24475-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="24475-118">Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="24475-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="24475-119">Debugowanie zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="24475-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)