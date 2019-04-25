---
title: Jak zaimportować polecenia cmdlet przy użyciu modułów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067981"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="51e6b-102">Jak importować polecenia cmdlet przy użyciu modułów</span><span class="sxs-lookup"><span data-stu-id="51e6b-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="51e6b-103">W tym temacie opisano jak zaimportować polecenia cmdlet do sesji środowiska Windows PowerShell przy użyciu modułu binarnego.</span><span class="sxs-lookup"><span data-stu-id="51e6b-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="51e6b-104">Może zawierać elementy członkowskie modułów, poleceń cmdlet, dostawców, funkcje, zmienne, aliasy i wiele więcej.</span><span class="sxs-lookup"><span data-stu-id="51e6b-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="51e6b-105">Przystawek może zawierać tylko polecenia cmdlet i dostawców.</span><span class="sxs-lookup"><span data-stu-id="51e6b-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="51e6b-106">Ładowanie za pomocą modułu poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="51e6b-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="51e6b-107">Utwórz folder modułu, który ma taką samą nazwę jak plik zestawu, w którym są implementowane polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51e6b-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="51e6b-108">W tej procedurze folder modułu jest tworzony w `system32` folderu.</span><span class="sxs-lookup"><span data-stu-id="51e6b-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="51e6b-109">Upewnij się, że `PSModulePath` zmienna środowiskowa zawiera ścieżkę do nowego folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="51e6b-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="51e6b-110">Domyślnie folder systemowy został już dodany do `PSModulePath` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="51e6b-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="51e6b-111">Skopiuj zestaw polecenia cmdlet w folderze modułu.</span><span class="sxs-lookup"><span data-stu-id="51e6b-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="51e6b-112">Uruchom następujące polecenie, aby dodać polecenia cmdlet do sesji:</span><span class="sxs-lookup"><span data-stu-id="51e6b-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="51e6b-113">Ta procedura może służyć do testowania poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51e6b-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="51e6b-114">Dodaje wszystkie polecenia cmdlet w zestawie do sesji.</span><span class="sxs-lookup"><span data-stu-id="51e6b-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="51e6b-115">Aby uzyskać więcej informacji na temat modułów, zobacz różnych typów modułów, różne sposoby ładowanie modułów i jak ograniczyć elementy modułu, które są eksportowane [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="51e6b-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="51e6b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51e6b-116">See Also</span></span>

[<span data-ttu-id="51e6b-117">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51e6b-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="51e6b-118">Instalowanie modułów</span><span class="sxs-lookup"><span data-stu-id="51e6b-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)