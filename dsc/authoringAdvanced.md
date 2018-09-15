# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="7d97e-101">Zaawansowane DSC do tworzenia i współpracy</span><span class="sxs-lookup"><span data-stu-id="7d97e-101">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="7d97e-102">W tym artykule opisano rodzaje metody łączenia konfiguracjami i zasobami.</span><span class="sxs-lookup"><span data-stu-id="7d97e-102">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="7d97e-103">Celem dla każdego scenariusza jest takie same, aby ograniczyć złożoność przy konfiguracji z wieloma są preferowane nawiązać połączenie z serwerem stanu końcowego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="7d97e-103">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="7d97e-104">Na przykład będzie wiele zespołów współtworzących wynik wdrożenia serwera, na przykład właściciela aplikacji, utrzymanie stanu aplikacji i centralny zespół przy zwalnianiu zmiany podstawy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7d97e-104">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="7d97e-105">Szczegóły skutecznego każde podejście, w tym korzyści i zagrożeń są szczegółowo opisane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="7d97e-105">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Potok](images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="7d97e-107">Typy wspólne technik tworzenia pakietów administracyjnych</span><span class="sxs-lookup"><span data-stu-id="7d97e-107">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="7d97e-108">Istnieją dwa rozwiązania wbudowane Local Configuration Manager, aby włączyć tę koncepcję:</span><span class="sxs-lookup"><span data-stu-id="7d97e-108">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="7d97e-109">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="7d97e-109">Concept</span></span> | <span data-ttu-id="7d97e-110">Szczegółowe informacje</span><span class="sxs-lookup"><span data-stu-id="7d97e-110">Detailed Information</span></span>
|-|-
| <span data-ttu-id="7d97e-111">Konfiguracje częściowe</span><span class="sxs-lookup"><span data-stu-id="7d97e-111">Partial Configurations</span></span> | [<span data-ttu-id="7d97e-112">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="7d97e-112">Documentation</span></span>](partialconfigs.md)
| <span data-ttu-id="7d97e-113">Zasoby złożone</span><span class="sxs-lookup"><span data-stu-id="7d97e-113">Composite Resources</span></span> | [<span data-ttu-id="7d97e-114">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="7d97e-114">Documentation</span></span>](authoringresourcecomposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="7d97e-115">Opis wpływu każde podejście</span><span class="sxs-lookup"><span data-stu-id="7d97e-115">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="7d97e-116">Jedno z poniższych rozwiązań może służyć do zarządzania wynik wdrożenia serwera.</span><span class="sxs-lookup"><span data-stu-id="7d97e-116">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="7d97e-117">Istnieje jednak istotną różnicą w wpływ za pomocą danej metody.</span><span class="sxs-lookup"><span data-stu-id="7d97e-117">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="7d97e-118">Konfiguracje częściowe</span><span class="sxs-lookup"><span data-stu-id="7d97e-118">Partial Configurations</span></span>

<span data-ttu-id="7d97e-119">Korzystając z konfiguracje częściowe, Local Configuration Manager jest skonfigurowany do niezależnie zarządzać wieloma konfiguracjami.</span><span class="sxs-lookup"><span data-stu-id="7d97e-119">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="7d97e-120">Konfiguracje są kompilowane niezależnie i przypisywany do węzła.</span><span class="sxs-lookup"><span data-stu-id="7d97e-120">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="7d97e-121">Wymaga to LCM należy skonfigurować z wyprzedzeniem o nazwie każdej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d97e-121">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](images/PartialConfiguration.jpg)

<span data-ttu-id="7d97e-123">Konfiguracje częściowe zapewnia dwa lub więcej, zespoły Pełna kontrola nad konfiguracji serwera, często bez korzyści komunikacji i współpracy.</span><span class="sxs-lookup"><span data-stu-id="7d97e-123">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="7d97e-124">Klienci zostały podane opinie, które może to prowadzić do konfliktów zasobów niezamierzone zastąpienia i ostatecznie utraty kontroli true konfiguracji zasobu.</span><span class="sxs-lookup"><span data-stu-id="7d97e-124">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="7d97e-125">Ponadto klientów zostały podane opinii, korzystając z tego modelu, każdego kontroli zmian konfiguracji zespoły prawdopodobnie nie można w pełni przetestowane za pomocą potoku wydania, co prowadzi do nieoczekiwanych wyników w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7d97e-125">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="7d97e-126">**Jest niezwykle, że jeden potok używane do oceny, wszystkie zmiany wersji serwerów.**</span><span class="sxs-lookup"><span data-stu-id="7d97e-126">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="7d97e-127">Na poniższej ilustracji zespół B zwalnia ich częściowe konfiguracji do zespołu A. zespołu, A następnie uruchamia testy na serwerze z obu konfiguracje stosowane.</span><span class="sxs-lookup"><span data-stu-id="7d97e-127">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="7d97e-128">W tym modelu tylko jeden urząd ma uprawnienia do wprowadzania zmian w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7d97e-128">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](images/PartialSinglePipeline.jpg)

<span data-ttu-id="7d97e-130">Gdy są wymagane zmiany z zespół B, należy przesłać, żądanie ściągnięcia względem środowiska kontroli źródła Team A.</span><span class="sxs-lookup"><span data-stu-id="7d97e-130">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="7d97e-131">Zespół A może następnie przejrzyj zmiany, przy użyciu automatyzacji testów i wydania do środowiska produkcyjnego, gdy istnieje pewność, że zmiany nie spowoduje błędów w aplikacji lub usług hostowanych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7d97e-131">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="7d97e-132">Zasoby złożone</span><span class="sxs-lookup"><span data-stu-id="7d97e-132">Composite Resources</span></span>

