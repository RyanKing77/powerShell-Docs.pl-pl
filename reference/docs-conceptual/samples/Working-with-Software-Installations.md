---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Praca z instalacjami oprogramowania
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686726"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="e430b-103">Praca z instalacjami oprogramowania</span><span class="sxs-lookup"><span data-stu-id="e430b-103">Working with Software Installations</span></span>

<span data-ttu-id="e430b-104">Aplikacje, które są przeznaczone do przy użyciu Instalatora Windows jest możliwy za pośrednictwem usługi WMI **klasy Win32_Product** klasy, ale nie wszystkie aplikacje używane obecnie za pomocą Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="e430b-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="e430b-105">Ponieważ Instalator Windows zapewnia najszerszą gamę standardowych technik do pracy z aplikacjami do zainstalowania, skupimy się przede wszystkim nad tymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="e430b-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="e430b-106">Aplikacje korzystające z Instalatora alternatywnego procedury ogólnie nie będzie zarządzany przez Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="e430b-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="e430b-107">Określone techniki pracy z tymi aplikacjami zależy od Instalatora oprogramowania i decyzje podjęte przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e430b-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="e430b-108">Aplikacje, które są instalowane przez skopiowanie plików aplikacji na komputerze, zwykle nie można zarządzać za pomocą techniki opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="e430b-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="e430b-109">Te aplikacje jako plików i folderów można zarządzać przy użyciu technik opisanych w sekcji "Praca z pliki i foldery".</span><span class="sxs-lookup"><span data-stu-id="e430b-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="e430b-110">Wyświetlanie listy aplikacji Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="e430b-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="e430b-111">Aby wyświetlić listę aplikacji, instalowane przy użyciu Instalatora Windows w systemie lokalnym lub zdalnym, użyj następującego prostego zapytania usługi WMI:</span><span class="sxs-lookup"><span data-stu-id="e430b-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="e430b-112">Aby wyświetlić wszystkie właściwości obiektu klasy Win32_Product do wyświetlenia, za pomocą parametru właściwości formatowania poleceń cmdlet, takich jak polecenia cmdlet Format-Lista wartości \* (wszystkie).</span><span class="sxs-lookup"><span data-stu-id="e430b-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="e430b-113">Alternatywnie można użyć **filtr Get-WmiObject** parametru, aby wybrać tylko Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="e430b-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="e430b-114">Ponieważ filtr używany w tym poleceniu jest filtr WMI, używa składni języka zapytań usługi WMI (WQL), nie składni programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e430b-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="e430b-115">Zamiast tego należy:</span><span class="sxs-lookup"><span data-stu-id="e430b-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="e430b-116">Należy zauważyć, że często znaki, takie jak spacje lub znaki równości, które mają specjalne znaczenie w programie Windows PowerShell kwerendy WQL.</span><span class="sxs-lookup"><span data-stu-id="e430b-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="e430b-117">Z tego powodu rozsądne jest zawsze wartość parametru filtru należy ująć w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="e430b-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="e430b-118">Można również użyć znaku ucieczki programu Windows PowerShell, początkowych (\`), chociaż nie może to poprawić czytelność.</span><span class="sxs-lookup"><span data-stu-id="e430b-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="e430b-119">Następujące polecenie jest odpowiednikiem poprzedniego polecenia i zwraca te same wyniki, ale używa początkowych jako znak ucieczki dla znaków specjalnych, zamiast cytowanie ciąg całej filtru.</span><span class="sxs-lookup"><span data-stu-id="e430b-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="e430b-120">Aby wyświetlić listę właściwości, które Cię interesują, należy użyć parametru właściwości formatowania poleceń cmdlet programu, aby wyświetlić listę odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="e430b-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="e430b-121">Na koniec można znaleźć tylko nazwy zainstalowanych aplikacji, prostą **całej Format** instrukcji upraszcza dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e430b-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="e430b-122">Mimo, że mamy kilka sposobów Przyjrzyj się aplikacji, które są używane Instalatora Windows podczas instalacji, firma Microsoft nie ma uwzględniane innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e430b-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="e430b-123">Większość standardowych aplikacji zarejestrowanie ich dezinstalatora Windows, firma Microsoft może pracować z tymi znajdując je lokalnie w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e430b-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="e430b-124">Wyświetlanie listy wszystkich do odinstalowania aplikacji</span><span class="sxs-lookup"><span data-stu-id="e430b-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="e430b-125">Mimo że nie ma gwarancji możliwości można znaleźć każdej aplikacji w systemie, istnieje możliwość znaleźć wszystkie programy z ofert wyświetlane w oknie dialogowym Dodaj lub usuń programy.</span><span class="sxs-lookup"><span data-stu-id="e430b-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="e430b-126">Dodaj lub usuń programy znajdzie te aplikacje w następującym kluczu rejestru:</span><span class="sxs-lookup"><span data-stu-id="e430b-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="e430b-127">**HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\odinstalować**.</span><span class="sxs-lookup"><span data-stu-id="e430b-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="e430b-128">Firma Microsoft można także sprawdzić ten klucz, aby znaleźć aplikacje.</span><span class="sxs-lookup"><span data-stu-id="e430b-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="e430b-129">Aby ułatwić wyświetlanie klucza Odinstaluj, firma Microsoft zamapuj dysk programu Windows PowerShell do tej lokalizacji rejestru:</span><span class="sxs-lookup"><span data-stu-id="e430b-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="e430b-130">**HKLM:** dysk jest mapowany do katalogu głównego **HKEY_LOCAL_MACHINE**, więc użyliśmy tego dysku w ścieżce klucza dezinstalacji.</span><span class="sxs-lookup"><span data-stu-id="e430b-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="e430b-131">Zamiast **HKLM:** można została określona ścieżka rejestru przy użyciu **HKLM** lub **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="e430b-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="e430b-132">Zaletą używania istniejącego dysku rejestru to, czy możemy użyć uzupełniania po naciśnięciu tabulatora do wypełnienia w nazwach kluczy, dzięki czemu firma Microsoft nie trzeba wpisywać ich.</span><span class="sxs-lookup"><span data-stu-id="e430b-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="e430b-133">W efekcie powstał dysk o nazwie "Odinstaluj", który może służyć do wyszukiwania szybki i wygodny sposób instalacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e430b-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="e430b-134">Możemy znaleźć liczba aplikacji zainstalowanych przez liczenie klucze rejestru w dezinstalacji: Dysk programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e430b-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="e430b-135">Firma Microsoft można wyszukiwać tej listy dalsze aplikacji za pomocą różnych technik, począwszy od **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="e430b-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="e430b-136">Aby uzyskać listę aplikacji i zapisywać je w **$UninstallableApplications** zmiennej, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e430b-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="e430b-137">Używamy długiej nazwy zmiennej tutaj dla przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="e430b-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="e430b-138">W rzeczywistości nie ma powodu używania długich nazwach.</span><span class="sxs-lookup"><span data-stu-id="e430b-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="e430b-139">Do nazwy zmiennych można używać uzupełniania po naciśnięciu tabulatora, można również użyć nazwy znaków 1 i 2 dla danej szybkości.</span><span class="sxs-lookup"><span data-stu-id="e430b-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="e430b-140">Dłużej, opisowe nazwy są najbardziej przydatne podczas tworzenia kodu do ponownego wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="e430b-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="e430b-141">Aby wyświetlić wartości wpisów rejestru w kluczach rejestru w ramach odinstalowywania, należy użyć metody GetValue kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="e430b-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="e430b-142">Wartość metody jest nazwę wpisu rejestru.</span><span class="sxs-lookup"><span data-stu-id="e430b-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="e430b-143">Na przykład można znaleźć nazwy wyświetlane aplikacje w kluczu dezinstalacji, należy użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e430b-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="e430b-144">Nie ma żadnej gwarancji, że te wartości są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="e430b-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="e430b-145">W poniższym przykładzie dwa elementy zainstalowane są wyświetlane jako "Windows Media Encoder Seria 9":</span><span class="sxs-lookup"><span data-stu-id="e430b-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="e430b-146">Instalowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e430b-146">Installing Applications</span></span>

<span data-ttu-id="e430b-147">Możesz użyć **klasy Win32_Product** klasy w celu zainstalowania pakietów Instalatora Windows, lokalnie i zdalnie.</span><span class="sxs-lookup"><span data-stu-id="e430b-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="e430b-148">W Windows Vista, Windows Server 2008 i nowszych wersjach systemu Windows do zainstalowania aplikacji, należy uruchomić program Windows PowerShell przy użyciu opcji "Uruchom jako administrator".</span><span class="sxs-lookup"><span data-stu-id="e430b-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="e430b-149">Podczas instalowania zdalnie, należy użyć ścieżkę sieciową Universal Naming Convention (UNC) do określenia ścieżki do pakietu msi, ponieważ w podsystemie WMI nie rozpoznaje ścieżki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e430b-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="e430b-150">Na przykład, aby zainstalować pakiet NewPackage.msi znajduje się w udziale sieciowym \\ \\AppServ\\dsp na komputerze zdalnym PC01, wpisz następujące polecenie w wierszu polecenia programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e430b-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="e430b-151">Aplikacje, które nie korzystają z technologii Instalatora Windows może mieć metody specyficzne dla aplikacji dostępnych dla automatycznego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="e430b-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="e430b-152">Aby ustalić, czy jest to metoda wdrażania automatyzacji, zapoznaj się z dokumentacją dla aplikacji lub zapoznaj się z dostawcą aplikacji, system pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="e430b-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="e430b-153">W niektórych przypadkach nawet wtedy, gdy dostawca aplikacji nie specjalnie projektowania aplikacji do automatyzacji instalacji Instalator producenta oprogramowania może mieć kilka technik związane z automatyzacją.</span><span class="sxs-lookup"><span data-stu-id="e430b-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="e430b-154">Usuwanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e430b-154">Removing Applications</span></span>

<span data-ttu-id="e430b-155">Usuwanie pakietu Instalatora Windows za pomocą programu Windows PowerShell działa w przybliżeniu taki sam sposób jak instalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="e430b-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="e430b-156">Oto przykład, który wybiera pakiet do odinstalowania, na podstawie jego nazwy; w niektórych przypadkach może być łatwiej filtrować za pomocą **Numer_identyfikacyjny**:</span><span class="sxs-lookup"><span data-stu-id="e430b-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="e430b-157">Usunięcie innych aplikacji nie jest to jednak takie proste, nawet wtedy, gdy jest wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="e430b-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="e430b-158">Znaleziono ciągi dezinstalacji wiersza polecenia dla tych aplikacji, dzięki możliwości wyodrębniania **UninstallString** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e430b-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="e430b-159">Ta metoda działa w dla aplikacji Instalatora Windows i starszych programów znajdujących się w kluczu dezinstalacji:</span><span class="sxs-lookup"><span data-stu-id="e430b-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="e430b-160">Dane wyjściowe można filtrować według nazwy wyświetlanej, jeśli chcesz:</span><span class="sxs-lookup"><span data-stu-id="e430b-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="e430b-161">Jednak te ciągi nie może być bezpośrednio można używać w wierszu polecenia programu Windows PowerShell bez wprowadzając pewne modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="e430b-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="e430b-162">Uaktualnianie aplikacji Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="e430b-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="e430b-163">Aby uaktualnić aplikację, musisz znać nazwę aplikacji i ścieżkę do pakietu uaktualnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e430b-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="e430b-164">Dzięki tym informacjom można uaktualnić aplikacji za pomocą jednego polecenia programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e430b-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```