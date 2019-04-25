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
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083386"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Jak dodać składnię do tematu pomocy dotyczącego polecenia cmdlet

- [Atrybuty parametru](#Parameter-Attributes)

- [Atrybuty wartości parametru](#Parameter-Value-Attributes)

- [Zbieranie informacji o składni](#Gathering-Syntax-Information)

- [Kodowanie Diagram składni XML](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Co należy wiedzieć o Diagram składni w pomocy dotyczącej poleceń Cmdlet

Przed przystąpieniem do kodu XML dla diagramu składni w pliku pomocy polecenia cmdlet, przeczytaj tę sekcję, aby uzyskać jasny obraz rodzaju danych, musisz podać, takie jak atrybuty parametrów i sposób wyświetlania tych danych na diagramie składni...

### <a name="parameter-attributes"></a>Atrybuty parametru

- Wymagana

  - W przypadku opcji true parametru musi znajdować się w wszystkie polecenia, które używają zestawu parametrów.

  - W przypadku wartości FAŁSZ parametr jest opcjonalny w wszystkie polecenia, które używają zestawu parametrów.

- Stanowisko

  - Jeśli nazwany, nazwa parametru jest wymagana.

  - Jeśli pozycyjne, nazwa parametru jest opcjonalne. Gdy zostanie pominięty, wartość parametru musi być w określonej pozycji w poleceniu. Na przykład, jeśli wartość jest pozycja = "1", wartość tego parametru musi być pierwszym ani składać Nienazwana wartość parametru w poleceniu.

- Wejście potokowe

  - W przypadku opcji true (ByValue), można przekazać dane wejściowe dla parametru. Dane wejściowe są skojarzone z ("powiązana") nawet wtedy, gdy nazwa właściwości i typ obiektu nie jest zgodny z oczekiwanym typem parametru. Windows PowerShell? składniki powiązania parametru spróbuj przekonwertować danych wejściowych do poprawnego typu i niepowodzenie polecenia tylko wtedy, gdy nie można przekonwertować typu. Według wartości, można ją skojarzyć tylko jeden parametr w zestaw parametrów.

  - W przypadku opcji true (ByPropertyName), można przekazać dane wejściowe dla parametru. Jednak dane wejściowe są skojarzone z parametrem tylko wtedy, gdy nazwa parametru jest zgodna z nazwą właściwości obiektu danych wejściowych. Na przykład, jeśli nazwa parametru jest `Path`, obiekty w potoku do polecenia cmdlet są skojarzone z tego parametru, tylko wtedy, gdy obiekt ma właściwość o nazwie ścieżki.

  - Jeśli prawda (ByValue, ByPropertyName), można przekazać dane wejściowe dla parametru, nazwa właściwości lub wartości. Według wartości, można ją skojarzyć tylko jeden parametr w zestaw parametrów.

  - W przypadku wartości FAŁSZ nie można przekazać danych wejściowych do tego parametru.

- Symboli wieloznacznych

  - W przypadku opcji true tekstu użytkownik wpisze wartość parametru może zawierać symbole wieloznaczne.

  - Jeśli ma wartość FAŁSZ, tekst, użytkownik wpisze wartość tego parametru nie może zawierać symboli wieloznacznych.

### <a name="parameter-value-attributes"></a>Atrybuty wartości parametru

- Wymagana

  - W przypadku opcji true zawsze wtedy, gdy za pomocą parametru za pomocą polecenia należy użyć określonej wartości.

  - Jeśli wartość to false, wartość parametru jest opcjonalne. Zazwyczaj wartość jest opcjonalna, tylko wtedy, gdy jest to jeden z kilku prawidłowe wartości dla parametru, takie jak w typie wyliczanym.

Wymagany atrybut wartości parametru różni się od wymaganego atrybutu parametru.

Atrybut wymagany parametr wskazuje, czy parametr (i jego wartość) musi być uwzględniony podczas wywoływania polecenia cmdlet. Z kolei wymaganego atrybutu jako wartość parametru jest używana tylko wtedy, gdy parametr znajduje się w poleceniu. Wskazuje, czy takiej wartości musi być używana z parametrem.

Zazwyczaj wymaganych wartości parametrów, które są symbolami zastępczymi, a wartości parametrów, które są literału nie są wymagane, ponieważ są one jednym z kilku wartości, które mogą być używane z parametrem.

### <a name="gathering-syntax-information"></a>Zbieranie informacji o składni

1. Uruchom przy użyciu nazwy polecenia cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Lista parametrów polecenia cmdlet. Wpisz znak łącznika (znana także jako "dash" lub "znak minus" (ASCII 45) przed nazwą każdego parametru. Oddzielne parametry do zestawów parametrów (niektóre polecenia cmdlet może mieć tylko jeden zestaw parametrów). W tym przykładzie Get-Tech polecenie cmdlet ma dwa zestawy parametrów.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Uruchom każdego parametru zestawu przy użyciu nazwy polecenia cmdlet.

   Wyświetl listę domyślnego parametru zestawu. Parametr domyślny jest określony przez klasę polecenia cmdlet.

   Dla każdego zestawu parametrów należy najpierw listę jego unikatowy parametr, chyba że istnieją parametry pozycyjne, które muszą występować jako pierwszy. W poprzednim przykładzie parametry nazwy i Identyfikatora są unikatowe parametry dla dwóch zestawów parametrów (każdego zestawu parametrów musi mieć jeden parametr, który jest unikatowy dla tego zestawu parametrów). Ułatwia użytkownikom na identyfikację zestaw parametrów, jakie należy podać parametr.

   Lista parametrów w kolejności, powinny one zostać wyświetlone w poleceniu. Kolejność nie ma znaczenia, lista parametrów powiązanych ze sobą, czy pierwsza lista najczęściej używane parametry.

   Pamiętaj wyświetlić listę parametry WhatIf i potwierdzenie, jeśli polecenie cmdlet obsługuje ShouldProcess.

   Nie umieszczaj typowych parametrów (takie jak Verbose, debugowania i ErrorAction) w diagramie składni. `Get-Help` Polecenia cmdlet dodaje te informacje dla Ciebie, gdy zawiera temat pomocy.

3. Dodaj wartości parametru. W programie Windows PowerShell?, wartości parametrów są reprezentowane przez ich typ architektury .NET. Jednak nazwy typu można stosować skrót, takie jak "string", aby uzyskać System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Tak długo, jak ich znaczenie jest jasna, takie jak "string", aby uzyskać System.String i "int", aby uzyskać System.Int32, skrócić typów.

   Lista wszystkich wartości wyliczenia, takich jak — parametr typu w poprzednim przykładzie, który może być ustawiony na "podstawowa" lub "zaawansowany".

   Przełącz parametry, takie jak - listy w poprzednim przykładzie, nie ma wartości.

4. Dodaj nawiasy kątowe do wartości parametrów, które są symbol zastępczy w porównaniu do wartości parametrów, które są literały.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Parametry opcjonalne i ich wartości należy ująć w nawiasy kwadratowe.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Nazwy parametrów opcjonalnych (w przypadku parametrów pozycyjnych) należy ująć w nawiasy kwadratowe. Nazwy w przypadku parametrów pozycyjnych, takie jak nazwa parametru w poniższym przykładzie jest konieczne uwzględnienie w poleceniu.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Jeśli wartość parametru może zawierać wiele wartości, takie jak listy nazw w parametrze Name, Dodaj parę nawiasów kwadratowych, bezpośrednio po wartości parametru.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Jeśli użytkownik może wybrać z parametrów lub wartości parametrów, takich jak parametr typu, należy ująć wybrany w nawiasach klamrowych i je oddzielić wyłączne symbol(;) OR.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Jeśli wartość tego parametru należy użyć określonego formatowania, takie jak znaki cudzysłowu lub nawiasów, Pokaż format, w składni.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Kodowanie Diagram składni XML

Węzeł składni XML, który rozpoczyna się natychmiast po węźle, opis, który kończy się \</maml:description > tag. Aby dowiedzieć się, jak zbieranie danych używanych w diagram składni, zobacz [zbierania informacji o składni](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Dodawanie węzła składni

Diagram składni wyświetlane w tematu pomocy polecenia cmdlet jest generowany na podstawie danych w węźle składni XML. Węzeł składni jest ujęta w parze \<: w składni polecenia > tagów. Z każdego zestawu parametrów polecenia cmdlet, ujęte w parę \<polecenia: syntaxitem > tagów. Nie ma żadnego limitu liczby \<polecenia: syntaxitem > Znaczniki, które można dodać.

Węzeł składni, który ma węzły elementu składni dla dwóch zestawów parametrów można znaleźć w poniższym przykładzie.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Dodawanie nazwy polecenia Cmdlet z parametrem zestawu danych

Każdy zestaw parametrów polecenia cmdlet jest określona w węzeł elementu składni. Każdy węzeł elementu składni zaczyna się od parę \<maml:name > tagów, które zawierają nazwę polecenia cmdlet.

Poniższy przykład zawiera węzeł składni, który ma węzły elementu składni dla dwóch zestawów parametrów.

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

### <a name="adding-parameters"></a>Dodawanie parametrów

Każdy parametr dodany do węzła elementu składnia jest określona w parę \<: parametr > tagów. Potrzebujesz parę \<: parametr > znaczniki dla każdego parametru zestawu parametrów, z wyjątkiem wspólne parametry, które są dostarczane przez środowisko Windows PowerShell?

Atrybuty otwarcia \<: parametr > tag określić, jak parametr pojawia się na diagramie składni. Informacje o atrybutach parametrów, zobacz [atrybuty parametru](#Parameter-Attributes).

> [!NOTE]
> \<: Parametr > tag wspiera nie zawiera elementu podrzędnego \<maml:description > którego zawartość nigdy nie jest wyświetlana. Opisy parametrów są określone w węźle parametru pliku XML. Aby uniknąć niespójności między informacjami zawartymi w elemencie składni bodes i węzeł parametr, Pomiń (\<maml:description > lub pozostawić je puste.

Poniższy przykład zawiera węzeł elementu składni dla parametru zestawu z dwoma parametrami.

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
