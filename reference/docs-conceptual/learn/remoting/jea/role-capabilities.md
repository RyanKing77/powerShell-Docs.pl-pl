---
ms.date: 07/10/2019
keywords: jea, PowerShell, zabezpieczenia
title: Możliwości roli JEA
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017958"
---
# <a name="jea-role-capabilities"></a>Możliwości roli JEA

Podczas tworzenia punktu końcowego JEA należy zdefiniować co najmniej jedną funkcję roli opisującą, co ktoś może wykonać w sesji JEA. Funkcja roli to plik danych programu PowerShell z `.psrc` rozszerzeniem, które zawiera listę wszystkich poleceń cmdlet, funkcji, dostawców i zewnętrznych programów, które są dostępne do łączenia użytkowników.

## <a name="determine-which-commands-to-allow"></a>Określanie poleceń, które mają być dozwolone

Pierwszym krokiem tworzenia pliku możliwości roli jest rozważenie, do czego użytkownicy potrzebują dostępu. Proces zbierania wymagań może zająć trochę czasu, ale jest to ważny proces. Umożliwienie użytkownikom dostępu do zbyt małej liczby poleceń cmdlet i funkcji może uniemożliwić im ich przeprowadzenie. Zezwalanie na dostęp za dużo poleceń cmdlet i funkcji może pozwolić użytkownikom na wykonywanie więcej niż zamierzonych i osłabionych zasobów zakresie zabezpieczeń.

Sposób działania tego procesu zależy od organizacji i celów. Poniższe porady mogą pomóc upewnić się, że jesteś w odpowiedniej ścieżce.

1. **Zidentyfikuj** polecenia używane przez użytkowników w celu uzyskania zadań. Może to wiązać się z badaniem pracowników działu IT, sprawdzaniem skryptów automatyzacji lub analizowaniem i dzienników sesji programu PowerShell.
2. **Zaktualizuj** użycie narzędzi wiersza polecenia do odpowiedników programu PowerShell, tam gdzie to możliwe, w celu uzyskania najlepszej inspekcji i środowiska dostosowania jea. Programy zewnętrzne nie mogą być ograniczone jako natywne polecenia cmdlet programu PowerShell i funkcje w programie JEA.
3. **Ogranicz** zakres poleceń cmdlet, aby zezwalać tylko na określone wartości parametrów lub parametrów. Jest to szczególnie ważne, jeśli użytkownicy powinni zarządzać tylko częścią systemu.
4. **Utwórz** funkcje niestandardowe, aby zamienić złożone polecenia lub polecenia, które są trudne do ograniczenia w jea. Prosta funkcja, która otacza złożone polecenie lub stosuje dodatkową logikę walidacji, może oferować dodatkową kontrolę dla administratorów i prostoty użytkowników końcowych.
5. **Przetestuj** listę zakresów dozwolonych poleceń użytkownikom lub usług Automation, a następnie dostosuj je w razie potrzeby.

### <a name="examples-of-potentially-dangerous-commands"></a>Przykłady potencjalnie niebezpiecznych poleceń

Ostrożne wybieranie poleceń jest ważne, aby zapewnić, że punkt końcowy JEA nie zezwoli użytkownikowi na podniesienie uprawnień.

> [!IMPORTANT]
> Podstawowe informacje wymagane do successCommands użytkownika w sesji JEA są często uruchamiane z podniesionymi uprawnieniami.

Poniższa tabela zawiera przykłady poleceń, które mogą być używane złośliwie, jeśli są dozwolone w stanie nieograniczonym. Nie jest to pełna lista i powinna być używana tylko jako ostrożny punkt wyjścia.

|                                            Ryzyko                                            |                                Przykład                                |                                                                              Powiązane polecenia                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Przyznawanie uprawnień administratora łączącego użytkownika w celu obejścia JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Uruchamianie dowolnego kodu, takiego jak złośliwe oprogramowanie, luki w zabezpieczeniach lub skrypty niestandardowe w celu obejścia ochrony | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Utwórz plik możliwości roli

Nowy plik możliwości roli programu PowerShell można utworzyć za pomocą polecenia cmdlet [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) .

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Otrzymany plik możliwości roli powinien być edytowany w celu zezwalania na polecenia wymagane przez rolę. Dokumentacja pomocy programu PowerShell zawiera kilka przykładów, jak można skonfigurować plik.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Zezwalanie na polecenia cmdlet i funkcje programu PowerShell

