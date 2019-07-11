---
ms.date: 07/10/2019
keywords: jea, programu powershell, zabezpieczeń
title: Możliwości roli usługi JEA
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726612"
---
# <a name="jea-role-capabilities"></a>Możliwości roli usługi JEA

Podczas tworzenia punktu końcowego JEA, należy zdefiniować jedną lub kilkoma funkcjami roli, które opisują ktoś czynności w ramach sesji usługi JEA. Funkcja roli jest plikiem danych programu PowerShell przy użyciu `.psrc` rozszerzenia, które wyświetla listę wszystkich poleceń cmdlet, funkcji, dostawców i zewnętrznych programów, które są dostępne do procesu łączenia użytkowników.

## <a name="determine-which-commands-to-allow"></a>Określić, jakie polecenia, aby umożliwić

Pierwszym krokiem w tworzeniu plik możliwości roli jest należy wziąć pod uwagę, jakie użytkownicy muszą mieć dostęp do. Wymagania procesu zbierania może wymagać trochę czasu, ale jest procesem ważne. Zapewniając użytkownikom dostęp do zbyt małej liczby poleceń cmdlet i funkcji może uniemożliwić ich wprowadzenie ich pracę. Zezwalanie na dostęp do zbyt wielu poleceń cmdlet i funkcji można zezwolić użytkownikom na więcej niż planowano co obniżać Twoje wystąpienie zabezpieczeń.

Jak obniżyć informacji na temat tego procesu zależy od tego, organizacji i cele. Poniższe porady mogą pomóc upewnić się, że jesteś na prawidłową ścieżkę.

1. **Identyfikowanie** korzystają użytkownicy polecenia do wykonywania ich zadań. Może to obejmować badanie informatykami, sprawdzanie skryptów automatyzacji lub analizowanie dzienników i zapisy sesji programu PowerShell.
2. **Aktualizacja** użycie narzędzi wiersza polecenia będące odpowiednikami programu PowerShell, gdzie to możliwe, najlepiej inspekcji i JEA dostosowywania środowiska. Nie można ograniczyć zewnętrznych programów jako dokładnością jako natywnych poleceń cmdlet programu PowerShell i funkcji jea.
3. **Ogranicz** zakresu poleceń cmdlet, aby zezwalać tylko na określonych parametrów lub wartości parametrów. Jest to szczególnie ważne w przypadku użytkowników należy zarządzać tylko części systemu.
4. **Utwórz** funkcji niestandardowych w celu zastąpienia polecenia złożonych lub polecenia, które są trudne do ograniczenia jea. Prostej funkcji, która opakowuje złożone polecenia lub stosuje logikę dodatkowe sprawdzenie poprawności oferują dodatkową kontrolę dla uproszczenia administratorów i użytkowników końcowych.
5. **Test** o określonym zakresie listę dopuszczalny rozmiar poleceń Twoje użytkownika lub grupy usługi automation i dostosowanie wedle potrzeb.

### <a name="examples-of-potentially-dangerous-commands"></a>Przykłady poleceń potencjalnie niebezpiecznych

Staranne wybieranie polecenia ważne jest, aby upewnić się, że punkt końcowy usługi JEA nie zezwala użytkownikowi na podniesienie poziomu uprawnień.

> [!IMPORTANT]
> Podstawowe informacje wymagane do successCommands użytkownika w ramach sesji usługi JEA często są uruchamiane z podwyższonym poziomem uprawnień.

Poniższa tabela zawiera przykłady poleceń, które mogą służyć złośliwie Jeśli jest to dozwolone w stanie nieograniczone. To nie jest kompletną listą i powinna służyć wyłącznie jako punktu wyjścia ostrzegawcze.

|                                            Ryzyko                                            |                                Przykład                                |                                                                              Powiązane polecenia                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Udzielanie użytkownik nawiązujący połączenie z uprawnieniami administratora w celu OBEJŚCIE usługi JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Uruchamiania dowolnego kodu, takich jak złośliwe oprogramowanie luki w zabezpieczeniach i niestandardowe skrypty do obejścia zabezpieczeń | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Utwórz plik możliwości roli

Można utworzyć nowy plik możliwości roli programu PowerShell przy użyciu [New PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) polecenia cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Wynikowy plik możliwości roli należy zmodyfikować w taki sposób, aby zezwalać na polecenia wymaganych dla danej roli. Dokumentacja pomocy programu PowerShell zawiera kilka przykładów sposobu konfigurowania pliku.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Polecenia cmdlet programu PowerShell i funkcji

