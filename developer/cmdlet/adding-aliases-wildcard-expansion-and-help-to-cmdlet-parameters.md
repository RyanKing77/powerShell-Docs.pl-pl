---
title: Dodawanie aliasy, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054883"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="15f7c-102">Dodawanie aliasów, rozszerzenia symboli wieloznacznych i pomocy do parametrów polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="15f7c-103">W tej sekcji opisano sposób dodawania aliasów i rozwijanie symbolu wieloznacznego i pomocy wiadomości do parametrów polecenia cmdlet Stop-Proc (opisanego w [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="15f7c-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="15f7c-104">To polecenie cmdlet Stop-Proc podejmuje próby zatrzymania procesów, które są pobierane za pomocą polecenia cmdlet Get-Proc (opisanego w [tworzenia Your pierwsze polecenie Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="15f7c-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="15f7c-105">Tematy w tej sekcji są następujące:</span><span class="sxs-lookup"><span data-stu-id="15f7c-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="15f7c-106">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="15f7c-107">Definiowanie parametrów modyfikacji systemu</span><span class="sxs-lookup"><span data-stu-id="15f7c-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="15f7c-108">Definiowanie aliasu parametru</span><span class="sxs-lookup"><span data-stu-id="15f7c-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="15f7c-109">Tworzenie pomocy dotyczącej parametrów</span><span class="sxs-lookup"><span data-stu-id="15f7c-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="15f7c-110">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="15f7c-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="15f7c-111">Obsługa rozszerzenia symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="15f7c-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="15f7c-112">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="15f7c-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="15f7c-113">Definiowanie typów obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="15f7c-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="15f7c-114">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="15f7c-115">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="15f7c-116">Definiowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-116">Defining the Cmdlet</span></span>

<span data-ttu-id="15f7c-117">Pierwszym krokiem w procesie tworzenia polecenia cmdlet jest zawsze nazewnictwa polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f7c-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="15f7c-118">Ponieważ piszesz polecenia cmdlet, aby zmienić system powinien zostać nazwany odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="15f7c-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="15f7c-119">Ponieważ to polecenie cmdlet zatrzymuje procesów systemowych, używa ona czasownik "Stop" zdefiniowany przez [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasy z rzeczownikiem "Proc", aby wskazać proces.</span><span class="sxs-lookup"><span data-stu-id="15f7c-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="15f7c-120">Aby uzyskać więcej informacji na temat polecenia cmdlet zatwierdzonych czasowników, zobacz [nazwy zlecenie poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="15f7c-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="15f7c-121">Poniższy kod jest w definicji klasy dla tego polecenia cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="15f7c-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="15f7c-122">Definiowanie parametrów modyfikacji systemu</span><span class="sxs-lookup"><span data-stu-id="15f7c-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="15f7c-123">Twoje polecenie cmdlet musi definiować parametry tej modyfikacji systemu pomocy technicznej i opinie użytkowników.</span><span class="sxs-lookup"><span data-stu-id="15f7c-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="15f7c-124">Polecenia cmdlet należy zdefiniować `Name` parametru lub równoważnej, aby polecenie cmdlet będzie można zmodyfikować system jakieś identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="15f7c-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="15f7c-125">Ponadto, polecenie cmdlet należy zdefiniować `Force` i `PassThru` parametrów.</span><span class="sxs-lookup"><span data-stu-id="15f7c-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="15f7c-126">Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="15f7c-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="15f7c-127">Definiowanie aliasu parametru</span><span class="sxs-lookup"><span data-stu-id="15f7c-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="15f7c-128">Alias parametru może być alternatywną nazwę lub dobrze zdefiniowanych 1 literę lub litery 2 krótkiej nazwy parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f7c-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="15f7c-129">W obu przypadkach celem aliasy użycia jest uproszczenie wpisu użytkownika z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="15f7c-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="15f7c-130">Windows PowerShell obsługuje aliasów parametrów za pomocą [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atrybut, który używa składni deklaracji [Alias()].</span><span class="sxs-lookup"><span data-stu-id="15f7c-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="15f7c-131">W poniższym kodzie pokazano, jak aliasu jest dodawany do `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="15f7c-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="15f7c-132">Oprócz używania [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) atrybutu, programu Windows PowerShell środowisko uruchomieniowe wykonuje dopasowanie części nazwy, nawet, jeśli nie określono żadnych aliasów.</span><span class="sxs-lookup"><span data-stu-id="15f7c-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="15f7c-133">Na przykład Twoje polecenie cmdlet ma `FileName` parametr a to znaczy jedynym parametrem, który rozpoczyna się od `F`, użytkownik może wprowadzić `Filename`, `Filenam`, `File`, `Fi`, lub `F` i nadal rozpoznaje wpis `FileName` parametru.</span><span class="sxs-lookup"><span data-stu-id="15f7c-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="15f7c-134">Tworzenie pomocy dotyczącej parametrów</span><span class="sxs-lookup"><span data-stu-id="15f7c-134">Creating Help for Parameters</span></span>

<span data-ttu-id="15f7c-135">Program Windows PowerShell umożliwia tworzenie pomocy dla parametrów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f7c-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="15f7c-136">W tym przypadku każdego parametru używany do modyfikacji i użytkownika informacje zwrotne z systemu.</span><span class="sxs-lookup"><span data-stu-id="15f7c-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="15f7c-137">Dla każdego parametru do obsługi pomocy można ustawić `HelpMessage` atrybutu — słowo kluczowe w [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaracji atrybutu.</span><span class="sxs-lookup"><span data-stu-id="15f7c-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="15f7c-138">This — słowo kluczowe definiuje tekst do wyświetlenia dla użytkownika, aby uzyskać pomoc przy użyciu parametru.</span><span class="sxs-lookup"><span data-stu-id="15f7c-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="15f7c-139">Można również ustawić `HelpMessageBaseName` — słowo kluczowe, aby zidentyfikować podstawowej nazwy zasobu dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="15f7c-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="15f7c-140">Jeśli ustawisz to słowo kluczowe, należy także ustawić `HelpMessageResourceId` — słowo kluczowe, aby określić identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="15f7c-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="15f7c-141">Poniższy kod z tego polecenia cmdlet Stop-Proc definiuje `HelpMessage` atrybutu słowo kluczowe `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="15f7c-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="15f7c-142">Zastępowanie metody przetwarzania danych wejściowych</span><span class="sxs-lookup"><span data-stu-id="15f7c-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="15f7c-143">Twojego polecenia cmdlet jest przesłonięcie metody przetwarzania danych wejściowych, w większości przypadków będzie to [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="15f7c-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="15f7c-144">Podczas modyfikowania systemu, polecenia cmdlet powinny wywoływać [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) i [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metody, aby umożliwić użytkownikowi Aby przekazać opinię, zanim zostanie zmienione.</span><span class="sxs-lookup"><span data-stu-id="15f7c-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="15f7c-145">Aby uzyskać więcej informacji o tych metodach, zobacz [Tworzenie polecenia Cmdlet, który modyfikuje System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="15f7c-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="15f7c-146">Obsługa rozszerzenia symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="15f7c-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="15f7c-147">Aby umożliwić zaznaczanie wielu obiektów, można użyć Twojego polecenia cmdlet [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) i [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klasy zapewniające Obsługa rozszerzenia symboli wieloznacznych dla parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="15f7c-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="15f7c-148">Przykłady wzorców symboli wieloznacznych lsa \* \*txt i [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="15f7c-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="15f7c-149">Gdy wzorzec zawiera znak, który ma zostać użyty dosłownie, użyj znaków cudzysłowu Wstecz (') jako znak ucieczki.</span><span class="sxs-lookup"><span data-stu-id="15f7c-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="15f7c-150">Symbol wieloznaczny rozszerzenia nazwy pliku i ścieżka są przykłady typowych scenariuszy, w których polecenia cmdlet mogą być Zezwalaj na obsługę ścieżki w danych wejściowych, gdy wymagany jest wybór wielu obiektów.</span><span class="sxs-lookup"><span data-stu-id="15f7c-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="15f7c-151">Często zdarza się w systemie plików, w których użytkownik chce, aby wyświetlić wszystkie pliki znajdujące się w bieżącym folderze.</span><span class="sxs-lookup"><span data-stu-id="15f7c-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="15f7c-152">Tylko rzadko należy implementacji dopasowania wzorca dostosowane symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="15f7c-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="15f7c-153">W tym przypadku Twojego polecenia cmdlet powinien obsługiwać pełną 1003.2 POSIX, 3.13 specyfikacji dla rozszerzenia symboli wieloznacznych lub następujące podzbioru uproszczone:</span><span class="sxs-lookup"><span data-stu-id="15f7c-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="15f7c-154">**Znak zapytania (?).**</span><span class="sxs-lookup"><span data-stu-id="15f7c-154">**Question mark (?).**</span></span> <span data-ttu-id="15f7c-155">Dopasowuje dowolny znak w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="15f7c-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="15f7c-156">**Gwiazdka (\*).**</span><span class="sxs-lookup"><span data-stu-id="15f7c-156">**Asterisk (\*).**</span></span> <span data-ttu-id="15f7c-157">Dopasowuje zero lub więcej znaków, zaczynając od określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="15f7c-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="15f7c-158">**Otwierającego nawiasu ([]).**</span><span class="sxs-lookup"><span data-stu-id="15f7c-158">**Open bracket ([).**</span></span> <span data-ttu-id="15f7c-159">Wprowadza wzorzec wyrażenie w nawiasie kwadratowym, który może zawierać znaków lub zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="15f7c-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="15f7c-160">Jeśli zakres jest wymagany, łącznika (-) jest używany do wskazania zakresu.</span><span class="sxs-lookup"><span data-stu-id="15f7c-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="15f7c-161">**Zamknij nawiasu (]).**</span><span class="sxs-lookup"><span data-stu-id="15f7c-161">**Close bracket (]).**</span></span> <span data-ttu-id="15f7c-162">Kończy się wzorzec wyrażenie w nawiasie kwadratowym.</span><span class="sxs-lookup"><span data-stu-id="15f7c-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="15f7c-163">**Oferta wstecz znaku ucieczki (').**</span><span class="sxs-lookup"><span data-stu-id="15f7c-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="15f7c-164">Wskazuje, że następny znak należy podjąć dosłownie.</span><span class="sxs-lookup"><span data-stu-id="15f7c-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="15f7c-165">Należy pamiętać, że podczas określania znaku cudzysłowu Wstecz, z poziomu wiersza polecenia (w przeciwieństwie do określenia programowo), znaku ucieczki wstecz oferty należy określić dwa razy.</span><span class="sxs-lookup"><span data-stu-id="15f7c-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="15f7c-166">Aby uzyskać więcej informacji na temat wzorców symboli wieloznacznych, zobacz [obsługi symboli wieloznacznych w parametrach polecenia Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="15f7c-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="15f7c-167">Poniższy kod pokazuje, jak ustawić opcje symboli wieloznacznych i zdefiniuj wzór symboli wieloznacznych, używany do rozpoznawania `Name` parametrów dla tego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f7c-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="15f7c-168">Poniższy kod przedstawia sposób testowania, czy nazwa procesu jest zgodny ze wzorcem zdefiniowanych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="15f7c-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="15f7c-169">Zwróć uwagę, że w tym przypadku jeśli nazwa procesu nie jest zgodna z wzorcem, polecenia cmdlet w dalszym ciągu na Pobierz dalej nazwę procesu.</span><span class="sxs-lookup"><span data-stu-id="15f7c-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="15f7c-170">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="15f7c-170">Code Sample</span></span>

<span data-ttu-id="15f7c-171">Aby uzyskać pełne C# przykładowego kodu, zobacz [przykładowe StopProcessSample03](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="15f7c-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="15f7c-172">Zdefiniuj typy obiektów i formatowanie</span><span class="sxs-lookup"><span data-stu-id="15f7c-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="15f7c-173">Program Windows PowerShell przekazuje informacje między poleceniami cmdlet, używając obiektów platformy .net.</span><span class="sxs-lookup"><span data-stu-id="15f7c-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="15f7c-174">W związku z tym polecenie cmdlet może być konieczne zdefiniowanie swój własny typ, lub polecenie cmdlet może być konieczne rozszerzyć istniejący typ dostarczane przez inne polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15f7c-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="15f7c-175">Aby uzyskać więcej informacji na temat definiowania nowych typów lub rozszerzanie istniejących typów, zobacz [rozszerzanie typów obiektów i formatowanie](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="15f7c-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="15f7c-176">Tworzenie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-176">Building the Cmdlet</span></span>

<span data-ttu-id="15f7c-177">Po zaimplementowaniu polecenia cmdlet, musi być zarejestrowana przy użyciu programu Windows PowerShell za pomocą przystawki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15f7c-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="15f7c-178">Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [sposób zarejestrować poleceń cmdlet, dostawców i hostowania aplikacji](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="15f7c-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="15f7c-179">Testowanie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-179">Testing the Cmdlet</span></span>

<span data-ttu-id="15f7c-180">Po zarejestrowaniu Twojego polecenia cmdlet przy użyciu programu Windows PowerShell można ją przetestować, uruchamiając go w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="15f7c-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="15f7c-181">Teraz przetestuj przykładowe polecenie cmdlet Stop-Proc.</span><span class="sxs-lookup"><span data-stu-id="15f7c-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="15f7c-182">Aby uzyskać więcej informacji o korzystaniu z poleceń cmdlet w wierszu polecenia, zobacz [wprowadzenie do programu Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="15f7c-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="15f7c-183">Uruchom program Windows PowerShell i użyj Stop-Proc, aby zatrzymać proces przy użyciu ProcessName alias `Name` parametru.</span><span class="sxs-lookup"><span data-stu-id="15f7c-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="15f7c-184">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="15f7c-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="15f7c-185">W wierszu polecenia, należy wprowadzić poniższy wpis.</span><span class="sxs-lookup"><span data-stu-id="15f7c-185">Make the following entry on the command line.</span></span> <span data-ttu-id="15f7c-186">Parametr Name jest obowiązkowy, zostanie wyświetlony monit o jej.</span><span class="sxs-lookup"><span data-stu-id="15f7c-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="15f7c-187">Wprowadzanie "!"</span><span class="sxs-lookup"><span data-stu-id="15f7c-187">Entering "!?"</span></span> <span data-ttu-id="15f7c-188">wyświetlenie tekstu pomocy skojarzonych z parametrem.</span><span class="sxs-lookup"><span data-stu-id="15f7c-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="15f7c-189">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="15f7c-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="15f7c-190">Teraz wprowadź następujący wpis, aby zatrzymać wszystkie procesy, które pasuje do wzorca symbol wieloznaczny "\* Uwaga\*".</span><span class="sxs-lookup"><span data-stu-id="15f7c-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="15f7c-191">Zostanie wyświetlony monit przed zatrzymaniem każdy proces, który pasuje do wzorca.</span><span class="sxs-lookup"><span data-stu-id="15f7c-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="15f7c-192">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="15f7c-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="15f7c-193">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="15f7c-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="15f7c-194">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="15f7c-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="15f7c-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f7c-195">See Also</span></span>

[<span data-ttu-id="15f7c-196">Tworzenie polecenia Cmdlet, który modyfikuje systemu</span><span class="sxs-lookup"><span data-stu-id="15f7c-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="15f7c-197">Jak utworzyć polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15f7c-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="15f7c-198">Formatowanie i rozszerzanie typy obiektów</span><span class="sxs-lookup"><span data-stu-id="15f7c-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="15f7c-199">Jak zarejestrować poleceń cmdlet, dostawców i aplikacji hosta</span><span class="sxs-lookup"><span data-stu-id="15f7c-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="15f7c-200">Obsługa symboli wieloznacznych w parametry polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="15f7c-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="15f7c-201">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15f7c-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
