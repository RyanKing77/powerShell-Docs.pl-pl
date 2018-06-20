---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 615f2998b11a0a927d3868d852e0d408f500c86d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188839"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b1bdc-103">Klasa MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b1bdc-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b1bdc-104">Lokalnego Configuration Manager (LCM) określa stany pliki konfiguracji, który korzysta z konfiguracji agenta w celu zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="b1bdc-105">Następująca składnia jest uproszczone z kodu Managed Object Format (MOF) i zawiera wszystkie właściwości dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1bdc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1bdc-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="b1bdc-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b1bdc-107">Members</span></span>
-------

<span data-ttu-id="b1bdc-108">**MSFT_DSCLocalConfigurationManager** klasa ma następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b1bdc-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="b1bdc-109">[Metody] []</span><span class="sxs-lookup"><span data-stu-id="b1bdc-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="b1bdc-110">Metody</span><span class="sxs-lookup"><span data-stu-id="b1bdc-110">Methods</span></span>

<span data-ttu-id="b1bdc-111">**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="b1bdc-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1bdc-112">Method</span></span> |<span data-ttu-id="b1bdc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b1bdc-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="b1bdc-114">Metoda ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="b1bdc-115">Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="b1bdc-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="b1bdc-117">Wyłącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="b1bdc-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="b1bdc-119">Włącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="b1bdc-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="b1bdc-121">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="b1bdc-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="b1bdc-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="b1bdc-123">Pobiera dane wyjściowe Agent konfiguracji odnoszące się do określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="b1bdc-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b1bdc-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="b1bdc-125">Podgląd historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="b1bdc-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="b1bdc-127">Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="b1bdc-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b1bdc-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="b1bdc-129">Uruchamia kontrolę spójności.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="b1bdc-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="b1bdc-131">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="b1bdc-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="b1bdc-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="b1bdc-133">Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="b1bdc-134">elementu resourceSet</span><span class="sxs-lookup"><span data-stu-id="b1bdc-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="b1bdc-135">Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="b1bdc-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="b1bdc-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="b1bdc-137">Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="b1bdc-138">Wycofywanie</span><span class="sxs-lookup"><span data-stu-id="b1bdc-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="b1bdc-139">Przedstawia powrót do poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="b1bdc-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="b1bdc-141">Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="b1bdc-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="b1bdc-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="b1bdc-143">Wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="b1bdc-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="b1bdc-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="b1bdc-145">Wysłany do węzła zarządzanego konfiguracji i uruchomić przy użyciu agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="b1bdc-146">Użyj GetConfigurationResultOutput, aby pobrać dane wyjściowe wynik.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="b1bdc-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="b1bdc-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="b1bdc-148">Konfiguruje ustawienia LCM, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="b1bdc-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="b1bdc-150">Zatrzymuje konfigurację, która jest w toku.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="b1bdc-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="b1bdc-152">Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b1bdc-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|





## <a name="requirements"></a><span data-ttu-id="b1bdc-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1bdc-153">Requirements</span></span>
------------
><span data-ttu-id="b1bdc-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b1bdc-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b1bdc-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1bdc-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>