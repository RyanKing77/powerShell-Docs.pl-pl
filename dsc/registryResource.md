---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób rejestru DSC
ms.openlocfilehash: fcd24b1dd729dbb0abd697a4a628dce01fdd5422
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="c1f25-103">Zasób rejestru DSC</span><span class="sxs-lookup"><span data-stu-id="c1f25-103">DSC Registry Resource</span></span>

> <span data-ttu-id="c1f25-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c1f25-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c1f25-105">**Rejestru** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania kluczy rejestru i wartości w docelowym węźle.</span><span class="sxs-lookup"><span data-stu-id="c1f25-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1f25-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1f25-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="c1f25-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c1f25-107">Properties</span></span>
|  <span data-ttu-id="c1f25-108">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c1f25-108">Property</span></span>  |  <span data-ttu-id="c1f25-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c1f25-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="c1f25-110">Klawisz</span><span class="sxs-lookup"><span data-stu-id="c1f25-110">Key</span></span>| <span data-ttu-id="c1f25-111">Określa ścieżkę klucza rejestru, dla którego chcesz zapewnić z określonym stanem.</span><span class="sxs-lookup"><span data-stu-id="c1f25-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="c1f25-112">Ta ścieżka musi zawierać gałęzi.</span><span class="sxs-lookup"><span data-stu-id="c1f25-112">This path must include the hive.</span></span>|
| <span data-ttu-id="c1f25-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="c1f25-113">ValueName</span></span>| <span data-ttu-id="c1f25-114">Wskazuje nazwę wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="c1f25-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="c1f25-115">Aby dodać lub usunąć klucz rejestru, bez określenia ValueType lub Dane_wartości należy określić tę właściwość jako ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="c1f25-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="c1f25-116">Aby zmodyfikować lub usunąć domyślną wartością klucza rejestru, należy określić tę właściwość jako ciąg pusty, jeśli określono również ValueType lub Dane_wartości.</span><span class="sxs-lookup"><span data-stu-id="c1f25-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="c1f25-117">Upewnij się</span><span class="sxs-lookup"><span data-stu-id="c1f25-117">Ensure</span></span>| <span data-ttu-id="c1f25-118">Wskazuje, czy istnieje klucz i wartość.</span><span class="sxs-lookup"><span data-stu-id="c1f25-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="c1f25-119">Aby upewnić się, że ich ustaw wartość "Brak".</span><span class="sxs-lookup"><span data-stu-id="c1f25-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="c1f25-120">Aby upewnić się, że nie istnieją, ustaw właściwość na "Brak".</span><span class="sxs-lookup"><span data-stu-id="c1f25-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="c1f25-121">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="c1f25-121">The default value is "Present".</span></span>|
| <span data-ttu-id="c1f25-122">Force</span><span class="sxs-lookup"><span data-stu-id="c1f25-122">Force</span></span>| <span data-ttu-id="c1f25-123">Jeśli określony klucz rejestru jest obecny, __życie__ zastępuje go przy użyciu nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="c1f25-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="c1f25-124">Jeśli usuwanie klucza rejestru za pomocą podkluczy, musi to być __$true__</span><span class="sxs-lookup"><span data-stu-id="c1f25-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="c1f25-125">Hex</span><span class="sxs-lookup"><span data-stu-id="c1f25-125">Hex</span></span>| <span data-ttu-id="c1f25-126">Wskazuje, czy dane są wyrażane w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="c1f25-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="c1f25-127">Jeśli jest określony, dane wartości DWORD/QWORD jest podana w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="c1f25-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="c1f25-128">Nie jest prawidłowy dla innych typów.</span><span class="sxs-lookup"><span data-stu-id="c1f25-128">Not valid for other types.</span></span> <span data-ttu-id="c1f25-129">Wartość domyślna to __$false__.</span><span class="sxs-lookup"><span data-stu-id="c1f25-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="c1f25-130">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c1f25-130">DependsOn</span></span>| <span data-ttu-id="c1f25-131">Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="c1f25-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c1f25-132">Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c1f25-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c1f25-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="c1f25-133">ValueData</span></span>| <span data-ttu-id="c1f25-134">Dane wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="c1f25-134">The data for the registry value.</span></span>|
| <span data-ttu-id="c1f25-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="c1f25-135">ValueType</span></span>| <span data-ttu-id="c1f25-136">Wskazuje typ wartości.</span><span class="sxs-lookup"><span data-stu-id="c1f25-136">Indicates the type of the value.</span></span> <span data-ttu-id="c1f25-137">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="c1f25-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="c1f25-138">String (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="c1f25-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="c1f25-139">Dane binarne (REG BINARY)</span><span class="sxs-lookup"><span data-stu-id="c1f25-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="c1f25-140">DWORD 32-bitowych (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="c1f25-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="c1f25-141">Qword 64-bitowych (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="c1f25-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="c1f25-142">Multi-string (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="c1f25-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="c1f25-143">Ciąg rozwijania (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="c1f25-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="c1f25-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1f25-144">Example</span></span>
<span data-ttu-id="c1f25-145">W tym przykładzie zapewnia, że klucz o nazwie "ExampleKey" są obecne w **HKEY\_lokalnego\_maszyny** hive.</span><span class="sxs-lookup"><span data-stu-id="c1f25-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
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

><span data-ttu-id="c1f25-146">**Uwaga:** zmiany ustawień rejestru **HKEY\_bieżącego\_użytkownika** gałęzi wymaga, czy konfiguracja jest uruchomiony przy użyciu poświadczeń użytkownika, a nie jako system.</span><span class="sxs-lookup"><span data-stu-id="c1f25-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="c1f25-147">Można użyć **PsDscRunAsCredential** właściwość, aby określić poświadczenia użytkownika w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c1f25-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="c1f25-148">Na przykład zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="c1f25-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>