---
ms.date: 10/13/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Omówienie platformy Desired State Configuration dla inżynierów
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405366"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="da1a1-103">Omówienie platformy Desired State Configuration dla inżynierów</span><span class="sxs-lookup"><span data-stu-id="da1a1-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="da1a1-104">Ten dokument jest przeznaczony dla zespołów deweloperów i operacji zrozumieć korzyści z programu PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="da1a1-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="da1a1-105">Dla zapewnia wyższy poziom Widok wartość DSC, zobacz [Przegląd Desired State Configuration dla osób podejmujących decyzje](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="da1a1-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="da1a1-106">Zalety Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="da1a1-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="da1a1-107">Istnieje DSC:</span><span class="sxs-lookup"><span data-stu-id="da1a1-107">DSC exists to:</span></span>

- <span data-ttu-id="da1a1-108">Zmniejsz złożoność obsługi skryptów w Windows</span><span class="sxs-lookup"><span data-stu-id="da1a1-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="da1a1-109">Zwiększanie szybkości iteracji</span><span class="sxs-lookup"><span data-stu-id="da1a1-109">Increase the speed of iteration</span></span>

<span data-ttu-id="da1a1-110">Pojęcie "ciągłego wdrażania" staje się niezwykle ważne.</span><span class="sxs-lookup"><span data-stu-id="da1a1-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="da1a1-111">Ciągłe wdrażanie oznacza możliwość wdrażania częściej i potencjalnie wiele razy dziennie.</span><span class="sxs-lookup"><span data-stu-id="da1a1-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="da1a1-112">Cel wdrożenia są nie poprawki, ale coś szybko opublikowane.</span><span class="sxs-lookup"><span data-stu-id="da1a1-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="da1a1-113">Wprowadzenie nowych funkcji przez proces tworzenia operacji jako sprawnie i niezawodne, jak to możliwe, zmniejszyć czas do osiągnięcia korzyści z nowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="da1a1-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="da1a1-114">Przejście do chmury obliczeniowej, oznacza to rozwiązanie wdrożenia, które korzysta z modelu "deklaratywnych" szablonów, gdzie środowisko stan końcowy jest zadeklarowany jako tekst, a publikowane w aparacie wdrażania.</span><span class="sxs-lookup"><span data-stu-id="da1a1-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="da1a1-115">Ta metoda wdrażania umożliwia dynamicznymi zmianami w dużej skali, przy użyciu odporność przed zagrożeniem awarii, ponieważ w dowolnym momencie wdrażania można spójnie powtórzyć, aby zagwarantować stanu końcowego.</span><span class="sxs-lookup"><span data-stu-id="da1a1-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="da1a1-116">Tworzenie narzędzi i usług, które obsługują ten styl operacji za pomocą automatyzacji to odpowiedzi na te zmiany.</span><span class="sxs-lookup"><span data-stu-id="da1a1-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="da1a1-117">DSC jest platforma, która zapewnia deklaracyjne i wdrażania (powtarzalne) idempotentne, konfiguracji i zgodności.</span><span class="sxs-lookup"><span data-stu-id="da1a1-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="da1a1-118">Platforma DSC umożliwia upewnij się, że składniki centrum danych prawidłowej konfiguracji, który uniemożliwia niepowodzeń wdrażania kosztowne i pozwala uniknąć błędów.</span><span class="sxs-lookup"><span data-stu-id="da1a1-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="da1a1-119">Traktując konfiguracje DSC jako część kodu aplikacji, DSC umożliwia ciągłe wdrażanie.</span><span class="sxs-lookup"><span data-stu-id="da1a1-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="da1a1-120">Konfiguracja DSC powinien zostać zaktualizowany w ramach aplikacji, zapewnia, że wiedzę potrzebną do wdrożenia aplikacji jest zawsze aktualny i gotowe do użycia.</span><span class="sxs-lookup"><span data-stu-id="da1a1-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="da1a1-121">"Mam programu PowerShell, dlaczego należy Desired State Configuration?"</span><span class="sxs-lookup"><span data-stu-id="da1a1-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="da1a1-122">Celem oddzielne konfiguracje DSC lub "co warto zrobić", wykonania lub "jak chcę to zrobił."</span><span class="sxs-lookup"><span data-stu-id="da1a1-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="da1a1-123">Oznacza to, że logika wykonywania znajduje się w ramach zasobów.</span><span class="sxs-lookup"><span data-stu-id="da1a1-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="da1a1-124">Użytkownicy nie muszą wiedzieć, jak wdrożyć lub wdrożyć funkcję, gdy zasób DSC dla tej funkcji jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="da1a1-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="da1a1-125">Dzięki temu użytkownikowi skupić się na strukturze ich wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="da1a1-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="da1a1-126">Na przykład skrypty programu PowerShell powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="da1a1-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="da1a1-127">Ten skrypt jest proste, zrozumiałe i proste.</span><span class="sxs-lookup"><span data-stu-id="da1a1-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="da1a1-128">Jednak przy próbie umieszczenie tego skryptu do środowiska produkcyjnego, uruchomisz kilka problemy.</span><span class="sxs-lookup"><span data-stu-id="da1a1-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="da1a1-129">Co się stanie w przypadku skryptu uruchamianego dwa razy w wierszu?</span><span class="sxs-lookup"><span data-stu-id="da1a1-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="da1a1-130">Co się stanie, jeśli Bob wcześniej był pełny dostęp do udziału?</span><span class="sxs-lookup"><span data-stu-id="da1a1-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="da1a1-131">Aby zrekompensować te problemy, "członu real" wersji skryptu będzie wyglądać bliżej mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="da1a1-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="da1a1-132">Ten skrypt jest bardziej złożone z dużą ilością logiki oraz obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="da1a1-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="da1a1-133">Skrypt jest bardziej złożone, ponieważ są już informujący, co ma gotowe, ale *jak to zrobić*.</span><span class="sxs-lookup"><span data-stu-id="da1a1-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="da1a1-134">DSC umożliwia określenie, co ma gotowe i podstawowej logiki jest wyodrębniony natychmiast.</span><span class="sxs-lookup"><span data-stu-id="da1a1-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="da1a1-135">Ten skrypt jest prawidłowo sformatowany i prostego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="da1a1-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="da1a1-136">Ścieżkami logiki oraz obsługi błędów, które występują w [zasobów](../resources/resources.md) implementacji, ale niewidoczna Autor skryptu.</span><span class="sxs-lookup"><span data-stu-id="da1a1-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="da1a1-137">Oddzielanie środowiska na podstawie struktury</span><span class="sxs-lookup"><span data-stu-id="da1a1-137">Separating Environment from Structure</span></span>

