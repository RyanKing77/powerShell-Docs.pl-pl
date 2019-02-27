---
title: Jak dodać typów wejściowych do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850176"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Jak dodać typy danych wejściowych do tematu pomocy dotyczącego polecenia cmdlet

W tej sekcji opisano sposób dodawania sekcji danych wejściowych do tematu pomocy polecenia cmdlet Windows PowerShell®. W sekcji danych wejściowych zawiera listę obiektów, które polecenie cmdlet przyjmuje jako dane wejściowe z potoku, według wartości lub według nazwy właściwości klasy platformy .NET.

Nie ma żadnego limitu liczby klas, które można dodać do sekcji danych wejściowych. Typy wejściowe są ujęte w \<polecenia: inputTypes > węzła do każdej klasy, ujęte w \<polecenia: atrybut inputType > element.

Schemat zawiera dwie \<maml:description > elementy w każdym \<polecenia: atrybut inputType > element. Jednak `Get-Help` polecenie cmdlet wyświetla tylko zawartość \<polecenia: atrybut inputType > /\<maml:description >) elementu.

Począwszy od programu Windows PowerShell 3.0 `Get-Help` polecenie cmdlet wyświetla zawartość \<maml:uri > element. Ten element umożliwia kierowanie użytkowników do tematów opisujących klasa platformy .NET.

Pokazano w poniższym XML \<maml:inputTypes > węzła.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Następujący kody XML pokazuje przykład użycia \<maml:inputTypes > węzła do danych wejściowych typu dokumentu.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```