---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Konfiguracje sesji usługi JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726550"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="19d34-103">Konfiguracje sesji usługi JEA</span><span class="sxs-lookup"><span data-stu-id="19d34-103">JEA Session Configurations</span></span>

<span data-ttu-id="19d34-104">Punkt końcowy usługi JEA jest zarejestrowany w systemie, tworząc i rejestrowanie w pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19d34-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="19d34-105">Konfiguracje sesji zdefiniować, kto może korzystać z punktu końcowego JEA i które role mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="19d34-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="19d34-106">Mogą również określać ustawienia globalne, które są stosowane do wszystkich użytkowników sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="19d34-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="19d34-107">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="19d34-107">Create a session configuration file</span></span>

<span data-ttu-id="19d34-108">Rejestrowanie punktu końcowego JEA, należy określić, jak ten punkt końcowy został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="19d34-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="19d34-109">Istnieje wiele opcji, należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="19d34-109">There are many options to consider.</span></span> <span data-ttu-id="19d34-110">Najważniejsze opcje są następujące:</span><span class="sxs-lookup"><span data-stu-id="19d34-110">The most important options are:</span></span>

- <span data-ttu-id="19d34-111">Kto ma dostęp do punktu końcowego JEA</span><span class="sxs-lookup"><span data-stu-id="19d34-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="19d34-112">Role można przypisać</span><span class="sxs-lookup"><span data-stu-id="19d34-112">Which roles they be assigned</span></span>
- <span data-ttu-id="19d34-113">Tożsamość usługi JEA używa w tle</span><span class="sxs-lookup"><span data-stu-id="19d34-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="19d34-114">Nazwa punktu końcowego usługi JEA</span><span class="sxs-lookup"><span data-stu-id="19d34-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="19d34-115">Te opcje są zdefiniowane w pliku danych programu PowerShell przy użyciu `.pssc` rozszerzenia znany jako plik konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19d34-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="19d34-116">Plik konfiguracji sesji można edytować za pomocą dowolnego edytora tekstów.</span><span class="sxs-lookup"><span data-stu-id="19d34-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="19d34-117">Uruchom następujące polecenie, aby utworzyć pusty szablon pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19d34-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="19d34-118">Tylko najbardziej typowe opcje konfiguracji są domyślnie dołączone w pliku szablonu.</span><span class="sxs-lookup"><span data-stu-id="19d34-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="19d34-119">Użyj `-Full` przełącznik, aby uwzględnić wszystkie ustawienia mające zastosowanie w wygenerowanym Współpracuje.</span><span class="sxs-lookup"><span data-stu-id="19d34-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="19d34-120">`-SessionType RestrictedRemoteServer` Pole wskazuje, że konfiguracja sesji jest używany przez usługi JEA do bezpiecznego zarządzania.</span><span class="sxs-lookup"><span data-stu-id="19d34-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="19d34-121">Sesje tego typu działają w **NoLanguage** tryb i mieć dostęp tylko do następujących domyślnych poleceń (i aliasy):</span><span class="sxs-lookup"><span data-stu-id="19d34-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="19d34-122">Clear-Host (zgodne ze specyfikacją, usuń zaznaczenie)</span><span class="sxs-lookup"><span data-stu-id="19d34-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="19d34-123">PSSession zakończenia (exsn, zakończenia)</span><span class="sxs-lookup"><span data-stu-id="19d34-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="19d34-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="19d34-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="19d34-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="19d34-125">Get-FormatData</span></span>
- <span data-ttu-id="19d34-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="19d34-126">Get-Help</span></span>
- <span data-ttu-id="19d34-127">(Środek) dla obiektu w miary</span><span class="sxs-lookup"><span data-stu-id="19d34-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="19d34-128">Wyewidencjonowanie i domyślne</span><span class="sxs-lookup"><span data-stu-id="19d34-128">Out-Default</span></span>
- <span data-ttu-id="19d34-129">Select-Object (wybór)</span><span class="sxs-lookup"><span data-stu-id="19d34-129">Select-Object (select)</span></span>