Aby autoryzować użytkowników do uruchamiania poleceń cmdlet lub funkcji programu PowerShell, Dodaj polecenie cmdlet lub nazwę funkcji do pól VisibleCmdlets lub VisibleFunctions. Jeśli nie masz pewności, czy polecenie jest poleceniu cmdlet lub funkcji, możesz uruchomić `Get-Command <name>` i sprawdzić Właściwość **CommandType** w danych wyjściowych.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Czasami zakres konkretnego polecenia cmdlet lub funkcji jest zbyt szeroki dla potrzeb użytkowników. Administrator DNS, na przykład, prawdopodobnie potrzebuje tylko dostępu do ponownego uruchomienia usługi DNS. W środowiskach z wieloma dzierżawcami dzierżawca ma dostęp do samoobsługowego narzędzia do zarządzania. Dzierżawy powinny być ograniczone do zarządzania własnymi zasobami. W takich przypadkach można ograniczyć parametry, które są udostępniane przez polecenie cmdlet lub funkcję.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

W bardziej zaawansowanych scenariuszach może być również konieczne ograniczenie wartości, które mogą być używane przez użytkownika z tymi parametrami. Możliwości roli umożliwiają zdefiniowanie zestawu wartości lub wzorca wyrażenia regularnego, który określa, jakie dane wejściowe są dozwolone.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Typowe parametry programu PowerShell](/powershell/module/microsoft.powershell.core/about/about_commonparameters) są zawsze dozwolone, nawet w przypadku ograniczenia dostępnych parametrów.
> Nie należy jawnie wystawić ich w polu Parameters.

W poniższej tabeli opisano różne sposoby dostosowywania widocznego polecenia cmdlet lub funkcji.
Możesz mieszać i dopasować dowolne z poniższych wartości w polu **VisibleCmdlets** .

|                                           Przykład                                           |                                                             Przypadek użycia                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` lub `@{ Name = 'My-Func' }`                                                      | Zezwala użytkownikowi na uruchamianie `My-Func` bez żadnych ograniczeń dotyczących parametrów.                                                      |
| `'MyModule\My-Func'`                                                                        | Zezwala użytkownikowi na uruchamianie `My-Func` z modułu `MyModule` bez żadnych ograniczeń dotyczących parametrów.                           |
| `'My-*'`                                                                                    | Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji przy użyciu zlecenia `My`.                                                                 |
| `'*-Func'`                                                                                  | Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji z rzeczownikiem `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Zezwala użytkownikowi na uruchamianie `My-Func` `Param1` z parametrami i `Param2` . Dowolna wartość może zostać dostarczona do parametrów.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Zezwala użytkownikowi na uruchamianie `My-Func` `Param1` z parametrem. Do parametru można podać tylko parametry "wartość1" i "wartość2".        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Zezwala użytkownikowi na uruchamianie `My-Func` `Param1` z parametrem. Wszystkie wartości zaczynające się od "contoso" można dostarczyć do parametru. |

> [!WARNING]
> W celu uzyskania najlepszych praktyk w zakresie zabezpieczeń nie zaleca się używania symboli wieloznacznych podczas definiowania widocznych poleceń cmdlet lub funkcji. Zamiast tego należy jawnie wyświetlić każde zaufane polecenie, aby upewnić się, że żadne inne polecenia, które współużytkują ten sam schemat nazewnictwa, nie są celowo autoryzowane.

Nie można zastosować zarówno **ValidatePattern** , jak i **ValidateSet** do tego samego polecenia cmdlet lub funkcji.

Jeśli to zrobisz, **ValidatePattern** zastępuje **ValidateSet**.

Aby uzyskać więcej informacji na temat **ValidatePattern**, zapoznaj się z wpisem " [ *Hej, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) i zawartością referencyjną [wyrażeń regularnych programu PowerShell](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) .

### <a name="allowing-external-commands-and-powershell-scripts"></a>Zezwalanie na polecenia zewnętrzne i skrypty programu PowerShell

Aby umożliwić użytkownikom uruchamianie plików wykonywalnych i skryptów programu PowerShell (. ps1) w sesji JEA, należy dodać pełną ścieżkę do każdego programu w polu **VisibleExternalCommands** .

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Tam, gdzie to możliwe, aby użyć polecenia cmdlet programu PowerShell lub odpowiedników funkcji dla wszystkich zewnętrznych plików wykonywalnych autoryzowanych od czasu, gdy masz kontrolę nad parametrami dozwolonymi przy użyciu poleceń cmdlet i funkcji programu PowerShell.

Wiele plików wykonywalnych pozwala odczytać bieżący stan, a następnie zmienić go przez podanie różnych parametrów.

Rozważmy na przykład rolę administratora serwera plików, który zarządza udziałami sieciowymi hostowanymi w systemie. Jednym ze sposobów zarządzania udziałami jest użycie `net share`. Jednak umożliwienie programu **net. exe** jest niebezpieczne, ponieważ użytkownik może użyć polecenia, aby uzyskać uprawnienia administratora `net group Administrators unprivilegedjeauser /add`w programie. Bezpieczniejszym rozwiązaniem jest umożliwienie [Get-SmbShare](/powershell/module/smbshare/get-smbshare), która osiąga ten sam wynik, ale ma znacznie bardziej ograniczony zakres.

