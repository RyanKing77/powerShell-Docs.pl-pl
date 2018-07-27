---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Ulepszenia wystarczający zakres administracji (JEA)
ms.openlocfilehash: 66cbacb78f8a365e9c8556c7c56b3c3525de7395
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267869"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Ulepszenia wystarczający zakres administracji (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Kopiowanie plików ograniczone do/z punktów końcowych JEA

Teraz możesz zdalnie skopiować plików do/z usługi JEA punktu końcowego i rest pewność, że użytkownik nawiązujący połączenie nie można po prostu skopiować *wszelkie* plików w systemie. Jest to możliwe, konfigurując pliku Współpracuje instalowanie dysku użytkownika łączenia się użytkowników. Dysk użytkownik jest nowy PSDrive, który jest unikatowy dla każdego użytkownika łączącego się i są utrwalane w sesjach. Gdy `Copy-Item` jest używany do kopiowania plików do lub z sesji JEA, jest ona ograniczona tylko zezwolić na dostęp do dysku użytkownika. Próby skopiuj pliki do innych PSDrive zakończy się niepowodzeniem.

Aby skonfigurować dysk użytkownika w pliku konfiguracji usługi JEA sesji, użyj następujące nowe pola:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Folder kopii dysku użytkownika zostanie utworzone po `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Aby korzystanie z dysku użytkownika i skopiuj pliki do/z punktu końcowego JEA skonfigurowany tak, aby udostępnić dysk użytkownika, użyj `-ToSession` i `-FromSession` parametrów w `Copy-Item`.

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

Następnie można napisać funkcji niestandardowych do przetwarzania danych przechowywanych w stacji użytkownika i należy je do użytkowników w pliku możliwości roli.

## <a name="support-for-group-managed-service-accounts"></a>Obsługa grupy usługi zarządzanej kont

W niektórych przypadkach zadania, które użytkownik musi wykonać w ramach sesji usługi JEA może być konieczne uzyskiwać dostęp do zasobów poza komputera lokalnego. Podczas sesji JEA jest skonfigurowany do używania konta wirtualnego, wszelkie próby uzyskania dostępu do tych zasobów pojawi się pochodzić z tożsamości komputera lokalnego, nie wirtualnego konta lub połączonego użytkownika. W TP5, uwzględniliśmy obsługę uruchamiania JEA w kontekście [konta usługi zarządzanego przez grupę](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), znacznie ułatwiając dostęp do zasobów sieciowych przy użyciu tożsamości domeny.

Aby skonfigurować sesję JEA uruchamiany w kontekście konta gMSA, należy użyć następujących nowy klucz w pliku Współpracuje:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Konta usług zarządzane przez grupę nie dają izolacji lub ograniczony zakres kont wirtualnych.
> Każdy użytkownik nawiązujący połączenie współużytkują ten sam tożsamości przez grupę, która może mieć uprawnień w całym przedsiębiorstwie. Ostrożność bardzo przy wybieraniu gMSA, a zawsze preferują kont wirtualnych, które są ograniczone do komputera lokalnego, jeśli jest to możliwe.

## <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

Technologia JEA jest doskonałym ograniczanie ktoś możliwościach gdy zostało podłączone do systemu, aby zarządzać, ale co, jeśli możesz również chcesz ograniczyć *podczas* ktoś można użyć technologii JEA? Dodano opcje konfiguracji w plikach konfiguracji sesji (.pssc) pozwala określić grupę zabezpieczeń, do których użytkownik musi należeć do ustanowienia sesji JEA. Może to być szczególnie przydatne, jeśli masz system tylko w czas (JIT) w danym środowisku i chcesz stworzyć podniesienia swoich uprawnień przed uzyskaniem dostępu do punktu końcowego JEA wysoce uprzywilejowanych użytkowników.

Nowy *RequiredGroups* polem w pliku Współpracuje umożliwia określenie logiki, aby określić, jeśli użytkownik może łączyć się JEA. Składa się z określania hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do konstruowania reguły. Poniżej przedstawiono kilka przykładów jak korzystać z tego pola:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Naprawiono: Kont wirtualnych są teraz obsługiwane w systemie Windows Server 2008 R2

W program WMF 5.1 można mogą teraz używać kont wirtualnych w systemie Windows Server 2008 R2, umożliwiając jednolitych konfiguracji i równoważności funkcji w systemie Windows Server 2008 R2 — 2016. Kont wirtualnych pozostają nieobsługiwane w przypadku korzystania z usługi JEA na Windows 7.