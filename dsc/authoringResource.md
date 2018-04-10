---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="581f1-103">Tworzenie niestandardowych Windows PowerShell Desired konfiguracji stanu zasobów</span><span class="sxs-lookup"><span data-stu-id="581f1-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="581f1-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="581f1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="581f1-105">Windows PowerShell Desired stan konfiguracji (DSC) ma wbudowane zasobów, które służy do konfigurowania środowiska.</span><span class="sxs-lookup"><span data-stu-id="581f1-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="581f1-106">(Aby uzyskać więcej informacji, zobacz [wbudowanych zasobów systemu Windows PowerShell Desired stan konfiguracji](builtInResource.md).) W tym temacie omówiono tworzenie zasobów i linków do tematów z określone informacje i przykłady.</span><span class="sxs-lookup"><span data-stu-id="581f1-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="581f1-107">Składniki zasobów DSC</span><span class="sxs-lookup"><span data-stu-id="581f1-107">DSC resource components</span></span>

<span data-ttu-id="581f1-108">Zasób DSC jest moduł programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="581f1-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="581f1-109">Moduł zawiera zarówno schematu (definicja konfigurowalne właściwości), jak i implementację (kod, który wykonuje faktyczną pracę określony w konfiguracji) dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="581f1-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="581f1-110">Schemat zasobów DSC można zdefiniować w pliku MOF i implementacji jest wykonywany przez moduł skryptu.</span><span class="sxs-lookup"><span data-stu-id="581f1-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="581f1-111">Począwszy od pomocy technicznej dla klas programu PowerShell w wersji 5 schematu i wdrażania zarówno można zdefiniować w klasie.</span><span class="sxs-lookup"><span data-stu-id="581f1-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="581f1-112">W następujących tematach opisano szczegółowo w sposób tworzenia zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="581f1-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="581f1-113">Pisanie niestandardowych zasobów DSC z MOF</span><span class="sxs-lookup"><span data-stu-id="581f1-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="581f1-114">Wdrażanie zasobów DSC w języku C#</span><span class="sxs-lookup"><span data-stu-id="581f1-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="581f1-115">Pisanie niestandardowych zasobów DSC z klasami programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="581f1-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="581f1-116">Zasoby złożonego: jako zasób przy użyciu konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="581f1-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="581f1-117">Przy użyciu narzędzia Projektant zasobów</span><span class="sxs-lookup"><span data-stu-id="581f1-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)