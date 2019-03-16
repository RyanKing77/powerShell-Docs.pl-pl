---
title: Obsługa symboli wieloznacznych w parametry polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059613"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="8e1be-102">Obsługiwanie symboli wieloznacznych w parametrach poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="8e1be-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="8e1be-103">Często należy zaprojektować polecenia cmdlet do uruchamiania w odniesieniu do grupy zasobów, a nie względem pojedynczy zasób.</span><span class="sxs-lookup"><span data-stu-id="8e1be-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="8e1be-104">Na przykład polecenia cmdlet konieczne zlokalizować wszystkich plików w magazynie danych o takiej samej nazwie lub rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8e1be-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="8e1be-105">Podczas projektowania polecenia cmdlet, które będą uruchamiane w odniesieniu do grupy zasobów, musisz podać pomocy technicznej dla symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="8e1be-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="8e1be-106">Przy użyciu symboli wieloznacznych jest czasami określane jako *symboli wieloznacznych*.</span><span class="sxs-lookup"><span data-stu-id="8e1be-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="8e1be-107">Polecenia cmdlet programu PowerShell Windows, który używać symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="8e1be-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="8e1be-108">Wiele poleceń cmdlet programu Windows PowerShell obsługuje znaki symboli wieloznacznych dla ich wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="8e1be-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="8e1be-109">Na przykład niemal każdego polecenia cmdlet, ma `Name` lub `Path` parametr obsługuje znaki symboli wieloznacznych dla tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8e1be-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="8e1be-110">(Mimo że większość poleceń cmdlet, które mają `Path` parametr również mieć `LiteralPath` parametr, który nie obsługuje symboli wieloznacznych.) Następujące polecenie pokazuje, jak symbolem wieloznacznym jest używana do zwracania wszystkich poleceń cmdlet w bieżącej sesji, którego nazwa zawiera zlecenia Get.</span><span class="sxs-lookup"><span data-stu-id="8e1be-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="8e1be-111">**PS > get polecenia get -\***</span><span class="sxs-lookup"><span data-stu-id="8e1be-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="8e1be-112">Obsługiwane symbole wieloznaczne</span><span class="sxs-lookup"><span data-stu-id="8e1be-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="8e1be-113">Program Windows PowerShell obsługuje następujące znaki symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="8e1be-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="8e1be-114">wieloznaczny</span><span class="sxs-lookup"><span data-stu-id="8e1be-114">Wildcard character</span></span>|<span data-ttu-id="8e1be-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8e1be-115">Description</span></span>|<span data-ttu-id="8e1be-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e1be-116">Example</span></span>|<span data-ttu-id="8e1be-117">Zgodne</span><span class="sxs-lookup"><span data-stu-id="8e1be-117">Matches</span></span>|<span data-ttu-id="8e1be-118">Nie jest zgodny z</span><span class="sxs-lookup"><span data-stu-id="8e1be-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="8e1be-119">Dopasowuje zero lub więcej znaków, zaczynając od określonej pozycji</span><span class="sxs-lookup"><span data-stu-id="8e1be-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="8e1be-120">a\*</span><span class="sxs-lookup"><span data-stu-id="8e1be-120">a\*</span></span>|<span data-ttu-id="8e1be-121">, Ag firmy Apple</span><span class="sxs-lookup"><span data-stu-id="8e1be-121">A, ag, Apple</span></span>||
|<span data-ttu-id="8e1be-122">?</span><span class="sxs-lookup"><span data-stu-id="8e1be-122">?</span></span>|<span data-ttu-id="8e1be-123">Anycharacter dopasowań w określonym położeniu</span><span class="sxs-lookup"><span data-stu-id="8e1be-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="8e1be-124">?n</span><span class="sxs-lookup"><span data-stu-id="8e1be-124">?n</span></span>|<span data-ttu-id="8e1be-125">W polu, na</span><span class="sxs-lookup"><span data-stu-id="8e1be-125">An, in, on</span></span>|<span data-ttu-id="8e1be-126">uruchomiono</span><span class="sxs-lookup"><span data-stu-id="8e1be-126">ran</span></span>|
|<span data-ttu-id="8e1be-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="8e1be-127">[ ]</span></span>|<span data-ttu-id="8e1be-128">Dopasowuje szeroką gamę znaków</span><span class="sxs-lookup"><span data-stu-id="8e1be-128">Matches a range of characters</span></span>|<span data-ttu-id="8e1be-129">ook [a-l]</span><span class="sxs-lookup"><span data-stu-id="8e1be-129">[a-l]ook</span></span>|<span data-ttu-id="8e1be-130">książki, Cooka, wygląd</span><span class="sxs-lookup"><span data-stu-id="8e1be-130">book, cook, look</span></span>|<span data-ttu-id="8e1be-131">trwała</span><span class="sxs-lookup"><span data-stu-id="8e1be-131">took</span></span>|
|<span data-ttu-id="8e1be-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="8e1be-132">[ ]</span></span>|<span data-ttu-id="8e1be-133">Pasuje do określonych znaków</span><span class="sxs-lookup"><span data-stu-id="8e1be-133">Matches the specified characters</span></span>|<span data-ttu-id="8e1be-134">ook [bc]</span><span class="sxs-lookup"><span data-stu-id="8e1be-134">[bc]ook</span></span>|<span data-ttu-id="8e1be-135">książki, Cooka</span><span class="sxs-lookup"><span data-stu-id="8e1be-135">book, cook</span></span>|<span data-ttu-id="8e1be-136">wygląd</span><span class="sxs-lookup"><span data-stu-id="8e1be-136">look</span></span>|

