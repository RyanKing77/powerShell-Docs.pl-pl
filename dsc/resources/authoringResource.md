---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684591"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="76aca-103">Tworzenie niestandardowych Windows PowerShell Desired State Configuration zasobów</span><span class="sxs-lookup"><span data-stu-id="76aca-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="76aca-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="76aca-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="76aca-105">Windows PowerShell Desired State Configuration (DSC) ma wbudowane zasoby, których można użyć, aby skonfigurować środowisko.</span><span class="sxs-lookup"><span data-stu-id="76aca-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="76aca-106">Ten temat zawiera omówienie związanych z tworzeniem zasobów i łącza do tematów, przy użyciu określonych informacji i przykładów.</span><span class="sxs-lookup"><span data-stu-id="76aca-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="76aca-107">Składniki zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="76aca-107">DSC resource components</span></span>

<span data-ttu-id="76aca-108">Zasób DSC jest moduł programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76aca-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="76aca-109">Moduł zawiera zarówno schematu (definicja konfigurowalne właściwości), jak i implementację (kod, który wykonuje faktyczną pracę określony w konfiguracji) dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="76aca-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="76aca-110">Schemat zasobów DSC można zdefiniować w pliku MOF i wykonania, odbywa się przez moduł skryptu.</span><span class="sxs-lookup"><span data-stu-id="76aca-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="76aca-111">Począwszy od obsługi klas programu PowerShell w wersji 5 schematu i implementację zarówno można zdefiniować w klasie.</span><span class="sxs-lookup"><span data-stu-id="76aca-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="76aca-112">W następujących tematach opisano bardziej szczegółowo, jak tworzyć zasoby DSC.</span><span class="sxs-lookup"><span data-stu-id="76aca-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="76aca-113">Pisanie zasobu DSC niestandardowych z pliku MOF</span><span class="sxs-lookup"><span data-stu-id="76aca-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="76aca-114">Wdrażanie zasobu DSC wC#</span><span class="sxs-lookup"><span data-stu-id="76aca-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="76aca-115">Pisanie zasobu DSC niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="76aca-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="76aca-116">Zasoby złożone: Przy użyciu konfiguracji DSC jako zasób</span><span class="sxs-lookup"><span data-stu-id="76aca-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="76aca-117">Przy użyciu narzędzia Projektant zasobów</span><span class="sxs-lookup"><span data-stu-id="76aca-117">Using the Resource Designer tool</span></span>](../authoringResourceMofDesigner.md)
