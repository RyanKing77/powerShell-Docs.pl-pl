---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób archiwum DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688406"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="87fcc-103">Zasób archiwum DSC</span><span class="sxs-lookup"><span data-stu-id="87fcc-103">DSC Archive Resource</span></span>

> <span data-ttu-id="87fcc-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="87fcc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="87fcc-105">Zasób archiwum w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do rozpakowywania plików archiwów (.zip) w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="87fcc-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="87fcc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="87fcc-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="87fcc-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="87fcc-107">Properties</span></span>

|  <span data-ttu-id="87fcc-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="87fcc-108">Property</span></span>  |  <span data-ttu-id="87fcc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="87fcc-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="87fcc-110">Lokalizacja docelowa</span><span class="sxs-lookup"><span data-stu-id="87fcc-110">Destination</span></span>| <span data-ttu-id="87fcc-111">Określa lokalizację, w której chcesz upewnić się, że zawartość archiwum zostały wyodrębnione.</span><span class="sxs-lookup"><span data-stu-id="87fcc-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="87fcc-112">Ścieżka</span><span class="sxs-lookup"><span data-stu-id="87fcc-112">Path</span></span>| <span data-ttu-id="87fcc-113">Określa ścieżkę źródłową pliku archiwum.</span><span class="sxs-lookup"><span data-stu-id="87fcc-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="87fcc-114">__Sumy kontrolnej__</span><span class="sxs-lookup"><span data-stu-id="87fcc-114">__Checksum__</span></span>| <span data-ttu-id="87fcc-115">Definiuje typ używany do określenia, czy dwa pliki są takie same.</span><span class="sxs-lookup"><span data-stu-id="87fcc-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="87fcc-116">Jeśli __sumy kontrolnej__ nie jest określona, tylko nazwa pliku lub katalogu jest używana do porównania.</span><span class="sxs-lookup"><span data-stu-id="87fcc-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="87fcc-117">Prawidłowe wartości to: SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji, none (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="87fcc-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="87fcc-118">Jeśli określisz __sumy kontrolnej__ bez __weryfikacji__, konfiguracja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="87fcc-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="87fcc-119">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="87fcc-119">Ensure</span></span>| <span data-ttu-id="87fcc-120">Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w __docelowy__.</span><span class="sxs-lookup"><span data-stu-id="87fcc-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="87fcc-121">Ustaw tę właściwość na __obecne__ zapewnienie zawartość istnieje.</span><span class="sxs-lookup"><span data-stu-id="87fcc-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="87fcc-122">Ustaw ją na __nieobecne__ aby upewnić się, nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="87fcc-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="87fcc-123">Wartość domyślna to __obecne__.</span><span class="sxs-lookup"><span data-stu-id="87fcc-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="87fcc-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="87fcc-124">DependsOn</span></span> | <span data-ttu-id="87fcc-125">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="87fcc-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="87fcc-126">Na przykład, jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić najpierw ResourceName i jego typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="87fcc-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="87fcc-127">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="87fcc-127">Validate</span></span>| <span data-ttu-id="87fcc-128">Używa właściwości sumy kontrolnej, aby ustalić, czy podpis jest zgodna z archiwum.</span><span class="sxs-lookup"><span data-stu-id="87fcc-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="87fcc-129">Jeśli określisz sumy kontrolnej bez sprawdzania poprawności, konfiguracja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="87fcc-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="87fcc-130">Jeśli określisz weryfikacji bez sumy kontrolnej, sumy kontrolnej algorytmu SHA-256 jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="87fcc-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="87fcc-131">Force</span><span class="sxs-lookup"><span data-stu-id="87fcc-131">Force</span></span>| <span data-ttu-id="87fcc-132">Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="87fcc-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="87fcc-133">Przy użyciu właściwości życie zastępuje takie błędy.</span><span class="sxs-lookup"><span data-stu-id="87fcc-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="87fcc-134">Wartość domyślna to False.</span><span class="sxs-lookup"><span data-stu-id="87fcc-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="87fcc-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="87fcc-135">Example</span></span>

<span data-ttu-id="87fcc-136">Poniższy przykład pokazuje, jak używać zasób archiwum, aby upewnić się, że zawartość pliku archiwum o nazwie Test.zip istnieją i są wyodrębniane w danej lokalizacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="87fcc-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```