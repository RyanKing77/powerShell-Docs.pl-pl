---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: Praca z instalacjami oprogramowania
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 2078376a8be19c9ff8ecc44183eb89f14bc388ed
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-software-installations"></a><span data-ttu-id="1be4c-103">Praca z instalacjami oprogramowania</span><span class="sxs-lookup"><span data-stu-id="1be4c-103">Working with Software Installations</span></span>
<span data-ttu-id="1be4c-104">Aplikacje, które są przeznaczone do użycia Instalatora Windows jest możliwy za pośrednictwem usługi WMI **klasy Win32_Product** klasy, ale nie wszystkie aplikacje używane obecnie, używając Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="1be4c-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="1be4c-105">Ponieważ Instalator systemu Windows zapewnia szeroką gamą standardowych technik do pracy z aplikacjami można zainstalować, możemy koncentruje się przede wszystkim na te aplikacje.</span><span class="sxs-lookup"><span data-stu-id="1be4c-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="1be4c-106">Aplikacje używające Instalatora alternatywnego procedury zazwyczaj nie będą zarządzane przez Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="1be4c-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="1be4c-107">Określone techniki pracy z tymi aplikacjami zależy od Instalatora oprogramowania i decyzje podjęte przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1be4c-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="1be4c-108">Aplikacje zainstalowane przez kopiowanie plików aplikacji na komputerze, zwykle nie można zarządzać za pomocą techniki opisane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1be4c-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="1be4c-109">Te aplikacje, jak pliki i foldery można zarządzać za pomocą techniki opisane w sekcji "Praca z pliki i foldery".</span><span class="sxs-lookup"><span data-stu-id="1be4c-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="1be4c-110">Wyświetlanie listy aplikacji Instalatora systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1be4c-110">Listing Windows Installer Applications</span></span>
<span data-ttu-id="1be4c-111">Aby wyświetlić listę aplikacji zainstalowanych przy użyciu Instalatora Windows na komputerze lokalnym lub zdalnym, użyj następującego prostego zapytania usługi WMI:</span><span class="sxs-lookup"><span data-stu-id="1be4c-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="1be4c-112">Aby wyświetlić wszystkie właściwości obiektu klasy Win32_Product do wyświetlenia, użyj parametru właściwości formatowania poleceń cmdlet, takich jak polecenia cmdlet Format listy o wartości \* (wszystkie).</span><span class="sxs-lookup"><span data-stu-id="1be4c-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

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

<span data-ttu-id="1be4c-113">Można użyć **filtru Get-WmiObject** parametr, aby wybrać tylko Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="1be4c-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="1be4c-114">Ponieważ filtr używane w tym poleceniu jest filtr WMI, używa składni języka zapytań usługi WMI (WQL), nie składnię Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1be4c-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="1be4c-115">Zamiast tego należy:</span><span class="sxs-lookup"><span data-stu-id="1be4c-115">Instead,:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="1be4c-116">Należy pamiętać, że kwerendy WQL często Użyj znaków, takich jak spacji lub znaku równości, które mają specjalne znaczenie w programie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1be4c-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="1be4c-117">Z tego powodu rozsądne jest zawsze wartość parametru filtru należy ująć w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="1be4c-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="1be4c-118">Można również użyć znak ucieczki środowiska Windows PowerShell, backtick (\\`), ale nie może to poprawić czytelność.</span><span class="sxs-lookup"><span data-stu-id="1be4c-118">You can also use the Windows PowerShell escape character, a backtick (\\`), although it may not improve readability.</span></span> <span data-ttu-id="1be4c-119">Polecenie jest odpowiednikiem poprzedniego polecenia i zwraca wyniki, ale używa backtick ucieczki znaków specjalnych, zamiast zamykający ciąg filtru całego.</span><span class="sxs-lookup"><span data-stu-id="1be4c-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="1be4c-120">Aby wyświetlić listę tylko właściwości, które są potrzebne, użyj parametru właściwości formatowania poleceń cmdlet do żądanej właściwości listy.</span><span class="sxs-lookup"><span data-stu-id="1be4c-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

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

