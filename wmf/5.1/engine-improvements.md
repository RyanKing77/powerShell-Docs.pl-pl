---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia aparatu programu PowerShell w programie WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055568"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="6b0e5-103">Ulepszenia aparatu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b0e5-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="6b0e5-104">Następujące ulepszenia w aparacie programu PowerShell core zostały wdrożone w WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="6b0e5-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="6b0e5-105">Wydajność</span><span class="sxs-lookup"><span data-stu-id="6b0e5-105">Performance</span></span>

<span data-ttu-id="6b0e5-106">Wydajność poprawiła się w niektórych obszarach ważne:</span><span class="sxs-lookup"><span data-stu-id="6b0e5-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="6b0e5-107">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="6b0e5-107">Startup</span></span>
- <span data-ttu-id="6b0e5-108">Przetwarzanie potokowe poleceń cmdlet, takich jak `ForEach-Object` i `Where-Object` wynosi około 50% szybsza</span><span class="sxs-lookup"><span data-stu-id="6b0e5-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="6b0e5-109">Ulepszenia przykład (Twoje wyniki mogą się różnić w zależności od sprzętu):</span><span class="sxs-lookup"><span data-stu-id="6b0e5-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="6b0e5-110">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="6b0e5-110">Scenario</span></span> | <span data-ttu-id="6b0e5-111">W wersji 5.0, czas (ms)</span><span class="sxs-lookup"><span data-stu-id="6b0e5-111">5.0 Time (ms)</span></span> | <span data-ttu-id="6b0e5-112">5.1 czas (ms)</span><span class="sxs-lookup"><span data-stu-id="6b0e5-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="6b0e5-113">900</span><span class="sxs-lookup"><span data-stu-id="6b0e5-113">900</span></span> | <span data-ttu-id="6b0e5-114">250</span><span class="sxs-lookup"><span data-stu-id="6b0e5-114">250</span></span> |
| <span data-ttu-id="6b0e5-115">Pierwszy kiedykolwiek uruchamiania środowiska PowerShell: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="6b0e5-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="6b0e5-116">30000</span><span class="sxs-lookup"><span data-stu-id="6b0e5-116">30000</span></span> | <span data-ttu-id="6b0e5-117">13000</span><span class="sxs-lookup"><span data-stu-id="6b0e5-117">13000</span></span> |
| <span data-ttu-id="6b0e5-118">Analiza pamięci podręcznej poleceń wbudowane: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="6b0e5-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="6b0e5-119">7000</span><span class="sxs-lookup"><span data-stu-id="6b0e5-119">7000</span></span> | <span data-ttu-id="6b0e5-120">520</span><span class="sxs-lookup"><span data-stu-id="6b0e5-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="6b0e5-121">1400</span><span class="sxs-lookup"><span data-stu-id="6b0e5-121">1400</span></span> | <span data-ttu-id="6b0e5-122">750</span><span class="sxs-lookup"><span data-stu-id="6b0e5-122">750</span></span> |

> [!Note]
> <span data-ttu-id="6b0e5-123">Jednej zmiany związane z uruchamiania mogą mieć wpływ na niektóre scenariusze nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="6b0e5-124">Program PowerShell nie jest już odczytuje pliki `$pshome\*.ps1xml` — te pliki zostały przekonwertowane na C# uniknąć niektórych plików i obciążenie Procesora przetwarzania plików XML.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="6b0e5-125">Pliki nadal istnieje do działu pomocy technicznej w wersji 2 side-by-side, więc w przypadku zmiany zawartość pliku nie będzie miała wpływu na V5, tylko w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="6b0e5-126">Należy zauważyć, że zmiany zawartości tych plików, nigdy nie było to obsługiwany scenariusz.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="6b0e5-127">Inna zmiana widoczne polega na tym, jak program PowerShell buforuje wyeksportowanego polecenia i inne informacje dla modułów, które są zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="6b0e5-128">Wcześniej ta pamięć podręczna została zapisana w katalogu `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="6b0e5-129">W program WMF 5.1 pamięć podręczna to pojedynczy plik `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="6b0e5-130">Zobacz [moduł analizy w pamięci podręcznej](scenarios-features.md#module-analysis-cache) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6b0e5-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>