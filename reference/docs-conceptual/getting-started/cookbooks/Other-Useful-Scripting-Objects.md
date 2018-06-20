---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Inne przydatne obiekty skryptowe
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949829"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="7bd1b-103">Inne przydatne obiekty skryptowe</span><span class="sxs-lookup"><span data-stu-id="7bd1b-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="7bd1b-104">Następujące obiekty oferowanie dodatkowych funkcji obsługi skryptów w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="7bd1b-105">Nie są częścią **$psISE** hierarchii.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="7bd1b-106">Przydatne obiektów skryptów</span><span class="sxs-lookup"><span data-stu-id="7bd1b-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="7bd1b-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="7bd1b-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="7bd1b-108">Istnieją pewne ograniczenia dotyczące współdziałania programu Windows PowerShell ISE z aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="7bd1b-109">Polecenia lub skryptu automatyzacji, który wymaga interwencji użytkownika może nie działać jak działa z konsoli programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="7bd1b-110">Możesz zablokować tych poleceń lub skryptów z poziomu uruchomionej w okienku polecenia programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="7bd1b-111">**$PsUnsupportedConsoleApplications** obiekt przechowuje listę tych poleceń.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="7bd1b-112">Jeśli zostanie podjęta próba uruchomienia polecenia na tej liście, możesz uzyskać komunikat, że nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="7bd1b-113">Poniższy skrypt dodaje wpis do listy.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="7bd1b-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="7bd1b-114">$psLocalHelp</span></span>

<span data-ttu-id="7bd1b-115">Jest to obiekt słownika, który mapuje kontekstowa między tematy pomocy i skojarzonych z nimi łączy w lokalnym skompilowany plik Pomocy HTML.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="7bd1b-116">Służy do zlokalizowania lokalnej pomocy dla określonego tematu.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="7bd1b-117">Można dodawać lub usuwać tematy z tej listy.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="7bd1b-118">Poniższy przykład kodu pokazuje przykładowe pary klucz wartość, które są zawarte w **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="7bd1b-119">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7bd1b-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="7bd1b-120">Klucz: Komputer</span><span class="sxs-lookup"><span data-stu-id="7bd1b-120">Key : Add-Computer</span></span>|<span data-ttu-id="7bd1b-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="7bd1b-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="7bd1b-122">Klucza: Zawartość</span><span class="sxs-lookup"><span data-stu-id="7bd1b-122">Key : Add-Content</span></span>|<span data-ttu-id="7bd1b-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="7bd1b-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="7bd1b-124">Poniższy skrypt dodaje wpis do listy.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="7bd1b-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="7bd1b-125">$psOnlineHelp</span></span>

<span data-ttu-id="7bd1b-126">Jest to obiekt słownika, który mapuje kontekstowa między tytuły tematów tematów pomocy i ich skojarzonych zewnętrzne adresy URL.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="7bd1b-127">Służy do lokalizowania określonego tematu pomocy w sieci web.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="7bd1b-128">Można dodawać lub usuwać tematy z tej listy.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="7bd1b-129">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7bd1b-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="7bd1b-130">Klucz: Komputer</span><span class="sxs-lookup"><span data-stu-id="7bd1b-130">Key : Add-Computer</span></span>|<span data-ttu-id="7bd1b-131">Wartość: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="7bd1b-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="7bd1b-132">Klucza: Zawartość</span><span class="sxs-lookup"><span data-stu-id="7bd1b-132">Key : Add-Content</span></span>|<span data-ttu-id="7bd1b-133">Wartość: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="7bd1b-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="7bd1b-134">Poniższy skrypt dodaje wpis do listy.</span><span class="sxs-lookup"><span data-stu-id="7bd1b-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="7bd1b-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bd1b-135">See Also</span></span>

- [<span data-ttu-id="7bd1b-136">Cel programu Windows PowerShell ISE skryptów modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="7bd1b-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)