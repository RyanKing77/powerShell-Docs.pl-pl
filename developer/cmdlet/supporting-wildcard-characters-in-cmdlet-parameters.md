---
title: Obsługiwanie symboli wieloznacznych w parametrach poleceń cmdlet
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104443"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="68d55-102">Obsługiwanie symboli wieloznacznych w parametrach poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="68d55-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="68d55-103">Często należy zaprojektować polecenie cmdlet do uruchamiania względem grupy zasobów, a nie do pojedynczego zasobu.</span><span class="sxs-lookup"><span data-stu-id="68d55-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="68d55-104">Na przykład polecenie cmdlet może potrzebować znaleźć wszystkie pliki w magazynie danych, które mają taką samą nazwę lub rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="68d55-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="68d55-105">Należy zapewnić obsługę symboli wieloznacznych podczas projektowania polecenia cmdlet, które zostanie uruchomione względem grupy zasobów.</span><span class="sxs-lookup"><span data-stu-id="68d55-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="68d55-106">Używanie symboli wieloznacznych jest czasami określane jako *obsługi symboli wieloznacznych*.</span><span class="sxs-lookup"><span data-stu-id="68d55-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="68d55-107">Polecenia cmdlet programu Windows PowerShell, które używają symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="68d55-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="68d55-108">Wiele poleceń cmdlet programu Windows PowerShell obsługuje symbole wieloznaczne dla wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="68d55-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="68d55-109">Na przykład niemal każde polecenie cmdlet, które ma `Name` parametr `Path` lub obsługuje symbole wieloznaczne dla tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="68d55-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="68d55-110">(Chociaż większość poleceń cmdlet, które mają `Path` parametr ma również `LiteralPath` parametr, który nie obsługuje symboli wieloznacznych). Następujące polecenie pokazuje, w jaki sposób symbol wieloznaczny jest używany do zwracania wszystkich poleceń cmdlet w bieżącej sesji, których nazwa zawiera zlecenie get.</span><span class="sxs-lookup"><span data-stu-id="68d55-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="68d55-111">Obsługiwane symbole wieloznaczne</span><span class="sxs-lookup"><span data-stu-id="68d55-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="68d55-112">Program Windows PowerShell obsługuje następujące symbole wieloznaczne.</span><span class="sxs-lookup"><span data-stu-id="68d55-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="68d55-113">Znaku</span><span class="sxs-lookup"><span data-stu-id="68d55-113">Wildcard</span></span> |                             <span data-ttu-id="68d55-114">Opis</span><span class="sxs-lookup"><span data-stu-id="68d55-114">Description</span></span>                             |  <span data-ttu-id="68d55-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="68d55-115">Example</span></span>   |     <span data-ttu-id="68d55-116">Zgodne</span><span class="sxs-lookup"><span data-stu-id="68d55-116">Matches</span></span>      | <span data-ttu-id="68d55-117">Nie jest zgodny z</span><span class="sxs-lookup"><span data-stu-id="68d55-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="68d55-118">Dopasowuje zero lub więcej znaków, zaczynając od określonej pozycji</span><span class="sxs-lookup"><span data-stu-id="68d55-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="68d55-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="68d55-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="68d55-120">?</span><span class="sxs-lookup"><span data-stu-id="68d55-120">?</span></span>        | <span data-ttu-id="68d55-121">Dopasowuje dowolny znak na określonej pozycji</span><span class="sxs-lookup"><span data-stu-id="68d55-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="68d55-122">, W, na</span><span class="sxs-lookup"><span data-stu-id="68d55-122">An, in, on</span></span>       | <span data-ttu-id="68d55-123">został</span><span class="sxs-lookup"><span data-stu-id="68d55-123">ran</span></span>            |
| <span data-ttu-id="68d55-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="68d55-124">[ ]</span></span>      | <span data-ttu-id="68d55-125">Dopasowuje zakres znaków</span><span class="sxs-lookup"><span data-stu-id="68d55-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="68d55-126">książka, Cooka, wygląd</span><span class="sxs-lookup"><span data-stu-id="68d55-126">book, cook, look</span></span> | <span data-ttu-id="68d55-127">NOOK, trwało</span><span class="sxs-lookup"><span data-stu-id="68d55-127">nook, took</span></span>     |
| <span data-ttu-id="68d55-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="68d55-128">[ ]</span></span>      | <span data-ttu-id="68d55-129">Dopasowuje określone znaki</span><span class="sxs-lookup"><span data-stu-id="68d55-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="68d55-130">książka, NOOK</span><span class="sxs-lookup"><span data-stu-id="68d55-130">book, nook</span></span>       | <span data-ttu-id="68d55-131">Cooka, spójrz</span><span class="sxs-lookup"><span data-stu-id="68d55-131">cook, look</span></span>     |