Aby autoryzować użytkowników o uruchomienie polecenia cmdlet programu PowerShell lub funkcje, należy dodać nazwę polecenia cmdlet lub funkcji do VisibleCmdlets lub VisibleFunctions pól. Jeśli nie masz pewności, czy polecenie jest polecenie cmdlet lub funkcji, możesz uruchomić `Get-Command <name>` i sprawdź **CommandType** właściwość w danych wyjściowych.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Czasami zakresu określonego polecenia cmdlet lub funkcji jest zbyt ogólnym, na potrzeby użytkowników. Administrator systemu DNS, na przykład wymaga jedynie prawdopodobnie uzyskać dostęp do ponownego uruchomienia usługi DNS. W środowiskach wielodostępnych dzierżawcy mają dostęp do narzędzia do samoobsługowego zarządzania. Dzierżawcy powinny być ograniczone do zarządzania własnych zasobów. W takich przypadkach można ograniczyć, które parametry są udostępniane z polecenia cmdlet lub funkcji.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

W bardziej zaawansowanych scenariuszach może być również konieczne ograniczenie wartości, które użytkownik może używać z następującymi parametrami. Możliwości roli pozwalają zdefiniować zestaw wartości lub wzorzec wyrażenia regularnego, które określają, jakie dane wejściowe jest dozwolone.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Typowe parametry programu PowerShell](/powershell/module/microsoft.powershell.core/about/about_commonparameters) zawsze dozwolone, nawet wtedy, gdy ograniczenia dostępnych parametrów.
> Należy nie jawnie ich listę w polu Parametry.

W poniższej tabeli opisano różne sposoby, które można dostosować widoczne polecenia cmdlet lub funkcji.
Możesz mieszać i dopasowywać znajdujących się poniżej w **VisibleCmdlets** pola.

