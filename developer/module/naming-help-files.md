---
title: Nazwy plików pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082185"
---
# <a name="naming-help-files"></a><span data-ttu-id="6f2f2-102">Nadawanie nazw plikom pomocy</span><span class="sxs-lookup"><span data-stu-id="6f2f2-102">Naming Help Files</span></span>

<span data-ttu-id="6f2f2-103">W tym temacie wyjaśniono, jak nazwa pliku pomocy opartych na języku XML, aby [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) polecenia cmdlet, mogą ją odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="6f2f2-104">Wymagania dotyczące nazw różnią się dla każdego typu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="6f2f2-105">Pliki pomocy dotyczącej poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f2f2-105">Cmdlet Help Files</span></span>

<span data-ttu-id="6f2f2-106">W pliku Pomocy C# polecenia cmdlet, musi nosić nazwę zestawu, w którym zdefiniowano polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="6f2f2-107">Użyj następującego formatu nazwy pliku:</span><span class="sxs-lookup"><span data-stu-id="6f2f2-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="6f2f2-108">Format nazwy zestawu jest wymagana, nawet wtedy, gdy zestaw jest zagnieżdżony moduł.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="6f2f2-109">Na przykład [polecenia Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) polecenia cmdlet jest zdefiniowany w zestawie Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="6f2f2-110">`Get-Help` Polecenie cmdlet wyszukuje utworzenia tematu Pomocy dotyczącego `Get-WinEvent` polecenia cmdlet tylko w pliku Microsoft.PowerShell.Diagnostics.dll help.xml w katalogu modułu.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="6f2f2-111">Pliki pomocy dostawcy</span><span class="sxs-lookup"><span data-stu-id="6f2f2-111">Provider Help files</span></span>

<span data-ttu-id="6f2f2-112">Dostawca programu Windows PowerShell można znaleźć w pliku pomocy musi mieć nazwę zestawu, w którym zdefiniowano dostawcy.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="6f2f2-113">Użyj następującego formatu nazwy pliku:</span><span class="sxs-lookup"><span data-stu-id="6f2f2-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="6f2f2-114">Format nazwy zestawu jest wymagana, nawet wtedy, gdy zestaw jest zagnieżdżony moduł.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="6f2f2-115">Na przykład dostawca certyfikatów jest zdefiniowany w zestawie Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="6f2f2-116">`Get-Help` Polecenie cmdlet wyszukuje tematu pomocy dla dostawcy certyfikat tylko w pliku Microsoft.PowerShell.Security.dll help.xml w katalogu modułu.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="6f2f2-117">Pliki Pomocy — funkcja</span><span class="sxs-lookup"><span data-stu-id="6f2f2-117">Function Help Files</span></span>

<span data-ttu-id="6f2f2-118">Funkcje mogą być udokumentowane przy użyciu [Pomoc oparta na komentarzach](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) lub zamieszczone w pliku pomocy XML.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="6f2f2-119">Gdy funkcja jest udokumentowany w pliku XML, funkcja musi mieć `.ExternalHelp` komentarz — słowo kluczowe, które kojarzy funkcji z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="6f2f2-120">W przeciwnym razie `Get-Help` polecenie cmdlet nie można odnaleźć pliku pomocy.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="6f2f2-121">Nie istnieją wymagania techniczne dla nazwy pliku pomocy funkcji.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="6f2f2-122">Jednak najlepszym rozwiązaniem jest nazwa pliku pomocy dla modułu skryptów, w którym zdefiniowano funkcji.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="6f2f2-123">Na przykład następująca funkcja jest zdefiniowana w pliku Mójmoduł.psm1.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="6f2f2-124">Pliki pomocy poleceń CIM</span><span class="sxs-lookup"><span data-stu-id="6f2f2-124">CIM Command Help Files</span></span>

<span data-ttu-id="6f2f2-125">Plik pomocy dla poleceń CIM, musi mieć nazwę dla pliku CDXML, w którym zdefiniowano polecenia modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="6f2f2-126">Użyj następującego formatu nazwy pliku:</span><span class="sxs-lookup"><span data-stu-id="6f2f2-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="6f2f2-127">CIM polecenia są definiowane w plików CDXML, które mogły zostać uwzględnione w modułach jako moduły zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="6f2f2-128">Gdy polecenie modelu wspólnych informacji są importowane do sesji jako funkcja, programu Windows PowerShell dodaje `.ExternalHelp` komentarz — słowo kluczowe do definicji funkcji, które kojarzy funkcji przy pomocy XML pliku, który nosi nazwę pliku CDXML, w którym zdefiniowano polecenia modelu wspólnych informacji.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="6f2f2-129">Pliki pomocy przepływu pracy skryptu</span><span class="sxs-lookup"><span data-stu-id="6f2f2-129">Script Workflow Help Files</span></span>

<span data-ttu-id="6f2f2-130">Skryptowymi przepływami pracy, które są uwzględnione w modułach mogą udokumentowane w plikach pomocy opartych na języku XML.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="6f2f2-131">Nie istnieją wymagania techniczne dla nazwy pliku pomocy.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="6f2f2-132">Jednak najlepszym rozwiązaniem jest nazwa pliku pomocy dla modułu skryptów, w którym zdefiniowano skryptowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="6f2f2-133">Przykład:</span><span class="sxs-lookup"><span data-stu-id="6f2f2-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="6f2f2-134">W przeciwieństwie do innych poleceń przy użyciu skryptu, nie wymagają skryptowymi przepływami pracy `.ExternalHelp` komentarz — słowo kluczowe, aby skojarzyć je z pliku pomocy.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="6f2f2-135">Zamiast tego programu Windows PowerShell przeszukuje podkatalogów interfejsu użytkownika specyficznych dla kultury katalog modułu plików pomocy opartych na języku XML, a szuka pomocy dla skryptowego przepływu pracy we wszystkich plikach.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="6f2f2-136">`.ExternalHelp` komentarz — słowo kluczowe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="6f2f2-137">Ponieważ `.ExternalHelp` — słowo kluczowe komentarza jest ignorowane, `Get-Help` polecenia cmdlet można znaleźć pomoc skryptowymi przepływami pracy tylko wtedy, gdy są one uwzględnione w modułach.</span><span class="sxs-lookup"><span data-stu-id="6f2f2-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>