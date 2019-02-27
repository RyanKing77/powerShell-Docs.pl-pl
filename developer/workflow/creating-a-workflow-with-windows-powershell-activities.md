---
title: Tworzenie przepływu pracy za pomocą programu Windows PowerShell działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845038"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="31c5e-102">Tworzenie przepływu pracy przy użyciu działań programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="31c5e-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="31c5e-103">Możesz utworzyć przepływ pracy programu Windows PowerShell, zaznaczając działań do przybornika Visual Studio i przeciągając je w oknie projektanta przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="31c5e-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="31c5e-104">Aby uzyskać informacji na temat dodawania działania programu Windows PowerShell do przybornika Visual Studio, zobacz [Dodawanie Windows PowerShell działań do przybornika Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="31c5e-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="31c5e-105">W poniższych procedurach opisano sposób tworzenia przepływu pracy, który umożliwia sprawdzenie stanu domeny grupy komputerów określonych przez użytkownika, jeśli nie są już połączone, a następnie umożliwia sprawdzenie stanu dołączania ich do domeny.</span><span class="sxs-lookup"><span data-stu-id="31c5e-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="31c5e-106">Konfigurowanie projektu</span><span class="sxs-lookup"><span data-stu-id="31c5e-106">Setting up the Project</span></span>

1. <span data-ttu-id="31c5e-107">Postępuj zgodnie z procedurą w [Dodawanie Windows PowerShell działań do przybornika Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) do tworzenia projektu przepływu pracy i dodawanie działań z [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) i [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) zestawów do przybornika.</span><span class="sxs-lookup"><span data-stu-id="31c5e-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="31c5e-108">Dodaj System.Management.Automation Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities i Microsoft.PowerShell.Commands.Management tego projektu jako zestawy odwołań.</span><span class="sxs-lookup"><span data-stu-id="31c5e-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="31c5e-109">Dodawanie działań do przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="31c5e-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="31c5e-110">Dodaj **sekwencji** działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="31c5e-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="31c5e-111">Utwórz argument o nazwie `ComputerName` z typem argumentu `String[]`.</span><span class="sxs-lookup"><span data-stu-id="31c5e-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="31c5e-112">Ten argument reprezentuje nazwy komputerów, aby sprawdzić i Dołącz.</span><span class="sxs-lookup"><span data-stu-id="31c5e-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="31c5e-113">Utwórz argument o nazwie `DomainCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="31c5e-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="31c5e-114">Ten argument reprezentuje poświadczenia domeny konta domeny, który jest autoryzowany do przyłączenia komputera do domeny.</span><span class="sxs-lookup"><span data-stu-id="31c5e-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="31c5e-115">Utwórz argument o nazwie `MachineCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="31c5e-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="31c5e-116">Ten argument reprezentuje poświadczenia administratora na komputerach w celu sprawdzenia i Dołącz do.</span><span class="sxs-lookup"><span data-stu-id="31c5e-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="31c5e-117">Dodaj **ParallelForEach** działania wewnątrz **sekwencji** działania.</span><span class="sxs-lookup"><span data-stu-id="31c5e-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="31c5e-118">Wprowadź `comp` i `ComputerName` w tekst pola tak, aby pętla wykonuje iterację przez elementy `ComputerName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="31c5e-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="31c5e-119">Dodaj **sekwencji** działania do treści **ParallelForEach** działania.</span><span class="sxs-lookup"><span data-stu-id="31c5e-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="31c5e-120">Ustaw **DisplayName** właściwości Sekwencja `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="31c5e-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="31c5e-121">Dodaj **GetWmiObject** działanie **JoinDomain** sekwencji.</span><span class="sxs-lookup"><span data-stu-id="31c5e-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="31c5e-122">Edytowanie właściwości **GetWmiObject** działania w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="31c5e-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="31c5e-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31c5e-123">Property</span></span>|<span data-ttu-id="31c5e-124">Wartość</span><span class="sxs-lookup"><span data-stu-id="31c5e-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="31c5e-125">**Class**</span><span class="sxs-lookup"><span data-stu-id="31c5e-125">**Class**</span></span>|<span data-ttu-id="31c5e-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="31c5e-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="31c5e-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="31c5e-127">**PSComputerName**</span></span>|<span data-ttu-id="31c5e-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="31c5e-128">{comp}</span></span>|
   |<span data-ttu-id="31c5e-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="31c5e-129">**PSCredential**</span></span>|<span data-ttu-id="31c5e-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="31c5e-130">MachineCred</span></span>|

