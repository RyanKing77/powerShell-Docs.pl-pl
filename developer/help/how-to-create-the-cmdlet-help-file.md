---
title: Jak utworzyć plik pomocy dotyczącej poleceń Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083250"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="640cb-102">Jak utworzyć plik pomocy dotyczącej poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="640cb-103">W tej sekcji opisano, jak utworzyć prawidłowy plik XML zawierający zawartość tematy pomocy do poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="640cb-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="640cb-104">W tej sekcji omówiono, jak nazwa pliku pomocy, jak dodać odpowiednie nagłówki XML i sposób dodawania węzłów zawierających różne sekcje zawartości pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="640cb-105">Aby uzyskać pełny widok pliku pomocy, otwórz jeden z plików dll Help.xml znajduje się w katalogu instalacyjnym programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="640cb-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="640cb-106">Na przykład plik Microsoft.PowerShell.Commands.Management.dll Help.xml zawiera zawartość dla kilku poleceń cmdlet programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="640cb-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="640cb-107">Jak utworzyć plik pomocy dotyczącej poleceń Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="640cb-108">Utwórz plik tekstowy i zapisz go przy użyciu kodowania UTF8.</span><span class="sxs-lookup"><span data-stu-id="640cb-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="640cb-109">Nazwa pliku musi mieć następujący format, tak aby program Windows PowerShell można wykryć je jako plik pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="640cb-110">Dodaj następujące nagłówki XML do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="640cb-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="640cb-111">Należy pamiętać, że plik zostanie zweryfikowana względem schematu wielu agentów modelowania języka (MAML).</span><span class="sxs-lookup"><span data-stu-id="640cb-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="640cb-112">Obecnie usługa programu Windows PowerShell nie zapewnia żadnych narzędzi do sprawdzania poprawności pliku.</span><span class="sxs-lookup"><span data-stu-id="640cb-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="640cb-113">Dodaj węzeł polecenia do pliku pomocy polecenia cmdlet dla każdego polecenia cmdlet w zestawie.</span><span class="sxs-lookup"><span data-stu-id="640cb-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="640cb-114">Każdy węzeł w węźle polecenia odnosi się do różnych części tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="640cb-115">W poniższej tabeli wymieniono elementu XML dla każdego węzła, następuje opisy dla każdego węzła.</span><span class="sxs-lookup"><span data-stu-id="640cb-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="640cb-116">Węzeł</span><span class="sxs-lookup"><span data-stu-id="640cb-116">Node</span></span>|<span data-ttu-id="640cb-117">Opis</span><span class="sxs-lookup"><span data-stu-id="640cb-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="640cb-118">Dodaje zawartość dla nazwy i streszczenie części tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-119">Aby uzyskać więcej informacji, zobacz [sposobu dodawania nazwa polecenia Cmdlet i streszczenie](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="640cb-120">Dodaje zawartość w sekcji Opis tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-121">Aby uzyskać więcej informacji, zobacz [sposób dodawania szczegółowy opis do tematu pomocy polecenia Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="640cb-122">Dodaje zawartość w sekcji SKŁADNI tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-123">Aby uzyskać więcej informacji, zobacz [jak dodać składnię do tematu pomocy polecenia Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="640cb-124">Dodaje zawartość sekcji Parametry tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-125">Aby uzyskać więcej informacji, zobacz [jak dodawanie parametrów do tematu pomocy polecenia Cmdlet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="640cb-126">Dodaje zawartość dla danych wejściowych części tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-127">Aby uzyskać więcej informacji, zobacz [sposób dodawania typów wejściowych do tematu pomocy polecenia Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="640cb-128">Dodaje zawartość dla danych wyjściowych części tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-129">Aby uzyskać więcej informacji, zobacz [jak dodać zwrócić wartości do tematu pomocy polecenia Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="640cb-130">Dodaje zawartość do sekcji Notatki tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-131">Aby uzyskać więcej informacji, zobacz [sposób dodawania notatki do tematu pomocy polecenia Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="640cb-132">Dodaje zawartość sekcji Przykłady tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-133">Aby uzyskać więcej informacji, zobacz [jak Dodaj przykłady do tematu pomocy polecenia Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="640cb-134">Dodaje zawartość w sekcji LINKI powiązane tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="640cb-135">Aby uzyskać więcej informacji, zobacz [jak dodać powiązane linki do tematu pomocy polecenia Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="640cb-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="640cb-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="640cb-136">Example</span></span>

 <span data-ttu-id="640cb-137">Oto przykład węzeł polecenia, który zawiera węzły dla różnych części tematu pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="640cb-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="640cb-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="640cb-138">See Also</span></span>

 [<span data-ttu-id="640cb-139">Jak dodać nazwę polecenia Cmdlet i streszczenie</span><span class="sxs-lookup"><span data-stu-id="640cb-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-140">Jak dodać szczegółowy opis do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="640cb-141">Jak dodać składnię do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-142">Jak dodać parametry do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="640cb-143">Jak dodać typów wejściowych do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-144">Jak dodać wartości zwracane do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-145">Jak dodać informacje o do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-146">Jak dodawać przykłady do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-147">Jak dodać powiązane linki do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="640cb-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="640cb-148">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="640cb-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)