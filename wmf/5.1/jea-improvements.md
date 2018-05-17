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
# <a name="improvements-to-just-enough-administration-jea"></a>Ulepszenia wystarczającego administracyjnej (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Kopiowanie plików ograniczone z JEA punkty końcowe

Teraz można zdalnie skopiuj pliki do/z JEA punktu końcowego i rest pewność, że użytkownik nawiązujący połączenie nie można skopiować tylko *żadnych* pliku w systemie.
Jest to możliwe, konfigurując pliku Współpracuje instalowanie dysku użytkownika do łączenia użytkowników.
Stacja użytkownika jest nowego elementu PSDrive jest unikatowy dla każdego łączącego się użytkownika, który będzie się powtarzał między sesjami.
Copy-Item używanego do kopiowania plików do lub z sesji JEA jest ograniczane tylko umożliwia dostęp do dysku użytkownika.
Próby skopiuj pliki do innego elementu PSDrive zakończy się niepowodzeniem.

Aby skonfigurować dysk użytkownika w pliku konfiguracji sesji JEA, użyj pola nowe:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Folder kopii dysku użytkownika zostanie utworzona na `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Aby korzystać z dysku użytkownika i skopiuj pliki do/z punktu końcowego JEA skonfigurowany tak, aby ujawnić stacji użytkownika, użyj `-ToSession` i `-FromSession` parametrów w elemencie kopiowania.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Następnie można zapisać funkcji niestandardowych do przetwarzania danych przechowywanych na dysku użytkownika i udostępnić tych użytkowników w pliku możliwości roli.

## <a name="support-for-group-managed-service-accounts"></a>Obsługa grupy zarządzania usługi kont

W niektórych przypadkach zadanie, które użytkownik musi wykonać w ramach sesji JEA może być konieczne uzyskiwać dostęp do zasobów poza komputera lokalnego.
Podczas sesji JEA jest skonfigurowany do używania konta wirtualnego, wszelkie próby osiągnąć tych zasobów pojawi się pochodzą z tożsamości komputera lokalnego, nie konta wirtualnego lub podłączonego użytkownika.
W TP5, możemy włączono obsługę działających JEA w kontekście [grupy konta usługi zarządzanego przez] (https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), co znacznie ułatwia dostęp do zasobów sieciowych przy użyciu tożsamości domeny.

Aby skonfigurować sesję JEA do uruchomienia w ramach konta gMSA, użyj następujących nowy klucz w pliku Współpracuje:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Uwaga:** konta usług zarządzane przez grupę nie dają izolacji lub ograniczonym zakresie kont wirtualnych.
> Każdy użytkownik nawiązujący połączenie będzie udostępniać tej samej tożsamości gMSA, które mogą mieć uprawnienia w całym przedsiębiorstwie.
> Trzeba zwrócić szczególną uwagę podczas wybierania grupę, a zawsze wybierasz kont wirtualnych, które są ograniczone do komputera lokalnego, jeśli to możliwe.

## <a name="conditional-access-policies"></a>Zasady dostępu warunkowego

JEA jest doskonałym rozwiązaniem ograniczanie ktoś czynności podłączeni już do systemu zarządzania, ale co zrobić, gdy zostanie również chcesz ograniczyć *podczas* osoba może użyć JEA?
Dodaliśmy opcje konfiguracji w plikach konfiguracji sesji (.pssc) pozwala określić grupę zabezpieczeń, do których użytkownik musi należeć w celu ustanowienia sesji JEA.
Może to być szczególnie przydatne, jeśli masz system tylko w czasie (JIT) w danym środowisku i mają być użytkowników przed uzyskaniem dostępu do punktu końcowego JEA uprawnieniach podniesienie poziomu ich uprawnień.

Nowy *RequiredGroups* polem w pliku Współpracuje pozwala na określenie logiki, aby ustalić, czy użytkownik może łączyć się JEA.
Składa się z określania hashtable (opcjonalnie zagnieżdżona), który używa "I" i "Lub" klucze do utworzenia reguły.
Oto kilka przykładów sposób korzystania z tego pola:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Stały: Kont wirtualnych są teraz obsługiwane w systemie Windows Server 2008 R2
W wersji 5.1 WMF jesteś teraz mogą używać kont wirtualnych w systemie Windows Server 2008 R2, włączanie konfiguracji spójne i parzystość funkcji w systemie Windows Server 2008 R2 — 2016.
Kont wirtualnych pozostają nieobsługiwane, gdy przy użyciu JEA w systemie Windows 7.
