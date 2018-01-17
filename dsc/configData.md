---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Przy użyciu danych konfiguracji"
ms.openlocfilehash: b56a3f970b0b5121585dc4ed2f32da3243b980bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="87a06-103">Przy użyciu danych konfiguracji w konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="87a06-103">Using configuration data in DSC</span></span>

><span data-ttu-id="87a06-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="87a06-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="87a06-105">Za pomocą wbudowanych DSC **ConfigurationData** parametru, można zdefiniować dane, które mogą być używane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87a06-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span> <span data-ttu-id="87a06-106">Dzięki temu można utworzyć pojedynczą konfiguracją, która może służyć do wielu węzłów lub dla różnych środowisk.</span><span class="sxs-lookup"><span data-stu-id="87a06-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span> <span data-ttu-id="87a06-107">Na przykład jeśli tworzysz aplikację, można korzystać z jednej konfiguracji dla środowisk zarówno projektowania i produkcji i korzystać z danych konfiguracji do określania danych dla każdego środowiska.</span><span class="sxs-lookup"><span data-stu-id="87a06-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="87a06-108">W tym temacie opisano strukturę **ConfigurationData** hashtable.</span><span class="sxs-lookup"><span data-stu-id="87a06-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span> <span data-ttu-id="87a06-109">Przykłady sposobu używania danych konfiguracji, zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="87a06-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="87a06-110">Typowy parametr ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="87a06-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="87a06-111">Typowy Parametr przyjmuje konfiguracji DSC **ConfigurationData**, określ, kiedy kompilacja konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87a06-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span> <span data-ttu-id="87a06-112">Informacje o konfiguracjach kompilacji, zobacz [konfiguracji DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="87a06-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="87a06-113">**ConfigurationData** parametr jest hasthtable, który musi mieć co najmniej jeden klucz o nazwie **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="87a06-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span> <span data-ttu-id="87a06-114">Może również mieć co najmniej jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="87a06-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="87a06-115">**Uwaga:** przykłady w tym temacie, użyj jednego klucza dodatkowe (innych niż nazwany **AllNodes** klucza) o nazwie `NonNodeData`, jednak zawierać dowolną liczbę dodatkowych kluczy i nazwy dowolne.</span><span class="sxs-lookup"><span data-stu-id="87a06-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

<span data-ttu-id="87a06-116">Wartość **AllNodes** klucza jest tablicą.</span><span class="sxs-lookup"><span data-stu-id="87a06-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="87a06-117">Każdy element tej tablicy jest również tablicy skrótów, który musi mieć co najmniej jeden klucz o nazwie **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="87a06-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

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

<span data-ttu-id="87a06-118">Kluczy można dodać do każdej tabeli skrótów:</span><span class="sxs-lookup"><span data-stu-id="87a06-118">You can add other keys to each hash table as well:</span></span>

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

<span data-ttu-id="87a06-119">Aby zastosować właściwości dla wszystkich węzłów, można utworzyć członkiem **AllNodes** tablica, która ma **NodeName** z `*`.</span><span class="sxs-lookup"><span data-stu-id="87a06-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span> <span data-ttu-id="87a06-120">Na przykład, w celu każdego węzła `LogPath` właściwości, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="87a06-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

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

