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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="92736-102">Jak dodać wartości zwracane do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="92736-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="92736-103">W tej sekcji opisano sposób dodawania sekcję danych wyjściowych do tematu pomocy polecenia cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="92736-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="92736-104">Sekcję danych wyjściowych zawiera listę obiektów, które polecenie cmdlet zwraca lub przekazuje w dół do potoku klasy platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="92736-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="92736-105">Nie ma żadnego limitu liczby klas, które można dodać do sekcji danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="92736-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="92736-106">Zwracane typy polecenia cmdlet są ujęte w \<polecenia: returnValues > węzła do każdej klasy, ujęte w \<polecenia: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="92736-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="92736-107">Jeśli polecenie cmdlet nie generuje żadnych danych wyjściowych, użyj tej sekcji, aby wskazać, że nie istnieje żadne dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="92736-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="92736-108">Na przykład zamiast nazwy klasy zapisu "None" i podaj krótki opis.</span><span class="sxs-lookup"><span data-stu-id="92736-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="92736-109">Jeśli polecenie cmdlet generuje dane wyjściowe warunkowo, umożliwia ten węzeł wyjaśnić warunki i dodaniu opisu warunkowych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="92736-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="92736-110">Schemat zawiera dwie \<maml:description > elementy w każdym \<polecenia: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="92736-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="92736-111">Jednak `Get-Help` polecenie cmdlet wyświetla tylko zawartość \<polecenia: returnValue > /\<maml:description > element.</span><span class="sxs-lookup"><span data-stu-id="92736-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="92736-112">Począwszy od programu Windows PowerShell 3.0 `Get-Help` polecenie cmdlet wyświetla zawartość \<maml:uri > element.</span><span class="sxs-lookup"><span data-stu-id="92736-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="92736-113">Ten element umożliwia kierowanie użytkowników do tematów opisujących klasa platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="92736-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="92736-114">Pokazano w poniższym XML \<maml:returnValues > węzła.</span><span class="sxs-lookup"><span data-stu-id="92736-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="92736-115">Następujący kody XML pokazuje przykład użycia \<maml:returnValues > węzła typu danych wyjściowych dokumentu.</span><span class="sxs-lookup"><span data-stu-id="92736-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



