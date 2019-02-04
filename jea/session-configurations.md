---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Konfiguracje sesji usługi JEA
ms.openlocfilehash: 1b598522d43b2c1a26a739a67cee5181b21a7c32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689127"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="adefc-103">Konfiguracje sesji usługi JEA</span><span class="sxs-lookup"><span data-stu-id="adefc-103">JEA Session Configurations</span></span>

> <span data-ttu-id="adefc-104">Dotyczy: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="adefc-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="adefc-105">Punkt końcowy usługi JEA jest zarejestrowany w systemie, tworząc i rejestrowanie pliku konfiguracji sesji programu PowerShell w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="adefc-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="adefc-106">Określenia konfiguracji sesji *kto* można używać punktu końcowego JEA i role, które będzie miał dostęp do.</span><span class="sxs-lookup"><span data-stu-id="adefc-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="adefc-107">Mogą również określać ustawienia globalne, które mają zastosowanie do użytkowników każdej roli w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="adefc-108">W tym temacie opisano, jak utworzyć plik konfiguracji sesji programu PowerShell i zarejestrować punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="adefc-109">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="adefc-109">Create a session configuration file</span></span>

<span data-ttu-id="adefc-110">Aby można było zarejestrować punkt końcowy usługi JEA, należy określić, jak skonfigurować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="adefc-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="adefc-111">Istnieje wiele opcji, należy wziąć pod uwagę w tym miejscu najważniejsze które bycia kto powinien mieć dostęp do punktu końcowego JEA, które role będzie ich można przypisać tożsamość usługi JEA użyje w sposób niewidoczny i co to jest nazwa punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="adefc-112">Te są definiowane w pliku konfiguracji sesji programu PowerShell, który plik danych programu PowerShell kończy się rozszerzeniem .pssc.</span><span class="sxs-lookup"><span data-stu-id="adefc-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="adefc-113">Aby utworzyć plik konfiguracji sesji szkielet dla punktów końcowych JEA, uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="adefc-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="adefc-114">Tylko najbardziej typowe opcje konfiguracji są domyślnie dołączone w szkielet pliku.</span><span class="sxs-lookup"><span data-stu-id="adefc-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="adefc-115">Użyj `-Full` przełącznik, aby uwzględnić wszystkie ustawienia mające zastosowanie w wygenerowanym Współpracuje.</span><span class="sxs-lookup"><span data-stu-id="adefc-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="adefc-116">Plik konfiguracji sesji można otworzyć w dowolnym edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="adefc-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="adefc-117">`-SessionType RestrictedRemoteServer` Pole wskazuje, używane przez usługi JEA do bezpiecznego zarządzania z konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="adefc-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="adefc-118">Sesje skonfigurowane w ten sposób będzie działał w [tryb NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) i może zawierać tylko następujące polecenia 8 domyślne (i aliasy) dostępne:</span><span class="sxs-lookup"><span data-stu-id="adefc-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="adefc-119">Clear-Host (zgodne ze specyfikacją, usuń zaznaczenie)</span><span class="sxs-lookup"><span data-stu-id="adefc-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="adefc-120">PSSession zakończenia (exsn, zakończenia)</span><span class="sxs-lookup"><span data-stu-id="adefc-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="adefc-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="adefc-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="adefc-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="adefc-122">Get-FormatData</span></span>
- <span data-ttu-id="adefc-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="adefc-123">Get-Help</span></span>
- <span data-ttu-id="adefc-124">(Środek) dla obiektu w miary</span><span class="sxs-lookup"><span data-stu-id="adefc-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="adefc-125">Wyewidencjonowanie i domyślne</span><span class="sxs-lookup"><span data-stu-id="adefc-125">Out-Default</span></span>
- <span data-ttu-id="adefc-126">Select-Object (wybór)</span><span class="sxs-lookup"><span data-stu-id="adefc-126">Select-Object (select)</span></span>

<span data-ttu-id="adefc-127">Żaden dostawca programu PowerShell są dostępne, podobnie jak wszelkie zewnętrznych programów (plików wykonywalnych, skryptów, itp.).</span><span class="sxs-lookup"><span data-stu-id="adefc-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="adefc-128">Istnieje kilka innych pól, które można skonfigurować dla sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="adefc-129">Zostały one omówione w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="adefc-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="adefc-130">Wybierz tożsamość usługi JEA</span><span class="sxs-lookup"><span data-stu-id="adefc-130">Choose the JEA identity</span></span>

