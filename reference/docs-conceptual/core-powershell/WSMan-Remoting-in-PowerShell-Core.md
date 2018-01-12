# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="77452-101">Komunikacji zdalnej usługi WS-Management (WSMan) w podstawowej programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="77452-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span> 

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="77452-102">Instrukcje dotyczące tworzenia punktu końcowego usługi zdalne</span><span class="sxs-lookup"><span data-stu-id="77452-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="77452-103">Pakiet podstawowy programu PowerShell dla systemu Windows zawiera usługę WinRM, wtyczki (`pwrshplugin.dll`) i skrypt instalacji (`Install-PowerShellRemoting.ps1`) w `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="77452-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="77452-104">Te pliki umożliwiają programu PowerShell do akceptowania przychodzących połączeń zdalnych programu PowerShell, jeśli nie określono punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="77452-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="77452-105">Motywacją</span><span class="sxs-lookup"><span data-stu-id="77452-105">Motivation</span></span>

<span data-ttu-id="77452-106">Instalacja programu PowerShell mogą nawiązywać sesje programu PowerShell do komputerów zdalnych przy użyciu `New-PSSession` i `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="77452-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="77452-107">Aby włączyć ją do akceptowania przychodzących połączeń zdalnych programu PowerShell, użytkownik musi utworzyć punkt końcowy komunikacji zdalnej usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="77452-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="77452-108">Jest to jawne opcjonalnych scenariusz użytkownika, w którym odbywa się PowerShellRemoting.ps1 instalacji można utworzyć punktu końcowego usługi WinRM.</span><span class="sxs-lookup"><span data-stu-id="77452-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="77452-109">Skrypt instalacji to rozwiązanie krótkoterminowej do chwili dodania dodatkowych funkcji do `Enable-PSRemoting` do wykonania tego samego działania.</span><span class="sxs-lookup"><span data-stu-id="77452-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="77452-110">Aby uzyskać więcej informacji, zobacz problem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="77452-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="77452-111">Akcje skryptu</span><span class="sxs-lookup"><span data-stu-id="77452-111">Script Actions</span></span>

<span data-ttu-id="77452-112">Skrypt</span><span class="sxs-lookup"><span data-stu-id="77452-112">The script</span></span>

1. <span data-ttu-id="77452-113">Tworzy katalog dla wtyczki w %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="77452-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="77452-114">Kopiuje pwrshplugin.dll do tej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="77452-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="77452-115">Generuje plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="77452-115">Generates a configuration file</span></span>
1. <span data-ttu-id="77452-116">Rejestruje to wtyczka z usługi WinRM</span><span class="sxs-lookup"><span data-stu-id="77452-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="77452-117">Rejestracji</span><span class="sxs-lookup"><span data-stu-id="77452-117">Registration</span></span>

<span data-ttu-id="77452-118">Skrypt musi zostać wykonana w sesji programu PowerShell poziomie administratora i działa w dwóch trybach.</span><span class="sxs-lookup"><span data-stu-id="77452-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="77452-119">Wykonane przez to wystąpienie programu PowerShell, który zarejestruje</span><span class="sxs-lookup"><span data-stu-id="77452-119">Executed by the instance of PowerShell that it will register</span></span>

``` powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="77452-120">Wykonywane przez inne wystąpienie programu PowerShell w imieniu wystąpienie, które zarejestruje</span><span class="sxs-lookup"><span data-stu-id="77452-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

``` powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="77452-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="77452-121">For Example:</span></span>

``` powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="77452-122">**Uwaga:** skryptu rejestracji komunikacji zdalnej uruchomi WinRM, więc wszystkie istniejące sesje PSRP zostanie zakończona natychmiast po uruchomieniu skryptu.</span><span class="sxs-lookup"><span data-stu-id="77452-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="77452-123">Jeśli uruchomiony podczas sesji zdalnej, to spowoduje przerwanie połączenia.</span><span class="sxs-lookup"><span data-stu-id="77452-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="77452-124">Łączenie z nowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="77452-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="77452-125">Utwórz sesję programu PowerShell do nowego punktu końcowego programu PowerShell, określając `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="77452-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="77452-126">Aby połączyć się z wystąpieniem programu PowerShell w powyższym przykładzie, użyj jednej:</span><span class="sxs-lookup"><span data-stu-id="77452-126">To connect to the PowerShell instance from the example above, use either:</span></span>

``` powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="77452-127">Należy pamiętać, że `New-PSSession` i `Enter-PSSession` wywołań, które nie określają `-ConfigurationName` będzie obowiązywać domyślny punkt końcowy programu PowerShell, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="77452-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>
