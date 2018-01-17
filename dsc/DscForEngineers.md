---
ms.date: 2017-10-13
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje"
ms.openlocfilehash: ae545ead0718def44d5a17708d254b872691e1d3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="106cd-103">Żądany przegląd stanu konfiguracji dla inżynierów</span><span class="sxs-lookup"><span data-stu-id="106cd-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="106cd-104">Ten dokument jest przeznaczony dla zespołów deweloperów i operacji korzyści z programu PowerShell żądanego stanu konfiguracji (DSC).</span><span class="sxs-lookup"><span data-stu-id="106cd-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="106cd-105">Dla zapewnia wyższy widok poziomu wartości DSC, można znaleźć pod adresem [żądany przegląd stanu konfiguracji dla inne osoby podejmujące decyzje](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="106cd-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="106cd-106">Korzyści wynikające z konfiguracji żądanego stanu</span><span class="sxs-lookup"><span data-stu-id="106cd-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="106cd-107">Istnieje DSC do:</span><span class="sxs-lookup"><span data-stu-id="106cd-107">DSC exists to:</span></span>

- <span data-ttu-id="106cd-108">Zmniejszanie złożoności skryptów w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="106cd-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="106cd-109">Przyspieszenie iteracji</span><span class="sxs-lookup"><span data-stu-id="106cd-109">Increase the speed of iteration</span></span>

<span data-ttu-id="106cd-110">Pojęcie "ciągłe wdrażanie" staje się coraz większe znaczenie.</span><span class="sxs-lookup"><span data-stu-id="106cd-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="106cd-111">Ciągłe wdrażanie oznacza możliwość wdrażania często, potencjalnie wiele razy dziennie.</span><span class="sxs-lookup"><span data-stu-id="106cd-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="106cd-112">Cel wdrożenia są nie rozwiązać coś, ale coś szybko opublikowane.</span><span class="sxs-lookup"><span data-stu-id="106cd-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="106cd-113">Pobieranie nowych funkcji do rozwoju do operacji możliwie najsprawniej i niezawodny sposób, jak to możliwe, ograniczenie czasu na wartość nowego logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="106cd-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="106cd-114">Przejście do chmury obliczeniowej oznacza wdrażania rozwiązania, które korzysta z modelu szablonu "deklaratywne", gdy środowisko stan końcowy został zadeklarowany jako tekst i opublikowane w aparacie wdrażania.</span><span class="sxs-lookup"><span data-stu-id="106cd-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="106cd-115">Ta metoda wdrażania umożliwia szybkie zmiany na dużą skalę, z odporności przed zagrożeniem awarii, ponieważ w dowolnym momencie wdrożenia można spójnie powtórzyć, aby zagwarantować stanu końcowego.</span><span class="sxs-lookup"><span data-stu-id="106cd-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="106cd-116">Tworzenie narzędzi i usług, które obsługują ten styl operacji za pomocą automatyzacji jest odpowiedzi na te zmiany.</span><span class="sxs-lookup"><span data-stu-id="106cd-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="106cd-117">DSC jest platforma, która zapewnia deklaratywne i wdrażania (powtarzalne) idempotentności, konfiguracji i zgodności.</span><span class="sxs-lookup"><span data-stu-id="106cd-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="106cd-118">Platforma DSC umożliwia zapewnienia prawidłowej konfiguracji, co pozwala uniknąć błędów i niepowodzeń wdrażania kosztowne uniemożliwia składniki centrum danych.</span><span class="sxs-lookup"><span data-stu-id="106cd-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="106cd-119">Traktując konfiguracji DSC jako części kodu aplikacji, DSC umożliwia ciągłego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="106cd-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="106cd-120">Powinny zostać uaktualnione konfiguracji DSC jako część aplikacji, zapewnia, że informacje potrzebne do wdrożenia aplikacji jest zawsze aktualne i gotowa do użycia.</span><span class="sxs-lookup"><span data-stu-id="106cd-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="106cd-121">"Mam programu PowerShell, dlaczego należy konfiguracji żądanego stanu"?</span><span class="sxs-lookup"><span data-stu-id="106cd-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="106cd-122">Oddzielne opcje konfiguracji DSC lub "co warto zrobić", z wykonywania lub "jak I chcesz to zrobić."</span><span class="sxs-lookup"><span data-stu-id="106cd-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="106cd-123">Oznacza to, że logika wykonywania jest zawarty w zasoby.</span><span class="sxs-lookup"><span data-stu-id="106cd-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="106cd-124">Użytkownicy nie muszą znać sposób wdrożenia lub funkcji jest wdrażany, kiedy zasób DSC tej funkcji jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="106cd-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="106cd-125">Dzięki temu użytkownikowi skupić się na strukturze ich wdrażania.</span><span class="sxs-lookup"><span data-stu-id="106cd-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="106cd-126">Na przykład skrypty programu PowerShell powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="106cd-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="106cd-127">Ten skrypt jest proste, zrozumiałe i bezpośrednie.</span><span class="sxs-lookup"><span data-stu-id="106cd-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="106cd-128">Jednak jeśli wprowadzenie tego skryptu do produkcji, należy uruchomić na kilka problemów.</span><span class="sxs-lookup"><span data-stu-id="106cd-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="106cd-129">Co się stanie w przypadku skryptu uruchamianego dwa razy pod rząd?</span><span class="sxs-lookup"><span data-stu-id="106cd-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="106cd-130">Co się stanie, jeśli Bob wcześniej ma pełny dostęp do udziału?</span><span class="sxs-lookup"><span data-stu-id="106cd-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="106cd-131">Kompensacji tych problemów, "rzeczywiste" wersji skryptu będzie wyglądać bliżej wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="106cd-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
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

<span data-ttu-id="106cd-132">Ten skrypt jest bardziej złożonych z dużą ilością logiki oraz obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="106cd-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="106cd-133">Skrypt jest bardziej złożony, ponieważ są już ostrzegający, co ma gotowe, ale *jak to zrobić*.</span><span class="sxs-lookup"><span data-stu-id="106cd-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="106cd-134">DSC umożliwia określenie, co ma gotowe i podstawowej logiki jest pobieranej optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="106cd-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="106cd-135">Ten skrypt jest prawidłowo sformatowany i prostego do odczytu.</span><span class="sxs-lookup"><span data-stu-id="106cd-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="106cd-136">Ścieżkami logiki oraz obsługi błędów są nadal dostępne w [zasobów](resources.md) implementacji, ale niewidoczna Autor skryptu.</span><span class="sxs-lookup"><span data-stu-id="106cd-136">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="106cd-137">Oddzielanie środowiska ze struktury</span><span class="sxs-lookup"><span data-stu-id="106cd-137">Separating Environment from Structure</span></span>

<span data-ttu-id="106cd-138">Wspólnego wzorca w DevOps ma wiele środowisk dla wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="106cd-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="106cd-139">Na przykład może być środowisku "dev" pozwala szybko prototypu nowy kod.</span><span class="sxs-lookup"><span data-stu-id="106cd-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="106cd-140">Kod ze środowiska "dev" przechodzi w stan środowiska "test", gdzie inne osoby zweryfikować nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="106cd-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="106cd-141">Na koniec kod przechodzi w stan "produkcyjnego" lub działającą witrynę środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="106cd-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="106cd-142">Konfiguracji DSC zmieścił się w tym potoku deweloperów test produkcyjną za pośrednictwem [dane konfiguracji](configData.md).</span><span class="sxs-lookup"><span data-stu-id="106cd-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="106cd-143">To dodatkowe abstracts różnica między struktury konfiguracji z węzłów, które są zarządzane.</span><span class="sxs-lookup"><span data-stu-id="106cd-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="106cd-144">Na przykład można zdefiniować konfigurację, która wymaga programu SQL server, serwer usług IIS i serwer warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="106cd-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="106cd-145">Niezależnie od tego, jakie węzłów odbierać różne tej konfiguracji te trzy elementy zawsze będzie obecne.</span><span class="sxs-lookup"><span data-stu-id="106cd-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="106cd-146">Dane konfiguracji umożliwia punktu wszystkie trzy elementy do tej samej maszynie w środowisku deweloperów, oddzielne limit trzy elementy do trzech różnych maszyn dla środowiska testowego, a na koniec na wszystkich serwerach produkcyjnych środowiska produkcyjną.</span><span class="sxs-lookup"><span data-stu-id="106cd-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="106cd-147">Aby wdrożyć w różnych środowiskach, można wywołać **Start DscConfiguration** z danymi prawidłowej konfiguracji środowiska docelową.</span><span class="sxs-lookup"><span data-stu-id="106cd-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="106cd-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="106cd-148">See Also</span></span>

[<span data-ttu-id="106cd-149">Konfiguracje</span><span class="sxs-lookup"><span data-stu-id="106cd-149">Configurations</span></span>](configurations.md)

[<span data-ttu-id="106cd-150">Dane konfiguracji</span><span class="sxs-lookup"><span data-stu-id="106cd-150">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="106cd-151">Zasoby</span><span class="sxs-lookup"><span data-stu-id="106cd-151">Resources</span></span>](resources.md)
