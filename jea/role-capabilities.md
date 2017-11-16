---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, programu powershell, zabezpieczeń"
title: "Możliwości roli JEA"
ms.openlocfilehash: 10f5f390daccbb012be6ee7272041e777810ee12
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="jea-role-capabilities"></a>Możliwości roli JEA

> Dotyczy: środowiska Windows PowerShell 5.0

Podczas tworzenia punktu końcowego JEA, musisz zdefiniować co najmniej jeden "roli funkcji" opisujące *co* ktoś zrobić w sesji JEA.
Możliwość roli jest plik danych programu PowerShell z rozszerzeniem .psrc, które wyświetla listę wszystkich poleceń cmdlet, funkcji, dostawców i zewnętrzne programy, które powinny być udostępniane łączenia użytkowników.

W tym temacie opisano, jak utworzyć plik programu PowerShell roli możliwości użytkowników JEA.

## <a name="determine-which-commands-to-allow"></a>Ustalić, jakie polecenia, aby umożliwić

Pierwszym krokiem podczas tworzenia pliku możliwości roli jest określenie, co użytkownicy, którzy mają przypisaną rolę wymaga dostępu do.
Wymagania, ten proces zbierania może trochę potrwać, ale jest bardzo ważne procesu.
Przyznawanie użytkownikom dostępu do zbyt mało polecenia cmdlet i funkcje może uniemożliwić ich pobierania ich pracy.
Zezwalania na dostęp do zbyt wielu poleceń cmdlet i funkcje może prowadzić do użytkowników czynności więcej niż przeznaczone z ich uprawnieniami administratora niejawne osłabienia Twojej strony zabezpieczeń.

Jak przejść na ten tego procesu zależy od organizacji i cele, jednak poniższe porady mogą pomóc, upewnij się, że jesteś na prawidłową ścieżkę.

1. **Zidentyfikuj** użytkowników poleceń używasz do wykonywania pracy. Może to obejmować badanie personel działu informatycznego, sprawdzanie skryptów automatyzacji lub analizowania zapisy sesji programu PowerShell lub dzienniki.
2. **Aktualizacja** używać narzędzi wiersza polecenia, aby ich odpowiedniki programu PowerShell, jeśli to możliwe, najlepszą inspekcji i JEA dostosowanie doświadczenie. Nie można ograniczyć programy zewnętrzne jako częściami jako natywnych poleceń cmdlet programu PowerShell i funkcji w ramach zasad JEA.
3. **Ogranicz** zakresu polecenia cmdlet, jeśli to konieczne tylko pozwalają określonych parametrów lub wartości parametrów. Jest to szczególnie ważne, jeśli użytkownicy powinni być tylko możliwość zarządzania części systemu.
4. **Utwórz** niestandardowych funkcji w celu zastąpienia złożonych polecenia lub poleceń, które są trudne do ograniczyć w ramach zasad JEA. Proste funkcję, która opakowuje złożone polecenia lub stosuje logikę weryfikacji dodatkowe mogą oferować dodatkową kontrolę dla uproszczenia administratorów i użytkowników końcowych.
5. **Test** listy zakresie dozwolonym poleceń użytkowników i/lub automatyzacji usług i Dostosuj odpowiednio do potrzeb.

Należy pamiętać, że polecenia w sesji JEA są często uprawnień uruchom admin (lub w inny sposób z podniesionymi uprawnieniami).
Staranne wybieranie dostępnych poleceń ważne jest, aby upewnić się, że punkt końcowy JEA nie zezwala użytkownik nawiązujący połączenie podniesienie poziomu uprawnień.
Poniżej przedstawiono kilka przykładów poleceń, których można użyć złośliwie Jeśli dozwolone w stanie nieograniczonego.
Zauważ, że to nie jest kompletną listą i należy używać tylko jako punktu wyjścia ostrzegawcze.

### <a name="examples-of-potentially-dangerous-commands"></a>Przykłady poleceń potencjalnie niebezpiecznych

Ryzyko | Przykład | Pokrewne polecenia
-----|---------|-----------------
Udzielanie uprawnień administratora, aby pominąć JEA użytkownik nawiązujący połączenie | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Uruchomienia dowolnego kodu, np. złośliwego oprogramowania, luki w zabezpieczeniach lub niestandardowych skryptów do obejścia zabezpieczeń | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Utwórz plik możliwości roli

Można utworzyć nowy plik możliwości roli programu PowerShell z [PSRoleCapabilityFile nowy](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) polecenia cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Wynikowy plik możliwości roli można go otworzyć w edytorze tekstów i zmodyfikowane w celu umożliwienia żądanych poleceń dla roli.
Dokumentacja pomocy programu PowerShell zawiera kilka przykładów sposobu konfigurowania pliku.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Stosowanie poleceń cmdlet programu PowerShell i funkcji