<span data-ttu-id="adefc-131">Za kulisami usługi JEA musi tożsamość (konto), aby używać podczas uruchamiania polecenia połączonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="adefc-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="adefc-132">Możesz zdecydować, tożsamość usługi JEA zostaną użyte w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="adefc-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="adefc-133">Konto wirtualne</span><span class="sxs-lookup"><span data-stu-id="adefc-133">Local Virtual Account</span></span>

<span data-ttu-id="adefc-134">Jeśli role obsługiwane przez ten punkt końcowy usługi JEA są używane do zarządzania na komputerze lokalnym, a konto administratora lokalnego jest wystarczające do uruchomienia pomyślnie poleceń, należy skonfigurować usługi JEA do używania konta lokalnego wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="adefc-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="adefc-135">Kont wirtualnych są tymczasowego konta, które są unikatowe dla określonego użytkownika i tylko ostatni czas trwania sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adefc-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="adefc-136">Na serwerze członkowskim lub stacji roboczej, kont wirtualnych należy na komputerze lokalnym **Administratorzy** grupy i mieć dostęp do większości zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="adefc-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="adefc-137">Na kontrolerze domeny usługi Active Directory kont wirtualnych należą do tej domeny **Administratorzy domeny** grupy.</span><span class="sxs-lookup"><span data-stu-id="adefc-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="adefc-138">Role obsługiwane przez tę konfigurację sesji nie wymagają takiego szerokie uprawnienia, opcjonalnie możesz określić grupy zabezpieczeń, do których będą należeć konta wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="adefc-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="adefc-139">Dla serwera członkowskiego lub stacji roboczej do określonych grup zabezpieczeń musi być grupy lokalne, a nie grupy z domeny.</span><span class="sxs-lookup"><span data-stu-id="adefc-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="adefc-140">Gdy określona jest co najmniej jedną grupę zabezpieczeń, konta wirtualnej już nie będą należeć do grupy administratorów lokalnego lub domeny.</span><span class="sxs-lookup"><span data-stu-id="adefc-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```
> [!NOTE]
> <span data-ttu-id="adefc-141">Kont wirtualnych tymczasowo są przyznawane logowanie w trybie usługi w zasadach zabezpieczeń serwera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="adefc-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="adefc-142">Jeśli jeden z VirtualAccountGroups określone zostało już udzielone tego prawa w zasadach, pojedyncze konto wirtualnego nie jest już będą dodawane i usuwane z zasad.</span><span class="sxs-lookup"><span data-stu-id="adefc-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="adefc-143">Może to być przydatne w scenariuszach takich jak kontrolery domeny, w których poprawki, zasady zabezpieczeń kontrolera domeny są ściśle poddawane inspekcji.</span><span class="sxs-lookup"><span data-stu-id="adefc-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="adefc-144">To jest dostępna tylko w systemu Windows Server 2016 z listopada 2018 r lub nowszy pakiet zbiorczy i 2019 serwera systemu Windows za pomocą 2019 stycznia lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="adefc-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="adefc-145">Konto usługi zarządzane przez grupę</span><span class="sxs-lookup"><span data-stu-id="adefc-145">Group Managed Service Account</span></span>


<span data-ttu-id="adefc-146">W scenariuszach wymagających JEA użytkownikowi dostęp do zasobów sieciowych, takich jak innych maszyn lub usług sieci web konto usługi zarządzanych przez grupę (gMSA) jest bardziej odpowiednia tożsamość do użycia.</span><span class="sxs-lookup"><span data-stu-id="adefc-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="adefc-147">konta gMSA zapewniają tożsamość domeny, która może służyć do uwierzytelniania względem zasobów na dowolnym komputerze w domenie.</span><span class="sxs-lookup"><span data-stu-id="adefc-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="adefc-148">Prawa zapewnia konta gMSA, który jest określany przez zasoby uzyskujesz dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="adefc-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="adefc-149">Nie będziesz automatycznie mieć uprawnienia administratora na wszystkich maszynach lub usługi, chyba że administrator komputera/usługi ma jawnie przyznane uprawnienia konta gMSA uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="adefc-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="adefc-150">konta gMSA powinny być używane tylko podczas dostępu do zasobów sieciowych wymaganych kilka powodów:</span><span class="sxs-lookup"><span data-stu-id="adefc-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="adefc-151">Jest trudniejsze wywodzić akcje użytkownika, gdy przy użyciu konta gMSA, ponieważ każdy użytkownik udostępnia taką samą tożsamość Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="adefc-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="adefc-152">Należy zapoznać się z zapisy sesji programu PowerShell i dzienniki, aby skorelować użytkowników z ich działania.</span><span class="sxs-lookup"><span data-stu-id="adefc-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="adefc-153">Dane konta gMSA mogą mieć dostęp do wielu zasobów sieciowych, których należy użytkownik nawiązujący połączenie nie wymaga dostępu do.</span><span class="sxs-lookup"><span data-stu-id="adefc-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="adefc-154">Zawsze próbuje ograniczyć czynne uprawnienia w ramach sesji usługi JEA do wykonania zasadę najmniejszych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="adefc-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="adefc-155">Konta usług zarządzane przez grupę tylko są dostępne w programie Windows PowerShell 5.1 lub nowszej i na komputerach przyłączonych do domeny.</span><span class="sxs-lookup"><span data-stu-id="adefc-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="adefc-156">Więcej informacji na temat uruchamiania jako użytkownicy</span><span class="sxs-lookup"><span data-stu-id="adefc-156">More information about run as users</span></span>

<span data-ttu-id="adefc-157">Dodatkowe informacje na temat wykonywania jako tożsamości i jak mogą wziąć pod uwagę w zabezpieczenia sesji JEA znajdują się w [zagadnienia dotyczące zabezpieczeń](security-considerations.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="adefc-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="adefc-158">Zapisy sesji</span><span class="sxs-lookup"><span data-stu-id="adefc-158">Session transcripts</span></span>

<span data-ttu-id="adefc-159">Zalecane jest, aby skonfigurować plik konfiguracji usługi JEA sesji, aby automatycznie rejestrował transkrypcji sesje użytkowników.</span><span class="sxs-lookup"><span data-stu-id="adefc-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="adefc-160">Zapisy sesji programu PowerShell zawierają informacje o użytkownik nawiązujący połączenie Uruchom jako tożsamość przypisaną do nich, i polecenia są uruchamiane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="adefc-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="adefc-161">Może być przydatne do inspekcji zespołu, która musi wiedzieć, kto wykonał określonej zmiany w systemie.</span><span class="sxs-lookup"><span data-stu-id="adefc-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="adefc-162">Aby skonfigurować transkrypcje automatyczne w pliku konfiguracji sesji, należy podać ścieżkę do folderu przechowywania transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="adefc-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="adefc-163">Aby uniemożliwić użytkownikom modyfikowanie lub usuwanie żadnych danych, należy skonfigurować określonego folderu.</span><span class="sxs-lookup"><span data-stu-id="adefc-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="adefc-164">Zapisy są zapisywane w folderze, konto System lokalny, który wymaga dostępu odczytu i zapisu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="adefc-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="adefc-165">Użytkownicy standardowi nie powinny mieć dostępu do folderu, a ograniczony zestaw zabezpieczeń Administratorzy powinni mieć dostęp do inspekcji transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="adefc-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="adefc-166">Dysku użytkownika</span><span class="sxs-lookup"><span data-stu-id="adefc-166">User drive</span></span>

<span data-ttu-id="adefc-167">Połączenie użytkownicy muszą kopiować pliki z punktu końcowego JEA w celu uruchomienia polecenia, po włączeniu dysku użytkownika w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="adefc-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="adefc-168">Dysk użytkownika jest [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) który jest mapowany do unikatowego folderu dla każdego użytkownika nawiązującego połączenie.</span><span class="sxs-lookup"><span data-stu-id="adefc-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="adefc-169">Ten folder służy jako miejsce dla nich skopiować pliki z systemu, bez udzielania dostępu do systemu plików pełnej lub udostępnianie dostawcy FileSystem.</span><span class="sxs-lookup"><span data-stu-id="adefc-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="adefc-170">Zawartość dysku użytkownika są trwałe dla wszystkich sesji, aby dopasować sytuacje, w którym mogą zostać przerwane połączenie sieciowe.</span><span class="sxs-lookup"><span data-stu-id="adefc-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="adefc-171">Domyślnie dysku użytkownika pozwala przechowywać maksymalnie 50MB danych dla poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="adefc-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="adefc-172">Można ograniczyć ilość danych, użytkownik może zużywać z *UserDriveMaximumSize* pola.</span><span class="sxs-lookup"><span data-stu-id="adefc-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="adefc-173">Jeśli chcesz, aby dane na dysku użytkownika były trwałe, można skonfigurować zaplanowane zadanie w systemie, aby automatycznie oczyścić folderu każdej nocy.</span><span class="sxs-lookup"><span data-stu-id="adefc-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="adefc-174">Dysku użytkownika jest dostępne tylko w programie Windows PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="adefc-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="adefc-175">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="adefc-175">Role definitions</span></span>

<span data-ttu-id="adefc-176">Definicje ról w pliku konfiguracji sesji zdefiniować mapowanie *użytkowników* do *role*.</span><span class="sxs-lookup"><span data-stu-id="adefc-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="adefc-177">Każdego użytkownika lub grupy uwzględnione w tym polu będzie automatycznie otrzymuje uprawnienie do punktu końcowego JEA po jej zarejestrowaniu.</span><span class="sxs-lookup"><span data-stu-id="adefc-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="adefc-178">Każdy użytkownik lub grupa może być uwzględniany jako klucz w tablicy skrótów tylko raz, ale można przypisać wiele ról.</span><span class="sxs-lookup"><span data-stu-id="adefc-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="adefc-179">Nazwa możliwości roli powinna być nazwą pliku możliwości roli, bez rozszerzenia .psrc.</span><span class="sxs-lookup"><span data-stu-id="adefc-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="adefc-180">Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, uzyskują dostęp do ról każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="adefc-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="adefc-181">Jeśli dwie role udzielić dostępu do tego samego polecenia cmdlet, restrykcyjny zestaw parametrów zostaną przyznane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="adefc-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="adefc-182">Podczas określania lokalnych użytkowników lub grupy w polu definicji roli, należy użyć nazwy komputera (nie *localhost* lub *.*) przed ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="adefc-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="adefc-183">Sprawdź nazwę komputera, sprawdzając `$env:computername` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="adefc-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="adefc-184">Kolejność wyszukiwania możliwości roli</span><span class="sxs-lookup"><span data-stu-id="adefc-184">Role capability search order</span></span>
<span data-ttu-id="adefc-185">Jak pokazano w powyższym przykładzie, możliwości roli odwołuje się płaskiej nazwy (nazwa pliku bez rozszerzenia) pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="adefc-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="adefc-186">Jeśli wiele możliwości roli są dostępne w systemie o takiej samej nazwie prostego, programu PowerShell użyje jej kolejność wyszukiwania niejawne aby wybrać plik możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="adefc-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="adefc-187">Będzie ono **nie** udzielić dostępu do wszystkich plików możliwości rolę o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="adefc-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="adefc-188">Korzysta z technologii JEA `$env:PSModulePath` zmiennej środowiskowej, aby określić, które ścieżki do skanowania w poszukiwaniu plików możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="adefc-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="adefc-189">W ramach każdej z tych ścieżek JEA będzie szukał prawidłowe moduły programu PowerShell, które zawierają podfolder "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="adefc-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="adefc-190">Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z programem Windows z funkcjami rola niestandardowa o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="adefc-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="adefc-191">Wszystkie inne konflikty nazewnictwa pierwszeństwo zależy od kolejności, w którym Windows wylicza pliki w katalogu (nie musi być w kolejności alfabetycznej).</span><span class="sxs-lookup"><span data-stu-id="adefc-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="adefc-192">Pierwszy plik możliwości roli znaleziono żądany nazwa będzie używana dla użytkownik nawiązujący połączenie.</span><span class="sxs-lookup"><span data-stu-id="adefc-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="adefc-193">Ponieważ kolejność wyszukiwania funkcja ról nie jest jednoznaczny. gdy dwie lub więcej możliwości roli ma taką samą nazwę, jest **zdecydowanie zaleca się** zapewnienia możliwości roli mają unikatowe nazwy na swojej maszynie.</span><span class="sxs-lookup"><span data-stu-id="adefc-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="adefc-194">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="adefc-194">Conditional access rules</span></span>

<span data-ttu-id="adefc-195">Wszyscy użytkownicy i grupy w polu RoleDefinitions automatycznie uzyskają dostęp do punktów końcowych JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="adefc-196">Zasady dostępu warunkowego pozwalają dostosować ten dostęp i Wymagaj od użytkowników należą do grup zabezpieczeń, które nie wpływają na role, które są przypisane.</span><span class="sxs-lookup"><span data-stu-id="adefc-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="adefc-197">Może to być przydatne, jeśli chcesz zintegrować "dokładnie na czas" uprzywilejowany dostęp do rozwiązania do zarządzania, uwierzytelnianie karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego za pomocą technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="adefc-198">Zasady dostępu warunkowego są definiowane w polu RequiredGroups w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="adefc-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="adefc-199">Tam możesz podać hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do konstruowania reguły.</span><span class="sxs-lookup"><span data-stu-id="adefc-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="adefc-200">Poniżej przedstawiono kilka przykładów jak korzystać z tego pola:</span><span class="sxs-lookup"><span data-stu-id="adefc-200">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="adefc-201">Zasady dostępu warunkowego są tylko dostępne w programie Windows PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="adefc-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="adefc-202">Inne właściwości</span><span class="sxs-lookup"><span data-stu-id="adefc-202">Other properties</span></span>
<span data-ttu-id="adefc-203">Pliki konfiguracji sesji można robić wszystko, co można zrobić plik możliwości roli, po prostu bez możliwości daje łączącego się użytkownikom dostęp do różnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="adefc-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="adefc-204">Jeśli chcesz umożliwić wszystkim użytkownikom dostępu do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="adefc-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="adefc-205">Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, należy uruchomić `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="adefc-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="adefc-206">Plik konfiguracji sesji testowania</span><span class="sxs-lookup"><span data-stu-id="adefc-206">Testing a session configuration file</span></span>

