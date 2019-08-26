---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Konfiguracje sesji JEA
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017881"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="0895b-103">Konfiguracje sesji JEA</span><span class="sxs-lookup"><span data-stu-id="0895b-103">JEA Session Configurations</span></span>

<span data-ttu-id="0895b-104">Punkt końcowy JEA jest zarejestrowany w systemie przez utworzenie i zarejestrowanie pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0895b-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="0895b-105">Konfiguracje sesji definiują, kto może korzystać z punktu końcowego JEA i jakie role mają do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="0895b-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="0895b-106">Definiują one również ustawienia globalne, które mają zastosowanie do wszystkich użytkowników sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="0895b-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="0895b-107">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="0895b-107">Create a session configuration file</span></span>

<span data-ttu-id="0895b-108">Aby zarejestrować punkt końcowy JEA, należy określić sposób, w jaki ten punkt końcowy jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="0895b-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="0895b-109">Istnieje wiele opcji, które należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="0895b-109">There are many options to consider.</span></span> <span data-ttu-id="0895b-110">Najważniejsze są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="0895b-110">The most important options are:</span></span>

- <span data-ttu-id="0895b-111">Kto ma dostęp do punktu końcowego JEA</span><span class="sxs-lookup"><span data-stu-id="0895b-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="0895b-112">Które role są przypisane</span><span class="sxs-lookup"><span data-stu-id="0895b-112">Which roles they be assigned</span></span>
- <span data-ttu-id="0895b-113">Których tożsamości JEA używa w ramach okładek</span><span class="sxs-lookup"><span data-stu-id="0895b-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="0895b-114">Nazwa punktu końcowego JEA</span><span class="sxs-lookup"><span data-stu-id="0895b-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="0895b-115">Te opcje są zdefiniowane w pliku danych programu PowerShell z `.pssc` rozszerzeniem znanym jako plik konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0895b-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="0895b-116">Plik konfiguracji sesji można edytować przy użyciu dowolnego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="0895b-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="0895b-117">Uruchom następujące polecenie, aby utworzyć plik konfiguracji pustego szablonu.</span><span class="sxs-lookup"><span data-stu-id="0895b-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="0895b-118">W pliku szablonu domyślnie są zawarte tylko najczęściej używane opcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0895b-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="0895b-119">Użyj przełącznika `-Full` , aby uwzględnić wszystkie odpowiednie ustawienia w wygenerowanym PSSC.</span><span class="sxs-lookup"><span data-stu-id="0895b-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="0895b-120">`-SessionType RestrictedRemoteServer` Pole wskazuje, że konfiguracja sesji jest używana przez jea do bezpiecznego zarządzania.</span><span class="sxs-lookup"><span data-stu-id="0895b-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="0895b-121">Sesje tego typu działają w trybie **NoLanguage** i mają dostęp tylko do następujących poleceń domyślnych (i aliasów):</span><span class="sxs-lookup"><span data-stu-id="0895b-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="0895b-122">Clear-Host (CLS, Clear)</span><span class="sxs-lookup"><span data-stu-id="0895b-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="0895b-123">Exit-PSSession (exsn, Exit)</span><span class="sxs-lookup"><span data-stu-id="0895b-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="0895b-124">Get-Command (GCM)</span><span class="sxs-lookup"><span data-stu-id="0895b-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="0895b-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="0895b-125">Get-FormatData</span></span>
- <span data-ttu-id="0895b-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="0895b-126">Get-Help</span></span>
- <span data-ttu-id="0895b-127">Measure-Object (Measure)</span><span class="sxs-lookup"><span data-stu-id="0895b-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="0895b-128">Out — wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="0895b-128">Out-Default</span></span>
- <span data-ttu-id="0895b-129">Select-Object (Select)</span><span class="sxs-lookup"><span data-stu-id="0895b-129">Select-Object (select)</span></span>

<span data-ttu-id="0895b-130">Żaden dostawca programu PowerShell nie jest dostępny ani nie ma żadnych programów zewnętrznych (plików wykonywalnych ani skryptów).</span><span class="sxs-lookup"><span data-stu-id="0895b-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="0895b-131">Aby uzyskać więcej informacji na temat trybów języka, zobacz [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="0895b-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="0895b-132">Wybieranie tożsamości JEA</span><span class="sxs-lookup"><span data-stu-id="0895b-132">Choose the JEA identity</span></span>

