---
title: Deklaracji atrybutu ValidatePattern | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848825"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="47a2e-102">ValidatePattern, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="47a2e-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="47a2e-103">Atrybut ValidatePattern Określa wzorzec wyrażenia regularnego weryfikującego argument parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="47a2e-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="47a2e-104">Ten atrybut umożliwia także przez funkcje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47a2e-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="47a2e-105">Wywołana ValidatePattern w ramach polecenia cmdlet środowiska uruchomieniowego programu Windows PowerShell argument parametru polecenia cmdlet jest konwertowany na ciąg, a następnie porównuje ciąg do wzorca, dostarczone przez atrybut ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="47a2e-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="47a2e-106">Polecenie cmdlet jest uruchamiane tylko wtedy, gdy jest to reprezentacja ciągu przekonwertowanego argument i podanego wzorca dopasowania.</span><span class="sxs-lookup"><span data-stu-id="47a2e-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="47a2e-107">Jeśli nie są zgodne, zostanie zgłoszony błąd w czasie wykonywania programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47a2e-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="47a2e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="47a2e-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="47a2e-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="47a2e-109">Parameters</span></span>

<span data-ttu-id="47a2e-110">`RegexString` ([System.String](/dotnet/api/System.String)) wymagane.</span><span class="sxs-lookup"><span data-stu-id="47a2e-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="47a2e-111">Określa wyrażenie regularne, która weryfikuje argument parametru.</span><span class="sxs-lookup"><span data-stu-id="47a2e-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="47a2e-112">Opcje ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) o nazwie parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="47a2e-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="47a2e-113">Bitowa kombinacja Określa [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flagi, które określają opcje wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="47a2e-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="47a2e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47a2e-114">Remarks</span></span>

- <span data-ttu-id="47a2e-115">Ten atrybut może służyć tylko raz dla parametru.</span><span class="sxs-lookup"><span data-stu-id="47a2e-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="47a2e-116">Możesz użyć `Option` parametru atrybutu do dalszego określenia wzorzec.</span><span class="sxs-lookup"><span data-stu-id="47a2e-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="47a2e-117">Na przykład umożliwia wzorca z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="47a2e-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="47a2e-118">Jeśli ten atrybut jest stosowany do kolekcji, każdy element w kolekcji musi być zgodna z wzorcem.</span><span class="sxs-lookup"><span data-stu-id="47a2e-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="47a2e-119">Atrybut ValidatePattern jest definiowany przez [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="47a2e-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="47a2e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47a2e-120">See Also</span></span>

[<span data-ttu-id="47a2e-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="47a2e-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="47a2e-122">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="47a2e-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
