---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048481"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d8239-103">Klasa MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d8239-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d8239-104">Lokalne konfiguracji Manager (LCM) określa stany pliki konfiguracji, która korzysta z konfiguracji agenta w celu zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d8239-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="d8239-105">Następująca składnia jest uproszczony w kodzie Managed Object Format (MOF) i obejmuje wszystkie właściwości dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="d8239-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8239-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8239-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="d8239-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d8239-107">Members</span></span>

<span data-ttu-id="d8239-108">**MSFT_DSCLocalConfigurationManager** klasy ma następujące składowe:</span><span class="sxs-lookup"><span data-stu-id="d8239-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="d8239-109">[Metody] []</span><span class="sxs-lookup"><span data-stu-id="d8239-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="d8239-110">Metody</span><span class="sxs-lookup"><span data-stu-id="d8239-110">Methods</span></span>

<span data-ttu-id="d8239-111">**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.</span><span class="sxs-lookup"><span data-stu-id="d8239-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="d8239-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="d8239-112">Method</span></span> |<span data-ttu-id="d8239-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d8239-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="d8239-114">Metoda ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="d8239-115">Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d8239-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="d8239-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="d8239-117">Wyłącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d8239-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="d8239-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="d8239-119">Włącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d8239-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="d8239-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="d8239-121">Wysyła dokument konfiguracji do zarządzanego węzła i używa **uzyskać** metoda przez agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="d8239-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="d8239-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="d8239-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="d8239-123">Pobiera dane wyjściowe agenta konfiguracji odnoszące się do określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="d8239-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="d8239-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d8239-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="d8239-125">Pobieranie historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d8239-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="d8239-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="d8239-127">Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.</span><span class="sxs-lookup"><span data-stu-id="d8239-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="d8239-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="d8239-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="d8239-129">Uruchamia kontrolę spójności.</span><span class="sxs-lookup"><span data-stu-id="d8239-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="d8239-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="d8239-131">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d8239-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="d8239-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="d8239-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="d8239-133">Bezpośrednio wywołuje **uzyskać** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d8239-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="d8239-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="d8239-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="d8239-135">Bezpośrednio wywołuje **ustaw** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d8239-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="d8239-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="d8239-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="d8239-137">Bezpośrednio wywołuje **testu** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="d8239-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="d8239-138">Wycofywanie</span><span class="sxs-lookup"><span data-stu-id="d8239-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="d8239-139">Ustala powrót do poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d8239-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="d8239-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="d8239-141">Wysyła dokument konfiguracji w węźle zarządzanym i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="d8239-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="d8239-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="d8239-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="d8239-143">Wysyła dokument konfiguracji do zarządzanego węzła i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="d8239-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="d8239-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="d8239-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="d8239-145">Wysłany do zarządzanych węzłów konfiguracji i rozpocząć korzystanie przez agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="d8239-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="d8239-146">Użyj GetConfigurationResultOutput do pobrania danych wyjściowych wyników.</span><span class="sxs-lookup"><span data-stu-id="d8239-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="d8239-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="d8239-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="d8239-148">Ustawia ustawienia LCM, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d8239-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="d8239-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="d8239-150">Zatrzymuje konfiguracji, który jest w toku.</span><span class="sxs-lookup"><span data-stu-id="d8239-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="d8239-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="d8239-152">Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d8239-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="d8239-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8239-153">Requirements</span></span>

<span data-ttu-id="d8239-154">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d8239-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d8239-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8239-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>