---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2d2ce000988f2c10ab04c4ba5a4650bd3c75ec7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="35910-103">Klasa MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="35910-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="35910-104">Lokalnego Configuration Manager (LCM) określa stany pliki konfiguracji, który korzysta z konfiguracji agenta w celu zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35910-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="35910-105">Następująca składnia jest uproszczone z kodu Managed Object Format (MOF) i zawiera wszystkie właściwości dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="35910-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="35910-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="35910-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="35910-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="35910-107">Members</span></span>
-------

<span data-ttu-id="35910-108">**MSFT_DSCLocalConfigurationManager** klasa ma następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="35910-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="35910-109">[Metody] []</span><span class="sxs-lookup"><span data-stu-id="35910-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="35910-110">Metody</span><span class="sxs-lookup"><span data-stu-id="35910-110">Methods</span></span>

<span data-ttu-id="35910-111">**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.</span><span class="sxs-lookup"><span data-stu-id="35910-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="35910-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="35910-112">Method</span></span> |<span data-ttu-id="35910-113">Opis</span><span class="sxs-lookup"><span data-stu-id="35910-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="35910-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="35910-115">Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="35910-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="35910-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="35910-117">Wyłącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="35910-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="35910-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="35910-119">Włącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="35910-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="35910-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="35910-121">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="35910-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="35910-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="35910-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="35910-123">Pobiera dane wyjściowe Agent konfiguracji odnoszące się do określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="35910-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="35910-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="35910-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="35910-125">Podgląd historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35910-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="35910-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="35910-127">Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.</span><span class="sxs-lookup"><span data-stu-id="35910-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="35910-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="35910-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="35910-129">Uruchamia kontrolę spójności.</span><span class="sxs-lookup"><span data-stu-id="35910-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="35910-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="35910-131">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35910-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="35910-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="35910-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="35910-133">Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="35910-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="35910-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="35910-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="35910-135">Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="35910-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="35910-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="35910-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="35910-137">Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="35910-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="35910-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="35910-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="35910-139">Przedstawia powrót do poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35910-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="35910-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="35910-141">Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="35910-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="35910-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="35910-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="35910-143">Wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="35910-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="35910-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="35910-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="35910-145">Wysłany do węzła zarządzanego konfiguracji i uruchomić przy użyciu agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="35910-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="35910-146">Użyj GetConfigurationResultOutput, aby pobrać dane wyjściowe wynik.</span><span class="sxs-lookup"><span data-stu-id="35910-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="35910-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="35910-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="35910-148">Konfiguruje ustawienia LCM, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35910-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="35910-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="35910-150">Zatrzymuje konfigurację, która jest w toku.</span><span class="sxs-lookup"><span data-stu-id="35910-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="35910-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="35910-152">Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="35910-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="35910-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35910-153">Requirements</span></span>
------------
><span data-ttu-id="35910-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="35910-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="35910-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="35910-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



