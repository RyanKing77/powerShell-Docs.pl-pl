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
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855118"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="7893f-102">Jak dodać przykłady do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="7893f-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="7893f-103">Warto poznać przykłady w pomocy dotyczącej poleceń Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7893f-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="7893f-104">Listę wszystkich nazw parametrów w poleceniu, nawet wtedy, gdy nazwy parametrów są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7893f-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="7893f-105">Dzięki temu użytkownikowi łatwo zinterpretować polecenia.</span><span class="sxs-lookup"><span data-stu-id="7893f-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="7893f-106">Należy unikać aliasów i nazw parametrów częściowych, mimo że działają one w Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="7893f-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="7893f-107">W opisie przykład wyjaśnić wymierne budowy polecenia.</span><span class="sxs-lookup"><span data-stu-id="7893f-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="7893f-108">Opisano, dlaczego Podjąłeś decyzję poszczególnych parametrów i wartości oraz jak w przypadku używania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7893f-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="7893f-109">Jeśli polecenie korzysta z wyrażenia, opisano je szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="7893f-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="7893f-110">Jeśli w poleceniu użyto właściwości i metod obiektów, szczególnie te właściwości, które nie są wyświetlane w domyślnym wyświetlaniem, skorzystaj z przykładu, który został szansy Monituj użytkownika o obiekcie.</span><span class="sxs-lookup"><span data-stu-id="7893f-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="7893f-111">Pomoc widoków wyświetlających przykłady</span><span class="sxs-lookup"><span data-stu-id="7893f-111">Help Views that Display Examples</span></span>

<span data-ttu-id="7893f-112">Przykłady są wyświetlane tylko w widokach szczegółowe i pełnej pomocy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7893f-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="7893f-113">Dodawanie węzła przykłady</span><span class="sxs-lookup"><span data-stu-id="7893f-113">Adding an Examples Node</span></span>

<span data-ttu-id="7893f-114">Następujący kod XML pokazuje, jak dodać węzeł przykłady, który zawiera jeden węzeł w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7893f-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="7893f-115">Dodaj węzły dodatkowe przykład każdego przykłady, które mają zostać uwzględnione w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="7893f-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="7893f-116">Dodawanie Title przykład</span><span class="sxs-lookup"><span data-stu-id="7893f-116">Adding an Example Title</span></span>

<span data-ttu-id="7893f-117">Następujący kod XML pokazuje, jak dodać tytuł dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="7893f-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="7893f-118">Tytuł jest używana do ustawiania przykład oprócz inne przykłady.</span><span class="sxs-lookup"><span data-stu-id="7893f-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="7893f-119">Windows PowerShell® używa standardowy nagłówek, który zawiera numer kolejny przykład.</span><span class="sxs-lookup"><span data-stu-id="7893f-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="7893f-120">Dodawanie kroku znaków</span><span class="sxs-lookup"><span data-stu-id="7893f-120">Adding Preceding Characters</span></span>

<span data-ttu-id="7893f-121">Następujący kod XML przedstawiono sposób dodawania znaków, takich jak wierszu programu Windows PowerShell, które są wyświetlane bezpośrednio przed przykładowe polecenie (bez spacji pośredniczące).</span><span class="sxs-lookup"><span data-stu-id="7893f-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="7893f-122">Windows PowerShell® używa w wierszu polecenia programu Windows PowerShell: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="7893f-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="7893f-123">Dodawanie polecenia</span><span class="sxs-lookup"><span data-stu-id="7893f-123">Adding the Command</span></span>

<span data-ttu-id="7893f-124">Następujący kod XML przedstawiono sposób dodawania rzeczywiste polecenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="7893f-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="7893f-125">Podczas dodawania polecenia, wpisz całą nazwę (nie należy używać aliasu) polecenia cmdlet i parametrów.</span><span class="sxs-lookup"><span data-stu-id="7893f-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="7893f-126">Ponadto mogą używać małych liter, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7893f-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="7893f-127">Dodawanie opisu</span><span class="sxs-lookup"><span data-stu-id="7893f-127">Adding a Description</span></span>

<span data-ttu-id="7893f-128">Następujący kod XML pokazuje, jak dodać opis w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7893f-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="7893f-129">Windows PowerShell® korzysta z jednego zestawu \<MAML: para > tagi opisu, nawet jeśli wiele \<MAML: para > Znaczniki może służyć.</span><span class="sxs-lookup"><span data-stu-id="7893f-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="7893f-130">Dodawanie przykładowych danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="7893f-130">Adding Example Output</span></span>

<span data-ttu-id="7893f-131">Następujący kod XML przedstawiono sposób dodawania danych wyjściowych polecenia.</span><span class="sxs-lookup"><span data-stu-id="7893f-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="7893f-132">Informacje o poleceniu wyników jest opcjonalne, ale w niektórych przypadkach warto pokazują efekt przy użyciu określonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="7893f-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="7893f-133">Windows PowerShell® używa dwóch zestawów pustego \<MAML: para > Znaczniki, aby rozdzielić dane wyjściowe polecenia polecenia.</span><span class="sxs-lookup"><span data-stu-id="7893f-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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