<span data-ttu-id="19d34-130">Żaden dostawca programu PowerShell są dostępne, podobnie jak wszelkie zewnętrznych programów (plików wykonywalnych i skryptów).</span><span class="sxs-lookup"><span data-stu-id="19d34-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="19d34-131">Aby uzyskać więcej informacji na temat trybów języka, zobacz [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="19d34-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="19d34-132">Wybierz tożsamość usługi JEA</span><span class="sxs-lookup"><span data-stu-id="19d34-132">Choose the JEA identity</span></span>

<span data-ttu-id="19d34-133">Za kulisami usługi JEA musi tożsamość (konto), aby używać podczas uruchamiania polecenia połączonych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="19d34-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="19d34-134">Należy zdefiniować tożsamości, które korzysta z technologii JEA w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="19d34-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="19d34-135">Konto wirtualne</span><span class="sxs-lookup"><span data-stu-id="19d34-135">Local Virtual Account</span></span>

<span data-ttu-id="19d34-136">Lokalnych kont wirtualnych są przydatne, gdy wszystkie role zdefiniowane dla punktu końcowego JEA są używane do zarządzania na komputerze lokalnym i konta administratora lokalnego jest wystarczająca do uruchomienia poleceń pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="19d34-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="19d34-137">Kont wirtualnych są tymczasowego konta, które są unikatowe dla określonego użytkownika i tylko ostatni czas trwania sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19d34-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="19d34-138">Na serwerze członkowskim lub stacji roboczej, kont wirtualnych należy na komputerze lokalnym **Administratorzy** grupy.</span><span class="sxs-lookup"><span data-stu-id="19d34-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="19d34-139">Na kontrolerze domeny usługi Active Directory kont wirtualnych należą do tej domeny **Administratorzy domeny** grupy.</span><span class="sxs-lookup"><span data-stu-id="19d34-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="19d34-140">Jeśli role zdefiniowane przez konfigurację sesji nie wymagają pełnymi uprawnieniami administracyjnymi, można określić grupy zabezpieczeń, do których będą należeć konta wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="19d34-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="19d34-141">Dla serwera członkowskiego lub stacji roboczej do określonych grup zabezpieczeń musi być grupy lokalne, a nie grupy z domeny.</span><span class="sxs-lookup"><span data-stu-id="19d34-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="19d34-142">Jeśli określono co najmniej jedną grupę zabezpieczeń konta wirtualnego nie jest przypisany do grupy administratorów lokalnego lub domeny.</span><span class="sxs-lookup"><span data-stu-id="19d34-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="19d34-143">Kont wirtualnych tymczasowo są przyznawane logowanie w trybie usługi w zasadach zabezpieczeń serwera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="19d34-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="19d34-144">Jeśli jeden z VirtualAccountGroups określone zostało już udzielone tego prawa w zasadach, pojedyncze konto wirtualnego nie jest już będą dodawane i usuwane z zasad.</span><span class="sxs-lookup"><span data-stu-id="19d34-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="19d34-145">Może to być przydatne w scenariuszach takich jak kontrolery domeny, w których poprawki, zasady zabezpieczeń kontrolera domeny są ściśle poddawane inspekcji.</span><span class="sxs-lookup"><span data-stu-id="19d34-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="19d34-146">To jest dostępna tylko w systemu Windows Server 2016 z listopada 2018 r lub nowszy pakiet zbiorczy i 2019 serwera systemu Windows za pomocą 2019 stycznia lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="19d34-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="19d34-147">Konto usługi zarządzane przez grupę</span><span class="sxs-lookup"><span data-stu-id="19d34-147">Group-managed service account</span></span>

