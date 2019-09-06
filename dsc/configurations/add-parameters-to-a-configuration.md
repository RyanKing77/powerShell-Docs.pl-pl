---
ms.date: 12/12/2018
keywords: DSC, PowerShell, zasób, Galeria, konfiguracja
title: Dodawanie parametrów do konfiguracji
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386315"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="6c3bd-103">Dodawanie parametrów do konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6c3bd-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="6c3bd-104">Podobnie jak w przypadku funkcji, [konfiguracje](configurations.md) mogą być sparametryzowane, aby umożliwić większą konfigurację dynamiczną na podstawie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="6c3bd-105">Kroki są podobne do tych opisanych w [funkcjach z parametrami](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="6c3bd-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="6c3bd-106">Ten przykład rozpoczyna się od podstawowej konfiguracji, która konfiguruje "bufor" usługi jako "uruchomiona".</span><span class="sxs-lookup"><span data-stu-id="6c3bd-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="6c3bd-107">Wbudowane parametry konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6c3bd-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="6c3bd-108">W przeciwieństwie do funkcji chociaż atrybut [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) nie dodaje żadnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="6c3bd-109">Oprócz [typowych parametrów](/powershell/module/microsoft.powershell.core/about/about_commonparameters)konfiguracje mogą również używać następujących wbudowanych parametrów, bez konieczności definiowania ich.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="6c3bd-110">Parametr</span><span class="sxs-lookup"><span data-stu-id="6c3bd-110">Parameter</span></span>  |<span data-ttu-id="6c3bd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6c3bd-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="6c3bd-112">Używane do definiowania [konfiguracji złożonych](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6c3bd-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="6c3bd-113">Używane do definiowania [konfiguracji złożonych](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6c3bd-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="6c3bd-114">Używane do definiowania [konfiguracji złożonych](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="6c3bd-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="6c3bd-115">Służy do przekazywania [danych konfiguracji](configData.md) strukturalnej do użycia w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="6c3bd-116">Służy do określania miejsca, w\<którym\>zostanie skompilowany plik "ComputerName. MOF"</span><span class="sxs-lookup"><span data-stu-id="6c3bd-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="6c3bd-117">Dodawanie własnych parametrów do konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6c3bd-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="6c3bd-118">Oprócz wbudowanych parametrów można także dodać własne parametry do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="6c3bd-119">Blok parametrów przechodzi bezpośrednio wewnątrz deklaracji konfiguracji, podobnie jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="6c3bd-120">Blok parametrów konfiguracyjnych powinien znajdować się poza deklaracjami **węzłów** i przekraczać wszystkie instrukcje *importu* .</span><span class="sxs-lookup"><span data-stu-id="6c3bd-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="6c3bd-121">Dodając parametry, można sprawić, aby konfiguracje były bardziej niezawodne i dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="6c3bd-122">Dodaj parametr ComputerName</span><span class="sxs-lookup"><span data-stu-id="6c3bd-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="6c3bd-123">Pierwszy parametr, który można dodać, to `-Computername` parametr, dzięki czemu można dynamicznie kompilować plik ". MOF" dla każdego `-Computername` przekazanego do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="6c3bd-124">Podobnie jak funkcje, można również zdefiniować wartość domyślną, na wypadek, gdy użytkownik nie przekaże wartości dla`-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="6c3bd-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="6c3bd-125">W ramach konfiguracji można określić `-ComputerName` parametr podczas definiowania bloku węzła.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="6c3bd-126">Wywoływanie konfiguracji za pomocą parametrów</span><span class="sxs-lookup"><span data-stu-id="6c3bd-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="6c3bd-127">Po dodaniu parametrów do konfiguracji można użyć ich w taki sam sposób, jak w przypadku polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="6c3bd-128">Kompilowanie wielu plików MOF</span><span class="sxs-lookup"><span data-stu-id="6c3bd-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="6c3bd-129">Blok węzła może również akceptować rozdzieloną przecinkami listę nazw komputerów i generować pliki "MOF" dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="6c3bd-130">Poniższy przykład umożliwia wygenerowanie plików "MOF" dla wszystkich komputerów przewidzianych do `-ComputerName` parametru.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="6c3bd-131">Zaawansowane parametry w konfiguracjach</span><span class="sxs-lookup"><span data-stu-id="6c3bd-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="6c3bd-132">Oprócz `-ComputerName` parametru można dodać parametry dla nazwy usługi i stanu.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="6c3bd-133">Poniższy przykład dodaje blok parametrów z `-ServiceName` parametrem i używa go do dynamicznego definiowania bloku zasobów **usługi** .</span><span class="sxs-lookup"><span data-stu-id="6c3bd-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="6c3bd-134">Dodaje `-State` również parametr do dynamicznego definiowania **stanu** w bloku zasobów **usługi** .</span><span class="sxs-lookup"><span data-stu-id="6c3bd-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="6c3bd-135">W większej liczbie scenariuszy advacned może być bardziej zrozumiałe przeniesienie danych dynamicznych do [danych konfiguracji](configData.md)strukturalnej.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="6c3bd-136">Przykładowa konfiguracja ma teraz wartość dynamiczną `$ServiceName`, ale jeśli nie zostanie określona, kompilacja powoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="6c3bd-137">Możesz dodać wartość domyślną, jak w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="6c3bd-138">W tym wystąpieniu sprawiasz, że po prostu wymusisz, że użytkownik może określić wartość `$ServiceName` parametru.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="6c3bd-139">Ten `parameter` atrybut umożliwia dodanie dalszej obsługi weryfikacji i potoku do parametrów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="6c3bd-140">Przed dowolnymi deklaracjami parametrów `parameter` Dodaj blok atrybutu jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="6c3bd-141">Można określić argumenty dla każdego `parameter` atrybutu, aby kontrolować aspekty zdefiniowanego parametru.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="6c3bd-142">Poniższy przykład wykonuje `$ServiceName` parametr **obowiązkowy** .</span><span class="sxs-lookup"><span data-stu-id="6c3bd-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="6c3bd-143">Dla parametru, chcemy uniemożliwić użytkownikowi Określanie wartości spoza wstępnie zdefiniowanego zestawu (na przykład uruchomionego, zatrzymanego), `ValidationSet*`aby użytkownik mógł określić wartości spoza wstępnie zdefiniowanego zestawu (na przykład uruchomione, `$State` Zatrzymane).</span><span class="sxs-lookup"><span data-stu-id="6c3bd-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="6c3bd-144">Poniższy przykład dodaje `ValidationSet` atrybut `$State` do parametru.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="6c3bd-145">Ponieważ nie chcemy, aby `$State` parametr był **obowiązkowy**, należy dodać do niego wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="6c3bd-146">Nie trzeba określać `parameter` atrybutu przy `validation` użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="6c3bd-147">Więcej informacji na temat `parameter` atrybutów i poprawności można znaleźć w [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="6c3bd-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="6c3bd-148">Pełna konfiguracja sparametryzowanej</span><span class="sxs-lookup"><span data-stu-id="6c3bd-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="6c3bd-149">Mamy teraz konfigurację sparametryzowanej, która wymusza użytkownikowi określenie `-InstanceName`, `-ServiceName`i sprawdza poprawność `-State` parametru.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="6c3bd-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c3bd-150">See also</span></span>

- [<span data-ttu-id="6c3bd-151">Pomoc dotycząca zapisu konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="6c3bd-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="6c3bd-152">Konfiguracje dynamiczne</span><span class="sxs-lookup"><span data-stu-id="6c3bd-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="6c3bd-153">Używanie danych konfiguracji w konfiguracjach</span><span class="sxs-lookup"><span data-stu-id="6c3bd-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="6c3bd-154">Oddziel dane dotyczące konfiguracji i środowiska</span><span class="sxs-lookup"><span data-stu-id="6c3bd-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
