---
title: Jak zaimportować polecenia cmdlet przy użyciu modułów | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215264"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="7bffb-102">Jak importować polecenia cmdlet przy użyciu modułów</span><span class="sxs-lookup"><span data-stu-id="7bffb-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="7bffb-103">W tym artykule opisano sposób importowania poleceń cmdlet do sesji programu PowerShell przy użyciu modułu binarnego.</span><span class="sxs-lookup"><span data-stu-id="7bffb-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="7bffb-104">Elementy członkowskie modułów mogą zawierać polecenia cmdlet, dostawcy, funkcje, zmienne, aliasy i wiele innych.</span><span class="sxs-lookup"><span data-stu-id="7bffb-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="7bffb-105">Przystawki mogą zawierać tylko polecenia cmdlet i dostawców.</span><span class="sxs-lookup"><span data-stu-id="7bffb-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="7bffb-106">Jak ładować polecenia cmdlet przy użyciu modułu</span><span class="sxs-lookup"><span data-stu-id="7bffb-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="7bffb-107">Utwórz folder modułu, który ma taką samą nazwę jak plik zestawu, w którym są zaimplementowane polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bffb-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="7bffb-108">W tej procedurze folder module zostanie utworzony w folderze systemu Windows `system32` .</span><span class="sxs-lookup"><span data-stu-id="7bffb-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="7bffb-109">Upewnij się, że `PSModulePath` zmienna środowiskowa zawiera ścieżkę do nowego folderu modułu.</span><span class="sxs-lookup"><span data-stu-id="7bffb-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="7bffb-110">Domyślnie folder systemowy jest już dodany do `PSModulePath` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="7bffb-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="7bffb-111">Aby wyświetlić `PSModulePath`, wpisz: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="7bffb-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="7bffb-112">Skopiuj zestaw poleceń cmdlet do folderu module.</span><span class="sxs-lookup"><span data-stu-id="7bffb-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="7bffb-113">Dodaj plik manifestu modułu (`.psd1`) w folderze głównym modułu.</span><span class="sxs-lookup"><span data-stu-id="7bffb-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="7bffb-114">Program PowerShell używa manifestu modułu do zaimportowania modułu.</span><span class="sxs-lookup"><span data-stu-id="7bffb-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="7bffb-115">Aby uzyskać więcej informacji, zobacz [jak napisać manifest modułu programu PowerShell](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="7bffb-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="7bffb-116">Uruchom następujące polecenie, aby dodać polecenia cmdlet do sesji:</span><span class="sxs-lookup"><span data-stu-id="7bffb-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="7bffb-117">Ta procedura może służyć do testowania poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bffb-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="7bffb-118">Dodaje wszystkie polecenia cmdlet w zestawie do sesji.</span><span class="sxs-lookup"><span data-stu-id="7bffb-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="7bffb-119">Aby uzyskać więcej informacji o modułach, zobacz [pisanie modułu programu Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="7bffb-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7bffb-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bffb-120">See also</span></span>

[<span data-ttu-id="7bffb-121">Jak napisać manifest modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="7bffb-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="7bffb-122">Importowanie modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="7bffb-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="7bffb-123">Import-Module</span><span class="sxs-lookup"><span data-stu-id="7bffb-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="7bffb-124">Instalowanie modułów</span><span class="sxs-lookup"><span data-stu-id="7bffb-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="7bffb-125">Modyfikowanie ścieżki instalacji PSModulePath</span><span class="sxs-lookup"><span data-stu-id="7bffb-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="7bffb-126">Pisanie polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7bffb-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