<span data-ttu-id="da1a1-138">Typowym wzorcem w infrastrukturze DevOps jest wielu środowisk na potrzeby wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="da1a1-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="da1a1-139">Na przykład może być środowisko "dev", umożliwia szybkie prototypów nowego kodu.</span><span class="sxs-lookup"><span data-stu-id="da1a1-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="da1a1-140">Kod w środowisku "dev" przechodzi do środowiska "test", gdzie Sprawdź nowe funkcje, inne osoby.</span><span class="sxs-lookup"><span data-stu-id="da1a1-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="da1a1-141">Na koniec kod przechodzi w stan "prod" lub w środowisku produkcyjnym działającej witryny.</span><span class="sxs-lookup"><span data-stu-id="da1a1-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="da1a1-142">Konfiguracje DSC obsłużyć ten potok dev-test-prod za pośrednictwem [dane konfiguracyjne](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="da1a1-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="da1a1-143">Przenosi to dodatkowo różnica między struktury konfiguracji z węzłów, które są zarządzane.</span><span class="sxs-lookup"><span data-stu-id="da1a1-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="da1a1-144">Na przykład można zdefiniować konfigurację, która wymaga programu SQL server, serwer usług IIS i serwer warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="da1a1-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="da1a1-145">Niezależnie od tego, jakie węzły odbierać różne części tej konfiguracji te trzy elementy zawsze będzie istnieć.</span><span class="sxs-lookup"><span data-stu-id="da1a1-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="da1a1-146">Dane konfiguracji można użyć aby wskazać wszystkie trzy elementy na tym samym komputerze dla środowiska deweloperskiego, oddzielne się trzy elementy do trzech różnych maszyn dla środowiska testowego, a na koniec na wszystkich serwerach produkcyjnych dla środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="da1a1-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="da1a1-147">Aby wdrożyć w różnych środowiskach, można wywołać **Start-DscConfiguration** z danymi prawidłowej konfiguracji dla środowisk docelowych.</span><span class="sxs-lookup"><span data-stu-id="da1a1-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="da1a1-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da1a1-148">See Also</span></span>

[<span data-ttu-id="da1a1-149">Konfiguracje</span><span class="sxs-lookup"><span data-stu-id="da1a1-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="da1a1-150">Dane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="da1a1-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="da1a1-151">Zasoby</span><span class="sxs-lookup"><span data-stu-id="da1a1-151">Resources</span></span>](../resources/resources.md)