<span data-ttu-id="0895b-133">W tle JEA potrzebuje tożsamości (konta) do użycia podczas uruchamiania poleceń połączonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0895b-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="0895b-134">Należy określić, której tożsamości JEA używać w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="0895b-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="0895b-135">Lokalne konto wirtualne</span><span class="sxs-lookup"><span data-stu-id="0895b-135">Local Virtual Account</span></span>

<span data-ttu-id="0895b-136">Lokalne konta wirtualne są przydatne, gdy wszystkie role zdefiniowane dla punktu końcowego JEA są używane do zarządzania komputerem lokalnym, a konto administratora lokalnego jest wystarczające do pomyślnego uruchomienia poleceń.</span><span class="sxs-lookup"><span data-stu-id="0895b-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="0895b-137">Konta wirtualne są kontami tymczasowymi, które są unikatowe dla określonego użytkownika i tylko przez czas trwania sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0895b-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="0895b-138">Na serwerze członkowskim lub stacji roboczej konta wirtualne należą do grupy **administratorów** komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0895b-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="0895b-139">Na kontrolerze domena usługi Active Directory konta wirtualne należą do grupy **Administratorzy domeny** domeny.</span><span class="sxs-lookup"><span data-stu-id="0895b-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="0895b-140">Jeśli role zdefiniowane przez konfigurację sesji nie wymagają pełnego uprawnienia administratora, można określić grupy zabezpieczeń, do których będzie należało konto wirtualne.</span><span class="sxs-lookup"><span data-stu-id="0895b-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="0895b-141">W przypadku serwera członkowskiego lub stacji roboczej określone grupy zabezpieczeń muszą być grupami lokalnymi, a nie grupami z domeny.</span><span class="sxs-lookup"><span data-stu-id="0895b-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="0895b-142">W przypadku określenia co najmniej jednej grupy zabezpieczeń konto wirtualne nie jest przypisane do grupy Administratorzy lokalni lub domeny.</span><span class="sxs-lookup"><span data-stu-id="0895b-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="0895b-143">Kontom wirtualnym tymczasowo przyznano Logowanie jako usługa bezpośrednio w zasadach zabezpieczeń serwera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="0895b-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="0895b-144">Jeśli jeden z określonych VirtualAccountGroups został już udzielony w zasadach, indywidualne konto wirtualne nie zostanie już dodane i usunięte z zasad.</span><span class="sxs-lookup"><span data-stu-id="0895b-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="0895b-145">Może to być przydatne w scenariuszach takich jak kontrolery domeny, w których zmiany zasad zabezpieczeń kontrolera domeny są ściśle poddawane inspekcji.</span><span class="sxs-lookup"><span data-stu-id="0895b-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="0895b-146">Jest to możliwe tylko w systemie Windows Server 2016 z pakietem zbiorczym z listopada 2018 lub nowszym oraz systemem Windows Server 2019 z pakietem zbiorczym z stycznia 2019 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="0895b-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="0895b-147">Konto usługi zarządzane przez grupę</span><span class="sxs-lookup"><span data-stu-id="0895b-147">Group-managed service account</span></span>

