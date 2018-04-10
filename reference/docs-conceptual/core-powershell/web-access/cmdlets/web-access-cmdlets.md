---
description: ''
ms.topic: article
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: polecenia cmdlet dostępu do sieci Web
ms.technology: powershell
ms.openlocfilehash: 6930fd6a08de69078576fb0d0fbabb04e05d0814
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="9bf3e-103">Polecenia cmdlet programu Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="9bf3e-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="9bf3e-104">Ten zawiera opisy polecenia cmdlet i składnia dla wszystkich poleceń cmdlet specyficznych dostępu do sieci Web programu Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="9bf3e-105">Wyświetla listę poleceń cmdlet w kolejności alfabetycznej na podstawie zleceń na początku polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="9bf3e-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9bf3e-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="9bf3e-107">Dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="9bf3e-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9bf3e-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="9bf3e-109">Zwraca zestaw reguł autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="9bf3e-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9bf3e-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="9bf3e-111">Konfiguruje aplikację sieci web programu Windows PowerShell Web Access w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="9bf3e-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9bf3e-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="9bf3e-113">Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="9bf3e-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9bf3e-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="9bf3e-115">Sprawdza reguły autoryzacji, aby sprawdzić, czy określonego użytkownika, komputer, żądania dostępu do punktu końcowego jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="9bf3e-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9bf3e-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="9bf3e-117">Odinstalowuje aplikację sieci web programu Windows PowerShell za pomocą programu IIS.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="9bf3e-118">**Uwaga**:</span><span class="sxs-lookup"><span data-stu-id="9bf3e-118">**Note**:</span></span>
>
><span data-ttu-id="9bf3e-119">Aby wyświetlić listę wszystkich poleceń cmdlet, które są dostępne, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="9bf3e-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="9bf3e-120">`Get-Command –Module PowerShellWebAccess` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="9bf3e-121">Aby uzyskać więcej informacji na temat lub składni dowolnych poleceń cmdlet, należy użyć: `Get-Help ` *&lt;nazwa polecenia cmdlet&gt;* gdzie *&lt;nazwa polecenia cmdlet&gt;* to nazwa polecenia cmdlet, który chcesz wyszukać.</span><span class="sxs-lookup"><span data-stu-id="9bf3e-121">For more information about, or for the syntax of, any of the cmdlets, use: `Get-Help `*&lt;cmdlet name&gt;* where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="9bf3e-122">Aby uzyskać szczegółowe informacje, możesz uruchomić dowolne z następujących poleceń cmdlet:</span><span class="sxs-lookup"><span data-stu-id="9bf3e-122">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="9bf3e-123">`Get-Help `*&lt;Nazwa polecenia cmdlet&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="9bf3e-123">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="9bf3e-124">`Get-Help `*&lt;Nazwa polecenia cmdlet&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="9bf3e-124">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="9bf3e-125">`Get-Help `*&lt;Nazwa polecenia cmdlet&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="9bf3e-125">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="9bf3e-126">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="9bf3e-126">More Information</span></span>

<span data-ttu-id="9bf3e-127">Aby uzyskać więcej informacji na temat środowiska PowerShell Web Access zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="9bf3e-127">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="9bf3e-128">Zainstalować i używać programu Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="9bf3e-128">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)