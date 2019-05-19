---
title: Jak dodać składnię do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855132"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="b6ea1-102">Jak dodać składnię do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6ea1-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="b6ea1-103">Przed przystąpieniem do kodu XML dla diagramu składni w pliku pomocy polecenia cmdlet, przeczytaj tę sekcję, aby uzyskać jasny obraz rodzaju danych, musisz podać, takie jak atrybuty parametrów i sposób wyświetlania tych danych na diagramie składni...</span><span class="sxs-lookup"><span data-stu-id="b6ea1-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="b6ea1-104">Atrybuty parametru</span><span class="sxs-lookup"><span data-stu-id="b6ea1-104">Parameter Attributes</span></span>

- <span data-ttu-id="b6ea1-105">Wymagana</span><span class="sxs-lookup"><span data-stu-id="b6ea1-105">Required</span></span>

  - <span data-ttu-id="b6ea1-106">W przypadku opcji true parametru musi znajdować się w wszystkie polecenia, które używają zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="b6ea1-107">W przypadku wartości FAŁSZ parametr jest opcjonalny w wszystkie polecenia, które używają zestawu parametrów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="b6ea1-108">Stanowisko</span><span class="sxs-lookup"><span data-stu-id="b6ea1-108">Position</span></span>

  - <span data-ttu-id="b6ea1-109">Jeśli nazwany, nazwa parametru jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="b6ea1-110">Jeśli pozycyjne, nazwa parametru jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="b6ea1-111">Gdy zostanie pominięty, wartość parametru musi być w określonej pozycji w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="b6ea1-112">Na przykład, jeśli wartość jest pozycja = "1", wartość tego parametru musi być pierwszym ani składać Nienazwana wartość parametru w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="b6ea1-113">Wejście potokowe</span><span class="sxs-lookup"><span data-stu-id="b6ea1-113">Pipeline Input</span></span>

  - <span data-ttu-id="b6ea1-114">W przypadku opcji true (ByValue), można przekazać dane wejściowe dla parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="b6ea1-115">Dane wejściowe są skojarzone z ("powiązana") nawet wtedy, gdy nazwa właściwości i typ obiektu nie jest zgodny z oczekiwanym typem parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="b6ea1-116">Windows PowerShell? składniki powiązania parametru spróbuj przekonwertować danych wejściowych do poprawnego typu i niepowodzenie polecenia tylko wtedy, gdy nie można przekonwertować typu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="b6ea1-117">Według wartości, można ją skojarzyć tylko jeden parametr w zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="b6ea1-118">W przypadku opcji true (ByPropertyName), można przekazać dane wejściowe dla parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="b6ea1-119">Jednak dane wejściowe są skojarzone z parametrem tylko wtedy, gdy nazwa parametru jest zgodna z nazwą właściwości obiektu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="b6ea1-120">Na przykład, jeśli nazwa parametru jest `Path`, obiekty w potoku do polecenia cmdlet są skojarzone z tego parametru, tylko wtedy, gdy obiekt ma właściwość o nazwie ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="b6ea1-121">Jeśli prawda (ByValue, ByPropertyName), można przekazać dane wejściowe dla parametru, nazwa właściwości lub wartości.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="b6ea1-122">Według wartości, można ją skojarzyć tylko jeden parametr w zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="b6ea1-123">W przypadku wartości FAŁSZ nie można przekazać danych wejściowych do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="b6ea1-124">Symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="b6ea1-124">Globbing</span></span>

  - <span data-ttu-id="b6ea1-125">W przypadku opcji true tekstu użytkownik wpisze wartość parametru może zawierać symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="b6ea1-126">Jeśli ma wartość FAŁSZ, tekst, użytkownik wpisze wartość tego parametru nie może zawierać symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="b6ea1-127">Atrybuty wartości parametru</span><span class="sxs-lookup"><span data-stu-id="b6ea1-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="b6ea1-128">Wymagana</span><span class="sxs-lookup"><span data-stu-id="b6ea1-128">Required</span></span>

  - <span data-ttu-id="b6ea1-129">W przypadku opcji true zawsze wtedy, gdy za pomocą parametru za pomocą polecenia należy użyć określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="b6ea1-130">Jeśli wartość to false, wartość parametru jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="b6ea1-131">Zazwyczaj wartość jest opcjonalna, tylko wtedy, gdy jest to jeden z kilku prawidłowe wartości dla parametru, takie jak w typie wyliczanym.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="b6ea1-132">Wymagany atrybut wartości parametru różni się od wymaganego atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="b6ea1-133">Atrybut wymagany parametr wskazuje, czy parametr (i jego wartość) musi być uwzględniony podczas wywoływania polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="b6ea1-134">Z kolei wymaganego atrybutu jako wartość parametru jest używana tylko wtedy, gdy parametr znajduje się w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="b6ea1-135">Wskazuje, czy takiej wartości musi być używana z parametrem.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="b6ea1-136">Zazwyczaj wymaganych wartości parametrów, które są symbolami zastępczymi, a wartości parametrów, które są literału nie są wymagane, ponieważ są one jednym z kilku wartości, które mogą być używane z parametrem.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="b6ea1-137">Zbieranie informacji o składni</span><span class="sxs-lookup"><span data-stu-id="b6ea1-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="b6ea1-138">Uruchom przy użyciu nazwy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="b6ea1-139">Lista parametrów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="b6ea1-140">Wpisz znak łącznika (znana także jako "dash" lub "znak minus" (ASCII 45) przed nazwą każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="b6ea1-141">Oddzielne parametry do zestawów parametrów (niektóre polecenia cmdlet może mieć tylko jeden zestaw parametrów).</span><span class="sxs-lookup"><span data-stu-id="b6ea1-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="b6ea1-142">W tym przykładzie Get-Tech polecenie cmdlet ma dwa zestawy parametrów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="b6ea1-143">Uruchom każdego parametru zestawu przy użyciu nazwy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="b6ea1-144">Wyświetl listę domyślnego parametru zestawu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-144">List the default parameter set first.</span></span> <span data-ttu-id="b6ea1-145">Parametr domyślny jest określony przez klasę polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="b6ea1-146">Dla każdego zestawu parametrów należy najpierw listę jego unikatowy parametr, chyba że istnieją parametry pozycyjne, które muszą występować jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="b6ea1-147">W poprzednim przykładzie parametry nazwy i Identyfikatora są unikatowe parametry dla dwóch zestawów parametrów (każdego zestawu parametrów musi mieć jeden parametr, który jest unikatowy dla tego zestawu parametrów).</span><span class="sxs-lookup"><span data-stu-id="b6ea1-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="b6ea1-148">Ułatwia użytkownikom na identyfikację zestaw parametrów, jakie należy podać parametr.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="b6ea1-149">Lista parametrów w kolejności, powinny one zostać wyświetlone w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="b6ea1-150">Kolejność nie ma znaczenia, lista parametrów powiązanych ze sobą, czy pierwsza lista najczęściej używane parametry.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="b6ea1-151">Pamiętaj wyświetlić listę parametry WhatIf i potwierdzenie, jeśli polecenie cmdlet obsługuje ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="b6ea1-152">Nie umieszczaj typowych parametrów (takie jak Verbose, debugowania i ErrorAction) w diagramie składni.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="b6ea1-153">`Get-Help` Polecenia cmdlet dodaje te informacje dla Ciebie, gdy zawiera temat pomocy.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="b6ea1-154">Dodaj wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-154">Add the parameter values.</span></span> <span data-ttu-id="b6ea1-155">W programie Windows PowerShell?, wartości parametrów są reprezentowane przez ich typ architektury .NET.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="b6ea1-156">Jednak nazwy typu można stosować skrót, takie jak "string", aby uzyskać System.String.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="b6ea1-157">Tak długo, jak ich znaczenie jest jasna, takie jak "string", aby uzyskać System.String i "int", aby uzyskać System.Int32, skrócić typów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="b6ea1-158">Lista wszystkich wartości wyliczenia, takich jak — parametr typu w poprzednim przykładzie, który może być ustawiony na "podstawowa" lub "zaawansowany".</span><span class="sxs-lookup"><span data-stu-id="b6ea1-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="b6ea1-159">Przełącz parametry, takie jak - listy w poprzednim przykładzie, nie ma wartości.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="b6ea1-160">Dodaj nawiasy kątowe do wartości parametrów, które są symbol zastępczy w porównaniu do wartości parametrów, które są literały.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="b6ea1-161">Parametry opcjonalne i ich wartości należy ująć w nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="b6ea1-162">Nazwy parametrów opcjonalnych (w przypadku parametrów pozycyjnych) należy ująć w nawiasy kwadratowe.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="b6ea1-163">Nazwy w przypadku parametrów pozycyjnych, takie jak nazwa parametru w poniższym przykładzie jest konieczne uwzględnienie w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="b6ea1-164">Jeśli wartość parametru może zawierać wiele wartości, takie jak listy nazw w parametrze Name, Dodaj parę nawiasów kwadratowych, bezpośrednio po wartości parametru.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="b6ea1-165">Jeśli użytkownik może wybrać z parametrów lub wartości parametrów, takich jak parametr typu, należy ująć wybrany w nawiasach klamrowych i je oddzielić wyłączne symbol(;) OR.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="b6ea1-166">Jeśli wartość tego parametru należy użyć określonego formatowania, takie jak znaki cudzysłowu lub nawiasów, Pokaż format, w składni.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="b6ea1-167">Kodowanie Diagram składni XML</span><span class="sxs-lookup"><span data-stu-id="b6ea1-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="b6ea1-168">Węzeł składni XML, który rozpoczyna się natychmiast po węźle, opis, który kończy się \</maml:description > tag.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="b6ea1-169">Aby dowiedzieć się, jak zbieranie danych używanych w diagram składni, zobacz [zbierania informacji o składni](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="b6ea1-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="b6ea1-170">Dodawanie węzła składni</span><span class="sxs-lookup"><span data-stu-id="b6ea1-170">Adding a Syntax Node</span></span>