<span data-ttu-id="1be4c-121">Na koniec, aby znaleźć tylko nazwy zainstalowanych aplikacji, prosty **całej Format** instrukcji upraszcza dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1be4c-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="1be4c-122">Teraz mamy kilka sposobów, aby przyjrzeć się aplikacji, które są używane do instalacji Instalatora Windows, firma Microsoft ma być nie omówiono inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="1be4c-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="1be4c-123">Ponieważ większość standardowych aplikacji zarejestrować ich dezinstalatora z systemem Windows, firma Microsoft może współpracować z tymi lokalnie, znajdowanie je w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1be4c-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="1be4c-124">Wyświetlanie listy wszystkich do odinstalowania aplikacji</span><span class="sxs-lookup"><span data-stu-id="1be4c-124">Listing All Uninstallable Applications</span></span>
<span data-ttu-id="1be4c-125">Nie ma gwarantowane można znaleźć każdej aplikacji w systemie, ale istnieje możliwość znaleźć wszystkie programy z listy wyświetlanych w oknie dialogowym Dodaj lub usuń programy.</span><span class="sxs-lookup"><span data-stu-id="1be4c-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="1be4c-126">Dodaj lub usuń programy znajduje tych aplikacji w następującym kluczu rejestru:</span><span class="sxs-lookup"><span data-stu-id="1be4c-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="1be4c-127">**HKEY_LOCAL_MACHINE\\oprogramowania\\Microsoft\\Windows\\CurrentVersion\\odinstalować**.</span><span class="sxs-lookup"><span data-stu-id="1be4c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="1be4c-128">Omówione można również ten klucz, aby znaleźć aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1be4c-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="1be4c-129">Aby ułatwić wyświetlić klucz Odinstaluj, możemy Mapuj dysk programu Windows PowerShell do tej lokalizacji w rejestrze:</span><span class="sxs-lookup"><span data-stu-id="1be4c-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="1be4c-130">**HKLM:** stacja jest mapowana do katalogu głównego **HKEY_LOCAL_MACHINE**, przez co możemy użyć ścieżki do klucza Odinstaluj tego dysku.</span><span class="sxs-lookup"><span data-stu-id="1be4c-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="1be4c-131">Zamiast **HKLM:** można została określona ścieżka rejestru za pomocą **HKLM** lub **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="1be4c-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="1be4c-132">Zaletą korzystania z istniejącym dyskiem rejestru jest wypełnianie nazw kluczy, dlatego firma Microsoft nie trzeba wpisywać ich używanie uzupełniania po naciśnięciu tabulatora.</span><span class="sxs-lookup"><span data-stu-id="1be4c-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="1be4c-133">Mamy teraz dysk o nazwie "Odinstaluj", który może służyć do wyszukiwania szybko i wygodnie instalacje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1be4c-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="1be4c-134">Znaleźliśmy liczba zainstalowanych aplikacji liczbą kluczy rejestru dezinstalacji: dysk programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1be4c-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="1be4c-135">Firma Microsoft można wyszukiwać tej listy dodatkowe aplikacje za pomocą różnych technik, począwszy od **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="1be4c-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="1be4c-136">Aby uzyskać listę aplikacji i zapisać je w **$UninstallableApplications** zmiennej, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="1be4c-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="1be4c-137">Użyto długich nazwę zmiennej tutaj dla uzyskania przejrzystości.</span><span class="sxs-lookup"><span data-stu-id="1be4c-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="1be4c-138">W rzeczywistości nie ma ma powodu do użycia długie nazwy.</span><span class="sxs-lookup"><span data-stu-id="1be4c-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="1be4c-139">Do nazwy zmiennych mogą używać uzupełniania po naciśnięciu tabulatora, również można użyć nazwy znaków 1 i 2 dla danej szybkości.</span><span class="sxs-lookup"><span data-stu-id="1be4c-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="1be4c-140">Nazwy dłuższe, opisowe są najbardziej przydatne podczas tworzenia kodu do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="1be4c-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="1be4c-141">Aby wyświetlić wartości wpisów rejestru w kluczach rejestru, w obszarze dezinstalacji, należy użyć metody GetValue kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="1be4c-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="1be4c-142">Wartość metody jest nazwą wpisu rejestru.</span><span class="sxs-lookup"><span data-stu-id="1be4c-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="1be4c-143">Na przykład aby znaleźć nazwy wyświetlanej aplikacji w kluczu Odinstaluj, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="1be4c-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

