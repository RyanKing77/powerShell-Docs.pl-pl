---
title: Jak napisać plik binarny programu PowerShell Module | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229334"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="1a970-102">Jak napisać moduł pliku binarnego programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a970-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="1a970-103">Binarny może być moduł zestawu (.dll), który zawiera polecenie cmdlet klasy.</span><span class="sxs-lookup"><span data-stu-id="1a970-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="1a970-104">Domyślnie wszystkie polecenia cmdlet w zestawie są importowane podczas importowania modułu binarnego.</span><span class="sxs-lookup"><span data-stu-id="1a970-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="1a970-105">Może jednak ograniczyć poleceń cmdlet, które są importowane, tworząc manifest modułu, którego moduł głównego to zestaw.</span><span class="sxs-lookup"><span data-stu-id="1a970-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="1a970-106">(Na przykład klucz CmdletsToExport manifestu można wyeksportować tylko tych poleceń cmdlet, które są wymagane.) Ponadto moduł binarny może zawierać dodatkowe pliki, struktura katalogów i innych rodzajów informacji o zarządzaniu przydatne, w których jednego polecenia cmdlet nie może.</span><span class="sxs-lookup"><span data-stu-id="1a970-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="1a970-107">Poniższa procedura opisuje sposób tworzenia i zainstaluj moduł programu PowerShell binarnego.</span><span class="sxs-lookup"><span data-stu-id="1a970-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="1a970-108">Jak tworzyć i instalować binarne modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a970-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="1a970-109">Tworzenie rozwiązania binarne programu PowerShell (takich jak polecenia cmdlet napisane w C#), korzystając z możliwości potrzebne i upewnij się, że działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="1a970-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="1a970-110">Z punktu widzenia kod podstawowy moduł binarnego jest po prostu zestaw polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a970-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="1a970-111">W rzeczywistości programu PowerShell będzie traktować zestawu jednego polecenia cmdlet jako moduł, ładowanie i zwalnianie z nie dodatkowego nakładu pracy ze strony dewelopera.</span><span class="sxs-lookup"><span data-stu-id="1a970-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="1a970-112">Aby uzyskać więcej informacji na temat pisania polecenia cmdlet, zobacz [pisania polecenia Cmdlet programu Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="1a970-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="1a970-113">Jeśli to konieczne, należy utworzyć pozostałą część rozwiązania: (dodatkowych poleceń cmdlet, pliki XML i tak dalej) i opisano je z manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="1a970-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="1a970-114">Oprócz opisujący zestawy polecenia cmdlet w rozwiązaniu, manifestu modułu opisujący, jak chcesz eksportować i importować modułu, jakie polecenia cmdlet zostaną ujawnione i dodatkowe pliki przejdzie do modułu.</span><span class="sxs-lookup"><span data-stu-id="1a970-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="1a970-115">Jak wspomniano wcześniej jednak, programu PowerShell można traktować binarne polecenia cmdlet, takich jak moduł o nie dodatkowego nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="1a970-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="1a970-116">W efekcie manifestu modułu przydaje się głównie na łączenie wielu plików w jednym pakiecie lub jawnie kontrolowania publikacji dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1a970-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="1a970-117">Aby uzyskać więcej informacji, zobacz [jak napisać Manifest modułu programu PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="1a970-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="1a970-118">Poniższy kod jest bardzo proste C# blok kodu, który zawiera trzy polecenia cmdlet w tym samym pliku, który może służyć jako moduł.</span><span class="sxs-lookup"><span data-stu-id="1a970-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="1a970-119">Pakiet rozwiązania i zapisać pakiet w innym miejscu w ścieżce modułu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a970-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="1a970-120">`PSModulePath` Zmiennej środowiskowej globalne w tym artykule opisano ścieżek domyślnych, używających programu PowerShell można znaleźć modułu.</span><span class="sxs-lookup"><span data-stu-id="1a970-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="1a970-121">Na przykład będzie wspólną ścieżkę można zapisać modułu w systemie `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="1a970-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="1a970-122">Jeśli nie używasz domyślnych ścieżek, należy jawnie określać lokalizację modułu podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="1a970-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="1a970-123">Należy utworzyć folder do zapisania modułu, ponieważ folder do przechowywania wielu zestawów i plików, dla danego rozwiązania może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="1a970-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="1a970-124">Należy pamiętać, że z technicznego punktu widzenia nie trzeba zainstalować modułu w dowolnym miejscu na `PSModulePath` — są po prostu domyślne lokalizacje wyglądające programu PowerShell dla modułu.</span><span class="sxs-lookup"><span data-stu-id="1a970-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="1a970-125">Jednak uważa się najlepszym rozwiązaniem jest, aby to zrobić, chyba że masz powód przechowywania modułu gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="1a970-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="1a970-126">Aby uzyskać więcej informacji, zobacz [Instalowanie modułu programu PowerShell](./installing-a-powershell-module.md) i [modyfikowania ścieżki instalacji modułu PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="1a970-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="1a970-127">Importowanie modułu programu PowerShell przy użyciu wywołania do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="1a970-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="1a970-128">Wywoływanie [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) załaduje modułu do aktywnej pamięci.</span><span class="sxs-lookup"><span data-stu-id="1a970-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="1a970-129">Jeśli używasz programu PowerShell 3.0, a później, po prostu wywoływania Nazwa modułu w kodzie, będzie również zaimportować go; Aby uzyskać więcej informacji, zobacz [zaimportowanie modułu PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="1a970-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="1a970-130">Importowanie zestawów przystawki jako moduły</span><span class="sxs-lookup"><span data-stu-id="1a970-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="1a970-131">Polecenia cmdlet i dostawców, które istnieją w przystawce w zestawach, może być załadowany jako moduły binarne.</span><span class="sxs-lookup"><span data-stu-id="1a970-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="1a970-132">Po przystawki zespoły są ładowane jako moduły binarne, poleceń cmdlet i dostawców w przystawce są dostępne dla użytkownika, ale klasy przystawki w zestawie jest ignorowana, a ta przystawka nie jest zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="1a970-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="1a970-133">Co w efekcie cmdlet przystawki dostarczane przez środowisko Windows PowerShell nie może wykryć przystawki, nawet jeśli polecenia cmdlet i dostawcy będą dostępne dla sesji.</span><span class="sxs-lookup"><span data-stu-id="1a970-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="1a970-134">Ponadto formatowania lub typów plików, których odwołuje się ta przystawka nie można zaimportować jako część modułu binarnego.</span><span class="sxs-lookup"><span data-stu-id="1a970-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="1a970-135">Aby zaimportować pliki formatowania i typów należy utworzyć manifestu modułu.</span><span class="sxs-lookup"><span data-stu-id="1a970-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="1a970-136">Zobacz, [jak napisać Manifest modułu programu PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="1a970-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a970-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a970-137">See Also</span></span>

[<span data-ttu-id="1a970-138">Pisanie modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1a970-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
