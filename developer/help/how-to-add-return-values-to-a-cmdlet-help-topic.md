---
title: Jak dodać zwrócenia wartości do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849217"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Jak dodać wartości zwracane do tematu pomocy dotyczącego polecenia cmdlet

W tej sekcji opisano sposób dodawania sekcję danych wyjściowych do tematu pomocy polecenia cmdlet Windows PowerShell®. Sekcję danych wyjściowych zawiera listę obiektów, które polecenie cmdlet zwraca lub przekazuje w dół do potoku klasy platformy .NET.

Nie ma żadnego limitu liczby klas, które można dodać do sekcji danych wyjściowych. Zwracane typy polecenia cmdlet są ujęte w \<polecenia: returnValues > węzła do każdej klasy, ujęte w \<polecenia: returnValue > element.

Jeśli polecenie cmdlet nie generuje żadnych danych wyjściowych, użyj tej sekcji, aby wskazać, że nie istnieje żadne dane wyjściowe. Na przykład zamiast nazwy klasy zapisu "None" i podaj krótki opis. Jeśli polecenie cmdlet generuje dane wyjściowe warunkowo, umożliwia ten węzeł wyjaśnić warunki i dodaniu opisu warunkowych danych wyjściowych.

Schemat zawiera dwie \<maml:description > elementy w każdym \<polecenia: returnValue > element. Jednak `Get-Help` polecenie cmdlet wyświetla tylko zawartość \<polecenia: returnValue > /\<maml:description > element.

Począwszy od programu Windows PowerShell 3.0 `Get-Help` polecenie cmdlet wyświetla zawartość \<maml:uri > element. Ten element umożliwia kierowanie użytkowników do tematów opisujących klasa platformy .NET.

Pokazano w poniższym XML \<maml:returnValues > węzła.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

Następujący kody XML pokazuje przykład użycia \<maml:returnValues > węzła typu danych wyjściowych dokumentu.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



