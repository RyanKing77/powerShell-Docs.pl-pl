---
title: Jak dodawać przykłady do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083471"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Jak dodać przykłady do tematu pomocy dotyczącego polecenia cmdlet

- [Warto poznać przykłady w pomocy dotyczącej poleceń Cmdlet](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [Pomoc widoków wyświetlających przykłady](#Help-Views-that-Display-Examples)

- [Dodawanie węzła przykłady](#Adding-an-Examples-Node)

- [Dodawanie kroku znaków](#Adding-Preceding-Characters)

- [Dodawanie polecenia](#Adding-the-Command)

- [Dodawanie opisu](#Adding-a-Description)

- [Dodawanie przykładowych danych wyjściowych](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Warto poznać przykłady w pomocy dotyczącej poleceń Cmdlet

- Listę wszystkich nazw parametrów w poleceniu, nawet wtedy, gdy nazwy parametrów są opcjonalne. Dzięki temu użytkownikowi łatwo zinterpretować polecenia.

- Należy unikać aliasów i nazw parametrów częściowych, mimo że działają one w Windows PowerShell®.

- W opisie przykład wyjaśnić wymierne budowy polecenia. Opisano, dlaczego Podjąłeś decyzję poszczególnych parametrów i wartości oraz jak w przypadku używania zmiennych.

- Jeśli polecenie korzysta z wyrażenia, opisano je szczegółowo.

- Jeśli w poleceniu użyto właściwości i metod obiektów, szczególnie te właściwości, które nie są wyświetlane w domyślnym wyświetlaniem, skorzystaj z przykładu, który został szansy Monituj użytkownika o obiekcie.

## <a name="help-views-that-display-examples"></a>Pomoc widoków wyświetlających przykłady

Przykłady są wyświetlane tylko w widokach szczegółowe i pełnej pomocy polecenia cmdlet.

## <a name="adding-an-examples-node"></a>Dodawanie węzła przykłady

Następujący kod XML pokazuje, jak dodać węzeł przykłady, który zawiera jeden węzeł w przykładzie. Dodaj węzły dodatkowe przykład każdego przykłady, które mają zostać uwzględnione w tym temacie.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Dodawanie Title przykład

Następujący kod XML pokazuje, jak dodać tytuł dla przykładu. Tytuł jest używana do ustawiania przykład oprócz inne przykłady. Windows PowerShell® używa standardowy nagłówek, który zawiera numer kolejny przykład.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Dodawanie kroku znaków

Następujący kod XML przedstawiono sposób dodawania znaków, takich jak wierszu programu Windows PowerShell, które są wyświetlane bezpośrednio przed przykładowe polecenie (bez spacji pośredniczące). Windows PowerShell® używa w wierszu polecenia programu Windows PowerShell: C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Dodawanie polecenia

Następujący kod XML przedstawiono sposób dodawania rzeczywiste polecenia przykładu. Podczas dodawania polecenia, wpisz całą nazwę (nie należy używać aliasu) polecenia cmdlet i parametrów. Ponadto mogą używać małych liter, jeśli to możliwe.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Dodawanie opisu

Następujący kod XML pokazuje, jak dodać opis w przykładzie. Windows PowerShell® korzysta z jednego zestawu \<MAML: para > tagi opisu, nawet jeśli wiele \<MAML: para > Znaczniki może służyć.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Dodawanie przykładowych danych wyjściowych

Następujący kod XML przedstawiono sposób dodawania danych wyjściowych polecenia. Informacje o poleceniu wyników jest opcjonalne, ale w niektórych przypadkach warto pokazują efekt przy użyciu określonych parametrów. Windows PowerShell® używa dwóch zestawów pustego \<MAML: para > Znaczniki, aby rozdzielić dane wyjściowe polecenia polecenia.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```