<span data-ttu-id="19d34-148">Konto usługi zarządzane przez grupę (GMSA) jest odpowiedniej tożsamości do użycia podczas JEA użytkownicy potrzebują dostępu do zasobów sieciowych, takich jak udziały plików i usług sieci web.</span><span class="sxs-lookup"><span data-stu-id="19d34-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="19d34-149">Konta Gmsa zapewniają tożsamość domeny, który jest używany do uwierzytelniania przy użyciu zasobów na dowolnym komputerze w domenie.</span><span class="sxs-lookup"><span data-stu-id="19d34-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="19d34-150">Prawa, które zapewnia GMSA, są określane przez zasoby uzyskiwany jest dostęp.</span><span class="sxs-lookup"><span data-stu-id="19d34-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="19d34-151">Nie masz uprawnień administratora na wszystkich maszynach lub usługi, chyba że administrator usługi lub maszynowo ma jawnie przyznane uprawnienia te prawa do opcją GMSA</span><span class="sxs-lookup"><span data-stu-id="19d34-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="19d34-152">Konta Gmsa należy używać tylko w przypadku, gdy jest to konieczne:</span><span class="sxs-lookup"><span data-stu-id="19d34-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="19d34-153">Trudno wywodzić akcje użytkownika, korzystając z GMSA.</span><span class="sxs-lookup"><span data-stu-id="19d34-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="19d34-154">Każdy użytkownik udostępnia taką samą tożsamość Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="19d34-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="19d34-155">Należy przejrzeć zapisy sesji programu PowerShell i dzienniki, aby skorelować poszczególnych użytkowników z ich działania.</span><span class="sxs-lookup"><span data-stu-id="19d34-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="19d34-156">Opcją GMSA może mieć dostęp do wielu zasobów sieciowych, które użytkownik nawiązujący połączenie nie wymaga dostępu do.</span><span class="sxs-lookup"><span data-stu-id="19d34-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="19d34-157">Zawsze próbuje ograniczyć czynne uprawnienia w ramach sesji usługi JEA do wykonania zasadę najmniejszych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="19d34-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="19d34-158">Konta usług zarządzane przez grupę tylko są dostępne na komputerach przyłączonych do domeny, przy użyciu programu PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="19d34-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="19d34-159">Aby uzyskać więcej informacji na temat zabezpieczania sesji JEA temacie [zagadnienia dotyczące zabezpieczeń](security-considerations.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="19d34-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="19d34-160">Zapisy sesji</span><span class="sxs-lookup"><span data-stu-id="19d34-160">Session transcripts</span></span>

<span data-ttu-id="19d34-161">Zaleca się konfigurowania punktu końcowego JEA, aby automatycznie rejestrował transkrypcji sesje użytkowników.</span><span class="sxs-lookup"><span data-stu-id="19d34-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="19d34-162">Zapisy sesji programu PowerShell zawierają informacje o użytkownik nawiązujący połączenie Uruchom jako tożsamość przypisaną do nich, i polecenia są uruchamiane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="19d34-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="19d34-163">Może być przydatne do inspekcji zespołu, która musi wiedzieć, kto wprowadził zmianę określonych w systemie.</span><span class="sxs-lookup"><span data-stu-id="19d34-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="19d34-164">Aby skonfigurować transkrypcje automatyczne w pliku konfiguracji sesji, należy podać ścieżkę do folderu przechowywania transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="19d34-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="19d34-165">Zapisy są zapisywane w folderze przez **systemu lokalnego** konta, które wymaga dostępu odczytu i zapisu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="19d34-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="19d34-166">Użytkownicy standardowi powinna nie mają dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="19d34-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="19d34-167">Ogranicz liczbę administratorów zabezpieczeń, mających dostęp do inspekcji transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="19d34-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="19d34-168">Dysku użytkownika</span><span class="sxs-lookup"><span data-stu-id="19d34-168">User drive</span></span>

