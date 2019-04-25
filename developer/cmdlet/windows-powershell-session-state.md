---
title: Stan sesji programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066978"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="adc24-102">Stan sesji program Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="adc24-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="adc24-103">Stan sesji odnosi się do bieżącej konfiguracji sesji środowiska Windows PowerShell lub modułu.</span><span class="sxs-lookup"><span data-stu-id="adc24-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="adc24-104">Sesję środowiska Windows PowerShell jest środowisko operacyjne, w którym używać hasła interaktywnie według wiersza polecenia użytkownika lub programowo aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="adc24-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="adc24-105">Stan sesji jest nazywana globalnego stanu sesji.</span><span class="sxs-lookup"><span data-stu-id="adc24-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="adc24-106">Z punktu widzenia projektanta sesję środowiska Windows PowerShell odnosi się do czasu między po otwarciu obszaru działania programu Windows PowerShell w aplikacji hosta, a kiedy zostanie zamknięty obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="adc24-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="adc24-107">Przyjrzano się w inny sposób, sesja jest okres istnienia wystąpienia aparatu programu Windows PowerShell, które jest wywoływane, gdy istnieje w obszarze działania.</span><span class="sxs-lookup"><span data-stu-id="adc24-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="adc24-108">Stan sesji modułu</span><span class="sxs-lookup"><span data-stu-id="adc24-108">Module Session State</span></span>

<span data-ttu-id="adc24-109">Stany sesji modułu są tworzone w każdym przypadku, gdy moduł lub jednej z jego zagnieżdżonych moduły są importowane do sesji.</span><span class="sxs-lookup"><span data-stu-id="adc24-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="adc24-110">Gdy moduł eksportuje element, na przykład polecenia cmdlet, funkcji lub skryptu, odwołania do tego elementu jest dodawany do stanu sesji globalnej sesji.</span><span class="sxs-lookup"><span data-stu-id="adc24-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="adc24-111">Jednak gdy element zostanie uruchomiony, jest ono wykonywane w ramach stanu sesji modułu.</span><span class="sxs-lookup"><span data-stu-id="adc24-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="adc24-112">Dane stanu sesji</span><span class="sxs-lookup"><span data-stu-id="adc24-112">Session-State Data</span></span>

<span data-ttu-id="adc24-113">Dane stanu sesji może być publicznym lub prywatnym.</span><span class="sxs-lookup"><span data-stu-id="adc24-113">Session state data can be public or private.</span></span> <span data-ttu-id="adc24-114">Publiczne dane są dostępne dla wywołań spoza stanu sesji, gdy prywatne dane są dostępne tylko do wywołań z w ramach stanu sesji.</span><span class="sxs-lookup"><span data-stu-id="adc24-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="adc24-115">Na przykład moduł może mieć prywatnych funkcja, która może być wywoływana tylko przez moduł lub tylko wewnętrznie przez element publiczny, który został wyeksportowany.</span><span class="sxs-lookup"><span data-stu-id="adc24-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="adc24-116">Jest to podobne do prywatnych i publicznych elementów członkowskich typu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adc24-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="adc24-117">Dane stanu sesji jest przechowywany przez bieżące wystąpienie aparatu wykonywania w kontekście bieżącej sesji programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adc24-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="adc24-118">Dane stanu sesji obejmuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="adc24-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="adc24-119">Informacje o ścieżce</span><span class="sxs-lookup"><span data-stu-id="adc24-119">Path information</span></span>

- <span data-ttu-id="adc24-120">Informacje o dysku</span><span class="sxs-lookup"><span data-stu-id="adc24-120">Drive information</span></span>

- <span data-ttu-id="adc24-121">Informacje o dostawcy programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="adc24-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="adc24-122">Informacje o zaimportowanych modułów i odwołania do elementów modułu (takich jak polecenia cmdlet, funkcji i skryptów), które są eksportowane przez moduł.</span><span class="sxs-lookup"><span data-stu-id="adc24-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="adc24-123">Te informacje i te odwołania są przeznaczone tylko stan globalny sesji.</span><span class="sxs-lookup"><span data-stu-id="adc24-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="adc24-124">Informacje o zmiennej stanu sesji</span><span class="sxs-lookup"><span data-stu-id="adc24-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="adc24-125">Uzyskiwanie dostępu do danych stanu sesji w ramach polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="adc24-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="adc24-126">Polecenia cmdlet mają dostęp do danych stanu sesji w wartość pośredni przez [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) właściwości klasy polecenia cmdlet lub bezpośrednio za pomocą [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasy.</span><span class="sxs-lookup"><span data-stu-id="adc24-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="adc24-127">[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasy zawiera właściwości, które mogą służyć do badania różnego rodzaju dane stanu sesji.</span><span class="sxs-lookup"><span data-stu-id="adc24-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="adc24-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adc24-128">See Also</span></span>

[<span data-ttu-id="adc24-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="adc24-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="adc24-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="adc24-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="adc24-131">Polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="adc24-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="adc24-132">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="adc24-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="adc24-133">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="adc24-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
