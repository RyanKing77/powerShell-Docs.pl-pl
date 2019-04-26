---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Korzystanie z danych konfiguracji
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080224"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="6078c-103">Korzystanie z danych konfiguracji w DSC</span><span class="sxs-lookup"><span data-stu-id="6078c-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="6078c-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6078c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6078c-105">Za pomocą wbudowanych DSC **ConfigurationData** parametru, można zdefiniować dane, które mogą być używane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6078c-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="6078c-106">Dzięki temu można utworzyć jednej konfiguracji, który może służyć do wielu węzłów lub w różnych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="6078c-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="6078c-107">Na przykład jeśli tworzysz aplikację, można użyć jednej konfiguracji dla środowisk środowisk deweloperskich i produkcyjnych i użyj dane konfiguracyjne, aby określić dane dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="6078c-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="6078c-108">W tym temacie opisano strukturę **ConfigurationData** hashtable.</span><span class="sxs-lookup"><span data-stu-id="6078c-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="6078c-109">Przykłady sposobu używania danych konfiguracji, zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="6078c-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="6078c-110">Typowy parametr danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6078c-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="6078c-111">Konfiguracja DSC przyjmuje typowego parametru **ConfigurationData**, należy określić podczas kompilacji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6078c-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="6078c-112">Aby dowiedzieć się, jak kompilowanie konfiguracji, zobacz [konfiguracje DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6078c-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="6078c-113">**ConfigurationData** parametr ma tablicę skrótów, którą musi mieć co najmniej jeden klucz o nazwie **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="6078c-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="6078c-114">Może też mieć co najmniej jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="6078c-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="6078c-115">Przykłady w tym temacie, użyj jednego dodatkowego klucza (innych niż nazwany **AllNodes** klucza) o nazwie `NonNodeData`, ale może zawierać dowolną liczbę dodatkowych kluczy i nazwij je, co tylko chcesz.</span><span class="sxs-lookup"><span data-stu-id="6078c-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="6078c-116">Wartość **AllNodes** klucza jest tablicą.</span><span class="sxs-lookup"><span data-stu-id="6078c-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="6078c-117">Każdy element tej tablicy jest również tabelę mieszania, który musi mieć co najmniej jeden klucz o nazwie **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="6078c-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="6078c-118">Inne klucze można dodać do każdej tabeli wyznaczania wartości skrótu:</span><span class="sxs-lookup"><span data-stu-id="6078c-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="6078c-119">Aby zastosować właściwości dla wszystkich węzłów, można utworzyć członkiem **AllNodes** tablica, która ma **NodeName** z `*`.</span><span class="sxs-lookup"><span data-stu-id="6078c-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="6078c-120">Na przykład, aby nadać każdy węzeł `LogPath` właściwości, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="6078c-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="6078c-121">To jest odpowiednikiem dodawania właściwości o nazwie `LogPath` o wartości `"C:\Logs"` do każdego z innych bloków (`VM-1`, `VM-2`, i `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="6078c-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="6078c-122">Definiowanie hashtable danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6078c-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="6078c-123">Można zdefiniować **ConfigurationData** jako zmienną, w tym samym pliku skryptu konfiguracji (jak w naszych poprzednich przykładach) lub w osobnym `.psd1` pliku.</span><span class="sxs-lookup"><span data-stu-id="6078c-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="6078c-124">Aby zdefiniować **ConfigurationData** w `.psd1` plików, utworzyć plik, który zawiera tylko tablicy skrótów, który reprezentuje dane konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6078c-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="6078c-125">Na przykład można utworzyć pliku o nazwie `MyData.psd1` z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="6078c-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="6078c-126">Kompilowanie konfiguracji z danymi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6078c-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="6078c-127">Aby skompilować konfigurację, dla którego zdefiniowano dane konfiguracji, przekazać dane konfiguracji jako wartość **ConfigurationData** parametru.</span><span class="sxs-lookup"><span data-stu-id="6078c-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="6078c-128">Spowoduje to utworzenie pliku MOF dla każdej pozycji w **AllNodes** tablicy.</span><span class="sxs-lookup"><span data-stu-id="6078c-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="6078c-129">Każdy plik MOF będzie miała z `NodeName` właściwość odpowiadający mu wpis w tablicy.</span><span class="sxs-lookup"><span data-stu-id="6078c-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="6078c-130">Na przykład, jeśli zdefiniujesz dane konfiguracji, podobnie jak w `MyData.psd1` pliku powyżej kompilacji konfiguracji będzie utworzenie ich obu `VM-1.mof` i `VM-2.mof` plików.</span><span class="sxs-lookup"><span data-stu-id="6078c-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="6078c-131">Kompilowanie konfiguracji z danymi konfiguracji przy użyciu zmiennej</span><span class="sxs-lookup"><span data-stu-id="6078c-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="6078c-132">Na korzystanie z danych konfiguracji, który jest zdefiniowany jako zmienną, w tym samym `.ps1` pliku konfiguracji, przekazać nazwę zmiennej jako wartości **ConfigurationData** parametru podczas kompilowania konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="6078c-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="6078c-133">Kompilowanie konfiguracji w danych konfiguracji, używając pliku danych</span><span class="sxs-lookup"><span data-stu-id="6078c-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="6078c-134">Aby korzystać z danych konfiguracji, która jest zdefiniowana w pliku psd1, przekazujesz ścieżkę i nazwę tego pliku jako wartość **ConfigurationData** parametru podczas kompilowania konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="6078c-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="6078c-135">Za pomocą zmiennych danych konfiguracji w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6078c-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="6078c-136">DSC udostępnia następujące zmienne specjalne, których można użyć w skrypcie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="6078c-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="6078c-137">**$AllNodes** odwołuje się do całej kolekcji węzłów zdefiniowane w **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="6078c-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="6078c-138">Można filtrować **AllNodes** kolekcji przy użyciu **. WHERE()** i **. Metody ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="6078c-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="6078c-139">**ConfigurationData** odwołuje się do tabeli całego wyznaczania wartości skrótu, który jest przekazywany jako parametr podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6078c-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="6078c-140">**MyTypeName** zawiera [konfiguracji](configurations.md) zmienna zostanie użyta w nazwie.</span><span class="sxs-lookup"><span data-stu-id="6078c-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="6078c-141">Na przykład w konfiguracji `MyDscConfiguration`, `$MyTypeName` będzie mieć wartość `MyDscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="6078c-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="6078c-142">**Węzeł** odwołuje się do określonego wpisu w **AllNodes** kolekcji po jest filtrowany za pomocą **. WHERE()** lub **. Metody ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="6078c-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="6078c-143">Możesz dowiedzieć się więcej o tych metodach w [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="6078c-143">You can read more about these methods in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="6078c-144">Korzystanie z danych niż węzła</span><span class="sxs-lookup"><span data-stu-id="6078c-144">Using non-node data</span></span>

<span data-ttu-id="6078c-145">Jak widzieliśmy w poprzednich przykładach **ConfigurationData** hashtable może mieć co najmniej jeden klucz oprócz wymaganych **AllNodes** klucza.</span><span class="sxs-lookup"><span data-stu-id="6078c-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="6078c-146">W przykładach w tym temacie, firma Microsoft ma używany tylko jeden dodatkowy węzeł o nazwie go `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="6078c-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="6078c-147">Można jednak zdefiniować dowolną liczbę dodatkowych kluczy i nazwy dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="6078c-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="6078c-148">Na przykład przy użyciu danych węzeł-zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="6078c-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6078c-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6078c-149">See Also</span></span>

- [<span data-ttu-id="6078c-150">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6078c-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="6078c-151">Konfiguracje DSC</span><span class="sxs-lookup"><span data-stu-id="6078c-151">DSC Configurations</span></span>](configurations.md)