|                                           Przykład                                           |                                                             Przypadek użycia                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` lub `@{ Name = 'My-Func' }`                                                      | Zezwala użytkownikowi na uruchamianie `My-Func` bez żadnych ograniczeń na parametry.                                                      |
| `'MyModule\My-Func'`                                                                        | Zezwala użytkownikowi na uruchamianie `My-Func` z modułu `MyModule` bez żadnych ograniczeń na parametry.                           |
| `'My-*'`                                                                                    | Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji za pomocą zlecenie `My`.                                                                 |
| `'*-Func'`                                                                                  | Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji z rzeczownikiem `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` i `Param2` parametrów. Dowolna wartość mogą być dostarczane do parametrów.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru. Tylko "Wartość1" i "Wartość2" mogą być dostarczane do parametru.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru. Żadnej wartości, zaczynając od "contoso" mogą być dostarczane do parametru. |

> [!WARNING]
> Aby uzyskać najlepsze rozwiązania w zakresie zabezpieczeń nie zaleca się używać symboli wieloznacznych, podczas definiowania widoczne dla poleceń cmdlet lub funkcji. Zamiast tego należy jawnie listę każdego zaufanych polecenia, aby upewnić się, że żadne polecenia, które współużytkują ten sam schemat nazewnictwa przypadkowo uprawnienia.

Nie można zastosować zarówno **ValidatePattern** i **ValidateSet** do tego samego polecenia cmdlet lub funkcji.

Jeśli to zrobisz, **ValidatePattern** zastępuje **ValidateSet**.

Aby uzyskać więcej informacji na temat **ValidatePattern**, zapoznaj się z [to *Hey, Scripting Guy!* wpis](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) i [wyrażeń regularnych w programie PowerShell](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)odwoływać się do zawartości.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Dzięki niemu agencje poleceń zewnętrznych i skryptów programu PowerShell

Aby zezwolić użytkownikom na uruchamianie plików wykonywalnych i skryptów programu PowerShell (.ps1) w ramach sesji usługi JEA, trzeba dodać pełną ścieżkę do każdego programu w **VisibleExternalCommands** pola.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Jeśli to możliwe, polecenia cmdlet lub funkcja odpowiedników dla zewnętrznych plików wykonywalnych, autoryzowane od momentu przy użyciu programu PowerShell mają kontrolę nad parametry są niedozwolone przy użyciu poleceń cmdlet programu PowerShell i funkcji.

Wiele plików wykonywalnych pozwala na odczyt bieżącego stanu, a następnie zmienić je, podając różne parametry.

Rozważmy na przykład rola Administrator serwera plików, który zarządza udziałów sieciowych hostowanych w systemie. Jednym ze sposobów zarządzania udziałami jest użycie `net share`. Jednakże, dzięki czemu **net.exe** jest niebezpieczne, ponieważ użytkownik może uzyskać uprawnienia administratora, przy użyciu za pomocą polecenia `net group Administrators unprivilegedjeauser /add`. Opcja bardziej bezpieczna jest umożliwienie [Get-SmbShare](/powershell/module/smbshare/get-smbshare), która osiąga ten sam wynik, ale ma bardzo bardziej ograniczony zakres.

Podczas wprowadzania poleceń zewnętrznych dostępnych dla użytkowników w ramach sesji usługi JEA, zawsze należy określić pełną ścieżkę do pliku wykonywalnego. Zapobiega to wykonywanie podobnie nazwanych i potencjalnie złośliwych programów znajdujących się w innym miejscu w systemie.

### <a name="allowing-access-to-powershell-providers"></a>Zezwalanie na dostęp do dostawcy programu PowerShell

Domyślnie żaden dostawca programu PowerShell są dostępne w sesji JEA. Zmniejsza to ryzyko poufnych informacji i ustawienia konfiguracji zostały ujawnione użytkownik nawiązujący połączenie.

Gdy jest to konieczne, można zezwolić na dostęp do dostawcy programu PowerShell przy użyciu `VisibleProviders` polecenia. Aby uzyskać pełną listę dostawców, uruchamianie `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Proste zadania, które wymagają dostępu do systemu plików, rejestru, magazynu certyfikatów lub innych dostawców poufne należy wziąć pod uwagę pisanie niestandardowej funkcji, która współpracuje z dostawcą w imieniu użytkownika. Funkcje, poleceń cmdlet i zewnętrznych programów dostępnych w ramach sesji usługi JEA nie są z zastrzeżeniem tych samych ograniczeń, jak JEA. Domyślnie, ich dostęp z dowolnego dostawcy. Również należy rozważyć użycie [dysku użytkownika](session-configurations.md#user-drive) podczas kopiowania plików do / z punktu końcowego JEA jest wymagana.

### <a name="creating-custom-functions"></a>Tworzenie funkcji niestandardowych

Można tworzyć niestandardowe funkcje w pliku możliwości roli, aby uprościć złożone zadania dla użytkowników końcowych. Funkcje niestandardowe są również przydatne, gdy potrzebujesz logikę weryfikacji zaawansowane o wprowadzenie wartości parametrów polecenia cmdlet. Możesz pisać proste funkcje **FunctionDefinitions** pola:

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
> Nie zapomnij dodać nazwę Twojej funkcji niestandardowych do **VisibleFunctions** pola, aby mogły być uruchamiane przez użytkowników usługi JEA.

Treść funkcji niestandardowych (blok skryptu) działa w trybie język domyślny dla systemu, a nie jest podlegających ograniczeniom języka firmy JEA. Oznacza to, że funkcje można uzyskiwać dostęp do systemu plików i rejestru i uruchamiania poleceń, które nie były widoczne w pliku możliwości roli. Należy zadbać, aby uniknąć uruchamiania dowolnego kodu, korzystając z parametrów. Dane wejściowe użytkownika potokowanie bezpośrednio do polecenia cmdlet, takich jak uniknąć `Invoke-Expression`.

W powyższym przykładzie należy zauważyć, że nazwa FQDN modułu (FQMN) `Microsoft.PowerShell.Utility\Select-Object` był używany zamiast skrót `Select-Object`.
Funkcje zdefiniowane w plikach możliwości roli są nadal podlega procesowi zakresu sesji JEA, który zawiera funkcje serwera proxy usługi JEA tworzy ograniczenie istniejące polecenia.

Domyślnie `Select-Object` jest poleceniem cmdlet ograniczone we wszystkich sesjach JEA, który nie zezwala na wybór dowolne właściwości obiektów. Aby używać nieograniczonego `Select-Object` w funkcjach, należy jawnie zażądać pełnego wdrożenia przy użyciu FQMN. Wszelkie ograniczone polecenie cmdlet w sesji JEA ma tych samych ograniczeń po wywołaniu przez funkcję. Aby uzyskać więcej informacji, zobacz [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Jeśli piszesz kilka niestandardowych funkcji jest bardziej wygodne i umieść je w module skryptów programu PowerShell. Możesz uwidocznić te funkcje przy użyciu sesji JEA **VisibleFunctions** pola, jak w przypadku modułów wbudowanych oraz innych firm.

Karta zakończenia ma działać prawidłowo w sesjach JEA możesz musi zawierać wbudowanej funkcji `tabexpansion2` w **VisibleFunctions** listy.

## <a name="place-role-capabilities-in-a-module"></a>W module umieścić możliwości roli

Aby dla programu PowerShell, aby znaleźć plik możliwości roli, muszą być przechowywane w **RoleCapabilities** folderu modułu programu PowerShell. Moduł mogą być przechowywane w dowolnym folderze zawarte w `$env:PSModulePath` zmiennej środowiskowej, jednak użytkownik nie należy umieścić go w System32 lub folderu gdzie niezaufanych, łączenie użytkowników można zmodyfikować pliki. Poniżej znajduje się przykład tworzenia podstawowych moduł skrypt programu PowerShell o nazwie **ContosoJEA** w `$env:ProgramFiles` ścieżki.

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

Aby uzyskać więcej informacji na temat modułów programu PowerShell, zobacz [opis modułu programu PowerShell](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Aktualizowanie możliwości roli

Możesz edytować plik możliwości roli, aby zaktualizować ustawienia w dowolnym momencie. Wszystkie nowe sesje JEA pracę po zaktualizowaniu możliwości roli będą odzwierciedlać poprawione możliwości.

Jest to, dlaczego kontrola dostępu do folderu możliwości roli jest tak ważny. Tylko wysoce zaufanych administratorów powinny mieć możliwość zmiany plików możliwości roli. Niezaufanego użytkownika mogą zmieniać pliki możliwości roli, łatwo udzielenie się dostępu do poleceń cmdlet, które pozwalają do podniesienia swoich uprawnień.

Dla administratorów chcących blokowanie dostępu do możliwości roli upewnij się, że System lokalny ma dostęp do odczytu do plików funkcji roli i zawierającego moduły.

## <a name="how-role-capabilities-are-merged"></a>Jak są scalane możliwości roli

Użytkownicy uzyskują dostęp do wszystkich zgodnych funkcji ról w [plik konfiguracji sesji](session-configurations.md) po użytkownik podał sesji JEA. JEA próbuje przyznać użytkownikowi restrykcyjny zestaw poleceń dozwolone przez żaden z tych ról.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets i VisibleFunctions

Najbardziej złożoną logikę scalanie wpływa na poleceń cmdlet i funkcje, które mogą mieć ich parametrów i wartości parametrów ograniczone jea.

Dostępne są następujące reguły:

1. Jeśli polecenie cmdlet jest dostępne tylko widoczne w jedną rolę, jest widoczny dla użytkownika o wszelkich ograniczeń odpowiednich parametrów.
2. Jeśli polecenie cmdlet jest widoczny w więcej niż jednej roli, a każda rola ma ograniczenia tego samego polecenia cmdlet, polecenie cmdlet jest widoczna dla użytkownika przy użyciu tych ograniczeń.
3. Jeśli polecenie cmdlet jest widoczny w więcej niż jednej roli, a każda rola umożliwia inny zbiór parametrów, polecenia cmdlet i wszystkie parametry, które są zdefiniowane dla każdej roli są widoczne dla użytkownika.
   Jeśli jedna rola nie ma ograniczenia dotyczące parametrów, wszystkie parametry są dozwolone.
4. Jeśli jedna rola definiuje zestaw sprawdzania poprawności lub wzorca weryfikacji dla parametru polecenia cmdlet, a także innych ról pozwala parametru, ale nie ogranicza wartości parametrów, sprawdzanie poprawności zestawu lub wzorzec jest ignorowany.
5. Jeśli zestaw sprawdzania poprawności jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, wszystkie wartości z wszystkich zestawów sprawdzania poprawności są dozwolone.
6. Jeśli wzorzec sprawdzania poprawności jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, wszelkie wartości, które pasuje do żadnego z wzorców są dozwolone.
7. Jeśli zestaw sprawdzania poprawności jest zdefiniowany w co najmniej jedną rolę, a wzorzec sprawdzania poprawności jest zdefiniowany w innej roli dla tego samego parametru polecenia cmdlet, zestaw sprawdzania poprawności jest ignorowana, a do pozostałych wzorców sprawdzania poprawności zostanie zastosowana reguła (6).

Poniżej przedstawiono przykładowy sposób role są łączone zgodnie z tymi zasadami:

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

Wszystkie pola w pliku możliwości roli są dodawane do zbiorczego zestawu poleceń zewnętrznych dopuszczalny rozmiar, aliasy, dostawców i skrypty uruchamiania. Polecenia, alias, dostawca lub skryptu w jedną rolę możliwości jest dostępna dla użytkownika JEA.

Uważaj upewnić się, że połączony zestaw dostawców z jednej roli funkcji i poleceń cmdlet/funkcje/poleceń z innego nie zezwalaj użytkownikom niezamierzonego dostępu do zasobów systemowych.
Na przykład, jeśli zezwala na jedną rolę `Remove-Item` polecenia cmdlet, a drugi umożliwia `FileSystem` dostawcy, są narażeni użytkownika JEA usuwanie dowolnych plików na komputerze. Dodatkowe informacje na temat identyfikowania czynnych uprawnień użytkowników można znaleźć w [inspekcji JEA](audit-and-report.md) artykułu.

## <a name="next-steps"></a>Następne kroki

[Utwórz plik konfiguracji sesji](session-configurations.md)
