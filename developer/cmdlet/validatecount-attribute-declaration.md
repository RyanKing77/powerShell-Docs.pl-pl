---
title: Deklaracji atrybutu ValidateCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983902"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="0650f-102">ValidateCount, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="0650f-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="0650f-103">Atrybut ValidateCount określa minimalną i maksymalną liczbę argumentów, które mogą uzyskać parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0650f-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="0650f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0650f-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="0650f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0650f-105">Parameters</span></span>

<span data-ttu-id="0650f-106">`MinLength` ([System.Int32][]) wymagane.</span><span class="sxs-lookup"><span data-stu-id="0650f-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="0650f-107">Określa minimalną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="0650f-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="0650f-108">`MaxLength`([System.Int32][]) wymagane.</span><span class="sxs-lookup"><span data-stu-id="0650f-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="0650f-109">Określa maksymalną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="0650f-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="0650f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0650f-110">Remarks</span></span>

- <span data-ttu-id="0650f-111">Aby uzyskać więcej informacji o tym, jak można zadeklarować tego atrybutu, zobacz [sposób sprawdzania poprawności liczby argumentów][].</span><span class="sxs-lookup"><span data-stu-id="0650f-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="0650f-112">Jeśli ten atrybut nie zostanie wywołany, z odpowiadającym mu parametrem polecenia cmdlet może mieć dowolną liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="0650f-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="0650f-113">Środowisko wykonawcze programu Windows PowerShell zgłasza błąd w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="0650f-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="0650f-114">`MinLength` i `MaxLength` parametry atrybutów nie mają wartości typu [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="0650f-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="0650f-115">Wartość `MaxLength` parametru atrybutu jest mniejsza niż wartość `MinLength` parametr atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0650f-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="0650f-116">Atrybut ValidateCount jest definiowany przez [System.Management.Automation.ValidateCountAttribute][] klasy.</span><span class="sxs-lookup"><span data-stu-id="0650f-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0650f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0650f-117">See Also</span></span>

<span data-ttu-id="0650f-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="0650f-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="0650f-119">[Sposób sprawdzania poprawności liczby argumentów][]</span><span class="sxs-lookup"><span data-stu-id="0650f-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="0650f-120">[Zapisywanie polecenia Cmdlet programu Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="0650f-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Sposób sprawdzania poprawności liczby argumentów]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Zapisywanie polecenia Cmdlet programu Windows PowerShell]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
