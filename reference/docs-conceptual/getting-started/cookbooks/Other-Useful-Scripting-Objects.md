---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Inne przydatne obiekty skryptowe
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 2ae9bc1864daedbcb0070c5f3862a6c98f8db2d4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893284"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="3e522-103">Inne przydatne obiekty skryptowe</span><span class="sxs-lookup"><span data-stu-id="3e522-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="3e522-104">Następujące obiekty zapewniają dodatkowe funkcje obsługi skryptów w środowisku Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3e522-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="3e522-105">Nie są one częścią **$psISE** hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3e522-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="3e522-106">Przydatne obiekty skryptów</span><span class="sxs-lookup"><span data-stu-id="3e522-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="3e522-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="3e522-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="3e522-108">Istnieją pewne ograniczenia dotyczące współdziałania programu Windows PowerShell ISE z aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="3e522-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="3e522-109">Polecenia lub skryptów automatyzacji, który wymaga interwencji użytkownika mogą nie działać w sposób, w jaki działa z poziomu konsoli programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e522-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="3e522-110">Można zablokować tych poleceń lub skryptów działających w okienku polecenia programu Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3e522-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="3e522-111">**$PsUnsupportedConsoleApplications** obiekt przechowuje listę tych poleceń.</span><span class="sxs-lookup"><span data-stu-id="3e522-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="3e522-112">Jeśli zostanie podjęta próba uruchomienia polecenia na tej liście, otrzymasz komunikat, że nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="3e522-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="3e522-113">Poniższy skrypt dodaje wpis do listy.</span><span class="sxs-lookup"><span data-stu-id="3e522-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="3e522-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="3e522-114">$psLocalHelp</span></span>

<span data-ttu-id="3e522-115">Jest to obiekt słownika, który przechowuje kontekstową mapowanie między tematy pomocy i skojarzonych z nimi łączy w lokalnym pliku Pomocy HTML skompilowany.</span><span class="sxs-lookup"><span data-stu-id="3e522-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="3e522-116">Jest ona używana do lokalizowania pomocy lokalnej do określonego tematu.</span><span class="sxs-lookup"><span data-stu-id="3e522-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="3e522-117">Można dodać lub usunąć tematy z tej listy.</span><span class="sxs-lookup"><span data-stu-id="3e522-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="3e522-118">Poniższy przykład kodu przedstawia przykładowe pary klucz wartość, które są zawarte w `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="3e522-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="pslocalhelp-sample-output"></a><span data-ttu-id="3e522-119">$psLocalHelp przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3e522-119">$psLocalHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="3e522-120">Klucz: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="3e522-120">Key : Add-Computer</span></span>|<span data-ttu-id="3e522-121">Wartość: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="3e522-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="3e522-122">Klucza: Zawartość</span><span class="sxs-lookup"><span data-stu-id="3e522-122">Key : Add-Content</span></span>|<span data-ttu-id="3e522-123">Wartość: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="3e522-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="3e522-124">Poniższy skrypt dodaje wpis do listy.</span><span class="sxs-lookup"><span data-stu-id="3e522-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="3e522-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="3e522-125">$psOnlineHelp</span></span>

<span data-ttu-id="3e522-126">Jest to obiekt słownika, który przechowuje kontekstową mapowanie między tytuły tematów tematów pomocy i ich skojarzone zewnętrzne adresy URL.</span><span class="sxs-lookup"><span data-stu-id="3e522-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="3e522-127">Jest ona używana do lokalizowania pomoc dotyczącą określonego tematu w sieci web.</span><span class="sxs-lookup"><span data-stu-id="3e522-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="3e522-128">Można dodać lub usunąć tematy z tej listy.</span><span class="sxs-lookup"><span data-stu-id="3e522-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

## <a name="psonilnehelp-sample-output"></a><span data-ttu-id="3e522-129">$psOnilneHelp przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3e522-129">$psOnilneHelp Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="3e522-130">Klucz: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="3e522-130">Key : Add-Computer</span></span>|<span data-ttu-id="3e522-131">Wartość: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="3e522-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="3e522-132">Klucza: Zawartość</span><span class="sxs-lookup"><span data-stu-id="3e522-132">Key : Add-Content</span></span>|<span data-ttu-id="3e522-133">Wartość: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="3e522-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

<span data-ttu-id="3e522-134">Poniższy skrypt dodaje wpis do listy.</span><span class="sxs-lookup"><span data-stu-id="3e522-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="3e522-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e522-135">See Also</span></span>

[<span data-ttu-id="3e522-136">Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3e522-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)