---
title: Pisanie tematów Pomocy dotyczących modułów programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845458"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="69774-102">Pisanie pomocy dotyczącej modułów programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69774-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="69774-103">Moduły programu Windows PowerShell może obejmować tematy Pomocy dotyczące modułu i członków modułu, takie jak polecenia cmdlet, dostawców, funkcji i skryptów.</span><span class="sxs-lookup"><span data-stu-id="69774-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="69774-104">`Get-Help` Polecenie cmdlet wyświetla tematy pomocy modułu w tym samym formacie jak Wyświetla Pomoc dla innych elementów programu Windows PowerShell, a użytkownicy standard `Get-Help` poleceń, aby uzyskać pomoc.</span><span class="sxs-lookup"><span data-stu-id="69774-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="69774-105">W tym dokumencie wyjaśniono, formatu i poprawne rozmieszczenie tematy pomocy modułu i sugerują one wskazówki dotyczące zawartości pomocy modułu.</span><span class="sxs-lookup"><span data-stu-id="69774-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="69774-106">Typy pomoc modułu</span><span class="sxs-lookup"><span data-stu-id="69774-106">Types of Module Help</span></span>

<span data-ttu-id="69774-107">Moduł może obejmować następujące typy pomocy.</span><span class="sxs-lookup"><span data-stu-id="69774-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="69774-108">**Pomocy dotyczącej poleceń cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="69774-108">**Cmdlet Help**.</span></span> <span data-ttu-id="69774-109">Tematy pomocy, które opisują poleceń cmdlet w module są pliki XML, które używają polecenia Pomoc schematu</span><span class="sxs-lookup"><span data-stu-id="69774-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="69774-110">**Dostawca pomocy**.</span><span class="sxs-lookup"><span data-stu-id="69774-110">**Provider Help**.</span></span> <span data-ttu-id="69774-111">Tematy pomocy, które opisują dostawców w module są pliki XML, które używają dostawcy pomocy schematu.</span><span class="sxs-lookup"><span data-stu-id="69774-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="69774-112">**Funkcja pomocy**.</span><span class="sxs-lookup"><span data-stu-id="69774-112">**Function Help**.</span></span> <span data-ttu-id="69774-113">Tematy pomocy, które opisują funkcje w module może być plików XML, użyj polecenia pomocy schematu lub oparta na komentarzach tematy pomocy, w ramach funkcji lub skryptu lub moduł skryptu</span><span class="sxs-lookup"><span data-stu-id="69774-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="69774-114">**Skrypt pomocy**.</span><span class="sxs-lookup"><span data-stu-id="69774-114">**Script Help**.</span></span> <span data-ttu-id="69774-115">Tematy pomocy, które opisują skrypty w module może być plików XML, użyj polecenia pomocy schematu lub oparta na komentarzach tematów pomocy w skrypcie modułu skryptu.</span><span class="sxs-lookup"><span data-stu-id="69774-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="69774-116">**Koncepcyjny ("o") pomocy**.</span><span class="sxs-lookup"><span data-stu-id="69774-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="69774-117">Koncepcyjny ("o") tematu Pomocy można użyć do opisania moduł i jej elementów członkowskich i wyjaśnić, jak elementy członkowskie można razem wykonywać zadania.</span><span class="sxs-lookup"><span data-stu-id="69774-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="69774-118">Koncepcyjne tematy pomocy są plikami tekstowymi przy użyciu kodowania Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="69774-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="69774-119">Nazwa pliku musi być `about_<name>.help.txt` formacie, na przykład about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="69774-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="69774-120">Domyślnie środowisko Windows PowerShell zawiera ponad 100 tych pojęć dotyczących pomocy i są one formatowane tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="69774-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="69774-121">Umieszczanie pomoc modułu</span><span class="sxs-lookup"><span data-stu-id="69774-121">Placement of Module Help</span></span>

<span data-ttu-id="69774-122">`Get-Help` Polecenia cmdlet szuka plików tematów pomocy modułu podkatalogi specyficzny dla języka katalog modułu.</span><span class="sxs-lookup"><span data-stu-id="69774-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="69774-123">Na przykład na poniższym diagramie strukturę katalogu przedstawiono lokalizację tematy pomocy dla modułu SampleModule.</span><span class="sxs-lookup"><span data-stu-id="69774-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="69774-124">W tym przykładzie  *\<ModulePath >* symbolu zastępczego jedna ze ścieżek używanych w `PSModulePath` zmiennej środowiskowej, np. $home\Documents\Modules, $pshome\Modules lub niestandardową ścieżkę podaną przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69774-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="69774-125">Uzyskiwanie pomocy modułu</span><span class="sxs-lookup"><span data-stu-id="69774-125">Getting Module Help</span></span>

