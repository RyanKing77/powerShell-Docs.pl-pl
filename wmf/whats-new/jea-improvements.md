---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ulepszenia wystarczający zakres administracji (JEA)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856203"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="7efc3-103">Ulepszenia wystarczający zakres administracji (JEA)</span><span class="sxs-lookup"><span data-stu-id="7efc3-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="7efc3-104">Just Enough Administration to nowa funkcja programu WMF 5.0, która umożliwia administracji opartej na rolach za pomocą komunikacji zdalnej programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7efc3-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="7efc3-105">Rozszerza istniejącą infrastrukturę ograniczone punktu końcowego, umożliwiając użytkowników niebędących administratorami uruchamiać odpowiednie polecenia, skrypty i pliki wykonywalne jako administrator.</span><span class="sxs-lookup"><span data-stu-id="7efc3-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="7efc3-106">Dzięki temu można zmniejszyć liczbę pełną Administratorzy w danym środowisku i ulepszania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7efc3-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="7efc3-107">Kopiowanie plików ograniczone do/z punktów końcowych JEA</span><span class="sxs-lookup"><span data-stu-id="7efc3-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="7efc3-108">Można teraz zdalnie kopiować pliki do/z punktu końcowego JEA i mieć pewność, że użytkownik nawiązujący połączenie nie można po prostu skopiować *wszelkie* plików w systemie.</span><span class="sxs-lookup"><span data-stu-id="7efc3-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="7efc3-109">Jest to możliwe, konfigurując pliku Współpracuje instalowanie dysku użytkownika łączenia się użytkowników.</span><span class="sxs-lookup"><span data-stu-id="7efc3-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="7efc3-110">Dysk użytkownik jest nowy PSDrive, który jest unikatowy dla każdego użytkownika łączącego się i są utrwalane w sesjach.</span><span class="sxs-lookup"><span data-stu-id="7efc3-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="7efc3-111">Gdy `Copy-Item` jest używany do kopiowania plików do lub z sesji JEA, jest ona ograniczona tylko zezwolić na dostęp do dysku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7efc3-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="7efc3-112">Próby skopiuj pliki do innych PSDrive zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="7efc3-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="7efc3-113">Aby skonfigurować dysk użytkownika w pliku konfiguracji usługi JEA sesji, użyj następujące nowe pola:</span><span class="sxs-lookup"><span data-stu-id="7efc3-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="7efc3-114">Folder kopii dysku użytkownika zostanie utworzone po `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="7efc3-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="7efc3-115">Aby korzystanie z dysku użytkownika i skopiuj pliki do/z punktu końcowego JEA skonfigurowany tak, aby udostępnić dysk użytkownika, użyj `-ToSession` i `-FromSession` parametrów w `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="7efc3-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="7efc3-116">Następnie można napisać funkcji niestandardowych do przetwarzania danych przechowywanych w stacji użytkownika i należy je do użytkowników w pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="7efc3-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="7efc3-117">Obsługa grupy usługi zarządzanej kont</span><span class="sxs-lookup"><span data-stu-id="7efc3-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="7efc3-118">W niektórych przypadkach zadania, które użytkownik musi wykonać w ramach sesji usługi JEA może być konieczne uzyskiwać dostęp do zasobów poza komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="7efc3-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="7efc3-119">Podczas sesji JEA jest skonfigurowany do używania konta wirtualnego, wszelkie próby uzyskania dostępu do tych zasobów pojawi się pochodzić z tożsamości komputera lokalnego, nie wirtualnego konta lub połączonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7efc3-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="7efc3-120">W TP5, uwzględniliśmy obsługę uruchamiania JEA w kontekście [konta usługi zarządzanego przez grupę](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), znacznie ułatwiając dostęp do zasobów sieciowych przy użyciu tożsamości domeny.</span><span class="sxs-lookup"><span data-stu-id="7efc3-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="7efc3-121">Aby skonfigurować sesję JEA uruchamiany w kontekście konta gMSA, należy użyć następujących nowy klucz w pliku Współpracuje:</span><span class="sxs-lookup"><span data-stu-id="7efc3-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="7efc3-122">Konta usług zarządzane przez grupę nie dają izolacji lub ograniczony zakres kont wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="7efc3-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="7efc3-123">Każdy użytkownik nawiązujący połączenie współużytkują ten sam tożsamości przez grupę, która może mieć uprawnień w całym przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="7efc3-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="7efc3-124">Ostrożność bardzo przy wybieraniu gMSA, a zawsze preferują kont wirtualnych, które są ograniczone do komputera lokalnego, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7efc3-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="7efc3-125">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="7efc3-125">Conditional access policies</span></span>

<span data-ttu-id="7efc3-126">Technologia JEA jest doskonałym ograniczanie ktoś możliwościach gdy zostało podłączone do systemu, aby zarządzać, ale co, jeśli możesz również chcesz ograniczyć *podczas* ktoś można użyć technologii JEA?</span><span class="sxs-lookup"><span data-stu-id="7efc3-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="7efc3-127">Dodano opcje konfiguracji w plikach konfiguracji sesji (.pssc) pozwala określić grupę zabezpieczeń, do których użytkownik musi należeć do ustanowienia sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="7efc3-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="7efc3-128">Jest to szczególnie przydatne, jeśli masz system tylko w czas (JIT) w danym środowisku i chcesz stworzyć podniesienia swoich uprawnień przed uzyskaniem dostępu do punktu końcowego JEA wysoce uprzywilejowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="7efc3-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="7efc3-129">Nowy *RequiredGroups* polem w pliku Współpracuje umożliwia określenie logiki, aby określić, jeśli użytkownik może łączyć się JEA.</span><span class="sxs-lookup"><span data-stu-id="7efc3-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="7efc3-130">Składa się z określania hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do konstruowania reguły.</span><span class="sxs-lookup"><span data-stu-id="7efc3-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="7efc3-131">Poniżej przedstawiono kilka przykładów sposobu użycia tego pola:</span><span class="sxs-lookup"><span data-stu-id="7efc3-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="7efc3-132">Poprawiono: Kont wirtualnych są teraz obsługiwane w systemie Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="7efc3-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="7efc3-133">W program WMF 5.1 można mogą teraz używać kont wirtualnych w systemie Windows Server 2008 R2, umożliwiając jednolitych konfiguracji i równoważności funkcji w systemie Windows Server 2008 R2 — 2016.</span><span class="sxs-lookup"><span data-stu-id="7efc3-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="7efc3-134">Kont wirtualnych pozostają nieobsługiwane w przypadku korzystania z usługi JEA na Windows 7.</span><span class="sxs-lookup"><span data-stu-id="7efc3-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>