<span data-ttu-id="0895b-148">Konto usługi zarządzane przez grupę (GMSA) jest odpowiednią tożsamością używaną, gdy użytkownicy JEA muszą uzyskać dostęp do zasobów sieciowych, takich jak udziały plików i usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0895b-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="0895b-149">Kont gMSA zapewniają tożsamość domeny, która jest używana do uwierzytelniania za pomocą zasobów na dowolnym komputerze w domenie.</span><span class="sxs-lookup"><span data-stu-id="0895b-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="0895b-150">Prawa, które zapewnia GMSA, są określane przez zasoby, do których uzyskujesz dostęp.</span><span class="sxs-lookup"><span data-stu-id="0895b-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="0895b-151">Nie masz uprawnień administratora na żadnych maszynach lub usługach, chyba że administrator maszyny lub usługi jawnie udzielił tych praw do GMSA.</span><span class="sxs-lookup"><span data-stu-id="0895b-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="0895b-152">Kont gMSA powinny być używane tylko wtedy, gdy jest to konieczne:</span><span class="sxs-lookup"><span data-stu-id="0895b-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="0895b-153">Trudno jest śledzić działania z powrotem do użytkownika podczas korzystania z GMSA.</span><span class="sxs-lookup"><span data-stu-id="0895b-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="0895b-154">Każdy użytkownik ma tę samą tożsamość Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="0895b-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="0895b-155">Należy przejrzeć transkrypcje i dzienniki sesji programu PowerShell w celu skorelowania poszczególnych użytkowników z ich działaniami.</span><span class="sxs-lookup"><span data-stu-id="0895b-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="0895b-156">GMSA może mieć dostęp do wielu zasobów sieciowych, do których użytkownik łączący nie potrzebuje dostępu.</span><span class="sxs-lookup"><span data-stu-id="0895b-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="0895b-157">Zawsze należy próbować ograniczyć czynne uprawnienia w sesji JEA, aby były zgodne z zasadą najniższych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="0895b-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="0895b-158">Konta usług zarządzane przez grupę są dostępne tylko na komputerach przyłączonych do domeny przy użyciu programu PowerShell 5,1 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="0895b-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="0895b-159">Aby uzyskać więcej informacji na temat zabezpieczania sesji JEA, zobacz artykuł dotyczący [zagadnień dotyczących zabezpieczeń](security-considerations.md) .</span><span class="sxs-lookup"><span data-stu-id="0895b-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="0895b-160">Transkrypcje sesji</span><span class="sxs-lookup"><span data-stu-id="0895b-160">Session transcripts</span></span>

<span data-ttu-id="0895b-161">Zaleca się skonfigurowanie punktu końcowego JEA, aby automatycznie rejestrować transkrypcje sesji użytkowników.</span><span class="sxs-lookup"><span data-stu-id="0895b-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="0895b-162">Transkrypcje sesji programu PowerShell zawierają informacje o połączonym użytkowniku, przypisanej tożsamości Uruchom jako i poleceniach uruchamianych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0895b-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="0895b-163">Mogą być przydatne dla zespołu ds. inspekcji, który musi zrozumieć, kto wprowadził konkretną zmianę w systemie.</span><span class="sxs-lookup"><span data-stu-id="0895b-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="0895b-164">Aby skonfigurować automatyczne transkrypcję w pliku konfiguracji sesji, podaj ścieżkę do folderu, w którym powinny być przechowywane transkrypcje.</span><span class="sxs-lookup"><span data-stu-id="0895b-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="0895b-165">Transkrypcje są zapisywane w folderze przez konto **systemu lokalnego** , które wymaga dostępu do odczytu i zapisu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="0895b-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="0895b-166">Użytkownicy standardowi nie powinni mieć dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="0895b-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="0895b-167">Ogranicz liczbę administratorów zabezpieczeń, którzy mają dostęp do inspekcji transkrypcji.</span><span class="sxs-lookup"><span data-stu-id="0895b-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="0895b-168">Dysk użytkownika</span><span class="sxs-lookup"><span data-stu-id="0895b-168">User drive</span></span>

<span data-ttu-id="0895b-169">Jeśli łączący się użytkownicy muszą kopiować pliki do lub z punktu końcowego JEA, można włączyć dysk użytkownika w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="0895b-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="0895b-170">Dysk użytkownika to **PSDrive** , który jest mapowany do unikatowego folderu dla każdego łączącego się użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0895b-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="0895b-171">Ten folder umożliwia użytkownikom kopiowanie plików do lub z systemu bez udzielania im dostępu do pełnego systemu plików ani udostępniania dostawcy plików.</span><span class="sxs-lookup"><span data-stu-id="0895b-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="0895b-172">Zawartość dysku użytkownika jest trwała między sesjami, aby uwzględnić sytuacje, w których można przerwać łączność sieciową.</span><span class="sxs-lookup"><span data-stu-id="0895b-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="0895b-173">Domyślnie dysk użytkownika umożliwia przechowywanie maksymalnie 50 MB danych na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0895b-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="0895b-174">Można ograniczyć ilość danych, które użytkownik może wykorzystać w polu *UserDriveMaximumSize* .</span><span class="sxs-lookup"><span data-stu-id="0895b-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="0895b-175">Jeśli nie chcesz, aby dane na dysku użytkownika były trwałe, możesz skonfigurować zaplanowane zadanie w systemie, aby automatycznie czyścić folder w każdej nocy.</span><span class="sxs-lookup"><span data-stu-id="0895b-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="0895b-176">Dysk użytkownika jest dostępny tylko w programie PowerShell w wersji 5,1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0895b-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="0895b-177">Aby uzyskać więcej informacji na temat PSDrives, zobacz [Zarządzanie dyskami programu PowerShell](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="0895b-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="0895b-178">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="0895b-178">Role definitions</span></span>

