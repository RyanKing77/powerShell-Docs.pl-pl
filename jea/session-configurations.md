---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, programu powershell, zabezpieczeń"
title: Konfiguracje sesji JEA
ms.openlocfilehash: 0a8931ae15caf04a3639ab46f130e5f5b0498d8c
ms.sourcegitcommit: 0733db9a05e89e6a23f6b52b9edd784fcbe8beec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2017
---
# <a name="jea-session-configurations"></a><span data-ttu-id="4d4cc-103">Konfiguracje sesji JEA</span><span class="sxs-lookup"><span data-stu-id="4d4cc-103">JEA Session Configurations</span></span>

> <span data-ttu-id="4d4cc-104">Dotyczy: środowiska Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4d4cc-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4d4cc-105">Punkt końcowy JEA jest zarejestrowany w systemie przez utworzenie i zarejestrowanie plik konfiguracji sesji programu PowerShell w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="4d4cc-106">Określenia konfiguracji sesji *kto* można używać punktu końcowego JEA i role, które będą mają dostęp.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="4d4cc-107">Określają one ustawienia globalne, które są stosowane do użytkowników z dowolnej roli w sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="4d4cc-108">W tym temacie opisano, jak utworzyć plik konfiguracji sesji programu PowerShell i zarejestrować punkt końcowy JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="4d4cc-109">Utwórz plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="4d4cc-109">Create a session configuration file</span></span>