<span data-ttu-id="7d97e-133">Zasób złożonego jest po prostu konfiguracji DSC w pakiecie jako zasób.</span><span class="sxs-lookup"><span data-stu-id="7d97e-133">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="7d97e-134">Nie istnieją specjalne wymagania dotyczące konfigurowania LCM do akceptowania zasoby złożone.</span><span class="sxs-lookup"><span data-stu-id="7d97e-134">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="7d97e-135">Zasoby są używane w ramach nowej konfiguracji i kompilacji pojedynczej wyniki w jednym pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="7d97e-135">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](images/CompositeResource.jpg)

<span data-ttu-id="7d97e-137">Istnieją dwa typowe scenariusze zasoby złożone.</span><span class="sxs-lookup"><span data-stu-id="7d97e-137">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="7d97e-138">Pierwsza to zmniejszyć złożoność i abstrakcyjny unikatowe koncepcje.</span><span class="sxs-lookup"><span data-stu-id="7d97e-138">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="7d97e-139">Drugi cel to umożliwić odniesienia do umieszczenia w pakiecie przez zespół aplikacji bezpiecznie wdrażać za pośrednictwem ich potoku tworzenia wersji w środowisku produkcyjnym, po pomyślnym przejściu wszystkich testów.</span><span class="sxs-lookup"><span data-stu-id="7d97e-139">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="7d97e-140">Zasoby złożone promowanie kompozycji i współpraca przy użyciu potoku podczas kompilowania dojrzałości operacyjne</span><span class="sxs-lookup"><span data-stu-id="7d97e-140">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="7d97e-141">Być może już używasz zasoby złożone bez wiedzy.</span><span class="sxs-lookup"><span data-stu-id="7d97e-141">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="7d97e-142">Na przykład **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="7d97e-142">An example is **ServiceSet**.</span></span>
<span data-ttu-id="7d97e-143">Ten zasób zarządza stan wielu usług Windows bez wymienienie ich osobno.</span><span class="sxs-lookup"><span data-stu-id="7d97e-143">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="7d97e-144">Właściwość Nazwa przyjmuje tablicę ciągów, aby podać nazwę każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="7d97e-144">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="7d97e-145">Podczas kompilowania konfiguracji MOF będzie zawierać unikatowy sekcji usługi dla każdej nazwy przekazywane do ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="7d97e-145">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="7d97e-146">Organizacje może być "agents" lub "pośredniczącym", który powinien być zainstalowany na każdym serwerze.</span><span class="sxs-lookup"><span data-stu-id="7d97e-146">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="7d97e-147">Zasób złożonego jest najlepszą odpowiedź, zarządzanie, zależnościami, instalacji i konfiguracji takiego narzędzia i programy narzędziowe.</span><span class="sxs-lookup"><span data-stu-id="7d97e-147">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="7d97e-148">Osobę lub zespół odpowiedzialny za rozwiązań obejmujących wiele serwerów autorów zawierające ich wymagania dotyczące konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d97e-148">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="7d97e-149">Następnie konfiguracji będzie dostarczana jako zasób złożonego za pomocą instrukcje podane w dokumentacji programu composite zasobów.</span><span class="sxs-lookup"><span data-stu-id="7d97e-149">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="7d97e-150">Na koniec nowy zasób złożonego powinny być publikowane do lokalizacji, na przykład do udziału plików lub NuGet źródła danych, w którym zespoły aplikacji mogą wykorzystywać je w ich konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d97e-150">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="7d97e-151">Każdorazowo zespół udostępnia nową wersję, będą one zwiększenie numeru wersji w manifeście modułu dla swojego zasobu złożonego.</span><span class="sxs-lookup"><span data-stu-id="7d97e-151">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="7d97e-152">Zespoły aplikacji obejmują złożonego zasobów w konfiguracji, które one tworzenie zarządzania zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d97e-152">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="7d97e-153">Gdy zespoły Operations/Security wydasz nową wersję ich zasobu, informują one zespoły aplikacji, nowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="7d97e-153">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="7d97e-154">Zespoły aplikacji mogą wyzwoliła wydanie do produkcji, gdzie jedyna różnica polega na linii bazowych.</span><span class="sxs-lookup"><span data-stu-id="7d97e-154">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="7d97e-155">Jednak zapewnia możliwość oceny wpływu na aplikacje przed ryzykiem przerwa w działaniu usługi.</span><span class="sxs-lookup"><span data-stu-id="7d97e-155">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="7d97e-156">Uwaga — informacje zwrotne dotyczące użytkowania zasoby złożone dołączyła krytykę, że wprowadzanie zmian wymaga kompilacji i zwalniania nowego pliku MOF.</span><span class="sxs-lookup"><span data-stu-id="7d97e-156">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="7d97e-157">To działanie jest celowe.</span><span class="sxs-lookup"><span data-stu-id="7d97e-157">This is by design.</span></span>
<span data-ttu-id="7d97e-158">Każdą nową wersją konfiguracji powinien zawierać statyczne odwołanie do określonej wersji poszczególnych zasobów i powinny być weryfikowane przez testy przed osiągnięciem węzły serwera produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="7d97e-158">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="7d97e-159">Proces testowania i zwalniania zmian z kontroli źródła tworzy bezpieczne środowisko służącą do zwalniania zmiany w partiach małe, ale często.</span><span class="sxs-lookup"><span data-stu-id="7d97e-159">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="7d97e-160">Aby uzyskać więcej informacji o zarządzaniu infrastrukturze podstawowej za pomocą potoków wydania, zobacz oficjalny dokument: [Model potoku wydania](http://aka.ms/thereleasepipelinemodel).</span><span class="sxs-lookup"><span data-stu-id="7d97e-160">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodel).</span></span>
