---
ms.date: 06/03/2019
keywords: polecenia cmdlet programu PowerShell
title: Praca z instalacjami oprogramowania
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830300"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="6b8c9-103">Praca z instalacjami oprogramowania</span><span class="sxs-lookup"><span data-stu-id="6b8c9-103">Working with Software Installations</span></span>

<span data-ttu-id="6b8c9-104">Aplikacje, które są przeznaczone do przy użyciu Instalatora Windows jest możliwy za pośrednictwem usługi WMI **klasy Win32_Product** klasy, ale nie wszystkie aplikacje używane obecnie za pomocą Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="6b8c9-105">Zazwyczaj aplikacje korzystające z Instalatora alternatywnego procedury nie są zarządzane przez Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="6b8c9-106">Określone techniki pracy z tymi aplikacjami zależy od tego, Instalator oprogramowania i decyzje podjęte przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="6b8c9-107">Na przykład aplikacje zainstalowane przez kopiowanie plików do folderu na komputerze, zwykle nie można zarządzać za pomocą techniki opisane poniżej.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="6b8c9-108">Można zarządzać te aplikacje jako plików i folderów za pomocą procedur omówionych w [Praca z plikami i folderami](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="6b8c9-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="6b8c9-109">**Klasy Win32_Product** klasa nie jest zoptymalizowany pod kątem zapytań.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="6b8c9-110">Zapytań, które używają filtrów symboli wieloznacznych spowodować WMI w celu użycia dostawcy tożsamości usługi Zarządzanej wyliczyć wszystkich zainstalowanych produktów, a następnie przeanalizować pełną listę po kolei, aby obsłużyć filtru.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="6b8c9-111">To również inicjuje Sprawdzanie spójności tego pakietów zainstalowanych, weryfikowanie i naprawić instalację.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="6b8c9-112">Sprawdzanie poprawności jest procesem powolnym i może powodować błędy w dziennikach zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="6b8c9-113">Aby uzyskać więcej informacji, wyszukaj [artykuł bazy wiedzy 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="6b8c9-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="6b8c9-114">Wyświetlanie listy aplikacji Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="6b8c9-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="6b8c9-115">Aby wyświetlić listę aplikacji, instalowane przy użyciu Instalatora Windows w systemie lokalnym lub zdalnym, użyj następującego prostego zapytania usługi WMI:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="6b8c9-116">Aby wyświetlić wszystkie właściwości **klasy Win32_Product** obiektu do wyświetlenia, użyj **właściwości** parametru formatowania poleceń cmdlet, takich jak `Format-List` polecenia cmdlet, o wartości `*` (wszystkie).</span><span class="sxs-lookup"><span data-stu-id="6b8c9-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="6b8c9-117">Alternatywnie można użyć `Get-CimInstance` **filtru** parametru, aby wybrać tylko Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="6b8c9-118">Wartość **filtru** parametr używa składni języka zapytań usługi WMI (WQL), nie składni programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="6b8c9-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="6b8c9-120">Aby wyświetlić listę właściwości, które Cię interesują, należy użyć **właściwość** parametru formatowania poleceń cmdlet, aby wyświetlić listę odpowiednich właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="6b8c9-121">Wyświetlanie listy wszystkich do odinstalowania aplikacji</span><span class="sxs-lookup"><span data-stu-id="6b8c9-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="6b8c9-122">Większość standardowych aplikacji zarejestrować dezinstalatora za pomocą Windows, firma Microsoft może pracować z tymi znajdując je lokalnie w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="6b8c9-123">Nie ma gwarancji możliwości można znaleźć każdej aplikacji w systemie.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="6b8c9-124">Jednak istnieje możliwość znaleźć wszystkie programy, w których wyświetlane na listach zawartości **apletu Dodaj lub usuń programy**.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="6b8c9-125">**Dodaj lub usuń programy** znajdzie te aplikacje w następującym kluczu rejestru:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="6b8c9-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="6b8c9-127">Firma Microsoft, można sprawdzić ten klucz, aby znaleźć aplikacje.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-127">We can examine this key to find applications.</span></span> <span data-ttu-id="6b8c9-128">Aby ułatwić wyświetlanie klucza Odinstaluj, firma Microsoft mapowania dysku środowiska PowerShell do tej lokalizacji rejestru:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="6b8c9-129">W efekcie powstał dysk o nazwie "Odinstaluj:" można szybko i wygodnie poszukaj instalacje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="6b8c9-130">Możemy znaleźć liczba aplikacji zainstalowanych przez liczenie klucze rejestru w dezinstalacji: Dysk programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="6b8c9-131">Firma Microsoft można wyszukiwać tej listy dalsze aplikacji za pomocą różnych technik, począwszy od **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="6b8c9-132">Aby uzyskać listę aplikacji i zapisywać je w **$UninstallableApplications** zmiennej, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="6b8c9-133">Aby wyświetlić wartości wpisów rejestru w kluczach rejestru w ramach odinstalowywania, należy użyć metody GetValue kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="6b8c9-134">Wartość metody jest nazwę wpisu rejestru.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="6b8c9-135">Na przykład można znaleźć nazwy wyświetlane aplikacje w kluczu dezinstalacji, należy użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="6b8c9-136">Nie ma żadnej gwarancji, że te wartości są unikatowe.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="6b8c9-137">W poniższym przykładzie dwa elementy zainstalowane są wyświetlane jako "Windows Media Encoder Seria 9":</span><span class="sxs-lookup"><span data-stu-id="6b8c9-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a><span data-ttu-id="6b8c9-138">Instalowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6b8c9-138">Installing Applications</span></span>

<span data-ttu-id="6b8c9-139">Możesz użyć **klasy Win32_Product** klasy w celu zainstalowania pakietów Instalatora Windows, lokalnie i zdalnie.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="6b8c9-140">Aby zainstalować aplikację, należy uruchomić program PowerShell przy użyciu opcji "Uruchom jako administrator".</span><span class="sxs-lookup"><span data-stu-id="6b8c9-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="6b8c9-141">Podczas instalowania zdalnie, należy użyć ścieżkę sieciową Universal Naming Convention (UNC) do określenia ścieżki do pakietu msi, ponieważ w podsystemie WMI nie rozpoznaje ścieżki programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="6b8c9-142">Na przykład, aby zainstalować pakiet NewPackage.msi znajduje się w udziale sieciowym `\\AppServ\dsp` na komputerze zdalnym PC01, wpisz następujące polecenie w wierszu polecenia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="6b8c9-143">Aplikacje, które nie korzystają z technologii Instalatora Windows może mieć metody specyficzne dla aplikacji dla automatycznego wdrażania.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="6b8c9-144">Zapoznaj się z dokumentacją dla aplikacji lub zapoznaj się z dostawcą aplikacji, system pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="6b8c9-145">Usuwanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6b8c9-145">Removing Applications</span></span>

<span data-ttu-id="6b8c9-146">Usuwanie pakietu Instalatora Windows, przy użyciu programu PowerShell działa w przybliżeniu taki sam sposób jak instalowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="6b8c9-147">Oto przykład, który wybiera pakiet do odinstalowania, na podstawie jego nazwy; w niektórych przypadkach może być łatwiej filtrować za pomocą **Numer_identyfikacyjny**:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="6b8c9-148">Usunięcie innych aplikacji nie jest to jednak takie proste, nawet wtedy, gdy jest wykonywane lokalnie.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="6b8c9-149">Znaleziono ciągi dezinstalacji wiersza polecenia dla tych aplikacji, dzięki możliwości wyodrębniania **UninstallString** właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="6b8c9-150">Ta metoda działa w dla aplikacji Instalatora Windows i starszych programów znajdujących się w kluczu dezinstalacji:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="6b8c9-151">Dane wyjściowe można filtrować według nazwy wyświetlanej, jeśli chcesz:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="6b8c9-152">Jednak te ciągi mogą nie być bezpośrednio można używać z wiersz polecenia programu PowerShell bez modyfikacji niektórych.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="6b8c9-153">Uaktualnianie aplikacji Instalatora Windows</span><span class="sxs-lookup"><span data-stu-id="6b8c9-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="6b8c9-154">Aby uaktualnić aplikację, musisz znać nazwę aplikacji i ścieżkę do pakietu uaktualnienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b8c9-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="6b8c9-155">Dzięki tym informacjom można uaktualnić aplikacji za pomocą jednego polecenia programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6b8c9-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
