---
title: Obsługa zdalna usługi WS-Management (WSMan) w programie PowerShell Core
description: Komunikacji zdalnej w programie PowerShell Core za pomocą usługi WS-Management
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587350"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Obsługa zdalna usługi WS-Management (WSMan) w programie PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrukcje, aby utworzyć punkt końcowy komunikacji zdalnej

Pakiet programu PowerShell Core for Windows obejmuje dodatku typu plug-in WinRM (`pwrshplugin.dll`) i skrypt instalacji (`Install-PowerShellRemoting.ps1`) w `$PSHome`.
Te pliki umożliwiają programu PowerShell do akceptowania przychodzących połączeń zdalnych programu PowerShell, jeśli nie określono punktu końcowego.

### <a name="motivation"></a>Motywacją

Instalacja programu PowerShell mogą nawiązywać sesje programu PowerShell z komputerów zdalnych przy użyciu `New-PSSession` i `Enter-PSSession`.
Aby włączyć ją do akceptowania przychodzących połączeń zdalnych programu PowerShell, użytkownik musi utworzyć punkt końcowy komunikacji zdalnej usługi WinRM.
Jest to jawne uczestnictwo scenariusz gdy użytkownik uruchamia PowerShellRemoting.ps1 instalacji, aby utworzyć punkt końcowy usługi WinRM.
Skrypt instalacji jest rozwiązaniem krótkoterminowym, dopóki nie możemy dodać kolejne funkcje do `Enable-PSRemoting` do wykonania tego samego działania.
Aby uzyskać więcej informacji, zobacz problem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Akcje skryptu

Skrypt

1. Tworzy katalog dla wtyczki w ramach %windir%\System32\PowerShell
1. Kopiuje pwrshplugin.dll do tej lokalizacji
1. Generuje plik konfiguracji
1. Rejestruje to wtyczki za pomocą usługi WinRM

### <a name="registration"></a>Rejestracja

Skrypt musi zostać wykonana w ramach sesji programu PowerShell z poziomu administratora i jest uruchamiany w dwóch trybach.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Wykonane przez to wystąpienie programu PowerShell, która zarejestruje

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Wykonane przez inne wystąpienie programu PowerShell w imieniu wystąpienia, które zarejestruje

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Na przykład:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**Uwaga:** skrypt rejestracji komunikacji zdalnej spowoduje ponowne uruchomienie usługi WinRM, dzięki czemu wszystkie istniejące sesje PSRP przestanie obowiązywać natychmiast, po uruchomieniu skryptu. Jeśli podczas sesji zdalnej, utracą połączenia.

## <a name="how-to-connect-to-the-new-endpoint"></a>Jak połączyć się z nowego punktu końcowego

Utwórz sesję programu PowerShell do nowego punktu końcowego programu PowerShell, określając `-ConfigurationName "some endpoint name"`. Aby nawiązać połączenie z wystąpieniem programu PowerShell w powyższym przykładzie, należy użyć albo:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Należy pamiętać, że `New-PSSession` i `Enter-PSSession` wywołań, które nie określają `-ConfigurationName` będą ukierunkowane na domyślny punkt końcowy programu PowerShell, `microsoft.powershell`.