<span data-ttu-id="0895b-179">Definicje ról w pliku konfiguracji sesji definiują mapowanie **użytkowników** do **ról**.</span><span class="sxs-lookup"><span data-stu-id="0895b-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="0895b-180">Każdy użytkownik lub Grupa uwzględniona w tym polu uzyskuje uprawnienia do punktu końcowego JEA, gdy jest on zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="0895b-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="0895b-181">Każdy użytkownik lub Grupa może być dołączana jako klucz w elemencie Hashtable tylko raz, ale można przypisać wiele ról.</span><span class="sxs-lookup"><span data-stu-id="0895b-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="0895b-182">Nazwa funkcji roli powinna być nazwą pliku możliwości roli bez `.psrc` rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="0895b-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="0895b-183">Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, uzyskuje dostęp do ról każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="0895b-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="0895b-184">Gdy dwie role udzielą dostępu do tych samych poleceń cmdlet, zestaw parametrów z największą liczbą jest przyznawany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="0895b-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="0895b-185">W przypadku określania lokalnych użytkowników lub grup w polu definicje ról należy użyć nazwy komputera, a nie od **localhost** lub symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="0895b-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="0895b-186">Nazwę komputera można sprawdzić, sprawdzając `$env:COMPUTERNAME` zmienną.</span><span class="sxs-lookup"><span data-stu-id="0895b-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="0895b-187">Kolejność wyszukiwania możliwości roli</span><span class="sxs-lookup"><span data-stu-id="0895b-187">Role capability search order</span></span>

<span data-ttu-id="0895b-188">Jak pokazano w powyższym przykładzie, możliwości roli są przywoływane przez podstawową nazwę pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="0895b-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="0895b-189">Nazwa podstawowa pliku to nazwa pliku bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="0895b-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="0895b-190">Jeśli w systemie jest dostępnych wiele możliwości roli o tej samej nazwie, program PowerShell użyje niejawnej kolejności wyszukiwania, aby wybrać skuteczny plik możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="0895b-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="0895b-191">JEA nie udziela dostępu do wszystkich plików możliwości roli o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="0895b-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="0895b-192">JEA używa `$env:PSModulePath` zmiennej środowiskowej w celu określenia ścieżek do skanowania dla plików możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="0895b-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="0895b-193">W ramach każdej z tych ścieżek JEA szuka prawidłowych modułów programu PowerShell zawierających podfolder "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="0895b-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="0895b-194">Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z systemem Windows, do możliwości roli niestandardowej o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="0895b-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="0895b-195">W przypadku wszystkich innych konfliktów nazewnictwa pierwszeństwo zależy od kolejności, w której system Windows wylicza pliki w katalogu.</span><span class="sxs-lookup"><span data-stu-id="0895b-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="0895b-196">Kolejność nie jest gwarantowana w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="0895b-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="0895b-197">Dla użytkownika łączącego jest używany pierwszy plik możliwości roli, który jest zgodny z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="0895b-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="0895b-198">Ponieważ kolejność wyszukiwania możliwości roli nie jest deterministyczna, **zdecydowanie** zalecamy, aby możliwości roli miały unikatowe nazwy plików.</span><span class="sxs-lookup"><span data-stu-id="0895b-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="0895b-199">Reguły dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="0895b-199">Conditional access rules</span></span>