<span data-ttu-id="1be4c-144">Nie ma żadnej gwarancji, że te wartości są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="1be4c-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="1be4c-145">W poniższym przykładzie dwa elementy zainstalowane są wyświetlane jako "Windows Media Encoder Seria 9":</span><span class="sxs-lookup"><span data-stu-id="1be4c-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="1be4c-146">Instalowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1be4c-146">Installing Applications</span></span>
<span data-ttu-id="1be4c-147">Można użyć **klasy Win32_Product** klasy instalowania pakietów Instalatora Windows lokalnie i zdalnie.</span><span class="sxs-lookup"><span data-stu-id="1be4c-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="1be4c-148">W systemie Windows Vista, Windows Server 2008 i nowszych wersjach systemu Windows Aby zainstalować aplikację, należy uruchomić środowiska Windows PowerShell przy użyciu opcji "Uruchom jako administrator".</span><span class="sxs-lookup"><span data-stu-id="1be4c-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="1be4c-149">Podczas instalowania zdalnie, należy użyć ścieżkę sieciową Universal Naming Convention (UNC) należy określić ścieżkę do pakietu msi, ponieważ w podsystemie WMI nie rozpoznaje ścieżki programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1be4c-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="1be4c-150">Na przykład, aby zainstalować pakiet NewPackage.msi znajduje się w udziale sieciowym \\ \\AppServ\\dsp na komputerze zdalnym PC01, wpisz następujące polecenie w wierszu polecenia programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1be4c-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="1be4c-151">Aplikacje, które nie korzystają z technologii Instalatora systemu Windows mogą mieć specyficzne dla aplikacji dostępne metody automatycznego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="1be4c-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="1be4c-152">Aby ustalić, czy jest to metoda automatyzacji wdrażania, zajrzyj do dokumentacji aplikacji lub zapoznaj się z dostawcą aplikacji, system pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="1be4c-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="1be4c-153">W niektórych przypadkach nawet wtedy, gdy z dostawcą aplikacji nie specjalnie projektowania aplikacji do automatyzacji instalacji Instalator producenta oprogramowania może mieć niektóre metody automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="1be4c-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="1be4c-154">Usuwanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1be4c-154">Removing Applications</span></span>
<span data-ttu-id="1be4c-155">Usuwanie pakietu Instalatora Windows za pomocą środowiska Windows PowerShell działa w przybliżeniu taki sam sposób jak instalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="1be4c-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="1be4c-156">Oto przykład, który wybiera pakietu do odinstalowania, na podstawie jego nazwy; w niektórych przypadkach może być łatwiejsze do filtrowania z **numerowi**:</span><span class="sxs-lookup"><span data-stu-id="1be4c-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="1be4c-157">Usunięcie inne aplikacje nie jest dość tak proste, nawet wtedy, gdy wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="1be4c-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="1be4c-158">Firma Microsoft można znaleźć ciągi dezinstalacji wiersza polecenia dla tych aplikacji, wyodrębniając **UninstallString** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1be4c-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="1be4c-159">Ta metoda działa w aplikacji Instalatora systemu Windows i starszych programów znajdujących się w kluczu dezinstalacji:</span><span class="sxs-lookup"><span data-stu-id="1be4c-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="1be4c-160">Dane wyjściowe można filtrować według nazwy wyświetlanej, jeśli chcesz:</span><span class="sxs-lookup"><span data-stu-id="1be4c-160">You can filter the output by the display name, if you like:</span></span>

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="1be4c-161">Jednak te ciągi nie może być bezpośrednio można używać z wierszu polecenia programu Windows PowerShell bez modyfikacji niektórych.</span><span class="sxs-lookup"><span data-stu-id="1be4c-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="1be4c-162">Uaktualnianie aplikacji Instalatora systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1be4c-162">Upgrading Windows Installer Applications</span></span>
<span data-ttu-id="1be4c-163">Aby uaktualnić aplikację, musisz znać nazwę aplikacji i ścieżkę do pakietu uaktualnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1be4c-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="1be4c-164">Z tych informacji można uaktualnić aplikację za pomocą jednego polecenia programu Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1be4c-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```

