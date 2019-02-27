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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851940"
---
# <a name="how-to-add-parameter-information"></a>Jak dodać informacje o parametrach

W tej sekcji opisano sposób dodawania zawartości, która jest wyświetlana w sekcji Parametry tematu pomocy polecenia cmdlet. Parametry części tematu Pomocy zawiera listę parametrów polecenia cmdlet i zawiera szczegółowy opis każdego parametru.

Zawartość sekcji Parametry powinny być zgodne z zawartością sekcji SKŁADNI tematu Pomocy. Jest odpowiedzialny za autora pomocy, aby upewnić się, że węzeł składnię i parametry zawierają podobne elementy XML.

> [!NOTE]
> Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell. Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.

### <a name="to-add-parameters"></a>Aby dodać parametry

1. Otwórz plik pomocy polecenia cmdlet i Znajdź węzeł polecenia cmdlet, które są dokumentowanie. Jeśli dodajesz nowe polecenie cmdlet, musisz utworzyć nowy węzeł polecenia. Plik pomocy będzie zawierać węzeł dla każdego polecenia cmdlet, które udostępniasz zawartość pomocy dla polecenia. Oto przykład pusty węzeł polecenia.

    ```xml
    <command:command>
    </command:command>
    ```

2. W ramach węzła polecenia Odszukaj węzeł, opis i Dodaj węzeł parametrów, jak pokazano poniżej. Dozwolony jest tylko jeden węzeł parametrów i powinien on być niezwłocznie zgodny węzeł składni.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. W węźle parametrów Dodaj parametr węzła dla każdego parametru polecenia cmdlet, jak pokazano poniżej.

   W tym przykładzie węzłem parametr jest dodawany do trzech parametrów.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Ponieważ są to te same znaczniki XML, które są używane w węźle składni, ponieważ parametry określone w tym miejscu musi być zgodna parametrów określonych przez węzeł składni, możesz skopiować węzły parametrów z węzła składni i wklej je do węzła parametrów. Należy jednak pamiętać skopiować tylko jedno wystąpienie węzła parametru, nawet jeśli parametr jest określony w wielu parametr ustawia w składni.

4. Dla każdego parametru zestawu węzłów, w wartości atrybutów, które definiują właściwości każdego parametru. Te atrybuty są następujące: wymagane symboli wieloznacznych, pipelineinput i położenia.

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

5. Dla każdego węzła parametr Dodaj nazwę parametru. Oto przykład nazwy parametru dodany do węzła parametru.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Dla każdego węzła parametru Dodaj opis parametru. Oto przykład opis parametru dodany do węzła parametru.

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

7. Dla każdego węzła parametru Dodaj typ .NET Framework parametru. Typ parametru jest wyświetlane wraz z nazwą parametru.

   Oto przykład typ .NET Framework parametr dodany do węzła parametru.

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

8. Dla każdego węzła parametr Dodaj wartość domyślna parametru. Gdy zawartość jest wyświetlana, opis parametru dodaje się następujące zdanie: Domyślną jest "DefaultValue".

   Oto przykład wartość domyślna parametru zostanie dodany do węzła parametru.

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

9. Dla każdego parametru, który ma wiele wartości należy dodać węzła możliwych wartości.

   Oto przykład węzła możliwych wartości, który definiuje dwa możliwe wartości dla parametru

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

Oto kilka rzeczy do zapamiętania, podczas dodawania parametrów.

- Atrybuty parametru nie są wyświetlane we wszystkich widokach tematu pomocy polecenia cmdlet. Jednak są wyświetlane w tabeli, zgodnie z opisem parametr, gdy użytkownik poprosi o podanie pełnej (Get-Help \<cmdletname > — pełna) lub parametr (Get-Help \<cmdletname >-parametr) widok tego tematu.

- Opis parametru jest jednym z najważniejszych części tematu pomocy polecenia cmdlet. Opis powinien być krótki, a także szczegółowe. Należy również pamiętać, że jeśli opis parametru staje się zbyt długi, np. kiedy dwa parametry współdziałać ze sobą, możesz dodać większej ilości zawartości w sekcji "Uwagi" tematu pomocy polecenia cmdlet.

  Opis parametru udostępnia dwa typy informacji.

- Jakie polecenia cmdlet wykonuje, gdy zostanie użyty parametr.

- Wartości prawne są dla parametru.

- Ponieważ wartości parametrów są wyrażane jako obiekty .NET Framework, użytkownicy muszą dowiedzieć się więcej o tych wartości niż w przypadku tradycyjnych pomoc w wierszu polecenia. Monituj użytkownika, jaki typ danych parametru jest przeznaczona do akceptowania i obejmują przykłady.

Wartość domyślna parametru to wartość, która jest używana, gdy parametr nie jest określony w wierszu polecenia. Należy pamiętać, że wartością domyślną jest opcjonalny, a nie jest wymagany dla niektórych parametrów, takich jak wymaganych parametrów. Jednak należy określić wartość domyślną dla większości parametrów opcjonalnych.

Wartość domyślna ułatwia użytkownikom zrozumienie wpływu użycia nie parametrze. Opisz wartość domyślną bardzo ściślej mówiąc, takie jak "bieżący katalog" lub "środowiska Windows PowerShell katalogu instalacyjnego ($pshome)" opcjonalna ścieżka. Można także napisać zdania, w tym artykule opisano domyślne, takie jak następujące zdanie, które są używane do `PassThru` parametru: "Jeśli przekazywanie nie zostanie określony, polecenie cmdlet nie zostały spełnione obiektów w dół do potoku."  Ponadto ponieważ wartość jest wyświetlana obok nazwy pola "**wartość domyślna**", nie trzeba uwzględnić termin "wartość domyślna" we wpisie.

Wartość domyślna parametru nie jest wyświetlane we wszystkich widokach tematu pomocy polecenia cmdlet. Jednak jest wyświetlany w tabeli (wraz z atrybuty parametrów), zgodnie z opisem parametr, gdy użytkownik poprosi o podanie pełnej (Get-Help \<cmdletname > — pełna) lub parametr (Get-Help \<cmdletname >-parametr) widok kraju itp.

Następujący kody XML pokazuje parę `<dev:defaultValue>` tagi dodane do `<command:parameter>` węzła. Należy zauważyć, że wartość domyślna następuje natychmiast po zamykającym `</command:parameterValue>` tag (Jeśli określono wartość parametru) lub zamykania `</maml:description>` tag opis parametru. Nazwa.

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

Dodawanie wartości dla typów wyliczeniowych

Jeśli parametr ma wiele wartości lub wartości typu wyliczeniowego, można opcjonalnie \<dev:possibleValues > węzła. Ten węzeł pozwala określić nazwę i opis dla wielu wartości.

Należy pamiętać, że opisy wartości wyliczenia nie występują na liście w domyślnych widoków pomocy wyświetlany przez `Get-Help` polecenia cmdlet, ale inne osoby przeglądające pomocy może wyświetlić tę zawartość w swoich opinii.

Pokazano w poniższym XML `<dev:possibleValues>` węzeł z dwóch wartości.

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