<span data-ttu-id="adefc-207">Możesz przetestować konfiguracji sesji przy użyciu [PSSessionConfigurationFile testu](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="adefc-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="adefc-208">Zdecydowanie zaleca się przetestowanie pliku konfiguracji sesji, jeśli edytowano plik współpracuje ręcznie za pomocą edytora tekstów, aby upewnić się, że składnia jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="adefc-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="adefc-209">Jeśli plik konfiguracji sesji nie zakończy się pomyślnie tego testu, nie można pomyślnie można zarejestrować w systemie.</span><span class="sxs-lookup"><span data-stu-id="adefc-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="adefc-210">Przykładowy plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="adefc-210">Sample session configuration file</span></span>

<span data-ttu-id="adefc-211">Poniżej znajduje się pełny przykład przedstawiający sposób tworzenia i sprawdzania poprawności konfiguracji sesji dla usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="adefc-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="adefc-212">Należy pamiętać, że definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności.</span><span class="sxs-lookup"><span data-stu-id="adefc-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="adefc-213">Nie jest to wymagane, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="adefc-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="adefc-214">Aktualizowanie plików konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="adefc-214">Updating session configuration files</span></span>

<span data-ttu-id="adefc-215">Jeśli zachodzi potrzeba zmiany właściwości konfiguracji sesji, JEA, w tym mapowanie użytkowników do ról, musisz najpierw [wyrejestrować](register-jea.md#unregistering-jea-configurations) i [ponownie zarejestrować](register-jea.md) JEA konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="adefc-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="adefc-216">Gdy ponownie zarejestrować JEA konfiguracji sesji, użyj zaktualizowanych zawierający potrzebne zmiany pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adefc-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="adefc-217">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="adefc-217">Next steps</span></span>

- [<span data-ttu-id="adefc-218">Rejestruj konfigurację usługi JEA</span><span class="sxs-lookup"><span data-stu-id="adefc-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="adefc-219">Role usługi JEA autora</span><span class="sxs-lookup"><span data-stu-id="adefc-219">Author JEA roles</span></span>](role-capabilities.md)
