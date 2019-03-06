---
title: Opis kodowania pliku w programie VSCode i PowerShell
description: Skonfiguruj kodowanie pliku VSCode i programu PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429809"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="67cb2-103">Opis kodowania pliku w programie VSCode i PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cb2-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="67cb2-104">Używając programu VS Code do tworzenia i edytowania skryptów programu PowerShell, jest ważne, czy pliki są zapisywane w formacie kodowania znaków jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="67cb2-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="67cb2-105">Co to jest kodowanie pliku i dlaczego jest ważna?</span><span class="sxs-lookup"><span data-stu-id="67cb2-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="67cb2-106">VSCode zarządza interfejs między ludzi, wprowadzanie ciągów znaków w buforze i bloków odczytu/zapisu bajtów w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="67cb2-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="67cb2-107">Gdy plik jest zapisywany VSCode, używa kodowania w tym celu tekstu.</span><span class="sxs-lookup"><span data-stu-id="67cb2-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="67cb2-108">Podobnie uruchomienie skryptu programu PowerShell ją przekonwertować bajtów w pliku znaków, aby odtworzyć go do programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67cb2-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="67cb2-109">Ponieważ VSCode zapisuje plik i programu PowerShell odczytuje plik, muszą używać tego samego systemu kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="67cb2-110">Prowadzi to proces analizowania skrypt programu PowerShell: *bajtów* -> *znaków* -> *tokenów*  ->   *drzewo abstrakcyjnej składni* -> *wykonywania*.</span><span class="sxs-lookup"><span data-stu-id="67cb2-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="67cb2-111">Zarówno VSCode, jak i programu PowerShell są instalowane z rozsądne domyślną konfigurację kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="67cb2-112">Jednak domyślne kodowanie używane przez program PowerShell został zmieniony wraz z wydaniem programu PowerShell Core (6.x).</span><span class="sxs-lookup"><span data-stu-id="67cb2-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="67cb2-113">Aby upewnić się, nie problemów przy użyciu programu PowerShell lub rozszerzenia programu PowerShell w VSCode, należy skonfigurować ustawienia programu VSCode i programu PowerShell prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="67cb2-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="67cb2-114">Typowe przyczyny problemów z kodowaniem</span><span class="sxs-lookup"><span data-stu-id="67cb2-114">Common causes of encoding issues</span></span>

<span data-ttu-id="67cb2-115">Kodowania problemy występują, gdy kodowanie VSCode lub pliku skryptu nie są zgodne oczekiwane kodowanie programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67cb2-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="67cb2-116">Nie ma możliwości dla programu PowerShell, aby automatycznie określić kodowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="67cb2-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="67cb2-117">Wszystko jest bardziej prawdopodobne kodowanie problemy podczas korzystania z znaków nie [7-bitowego zestawu znaków ASCII](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="67cb2-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="67cb2-118">Przykład:</span><span class="sxs-lookup"><span data-stu-id="67cb2-118">For example:</span></span>