Aby zezwolić użytkownikom na uruchamianie poleceń cmdlet programu PowerShell lub funkcje, Dodaj nazwę polecenia cmdlet lub funkcja do VisbibleCmdlets lub VisibleFunctions pól.
Jeśli nie masz pewności, czy polecenie jest polecenie cmdlet lub funkcji, można uruchomić `Get-Command <name>` i sprawdź właściwość "CommandType" w danych wyjściowych.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Czasami zakres konkretnego polecenia cmdlet lub funkcji jest zbyt szerokie do własnych potrzeb.
Administrator DNS, na przykład potrzeby prawdopodobnie tylko dostęp do Uruchom ponownie usługę DNS.
W środowisku wielu dzierżawców gdzie dzierżaw uzyskają dostęp do narzędzia do samoobsługowego zarządzania dzierżaw powinien być ograniczony do zarządzanie za pomocą ich własnych zasobów.
W tych przypadkach można ograniczyć, parametry, które są dostępne z polecenie cmdlet lub funkcji.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

W bardziej zaawansowanych scenariuszy, może być również konieczne ograniczanie ktoś może dostarczyć wartości dla tych parametrów.
Możliwości roli pozwalają zdefiniować zestaw dozwolonych wartości lub wzorzec wyrażenia regularnego, które jest obliczane w celu ustalenia, czy jest dozwolone w określonych danych wejściowych.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Typowe parametry programu PowerShell](https://technet.microsoft.com/en-us/library/hh847884.aspx) są zawsze dozwolone, nawet jeśli ograniczysz dostępnych parametrów.
> Użytkownik nie powinny jawnie zawierać je w polu Parametry.

W poniższej tabeli opisano różne sposoby, które można dostosować widoczne polecenia cmdlet lub funkcji.
Można mieszać i zgodna z żadną poniżej w VisibleCmdlets pola.

Przykład                                                                                      | Przypadek użycia
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` lub `@{ Name = 'My-Func' }`                                                       | Zezwala użytkownikowi na uruchamianie `My-Func` bez żadnych ograniczeń na parametry.
`'MyModule\My-Func'`                                                                         | Zezwala użytkownikowi na uruchamianie `My-Func` z modułu `MyModule` bez żadnych ograniczeń na parametry.
`'My-*'`                                                                                     | Zezwala użytkownikowi na uruchamianie polecenia cmdlet ani funkcja ze zleceniem `My`.
`'*-Func'`                                                                                   | Zezwala użytkownikowi na Uruchom polecenie cmdlet ani funkcji z rzeczownikiem `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` i/lub `Param2` parametrów. Można podać wartości parametrów.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru. Tylko "Wartość1" i "Wartość2" mogą być dostarczane do parametru.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru. Można podać wartości, zaczynając od "contoso" do parametru.


> [!WARNING]
> Aby uzyskać najlepsze rozwiązania w zakresie zabezpieczeń nie zaleca się użyć symboli wieloznacznych, definiując widoczne poleceń cmdlet lub funkcji.
> Zamiast tego należy jawnie listy każdego zaufanych polecenie, aby upewnić się, że wszystkie inne polecenia, które współużytkują tego samego schematu nazewnictwa przypadkowo są autoryzowane.

Zarówno ValidatePattern i ValidateSet nie można zastosować do tego samego polecenia cmdlet lub funkcji.

Jeśli to zrobisz, ValidatePattern przesłoni ValidateSet.

Aby uzyskać więcej informacji na temat ValidatePattern, zapoznaj się z [to *Witaj, Twórco skryptów!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) i [wyrażeń regularnych programu PowerShell](https://technet.microsoft.com/en-us/library/hh847880.aspx) odwołania zawartości.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Stosowanie zewnętrznych poleceń i skryptów programu PowerShell

Aby zezwolić użytkownikom na uruchamianie plików wykonywalnych i skryptów programu PowerShell (ps1) w sesji JEA, należy dodać pełną ścieżkę do każdego programu w polu VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Zalecane jest, gdzie to możliwe, użyj programu PowerShell polecenia cmdlet/funkcja odpowiedniki zewnętrznych plików wykonywalnych, zezwolić, ponieważ mają kontroli nad którym parametry są dozwolone z poleceń cmdlet programu PowerShell/funkcje.

Wiele plików wykonywalnych umożliwiają zarówno odczytać bieżący stan, a następnie zmień ją tak, zapewniając innych parametrów.

Rozważmy na przykład rolę Administrator serwera plików, który chce, aby sprawdzić, które udziały sieciowe są obsługiwane przez komputer lokalny.
Jednym ze sposobów sprawdzenia, jest użycie `net share`.
Jednakże, dzięki czemu net.exe jest bardzo niebezpieczne, ponieważ administrator może równie łatwo używać polecenia w celu uzyskania uprawnień administratora z `net group Administrators unprivilegedjeauser /add`.
Lepszym rozwiązaniem jest umożliwienie [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) które osiąga ten sam rezultat, ale ma znacznie bardziej ograniczony zakres.

Podczas wprowadzania poleceń zewnętrznych dostępne dla użytkowników w sesji JEA, należy zawsze podać pełną ścieżkę do pliku wykonywalnego, aby upewnić się o podobnej nazwie (i potencjalnie malicous) program umieszczone w innym miejscu w systemie nie są wykonywane zamiast tego.

### <a name="allowing-access-to-powershell-providers"></a>Zezwalanie na dostęp do dostawcy programu PowerShell

Domyślnie nie dostawcy programu PowerShell są dostępne w sesji JEA.

To jest głównie zmniejszenia ryzyka poufne informacje i ustawienia konfiguracji są ujawniane użytkownik nawiązujący połączenie.

Jeśli to konieczne, można zezwolić na dostęp do dostawcy programu PowerShell przy użyciu `VisibleProviders` polecenia.
Aby zapoznać się z pełną listą dostawców, uruchamiania `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Proste zadania, które wymagają dostępu do systemu plików, rejestru, magazynu certyfikatów lub innych poufnych dostawców należy również rozważyć pisanie niestandardowej funkcji, która współpracuje z dostawcą w imieniu użytkownika.
Funkcje, polecenia cmdlet i programów zewnętrznych, które są dostępne w sesji JEA nie podlegają takich samych ograniczeń jako JEA — domyślnie uzyskać dostęp do każdego dostawcy.
Należy również rozważyć przy użyciu [dysku użytkownika](session-configurations.md#user-drive) podczas kopiowania plików do/z punktu końcowego JEA jest wymagana.

### <a name="creating-custom-functions"></a>Tworzenie funkcji niestandardowej

Można tworzyć niestandardowe funkcji w pliku możliwości roli uprościć złożone zadania dla użytkowników końcowych.
Funkcje niestandardowe są także przydatne, gdy wymagają logikę weryfikacji zaawansowane wartości parametrów polecenia cmdlet.
Proste funkcje można pisać w **FunctionDefinitions** pola:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Nie zapomnij dodać nazwę funkcji niestandardowych do **VisibleFunctions** pól, co może być uruchamiane przez użytkowników JEA.


Treść funkcji niestandardowych (bloku skryptu) działa w trybie język domyślny dla systemu i nie podlega JEA w języku ograniczenia.
Oznacza to, że funkcji można uzyskiwać dostęp do systemu plików i rejestru i uruchamiania poleceń, które zostały utworzone widoczne w pliku możliwości roli.
Zwrócić uwagę, aby uniknąć dowolnego kodu ma być uruchamiany przy użyciu parametrów i uniknąć potokowanie danych wejściowych użytkownika bezpośrednio do polecenia cmdlet, takich jak `Invoke-Expression`.

W powyższym przykładzie, można zauważyć, że nazwa FQDN modułu (FQMN) `Microsoft.PowerShell.Utility\Select-Object` użyto zamiast skrócona `Select-Object`.
Funkcje zdefiniowane w plikach możliwości roli nadal obowiązują na zakres JEA sesji, która obejmuje funkcje serwera proxy JEA tworzy ograniczyć istniejących poleceń.

Select-Object jest domyślnie ograniczonego polecenia cmdlet we wszystkich sesjach JEA, który nie pozwala na wybranie dowolnego właściwości obiektów.
Aby używać nieograniczonego Select-Object w funkcjach, określając FQMN musi jawne żądanie pełnego wdrożenia.
Ograniczone dowolnym poleceniu cmdlet w sesji JEA będzie mieć takie samo zachowanie, gdy została wywołana z funkcji, zgodnie z jego środowiska PowerShell [pierwszeństwa poleceń](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Jeśli piszesz wiele funkcji niestandardowych, może być łatwiej umieść je w [moduł skryptu programu PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
Następnie można wprowadzić te funkcje widoczne w sesji JEA, korzystając z pola VisibleFunctions, jak w przypadku modułów wbudowane i innych firm.

## <a name="place-role-capabilities-in-a-module"></a>Umieść funkcji ról w module

Aby dla programu PowerShell znaleźć plik możliwości roli muszą być przechowywane w folderze "RoleCapabilities" w module środowiska PowerShell.
Moduł mogą być przechowywane w dowolnym folderze zawarte w `$env:PSModulePath` zmiennej środowiskowej, jednak należy nie umieszczać w System32 (zastrzeżone dla wbudowanych modułów) lub w folderze gdzie niezaufanych, łączenie użytkowników można zmodyfikować plików.
Poniżej przedstawiono przykład tworzenia podstawowych moduł skryptu programu PowerShell o nazwie *ContosoJEA* w ścieżce "Program Files".

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Zobacz [opis modułu programu PowerShell](https://msdn.microsoft.com/en-us/library/dd878324.aspx) uzyskać więcej informacji o moduły programu PowerShell, manifesty modułu i PSModulePath zmiennej środowiskowej.

## <a name="updating-role-capabilities"></a>Aktualizowanie roli


Należy zaktualizować plik możliwości roli w dowolnym momencie przez po prostu zapisywanie zmian w pliku możliwości roli.
Wszystkie nowe sesje JEA uruchomiony po zaktualizowaniu możliwości roli będzie odzwierciedlać poprawione funkcje.

To dlatego tak ważne jest kontrolowanie dostępu do folderu możliwości roli.
Tylko wysoce zaufanych administratorów powinna być możliwość zmiany roli plikach możliwości.
Niezaufanych użytkownik może zmienić plikach możliwości roli, łatwo przyznanie sobie dostępu do poleceń cmdlet, które zezwolić im na podniesienie ich uprawnień.


Dla administratorów chcących blokowania dostępu do funkcji roli upewnij się, że System lokalny ma dostęp do odczytu do plików możliwości roli i zawierające moduły.

## <a name="how-role-capabilities-are-merged"></a>Jak są scalane możliwości roli

Użytkownicy mogą uzyskać dostęp do wiele możliwości roli po wprowadzeniu JEA sesji w zależności od roli mapowania w [pliku konfiguracji sesji](session-configurations.md).
W takim przypadku JEA próbuje dla użytkownika *najbardziej ograniczająca* zestaw poleceń, przy użyciu jednej z ról.

**VisibleCmdlets i VisibleFunctions**

Najbardziej złożonej logiki scalania dotyczy poleceń cmdlet i funkcje, które mogą ich parametrów i wartości parametrów w ramach zasad JEA ograniczone.

Dostępne są następujące reguły:

1. Jeśli polecenie cmdlet tylko stają się widoczne w jedną rolę, będą widoczne dla użytkowników z żadnych ograniczeń odpowiednich parametrów.
2. Jeśli polecenie cmdlet stają się widoczne w więcej niż jednej roli, a każda rola ma takich samych ograniczeń na polecenia cmdlet, polecenie cmdlet będą widoczne dla użytkowników z tych ograniczeń.
3. Jeśli polecenie cmdlet stają się widoczne w więcej niż jednej roli, a tych rolach inny zestaw parametrów, polecenia cmdlet i wszystkich parametrów zdefiniowanych w każdej roli będzie widoczny dla użytkownika. Jeśli jedna rola nie ma ograniczenia dotyczące parametrów, dozwolone będą wszystkie parametry.
4. Jeśli jedną rolę definiuje zestaw weryfikacji lub wzorca sprawdzania poprawności dla parametru polecenia cmdlet i innych ról pozwala parametru, ale nie ograniczenie wartości parametrów, sprawdzanie poprawności zestawu lub wzorzec zostanie zignorowany.
5. Zestaw weryfikacji jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, dozwolone będą wszystkie wartości ze wszystkich zbiorów weryfikacji.
6. Jeśli wzorzec weryfikacji jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, dozwolone wartości, które spełniają wzorce.
7. Jeśli zestaw weryfikacji jest zdefiniowany w jedną lub więcej ról, a wzorzec weryfikacji jest zdefiniowany w innej roli dla tego samego parametru polecenia cmdlet, jest ignorowana, ustaw weryfikacji i reguła (6) jest stosowana do pozostałych wzorców weryfikacji.

Poniżej przedstawiono przykładowy sposób role są łączone zgodnie z następującymi regułami:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, ScriptsToProcess VisibleAliases, VisibleProviders,**

Wszystkie pola w pliku możliwości roli po prostu są dodawane do zbiorczego zestawu dopuszczalny poleceń zewnętrznych, aliasy dostawców i skrypty uruchamiania.
Polecenia, aliasu, dostawcy lub dostępne w jednym możliwości roli skryptu będzie dostępne dla użytkownika JEA.

Uważaj, upewnij się, że połączony zestaw dostawców z jednego możliwości roli i poleceń cmdlet/funkcje/poleceń z innego nie zezwalają na użytkowników łączących niezamierzone dostęp do zasobów systemowych.
Na przykład, jeśli zezwala na jedną rolę `Remove-Item` polecenia cmdlet, a druga zezwala `FileSystem` dostawcy, są narażeni na ataki użytkownika JEA usuwanie dowolnych plików na komputerze.
Dodatkowe informacje na temat identyfikowania czynnych uprawnień użytkowników znajdują się w [inspekcji tematu JEA](audit-and-report.md).

## <a name="next-steps"></a>Następne kroki

- [Utwórz plik konfiguracji sesji](session-configurations.md)

