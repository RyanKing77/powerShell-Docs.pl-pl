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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="8edd5-102">Jak dodać typy danych wejściowych do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="8edd5-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="8edd5-103">W tej sekcji opisano sposób dodawania sekcji danych wejściowych do tematu pomocy polecenia cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="8edd5-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="8edd5-104">W sekcji danych wejściowych zawiera listę obiektów, które polecenie cmdlet przyjmuje jako dane wejściowe z potoku, według wartości lub według nazwy właściwości klasy platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="8edd5-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="8edd5-105">Nie ma żadnego limitu liczby klas, które można dodać do sekcji danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8edd5-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="8edd5-106">Typy wejściowe są ujęte w \<polecenia: inputTypes > węzła do każdej klasy, ujęte w \<polecenia: atrybut inputType > element.</span><span class="sxs-lookup"><span data-stu-id="8edd5-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="8edd5-107">Schemat zawiera dwie \<maml:description > elementy w każdym \<polecenia: atrybut inputType > element.</span><span class="sxs-lookup"><span data-stu-id="8edd5-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="8edd5-108">Jednak `Get-Help` polecenie cmdlet wyświetla tylko zawartość \<polecenia: atrybut inputType > /\<maml:description >) elementu.</span><span class="sxs-lookup"><span data-stu-id="8edd5-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="8edd5-109">Począwszy od programu Windows PowerShell 3.0 `Get-Help` polecenie cmdlet wyświetla zawartość \<maml:uri > element.</span><span class="sxs-lookup"><span data-stu-id="8edd5-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="8edd5-110">Ten element umożliwia kierowanie użytkowników do tematów opisujących klasa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="8edd5-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="8edd5-111">Pokazano w poniższym XML \<maml:inputTypes > węzła.</span><span class="sxs-lookup"><span data-stu-id="8edd5-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="8edd5-112">Następujący kody XML pokazuje przykład użycia \<maml:inputTypes > węzła do danych wejściowych typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8edd5-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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