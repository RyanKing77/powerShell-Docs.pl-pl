---
title: Pisanie modułu programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848167"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="24163-102">Pisanie modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24163-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="24163-103">Ten dokument jest przeznaczony dla administratorów, deweloperzy skryptu i polecenia cmdlet deweloperzy, którzy potrzebują pakować i rozpowszechniać ich poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24163-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="24163-104">Za pomocą modułów programu Windows PowerShell, można pakietu i dystrybuować rozwiązania programu Windows PowerShell bez przy użyciu języka skompilowany.</span><span class="sxs-lookup"><span data-stu-id="24163-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="24163-105">Moduły programu Windows PowerShell umożliwiają partycji, organizowanie i abstrakcyjnej kodu programu Windows PowerShell na jednostki samodzielnych, wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="24163-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="24163-106">W tych jednostkach wielokrotnego użytku mogą łatwo udostępniać moduły bezpośrednio z innymi osobami.</span><span class="sxs-lookup"><span data-stu-id="24163-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="24163-107">Jeśli jesteś deweloperem skryptu, można również Przeprowadź ponowne pakowanie modułów innych firm do tworzenia niestandardowych aplikacji opartych na skryptach.</span><span class="sxs-lookup"><span data-stu-id="24163-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="24163-108">Moduły, podobnie jak modułów w innych językach skryptów, takich jak Perl i Python, Włącz gotowe do produkcji rozwiązania skryptów, które składniki wielokrotnego użytku, do dystrybucji, za pomocą jednocześnie ma dodatkową zaletę umożliwiając Przeprowadź ponowne pakowanie i streszczenie kilka składników Twórz niestandardowe rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="24163-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="24163-109">W swoich najbardziej podstawowym programu Windows PowerShell będą traktować prawidłowy kod skryptu programu Windows PowerShell zapisywane w pliku psm1 jako moduł.</span><span class="sxs-lookup"><span data-stu-id="24163-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="24163-110">PowerShell automatycznie traktują każdy zespół binarne polecenia cmdlet jako moduł.</span><span class="sxs-lookup"><span data-stu-id="24163-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="24163-111">Jednak również służy modułem (lub dokładniej, manifestu modułu) powiązać razem całego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="24163-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="24163-112">W poniższych scenariuszach opisano typowe zastosowania dla modułów programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24163-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="24163-113">Biblioteki</span><span class="sxs-lookup"><span data-stu-id="24163-113">Libraries</span></span>

<span data-ttu-id="24163-114">Moduły można pakować i rozpowszechniać spójnych biblioteki funkcji służących do wykonywania typowych zadań.</span><span class="sxs-lookup"><span data-stu-id="24163-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="24163-115">Zazwyczaj nazwy tych funkcji udostępnić co najmniej jeden rzeczowniki odzwierciedlające typowe zadania, które są używane dla.</span><span class="sxs-lookup"><span data-stu-id="24163-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="24163-116">Te funkcje można także podobny do klasy .NET Framework, w tym mają publicznych i prywatnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="24163-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="24163-117">Na przykład biblioteka może zawierać zbiór funkcji do transferu plików.</span><span class="sxs-lookup"><span data-stu-id="24163-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="24163-118">W tym przypadku rzeczownik odzwierciedlające typowe zadania może być "plik".</span><span class="sxs-lookup"><span data-stu-id="24163-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="24163-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="24163-119">Configuration</span></span>

<span data-ttu-id="24163-120">Moduły może służyć do dostosowywania środowiska, dodając konkretne polecenia cmdlet, dostawców, funkcje i zmienne.</span><span class="sxs-lookup"><span data-stu-id="24163-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="24163-121">Skompilowany kod tworzenia i dystrybucji</span><span class="sxs-lookup"><span data-stu-id="24163-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="24163-122">Polecenia cmdlet i dostawcy deweloperzy mogą używać modułów, testowanie i rozpowszechniania ich skompilowany kod bez konieczności tworzenia przystawek. Będą mogli zaimportować zestaw, który zawiera kod skompilowany jako moduł (moduł binarny) bez konieczności tworzenia i rejestrowania przystawki.</span><span class="sxs-lookup"><span data-stu-id="24163-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="24163-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24163-123">See Also</span></span>

[<span data-ttu-id="24163-124">Opis modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24163-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="24163-125">Jak napisać modul Skriptu Powershellu</span><span class="sxs-lookup"><span data-stu-id="24163-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="24163-126">Jak napisać modułu plik binarny programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="24163-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="24163-127">Jak napisać Manifest modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="24163-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="24163-128">Modyfikowanie PSModulePath ścieżki instalacji</span><span class="sxs-lookup"><span data-stu-id="24163-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="24163-129">Importowanie modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="24163-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="24163-130">Instalowanie modułu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="24163-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