<span data-ttu-id="69774-126">Gdy użytkownik importuje modułu do sesji, tematy pomocy dla tego modułu są importowane do sesji, wraz z modułem.</span><span class="sxs-lookup"><span data-stu-id="69774-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="69774-127">Możesz wyświetlić listę plików tematów pomocy w wartości klucza FileList w manifeście modułu, ale nie dotyczy tematy Pomocy `Export-ModuleMember` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69774-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="69774-128">Możesz podać tematy pomocy modułu w różnych językach.</span><span class="sxs-lookup"><span data-stu-id="69774-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="69774-129">`Get-Help` Polecenie cmdlet automatycznie wyświetla tematy pomocy modułu w języku, który jest określony dla bieżącego użytkownika w elemencie Opcje regionalne i językowe w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="69774-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="69774-130">W systemach Windows Vista i nowszych wersjach systemu Windows `Get-Help` Wyszukuje tematy pomocy podkatalogi specyficzny dla języka katalog modułu zgodnie ze standardami rezerwowego języka dla Windows.</span><span class="sxs-lookup"><span data-stu-id="69774-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="69774-131">W programie Windows PowerShell 3.0, uruchamianie `Get-Help` polecenia dla polecenia cmdlet lub funkcji wyzwala automatyczne importowanie modułu.</span><span class="sxs-lookup"><span data-stu-id="69774-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="69774-132">`Get-Help` Natychmiast polecenie cmdlet wyświetla zawartość tematów pomocy w module.</span><span class="sxs-lookup"><span data-stu-id="69774-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="69774-133">Jeśli moduł zawiera tematy pomocy i istnieją tematów pomocy dotyczącej poleceń w module na komputerze użytkownika `Get-Help` Wyświetla Pomoc wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="69774-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="69774-134">Wygenerowany automatycznie pomocy zawiera polecenia składni, parametrów i typów wejściowych i wyjściowych, ale nie obejmuje wszystkie opisy.</span><span class="sxs-lookup"><span data-stu-id="69774-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="69774-135">Wygenerowany automatycznie pomocy zawiera tekst, który kieruje użytkownika podjąć próbę użycia `Update-Help` polecenia cmdlet, aby pobrać Pomoc dla polecenia z Internetu lub udziału plików.</span><span class="sxs-lookup"><span data-stu-id="69774-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="69774-136">Ponadto zaleca używanie **Online** parametru `Get-Help` polecenie cmdlet umożliwiające pobranie wersji online tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="69774-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="69774-137">Obsługa aktualizowalnej pomocy</span><span class="sxs-lookup"><span data-stu-id="69774-137">Supporting Updatable Help</span></span>

<span data-ttu-id="69774-138">Użytkownicy programu Windows PowerShell 3.0 i nowszych wersjach środowiska Windows PowerShell można pobrać i zainstalować pliki zaktualizowane pomocy dla modułu z Internetu lub udziału pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="69774-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="69774-139">`Update-Help` i `Save-Help` poleceń cmdlet ukryć szczegóły zarządzania przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69774-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="69774-140">Użytkownicy mogą wykonywać `Update-Help` polecenia cmdlet, a następnie użyj `Get-Help` polecenia cmdlet, aby odczytać najnowszych plików pomocy dla modułu w wierszu polecenia programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69774-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="69774-141">Użytkownicy muszą uruchomić system Windows lub programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69774-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="69774-142">Użytkownicy się za zaporami i tych, bez dostępu do Internetu mogą używać aktualizowalnej pomocy, jak również.</span><span class="sxs-lookup"><span data-stu-id="69774-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="69774-143">Administratorzy z Internetu do sterowania dostępem `Save-Help` polecenia cmdlet, aby pobrać i zainstalować najnowszych plików pomocy do udziału plików.</span><span class="sxs-lookup"><span data-stu-id="69774-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="69774-144">Następnie należy użyć użytkowników **ścieżki** parametru `Update-Help` polecenie cmdlet umożliwiające pobranie najnowszych plików pomocy z udziału plików.</span><span class="sxs-lookup"><span data-stu-id="69774-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="69774-145">Autorzy modułów uwzględnić pliki pomocy w module i za pomocą aktualizowalnej pomocy zaktualizować pliki pomocy lub Pomiń pliki pomocy w module i używać aktualizowalnej pomocy można zainstalować i zaktualizować je.</span><span class="sxs-lookup"><span data-stu-id="69774-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="69774-146">Aby uzyskać więcej informacji na temat aktualizowalnej pomocy zobacz [Obsługa aktualizowalnej pomocy](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="69774-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="69774-147">Obsługa pomocy online</span><span class="sxs-lookup"><span data-stu-id="69774-147">Supporting Online Help</span></span>

<span data-ttu-id="69774-148">Użytkownicy, którzy nie może lub nie należy instalować zaktualizowano pomoc, której pliki na swoich komputerach zależą od często wersję modułu tematy Pomocy online.</span><span class="sxs-lookup"><span data-stu-id="69774-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="69774-149">**Online** parametru `Get-Help` polecenia cmdlet spowoduje otwarcie wersji online polecenia cmdlet lub zaawansowanych funkcji tematu pomocy dla użytkownika w swojej domyślnej przeglądarki internetowej.</span><span class="sxs-lookup"><span data-stu-id="69774-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="69774-150">`Get-Help` Polecenie cmdlet używa wartości **HelpUri** właściwości polecenia cmdlet lub funkcję, aby znaleźć wersji online tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="69774-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="69774-151">Począwszy od programu Windows PowerShell 3.0, możesz pomóc użytkownikom znajdowanie wersji online tematy pomocy polecenia cmdlet i funkcję, definiując atrybutu HelpUri w klasie polecenia cmdlet lub **HelpUri** właściwość **CmdletBinding** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="69774-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="69774-152">Wartość atrybutu jest wartość **HelpUri** właściwości polecenia cmdlet lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="69774-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="69774-153">Aby uzyskać więcej informacji, zobacz [Obsługa pomocy Online](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="69774-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69774-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69774-154">See Also</span></span>

[<span data-ttu-id="69774-155">Pisanie modułu programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69774-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="69774-156">Obsługa aktualizowalnej pomocy</span><span class="sxs-lookup"><span data-stu-id="69774-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="69774-157">Obsługa pomocy Online</span><span class="sxs-lookup"><span data-stu-id="69774-157">Supporting Online Help</span></span>](./supporting-online-help.md)