<span data-ttu-id="87a06-121">Jest to równoważne dodawania właściwości o nazwie `LogPath` o wartości `"C:\Logs"` do każdego z innych bloków (`VM-1`, `VM-2`, i `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="87a06-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="87a06-122">Definiowanie ConfigurationData hashtable</span><span class="sxs-lookup"><span data-stu-id="87a06-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="87a06-123">Można zdefiniować **ConfigurationData** jako zmiennej w ramach tego samego pliku skryptu jako konfiguracji (jak w naszych przykładach poprzedniej) lub w oddzielnej `.psd1` pliku.</span><span class="sxs-lookup"><span data-stu-id="87a06-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span> <span data-ttu-id="87a06-124">Aby zdefiniować **ConfigurationData** w `.psd1` pliku, Utwórz plik, który zawiera tylko hashtable, który reprezentuje dane konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87a06-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="87a06-125">Na przykład można utworzyć pliku o nazwie `MyData.psd1` z następującą zawartość:</span><span class="sxs-lookup"><span data-stu-id="87a06-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

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

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="87a06-126">Kompilowanie konfiguracji z danymi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87a06-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="87a06-127">Aby skompilować konfiguracji, dla którego zdefiniowano dane konfiguracji, przekazać dane konfiguracji jako wartość **ConfigurationData** parametru.</span><span class="sxs-lookup"><span data-stu-id="87a06-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="87a06-128">Spowoduje to utworzenie pliku MOF dla każdej pozycji w **AllNodes** tablicy.</span><span class="sxs-lookup"><span data-stu-id="87a06-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="87a06-129">Każdy plik MOF będą miały nazwę nadaną przez `NodeName` właściwości odpowiadający mu wpis w tablicy.</span><span class="sxs-lookup"><span data-stu-id="87a06-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="87a06-130">Na przykład, jeśli należy zdefiniować dane konfiguracji, jak w `MyData.psd1` pliku powyżej, kompilowanie konfiguracji spowoduje utworzenie zarówno `VM-1.mof` i `VM-2.mof` plików.</span><span class="sxs-lookup"><span data-stu-id="87a06-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="87a06-131">Kompilowanie konfiguracji z danymi konfiguracji przy użyciu zmiennej</span><span class="sxs-lookup"><span data-stu-id="87a06-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="87a06-132">Aby użyć danych konfiguracji, który jest zdefiniowany jako zmienną, w tym samym `.ps1` pliku jako Konfiguracja, przekaż nazwę zmiennej jako wartości **ConfigurationData** parametr podczas kompilowania konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="87a06-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="87a06-133">Kompilowanie konfiguracji z danymi konfiguracji przy użyciu pliku danych</span><span class="sxs-lookup"><span data-stu-id="87a06-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="87a06-134">Aby korzystać z danych konfiguracji, która jest zdefiniowana w pliku psd1, przekazujesz ścieżkę i nazwę tego pliku jako wartość **ConfigurationData** parametr podczas kompilowania konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="87a06-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="87a06-135">Używanie zmiennych ConfigurationData w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87a06-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="87a06-136">DSC udostępnia trzy zmienne specjalne, których można użyć w skrypcie konfiguracji: **$AllNodes**, **$Node**, i **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="87a06-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="87a06-137">**$AllNodes** odwołuje się do całego kolekcja węzłów zdefiniowane w **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="87a06-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="87a06-138">Można filtrować **AllNodes** kolekcji przy użyciu **. WHERE()** i **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="87a06-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="87a06-139">**Węzeł** odwołuje się do określonego wpisu w **AllNodes** kolekcji po jest filtrowana za pomocą **. WHERE()** lub **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="87a06-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="87a06-140">**ConfigurationData** odwołuje się do tabeli całego wyznaczania wartości skrótu, która jest przekazywana jako parametr podczas kompilowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87a06-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="87a06-141">Przy użyciu danych z systemem innym niż węzeł</span><span class="sxs-lookup"><span data-stu-id="87a06-141">Using non-node data</span></span>

<span data-ttu-id="87a06-142">Jak przedstawiono w poprzednich przykładach, możemy **ConfigurationData** hashtable może mieć co najmniej jeden klucz oprócz wymaganych **AllNodes** klucza.</span><span class="sxs-lookup"><span data-stu-id="87a06-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="87a06-143">W przykładach w niniejszym temacie, firma Microsoft ma używany tylko jeden dodatkowy węzeł o nazwie go `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="87a06-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span> <span data-ttu-id="87a06-144">Można jednak określić dowolną liczbę dodatkowych kluczy i nazwy dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="87a06-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="87a06-145">Na przykład przy użyciu danych z systemem innym niż węzeł, zobacz [oddzielanie danych konfiguracji i środowiska](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="87a06-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87a06-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87a06-146">See Also</span></span>
- [<span data-ttu-id="87a06-147">Opcje poświadczeń w danych konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87a06-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="87a06-148">Konfiguracji DSC</span><span class="sxs-lookup"><span data-stu-id="87a06-148">DSC Configurations</span></span>](configurations.md)