- <span data-ttu-id="67cb2-119">Akcentowanie znaków łaciński (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="67cb2-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="67cb2-120">Znaki inne niż łacińskie, takich jak cyrylica (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="67cb2-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="67cb2-121">Chiński Hanowi (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="67cb2-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="67cb2-122">Typowe przyczyny problemów z kodowaniem są:</span><span class="sxs-lookup"><span data-stu-id="67cb2-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="67cb2-123">Kodowanie VSCode i programu PowerShell nie została zmieniona z ustawień domyślnych.</span><span class="sxs-lookup"><span data-stu-id="67cb2-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="67cb2-124">Programu PowerShell 5.1 i poniżej domyślne kodowanie różni się od VSCode firmy.</span><span class="sxs-lookup"><span data-stu-id="67cb2-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="67cb2-125">Inny edytor otworzył i zastąpić plik przy użyciu nowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="67cb2-126">To często zdarza się przy użyciu środowiska ISE.</span><span class="sxs-lookup"><span data-stu-id="67cb2-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="67cb2-127">Plik jest sprawdzany do kontroli źródła przy użyciu kodowania, która różni się od jakich VSCode lub programu PowerShell oczekuje.</span><span class="sxs-lookup"><span data-stu-id="67cb2-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="67cb2-128">Może to nastąpić, korzystając z współpracowników edytorów z różnymi konfiguracjami kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="67cb2-129">Jak sprawdzić, jeśli masz problemy z kodowaniem</span><span class="sxs-lookup"><span data-stu-id="67cb2-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="67cb2-130">Błędy kodowania często są one widoczne jako analizy błędów w skryptach.</span><span class="sxs-lookup"><span data-stu-id="67cb2-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="67cb2-131">Jeśli okaże się sekwencje znaków dziwne w skrypcie, może to być problem.</span><span class="sxs-lookup"><span data-stu-id="67cb2-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="67cb2-132">W przykładzie poniżej półpauzę (`–`) jest wyświetlana jako znaki `â€“`:</span><span class="sxs-lookup"><span data-stu-id="67cb2-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="67cb2-133">Ten problem występuje, ponieważ VSCode koduje znak `–` w formacie UTF-8, jako bajtów `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="67cb2-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="67cb2-134">Kiedy bajty te są zdekodowany jako Windows-1252, są interpretowane jako znaki `â€“`.</span><span class="sxs-lookup"><span data-stu-id="67cb2-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="67cb2-135">Niektóre sekwencje znaków dziwne, które można napotkać obejmują:</span><span class="sxs-lookup"><span data-stu-id="67cb2-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="67cb2-136">`â€“` Zamiast `–`</span><span class="sxs-lookup"><span data-stu-id="67cb2-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="67cb2-137">`â€”` Zamiast `—`</span><span class="sxs-lookup"><span data-stu-id="67cb2-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="67cb2-138">`Ã„2` Zamiast `Ä`</span><span class="sxs-lookup"><span data-stu-id="67cb2-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="67cb2-139">`Â` zamiast ` ` (spacja nierozdzielająca)</span><span class="sxs-lookup"><span data-stu-id="67cb2-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="67cb2-140">`Ã©` Zamiast `é`</span><span class="sxs-lookup"><span data-stu-id="67cb2-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="67cb2-141">Przydatne w tym [odwołania](https://www.i18nqa.com/debug/utf8-debug.html) zawiera listę typowych wzorców, które wskazują na problem kodowania UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="67cb2-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="67cb2-142">Jak działa rozszerzenie PowerShell VSCode współdziała z kodowania</span><span class="sxs-lookup"><span data-stu-id="67cb2-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="67cb2-143">Rozszerzenie PowerShell wchodzi w interakcję z skrypty na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="67cb2-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="67cb2-144">Podczas edytowania skryptów w VSCode, zawartość są wysyłane przez VSCode do rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="67cb2-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="67cb2-145">[Language Server Protocol][] określającemu, że ta zawartość jest przesyłany w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="67cb2-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="67cb2-146">W związku z tym nie jest możliwe dla rozszerzenia Aby pobrać błędne szyfrowanie.</span><span class="sxs-lookup"><span data-stu-id="67cb2-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="67cb2-147">Gdy skryptów są wykonywane bezpośrednio w konsoli programu zintegrowanego, są odczytywane z pliku programu PowerShell, bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="67cb2-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="67cb2-148">Jeśli kodowanie programu PowerShell różni się od firmy VSCode, coś tutaj można wprowadzić problem.</span><span class="sxs-lookup"><span data-stu-id="67cb2-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="67cb2-149">Gdy skrypt, który jest otwarty w VSCode odwołuje się do innego skryptu, który nie jest otwarty w VSCode, rozszerzenie przechodzi do ładowania zawartości tego skryptu z systemu plików.</span><span class="sxs-lookup"><span data-stu-id="67cb2-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="67cb2-150">Rozszerzenie programu PowerShell, wartością domyślną jest kodowanie UTF-8, ale używa [znacznika kolejności bajtów][], lub znak BOM, wykrywania, aby wybrać poprawne kodowanie.</span><span class="sxs-lookup"><span data-stu-id="67cb2-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="67cb2-151">Ten problem występuje, gdy przy założeniu kodowanie formatów bez znaku BOM (takich jak [UTF-8][] z znak BOM nie i [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="67cb2-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="67cb2-152">Rozszerzenie PowerShell wartość domyślna to UTF-8.</span><span class="sxs-lookup"><span data-stu-id="67cb2-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="67cb2-153">Rozszerzenie nie można zmienić ustawienia kodowania VSCode firmy.</span><span class="sxs-lookup"><span data-stu-id="67cb2-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="67cb2-154">Aby uzyskać więcej informacji, zobacz [wystawiać #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="67cb2-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="67cb2-155">Wybierając odpowiednie kodowania</span><span class="sxs-lookup"><span data-stu-id="67cb2-155">Choosing the right encoding</span></span>

<span data-ttu-id="67cb2-156">Różne systemy i aplikacje mogą używać różnych kodowań:</span><span class="sxs-lookup"><span data-stu-id="67cb2-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="67cb2-157">W programie .NET Standard w Internecie lub w środowisku systemu Linux, UTF-8 jest teraz kodowanie dominującego.</span><span class="sxs-lookup"><span data-stu-id="67cb2-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="67cb2-158">Używana w wielu aplikacjach .NET Framework [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="67cb2-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="67cb2-159">Historyczne ze względu na jest to czasami nazywane "Unicode", która teraz termin odnosi się do szerokiego [standardowa](https://en.wikipedia.org/wiki/Unicode) zawierającej UTF-16 i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="67cb2-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="67cb2-160">W Windows wiele aplikacji natywnych, które powstały wcześniej niż Unicode nadal używać Windows-1252 domyślnie.</span><span class="sxs-lookup"><span data-stu-id="67cb2-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="67cb2-161">Kodowania Unicode mają również koncepcji kolejności bajtów (BOM) znaku.</span><span class="sxs-lookup"><span data-stu-id="67cb2-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="67cb2-162">BOM występować na początku tekstu mówić dekoder, kodowania, która używa tekstu.</span><span class="sxs-lookup"><span data-stu-id="67cb2-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="67cb2-163">Dla wielobajtowego kodowania, wskazuje także BOM [kolejność bajtów](https://en.wikipedia.org/wiki/Endianness) kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="67cb2-164">BOM mają być bajtów, które rzadko występują w tekstu innego niż Unicode, dzięki czemu uzasadnione przypuszczenie, że tekst jest Unicode, jeśli występuje znak BOM.</span><span class="sxs-lookup"><span data-stu-id="67cb2-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="67cb2-165">BOM są opcjonalne i ich wdrażania nie jest tak popularne w środowisku systemu Linux, ponieważ niezawodną Konwencji UTF-8 są używane wszędzie.</span><span class="sxs-lookup"><span data-stu-id="67cb2-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="67cb2-166">Większość aplikacji systemu Linux zakładają, że wprowadzanie tekstu jest zakodowany w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="67cb2-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="67cb2-167">Gdy wiele aplikacji systemu Linux rozpozna i zapewnia prawidłowej obsługi znak BOM, liczbą nie, co prowadzi do artefaktów w tekście modyfikować za pomocą tych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="67cb2-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="67cb2-168">**W związku z tym**:</span><span class="sxs-lookup"><span data-stu-id="67cb2-168">**Therefore**:</span></span>

- <span data-ttu-id="67cb2-169">Pracujesz przede wszystkim z aplikacji Windows i programu Windows PowerShell, należy najpierw kodowania, takich jak UTF-8 z BOM lub UTF-16.</span><span class="sxs-lookup"><span data-stu-id="67cb2-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="67cb2-170">Jeśli pracujesz na platformach preferowaną UTF-8 z BOM.</span><span class="sxs-lookup"><span data-stu-id="67cb2-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="67cb2-171">Jeśli użytkownik pracuje się głównie w kontekstach skojarzone z systemem Linux, preferowaną UTF-8 bez BOM.</span><span class="sxs-lookup"><span data-stu-id="67cb2-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="67cb2-172">Windows-1252 i latin-1 są zasadniczo starszych kodowania, które należy unikać, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="67cb2-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="67cb2-173">Jednak niektóre starsze aplikacje Windows może zależą od nich.</span><span class="sxs-lookup"><span data-stu-id="67cb2-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="67cb2-174">Warto również zauważyć, że skrypt podpisywania [kodowanie zależne od](https://github.com/PowerShell/PowerShell/issues/3466), co oznacza zmianę kodowania na podpisanych skryptów będzie wymagać ponownego podpisywania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="67cb2-175">Konfigurowanie programu VSCode</span><span class="sxs-lookup"><span data-stu-id="67cb2-175">Configuring VSCode</span></span>

<span data-ttu-id="67cb2-176">Dla programu VSCode domyślnym kodowaniem jest UTF-8 bez BOM.</span><span class="sxs-lookup"><span data-stu-id="67cb2-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="67cb2-177">Aby ustawić [Kodowanie dla programu VSCode][], przejdź do ustawień programu VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) i ustaw `"files.encoding"` ustawienia:</span><span class="sxs-lookup"><span data-stu-id="67cb2-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="67cb2-178">Niektóre możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="67cb2-178">Some possible values are:</span></span>

- <span data-ttu-id="67cb2-179">`utf8`: [UTF-8] bez BOM</span><span class="sxs-lookup"><span data-stu-id="67cb2-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="67cb2-180">`utf8bom`: [UTF-8] z BOM</span><span class="sxs-lookup"><span data-stu-id="67cb2-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="67cb2-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="67cb2-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="67cb2-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="67cb2-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="67cb2-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="67cb2-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="67cb2-184">Należy uzyskać listę rozwijaną dla tego w widoku graficznego interfejsu użytkownika lub wyświetlić uzupełnienia go w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="67cb2-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="67cb2-185">Na automatyczne wykrywanie kodowania, gdy jest to możliwe, można również dodać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="67cb2-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="67cb2-186">Jeśli nie chcesz, aby te ustawienia mają wpływ na wszystkie typy plików, programu VSCode umożliwia także konfiguracje między językami.</span><span class="sxs-lookup"><span data-stu-id="67cb2-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="67cb2-187">Utwórz ustawienie specyficzne dla języka, umieszczając ustawienia `[<language-name>]` pola.</span><span class="sxs-lookup"><span data-stu-id="67cb2-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="67cb2-188">Przykład:</span><span class="sxs-lookup"><span data-stu-id="67cb2-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="67cb2-189">Konfigurowanie programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cb2-189">Configuring PowerShell</span></span>

<span data-ttu-id="67cb2-190">W programie PowerShell domyślne kodowanie różni się zależnie od wersji:</span><span class="sxs-lookup"><span data-stu-id="67cb2-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="67cb2-191">W programie PowerShell 6 + kodowanie domyślne to UTF-8 bez BOM na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="67cb2-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="67cb2-192">W programie Windows PowerShell, domyślnym kodowaniem jest zwykle Windows-1252, rozszerzenie [latin 1][], znanego również jako ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="67cb2-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="67cb2-193">W programie PowerShell 5 + można znaleźć domyślnego kodowania w tym:</span><span class="sxs-lookup"><span data-stu-id="67cb2-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="67cb2-194">Następujące [skryptu](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) może służyć do określenia wnioskuje co kodowanie sesji programu PowerShell dla skryptu bez BOM.</span><span class="sxs-lookup"><span data-stu-id="67cb2-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="67cb2-195">Istnieje możliwość konfigurowania programu PowerShell do korzystania z kodowaniem danego ogólnie za pomocą ustawień profilu.</span><span class="sxs-lookup"><span data-stu-id="67cb2-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="67cb2-196">Zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="67cb2-196">See the following articles:</span></span>

- <span data-ttu-id="67cb2-197">[@mklement0]firmy [odpowiedziami dotyczącymi programu PowerShell kodowania na stronie StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="67cb2-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="67cb2-198">[@rkeithhill]firmy [wpis w blogu o obsłudze wprowadzania bez BOM UTF-8 w programie PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="67cb2-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="67cb2-199">Nie jest możliwe wymusić programu PowerShell do korzystania z określonego kodowania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="67cb2-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="67cb2-200">Program PowerShell 5.1 i poniżej domyślnie Windows-1252, kodowanie, gdy znak BOM nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="67cb2-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="67cb2-201">Ze względu na współdziałanie najlepiej jest zapisać skrypty w formacie Unicode, za pomocą znak BOM.</span><span class="sxs-lookup"><span data-stu-id="67cb2-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67cb2-202">Jakichkolwiek innych narzędzi, masz tego touch programu PowerShell, skryptów mogą mieć wpływ na wybór kodowania lub ponownie zakodować skrypty do innego kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="67cb2-203">Istniejące skrypty</span><span class="sxs-lookup"><span data-stu-id="67cb2-203">Existing scripts</span></span>

<span data-ttu-id="67cb2-204">Skrypty już w systemie plików może być konieczne do zakodowania ponownie wybrany nowy kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="67cb2-205">W dolnym pasku VSCode będzie wyświetlana etykieta UTF-8.</span><span class="sxs-lookup"><span data-stu-id="67cb2-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="67cb2-206">Kliknij go, aby otworzyć pasek akcji, a następnie wybierz pozycję **Zapisz z kodowaniem**.</span><span class="sxs-lookup"><span data-stu-id="67cb2-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="67cb2-207">Teraz możesz wybrać nowe kodowanie dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="67cb2-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="67cb2-208">Zobacz [Kodowanie dla programu VSCode][] pełne instrukcje.</span><span class="sxs-lookup"><span data-stu-id="67cb2-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="67cb2-209">Jeśli potrzebujesz ponownie zakodować wiele plików, można użyć następującego skryptu:</span><span class="sxs-lookup"><span data-stu-id="67cb2-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="67cb2-210">PowerShell Integrated Scripting środowiska (ISE)</span><span class="sxs-lookup"><span data-stu-id="67cb2-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="67cb2-211">Możesz również edytować skrypty przy użyciu programu PowerShell ISE, należy zsynchronizować swoje ustawienia kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="67cb2-212">Środowiska ISE należy uwzględnić znak BOM, ale jest również możliwe użycie odbicia do [Ustawianie kodowania](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="67cb2-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="67cb2-213">Należy pamiętać o tym, czy nie byłoby to utrwalone między startupy.</span><span class="sxs-lookup"><span data-stu-id="67cb2-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="67cb2-214">Oprogramowanie do kontroli źródła</span><span class="sxs-lookup"><span data-stu-id="67cb2-214">Source control software</span></span>

<span data-ttu-id="67cb2-215">Niektóre narzędzia do kontroli źródła, takich jak git, ignorowanie kodowania; System git śledzi tylko bajtów.</span><span class="sxs-lookup"><span data-stu-id="67cb2-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="67cb2-216">Inne, takie jak TFS lub Mercurial, nie.</span><span class="sxs-lookup"><span data-stu-id="67cb2-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="67cb2-217">Nawet z niektórych narzędzi opartych o git zależy od tego, dekodowanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="67cb2-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="67cb2-218">Gdy jest to możliwe, upewnij się, że:</span><span class="sxs-lookup"><span data-stu-id="67cb2-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="67cb2-219">Skonfiguruj kodowanie w kontroli źródła aby dopasować go do konfiguracji programu VSCode tekstu.</span><span class="sxs-lookup"><span data-stu-id="67cb2-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="67cb2-220">Upewnij się, że wszystkie pliki są zaewidencjonowane do kontroli źródła przy użyciu odpowiednich kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="67cb2-221">Uważaj, zmian kodowanie otrzymane za pomocą kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="67cb2-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="67cb2-222">Klucza znak ten jest różnic wskazujący zmiany, ale gdy nic nie wydaje się, że zostały zmienione (ponieważ masz bajtów, ale znaki nie).</span><span class="sxs-lookup"><span data-stu-id="67cb2-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="67cb2-223">Współpracowników i środowiska</span><span class="sxs-lookup"><span data-stu-id="67cb2-223">Collaborators' environments</span></span>

<span data-ttu-id="67cb2-224">Na podstawie Konfigurowanie kontroli źródła, upewnij się, że współpracownicy w taki sposób, na wszystkie pliki, które możesz udostępniać nie ustawień, które zastępują kodowania przez ponowne kodowanie plików, programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67cb2-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="67cb2-225">Inne programy</span><span class="sxs-lookup"><span data-stu-id="67cb2-225">Other programs</span></span>

<span data-ttu-id="67cb2-226">Inny program, który odczytuje lub zapisuje skrypt programu PowerShell ponownie zakodować go.</span><span class="sxs-lookup"><span data-stu-id="67cb2-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="67cb2-227">Niektóre przykłady to:</span><span class="sxs-lookup"><span data-stu-id="67cb2-227">Some examples are:</span></span>

- <span data-ttu-id="67cb2-228">Korzystanie ze Schowka do kopiowania i wklejania skryptu.</span><span class="sxs-lookup"><span data-stu-id="67cb2-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="67cb2-229">To jest typowe w przypadku takich scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="67cb2-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="67cb2-230">Kopiowanie skrypt do maszyny Wirtualnej</span><span class="sxs-lookup"><span data-stu-id="67cb2-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="67cb2-231">Kopiowanie skryptu z wiadomości e-mail lub strony sieci Web</span><span class="sxs-lookup"><span data-stu-id="67cb2-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="67cb2-232">Kopiowanie skrypt do lub z dokumentu Microsoft Word lub PowerPoint</span><span class="sxs-lookup"><span data-stu-id="67cb2-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="67cb2-233">Inne edytory tekstu, takie jak:</span><span class="sxs-lookup"><span data-stu-id="67cb2-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="67cb2-234">Notepad</span><span class="sxs-lookup"><span data-stu-id="67cb2-234">Notepad</span></span>
  - <span data-ttu-id="67cb2-235">vim</span><span class="sxs-lookup"><span data-stu-id="67cb2-235">vim</span></span>
  - <span data-ttu-id="67cb2-236">Inne Edytor skryptów programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cb2-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="67cb2-237">Edycji tekstu, narzędzia, takie jak:</span><span class="sxs-lookup"><span data-stu-id="67cb2-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="67cb2-238">Operatorów przekierowania programu PowerShell, takie jak `>` i `>>`</span><span class="sxs-lookup"><span data-stu-id="67cb2-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="67cb2-239">Plik transferu programów, takich jak:</span><span class="sxs-lookup"><span data-stu-id="67cb2-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="67cb2-240">Przeglądarka sieci web, podczas pobierania skryptów</span><span class="sxs-lookup"><span data-stu-id="67cb2-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="67cb2-241">Udział plików</span><span class="sxs-lookup"><span data-stu-id="67cb2-241">A file share</span></span>

<span data-ttu-id="67cb2-242">Niektóre z tych narzędzi postępowania w bajtach, a nie na tekst, ale oferują inne konfiguracje kodowania.</span><span class="sxs-lookup"><span data-stu-id="67cb2-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="67cb2-243">W przypadkach, gdzie należy skonfigurować, kodowania musisz wprowadzić takie same jak edytor kodowania, aby uniknąć problemów.</span><span class="sxs-lookup"><span data-stu-id="67cb2-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="67cb2-244">Inne zasoby, kodując go w programie PowerShell</span><span class="sxs-lookup"><span data-stu-id="67cb2-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="67cb2-245">Istnieje kilka innych nieuprzywilejowany wpisy na kodowanie i konfigurowanie kodowania w programie PowerShell, które są warte odczytu:</span><span class="sxs-lookup"><span data-stu-id="67cb2-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="67cb2-246">[@mklement0]firmy [podsumowania PowerShell kodowania na stronie StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="67cb2-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="67cb2-247">Wcześniejsze numery otwarta w programie PowerShell vscode kodowania problemy:</span><span class="sxs-lookup"><span data-stu-id="67cb2-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="67cb2-248">#1308</span><span class="sxs-lookup"><span data-stu-id="67cb2-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="67cb2-249">#1628</span><span class="sxs-lookup"><span data-stu-id="67cb2-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="67cb2-250">#1680</span><span class="sxs-lookup"><span data-stu-id="67cb2-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="67cb2-251">#1744</span><span class="sxs-lookup"><span data-stu-id="67cb2-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="67cb2-252">#1751</span><span class="sxs-lookup"><span data-stu-id="67cb2-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="67cb2-253">Klasycznym *Joel oprogramowania* Opisz Unicode</span><span class="sxs-lookup"><span data-stu-id="67cb2-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="67cb2-254">Kodowanie w .NET Standard</span><span class="sxs-lookup"><span data-stu-id="67cb2-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[znacznika kolejności bajtów]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Kodowanie dla programu VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
