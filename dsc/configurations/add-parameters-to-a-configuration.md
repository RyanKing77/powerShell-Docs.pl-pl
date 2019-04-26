---
ms.date: 12/12/2018
keywords: DSC, powershell, zasób, galerii, Instalator
title: Dodawanie parametrów do konfiguracji
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080260"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="7bbe8-103">Dodawanie parametrów do konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7bbe8-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="7bbe8-104">Funkcje, takie jak [konfiguracje](configurations.md) mogą być parametryzowane, aby umożliwić bardziej dynamiczne konfiguracje oparte na danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="7bbe8-105">Kroki są podobne do tych opisanych w [funkcje z parametrami](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="7bbe8-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="7bbe8-106">W tym przykładzie rozpoczyna się od podstawowej konfiguracji, który konfiguruje usługę "Buforu", "Działa".</span><span class="sxs-lookup"><span data-stu-id="7bbe8-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="7bbe8-107">Wbudowane parametry konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7bbe8-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="7bbe8-108">W przeciwieństwie do funkcji, [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) atrybut dodaje żadnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="7bbe8-109">Oprócz [wspólne parametry](/powershell/module/microsoft.powershell.core/about/about_commonparameters), konfiguracje można również użyć następujące wbudowane parametrów, bez konieczności ich.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="7bbe8-110">Parametr</span><span class="sxs-lookup"><span data-stu-id="7bbe8-110">Parameter</span></span>  |<span data-ttu-id="7bbe8-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7bbe8-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="7bbe8-112">Używanego przy definiowaniu [złożonej konfiguracji](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="7bbe8-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="7bbe8-113">Używanego przy definiowaniu [złożonej konfiguracji](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="7bbe8-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="7bbe8-114">Używanego przy definiowaniu [złożonej konfiguracji](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="7bbe8-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="7bbe8-115">Służy do przekazywania w strukturze [dane konfiguracyjne](configData.md) do użytku w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="7bbe8-116">Pozwala określić, gdzie Twoje "\<computername\>MOF" zostanie skompilowany plik</span><span class="sxs-lookup"><span data-stu-id="7bbe8-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="7bbe8-117">Dodawanie własnych parametrów konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7bbe8-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="7bbe8-118">Oprócz wbudowanych parametrów można również dodać własne parametry do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="7bbe8-119">Blok parametrów przechodzi bezpośrednio wewnątrz deklaracji konfiguracji, podobnie jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="7bbe8-120">Blok parametrów konfiguracji powinien znajdować się poza dowolne **węzła** deklaracji i nowszych dowolne *zaimportować* instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="7bbe8-121">Dodając parametry, można tworzyć konfiguracje bardziej niezawodnych i dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="7bbe8-122">Dodaj parametr nazwa_komputera</span><span class="sxs-lookup"><span data-stu-id="7bbe8-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="7bbe8-123">Pierwszy parametr, można dodać jest `-Computername` parametru, więc możesz dynamicznie skompilować pliku "MOF" dla każdego `-Computername` przekazać do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="7bbe8-124">Takie jak Functions można również zdefiniować wartość domyślna w przypadku, gdy użytkownik nie przekaże wartości `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="7bbe8-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="7bbe8-125">W ramach konfiguracji, możesz określić swoje `-ComputerName` parametru podczas definiowania bloku z węzła.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="7bbe8-126">Wywoływanie konfigurację z parametrami</span><span class="sxs-lookup"><span data-stu-id="7bbe8-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="7bbe8-127">Po dodaniu parametry konfiguracji, można je tak, jak za pomocą polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="7bbe8-128">Kompilowanie wielu plików MOF</span><span class="sxs-lookup"><span data-stu-id="7bbe8-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="7bbe8-129">Blok węzła także zaakceptować wartość rozdzielaną przecinkami listę nazw komputerów i będzie generować pliki "MOF" dla każdego.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="7bbe8-130">Można uruchomić poniższy przykład, aby wygenerować pliki "MOF" dla wszystkich komputerów, przekazywane do `-ComputerName` parametru.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="7bbe8-131">Zaawansowane parametry w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7bbe8-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="7bbe8-132">Oprócz `-ComputerName` parametru, możemy dodać parametry dla nazwy usługi i stanu.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="7bbe8-133">Poniższy przykład umożliwia dodanie bloku parametrów, za pomocą `-ServiceName` parametru i używa go w celu dynamicznego definiowania **usługi** bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="7bbe8-134">Dodaje także `-State` parametr w celu dynamicznego definiowania **stanu** w **usługi** bloku zasobów.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="7bbe8-135">W dalszych scenariuszach advacned, może być bardziej zrozumiałe, aby przenieść dane dynamiczne do ze strukturą [dane konfiguracyjne](configData.md).</span><span class="sxs-lookup"><span data-stu-id="7bbe8-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="7bbe8-136">Przykład konfiguracji teraz przyjmuje dynamiczny `$ServiceName`, ale jeśli nie jest określony, kompilacja będzie skutkowało błędem.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="7bbe8-137">Można dodać wartość domyślną, np. w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="7bbe8-138">W tym wystąpieniu, więcej sensu można po prostu zmusza użytkownika do określenia wartości `$ServiceName` parametru.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="7bbe8-139">`parameter` Atrybut można dodawać dodatkowe sprawdzanie poprawności i potoku obsługi parametrów konfiguracji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="7bbe8-140">Nad dowolnym deklaracji parametru Dodaj `parameter` bloku attribute, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="7bbe8-141">Można określić argumenty do każdego `parameter` atrybutu do sterowania aspektami zdefiniowany parametr.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="7bbe8-142">Poniższy przykład wykonuje `$ServiceName` **obowiązkowe** parametru.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="7bbe8-143">Dla `$State` parametru, prosimy o poświęcenie zapobiec określania wartości poza zestaw wstępnie zdefiniowanych przez użytkownika (takie jak uruchamianie, zatrzymane) `ValidationSet*`atrybut może uniemożliwić użytkownikowi korzystanie ze określania wartości poza zestaw wstępnie zdefiniowanych (na przykład działanie Zatrzymana).</span><span class="sxs-lookup"><span data-stu-id="7bbe8-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="7bbe8-144">W poniższym przykładzie dodano `ValidationSet` atrybutu `$State` parametru.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="7bbe8-145">Ponieważ nie chcemy mieć `$State` parametru **obowiązkowe**, musimy dodać wartość domyślną dla niego.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="7bbe8-146">Nie należy określić `parameter` atrybutu przy użyciu `validation` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="7bbe8-147">Przeczytaj więcej o `parameter` i sprawdzanie poprawności atrybutów w [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7bbe8-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="7bbe8-148">W pełni sparametryzowane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7bbe8-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="7bbe8-149">W efekcie powstał sparametryzowane konfigurację, która wymusza użytkownikowi na określenie `-InstanceName`, `-ServiceName`i sprawdza poprawność `-State` parametru.</span><span class="sxs-lookup"><span data-stu-id="7bbe8-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="7bbe8-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bbe8-150">See also</span></span>

- [<span data-ttu-id="7bbe8-151">Zapis pomocy dotyczących konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="7bbe8-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="7bbe8-152">Dynamiczne konfiguracje</span><span class="sxs-lookup"><span data-stu-id="7bbe8-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="7bbe8-153">Korzystanie z danych konfiguracji w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7bbe8-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="7bbe8-154">Osobne dane konfiguracji i środowiska</span><span class="sxs-lookup"><span data-stu-id="7bbe8-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
