---
title: Deklaracji atrybutu ValidateSet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850456"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="69fe7-102">ValidateSet, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="69fe7-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="69fe7-103">Atrybut ValidateSetAttribute określa zestaw możliwych wartości dla parametru w argumencie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69fe7-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="69fe7-104">Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69fe7-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="69fe7-105">Jeśli ten atrybut jest określony, środowisko uruchomieniowe programu Windows PowerShell Określa, czy podany argument parametru polecenia cmdlet pasuje do elementu w zestawie podany element.</span><span class="sxs-lookup"><span data-stu-id="69fe7-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="69fe7-106">Polecenie cmdlet jest uruchamiane tylko wtedy, gdy argument parametru pasuje do elementu w zestawie.</span><span class="sxs-lookup"><span data-stu-id="69fe7-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="69fe7-107">Jeśli nie zostanie znalezione dopasowanie, błąd jest zgłaszany przez środowisko uruchomieniowe programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69fe7-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="69fe7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="69fe7-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="69fe7-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="69fe7-109">Parameters</span></span>

<span data-ttu-id="69fe7-110">`ValidValues` ([System.String](/dotnet/api/System.String)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="69fe7-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="69fe7-111">Określa wartości elementu prawidłowego parametru.</span><span class="sxs-lookup"><span data-stu-id="69fe7-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="69fe7-112">Poniższy przykład pokazuje sposób określania elementu jednego lub wielu elementów.</span><span class="sxs-lookup"><span data-stu-id="69fe7-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="69fe7-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="69fe7-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="69fe7-114">Wartość domyślna `true` wskazuje, że wielkość liter jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="69fe7-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="69fe7-115">Wartość `false` sprawia, że polecenia cmdlet jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="69fe7-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="69fe7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69fe7-116">Remarks</span></span>

- <span data-ttu-id="69fe7-117">Ten atrybut może służyć tylko raz dla parametru.</span><span class="sxs-lookup"><span data-stu-id="69fe7-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="69fe7-118">Jeśli wartość tego parametru jest tablicą, każdy element tablicy muszą być zgodne z elementu zestawu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="69fe7-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="69fe7-119">Atrybut ValidateSetAttribute jest definiowany przez [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="69fe7-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="69fe7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69fe7-120">See Also</span></span>

[<span data-ttu-id="69fe7-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="69fe7-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="69fe7-122">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69fe7-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
