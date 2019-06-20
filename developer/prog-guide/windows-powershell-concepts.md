---
title: Pojęcia dotyczące programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263846"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="d6f59-102">Zagadnienia dotyczące programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6f59-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="d6f59-103">Ta sekcja zawiera ogólne informacje, które pomoże Ci zrozumieć programu PowerShell z punktu widzenia dewelopera.</span><span class="sxs-lookup"><span data-stu-id="d6f59-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="d6f59-104">Nazwa tematu</span><span class="sxs-lookup"><span data-stu-id="d6f59-104">Topic Name</span></span>|<span data-ttu-id="d6f59-105">Opis</span><span class="sxs-lookup"><span data-stu-id="d6f59-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="d6f59-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="d6f59-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="d6f59-107">Opis obiektów programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6f59-107">Description of PowerShell objects.</span></span> <span data-ttu-id="d6f59-108">Aby uzyskać więcej informacji, zobacz [o tworzenie obiektów](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="d6f59-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="d6f59-109">Tworzenie obszary działania</span><span class="sxs-lookup"><span data-stu-id="d6f59-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="d6f59-110">Środowisk operacyjnych, w której polecenia są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="d6f59-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="d6f59-111">Aby uzyskać więcej informacji, zobacz [klasy obszarem działania](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="d6f59-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="d6f59-112">Rozszerzanie obiektów danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="d6f59-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="d6f59-113">Jak rozszerzyć obiektów programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6f59-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="d6f59-114">Aby uzyskać więcej informacji, zobacz [Types.ps1xml — informacje](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="d6f59-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="d6f59-115">Rejestrowanie poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6f59-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="d6f59-116">Jak udostępnić modułów i przystawek w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6f59-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="d6f59-117">Aby uzyskać więcej informacji, zobacz [modułów i przystawek](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="d6f59-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="d6f59-118">Żądania potwierdzenia z polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6f59-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="d6f59-119">Jak polecenia cmdlet i dostawców poprosić o informacje zwrotne użytkownika przed wykonaniem akcji.</span><span class="sxs-lookup"><span data-stu-id="d6f59-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="d6f59-120">Klasa RuntimeDefinedParameter</span><span class="sxs-lookup"><span data-stu-id="d6f59-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="d6f59-121">Deklaracji parametrów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d6f59-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="d6f59-122">Namespace System.Management.Automation</span><span class="sxs-lookup"><span data-stu-id="d6f59-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="d6f59-123">Przegląd przestrzeni nazw interfejsu API programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6f59-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="d6f59-124">Przegląd dostawcy programu PowerShell Windows</span><span class="sxs-lookup"><span data-stu-id="d6f59-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="d6f59-125">Przegląd informacji o dostawcy programu PowerShell, które są używane do dostępu do danych są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="d6f59-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="d6f59-126">Zapisywanie Pomoc dla poleceń cmdlet programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6f59-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="d6f59-127">Jak napisać polecenia cmdlet programu PowerShell pomocy.</span><span class="sxs-lookup"><span data-stu-id="d6f59-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d6f59-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6f59-128">See also</span></span>

[<span data-ttu-id="d6f59-129">Klasa programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6f59-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="d6f59-130">Dokumentacja interfejsu API programu PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d6f59-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="d6f59-131">Windows PowerShell przewodnik</span><span class="sxs-lookup"><span data-stu-id="d6f59-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d6f59-132">Pisanie tematów Pomocy dotyczących modułów programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6f59-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="d6f59-133">Pisanie dostawcy programu Powershell Windows</span><span class="sxs-lookup"><span data-stu-id="d6f59-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="d6f59-134">Dokumentacja interfejsu API programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6f59-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="d6f59-135">Dokumentacja programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d6f59-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)