<span data-ttu-id="68d55-132">Podczas projektowania poleceń cmdlet, które obsługują symbole wieloznaczne, Zezwalaj na kombinacje symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="68d55-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="68d55-133">Na przykład następujące polecenie używa `Get-ChildItem` polecenia cmdlet w celu pobrania wszystkich plików. txt, które znajdują się w folderze c:\Techdocs i zaczynają się od liter od "a" do "l".</span><span class="sxs-lookup"><span data-stu-id="68d55-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="68d55-134">Poprzednie polecenie korzysta z symbolu wieloznacznego `[a-l]` zakresu, aby określić, że nazwa pliku powinna zaczynać się od znaków od "a" do "l" i `*` używa znaku wieloznacznego jako symbolu zastępczego dla wszelkich znaków między pierwszą literą nazwy pliku i rozszerzenie **. txt** .</span><span class="sxs-lookup"><span data-stu-id="68d55-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="68d55-135">W poniższym przykładzie użyto wzorca wieloznacznego zakresu, który wyklucza literę "d", ale zawiera wszystkie inne litery od "a" do "f".</span><span class="sxs-lookup"><span data-stu-id="68d55-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="68d55-136">Obsługa znaków literału w wzorcach symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="68d55-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="68d55-137">Jeśli określony wzorzec wieloznaczny zawiera znaki literału, które nie powinny być interpretted jako symbole wieloznaczne, użyj znaku cudzysłowu (`` ` ``) jako znaku ucieczki.</span><span class="sxs-lookup"><span data-stu-id="68d55-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="68d55-138">W przypadku określenia znaków literału int w interfejsie API programu PowerShell należy użyć pojedynczego znacznika.</span><span class="sxs-lookup"><span data-stu-id="68d55-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="68d55-139">W przypadku określenia znaków literału w wierszu polecenia programu PowerShell należy użyć dwóch znaczników.</span><span class="sxs-lookup"><span data-stu-id="68d55-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="68d55-140">Na przykład poniższy wzorzec zawiera dwa nawiasy, które muszą być wykonane dosłownie.</span><span class="sxs-lookup"><span data-stu-id="68d55-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="68d55-141">W przypadku użycia w interfejsie API programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="68d55-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="68d55-142">"Jan Kowalski \`[\*"] "</span><span class="sxs-lookup"><span data-stu-id="68d55-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="68d55-143">Gdy jest używany z wiersza polecenia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="68d55-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="68d55-144">"Jan Kowalski \` \`[\*\`"] "</span><span class="sxs-lookup"><span data-stu-id="68d55-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="68d55-145">Ten wzorzec pasuje do "Jan Kowalski [Marketing]" lub "Jan Kowalski [programowanie]".</span><span class="sxs-lookup"><span data-stu-id="68d55-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="68d55-146">Przykład:</span><span class="sxs-lookup"><span data-stu-id="68d55-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="68d55-147">Znaki danych wyjściowych polecenia cmdlet i symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="68d55-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="68d55-148">Gdy parametry poleceń cmdlet obsługują symbole wieloznaczne, operacja zwykle generuje tablicę wyjściową.</span><span class="sxs-lookup"><span data-stu-id="68d55-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="68d55-149">Czasami nie ma sensu, aby obsługiwał tablicę wyjściową, ponieważ użytkownik może użyć tylko jednego elementu.</span><span class="sxs-lookup"><span data-stu-id="68d55-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="68d55-150">Na przykład `Set-Location` polecenie cmdlet nie obsługuje danych wyjściowych tablicy, ponieważ użytkownik ustawia tylko jedną lokalizację.</span><span class="sxs-lookup"><span data-stu-id="68d55-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="68d55-151">W tym wystąpieniu polecenie cmdlet nadal obsługuje symbole wieloznaczne, ale wymusza rozpoznawanie do pojedynczej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="68d55-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="68d55-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68d55-152">See Also</span></span>

[<span data-ttu-id="68d55-153">Pisanie polecenia cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="68d55-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="68d55-154">Klasa WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="68d55-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
