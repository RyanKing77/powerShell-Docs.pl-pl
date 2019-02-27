---
title: Pisanie tematów Pomocy dotyczących poleceń cmdlet programu PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848111"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="80696-102">Zapisywanie Pomoc dla poleceń cmdlet programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="80696-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="80696-103">Polecenia cmdlet programu PowerShell może być przydatna, ale chyba, że tematy pomocy wyjaśniają, działanie polecenia cmdlet i jak z niej korzystać, polecenie cmdlet nie może pobrać używane, lub gorsza, może frustrować użytkowników.</span><span class="sxs-lookup"><span data-stu-id="80696-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="80696-104">Format pliku pomocy polecenia cmdlet opartego na XML zwiększa spójność, ale bardzo pomóc wymaga znacznie więcej.</span><span class="sxs-lookup"><span data-stu-id="80696-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="80696-105">Jeśli nigdy nie zostały zapisane pomocy polecenia cmdlet, należy rozważyć następujące wskazówki.</span><span class="sxs-lookup"><span data-stu-id="80696-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="80696-106">Schemat XML, wymagane do tworzenia tematu pomocy polecenia cmdlet jest opisane w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="80696-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="80696-107">Rozpoczynać [tworzenia pliku pomocy dotyczącej poleceń Cmdlet](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="80696-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="80696-108">Ten temat zawiera opis węzłów XML najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="80696-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="80696-109">Wskazówki dotyczące pisania w celu uzyskania pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="80696-110">Dobrze zapisu</span><span class="sxs-lookup"><span data-stu-id="80696-110">Write well</span></span>
<span data-ttu-id="80696-111">Nic nie zastępuje dobrze napisane tematu.</span><span class="sxs-lookup"><span data-stu-id="80696-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="80696-112">Jeśli nie jesteś Edytor professional, znaleźć moduł zapisujący lub edytora, aby.</span><span class="sxs-lookup"><span data-stu-id="80696-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="80696-113">Innym sposobem jest, aby skopiować tekst pomocy do programu Microsoft Word i użyć gramatykę i pisownię sprawdza, aby zwiększyć swoją pracę.</span><span class="sxs-lookup"><span data-stu-id="80696-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="80696-114">Po prostu zapisu</span><span class="sxs-lookup"><span data-stu-id="80696-114">Write simply</span></span>
<span data-ttu-id="80696-115">Użyj prostych słów i fraz.</span><span class="sxs-lookup"><span data-stu-id="80696-115">Use simple words and phrases.</span></span>
<span data-ttu-id="80696-116">Należy unikać żargonu.</span><span class="sxs-lookup"><span data-stu-id="80696-116">Avoid jargon.</span></span>
<span data-ttu-id="80696-117">Należy wziąć pod uwagę, że wielu czytników są wyposażone w tylko obcego słownika i tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="80696-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="80696-118">Stale zapisu</span><span class="sxs-lookup"><span data-stu-id="80696-118">Write consistently</span></span>
<span data-ttu-id="80696-119">Pomoc dla powiązane polecenia cmdlet powinny być podobne (na przykład get-x i set-x).</span><span class="sxs-lookup"><span data-stu-id="80696-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="80696-120">Na użytek standardowe opisy standardowe parametry, takie jak **życie** i **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="80696-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="80696-121">(Je skopiować z pomocy dla podstawowych poleceń cmdlet środowiska.) Użyj standardowych warunków.</span><span class="sxs-lookup"><span data-stu-id="80696-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="80696-122">Na przykład użyj "parametr", nie "argument" i użyj "polecenie cmdlet" nie "polecenie" lub "command-let".</span><span class="sxs-lookup"><span data-stu-id="80696-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="80696-123">Streszczenie rozpoczynać się zlecenia</span><span class="sxs-lookup"><span data-stu-id="80696-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="80696-124">Pole streszczenie informuje użytkownika, jakie polecenia cmdlet nie, co to jest ani nie jak to działa.</span><span class="sxs-lookup"><span data-stu-id="80696-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="80696-125">Czasowniki Utwórz instrukcję opartego na zadaniach informuje użytkowników, jeśli to polecenie cmdlet spełnia ich wymagań.</span><span class="sxs-lookup"><span data-stu-id="80696-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="80696-126">Użyj prostych zleceń, takich jak "get", "Utwórz" i "Zmień".</span><span class="sxs-lookup"><span data-stu-id="80696-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="80696-127">Należy unikać "set", który może być niejasna i ozdobnych wyrazy, takie jak "Modyfikuj".</span><span class="sxs-lookup"><span data-stu-id="80696-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="80696-128">Skup się na obiekty</span><span class="sxs-lookup"><span data-stu-id="80696-128">Focus on objects</span></span>
<span data-ttu-id="80696-129">Większość "get" wyświetlania poleceń cmdlet coś, ale ich podstawową funkcją jest pobranie obiektu.</span><span class="sxs-lookup"><span data-stu-id="80696-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="80696-130">W pomocy skupić się na obiekt, tak że użytkownicy wiedzą, że domyślnym wyświetlaniem jest jednym z wielu i czy można użyć metod i właściwości obiektu, który uzyskano, wykonując je na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="80696-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="80696-131">Szczegółowy opis zapisu</span><span class="sxs-lookup"><span data-stu-id="80696-131">Write detailed descriptions</span></span>
<span data-ttu-id="80696-132">Krótko listę wszystko, co zrobić w szczegółowy opis polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80696-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="80696-133">Jeśli jest funkcja main, aby zmienić jedną właściwość, ale polecenia cmdlet można zmienić wszystkie właściwości, Wyświetl listę to w szczegółowy opis.</span><span class="sxs-lookup"><span data-stu-id="80696-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="80696-134">Należy użyć składni konwencjonalne</span><span class="sxs-lookup"><span data-stu-id="80696-134">Use conventional syntax</span></span>
<span data-ttu-id="80696-135">Użyj standardowego formatu notacji Backusa-Naura, który jest wspólny dla Windows i pomoc w wierszu polecenia systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="80696-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="80696-136">Używanie typów programu Microsoft .NET Framework o wprowadzenie wartości parametrów</span><span class="sxs-lookup"><span data-stu-id="80696-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="80696-137">Symbole zastępcze wartości parametrów (w składnia i opisy parametrów) Pokaż typy obiektów, które akceptują parametr dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80696-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="80696-138">Zespół programu PowerShell opracowany niniejszej Konwencji, aby ułatwić pomagać innym użytkownikom dotyczące programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80696-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="80696-139">Zapis opisy parametrów ukończone</span><span class="sxs-lookup"><span data-stu-id="80696-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="80696-140">Opisy parametrów, należy poinformować użytkowników o dwie rzeczy: jakie parametru nie (jego działanie), a co wpisanie wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="80696-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="80696-141">Zapis praktyczne przykłady</span><span class="sxs-lookup"><span data-stu-id="80696-141">Write practical examples</span></span>
<span data-ttu-id="80696-142">W przykładach powinien pokazano, jak używać wszystkich parametrów, ale ważne jest pokazują, jak użyć polecenia cmdlet w rzeczywistych warunkach zadania.</span><span class="sxs-lookup"><span data-stu-id="80696-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="80696-143">Rozpocznij od prostego przykładu i zapisu przykłady coraz bardziej złożonych.</span><span class="sxs-lookup"><span data-stu-id="80696-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="80696-144">W ostatnim przykładzie pokazano, jak użyć polecenia cmdlet w potoku.</span><span class="sxs-lookup"><span data-stu-id="80696-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="80696-145">Użyj pola notatki</span><span class="sxs-lookup"><span data-stu-id="80696-145">Use the Notes field</span></span>
<span data-ttu-id="80696-146">Pole uwagi umożliwia opisano pojęcia, które użytkownicy muszą zrozumieć polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80696-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="80696-147">Informacje o umożliwia również pomóc użytkownikom w unikaniu typowych błędów.</span><span class="sxs-lookup"><span data-stu-id="80696-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="80696-148">Należy unikać adresy URL w miarę jak ulegają zmianom.</span><span class="sxs-lookup"><span data-stu-id="80696-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="80696-149">Zamiast tego Podaj użytkownikom terminy do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="80696-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="80696-150">Testowanie Twojej pomocy</span><span class="sxs-lookup"><span data-stu-id="80696-150">Test your Help</span></span>
<span data-ttu-id="80696-151">Przetestuj pomocy, tak samo, jak testować kod.</span><span class="sxs-lookup"><span data-stu-id="80696-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="80696-152">Mieć przyjaciół i współpracowników odczytywanie zawartości pomocy i opinii.</span><span class="sxs-lookup"><span data-stu-id="80696-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="80696-153">Można również poproś o opinię z grup dyskusyjnych.</span><span class="sxs-lookup"><span data-stu-id="80696-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="80696-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80696-154">See Also</span></span>

 [<span data-ttu-id="80696-155">Jak utworzyć plik pomocy dotyczącej poleceń Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="80696-156">Jak dodać nazwę polecenia Cmdlet i streszczenie do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-157">Jak dodać szczegółowy opis do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="80696-158">Jak dodać składnię do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-159">Jak dodać parametry do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="80696-160">Jak dodać typy danych wejściowych do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-161">Jak dodać wartości zwracane do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-162">Jak dodać uwagi tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-163">Jak dodawać przykłady do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-164">Jak dodać powiązane linki do tematu pomocy polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80696-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="80696-165">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="80696-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)