<span data-ttu-id="b6ea1-171">Diagram składni wyświetlane w tematu pomocy polecenia cmdlet jest generowany na podstawie danych w węźle składni XML.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="b6ea1-172">Węzeł składni jest ujęta w parze \<: w składni polecenia > tagów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="b6ea1-173">Z każdego zestawu parametrów polecenia cmdlet, ujęte w parę \<polecenia: syntaxitem > tagów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="b6ea1-174">Nie ma żadnego limitu liczby \<polecenia: syntaxitem > Znaczniki, które można dodać.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="b6ea1-175">Węzeł składni, który ma węzły elementu składni dla dwóch zestawów parametrów można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="b6ea1-176">Dodawanie nazwy polecenia Cmdlet z parametrem zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b6ea1-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="b6ea1-177">Każdy zestaw parametrów polecenia cmdlet jest określona w węzeł elementu składni.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="b6ea1-178">Każdy węzeł elementu składni zaczyna się od parę \<maml:name > tagów, które zawierają nazwę polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="b6ea1-179">Poniższy przykład zawiera węzeł składni, który ma węzły elementu składni dla dwóch zestawów parametrów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="b6ea1-180">Dodawanie parametrów</span><span class="sxs-lookup"><span data-stu-id="b6ea1-180">Adding Parameters</span></span>

