---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Tworzenie obiektów .NET i COM nowego obiektu
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: ef8215303aacd90536d3c2ae57bc3629e202f318
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086375"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="037bf-103">Tworzenie obiektów .NET i COM (New-Object)</span><span class="sxs-lookup"><span data-stu-id="037bf-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="037bf-104">Brak składników oprogramowania za pomocą środowiska .NET Framework i COM interfejsy, które umożliwiają wykonywanie wielu zadań administracyjnych.</span><span class="sxs-lookup"><span data-stu-id="037bf-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="037bf-105">Program Windows PowerShell pozwala używać tych składników, więc nie są ograniczone do zadania, które mogą być wykonywane przy użyciu poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="037bf-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="037bf-106">Wiele poleceń cmdlet w początkowym wydaniu programu Windows PowerShell nie działają na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="037bf-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="037bf-107">Przedstawiony zostanie sposób obejść to ograniczenie, gdy zarządzanie dziennikami zdarzeń za pomocą programu .NET Framework **System.Diagnostics.EventLog** klasy bezpośrednio z programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="037bf-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="037bf-108">Za pomocą nowego obiektu dla dostępu do dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="037bf-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="037bf-109">Biblioteka klas programu .NET Framework zawiera klasę o nazwie **System.Diagnostics.EventLog** który może służyć do zarządzania dziennikami zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="037bf-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="037bf-110">Można utworzyć nowe wystąpienie klasy .NET Framework za pomocą **New-Object** polecenia cmdlet z **TypeName** parametru.</span><span class="sxs-lookup"><span data-stu-id="037bf-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="037bf-111">Na przykład następujące polecenie tworzy odwołanie do dziennika zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="037bf-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="037bf-112">Mimo że polecenie utworzone wystąpienie klasy w dzienniku zdarzeń, wystąpienie nie zawiera żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="037bf-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="037bf-113">To, ponieważ firma Microsoft nie określiła określonego dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="037bf-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="037bf-114">Jak uzyskać prawdziwe dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="037bf-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="037bf-115">Za pomocą nowego obiektu za pomocą konstruktorów</span><span class="sxs-lookup"><span data-stu-id="037bf-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="037bf-116">Aby odwołać się do określonego dziennika zdarzeń, należy określić nazwę dziennika.</span><span class="sxs-lookup"><span data-stu-id="037bf-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="037bf-117">**Nowy obiekt** ma **Listaargumentów** parametru.</span><span class="sxs-lookup"><span data-stu-id="037bf-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="037bf-118">Argumenty przekazywane jako wartości tego parametru są używane przez metodę uruchamiania specjalne obiektu.</span><span class="sxs-lookup"><span data-stu-id="037bf-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="037bf-119">Metoda jest wywoływana *Konstruktor* ponieważ jest używana do konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="037bf-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="037bf-120">Na przykład aby uzyskać odwołanie do dziennika aplikacji, należy określić ciąg "Aplikacja" jako argumentu:</span><span class="sxs-lookup"><span data-stu-id="037bf-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="037bf-121">Ponieważ większość klas podstawowych platformy .NET Framework są zawarte w przestrzeni nazw systemu, programu Windows PowerShell automatycznie podejmie próbę znalezienia klas, które określisz w przestrzeni nazw systemu, jeśli nie znajdzie dopasowania dla typename, które określisz.</span><span class="sxs-lookup"><span data-stu-id="037bf-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="037bf-122">Oznacza to, że można określić Diagnostics.EventLog zamiast System.Diagnostics.EventLog.</span><span class="sxs-lookup"><span data-stu-id="037bf-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="037bf-123">Przechowywanie obiektów w zmiennych</span><span class="sxs-lookup"><span data-stu-id="037bf-123">Storing Objects in Variables</span></span>

