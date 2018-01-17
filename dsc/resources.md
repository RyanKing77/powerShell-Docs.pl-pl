---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasoby usługi Konfiguracja DSC"
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="39315-103">Zasoby usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="39315-103">DSC Resources</span></span>

><span data-ttu-id="39315-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="39315-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="39315-105">Żądana Konfiguracja stanu (DSC) zasoby dostarczają bloków konstrukcyjnych dla konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="39315-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="39315-106">Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skryptu programu PowerShell, które wywołuje lokalnego Menedżera konfiguracji (LCM) umożliwia "tak".</span><span class="sxs-lookup"><span data-stu-id="39315-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="39315-107">Zasób może modelu coś jako ogólnego jako plik lub jako określone w ustawieniach serwera IIS.</span><span class="sxs-lookup"><span data-stu-id="39315-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="39315-108">Grupy takich jak zasoby połączone w Module DSC organizuje wszystkie wymagane pliki w strukturze przenośnego i zawierający metadane, aby określić, jak zasoby są przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="39315-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="39315-109">DSC zasobów można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="39315-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="39315-110">Wbudowane zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="39315-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="39315-111">Tworzenie niestandardowych zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="39315-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="39315-112">Wbudowane DSC zasobów dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="39315-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

