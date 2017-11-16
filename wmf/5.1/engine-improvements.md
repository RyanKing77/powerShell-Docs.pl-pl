---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: "Ulepszenia dotyczące aparatu programu PowerShell w programie WMF 5.1"
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="aaf51-103">Ulepszenia aparatu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="aaf51-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="aaf51-104">Wprowadzono następujące ulepszenia podstawowym aparatem programu PowerShell są zaimplementowane w wersji 5.1 WMF:</span><span class="sxs-lookup"><span data-stu-id="aaf51-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="aaf51-105">Wydajność</span><span class="sxs-lookup"><span data-stu-id="aaf51-105">Performance</span></span> ##

<span data-ttu-id="aaf51-106">Wydajność poprawiła w pewne ważne kwestie:</span><span class="sxs-lookup"><span data-stu-id="aaf51-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="aaf51-107">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="aaf51-107">Startup</span></span>
- <span data-ttu-id="aaf51-108">Przetwarzanie potokowe do poleceń cmdlet, takich jak ForEach-Object i Where-Object to około 50% szybsza</span><span class="sxs-lookup"><span data-stu-id="aaf51-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span> 

<span data-ttu-id="aaf51-109">Niektóre ulepszenia przykład (wyniki mogą się różnić w zależności od sprzętu):</span><span class="sxs-lookup"><span data-stu-id="aaf51-109">Some example improvements (your results may vary depending on your hardware):</span></span> 

| <span data-ttu-id="aaf51-110">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="aaf51-110">Scenario</span></span> | <span data-ttu-id="aaf51-111">5.0 czas (ms)</span><span class="sxs-lookup"><span data-stu-id="aaf51-111">5.0 Time (ms)</span></span> | <span data-ttu-id="aaf51-112">5.1 czas (ms)</span><span class="sxs-lookup"><span data-stu-id="aaf51-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="aaf51-113">900</span><span class="sxs-lookup"><span data-stu-id="aaf51-113">900</span></span> | <span data-ttu-id="aaf51-114">250</span><span class="sxs-lookup"><span data-stu-id="aaf51-114">250</span></span> |
| <span data-ttu-id="aaf51-115">Pierwszy kiedykolwiek uruchamiania programu PowerShell:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="aaf51-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="aaf51-116">30000</span><span class="sxs-lookup"><span data-stu-id="aaf51-116">30000</span></span> | <span data-ttu-id="aaf51-117">13000</span><span class="sxs-lookup"><span data-stu-id="aaf51-117">13000</span></span> |
| <span data-ttu-id="aaf51-118">Wbudowane buforu analizy polecenia:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="aaf51-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="aaf51-119">7000</span><span class="sxs-lookup"><span data-stu-id="aaf51-119">7000</span></span> | <span data-ttu-id="aaf51-120">520</span><span class="sxs-lookup"><span data-stu-id="aaf51-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="aaf51-121">1400</span><span class="sxs-lookup"><span data-stu-id="aaf51-121">1400</span></span> | <span data-ttu-id="aaf51-122">750</span><span class="sxs-lookup"><span data-stu-id="aaf51-122">750</span></span> |
  
> <span data-ttu-id="aaf51-123">Należy pamiętać, że jeden zmiany dotyczące uruchamiania może mieć wpływ na niektóre nieobsługiwanych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="aaf51-123">Note One change related to startup might impact some unsupported scenarios.</span></span> 
> <span data-ttu-id="aaf51-124">PowerShell już odczytuje pliki `$pshome\*.ps1xml` — tych plików został przekonwertowany na C#, aby uniknąć niektórych plików i obciążenie procesora CPU przetwarzania XML pliki.</span><span class="sxs-lookup"><span data-stu-id="aaf51-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> 
<span data-ttu-id="aaf51-125">Pliki nadal istnieją obsługi V2 side-by-side, więc jeśli zmienisz zawartość pliku nie będzie miała wpływu na V5, tylko w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="aaf51-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> 
<span data-ttu-id="aaf51-126">Należy pamiętać, że zmiany tych plików zawartości nigdy nie był obsługiwany scenariusz.</span><span class="sxs-lookup"><span data-stu-id="aaf51-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="aaf51-127">Inna zmiana widoczny jest sposób PowerShell buforuje wyeksportowany polecenia i inne informacje dla modułów, które są zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="aaf51-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="aaf51-128">Wcześniej ta pamięć podręczna była przechowywana w katalogu `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="aaf51-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="aaf51-129">W wersji 5.1 WMF, pamięć podręczna jest pojedynczy plik `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="aaf51-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="aaf51-130">Zobacz [moduł analizy w pamięci podręcznej](scenarios-features.md#module-analysis-cache) więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="aaf51-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>

