# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Komunikacji zdalnej usługi WS-Management (WSMan) w podstawowej programu PowerShell 

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instrukcje dotyczące tworzenia punktu końcowego usługi zdalne

Pakiet podstawowy programu PowerShell dla systemu Windows zawiera usługę WinRM, wtyczki (`pwrshplugin.dll`) i skrypt instalacji (`Install-PowerShellRemoting.ps1`) w `$PSHome`.
Te pliki umożliwiają programu PowerShell do akceptowania przychodzących połączeń zdalnych programu PowerShell, jeśli nie określono punktu końcowego.

### <a name="motivation"></a>Motywacją

Instalacja programu PowerShell mogą nawiązywać sesje programu PowerShell do komputerów zdalnych przy użyciu `New-PSSession` i `Enter-PSSession`.
Aby włączyć ją do akceptowania przychodzących połączeń zdalnych programu PowerShell, użytkownik musi utworzyć punkt końcowy komunikacji zdalnej usługi WinRM.
Jest to jawne opcjonalnych scenariusz użytkownika, w którym odbywa się PowerShellRemoting.ps1 instalacji można utworzyć punktu końcowego usługi WinRM.
Skrypt instalacji to rozwiązanie krótkoterminowej do chwili dodania dodatkowych funkcji do `Enable-PSRemoting` do wykonania tego samego działania.
Aby uzyskać więcej informacji, zobacz problem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Akcje skryptu

Skrypt

1. Tworzy katalog dla wtyczki w %windir%\System32\PowerShell
1. Kopiuje pwrshplugin.dll do tej lokalizacji
1. Generuje plik konfiguracji
1. Rejestruje to wtyczka z usługi WinRM

### <a name="registration"></a>Rejestracji

Skrypt musi zostać wykonana w sesji programu PowerShell poziomie administratora i działa w dwóch trybach.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Wykonane przez to wystąpienie programu PowerShell, który zarejestruje

``` powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Wykonywane przez inne wystąpienie programu PowerShell w imieniu wystąpienie, które zarejestruje

``` powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Na przykład:

``` powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**Uwaga:** skryptu rejestracji komunikacji zdalnej uruchomi WinRM, więc wszystkie istniejące sesje PSRP zostanie zakończona natychmiast po uruchomieniu skryptu. Jeśli uruchomiony podczas sesji zdalnej, to spowoduje przerwanie połączenia.

## <a name="how-to-connect-to-the-new-endpoint"></a>Łączenie z nowego punktu końcowego

Utwórz sesję programu PowerShell do nowego punktu końcowego programu PowerShell, określając `-ConfigurationName "some endpoint name"`. Aby połączyć się z wystąpieniem programu PowerShell w powyższym przykładzie, użyj jednej:

``` powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Należy pamiętać, że `New-PSSession` i `Enter-PSSession` wywołań, które nie określają `-ConfigurationName` będzie obowiązywać domyślny punkt końcowy programu PowerShell, `microsoft.powershell`.