<span data-ttu-id="8e1be-137">Podczas projektowania poleceń cmdlet, który obsługuje znaki symboli wieloznacznych, umożliwiają kombinacji symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="8e1be-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="8e1be-138">Na przykład następujące polecenie używa `Get-ChildItem` polecenie cmdlet do pobierania wszystkich plików txt znajdujących się w folderze c:\Techdocs i zaczynające się od liter "" do "l."</span><span class="sxs-lookup"><span data-stu-id="8e1be-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="8e1be-139">**polecenie GET-childitem c:\techdocs\\[a-l]\*txt**</span><span class="sxs-lookup"><span data-stu-id="8e1be-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="8e1be-140">Poprzednie polecenie korzysta z symbolami wieloznacznymi zakresu **[a-l]** do określenia, czy nazwa pliku ma się zacząć od znaków "" do "l."</span><span class="sxs-lookup"><span data-stu-id="8e1be-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="8e1be-141">Następnie używa polecenia \* wieloznacznego jako symbolu zastępczego dla żadnych znaków między pierwszą literę nazwy pliku i rozszerzenie txt.</span><span class="sxs-lookup"><span data-stu-id="8e1be-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="8e1be-142">W poniższym przykładzie użyto wzór symboli wieloznacznych zakres, który wyklucza literę "d", ale obejmuje wszystkie inne litery od "a" do "f."</span><span class="sxs-lookup"><span data-stu-id="8e1be-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="8e1be-143">**polecenie GET-childitem c:\techdocs\\[a cef]\*txt**</span><span class="sxs-lookup"><span data-stu-id="8e1be-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="8e1be-144">Obsługa znaków literałowych w wzorców symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="8e1be-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="8e1be-145">Jeśli wzór symboli wieloznacznych, które określisz zawiera znaki literału, należy użyć znaku początkowych ('), jako znak ucieczki.</span><span class="sxs-lookup"><span data-stu-id="8e1be-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="8e1be-146">Po określeniu programowo znaków literałowych, należy użyć pojedynczej początkowych.</span><span class="sxs-lookup"><span data-stu-id="8e1be-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="8e1be-147">Po określeniu znaków literałowych w wierszu polecenia, użyj dwa znaki grawisu.</span><span class="sxs-lookup"><span data-stu-id="8e1be-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="8e1be-148">Na przykład następujący wzorzec zawiera dwa nawiasy kwadratowe, które należy podjąć, dosłownie.</span><span class="sxs-lookup"><span data-stu-id="8e1be-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="8e1be-149">"Jan Kowalski \`[\*"] "(określony programowe)</span><span class="sxs-lookup"><span data-stu-id="8e1be-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="8e1be-150">"Jan Kowalski \` \`[\*\`"] "(określony w wierszu polecenia)</span><span class="sxs-lookup"><span data-stu-id="8e1be-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="8e1be-151">Ten wzorzec pasuje do "Jan Kowalski [Marketing]" lub "Jan Kowalski [programowanie]".</span><span class="sxs-lookup"><span data-stu-id="8e1be-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="8e1be-152">Dane wyjściowe polecenia cmdlet i symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="8e1be-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="8e1be-153">Parametry polecenia cmdlet obsługuje znaki symboli wieloznacznych, działanie polecenia cmdlet zwykle generuje dane wyjściowe tablicy.</span><span class="sxs-lookup"><span data-stu-id="8e1be-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="8e1be-154">Od czasu do czasu nie ma sensu obsługi tablicy danych wyjściowych, ponieważ użytkownik może użyć tylko pojedynczego elementu w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="8e1be-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="8e1be-155">Na przykład `Set-Location` polecenie cmdlet obsługuje tablicy danych wyjściowych, ponieważ użytkownik ustawia jednej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="8e1be-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="8e1be-156">W tym wypadku polecenia cmdlet nadal obsługuje znaki symboli wieloznacznych, ale wymusza rozdzielczości w jednym miejscu.</span><span class="sxs-lookup"><span data-stu-id="8e1be-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e1be-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e1be-157">See Also</span></span>

[<span data-ttu-id="8e1be-158">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e1be-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="8e1be-159">Klasa WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="8e1be-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