<span data-ttu-id="4d4cc-110">Aby można było zarejestrować punkt końcowy JEA, należy określić konfiguracji tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="4d4cc-111">Istnieje wiele opcji, należy wziąć pod uwagę w tym miejscu najważniejsze które są kto ma dostęp do punktu końcowego JEA, role będą one można przypisać tożsamość będzie JEA używają i jakie będą Nazwa punktu końcowego JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="4d4cc-112">Są one wszystkie zdefiniowane w pliku konfiguracji sesji programu PowerShell, który plik programu PowerShell danych kończy się rozszerzeniem .pssc.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="4d4cc-113">Aby utworzyć plik konfiguracji sesji szkielet dla punktów końcowych JEA, uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="4d4cc-114">Tylko najbardziej typowe opcje konfiguracji są domyślnie dołączone w pliku szkielet.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="4d4cc-115">Użyj `-Full` przełącznik, aby uwzględnić wszystkie ustawienia mające zastosowanie w wygenerowanym Współpracuje.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="4d4cc-116">Plik konfiguracji sesji można otworzyć w dowolnym edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="4d4cc-117">`-SessionType RestrictedRemoteServer` Pole wskazuje używany przez JEA bezpiecznego zarządzania z konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="4d4cc-118">Sesje skonfigurowane w ten sposób będzie działać w [tryb NoLanguage](https://technet.microsoft.com/en-us/library/dn433292.aspx) i może zawierać tylko następujące polecenia 8 domyślne (i aliasy) dostępne:</span><span class="sxs-lookup"><span data-stu-id="4d4cc-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/en-us/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="4d4cc-119">Wyczyść-Host (ze specyfikacją cls, wyczyść)</span><span class="sxs-lookup"><span data-stu-id="4d4cc-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="4d4cc-120">Zakończ-PSSession (exsn, zakończenia)</span><span class="sxs-lookup"><span data-stu-id="4d4cc-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="4d4cc-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="4d4cc-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="4d4cc-122">Klasy FormatData Get</span><span class="sxs-lookup"><span data-stu-id="4d4cc-122">Get-FormatData</span></span>
- <span data-ttu-id="4d4cc-123">Get-Help</span><span class="sxs-lookup"><span data-stu-id="4d4cc-123">Get-Help</span></span>
- <span data-ttu-id="4d4cc-124">Miara — obiekt (miary)</span><span class="sxs-lookup"><span data-stu-id="4d4cc-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="4d4cc-125">Domyślna wyjściowego</span><span class="sxs-lookup"><span data-stu-id="4d4cc-125">Out-Default</span></span>
- <span data-ttu-id="4d4cc-126">Select-Object (zaznacz)</span><span class="sxs-lookup"><span data-stu-id="4d4cc-126">Select-Object (select)</span></span>

<span data-ttu-id="4d4cc-127">Nie dostawcy programu PowerShell są dostępne, ani się, że wszystkie zewnętrzne programy (pliki wykonywalne, skrypty itp.).</span><span class="sxs-lookup"><span data-stu-id="4d4cc-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="4d4cc-128">Istnieje kilka innych pól, które można skonfigurować dla sesji JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="4d4cc-129">Zostały one omówione w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="4d4cc-130">Wybierz tożsamość JEA</span><span class="sxs-lookup"><span data-stu-id="4d4cc-130">Choose the JEA identity</span></span>

<span data-ttu-id="4d4cc-131">W tle JEA musi tożsamości (konto) do użycia podczas uruchamiania polecenia podłączonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="4d4cc-132">Możesz zdecydować, tożsamość JEA będzie używany w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="4d4cc-133">Lokalne konto wirtualne</span><span class="sxs-lookup"><span data-stu-id="4d4cc-133">Local Virtual Account</span></span>

<span data-ttu-id="4d4cc-134">Jeśli role obsługiwane przez ten punkt końcowy JEA są używane do zarządzania na komputerze lokalnym, a konto administratora lokalnego jest wystarczająca do uruchomienia polecenia, należy skonfigurować JEA się za pomocą konta lokalnego wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="4d4cc-135">Konta wirtualne są tymczasowego konta, które są unikatowe dla określonego użytkownika i tylko ostatni czas trwania sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="4d4cc-136">Na serwerze członkowskim lub stacji roboczej, kont wirtualnych należy na komputerze lokalnym **Administratorzy** grupy i mają dostęp do większości zasobów systemowych.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="4d4cc-137">Na kontrolerze domeny usługi Active Directory kont wirtualnych należą do tej domeny **Administratorzy domeny** grupy.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="4d4cc-138">Jeśli role obsługiwany przez konfigurację sesji nie wymagają takiego szerokie uprawnienia, opcjonalnie możesz określić grupy zabezpieczeń, do których będą należeć Konto wirtualne.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="4d4cc-139">Na serwerze członkowskim lub stacji roboczej do określonych grup zabezpieczeń musi być grup lokalnych nie grupy z domeny.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="4d4cc-140">Jeśli określona jest co najmniej jedną grupę zabezpieczeń konta wirtualnego będzie już należy do grupy administratorów lokalnego lub domeny.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="4d4cc-141">Konto usługi zarządzane przez grupę</span><span class="sxs-lookup"><span data-stu-id="4d4cc-141">Group Managed Service Account</span></span>


<span data-ttu-id="4d4cc-142">W scenariuszach wymagających JEA użytkownikowi dostęp do zasobów sieciowych, takich jak inne maszyny lub usługi sieci web konto usługi zarządzane przez grupę (gMSA) jest bardziej odpowiednia tożsamości do użycia.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="4d4cc-143">konta gMSA zapewniają tożsamość domeny, która może służyć do uwierzytelniania względem zasobów na dowolnym komputerze w domenie.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="4d4cc-144">Prawa zapewnia konto usługi zarządzane przez grupę, jest określany przez zasoby masz dostęp.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="4d4cc-145">Nie automatycznie ma prawa administratora na wszystkie maszyny lub usługi, chyba że administrator maszyny/usługi ma jawnie przyznane uprawnienia tego konta gMSA uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="4d4cc-146">konta gMSA należy używać tylko podczas dostępu do zasobów sieciowych są wymagane do kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="4d4cc-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="4d4cc-147">Jest trudniej wywodzić akcje użytkownika, gdy za pomocą konta gMSA, ponieważ każdy użytkownik udostępnia tej samej tożsamości Uruchom jako.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="4d4cc-148">Należy zapoznać się dzienniki służące do skorelowania użytkowników z ich działania i zapisy sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="4d4cc-149">Konta gMSA mogą mieć dostęp do wielu zasobów sieciowych, które użytkownik nawiązujący połączenie nie potrzebują dostępu do.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="4d4cc-150">Zawsze spróbuj ograniczyć czynnych uprawnień w sesji JEA postępuj zgodnie z zasadą najniższych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="4d4cc-151">Konta usług zarządzane przez grupę tylko są dostępne w programie Windows PowerShell 5.1 lub nowszej i na komputerach przyłączonych do domeny.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="4d4cc-152">Więcej informacji na temat uruchamiania jako użytkowników</span><span class="sxs-lookup"><span data-stu-id="4d4cc-152">More information about run as users</span></span>

<span data-ttu-id="4d4cc-153">Dodatkowe informacje na temat uruchamiania jako tożsamości i jak uwzględnić ich bezpieczeństwo sesji JEA znajdują się w [zagadnienia dotyczące zabezpieczeń](security-considerations.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="4d4cc-154">Zapisy sesji</span><span class="sxs-lookup"><span data-stu-id="4d4cc-154">Session transcripts</span></span>

<span data-ttu-id="4d4cc-155">Zalecane jest skonfigurowanie plik konfiguracji sesji JEA automatyczne rejestrowanie zapisy sesji użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="4d4cc-156">Zapisy sesji programu PowerShell zawierają informacje o użytkownik nawiązujący połączenie, Uruchom jako tożsamość przypisana, i polecenia uruchamiane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="4d4cc-157">Mogą być przydatne do inspekcji zespołu, który wymaga, aby zrozumieć, kto wykonał określonej zmiany do systemu.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="4d4cc-158">Aby skonfigurować automatyczne zapisu w pliku konfiguracji sesji, należy podać ścieżkę do folderu przechowywania zapisów.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="4d4cc-159">Określony folder należy skonfigurować tak, aby uniemożliwić użytkownikom modyfikacja lub usunięcie wszystkich danych w ramach tego.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="4d4cc-160">Zapisy są zapisywane w folderze przy użyciu konta systemu lokalnego, uprawnienia do odczytu i zapisu do katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="4d4cc-161">Użytkownicy standardowi powinien nie masz dostępu do folderu, a ograniczony zestaw zabezpieczeń Administratorzy powinni mieć dostęp do inspekcji zapisów.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="4d4cc-162">Stacji użytkownika</span><span class="sxs-lookup"><span data-stu-id="4d4cc-162">User drive</span></span>

<span data-ttu-id="4d4cc-163">Łączącego użytkownicy muszą do kopiowania plików z punktu końcowego JEA, aby można było uruchomić polecenie, po włączeniu dysku użytkownika w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="4d4cc-164">Dysk użytkownika jest [elementu PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) który jest mapowany do unikatowego folderu dla każdego użytkownika łączącego.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-164">The user drive is a [PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="4d4cc-165">Ten folder pełni miejsca, aby skopiować pliki z systemu, bez udzielania dostępu do systemu plików pełnego lub udostępnianie dostawcy FileSystem.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="4d4cc-166">Zawartość dysku użytkownika są trwałe między sesjami, aby zmieścił się w sytuacjach, w którym można przerwać połączenie sieciowe.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="4d4cc-167">Domyślnie dysku użytkownika umożliwia przechowywanie maksymalnie 50MB danych dla poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="4d4cc-168">Można ograniczyć ilość danych, które użytkownik może korzystać z *UserDriveMaximumSize* pola.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="4d4cc-169">Jeśli nie chcesz, aby dane na dysku użytkownika były trwałe, zaplanowane zadanie można skonfigurować w systemie, aby wyczyścić automatycznie folderze każdej nocy.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="4d4cc-170">Dysku użytkownika jest dostępne wyłącznie w programie Windows PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="4d4cc-171">Definicje ról</span><span class="sxs-lookup"><span data-stu-id="4d4cc-171">Role definitions</span></span>

<span data-ttu-id="4d4cc-172">Definicje ról w pliku konfiguracji sesji zdefiniować mapowanie *użytkowników* do *ról*.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="4d4cc-173">Każdy użytkownik lub grupa zawarte w tym polu będzie automatycznie mieć uprawnienie do punktu końcowego JEA gdy jest on zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="4d4cc-174">Każdy użytkownik lub grupa może być uwzględniana jako klucz w tablicy skrótów tylko raz, ale można przypisać wiele ról.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="4d4cc-175">Nazwa roli możliwości powinna być nazwa pliku możliwości roli, bez rozszerzenia .psrc.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="4d4cc-176">Jeśli użytkownik należy do więcej niż jednej grupy w definicji roli, otrzyma dostęp do poszczególnych ról.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="4d4cc-177">Jeśli dwie role udzielić dostępu do tych samych poleceń cmdlet, najbardziej ograniczająca zestaw parametrów zostaną przyznane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="4d4cc-178">Podczas określania lokalnych użytkowników lub grupy w polu definicji roli, należy użyć nazwy komputera (nie *localhost* lub *.*) przed ukośniku odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="4d4cc-179">Sprawdź nazwę komputera, sprawdzając `$env:computername` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="4d4cc-180">Kolejność wyszukiwania możliwości roli</span><span class="sxs-lookup"><span data-stu-id="4d4cc-180">Role capability search order</span></span>
<span data-ttu-id="4d4cc-181">Jak pokazano w przykładzie powyżej, możliwości roli odwołuje się płaskiej nazwy (nazwa pliku bez rozszerzenia) pliku możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="4d4cc-182">Jeśli wiele możliwości roli są dostępne w systemie o takiej samej nazwie prosty, programu PowerShell użyje ich kolejność niejawnego wyszukiwania i wybierz plik możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="4d4cc-183">Będzie on **nie** zapewniają dostęp do wszystkich plików możliwości Rola o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="4d4cc-184">Używa JEA `$env:PSModulePath` zmiennej środowiskowej, aby określić, które ścieżki do skanowania w poszukiwaniu plików możliwości roli.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="4d4cc-185">W każdej z tych ścieżek JEA będzie szukać prawidłowy moduły programu PowerShell zawierających podfolder "RoleCapabilities".</span><span class="sxs-lookup"><span data-stu-id="4d4cc-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="4d4cc-186">Podobnie jak w przypadku importowania modułów, JEA preferuje możliwości roli, które są dostarczane z systemem Windows do funkcji rola niestandardowa o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="4d4cc-187">Dla wszystkich innych konfliktów nazw pierwszeństwo jest określana przez kolejność, w którym system Windows wylicza pliki w katalogu (nie gwarantuje to w kolejności alfabetycznej).</span><span class="sxs-lookup"><span data-stu-id="4d4cc-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="4d4cc-188">Znaleziono plik możliwości roli, które odpowiadają żądaną nazwa będzie używana dla użytkownik nawiązujący połączenie.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="4d4cc-189">Ponieważ kolejność wyszukiwania możliwości rola nie jest deterministyczna, gdy dwie lub więcej możliwości Rola o tej samej nazwie, jest **zdecydowanie zalecane** zapewnienia możliwości roli mają unikatowe nazwy na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="4d4cc-190">Zasady dostępu warunkowego</span><span class="sxs-lookup"><span data-stu-id="4d4cc-190">Conditional access rules</span></span>

<span data-ttu-id="4d4cc-191">Wszyscy użytkownicy i grupy w polu RoleDefinitions automatycznie otrzymują dostęp do punktów końcowych JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="4d4cc-192">Zasady dostępu warunkowego umożliwiają uściślić dostęp i wymaganie od użytkowników należą do grup zabezpieczeń, które nie wpływają na role, które są przypisane.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="4d4cc-193">Może to być przydatne, jeśli chcesz zintegrować "tylko w czasie" uprzywilejowany dostęp do rozwiązania do zarządzania, uwierzytelnienie karty inteligentnej lub innego rozwiązania do uwierzytelniania wieloskładnikowego z JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="4d4cc-194">Zasady dostępu warunkowego są definiowane w polu RequiredGroups w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="4d4cc-195">Istnieje, możesz podać hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do utworzenia reguły.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="4d4cc-196">Oto kilka przykładów sposób korzystania z tego pola:</span><span class="sxs-lookup"><span data-stu-id="4d4cc-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="4d4cc-197">Zasady dostępu warunkowego są tylko dostępne w programie Windows PowerShell 5.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="4d4cc-198">Inne właściwości</span><span class="sxs-lookup"><span data-stu-id="4d4cc-198">Other properties</span></span>
<span data-ttu-id="4d4cc-199">Pliki konfiguracji sesji można również wszystkiego plik możliwości roli można wykonać, tylko bez możliwości daje łączącego użytkownikom dostęp do różnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="4d4cc-200">Jeśli chcesz zezwolić wszystkim użytkownikom dostępu do określonych poleceń cmdlet, funkcji lub dostawców, możesz to zrobić bezpośrednio w pliku konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="4d4cc-201">Aby uzyskać pełną listę obsługiwanych właściwości w pliku konfiguracji sesji, uruchom `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="4d4cc-202">Plik konfiguracji sesji testowania</span><span class="sxs-lookup"><span data-stu-id="4d4cc-202">Testing a session configuration file</span></span>

<span data-ttu-id="4d4cc-203">Można przetestować konfiguracji sesji przy użyciu [PSSessionConfigurationFile testu](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="4d4cc-204">Zdecydowanie zaleca się przetestowanie pliku konfiguracji sesji, edytując plik współpracuje ręcznie przy użyciu edytora tekstów, aby upewnić się, że składnia jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="4d4cc-205">Jeśli plik konfiguracji sesji tego testu nie zostały spełnione, nie można pomyślnie można zarejestrować w systemie.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="4d4cc-206">Przykładowy plik konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="4d4cc-206">Sample session configuration file</span></span>

<span data-ttu-id="4d4cc-207">Poniżej znajduje się pełny przykład przedstawiający sposób tworzenia i weryfikowanie konfiguracji sesji dla JEA.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="4d4cc-208">Należy pamiętać, że definicje ról są tworzone i przechowywane w `$roles` zmiennej dla wygody i czytelności.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="4d4cc-209">Nie jest wymagane w tym celu.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="4d4cc-210">Aktualizowanie plików konfiguracji sesji</span><span class="sxs-lookup"><span data-stu-id="4d4cc-210">Updating session configuration files</span></span>

<span data-ttu-id="4d4cc-211">Jeśli musisz zmienić właściwości konfiguracji sesji, JEA, w tym mapowanie użytkowników do ról, należy najpierw [wyrejestrować](register-jea.md#unregistering-jea-configurations) i [ponownie zarejestrować](register-jea.md) JEA konfiguracji sesji.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="4d4cc-212">Gdy ponownie zarejestrować JEA konfiguracji sesji, użyj zaktualizowane zawierającego odpowiednie zmiany pliku konfiguracji sesji programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d4cc-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4d4cc-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4d4cc-213">Next steps</span></span>

- [<span data-ttu-id="4d4cc-214">Rejestruj konfigurację JEA</span><span class="sxs-lookup"><span data-stu-id="4d4cc-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="4d4cc-215">Autor JEA ról</span><span class="sxs-lookup"><span data-stu-id="4d4cc-215">Author JEA roles</span></span>](role-capabilities.md)