<span data-ttu-id="0895b-200">Wszyscy użytkownicy i grupy uwzględnione w polu **RoleDefinitions** mają automatycznie udzielony dostęp do punktów końcowych jea.</span><span class="sxs-lookup"><span data-stu-id="0895b-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="0895b-201">Reguły dostępu warunkowego umożliwiają ograniczenie dostępu i wymaganie, aby użytkownicy należały do dodatkowych grup zabezpieczeń, które nie mają wpływu na role, do których są przypisane.</span><span class="sxs-lookup"><span data-stu-id="0895b-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="0895b-202">Jest to przydatne, gdy chcesz zintegrować rozwiązanie do zarządzania dostępem uprzywilejowanym w trybie just-in-Time, uwierzytelniania karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego z JEA.</span><span class="sxs-lookup"><span data-stu-id="0895b-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="0895b-203">Reguły dostępu warunkowego są zdefiniowane w polu RequiredGroups w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="0895b-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="0895b-204">Tam można podać tablicę skrótów (opcjonalnie zagnieżdżoną), która używa kluczy "i" i "lub" do konstruowania reguł.</span><span class="sxs-lookup"><span data-stu-id="0895b-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="0895b-205">Poniżej przedstawiono kilka przykładów użycia tego pola:</span><span class="sxs-lookup"><span data-stu-id="0895b-205">Here are some examples of how to use this field:</span></span>

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
> <span data-ttu-id="0895b-206">Reguły dostępu warunkowego są dostępne tylko w programie PowerShell w wersji 5,1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="0895b-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="0895b-207">Inne właściwości</span><span class="sxs-lookup"><span data-stu-id="0895b-207">Other properties</span></span>

<span data-ttu-id="0895b-208">Pliki konfiguracji sesji mogą również wykonywać wszystko, co może zrobić plik możliwości roli, bez możliwości nadawania użytkownikom dostępu do różnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="0895b-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="0895b-209">Jeśli chcesz zezwolić wszystkim użytkownikom na dostęp do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="0895b-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="0895b-210">Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, uruchom `Get-Help New-PSSessionConfigurationFile -Full`polecenie.</span><span class="sxs-lookup"><span data-stu-id="0895b-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="0895b-211">Testowanie pliku konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="0895b-211">Testing a session configuration file</span></span>

<span data-ttu-id="0895b-212">Konfigurację sesji można testować za pomocą polecenia cmdlet [test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) .</span><span class="sxs-lookup"><span data-stu-id="0895b-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="0895b-213">Zaleca się przetestowanie pliku konfiguracji sesji, jeśli `.pssc` plik został ręcznie edytowany.</span><span class="sxs-lookup"><span data-stu-id="0895b-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="0895b-214">Testowanie zapewnia poprawną składnię.</span><span class="sxs-lookup"><span data-stu-id="0895b-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="0895b-215">Jeśli ten test zakończy się niepowodzeniem, nie można zarejestrować go w systemie.</span><span class="sxs-lookup"><span data-stu-id="0895b-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="0895b-216">Przykładowy plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="0895b-216">Sample session configuration file</span></span>

<span data-ttu-id="0895b-217">Poniższy przykład pokazuje, jak utworzyć i zweryfikować konfigurację sesji dla JEA.</span><span class="sxs-lookup"><span data-stu-id="0895b-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="0895b-218">Definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności.</span><span class="sxs-lookup"><span data-stu-id="0895b-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="0895b-219">Nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="0895b-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="0895b-220">Aktualizowanie plików konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="0895b-220">Updating session configuration files</span></span>

<span data-ttu-id="0895b-221">Aby zmienić właściwości konfiguracji sesji JEA, z uwzględnieniem mapowania użytkowników do ról, należy wyrejestrować. [](register-jea.md#unregistering-jea-configurations)</span><span class="sxs-lookup"><span data-stu-id="0895b-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="0895b-222">Następnie [zarejestruj ponownie](register-jea.md) konfigurację sesji jea przy użyciu zaktualizowanego pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="0895b-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0895b-223">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="0895b-223">Next steps</span></span>

- [<span data-ttu-id="0895b-224">Rejestrowanie konfiguracji JEA</span><span class="sxs-lookup"><span data-stu-id="0895b-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="0895b-225">Tworzenie ról JEA</span><span class="sxs-lookup"><span data-stu-id="0895b-225">Author JEA roles</span></span>](role-capabilities.md)
