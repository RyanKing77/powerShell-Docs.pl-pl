---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Nowe i zaktualizowane polecenia cmdlet
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856245"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="b192a-103">Nowe i zaktualizowane polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="b192a-103">New and updated cmdlets</span></span>

<span data-ttu-id="b192a-104">Dodaliśmy nowe i zaktualizowane istniejące polecenia cmdlet na podstawie opinii społeczności.</span><span class="sxs-lookup"><span data-stu-id="b192a-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="b192a-105">Polecenia cmdlet archiwum</span><span class="sxs-lookup"><span data-stu-id="b192a-105">Archive cmdlets</span></span>

<span data-ttu-id="b192a-106">Dwa nowe polecenia cmdlet `Compress-Archive` i `Expand-Archive`systemowi Kompresuj i rozwiń plików ZIP.</span><span class="sxs-lookup"><span data-stu-id="b192a-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="b192a-107">Aby uzyskać więcej informacji, zobacz [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) dokumentacji modułu.</span><span class="sxs-lookup"><span data-stu-id="b192a-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="b192a-108">Polecenia cmdlet wykazu</span><span class="sxs-lookup"><span data-stu-id="b192a-108">Catalog Cmdlets</span></span>

<span data-ttu-id="b192a-109">Dodano dwa nowe polecenia cmdlet w Microsoft.PowerShell.Security module.</span><span class="sxs-lookup"><span data-stu-id="b192a-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="b192a-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b192a-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="b192a-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b192a-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="b192a-112">Te Generowanie i zweryfikować pliki w katalogu Windows.</span><span class="sxs-lookup"><span data-stu-id="b192a-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="b192a-113">Polecenia cmdlet schowka</span><span class="sxs-lookup"><span data-stu-id="b192a-113">Clipboard cmdlets</span></span>

<span data-ttu-id="b192a-114">`Get-Clipboard` i `Set-Clipboard` ułatwić transferu zawartości do i z sesji środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b192a-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="b192a-115">Polecenia cmdlet Schowka obsługuje obrazy, pliki audio, listy plików i tekst.</span><span class="sxs-lookup"><span data-stu-id="b192a-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="b192a-116">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="b192a-116">For more information, see:</span></span>

