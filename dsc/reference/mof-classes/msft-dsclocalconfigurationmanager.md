---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Klasa MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726887"
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="75aa2-103">Klasa MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="75aa2-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="75aa2-104">Lokalne konfiguracji Manager (LCM) określa stany pliki konfiguracji, która korzysta z konfiguracji agenta w celu zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="75aa2-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="75aa2-105">Następująca składnia jest uproszczony w kodzie Managed Object Format (MOF) i obejmuje wszystkie właściwości dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="75aa2-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="75aa2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="75aa2-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="75aa2-107">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="75aa2-107">Members</span></span>

<span data-ttu-id="75aa2-108">**MSFT_DSCLocalConfigurationManager** klasy ma następujące składowe:</span><span class="sxs-lookup"><span data-stu-id="75aa2-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="75aa2-109">[Metody] []</span><span class="sxs-lookup"><span data-stu-id="75aa2-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="75aa2-110">Metody</span><span class="sxs-lookup"><span data-stu-id="75aa2-110">Methods</span></span>

<span data-ttu-id="75aa2-111">**MSFT_DSCLocalConfigurationManager** klasa ma tych metod.</span><span class="sxs-lookup"><span data-stu-id="75aa2-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="75aa2-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="75aa2-112">Method</span></span> |<span data-ttu-id="75aa2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="75aa2-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="75aa2-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="75aa2-115">Używa agenta konfiguracji, aby zastosować konfigurację, która jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="75aa2-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="75aa2-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="75aa2-117">Wyłącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="75aa2-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="75aa2-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="75aa2-119">Włącza debugowanie zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="75aa2-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="75aa2-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="75aa2-121">Wysyła dokument konfiguracji do zarządzanego węzła i używa **uzyskać** metoda przez agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="75aa2-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="75aa2-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="75aa2-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="75aa2-123">Pobiera dane wyjściowe agenta konfiguracji odnoszące się do określonego zadania.</span><span class="sxs-lookup"><span data-stu-id="75aa2-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="75aa2-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="75aa2-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="75aa2-125">Pobieranie historii stanu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="75aa2-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="75aa2-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="75aa2-127">Pobiera ustawienia LCM, które są używane do kontrolowania konfiguracji agenta.</span><span class="sxs-lookup"><span data-stu-id="75aa2-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="75aa2-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="75aa2-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="75aa2-129">Uruchamia kontrolę spójności.</span><span class="sxs-lookup"><span data-stu-id="75aa2-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="75aa2-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="75aa2-131">Usuwa pliki konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="75aa2-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="75aa2-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="75aa2-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="75aa2-133">Bezpośrednio wywołuje **uzyskać** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="75aa2-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="75aa2-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="75aa2-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="75aa2-135">Bezpośrednio wywołuje **ustaw** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="75aa2-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="75aa2-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="75aa2-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="75aa2-137">Bezpośrednio wywołuje **testu** metod zasobów DSC.</span><span class="sxs-lookup"><span data-stu-id="75aa2-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="75aa2-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="75aa2-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="75aa2-139">Ustala powrót do poprzedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="75aa2-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="75aa2-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="75aa2-141">Wysyła dokument konfiguracji w węźle zarządzanym i zapisuje go jako oczekujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="75aa2-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="75aa2-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="75aa2-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="75aa2-143">Wysyła dokument konfiguracji do zarządzanego węzła i używa agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="75aa2-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="75aa2-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="75aa2-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="75aa2-145">Wysłany do zarządzanych węzłów konfiguracji i rozpocząć korzystanie przez agenta konfiguracji, aby zastosować konfigurację.</span><span class="sxs-lookup"><span data-stu-id="75aa2-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="75aa2-146">Użyj GetConfigurationResultOutput do pobrania danych wyjściowych wyników.</span><span class="sxs-lookup"><span data-stu-id="75aa2-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="75aa2-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="75aa2-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="75aa2-148">Ustawia ustawienia LCM, które są używane do kontrolowania przez agenta konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="75aa2-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="75aa2-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="75aa2-150">Zatrzymuje konfiguracji, który jest w toku.</span><span class="sxs-lookup"><span data-stu-id="75aa2-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="75aa2-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="75aa2-152">Wysyła dokument konfiguracji w węźle zarządzanym i sprawdza bieżącą konfigurację dla dokumentu.</span><span class="sxs-lookup"><span data-stu-id="75aa2-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="75aa2-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75aa2-153">Requirements</span></span>

<span data-ttu-id="75aa2-154">**PLIK MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="75aa2-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="75aa2-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="75aa2-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