Podczas udostępniania poleceń zewnętrznych użytkownikom w sesji JEA należy zawsze określić pełną ścieżkę do pliku wykonywalnego. Zapobiega to wykonywaniu podobnych i potencjalnie złośliwych programów, które znajdują się w innym miejscu w systemie.

### <a name="allowing-access-to-powershell-providers"></a>Zezwalanie na dostęp do dostawców programu PowerShell

Domyślnie żaden dostawca programu PowerShell nie jest dostępny w sesjach JEA. Zmniejsza to ryzyko, że informacje poufne i ustawienia konfiguracji są ujawniane użytkownikowi nawiązującemu połączenie.

W razie potrzeby można zezwolić na dostęp do dostawców programu PowerShell przy użyciu `VisibleProviders` polecenia. Aby uzyskać pełną listę dostawców, uruchom `Get-PSProvider`polecenie.

```powershell
VisibleProviders = 'Registry'
```

W przypadku prostych zadań, które wymagają dostępu do systemu plików, rejestru, magazynu certyfikatów lub innych wrażliwych dostawców, należy rozważyć zapisanie niestandardowej funkcji, która współpracuje z dostawcą w imieniu użytkownika. Funkcje, polecenia cmdlet i programy zewnętrzne dostępne w sesji JEA nie podlegają takim samym ograniczeniom jak JEA. Domyślnie mają dostęp do dowolnego dostawcy. Należy również rozważyć użycie [dysku użytkownika](session-configurations.md#user-drive) podczas kopiowania plików do lub z punktu końcowego jea.

### <a name="creating-custom-functions"></a>Tworzenie funkcji niestandardowych

Możesz tworzyć niestandardowe funkcje w pliku możliwości roli, aby uprościć złożone zadania dla użytkowników końcowych. Funkcje niestandardowe są również przydatne, gdy wymagana jest zaawansowana logika walidacji dla wartości parametrów polecenia cmdlet. Proste funkcje można napisać w polu **FunctionDefinitions** :

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Nie zapomnij dodać nazwy funkcji niestandardowych do pola **VisibleFunctions** , aby mogły być uruchamiane przez użytkowników jea.

Treść (blok skryptu) funkcji niestandardowych jest uruchamiana w domyślnym trybie języka dla systemu i nie podlega ograniczeniom języka JEA. Oznacza to, że funkcje mogą uzyskać dostęp do systemu plików i rejestru i uruchamiać polecenia, które nie były widoczne w pliku możliwości roli. Należy zachować ostrożność, aby uniknąć uruchamiania dowolnego kodu przy użyciu parametrów. Unikaj bezpośredniego wprowadzania danych przez użytkownika do poleceń `Invoke-Expression`cmdlet, takich jak.

W powyższym przykładzie należy zauważyć, że zamiast skrótu `Microsoft.PowerShell.Utility\Select-Object` `Select-Object`użyto w pełni kwalifikowanej nazwy modułu (FQMN).
Funkcje zdefiniowane w plikach możliwości roli są nadal objęte zakresem sesji JEA, które obejmują JEA funkcje serwera proxy, które są tworzone w celu ograniczenia istniejących poleceń.

Domyślnie program `Select-Object` to ograniczone polecenie cmdlet we wszystkich sesjach jea, które nie zezwalają na wybór arbitralnych właściwości obiektów. Aby użyć nieograniczeń `Select-Object` w funkcjach, należy jawnie zażądać pełnej implementacji przy użyciu FQMN. Każde ograniczone polecenie cmdlet w sesji JEA ma takie same ograniczenia w przypadku wywołania funkcji. Aby uzyskać więcej informacji, zobacz [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Jeśli piszesz kilka funkcji niestandardowych, wygodniejsze jest umieszczenie ich w module skryptu programu PowerShell. Te funkcje są widoczne w sesji JEA przy użyciu pola **VisibleFunctions** , tak jak w przypadku modułów wbudowanych i innych firm.

Aby ukończenie karty działało prawidłowo w sesjach jea, należy dołączyć wbudowaną funkcję `tabexpansion2` na liście **VisibleFunctions** .

## <a name="place-role-capabilities-in-a-module"></a>Umieść możliwości roli w module

Aby program PowerShell znalazł plik możliwości roli, musi on być przechowywany w folderze **RoleCapabilities** w module programu PowerShell. Moduł może być przechowywany w dowolnym folderze uwzględnionym w `$env:PSModulePath` zmiennej środowiskowej, ale nie powinien być umieszczony w pliku system32 ani w folderze, w którym niezaufany użytkownicy mogą modyfikować pliki. Poniżej przedstawiono przykład tworzenia podstawowego modułu skryptu programu PowerShell o nazwie **ContosoJEA** w `$env:ProgramFiles` ścieżce.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Aby uzyskać więcej informacji na temat modułów programu PowerShell, zobacz [Opis modułu programu PowerShell](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Aktualizowanie możliwości roli

Można edytować plik możliwości roli, aby zaktualizować ustawienia w dowolnym momencie. Wszystkie nowe sesje JEA uruchomione po zaktualizowaniu możliwości roli zostaną odzwierciedlone w zmienionych możliwościach.

Jest to dlatego, że kontrolowanie dostępu do folderu możliwości roli jest tak ważne. Tylko Administratorzy o dużej zaufaniu powinni mieć możliwość zmiany plików możliwości roli. Jeśli niezaufany użytkownik może zmienić pliki możliwości roli, może łatwo dać sobie dostęp do poleceń cmdlet, które pozwalają im podwyższyć poziom uprawnień.

W przypadku administratorów chcących blokować dostęp do możliwości roli upewnij się, że system lokalny ma dostęp do odczytu do plików możliwości roli i zawiera moduły.

## <a name="how-role-capabilities-are-merged"></a>Jak są scalane możliwości roli

Użytkownicy uzyskują dostęp do wszystkich zgodnych możliwości roli w [pliku konfiguracji sesji](session-configurations.md) po wprowadzeniu sesji jea. JEA próbuje dać użytkownikowi najbardziej ograniczając zestaw poleceń dozwolonych przez dowolne role.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets i VisibleFunctions

Najbardziej złożona logika scalania ma wpływ na polecenia cmdlet i funkcje, których parametry i wartości parametrów są ograniczone w JEA.

Reguły są następujące:

1. Jeśli polecenie cmdlet jest widoczne tylko w jednej roli, jest widoczne dla użytkownika z odpowiednimi ograniczeniami parametrów.
2. Jeśli polecenie cmdlet jest widoczne w więcej niż jednej roli, a każda rola ma takie same ograniczenia dotyczące polecenia cmdlet, polecenie cmdlet jest widoczne dla użytkownika z tymi ograniczeniami.
3. Jeśli polecenie cmdlet jest widoczne w więcej niż jednej roli, a każda rola umożliwia korzystanie z innego zestawu parametrów, polecenie cmdlet i wszystkie parametry zdefiniowane w każdej roli są widoczne dla użytkownika.
   Jeśli jedna rola nie ma ograniczeń dotyczących parametrów, wszystkie parametry są dozwolone.
4. Jeśli jedna rola definiuje walidację zestawu lub walidację wzorca dla parametru polecenia cmdlet, a inna rola zezwala na parametr, ale nie ogranicza wartości parametrów, zestaw walidacji lub wzorzec jest ignorowany.
5. Jeśli zestaw walidacji jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, dozwolone są wszystkie wartości z wszystkich zestawów walidacji.
6. Jeśli wzorzec walidacji jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, dozwolone są wszystkie wartości, które pasują do któregokolwiek z wzorców.
7. Jeśli zestaw walidacji jest zdefiniowany w jednej lub kilku rolach, a wzorzec walidacji jest zdefiniowany w innej roli dla tego samego parametru polecenia cmdlet, zestaw walidacji jest ignorowany, a reguła (6) odnosi się do pozostałych wzorców walidacji.

Poniżej przedstawiono przykład sposobu, w jaki role są scalane zgodnie z następującymi regułami:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Wszystkie inne pola w pliku możliwości roli są dodawane do zbiorczego zestawu dozwolonych poleceń zewnętrznych, aliasów, dostawców i skryptów uruchamiania. Wszystkie polecenia, aliasy, dostawcy lub skrypty dostępne w jednej funkcji roli są dostępne dla użytkownika JEA.

Należy zachować ostrożność, aby mieć pewność, że połączony zestaw dostawców z jednej możliwości roli i poleceń cmdlet/funkcji/poleceń od innego nie zezwoli użytkownikom na niezamierzone dostęp do zasobów systemowych.
Na przykład, jeśli jedna rola zezwala na `Remove-Item` wykonanie polecenia cmdlet, a `FileSystem` drugi umożliwia dostawcy, istnieje ryzyko, że użytkownik jea usuwa dowolne pliki na komputerze. Dodatkowe informacje na temat identyfikowania czynnych uprawnień użytkowników można znaleźć w artykule dotyczącym [inspekcji jea](audit-and-report.md) .

## <a name="next-steps"></a>Następne kroki

[Utwórz plik konfiguracji sesji](session-configurations.md)