9. <span data-ttu-id="31c5e-131">Dodaj **AddComputer** działanie **JoinDomain** sekwencji po **GetWmiObject** działania.</span><span class="sxs-lookup"><span data-stu-id="31c5e-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="31c5e-132">Edytowanie właściwości **AddComputer** działania w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="31c5e-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="31c5e-133">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31c5e-133">Property</span></span>|<span data-ttu-id="31c5e-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="31c5e-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="31c5e-135">**NazwaKomputera**</span><span class="sxs-lookup"><span data-stu-id="31c5e-135">**ComputerName**</span></span>|<span data-ttu-id="31c5e-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="31c5e-136">{comp}</span></span>|
    |<span data-ttu-id="31c5e-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="31c5e-137">**DomainCredential**</span></span>|<span data-ttu-id="31c5e-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="31c5e-138">DomainCred</span></span>|

11. <span data-ttu-id="31c5e-139">Dodaj **RestartComputer** działanie **JoinDomain** sekwencji po **AddComputer** działania.</span><span class="sxs-lookup"><span data-stu-id="31c5e-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="31c5e-140">Edytowanie właściwości **RestartComputer** działania w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="31c5e-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="31c5e-141">Właściwość</span><span class="sxs-lookup"><span data-stu-id="31c5e-141">Property</span></span>|<span data-ttu-id="31c5e-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="31c5e-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="31c5e-143">**NazwaKomputera**</span><span class="sxs-lookup"><span data-stu-id="31c5e-143">**ComputerName**</span></span>|<span data-ttu-id="31c5e-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="31c5e-144">{comp}</span></span>|
    |<span data-ttu-id="31c5e-145">**Poświadczenie**</span><span class="sxs-lookup"><span data-stu-id="31c5e-145">**Credential**</span></span>|<span data-ttu-id="31c5e-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="31c5e-146">MachineCred</span></span>|
    |<span data-ttu-id="31c5e-147">**Aby uzyskać**</span><span class="sxs-lookup"><span data-stu-id="31c5e-147">**For**</span></span>|<span data-ttu-id="31c5e-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="31c5e-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="31c5e-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="31c5e-149">**Force**</span></span>|<span data-ttu-id="31c5e-150">True</span><span class="sxs-lookup"><span data-stu-id="31c5e-150">True</span></span>|
    |<span data-ttu-id="31c5e-151">Czekaj</span><span class="sxs-lookup"><span data-stu-id="31c5e-151">Wait</span></span>|<span data-ttu-id="31c5e-152">True</span><span class="sxs-lookup"><span data-stu-id="31c5e-152">True</span></span>|
    |<span data-ttu-id="31c5e-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="31c5e-153">PSComputerName</span></span>|<span data-ttu-id="31c5e-154">{""}</span><span class="sxs-lookup"><span data-stu-id="31c5e-154">{""}</span></span>|

13. <span data-ttu-id="31c5e-155">Dodaj **GetWmiObject** działanie **JoinDomain** sekwencji po **RestartComputer** działania.</span><span class="sxs-lookup"><span data-stu-id="31c5e-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="31c5e-156">Edycja jej właściwości na taki sam jak poprzedni **GetWmiObject** działania.</span><span class="sxs-lookup"><span data-stu-id="31c5e-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="31c5e-157">Po zakończeniu procedury okna projektu przepływu pracy powinien wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="31c5e-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="31c5e-158">![JoinDomain XAML w Projektancie przepływu pracy](../media/joindomainworkflow.png)
    ![JoinDomain XAML w Projektancie przepływu pracy](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="31c5e-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>