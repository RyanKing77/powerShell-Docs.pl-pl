---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Ulepszenia wystarczającego administracyjnej (JEA)
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="1cb5a-103">Ulepszenia wystarczającego administracyjnej (JEA)</span><span class="sxs-lookup"><span data-stu-id="1cb5a-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="1cb5a-104">Kopiowanie plików ograniczone z JEA punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="1cb5a-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="1cb5a-105">Teraz można zdalnie skopiuj pliki do/z JEA punktu końcowego i rest pewność, że użytkownik nawiązujący połączenie nie można skopiować tylko *żadnych* pliku w systemie.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="1cb5a-106">Jest to możliwe, konfigurując pliku Współpracuje instalowanie dysku użytkownika do łączenia użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="1cb5a-107">Stacja użytkownika jest nowego elementu PSDrive jest unikatowy dla każdego łączącego się użytkownika, który będzie się powtarzał między sesjami.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="1cb5a-108">Copy-Item używanego do kopiowania plików do lub z sesji JEA jest ograniczane tylko umożliwia dostęp do dysku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="1cb5a-109">Próby skopiuj pliki do innego elementu PSDrive zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="1cb5a-110">Aby skonfigurować dysk użytkownika w pliku konfiguracji sesji JEA, użyj pola nowe:</span><span class="sxs-lookup"><span data-stu-id="1cb5a-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="1cb5a-111">Folder kopii dysku użytkownika zostanie utworzona na `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="1cb5a-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="1cb5a-112">Aby korzystać z dysku użytkownika i skopiuj pliki do/z punktu końcowego JEA skonfigurowany tak, aby ujawnić stacji użytkownika, użyj `-ToSession` i `-FromSession` parametrów w elemencie kopiowania.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="1cb5a-113">Następnie można zapisać funkcji niestandardowych do przetwarzania danych przechowywanych na dysku użytkownika i udostępnić tych użytkowników w pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="1cb5a-114">Obsługa grupy zarządzania usługi kont</span><span class="sxs-lookup"><span data-stu-id="1cb5a-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="1cb5a-115">W niektórych przypadkach zadanie, które użytkownik musi wykonać w ramach sesji JEA może być konieczne uzyskiwać dostęp do zasobów poza komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="1cb5a-116">Podczas sesji JEA jest skonfigurowany do używania konta wirtualnego, wszelkie próby osiągnąć tych zasobów pojawi się pochodzą z tożsamości komputera lokalnego, nie konta wirtualnego lub podłączonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="1cb5a-117">W TP5, możemy włączono obsługę działających JEA w kontekście [grupy konta usługi zarządzanego przez] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), co znacznie ułatwia dostęp do zasobów sieciowych przy użyciu tożsamości domeny.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="1cb5a-118">Aby skonfigurować sesję JEA do uruchomienia w ramach konta gMSA, użyj następujących nowy klucz w pliku Współpracuje:</span><span class="sxs-lookup"><span data-stu-id="1cb5a-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="1cb5a-119">**Uwaga:** konta usług zarządzane przez grupę nie dają izolacji lub ograniczonym zakresie kont wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="1cb5a-120">Każdy użytkownik nawiązujący połączenie będzie udostępniać tej samej tożsamości gMSA, które mogą mieć uprawnienia w całym przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="1cb5a-121">Trzeba zwrócić szczególną uwagę podczas wybierania grupę, a zawsze wybierasz kont wirtualnych, które są ograniczone do komputera lokalnego, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="1cb5a-122">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="1cb5a-122">Conditional access policies</span></span>

<span data-ttu-id="1cb5a-123">JEA jest doskonałym rozwiązaniem ograniczanie ktoś czynności podłączeni już do systemu zarządzania, ale co zrobić, gdy zostanie również chcesz ograniczyć *podczas* osoba może użyć JEA?</span><span class="sxs-lookup"><span data-stu-id="1cb5a-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="1cb5a-124">Dodaliśmy opcje konfiguracji w plikach konfiguracji sesji (.pssc) pozwala określić grupę zabezpieczeń, do których użytkownik musi należeć w celu ustanowienia sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="1cb5a-125">Może to być szczególnie przydatne, jeśli masz system tylko w czasie (JIT) w danym środowisku i mają być użytkowników przed uzyskaniem dostępu do punktu końcowego JEA uprawnieniach podniesienie poziomu ich uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="1cb5a-126">Nowy *RequiredGroups* polem w pliku Współpracuje pozwala na określenie logiki, aby ustalić, czy użytkownik może łączyć się JEA.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="1cb5a-127">Składa się z określania hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do utworzenia reguły.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="1cb5a-128">Oto kilka przykładów sposób korzystania z tego pola:</span><span class="sxs-lookup"><span data-stu-id="1cb5a-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="1cb5a-129">Stały: Kont wirtualnych są teraz obsługiwane w systemie Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="1cb5a-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="1cb5a-130">W wersji 5.1 WMF jesteś teraz mogą używać kont wirtualnych w systemie Windows Server 2008 R2, włączanie konfiguracji spójne i parzystość funkcji w systemie Windows Server 2008 R2 — 2016.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="1cb5a-131">Kont wirtualnych pozostają nieobsługiwane, gdy przy użyciu JEA w systemie Windows 7.</span><span class="sxs-lookup"><span data-stu-id="1cb5a-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>