<span data-ttu-id="b6ea1-181">Każdy parametr dodany do węzła elementu składnia jest określona w parę \<: parametr > tagów.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="b6ea1-182">Potrzebujesz parę \<: parametr > znaczniki dla każdego parametru zestawu parametrów, z wyjątkiem wspólne parametry, które są dostarczane przez środowisko Windows PowerShell?</span><span class="sxs-lookup"><span data-stu-id="b6ea1-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="b6ea1-183">Atrybuty otwarcia \<: parametr > tag określić, jak parametr pojawia się na diagramie składni.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="b6ea1-184">Informacje o atrybutach parametrów, zobacz [atrybuty parametru](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="b6ea1-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="b6ea1-185">\<: Parametr > tag wspiera nie zawiera elementu podrzędnego \<maml:description > którego zawartość nigdy nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="b6ea1-186">Opisy parametrów są określone w węźle parametru pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="b6ea1-187">Aby uniknąć niespójności między informacjami zawartymi w elemencie składni bodes i węzeł parametr, Pomiń (\<maml:description > lub pozostawić je puste.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="b6ea1-188">Poniższy przykład zawiera węzeł elementu składni dla parametru zestawu z dwoma parametrami.</span><span class="sxs-lookup"><span data-stu-id="b6ea1-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