<span data-ttu-id="19d34-169">Połączenie użytkownicy potrzebują do kopiowania plików do / z punktu końcowego JEA, po włączeniu dysku użytkownika w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="19d34-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="19d34-170">Dysk użytkownika jest **PSDrive** który jest mapowany do unikatowego folderu dla każdego użytkownika nawiązującego połączenie.</span><span class="sxs-lookup"><span data-stu-id="19d34-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="19d34-171">Ten folder umożliwia użytkownikom do kopiowania plików do / z systemu bez udzielania dostępu do systemu plików pełnej lub udostępnianie dostawcy FileSystem.</span><span class="sxs-lookup"><span data-stu-id="19d34-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="19d34-172">Zawartość dysku użytkownika są trwałe dla wszystkich sesji, aby dopasować sytuacje, w którym mogą zostać przerwane połączenie sieciowe.</span><span class="sxs-lookup"><span data-stu-id="19d34-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="19d34-173">Domyślnie dysku użytkownika pozwala przechowywać maksymalnie 50MB danych dla poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="19d34-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="19d34-174">Można ograniczyć ilość danych, użytkownik może zużywać z *UserDriveMaximumSize* pola.</span><span class="sxs-lookup"><span data-stu-id="19d34-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="19d34-175">Jeśli nie chcesz, aby dane na dysku użytkownika były trwałe, można skonfigurować zaplanowane zadanie w systemie, aby automatycznie oczyścić folderu każdej nocy.</span><span class="sxs-lookup"><span data-stu-id="19d34-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="19d34-176">Dysku użytkownika jest dostępne tylko w programie PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="19d34-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="19d34-177">Aby uzyskać więcej informacji na temat PSDrives zobacz [dyski Zarządzanie PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="19d34-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="19d34-178">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="19d34-178">Role definitions</span></span>

<span data-ttu-id="19d34-179">Definicje ról w pliku konfiguracji sesji zdefiniować mapowanie **użytkowników** do **role**.</span><span class="sxs-lookup"><span data-stu-id="19d34-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="19d34-180">Każdego użytkownika lub grupy uwzględnione w tym polu jest uprawnienie do punktu końcowego JEA po jej zarejestrowaniu.</span><span class="sxs-lookup"><span data-stu-id="19d34-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="19d34-181">Każdy użytkownik lub grupa może być uwzględniany jako klucz w tablicy skrótów tylko raz, ale można przypisać wiele ról.</span><span class="sxs-lookup"><span data-stu-id="19d34-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="19d34-182">Nazwa możliwości roli powinna być nazwa pliku możliwości roli, bez `.psrc` rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="19d34-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="19d34-183">Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, uzyska dostęp do ról każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="19d34-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="19d34-184">Jeśli dwie role udzielić dostępu do tego samego polecenia cmdlet, restrykcyjny zestaw parametrów jest udzielany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="19d34-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="19d34-185">Podczas określania lokalnych użytkowników lub grupy w polu definicji roli, należy użyć nazwy komputera nie **localhost** ani symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="19d34-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="19d34-186">Sprawdź nazwę komputera, sprawdzając `$env:COMPUTERNAME` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="19d34-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="19d34-187">Kolejność wyszukiwania możliwości roli</span><span class="sxs-lookup"><span data-stu-id="19d34-187">Role capability search order</span></span>

<span data-ttu-id="19d34-188">Jak pokazano w powyższym przykładzie, możliwości roli odwołuje się nazwa podstawowa pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="19d34-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="19d34-189">Nazwa podstawowa pliku jest nazwa pliku bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="19d34-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="19d34-190">Jeśli wiele możliwości roli są dostępne w systemie o takiej samej nazwie, programu PowerShell używa jej kolejność wyszukiwania niejawne, aby wybrać plik możliwości skutecznego roli.</span><span class="sxs-lookup"><span data-stu-id="19d34-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="19d34-191">JEA jest **nie** udzielić dostępu do wszystkich plików możliwości rolę o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="19d34-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="19d34-192">Korzysta z technologii JEA `$env:PSModulePath` zmiennej środowiskowej, aby określić, które ścieżki do skanowania w poszukiwaniu plików możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="19d34-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="19d34-193">W ramach każdej z tych ścieżek JEA szuka prawidłowe moduły programu PowerShell, które zawierają podfolder "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="19d34-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="19d34-194">Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z programem Windows z funkcjami rola niestandardowa o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="19d34-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="19d34-195">Dla wszystkich innych nazw powoduje konflikt pierwszeństwo zależy od kolejności, w którym Windows wylicza pliki w katalogu.</span><span class="sxs-lookup"><span data-stu-id="19d34-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="19d34-196">Kolejność nie jest musi być znakiem alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="19d34-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="19d34-197">Pierwszy plik możliwości roli znaleziono, który jest zgodny z określonym nazwa jest używana jako użytkownik nawiązujący połączenie.</span><span class="sxs-lookup"><span data-stu-id="19d34-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="19d34-198">Ponieważ wyszukiwanie możliwości roli kolejność nie jest deterministyczna, jest **zdecydowanie zaleca się** czy możliwości roli mają unikatowych nazw plików.</span><span class="sxs-lookup"><span data-stu-id="19d34-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="19d34-199">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="19d34-199">Conditional access rules</span></span>

<span data-ttu-id="19d34-200">Wszyscy użytkownicy i grupy objęte **RoleDefinitions** pola automatycznie uzyskają dostęp do punktów końcowych JEA.</span><span class="sxs-lookup"><span data-stu-id="19d34-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="19d34-201">Zasady dostępu warunkowego pozwalają dostosować ten dostęp i Wymagaj od użytkowników należą do grup zabezpieczeń, które nie miały wpływu na role, do których masz przypisaną.</span><span class="sxs-lookup"><span data-stu-id="19d34-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="19d34-202">Jest to przydatne, gdy chcesz zintegrować to rozwiązanie do zarządzania uprzywilejowany dostęp just in time, uwierzytelnianie karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego za pomocą technologii JEA.</span><span class="sxs-lookup"><span data-stu-id="19d34-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="19d34-203">Zasady dostępu warunkowego są definiowane w polu RequiredGroups w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="19d34-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="19d34-204">Tam możesz podać hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do konstruowania reguły.</span><span class="sxs-lookup"><span data-stu-id="19d34-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="19d34-205">Poniżej przedstawiono kilka przykładów sposobu użycia tego pola:</span><span class="sxs-lookup"><span data-stu-id="19d34-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="19d34-206">Zasady dostępu warunkowego są tylko dostępne w programie PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="19d34-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="19d34-207">Inne właściwości</span><span class="sxs-lookup"><span data-stu-id="19d34-207">Other properties</span></span>

<span data-ttu-id="19d34-208">Pliki konfiguracji sesji można robić wszystko, co można zrobić plik możliwości roli, po prostu bez możliwości daje łączącego się użytkownikom dostęp do różnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="19d34-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="19d34-209">Jeśli chcesz umożliwić wszystkim użytkownikom dostępu do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="19d34-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="19d34-210">Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, należy uruchomić `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="19d34-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="19d34-211">Plik konfiguracji sesji testowania</span><span class="sxs-lookup"><span data-stu-id="19d34-211">Testing a session configuration file</span></span>

<span data-ttu-id="19d34-212">Możesz przetestować konfiguracji sesji przy użyciu [PSSessionConfigurationFile testu](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19d34-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="19d34-213">Zalecane jest, sprawdzić plik konfiguracji sesji, czy można ręcznie edytować `.pssc` pliku.</span><span class="sxs-lookup"><span data-stu-id="19d34-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="19d34-214">Testowanie gwarantuje, że składnia jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="19d34-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="19d34-215">W przypadku pliku konfiguracji sesji niepowodzenia tego testu nie można zarejestrować w systemie.</span><span class="sxs-lookup"><span data-stu-id="19d34-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="19d34-216">Przykładowy plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="19d34-216">Sample session configuration file</span></span>

<span data-ttu-id="19d34-217">Poniższy przykład pokazuje, jak utworzyć i zweryfikować konfigurację sesji dla usługi JEA.</span><span class="sxs-lookup"><span data-stu-id="19d34-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="19d34-218">Definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności.</span><span class="sxs-lookup"><span data-stu-id="19d34-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="19d34-219">Nie jest to wymagane, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="19d34-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="19d34-220">Aktualizowanie plików konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="19d34-220">Updating session configuration files</span></span>

<span data-ttu-id="19d34-221">Aby zmienić właściwości konfiguracji sesji, JEA, w tym mapowanie użytkowników do ról, należy najpierw [wyrejestrować](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="19d34-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="19d34-222">Następnie [ponownie zarejestrować](register-jea.md) JEA konfiguracji sesji przy użyciu pliku konfiguracji sesji zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="19d34-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="19d34-223">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="19d34-223">Next steps</span></span>

- [<span data-ttu-id="19d34-224">Rejestruj konfigurację usługi JEA</span><span class="sxs-lookup"><span data-stu-id="19d34-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="19d34-225">Role usługi JEA autora</span><span class="sxs-lookup"><span data-stu-id="19d34-225">Author JEA roles</span></span>](role-capabilities.md)
