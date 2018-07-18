---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób rejestru DSC
ms.openlocfilehash: b77710d7a6fc599949e78c17af309ad88a1a0872
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093589"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="4ddc6-103">Zasób rejestru DSC</span><span class="sxs-lookup"><span data-stu-id="4ddc6-103">DSC Registry Resource</span></span>

> <span data-ttu-id="4ddc6-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4ddc6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4ddc6-105">**Rejestru** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania kluczy rejestru i wartości w węźle docelowym.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ddc6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ddc6-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="4ddc6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4ddc6-107">Properties</span></span>

|  <span data-ttu-id="4ddc6-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4ddc6-108">Property</span></span>  |  <span data-ttu-id="4ddc6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4ddc6-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="4ddc6-110">Klawisz</span><span class="sxs-lookup"><span data-stu-id="4ddc6-110">Key</span></span>| <span data-ttu-id="4ddc6-111">Wskazuje ścieżkę klucza rejestru, dla którego chcesz zapewnić określonego stanu.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="4ddc6-112">Ta ścieżka musi zawierać gałęzi.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-112">This path must include the hive.</span></span>|
| <span data-ttu-id="4ddc6-113">valueName</span><span class="sxs-lookup"><span data-stu-id="4ddc6-113">ValueName</span></span>| <span data-ttu-id="4ddc6-114">Wskazuje nazwę wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="4ddc6-115">Aby dodać lub usunąć klucz rejestru, należy określić tę właściwość jako ciąg pusty, bez wcześniejszego określania ValueType lub Dane_wartości.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="4ddc6-116">Aby zmodyfikować lub usunąć domyślną wartością klucza rejestru, należy określić tę właściwość jako ciąg pusty podczas również określenie ValueType lub Dane_wartości.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="4ddc6-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="4ddc6-117">Ensure</span></span>| <span data-ttu-id="4ddc6-118">Wskazuje, czy istnieją kluczy i wartości.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="4ddc6-119">Aby upewnić się, że tak, należy ustawić tę właściwość na "Obecny".</span><span class="sxs-lookup"><span data-stu-id="4ddc6-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="4ddc6-120">Aby upewnić się, że nie istnieją, należy ustawić właściwość na "Brak".</span><span class="sxs-lookup"><span data-stu-id="4ddc6-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="4ddc6-121">Wartość domyślna to "Istnieje".</span><span class="sxs-lookup"><span data-stu-id="4ddc6-121">The default value is "Present".</span></span>|
| <span data-ttu-id="4ddc6-122">Force</span><span class="sxs-lookup"><span data-stu-id="4ddc6-122">Force</span></span>| <span data-ttu-id="4ddc6-123">Jeśli określony klucz rejestru jest obecny, **życie** zastępowane nową wartością.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="4ddc6-124">Jeśli usuwanie klucza rejestru za pomocą podkluczy, musi to być **$true**</span><span class="sxs-lookup"><span data-stu-id="4ddc6-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="4ddc6-125">Hex</span><span class="sxs-lookup"><span data-stu-id="4ddc6-125">Hex</span></span>| <span data-ttu-id="4ddc6-126">Wskazuje, jeśli dane są wyrażane w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="4ddc6-127">Jeśli zostanie określony, dane wartość DWORD/QWORD są prezentowane w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="4ddc6-128">Nie jest prawidłowy dla innych typów.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-128">Not valid for other types.</span></span> <span data-ttu-id="4ddc6-129">Wartość domyślna to **$false**.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="4ddc6-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4ddc6-130">DependsOn</span></span>| <span data-ttu-id="4ddc6-131">Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4ddc6-132">Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="4ddc6-133">Dane_wartości</span><span class="sxs-lookup"><span data-stu-id="4ddc6-133">ValueData</span></span>| <span data-ttu-id="4ddc6-134">Dane wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-134">The data for the registry value.</span></span>|
| <span data-ttu-id="4ddc6-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="4ddc6-135">ValueType</span></span>| <span data-ttu-id="4ddc6-136">Wskazuje typ wartości.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-136">Indicates the type of the value.</span></span> <span data-ttu-id="4ddc6-137">Obsługiwane typy to: ciągu (REG_SZ), plik binarny (dane BINARNE REG), Dword 32-bitowych (REG_DWORD), Qword 64-bitowych (REG_QWORD), ciągu wielokrotnego (REG_MULTI_SZ), ciągu rozwijalnego (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="4ddc6-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="4ddc6-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ddc6-138">Example</span></span>

<span data-ttu-id="4ddc6-139">W tym przykładzie gwarantuje, że klucz o nazwie "ExampleKey" jest obecny w **HKEY\_lokalnego\_maszyny** hive.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="4ddc6-140">Zmiany ustawień rejestru **HKEY\_bieżącego\_użytkownika** gałęzi wymaga, że konfiguracja jest uruchamiany przy użyciu poświadczeń użytkownika, a nie jako system.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-140">Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="4ddc6-141">Możesz użyć **PsDscRunAsCredential** właściwości w celu określenia poświadczeń użytkownika do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4ddc6-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="4ddc6-142">Aby uzyskać przykład, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="4ddc6-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>