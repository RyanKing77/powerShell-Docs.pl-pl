---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 35f732698fcc58f7bd43945edd10c143ffb79af9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ca7ae-103">Klasa MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ca7ae-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ca7ae-104">Lokalnego Configuration Manager (LCM) określa stany pliki konfiguracji, który korzysta z konfiguracji agenta w celu zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="ca7ae-105">Następująca składnia jest uproszczone z kodu Managed Object Format (MOF) i zawiera wszystkie właściwości dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca7ae-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca7ae-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="ca7ae-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ca7ae-107">Members</span></span>
-------

<span data-ttu-id="ca7ae-108">**MSFT_DSCLocalConfigurationManager** klasa ma następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="ca7ae-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="ca7ae-109">[Metody] []</span><span class="sxs-lookup"><span data-stu-id="ca7ae-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="ca7ae-110">Metody</span><span class="sxs-lookup"><span data-stu-id="ca7ae-110">Methods</span></span>

<span data-ttu-id="ca7ae-111">**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="ca7ae-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca7ae-112">Method</span></span> |<span data-ttu-id="ca7ae-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ca7ae-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="ca7ae-114">Metoda ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="ca7ae-115">Używa agenta konfiguracji umożliwiają zastosowanie konfiguracji, który jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="ca7ae-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="ca7ae-117">Wyłącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="ca7ae-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="ca7ae-119">Włącza debugowanie zasobów usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="ca7ae-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="ca7ae-121">Wysyła dokument konfiguracji do węzła zarządzanego i używa **uzyskać** metody Agent konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="ca7ae-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="ca7ae-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="ca7ae-123">Pobiera dane wyjściowe Agent konfiguracji odnoszące się do określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="ca7ae-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="ca7ae-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="ca7ae-125">Podgląd historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="ca7ae-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="ca7ae-127">Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="ca7ae-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="ca7ae-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="ca7ae-129">Uruchamia kontrolę spójności.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="ca7ae-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="ca7ae-131">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="ca7ae-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="ca7ae-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="ca7ae-133">Bezpośrednio wywołuje **uzyskać** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="ca7ae-134">Elementu ResourceSet</span><span class="sxs-lookup"><span data-stu-id="ca7ae-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="ca7ae-135">Bezpośrednio wywołuje **ustawić** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="ca7ae-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="ca7ae-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="ca7ae-137">Bezpośrednio wywołuje **testu** metody zasobu usługi Konfiguracja DSC.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="ca7ae-138">Wycofywanie</span><span class="sxs-lookup"><span data-stu-id="ca7ae-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="ca7ae-139">Przedstawia powrót do poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="ca7ae-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="ca7ae-141">Wysyła dokument konfiguracji do węzła zarządzanego i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="ca7ae-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="ca7ae-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="ca7ae-143">Wysyła dokument konfiguracji do węzła zarządzanego i używa konfiguracji agenta, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="ca7ae-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="ca7ae-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="ca7ae-145">Wysłany do węzła zarządzanego konfiguracji i uruchomić przy użyciu agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="ca7ae-146">Użyj GetConfigurationResultOutput, aby pobrać dane wyjściowe wynik.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="ca7ae-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="ca7ae-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="ca7ae-148">Konfiguruje ustawienia LCM, które są używane do sterowania agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="ca7ae-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="ca7ae-150">Zatrzymuje konfigurację, która jest w toku.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="ca7ae-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="ca7ae-152">Wysyła dokument konfiguracji do węzła zarządzanego i sprawdza bieżącą konfigurację względem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ca7ae-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="ca7ae-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca7ae-153">Requirements</span></span>
------------
><span data-ttu-id="ca7ae-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ca7ae-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ca7ae-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ca7ae-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



