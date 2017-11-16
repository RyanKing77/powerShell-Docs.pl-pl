---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasoby usługi Konfiguracja DSC"
ms.openlocfilehash: 62bf352b929d661e585e145e5aab0f44f13010a1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-resources"></a><span data-ttu-id="b25f5-103">Zasoby usługi Konfiguracja DSC</span><span class="sxs-lookup"><span data-stu-id="b25f5-103">DSC Resources</span></span>

><span data-ttu-id="b25f5-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b25f5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b25f5-105">Żądana Konfiguracja stanu (DSC) zasoby dostarczają bloków konstrukcyjnych dla konfiguracji DSC.</span><span class="sxs-lookup"><span data-stu-id="b25f5-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="b25f5-106">Zasób udostępnia właściwości, które mogą być skonfigurowane (schemat) i zawiera funkcje skryptu programu PowerShell, które wywołuje lokalnego Menedżera konfiguracji (LCM) umożliwia "tak".</span><span class="sxs-lookup"><span data-stu-id="b25f5-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="b25f5-107">Zasób może modelu coś jako ogólnego jako plik lub jako określone w ustawieniach serwera IIS.</span><span class="sxs-lookup"><span data-stu-id="b25f5-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="b25f5-108">Grupy takich jak zasoby połączone w Module DSC organizuje wszystkie wymagane pliki w strukturze przenośnego i zawierający metadane, aby określić, jak zasoby są przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="b25f5-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="b25f5-109">DSC zasobów można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="b25f5-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="b25f5-110">Wbudowane zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="b25f5-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="b25f5-111">Tworzenie niestandardowych zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="b25f5-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="b25f5-112">Wbudowane DSC zasobów dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="b25f5-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

