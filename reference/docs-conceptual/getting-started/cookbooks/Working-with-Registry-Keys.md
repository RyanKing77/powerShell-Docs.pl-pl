---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Praca z kluczy rejestru
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: efb2c016afa2212c2907c0740ad26c4e4cddd3af
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="d5fc8-103">Praca z kluczy rejestru</span><span class="sxs-lookup"><span data-stu-id="d5fc8-103">Working with Registry Keys</span></span>
<span data-ttu-id="d5fc8-104">Ponieważ klucze rejestru są elementy na dyskach środowiska Windows PowerShell, pracy z nimi jest bardzo podobny do pracy z plikami i folderami.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="d5fc8-105">Jeden krytyczne różnica polega na tym, że każdy element na dysk programu Windows PowerShell opartych na rejestrze jest kontenerem, podobnie jak folder na dysku systemu plików.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="d5fc8-106">Wpisy rejestru oraz powiązanych wartości, są jednak właściwości elementów nie różne elementy.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="d5fc8-107">Wyświetlanie listy wszystkich jego podkluczy klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="d5fc8-107">Listing All Subkeys of a Registry Key</span></span>
<span data-ttu-id="d5fc8-108">Wszystkie elementy bezpośrednio w kluczu rejestru można wyświetlać za pomocą **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="d5fc8-109">Dodaj opcjonalny **życie** parametru do wyświetlania ukryte lub elementów systemu.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="d5fc8-110">Na przykład to polecenie wyświetla elementy bezpośrednio z poziomu środowiska Windows PowerShell dysku HKCU:, które odpowiada gałęzi HKEY_CURRENT_USER rejestru:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="d5fc8-111">Są widoczne w gałęzi HKEY_CURRENT_USER w Edytorze rejestru (Regedit.exe) klucze najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="d5fc8-112">Ta ścieżka rejestru można również określić, określając nazwę dostawcy rejestru, a następnie "**::**".</span><span class="sxs-lookup"><span data-stu-id="d5fc8-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="d5fc8-113">Pełna nazwa dostawcy rejestru **Microsoft.PowerShell.Core\\rejestru**, ale to może zostać skrócony nieco **rejestru**.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="d5fc8-114">Dowolne z poniższych poleceń, wyświetla zawartość bezpośrednio pod HKCU:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="d5fc8-115">Te polecenia listy tylko bezpośrednio zawartych w niej elementów, podobnie jak przy użyciu jego Cmd.exe **DIR** polecenia lub **ls** w powłoce systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="d5fc8-116">Aby wyświetlić zawartych w niej elementów, należy określić **Recurse** parametru.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="d5fc8-117">Aby wyświetlić listę wszystkich kluczy rejestru HKCU, użyj następującego polecenia (Ta operacja może zająć bardzo dużo czasu.):</span><span class="sxs-lookup"><span data-stu-id="d5fc8-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="d5fc8-118">**Get-ChildItem** można wykonywać złożonych możliwości filtrowania, za pomocą jego **ścieżki**, **filtru**, **Include**, i **wykluczyć** parametrów, ale te parametry są zwykle tylko na podstawie nazwy.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="d5fc8-119">Można wykonać złożone filtrowanie na podstawie innych właściwości elementów za pomocą **Where-Object**polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-119">You can perform complex filtering based on other properties of items by using the **Where-Object**cmdlet.</span></span> <span data-ttu-id="d5fc8-120">Polecenie znajduje wszystkie klucze w HKCU:\\oprogramowania, które ma nie więcej niż jedną podkluczy, a także mieć dokładnie cztery wartości:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="d5fc8-121">Kopiowanie kluczy</span><span class="sxs-lookup"><span data-stu-id="d5fc8-121">Copying Keys</span></span>
<span data-ttu-id="d5fc8-122">Kopiowanie wykonuje się za pomocą **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="d5fc8-123">Polecenie kopiuje HKLM:\\oprogramowania\\Microsoft\\Windows\\CurrentVersion i wszystkie jej właściwości w celu HKCU:\\, tworzenie nowy klucz o nazwie "CurrentVersion":</span><span class="sxs-lookup"><span data-stu-id="d5fc8-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="d5fc8-124">Jeśli należy zbadać ten nowy klucz w Edytorze rejestru lub za pomocą **Get-ChildItem**, można zauważyć, że nie masz kopii podkluczy zawarte w nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="d5fc8-125">Aby można było skopiować wszystkie zawartość kontenera, należy określić **Recurse** parametru.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="d5fc8-126">Aby poprzedniego cykliczne polecenia kopiowania, należy użyć tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-126">To make the preceding copy command recursive, you would use this command:</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="d5fc8-127">Można nadal używać innych narzędzi, masz już dostępne do wykonywania kopii plików.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="d5fc8-128">Wszystkie narzędzia do edycji rejestru — tym reg.exe, regini.exe i regedit.exe—and obiektów COM, które obsługuje edycji rejestru (np. Klasa StdRegProv obiektu WScript.Shell i usługi WMI) można można używać wewnątrz środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="d5fc8-129">Tworzenie kluczy</span><span class="sxs-lookup"><span data-stu-id="d5fc8-129">Creating Keys</span></span>
<span data-ttu-id="d5fc8-130">Tworzenie nowych kluczy w rejestrze jest łatwiejsze niż w przypadku tworzenia nowego elementu w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="d5fc8-131">Ponieważ wszystkie klucze rejestru są kontenerami, nie trzeba określić typ elementu; Możesz po prostu podać jawne ścieżkę, takich jak:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="d5fc8-132">Umożliwia także ścieżkę opartej na dostawcy, aby określić klucz:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-132">You can also use a provider-based path to specify a key:</span></span>

```
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="d5fc8-133">Usuwanie kluczy</span><span class="sxs-lookup"><span data-stu-id="d5fc8-133">Deleting Keys</span></span>
<span data-ttu-id="d5fc8-134">Usuwanie elementów zasadniczo jest taka sama dla wszystkich dostawców.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="d5fc8-135">Następujące polecenia dyskretnie spowoduje usunięcie elementów:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-135">The following commands will silently remove items:</span></span>

```
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="d5fc8-136">Usunięcie wszystkich kluczy w określonym kluczu</span><span class="sxs-lookup"><span data-stu-id="d5fc8-136">Removing All Keys Under a Specific Key</span></span>
<span data-ttu-id="d5fc8-137">Można usunąć zawartych w niej elementów, używając **Usuń element**, ale pojawi się monit o potwierdzenie usunięcia, jeśli element zawiera coś innego.</span><span class="sxs-lookup"><span data-stu-id="d5fc8-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="d5fc8-138">Na przykład firma Microsoft podejmie próbę usunięcia HKCU:\\podklucza CurrentVersion utworzyliśmy, widzimy to:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="d5fc8-139">Aby usunąć zawartych w niej elementów bez monitowania, określ **-Recurse** parametru:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="d5fc8-140">Jeśli chcesz usunąć wszystkie elementy w HKCU:\\CurrentVersion, ale nie HKCU:\\CurrentVersion samego, możesz zamiast tego użyć:</span><span class="sxs-lookup"><span data-stu-id="d5fc8-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

