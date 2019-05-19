---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia aparatu programu PowerShell w programie WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856182"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="02f1e-103">Ulepszenia aparatu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="02f1e-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="02f1e-104">Następujące ulepszenia w aparacie programu PowerShell core zostały wdrożone w WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="02f1e-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="02f1e-105">Wydajność</span><span class="sxs-lookup"><span data-stu-id="02f1e-105">Performance</span></span>

<span data-ttu-id="02f1e-106">Wydajność poprawiła się w niektórych obszarach ważne:</span><span class="sxs-lookup"><span data-stu-id="02f1e-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="02f1e-107">Uruchamianie</span><span class="sxs-lookup"><span data-stu-id="02f1e-107">Startup</span></span>
- <span data-ttu-id="02f1e-108">Przetwarzanie potokowe poleceń cmdlet, takich jak `ForEach-Object` i `Where-Object` wynosi około 50% szybsza</span><span class="sxs-lookup"><span data-stu-id="02f1e-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="02f1e-109">Ulepszenia przykład (Twoje wyniki mogą się różnić w zależności od sprzętu):</span><span class="sxs-lookup"><span data-stu-id="02f1e-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="02f1e-110">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="02f1e-110">Scenario</span></span> | <span data-ttu-id="02f1e-111">W wersji 5.0, czas (ms)</span><span class="sxs-lookup"><span data-stu-id="02f1e-111">5.0 Time (ms)</span></span> | <span data-ttu-id="02f1e-112">5.1 czas (ms)</span><span class="sxs-lookup"><span data-stu-id="02f1e-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="02f1e-113">900</span><span class="sxs-lookup"><span data-stu-id="02f1e-113">900</span></span> | <span data-ttu-id="02f1e-114">250</span><span class="sxs-lookup"><span data-stu-id="02f1e-114">250</span></span> |
| <span data-ttu-id="02f1e-115">Pierwszy kiedykolwiek uruchamiania środowiska PowerShell: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="02f1e-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="02f1e-116">30000</span><span class="sxs-lookup"><span data-stu-id="02f1e-116">30000</span></span> | <span data-ttu-id="02f1e-117">13000</span><span class="sxs-lookup"><span data-stu-id="02f1e-117">13000</span></span> |
| <span data-ttu-id="02f1e-118">Analiza pamięci podręcznej poleceń wbudowane: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="02f1e-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="02f1e-119">7000</span><span class="sxs-lookup"><span data-stu-id="02f1e-119">7000</span></span> | <span data-ttu-id="02f1e-120">520</span><span class="sxs-lookup"><span data-stu-id="02f1e-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="02f1e-121">1400</span><span class="sxs-lookup"><span data-stu-id="02f1e-121">1400</span></span> | <span data-ttu-id="02f1e-122">750</span><span class="sxs-lookup"><span data-stu-id="02f1e-122">750</span></span> |

> [!NOTE]
> <span data-ttu-id="02f1e-123">Jednej zmiany związane z uruchamiania mogą mieć wpływ na niektóre scenariusze nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="02f1e-123">One change related to startup might impact some unsupported scenarios.</span></span> <span data-ttu-id="02f1e-124">Program PowerShell nie jest już odczytuje pliki `$pshome\*.ps1xml` — te pliki zostały przekonwertowane na C# uniknąć niektórych plików i obciążenie Procesora przetwarzania plików XML.</span><span class="sxs-lookup"><span data-stu-id="02f1e-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> <span data-ttu-id="02f1e-125">Pliki nadal istnieje do działu pomocy technicznej w wersji 2 side-by-side, więc w przypadku zmiany zawartość pliku nie będzie miała wpływu na V5, tylko w wersji 2.</span><span class="sxs-lookup"><span data-stu-id="02f1e-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> <span data-ttu-id="02f1e-126">Należy zauważyć, że zmiany zawartości tych plików, nigdy nie było to obsługiwany scenariusz.</span><span class="sxs-lookup"><span data-stu-id="02f1e-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="02f1e-127">Inna zmiana widoczne polega na tym, jak program PowerShell buforuje wyeksportowanego polecenia i inne informacje dla modułów, które są zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="02f1e-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="02f1e-128">Wcześniej ta pamięć podręczna została zapisana w katalogu `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="02f1e-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="02f1e-129">W program WMF 5.1 pamięć podręczna to pojedynczy plik `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="02f1e-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="02f1e-130">Zobacz [moduł analizy w pamięci podręcznej](release-notes.md#module-analysis-cache) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="02f1e-130">See [Module Analysis Cache](release-notes.md#module-analysis-cache) for more details.</span></span>