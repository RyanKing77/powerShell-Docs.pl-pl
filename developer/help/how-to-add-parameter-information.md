---
title: Jak dodać informacje o parametrach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083369"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="2ec33-102">Jak dodać informacje o parametrach</span><span class="sxs-lookup"><span data-stu-id="2ec33-102">How to Add Parameter Information</span></span>

<span data-ttu-id="2ec33-103">W tej sekcji opisano sposób dodawania zawartości, która jest wyświetlana w sekcji Parametry tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ec33-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="2ec33-104">Parametry części tematu Pomocy zawiera listę parametrów polecenia cmdlet i zawiera szczegółowy opis każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="2ec33-105">Zawartość sekcji Parametry powinny być zgodne z zawartością sekcji SKŁADNI tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="2ec33-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="2ec33-106">Jest odpowiedzialny za autora pomocy, aby upewnić się, że węzeł składnię i parametry zawierają podobne elementy XML.</span><span class="sxs-lookup"><span data-stu-id="2ec33-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="2ec33-107">Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ec33-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="2ec33-108">Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ec33-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="2ec33-109">Aby dodać parametry</span><span class="sxs-lookup"><span data-stu-id="2ec33-109">To Add Parameters</span></span>

1. <span data-ttu-id="2ec33-110">Otwórz plik pomocy polecenia cmdlet i Znajdź węzeł polecenia cmdlet, które są dokumentowanie.</span><span class="sxs-lookup"><span data-stu-id="2ec33-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="2ec33-111">Jeśli dodajesz nowe polecenie cmdlet, musisz utworzyć nowy węzeł polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ec33-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="2ec33-112">Plik pomocy będzie zawierać węzeł dla każdego polecenia cmdlet, które udostępniasz zawartość pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ec33-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="2ec33-113">Oto przykład pusty węzeł polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ec33-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="2ec33-114">W ramach węzła polecenia Odszukaj węzeł, opis i Dodaj węzeł parametrów, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="2ec33-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="2ec33-115">Dozwolony jest tylko jeden węzeł parametrów i powinien on być niezwłocznie zgodny węzeł składni.</span><span class="sxs-lookup"><span data-stu-id="2ec33-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="2ec33-116">W węźle parametrów Dodaj parametr węzła dla każdego parametru polecenia cmdlet, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="2ec33-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="2ec33-117">W tym przykładzie węzłem parametr jest dodawany do trzech parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ec33-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="2ec33-118">Ponieważ są to te same znaczniki XML, które są używane w węźle składni, ponieważ parametry określone w tym miejscu musi być zgodna parametrów określonych przez węzeł składni, możesz skopiować węzły parametrów z węzła składni i wklej je do węzła parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ec33-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="2ec33-119">Należy jednak pamiętać skopiować tylko jedno wystąpienie węzła parametru, nawet jeśli parametr jest określony w wielu parametr ustawia w składni.</span><span class="sxs-lookup"><span data-stu-id="2ec33-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="2ec33-120">Dla każdego parametru zestawu węzłów, w wartości atrybutów, które definiują właściwości każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="2ec33-121">Te atrybuty są następujące: wymagane symboli wieloznacznych, pipelineinput i położenia.</span><span class="sxs-lookup"><span data-stu-id="2ec33-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="2ec33-122">Dla każdego węzła parametr Dodaj nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="2ec33-123">Oto przykład nazwy parametru dodany do węzła parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="2ec33-124">Dla każdego węzła parametru Dodaj opis parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="2ec33-125">Oto przykład opis parametru dodany do węzła parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="2ec33-126">Dla każdego węzła parametru Dodaj typ .NET Framework parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="2ec33-127">Typ parametru jest wyświetlane wraz z nazwą parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="2ec33-128">Oto przykład typ .NET Framework parametr dodany do węzła parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="2ec33-129">Dla każdego węzła parametr Dodaj wartość domyślna parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="2ec33-130">Gdy zawartość jest wyświetlana, opis parametru dodaje się następujące zdanie: Domyślną jest "DefaultValue".</span><span class="sxs-lookup"><span data-stu-id="2ec33-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="2ec33-131">Oto przykład wartość domyślna parametru zostanie dodany do węzła parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="2ec33-132">Dla każdego parametru, który ma wiele wartości należy dodać węzła możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="2ec33-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="2ec33-133">Oto przykład węzła możliwych wartości, który definiuje dwa możliwe wartości dla parametru</span><span class="sxs-lookup"><span data-stu-id="2ec33-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="2ec33-134">Oto kilka rzeczy do zapamiętania, podczas dodawania parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ec33-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="2ec33-135">Atrybuty parametru nie są wyświetlane we wszystkich widokach tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ec33-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="2ec33-136">Jednak są wyświetlane w tabeli, zgodnie z opisem parametr, gdy użytkownik poprosi o podanie pełnej (Get-Help \<cmdletname > — pełna) lub parametr (Get-Help \<cmdletname >-parametr) widok tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2ec33-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="2ec33-137">Opis parametru jest jednym z najważniejszych części tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ec33-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="2ec33-138">Opis powinien być krótki, a także szczegółowe.</span><span class="sxs-lookup"><span data-stu-id="2ec33-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="2ec33-139">Należy również pamiętać, że jeśli opis parametru staje się zbyt długi, np. kiedy dwa parametry współdziałać ze sobą, możesz dodać większej ilości zawartości w sekcji "Uwagi" tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ec33-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="2ec33-140">Opis parametru udostępnia dwa typy informacji.</span><span class="sxs-lookup"><span data-stu-id="2ec33-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="2ec33-141">Jakie polecenia cmdlet wykonuje, gdy zostanie użyty parametr.</span><span class="sxs-lookup"><span data-stu-id="2ec33-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="2ec33-142">Wartości prawne są dla parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="2ec33-143">Ponieważ wartości parametrów są wyrażane jako obiekty .NET Framework, użytkownicy muszą dowiedzieć się więcej o tych wartości niż w przypadku tradycyjnych pomoc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ec33-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="2ec33-144">Monituj użytkownika, jaki typ danych parametru jest przeznaczona do akceptowania i obejmują przykłady.</span><span class="sxs-lookup"><span data-stu-id="2ec33-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="2ec33-145">Wartość domyślna parametru to wartość, która jest używana, gdy parametr nie jest określony w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2ec33-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="2ec33-146">Należy pamiętać, że wartością domyślną jest opcjonalny, a nie jest wymagany dla niektórych parametrów, takich jak wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ec33-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="2ec33-147">Jednak należy określić wartość domyślną dla większości parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="2ec33-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="2ec33-148">Wartość domyślna ułatwia użytkownikom zrozumienie wpływu użycia nie parametrze.</span><span class="sxs-lookup"><span data-stu-id="2ec33-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="2ec33-149">Opisz wartość domyślną bardzo ściślej mówiąc, takie jak "bieżący katalog" lub "środowiska Windows PowerShell katalogu instalacyjnego ($pshome)" opcjonalna ścieżka.</span><span class="sxs-lookup"><span data-stu-id="2ec33-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="2ec33-150">Można także napisać zdania, w tym artykule opisano domyślne, takie jak następujące zdanie, które są używane do `PassThru` parametru: "Jeśli przekazywanie nie zostanie określony, polecenie cmdlet nie zostały spełnione obiektów w dół do potoku."</span><span class="sxs-lookup"><span data-stu-id="2ec33-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="2ec33-151">Ponadto ponieważ wartość jest wyświetlana obok nazwy pola "**wartość domyślna**", nie trzeba uwzględnić termin "wartość domyślna" we wpisie.</span><span class="sxs-lookup"><span data-stu-id="2ec33-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="2ec33-152">Wartość domyślna parametru nie jest wyświetlane we wszystkich widokach tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ec33-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="2ec33-153">Jednak jest wyświetlany w tabeli (wraz z atrybuty parametrów), zgodnie z opisem parametr, gdy użytkownik poprosi o podanie pełnej (Get-Help \<cmdletname > — pełna) lub parametr (Get-Help \<cmdletname >-parametr) widok kraju itp.</span><span class="sxs-lookup"><span data-stu-id="2ec33-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="2ec33-154">Następujący kody XML pokazuje parę `<dev:defaultValue>` tagi dodane do `<command:parameter>` węzła.</span><span class="sxs-lookup"><span data-stu-id="2ec33-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="2ec33-155">Należy zauważyć, że wartość domyślna następuje natychmiast po zamykającym `</command:parameterValue>` tag (Jeśli określono wartość parametru) lub zamykania `</maml:description>` tag opis parametru.</span><span class="sxs-lookup"><span data-stu-id="2ec33-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="2ec33-156">Nazwa.</span><span class="sxs-lookup"><span data-stu-id="2ec33-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="2ec33-157">Dodawanie wartości dla typów wyliczeniowych</span><span class="sxs-lookup"><span data-stu-id="2ec33-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="2ec33-158">Jeśli parametr ma wiele wartości lub wartości typu wyliczeniowego, można opcjonalnie \<dev:possibleValues > węzła.</span><span class="sxs-lookup"><span data-stu-id="2ec33-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="2ec33-159">Ten węzeł pozwala określić nazwę i opis dla wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="2ec33-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="2ec33-160">Należy pamiętać, że opisy wartości wyliczenia nie występują na liście w domyślnych widoków pomocy wyświetlany przez `Get-Help` polecenia cmdlet, ale inne osoby przeglądające pomocy może wyświetlić tę zawartość w swoich opinii.</span><span class="sxs-lookup"><span data-stu-id="2ec33-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="2ec33-161">Pokazano w poniższym XML `<dev:possibleValues>` węzeł z dwóch wartości.</span><span class="sxs-lookup"><span data-stu-id="2ec33-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```