- [<span data-ttu-id="b192a-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="b192a-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="b192a-118">Zestaw Schowka</span><span class="sxs-lookup"><span data-stu-id="b192a-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="b192a-119">Kryptograficznych polecenia cmdlet składni wiadomości (CMS)</span><span class="sxs-lookup"><span data-stu-id="b192a-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="b192a-120">Polecenia cmdlet składnię komunikatów kryptograficznych obsługują szyfrowanie i odszyfrowywanie zawartości przy użyciu formatu standardowego IETF kryptograficznie ochrony wiadomości, zgodnie z opisem przez [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="b192a-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="b192a-121">Standardowa szyfrowania CMS implementuje kryptografii klucza publicznego, w którym klucz używany do szyfrowania zawartości ( *klucza publicznego*) i klucz używany do odszyfrowywania zawartości ( *klucza prywatnego*) są oddzielone.</span><span class="sxs-lookup"><span data-stu-id="b192a-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="b192a-122">Klucz publiczny może być powszechnie udostępniony i nie jest poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="b192a-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="b192a-123">Żadnej zawartości, szyfrowane przy użyciu klucza publicznego odszyfrować je mogą tylko przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="b192a-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="b192a-124">Aby uzyskać więcej informacji, zobacz [kryptografii klucza publicznego](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="b192a-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="b192a-125">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="b192a-125">For more information see:</span></span>

- [<span data-ttu-id="b192a-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b192a-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [<span data-ttu-id="b192a-127">Ochrona CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b192a-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [<span data-ttu-id="b192a-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b192a-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

<span data-ttu-id="b192a-129">Certyfikaty wymagają identyfikator unikatowy użycia klucza (EKU), takie jak "Podpisywanie kodu" lub "Zaszyfrowanych wiadomości E-mail", aby je zidentyfikować jako certyfikaty szyfrowania danych w programie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b192a-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="b192a-130">Aby wyświetlić certyfikaty szyfrowania dokumentu dostawcę certyfikatów, można użyć **DocumentEncryptionCert** parametru dynamicznego `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="b192a-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="b192a-131">Wyodrębnianie i analizowanie obiektów ze strukturą z zawartości ciągu</span><span class="sxs-lookup"><span data-stu-id="b192a-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="b192a-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="b192a-132">ConvertFrom-String</span></span>

<span data-ttu-id="b192a-133">Nowy `ConvertFrom-String` polecenie cmdlet obsługuje dwa tryby:</span><span class="sxs-lookup"><span data-stu-id="b192a-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="b192a-134">Basic rozdzielonych analizy</span><span class="sxs-lookup"><span data-stu-id="b192a-134">Basic delimited parsing</span></span>
- <span data-ttu-id="b192a-135">Wygenerowany automatycznie oparte na przykładzie analizy</span><span class="sxs-lookup"><span data-stu-id="b192a-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="b192a-136">Rozdzielany podczas analizowania, domyślnie dzieli dane wejściowe na biały znak, a następnie przypisuje nazwy właściwości do wynikowego grup.</span><span class="sxs-lookup"><span data-stu-id="b192a-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="b192a-137">**UpdateTemplate** parametr zapisuje wyniki algorytmu uczenia na komentarz w pliku szablonu.</span><span class="sxs-lookup"><span data-stu-id="b192a-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="b192a-138">Dzięki temu learning przetwarzania kosztu jednorazowe (etap najwolniejsze).</span><span class="sxs-lookup"><span data-stu-id="b192a-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="b192a-139">Uruchamianie `ConvertFrom-String` przy użyciu szablonu, który zawiera algorytmu uczenia zakodowany jest teraz prawie natychmiastowe.</span><span class="sxs-lookup"><span data-stu-id="b192a-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="b192a-140">Aby uzyskać więcej informacji, zobacz [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="b192a-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="b192a-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="b192a-141">Convert-String</span></span>

<span data-ttu-id="b192a-142">`Convert-String` Umożliwia podanie przed i po przykłady sposobu tekstu do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="b192a-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="b192a-143">Polecenia cmdlet, które automatycznie formatowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="b192a-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="b192a-144">Aby uzyskać więcej informacji, zobacz [przekonwertować ciągu](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="b192a-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="b192a-145">Aktualizacje obiektu FileInfo</span><span class="sxs-lookup"><span data-stu-id="b192a-145">Updates to FileInfo object</span></span>

<span data-ttu-id="b192a-146">Informacje o wersji pliku mogą mylące, zwłaszcza w przypadkach, w której plik został poprawek.</span><span class="sxs-lookup"><span data-stu-id="b192a-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="b192a-147">Program WMF 5.0 dodaje nowe **FileVersionRaw** i **ProductVersionRaw** skryptu właściwości **FileInfo** obiektów.</span><span class="sxs-lookup"><span data-stu-id="b192a-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="b192a-148">Oto właściwości wyświetlane powershell.exe (przy założeniu, że $pid jest identyfikator procesu programu PowerShell):</span><span class="sxs-lookup"><span data-stu-id="b192a-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="b192a-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="b192a-149">Format-Hex</span></span>

<span data-ttu-id="b192a-150">`Format-Hex` Umożliwia wyświetlanie danych tekstowych lub binarnych w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="b192a-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="b192a-151">Aby uzyskać więcej informacji, zobacz [Format szesnastkowy](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="b192a-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="b192a-152">Polecenie GET-ChildItem ma parametr - Depth</span><span class="sxs-lookup"><span data-stu-id="b192a-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="b192a-153">`Get-ChildItem` ma teraz **głębokość** parametr do użycia z usługą **Recurse** ograniczyć rekursji:</span><span class="sxs-lookup"><span data-stu-id="b192a-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="b192a-154">Obsługa modułów na potrzeby deklarowania zakresów wersji (1.\* itp.)</span><span class="sxs-lookup"><span data-stu-id="b192a-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="b192a-155">Teraz można połączyć **MinimumVersion** i **MaximumVersion** można zaimportować modułu w obrębie określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="b192a-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="b192a-156">Parametry obsługują także symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="b192a-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="b192a-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="b192a-157">New-Guid</span></span>

<span data-ttu-id="b192a-158">Istnieje wiele scenariuszy, w którym youneed Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="b192a-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="b192a-159">`New-GUID` Polecenie cmdlet zapewnia prosty sposób utworzyć nowego identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="b192a-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="b192a-160">Parametr NoNewLine</span><span class="sxs-lookup"><span data-stu-id="b192a-160">NoNewLine parameter</span></span>

<span data-ttu-id="b192a-161">`Out-File`, `Add-Content`, i `Set-Content` powstał nowy **NoNewline** przełącznika, który umożliwia pominięcie znakiem nowego wiersza po danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b192a-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="b192a-162">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b192a-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

<span data-ttu-id="b192a-163">Bez **NoNewline** określony, poszczególne fragmenty powinna znajdować się w osobnym wierszu:</span><span class="sxs-lookup"><span data-stu-id="b192a-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="b192a-164">Interakcja z symboliczne linki korzystające z poleceń cmdlet elementów ulepszone</span><span class="sxs-lookup"><span data-stu-id="b192a-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="b192a-165">Polecenie cmdlet elementu i kilka powiązane polecenia cmdlet zostały rozszerzone do obsługi łącza symbolicznego.</span><span class="sxs-lookup"><span data-stu-id="b192a-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="b192a-166">Łącza symbolicznego, pliki</span><span class="sxs-lookup"><span data-stu-id="b192a-166">Symbolic link files</span></span>

<span data-ttu-id="b192a-167">W tym przykładzie utworzymy nowy plik łącze symboliczne o nazwie MySymLinkFile.txt w C:\Temp, który stanowi łącze do $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="b192a-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="b192a-168">Wszystkie trzy przykłady generuje ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="b192a-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="b192a-169">Łącze symboliczne katalogów</span><span class="sxs-lookup"><span data-stu-id="b192a-169">Symbolic link directories</span></span>

<span data-ttu-id="b192a-170">W tym przykładzie utworzymy nowego katalogu łącze symboliczne o nazwie MySymLinkDir w C:\Temp, który stanowi łącze do folderu $pshome.</span><span class="sxs-lookup"><span data-stu-id="b192a-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="b192a-171">Wszystkie trzy przykłady generuje ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="b192a-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="b192a-172">Twarde linki</span><span class="sxs-lookup"><span data-stu-id="b192a-172">Hard links</span></span>

<span data-ttu-id="b192a-173">Tej samej kombinacji **ścieżki** i **nazwa** dozwolone zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="b192a-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="b192a-174">Katalog w punktach transferu</span><span class="sxs-lookup"><span data-stu-id="b192a-174">Directory junctions</span></span>

<span data-ttu-id="b192a-175">Tej samej kombinacji **ścieżki** i **nazwa** dozwolone zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="b192a-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="b192a-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="b192a-176">Get-ChildItem</span></span>

<span data-ttu-id="b192a-177">`Get-ChildItem` teraz wyświetla "l" w **tryb** właściwości do wskazania łącze symboliczne pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="b192a-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="b192a-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="b192a-178">Remove-Item</span></span>

<span data-ttu-id="b192a-179">Usuwanie łącza symbolicznego działa jak usuwanie dowolny inny typ elementu.</span><span class="sxs-lookup"><span data-stu-id="b192a-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="b192a-180">Użyj **życie** parametru, aby usunąć pliki w katalogu docelowego i łącza symbolicznego.</span><span class="sxs-lookup"><span data-stu-id="b192a-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="b192a-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="b192a-181">New-TemporaryFile</span></span>

<span data-ttu-id="b192a-182">Czasami w skryptach, można utworzyć pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="b192a-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="b192a-183">Teraz możesz zrobić to za pomocą `New-TemporaryFile` polecenia cmdlet:</span><span class="sxs-lookup"><span data-stu-id="b192a-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="b192a-184">Zarządzanie przełącznikiem sieciowym przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="b192a-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="b192a-185">Przełącznika sieci poleceń cmdlet, wprowadzone w programie WMF 5.0 umożliwiają zastosowanie przełącznika, wirtualnej sieci LAN (VLAN) i podstawowa konfiguracja portu przełącznika sieci warstwy 2 do przełączników sieciowych z certyfikatem logo systemu Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="b192a-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="b192a-186">Za pomocą tych poleceń cmdlet można wykonywać:</span><span class="sxs-lookup"><span data-stu-id="b192a-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="b192a-187">Globalne przełącznika konfiguracji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="b192a-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="b192a-188">Ustaw nazwę hosta</span><span class="sxs-lookup"><span data-stu-id="b192a-188">Set host name</span></span>
  - <span data-ttu-id="b192a-189">Transparent przełącznik set</span><span class="sxs-lookup"><span data-stu-id="b192a-189">Set switch banner</span></span>
  - <span data-ttu-id="b192a-190">Zachowaj konfigurację</span><span class="sxs-lookup"><span data-stu-id="b192a-190">Persist configuration</span></span>
  - <span data-ttu-id="b192a-191">Włącza lub wyłącza funkcję</span><span class="sxs-lookup"><span data-stu-id="b192a-191">Enable or disable feature</span></span>

- <span data-ttu-id="b192a-192">Konfiguracja sieci VLAN:</span><span class="sxs-lookup"><span data-stu-id="b192a-192">VLAN configuration:</span></span>
  - <span data-ttu-id="b192a-193">Tworzenie lub usuwanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b192a-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="b192a-194">Włączanie lub wyłączanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b192a-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="b192a-195">Wyliczanie sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b192a-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="b192a-196">Przyjazna nazwa zestawu do sieci VLAN</span><span class="sxs-lookup"><span data-stu-id="b192a-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="b192a-197">Konfiguracja portu warstwy 2:</span><span class="sxs-lookup"><span data-stu-id="b192a-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="b192a-198">Wyliczanie portów</span><span class="sxs-lookup"><span data-stu-id="b192a-198">Enumerate ports</span></span>
  - <span data-ttu-id="b192a-199">Włączać lub wyłączać porty</span><span class="sxs-lookup"><span data-stu-id="b192a-199">Enable or disable ports</span></span>
  - <span data-ttu-id="b192a-200">Tryby portu zestawu i właściwości</span><span class="sxs-lookup"><span data-stu-id="b192a-200">Set port modes and properties</span></span>
  - <span data-ttu-id="b192a-201">Dodawanie lub kojarzenie sieci VLAN na magistrali lub dostęp przy użyciu portu</span><span class="sxs-lookup"><span data-stu-id="b192a-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="b192a-202">Aby uzyskać więcej informacji, zobacz [NetworkSwitchManager](/powershell/module/networkswitchmanager/) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b192a-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="b192a-203">Generowanie poleceń cmdlet programu PowerShell w oparciu o punkt końcowy OData z ODataUtils</span><span class="sxs-lookup"><span data-stu-id="b192a-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="b192a-204">Moduł ODataUtils umożliwia generowanie poleceń cmdlet programu PowerShell z punkty końcowe REST, które obsługują OData.</span><span class="sxs-lookup"><span data-stu-id="b192a-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="b192a-205">Moduł Microsoft.PowerShell.ODataUtils obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="b192a-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="b192a-206">Kanał dodatkowe informacje z punktu końcowego po stronie serwera po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="b192a-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="b192a-207">Obsługa stronicowania po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="b192a-207">Client-side paging support</span></span>
- <span data-ttu-id="b192a-208">Filtrowanie po stronie serwera, za pomocą wybierz parametr -</span><span class="sxs-lookup"><span data-stu-id="b192a-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="b192a-209">Obsługa nagłówków żądań sieci web</span><span class="sxs-lookup"><span data-stu-id="b192a-209">Support for web request headers</span></span>

<span data-ttu-id="b192a-210">Polecenia cmdlet serwera proxy generowany przez `Export-ODataEndPointProxy` polecenia cmdlet zawierają dodatkowe informacje z punktu końcowego OData po stronie serwera, o **informacji** strumienia.</span><span class="sxs-lookup"><span data-stu-id="b192a-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="b192a-211">W poniższym przykładzie jesteśmy podczas pobierania produktu i przechwytywania danych wyjściowych w `$infoStream` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b192a-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="b192a-212">Określając **IncludeTotalResponseCount** parametru, uzyskujemy łącznej liczby wszystkich **produktu** rekordów dostępne na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b192a-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="b192a-213">Rekordy można uzyskać z serwera w gałęziach, używając obsługę stronicowania po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="b192a-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="b192a-214">Jest to przydatne, jeśli musi pobrać dużą ilość danych z serwera za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="b192a-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="b192a-215">Polecenia cmdlet wygenerowany serwer proxy obsługuje **wybierz** parametr, który jest używany jako filtr do odbierania właściwości rekordu, wymaganych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b192a-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="b192a-216">Filtrowanie odbywa się na serwerze, co zmniejsza ilość danych przesyłanych przez sieć.</span><span class="sxs-lookup"><span data-stu-id="b192a-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="b192a-217">`Export-ODataEndpointProxy` Polecenia cmdlet i polecenia cmdlet serwera proxy, generowane przez nią, obsługują teraz **nagłówki** parametru.</span><span class="sxs-lookup"><span data-stu-id="b192a-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="b192a-218">Nagłówek może służyć do kanału dodatkowe informacje, oczekiwany przez punkt końcowy OData.</span><span class="sxs-lookup"><span data-stu-id="b192a-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="b192a-219">W poniższym przykładzie, tabelę mieszania, zawierający klucz subskrypcji znajduje się na **nagłówki** parametru.</span><span class="sxs-lookup"><span data-stu-id="b192a-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="b192a-220">Jest to typowy przykład dla usług, które są oczekiwane klucz subskrypcji na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="b192a-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