<span data-ttu-id="037bf-124">Możesz chcieć przechowywać odwołanie do obiektu, aby można było używać w bieżącej powłoce.</span><span class="sxs-lookup"><span data-stu-id="037bf-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="037bf-125">Mimo że program Windows PowerShell umożliwia sporego nakładu pracy korzystających z potoków, zmniejszenie potrzebę zmiennych, czasem przechowywania odwołań do obiektów w zmiennych wygodniej do manipulowania tymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="037bf-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="037bf-126">Program Windows PowerShell umożliwia tworzenie zmiennych, które zasadniczo są nazwane obiekty.</span><span class="sxs-lookup"><span data-stu-id="037bf-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="037bf-127">Dane wyjściowe wszystkie prawidłowe polecenia programu Windows PowerShell, mogą być przechowywane w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="037bf-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="037bf-128">Nazwy zmiennych zawsze zaczynają się od $.</span><span class="sxs-lookup"><span data-stu-id="037bf-128">Variable names always begin with $.</span></span> <span data-ttu-id="037bf-129">Jeśli chcesz przechowywać odwołania dziennik aplikacji w zmiennej o nazwie $AppLog, wpisz nazwę zmiennej, następuje znak równości, a następnie wpisz polecenie używane do utworzenia obiektu dziennika aplikacji:</span><span class="sxs-lookup"><span data-stu-id="037bf-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="037bf-130">Następnie wpisz $AppLog, można wyświetlić, czy zawiera on w dzienniku aplikacji:</span><span class="sxs-lookup"><span data-stu-id="037bf-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="037bf-131">Dostęp do zdalnego dziennika zdarzeń za pomocą nowego obiektu</span><span class="sxs-lookup"><span data-stu-id="037bf-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="037bf-132">Polecenia używane w poprzedniej sekcji docelowe komputerze lokalnym; **Get EventLog** polecenia cmdlet można to zrobić.</span><span class="sxs-lookup"><span data-stu-id="037bf-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="037bf-133">Aby uzyskać dostęp do dzienników aplikacji na komputerze zdalnym, należy podać zarówno nazwę dziennika i nazwę komputera (lub adres IP) jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="037bf-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="037bf-134">Teraz, gdy odwołanie do dziennika zdarzeń, który jest przechowywany w zmiennej $RemoteAppLog, jakie zadania można możemy wykonać na nim?</span><span class="sxs-lookup"><span data-stu-id="037bf-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="037bf-135">Wyczyszczenie dziennika zdarzeń za pomocą metod obiektów</span><span class="sxs-lookup"><span data-stu-id="037bf-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="037bf-136">Obiekty mają często metod, które mogą być wywoływane w celu wykonywania zadań.</span><span class="sxs-lookup"><span data-stu-id="037bf-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="037bf-137">Możesz użyć **Get-Member** do wyświetlenia metody skojarzona z obiektem.</span><span class="sxs-lookup"><span data-stu-id="037bf-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="037bf-138">Poniższe polecenie i wybrane dane wyjściowe pokazują niektóre metody klasy w dzienniku zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="037bf-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="037bf-139">**Clear()** metoda można wyczyścić dziennik zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="037bf-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="037bf-140">Podczas wywoływania metody, należy zawsze wykonać nazwę metody przez nawiasy, nawet jeśli metoda nie wymaga argumentów.</span><span class="sxs-lookup"><span data-stu-id="037bf-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="037bf-141">Dzięki temu Windows PowerShell rozróżnienia metody i potencjalne właściwości o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="037bf-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="037bf-142">Wpisz następujące polecenie, aby wywołać **wyczyść** metody:</span><span class="sxs-lookup"><span data-stu-id="037bf-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="037bf-143">Wpisz następujące polecenie, aby wyświetlić dziennik.</span><span class="sxs-lookup"><span data-stu-id="037bf-143">Type the following to display the log.</span></span> <span data-ttu-id="037bf-144">Zostanie wyświetlony w dzienniku zdarzeń zostały wyczyszczone, a teraz jest 0 wpisów zamiast 262:</span><span class="sxs-lookup"><span data-stu-id="037bf-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="037bf-145">Tworzenie obiektów COM za pomocą nowego obiektu</span><span class="sxs-lookup"><span data-stu-id="037bf-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="037bf-146">Możesz użyć **New-Object** pracę dzięki składnikom Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="037bf-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="037bf-147">Składniki z zakresu od różnych bibliotek dodane za pomocą Windows Script Host (WSH) w celu aplikacji ActiveX, takich jak program Internet Explorer, które są zainstalowane na większości systemów.</span><span class="sxs-lookup"><span data-stu-id="037bf-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="037bf-148">**Nowy obiekt** używa otok wywoływanych w czasie wykonywania Framework .NET do tworzenia obiektów COM, dlatego ma te same ograniczenia, które .NET Framework obsługuje podczas wywoływania obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="037bf-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="037bf-149">Aby utworzyć obiekt COM, należy określić **ComObject** parametrem identyfikator programowy lub *ProgId* klasy COM, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="037bf-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="037bf-150">Wyczerpujące omówienie ograniczeń użytkowania COM i określania, jakie są dostępne w systemie ProgID jest poza zakresem niniejszego podręcznika użytkownika, ale dobrze znane obiekty ze środowisk, takich jak hosta skryptów systemu Windows mogą być używane w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="037bf-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="037bf-151">Obiekty hosta skryptów systemu Windows można tworzyć, określając te ProgID: **Obiektu WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, i **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="037bf-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="037bf-152">Następujące polecenia tworzą następujące obiekty:</span><span class="sxs-lookup"><span data-stu-id="037bf-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="037bf-153">Mimo że większość funkcjonalności tych klas są udostępniane w inny sposób w środowisku Windows PowerShell, nadal łatwiej zrobić za pomocą klasy funkcji jest kilka zadań, takich jak tworzenie skrótów.</span><span class="sxs-lookup"><span data-stu-id="037bf-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="037bf-154">Tworzenie skrótu na pulpicie za pomocą obiektu WScript.Shell.</span><span class="sxs-lookup"><span data-stu-id="037bf-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="037bf-155">Jedno zadanie, które mogą być wykonywane szybko za pomocą obiektu COM jest utworzenie skrótu.</span><span class="sxs-lookup"><span data-stu-id="037bf-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="037bf-156">Załóżmy, że chcesz utworzyć skrót na pulpicie prowadzący do folderu macierzystego dla środowiska Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="037bf-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="037bf-157">Najpierw należy utworzyć odwołanie do **obiektu WScript.Shell**, które będą przechowywane w zmiennej o nazwie **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="037bf-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="037bf-158">Get-Member działa z obiektami COM, dzięki czemu możesz zapoznać się z elementów członkowskich obiektu, wpisując:</span><span class="sxs-lookup"><span data-stu-id="037bf-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="037bf-159">**Get-Member** ma opcjonalny **InputObject** parametru zamiast przesyłanie potokowe umożliwia podanie danych wejściowych do **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="037bf-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="037bf-160">Takie same dane wyjściowe, jak pokazano powyżej, jeśli zamiast tego użyto polecenia otrzymamy **Get-Member — InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="037bf-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="037bf-161">Jeśli używasz **InputObject**, traktuje jej argument jako pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="037bf-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="037bf-162">Oznacza to, że jeśli masz kilka obiektów w zmiennej, **Get-Member** traktuje je jako tablica obiektów.</span><span class="sxs-lookup"><span data-stu-id="037bf-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="037bf-163">Przykład:</span><span class="sxs-lookup"><span data-stu-id="037bf-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="037bf-164">**CreateShortcut obiektu WScript.Shell** metoda przyjmuje jeden argument, a ścieżka do pliku skrótów do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="037bf-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="037bf-165">Firma Microsoft może wpisz pełną ścieżkę do programu desktop, ale jest łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="037bf-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="037bf-166">Pulpit jest zwykle reprezentowany przez folder o nazwie pulpitu bieżącego użytkownika w folderze głównym.</span><span class="sxs-lookup"><span data-stu-id="037bf-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="037bf-167">Program Windows PowerShell ma zmienną **$Home** zawierający ścieżkę do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="037bf-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="037bf-168">Możemy określić ścieżkę do folderu macierzystego przy użyciu tej zmiennej, a następnie dodaj nazwę folderu pulpitu i nazwy skrótu do tworzenia, wpisując:</span><span class="sxs-lookup"><span data-stu-id="037bf-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="037bf-169">Gdy używasz coś, co przypomina nazwę zmiennej w podwójne cudzysłowy, programu Windows PowerShell próbuje zastąpić o pasującej wartości.</span><span class="sxs-lookup"><span data-stu-id="037bf-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="037bf-170">Jeśli używasz jednego ofert, programu Windows PowerShell nie podejmuje próby podstawiania wartości zmiennej.</span><span class="sxs-lookup"><span data-stu-id="037bf-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="037bf-171">Na przykład wpisz następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="037bf-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="037bf-172">Teraz mamy zmienną o nazwie **$lnk** zawiera nowe odwołanie skrótów.</span><span class="sxs-lookup"><span data-stu-id="037bf-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="037bf-173">Jeśli chcesz wyświetlić jej elementów członkowskich, można przekazać go do **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="037bf-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="037bf-174">Danych wyjściowych poniżej przedstawiono elementy członkowskie, że należy wykonać, aby zakończyć tworzenie naszej skrótów:</span><span class="sxs-lookup"><span data-stu-id="037bf-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="037bf-175">Trzeba określić **TargetPath**, czyli do folderu aplikacji dla programu Windows PowerShell, a następnie Zapisz skrót **$lnk** przez wywołanie metody **Zapisz** metody.</span><span class="sxs-lookup"><span data-stu-id="037bf-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="037bf-176">Ścieżka folderu aplikacji programu Windows PowerShell jest przechowywana w zmiennej **$PSHome**, dzięki czemu możemy to zrobić, wpisując:</span><span class="sxs-lookup"><span data-stu-id="037bf-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="037bf-177">Za pomocą programu Internet Explorer w programie Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="037bf-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="037bf-178">Wiele aplikacji (w tym aplikacji i programu Internet Explorer z rodziny Microsoft Office) można zautomatyzować za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="037bf-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="037bf-179">Program Internet Explorer przedstawiono niektóre typowe techniki i zagadnieniach dotyczących pracy z aplikacji opartych na modelu COM.</span><span class="sxs-lookup"><span data-stu-id="037bf-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="037bf-180">Utwórz wystąpienie programu Internet Explorer, określając Internet Explorer ProgId, **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="037bf-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="037bf-181">To polecenie uruchamia program Internet Explorer, ale nie była widoczna.</span><span class="sxs-lookup"><span data-stu-id="037bf-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="037bf-182">Jeśli wpiszesz Get-Process, widać, że proces o nazwie iexplore działa.</span><span class="sxs-lookup"><span data-stu-id="037bf-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="037bf-183">W rzeczywistości Jeśli zakończysz programu Windows PowerShell, proces będzie kontynuował pracę.</span><span class="sxs-lookup"><span data-stu-id="037bf-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="037bf-184">Należy ponownie uruchomić komputer lub użyć narzędzia takie jak Menedżer zadań, aby zakończyć proces iexplore.</span><span class="sxs-lookup"><span data-stu-id="037bf-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="037bf-185">Często nazywane obiektami COM, które Uruchom jako oddzielne procesy *pliki wykonywalne ActiveX*, może, mogą nie być wyświetlane okno interfejsu użytkownika podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="037bf-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="037bf-186">Jeśli tworzenie okna, ale nie była widoczna, takich jak Internet Explorer, zazwyczaj przeniesie fokus na pulpit Windows i należy okna widoczne wchodzić w interakcje z nią.</span><span class="sxs-lookup"><span data-stu-id="037bf-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="037bf-187">Wpisując **$ie | Get-Member**, możesz wyświetlić właściwości i metody dla programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="037bf-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="037bf-188">Aby wyświetlić okno programu Internet Explorer, należy ustawić właściwość Visible $true, wpisując:</span><span class="sxs-lookup"><span data-stu-id="037bf-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="037bf-189">Następnie można przejść do określonego adresu sieci Web przy użyciu metody Nawigacja:</span><span class="sxs-lookup"><span data-stu-id="037bf-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="037bf-190">Korzystając z innymi członkami modelu obiektów programu Internet Explorer, istnieje możliwość pobrania zawartości tekstowej ze strony internetowej.</span><span class="sxs-lookup"><span data-stu-id="037bf-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="037bf-191">Następujące polecenie spowoduje wyświetlenie tekstu w formacie HTML w treści bieżącej strony sieci Web:</span><span class="sxs-lookup"><span data-stu-id="037bf-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="037bf-192">Aby zamknąć program Internet Explorer z wnętrza programu PowerShell, należy wywołać jej metodę Quit():</span><span class="sxs-lookup"><span data-stu-id="037bf-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="037bf-193">Spowoduje to wymuszenie go zamknąć.</span><span class="sxs-lookup"><span data-stu-id="037bf-193">This will force it to close.</span></span> <span data-ttu-id="037bf-194">$Ie zmiennej nie zawiera już prawidłowe odwołanie, mimo że nadal jest wyświetlany jako obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="037bf-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="037bf-195">Jeśli spróbujesz go używać, zostanie wyświetlony błąd automatyzacji:</span><span class="sxs-lookup"><span data-stu-id="037bf-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="037bf-196">Można usunąć pozostałe odwoływać przy użyciu polecenia, takie jak $ie = $null lub całkowicie usunąć zmienną, wpisując:</span><span class="sxs-lookup"><span data-stu-id="037bf-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="037bf-197">Nie istnieje dla tego, czy pliki wykonywalne ActiveX zamknąć lub będą nadal działać po usunięciu odwołanie do jednej wspólnej standard.</span><span class="sxs-lookup"><span data-stu-id="037bf-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="037bf-198">W zależności od okoliczności, takich jak tego, czy aplikacja jest widoczna, czy zmieniony dokument jest uruchomiona w nim i nawet tego, czy program Windows PowerShell jest nadal uruchomiona aplikacja może być lub może nie zakończyć.</span><span class="sxs-lookup"><span data-stu-id="037bf-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="037bf-199">Z tego powodu należy przetestować zachowanie po przerwaniu dla każdego pliku wykonywalnego, aby użyć w programie Windows PowerShell ActiveX.</span><span class="sxs-lookup"><span data-stu-id="037bf-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="037bf-200">Wyświetlanie ostrzeżeń dotyczących obiektów COM opakowane w ramach platformy .NET</span><span class="sxs-lookup"><span data-stu-id="037bf-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="037bf-201">W niektórych przypadkach obiekt COM może mieć skojarzone .NET Framework *otoka wywoływana w czasie wykonywania* lub RCW i spowoduje używane przez **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="037bf-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="037bf-202">Ponieważ zachowanie RCW może różnić się od zachowania normalnego obiektu COM **New-Object** ma **Strict** parametru ostrzegania o RCW dostępu.</span><span class="sxs-lookup"><span data-stu-id="037bf-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="037bf-203">Jeśli określisz **Strict** parametru i następnie utworzyć obiekt COM, który używa RCW, pojawi się komunikat ostrzegawczy:</span><span class="sxs-lookup"><span data-stu-id="037bf-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="037bf-204">Mimo, że obiekt nadal jest tworzony, zostanie wyświetlone ostrzeżenie, że nie jest standardowy obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="037bf-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>