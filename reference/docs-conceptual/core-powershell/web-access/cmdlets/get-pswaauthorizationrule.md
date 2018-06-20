---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188912"
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="09b35-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="09b35-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="09b35-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="09b35-104">SYNOPSIS</span></span>

<span data-ttu-id="09b35-105">Zwraca zestaw reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="09b35-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="09b35-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="09b35-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="09b35-107">ID</span><span class="sxs-lookup"><span data-stu-id="09b35-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="09b35-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="09b35-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="09b35-109">OPIS</span><span class="sxs-lookup"><span data-stu-id="09b35-109">DESCRIPTION</span></span>

<span data-ttu-id="09b35-110">**Get-PswaAuthorizationRule** polecenie cmdlet zwraca zestaw reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="09b35-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="09b35-111">Jeśli żadna **identyfikator** parametru ani **RuleName** określony parametr, a następnie to polecenie cmdlet wyświetla listę wszystkich reguł.</span><span class="sxs-lookup"><span data-stu-id="09b35-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="09b35-112">**Identyfikator** parametru może służyć do filtrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="09b35-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="09b35-113">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="09b35-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="09b35-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="09b35-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="09b35-115">Określa identyfikatory (ID) reguł, które należy uzyskać tego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09b35-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="09b35-116">Jeżeli nie określono żadnych identyfikatorów, to polecenie cmdlet zwraca wszystkie reguły autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="09b35-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="09b35-117">Aliasy</span><span class="sxs-lookup"><span data-stu-id="09b35-117">Aliases</span></span>                              | <span data-ttu-id="09b35-118">brak</span><span class="sxs-lookup"><span data-stu-id="09b35-118">none</span></span>                                 |
| <span data-ttu-id="09b35-119">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="09b35-119">Required?</span></span>                            | <span data-ttu-id="09b35-120">false</span><span class="sxs-lookup"><span data-stu-id="09b35-120">false</span></span>                                |
| <span data-ttu-id="09b35-121">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="09b35-121">Position?</span></span>                            | <span data-ttu-id="09b35-122">2</span><span class="sxs-lookup"><span data-stu-id="09b35-122">2</span></span>                                    |
| <span data-ttu-id="09b35-123">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="09b35-123">Default Value</span></span>                        | <span data-ttu-id="09b35-124">brak</span><span class="sxs-lookup"><span data-stu-id="09b35-124">none</span></span>                                 |
| <span data-ttu-id="09b35-125">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="09b35-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="09b35-126">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="09b35-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="09b35-127">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="09b35-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="09b35-128">false</span><span class="sxs-lookup"><span data-stu-id="09b35-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="09b35-129">-RuleName&lt;ciągu\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="09b35-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="09b35-130">Określa nazwy reguł autoryzacji do pobrania.</span><span class="sxs-lookup"><span data-stu-id="09b35-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="09b35-131">Ten parametr zwraca wszystkie reguły odpowiadające dokładnie nazwy reguł w tej tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="09b35-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="09b35-132">Aliasy</span><span class="sxs-lookup"><span data-stu-id="09b35-132">Aliases</span></span>                              | <span data-ttu-id="09b35-133">brak</span><span class="sxs-lookup"><span data-stu-id="09b35-133">none</span></span>                                 |
| <span data-ttu-id="09b35-134">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="09b35-134">Required?</span></span>                            | <span data-ttu-id="09b35-135">true</span><span class="sxs-lookup"><span data-stu-id="09b35-135">true</span></span>                                 |
| <span data-ttu-id="09b35-136">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="09b35-136">Position?</span></span>                            | <span data-ttu-id="09b35-137">2</span><span class="sxs-lookup"><span data-stu-id="09b35-137">2</span></span>                                    |
| <span data-ttu-id="09b35-138">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="09b35-138">Default Value</span></span>                        | <span data-ttu-id="09b35-139">brak</span><span class="sxs-lookup"><span data-stu-id="09b35-139">none</span></span>                                 |
| <span data-ttu-id="09b35-140">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="09b35-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="09b35-141">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="09b35-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="09b35-142">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="09b35-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="09b35-143">false</span><span class="sxs-lookup"><span data-stu-id="09b35-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="09b35-144">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="09b35-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="09b35-145">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="09b35-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="09b35-146">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="09b35-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="09b35-147">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="09b35-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="09b35-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="09b35-148">int\[\]</span></span>

<span data-ttu-id="09b35-149">To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablica wartości typu string jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="09b35-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="09b35-150">Ciąg\[\]</span><span class="sxs-lookup"><span data-stu-id="09b35-150">String\[\]</span></span>

<span data-ttu-id="09b35-151">To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablica wartości typu string jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="09b35-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="09b35-152">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="09b35-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="09b35-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="09b35-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="09b35-154">To polecenie cmdlet tworzy obiekt PswaAuthorizationRule jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="09b35-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="09b35-155">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="09b35-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="09b35-156">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="09b35-156">EXAMPLE 1</span></span>

<span data-ttu-id="09b35-157">W tym przykładzie pobiera wszystkie reguły.</span><span class="sxs-lookup"><span data-stu-id="09b35-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="09b35-158">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="09b35-158">EXAMPLE 2</span></span>

<span data-ttu-id="09b35-159">W tym przykładzie pobiera reguła o identyfikatorze *2*.</span><span class="sxs-lookup"><span data-stu-id="09b35-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="09b35-160">PRZYKŁAD 3 {.subHeading #example-3}</span><span class="sxs-lookup"><span data-stu-id="09b35-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="09b35-161">W tym przykładzie pokazano, jak polecenie cmdlet przyjmuje wartość z potoku.</span><span class="sxs-lookup"><span data-stu-id="09b35-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="09b35-162">Identyfikator reguły i nazwę reguły są przekazywane w tym poleceniu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="09b35-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="09b35-163">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="09b35-163">Related topics</span></span>

- [<span data-ttu-id="09b35-164">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="09b35-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="09b35-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="09b35-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="09b35-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="09b35-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="09b35-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="09b35-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)