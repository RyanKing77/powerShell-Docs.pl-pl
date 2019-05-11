---
ms.date: 06/12/2017
keywords: jea, programu powershell, zabezpieczeń
title: Możliwości roli usługi JEA
ms.openlocfilehash: 528b41c0e2ffdcfed3251fb0f714c649e7290761
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229551"
---
# <a name="jea-role-capabilities"></a>Możliwości roli usługi JEA

> Dotyczy: Windows PowerShell 5.0

Podczas tworzenia punktu końcowego JEA, należy zdefiniować co najmniej jeden "możliwości roli" zawierające *co* ktoś można wykonać w ramach sesji usługi JEA.
Funkcja roli jest plikiem danych środowiska PowerShell z rozszerzeniem .psrc, które wyświetla listę wszystkich poleceń cmdlet, funkcji, dostawców i zewnętrznych programów, które powinny zostać udostępnione do procesu łączenia użytkowników.

W tym temacie opisano, jak utworzyć plik możliwości roli programu PowerShell dla użytkowników usługi JEA.

## <a name="determine-which-commands-to-allow"></a>Określić, jakie polecenia, aby umożliwić

Pierwszym krokiem podczas tworzenia pliku możliwości roli jest należy wziąć pod uwagę, jakie użytkownicy, którzy mają przypisaną rolę będą potrzebowali dostępu do.
To wymaganie procesu zbierania może wymagać trochę czasu, ale jest bardzo ważne procesu.
Zapewniając użytkownikom dostęp do zbyt małej liczby poleceń cmdlet i funkcji może uniemożliwić ich wprowadzenie ich pracę.
Zezwalanie na dostęp do zbyt wielu poleceń cmdlet i funkcji może prowadzić do użytkowników, wykonując bardziej niż planowano z ich uprawnieniami administratora niejawne osłabienia Twoje wystąpienie zabezpieczeń.

Jak obniżyć informacji na temat tego procesu zależy od organizacji i cele, jednak poniższe porady mogą pomóc upewnić się, że jesteś na prawidłową ścieżkę.

1. **Identyfikowanie** korzystają użytkownicy polecenia do wykonywania ich zadań. Może to obejmować badanie informatykami, sprawdzanie skryptów automatyzacji lub analizowanie zapisy sesji programu PowerShell lub dzienniki.
2. **Aktualizacja** na użytek narzędzi wiersza polecenia do odpowiedników środowiska PowerShell, jeśli jest to możliwe, najlepsze inspekcji i JEA dostosowywania środowiska. Nie można ograniczyć zewnętrznych programów jako dokładnością jako natywnych poleceń cmdlet programu PowerShell i funkcji jea.
3. **Ogranicz** zakresu poleceń cmdlet, jeśli to konieczne tylko pozwalają określonych parametrów lub wartości parametrów. Jest to szczególnie ważne, jeśli użytkownicy tylko powinny mieć możliwość zarządzania części systemu.
4. **Utwórz** funkcji niestandardowych w celu zastąpienia polecenia złożonych lub polecenia, które są trudne do ograniczenia jea. Prostej funkcji, która opakowuje złożone polecenia lub stosuje logikę dodatkowe sprawdzenie poprawności oferują dodatkową kontrolę dla uproszczenia administratorów i użytkowników końcowych.
5. **Test** o określonym zakresie listę dopuszczalnych poleceń z użytkowników i/lub automatyzacji usług i dostosować zgodnie z potrzebami.

Koniecznie należy pamiętać, że polecenia w sesji JEA często uprawnieniami Uruchom za pomocą administratora (lub inaczej podwyższonego poziomu uprawnień).
Staranne wybieranie dostępnych poleceń ważne jest, aby upewnić się, że punkt końcowy usługi JEA nie zezwala na użytkownik nawiązujący połączenie do podniesienia swoich uprawnień.
Poniżej przedstawiono kilka przykładów poleceń, które mogą służyć złośliwie Jeśli jest to dozwolone w stanie nieograniczone.
Pamiętaj, że to nie jest kompletną listą i powinna służyć wyłącznie jako punktu wyjścia ostrzegawcze.

### <a name="examples-of-potentially-dangerous-commands"></a>Przykłady poleceń potencjalnie niebezpiecznych

Ryzyko | Przykład | Powiązane polecenia
-----|---------|-----------------
Udzielanie użytkownik nawiązujący połączenie z uprawnieniami administratora w celu OBEJŚCIE usługi JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Uruchamiania dowolnego kodu, takich jak złośliwe oprogramowanie luki w zabezpieczeniach i niestandardowe skrypty do obejścia zabezpieczeń | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Utwórz plik możliwości roli

Można utworzyć nowy plik możliwości roli programu PowerShell przy użyciu [New PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) polecenia cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Wynikowy plik możliwości roli można otworzyć w edytorze tekstów i zmodyfikowane w celu zezwalania na żądaną polecenia dla roli.
Dokumentacja pomocy programu PowerShell zawiera kilka przykładów sposobu konfigurowania pliku.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Polecenia cmdlet programu PowerShell i funkcji

Aby autoryzować użytkowników o uruchomienie polecenia cmdlet programu PowerShell lub funkcje, należy dodać nazwę polecenia cmdlet lub funkcji do VisibleCmdlets lub VisibleFunctions pól.
Jeśli nie masz pewności, czy polecenie jest polecenie cmdlet lub funkcji, możesz uruchomić `Get-Command <name>` i sprawdź właściwość "CommandType" w danych wyjściowych.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Czasami zakresu określonego polecenia cmdlet lub funkcji jest zbyt ogólnym, na potrzeby użytkowników.
Administrator systemu DNS, na przykład wymaga jedynie prawdopodobnie uzyskać dostęp do ponownego uruchomienia usługi DNS.
W środowisku z wieloma dzierżawami, gdy dzierżawcy uzyskują dostęp do narzędzia do samoobsługowego zarządzania dzierżaw, należy ograniczyć do zarządzania za pomocą ich własnych zasobów.
W takich przypadkach można ograniczyć, które parametry są udostępniane z polecenia cmdlet lub funkcji.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

W bardziej zaawansowanych scenariuszy może być również konieczne ograniczenie wartości, które osoba może dostarczyć do tych parametrów.
Możliwości roli pozwalają zdefiniować zestaw dozwolonych wartości lub wzorzec wyrażenia regularnego, który jest oceniany w celu określenia, czy dany danych wejściowych może.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> [Typowe parametry programu PowerShell](https://technet.microsoft.com/library/hh847884.aspx) zawsze dozwolone, nawet wtedy, gdy ograniczenia dostępnych parametrów.
> Należy nie jawnie ich listę w polu Parametry.

W poniższej tabeli opisano różne sposoby, które można dostosować widoczne polecenia cmdlet lub funkcji.
Możesz mieszać i dopasowywać znajdujących się poniżej w VisibleCmdlets pola.

Przykład                                                                                      | Przypadek użycia
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` lub `@{ Name = 'My-Func' }`                                                       | Zezwala użytkownikowi na uruchamianie `My-Func` bez żadnych ograniczeń na parametry.
`'MyModule\My-Func'`                                                                         | Zezwala użytkownikowi na uruchamianie `My-Func` z modułu `MyModule` bez żadnych ograniczeń na parametry.
`'My-*'`                                                                                     | Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji za pomocą zlecenie `My`.
`'*-Func'`                                                                                   | Zezwala użytkownikowi na uruchamianie dowolnego polecenia cmdlet lub funkcji z rzeczownikiem `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` i/lub `Param2` parametrów. Dowolna wartość mogą być dostarczane do parametrów.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru. Tylko "Wartość1" i "Wartość2" mogą być dostarczane do parametru.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Zezwala użytkownikowi na uruchamianie `My-Func` z `Param1` parametru. Żadnej wartości, zaczynając od "contoso" mogą być dostarczane do parametru.

> [!WARNING]
> Aby uzyskać najlepsze rozwiązania w zakresie zabezpieczeń nie zaleca się używać symboli wieloznacznych, podczas definiowania widoczne dla poleceń cmdlet lub funkcji.
> Zamiast tego należy jawnie listę każdego zaufanych polecenia, aby upewnić się, że żadne polecenia, które współużytkują ten sam schemat nazewnictwa przypadkowo uprawnienia.

Nie można zastosować ValidatePattern i ValidateSet do tego samego polecenia cmdlet lub funkcji.

Jeśli to zrobisz, ValidatePattern spowoduje zastąpienie ValidateSet.

Aby uzyskać więcej informacji na temat ValidatePattern, zapoznaj się [to *Hey, Scripting Guy!* wpis](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) i [wyrażeń regularnych w programie PowerShell](https://technet.microsoft.com/library/hh847880.aspx) odwoływać się do zawartości.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Dzięki niemu agencje poleceń zewnętrznych i skryptów programu PowerShell

Aby zezwolić użytkownikom na uruchamianie plików wykonywalnych i skryptów programu PowerShell (.ps1) w ramach sesji usługi JEA, musisz dodać pełną ścieżkę do każdego programu, w polu VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Zalecane jest, jeśli to możliwe, użyj odpowiedników funkcji/polecenia cmdlet programu PowerShell zewnętrznych plików wykonywalnych, autoryzowane, ponieważ masz pełną kontrolę nad tym, którzy parametrów są dozwolone w przypadku poleceń cmdlet programu PowerShell/funkcji.

Wiele plików wykonywalnych umożliwiają zarówno odczyt bieżącego stanu, a następnie zmienić je po prostu, podając różne parametry.

Na przykład należy wziąć pod uwagę w roli administratora serwera plików, kto chce, aby sprawdzić, które udziały sieciowe są hostowane przez komputer lokalny.
Jednym ze sposobów, aby sprawdzić, jest użycie `net share`.
Jednakże, dzięki czemu net.exe jest bardzo niebezpieczny, ponieważ administrator może równie łatwo polecenie służy do uzyskania uprawnień administratora za pomocą `net group Administrators unprivilegedjeauser /add`.
Lepszym rozwiązaniem jest umożliwienie [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) które osiąga ten sam wynik, ale ma bardziej ograniczony zakres.

Podczas wprowadzania poleceń zewnętrznych dostępnych dla użytkowników w ramach sesji usługi JEA, zawsze należy określić pełną ścieżkę do pliku wykonywalnego, aby upewnić się, program o podobnej nazwie (i potencjalnie złośliwych) umieszczone w innym miejscu w systemie nie są wykonywane zamiast tego.

### <a name="allowing-access-to-powershell-providers"></a>Zezwalanie na dostęp do dostawcy programu PowerShell

Domyślnie żaden dostawca programu PowerShell są dostępne w sesji JEA.

To jest głównie zmniejszenia ryzyka poufnych informacji i ustawienia konfiguracji zostały ujawnione użytkownik nawiązujący połączenie.

Gdy jest to konieczne, można zezwolić na dostęp do dostawcy programu PowerShell przy użyciu `VisibleProviders` polecenia.
Aby uzyskać pełną listę dostawców, uruchamianie `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Proste zadania, które wymagają dostępu do systemu plików, rejestru, magazynu certyfikatów lub innych dostawców poufnych możesz też rozważyć pisanie niestandardowej funkcji, która współpracuje z dostawcą w imieniu użytkownika.
Funkcje, poleceń cmdlet i zewnętrznych programów, które są dostępne w ramach sesji usługi JEA nie podlegają tych samych ograniczeń, jak JEA — mogą uzyskiwać dostęp do dowolnego dostawcy domyślnie.
Ponadto należy wziąć pod uwagę przy użyciu [dysku użytkownika](session-configurations.md#user-drive) podczas kopiowania plików do/z punktu końcowego JEA jest wymagana.

### <a name="creating-custom-functions"></a>Tworzenie funkcji niestandardowych

Można tworzyć niestandardowe funkcje w pliku możliwości roli, aby uprościć złożone zadania dla użytkowników końcowych.
Funkcje niestandardowe są również przydatne, gdy potrzebujesz logikę weryfikacji zaawansowane o wprowadzenie wartości parametrów polecenia cmdlet.
Możesz pisać proste funkcje **FunctionDefinitions** pola:

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
> Nie zapomnij dodać nazwę Twojej funkcji niestandardowych do **VisibleFunctions** pola, aby mogły być uruchamiane przez użytkowników usługi JEA.

Treść funkcji niestandardowych (blok skryptu) działa w trybie język domyślny dla systemu i nie jest przedmiotem ograniczeń języka firmy JEA.
Oznacza to, czy funkcje można uzyskać dostęp do systemu plików i rejestru i uruchamiania poleceń, które zostały utworzone widoczny w pliku możliwości roli.
Pamiętaj, aby uniknąć, dzięki czemu dowolny kod ma być uruchamiany przy użyciu parametrów i uniknąć dane wejściowe użytkownika potokowanie bezpośrednio do polecenia cmdlet, takich jak `Invoke-Expression`.

W powyższym przykładzie można zauważyć, że nazwa FQDN modułu (FQMN) `Microsoft.PowerShell.Utility\Select-Object` był używany zamiast skrót `Select-Object`.
Funkcje zdefiniowane w plikach możliwości roli są nadal podlega procesowi zakresu sesji JEA, który zawiera funkcje serwera proxy usługi JEA tworzy ograniczenie istniejące polecenia.

Select-Object jest domyślnie ograniczone polecenia cmdlet we wszystkich sesjach JEA, który nie zezwala na wybranie dowolnego właściwości obiektów.
Aby używać nieograniczonego Select-Object w przypadku funkcji, możesz jawne żądanie pełną implementację, określając FQMN.
Każdego ograniczone polecenia cmdlet w sesji JEA będzie mieć takie samo zachowanie, gdy wywoływana z funkcji, zgodnie z programu PowerShell [polecenia pierwszeństwo](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Jeśli piszesz wiele niestandardowych funkcji może być łatwiej je umieszczać [modułu skryptu PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
Następnie można wprowadzić te funkcje widoczne w sesji JEA, korzystając z pola VisibleFunctions, jak w przypadku modułów wbudowane i innych firm.

Karta zakończenia ma działać prawidłowo w sesjach JEA możesz musi zawierać wbudowanej funkcji `tabexpansion2` w **VisibleFunctions** listy.

## <a name="place-role-capabilities-in-a-module"></a>W module umieścić możliwości roli

Aby dla programu PowerShell, aby znaleźć plik możliwości roli muszą być przechowywane w folderze "RoleCapabilities" w module programu PowerShell.
Moduł mogą być przechowywane w dowolnym folderze zawarte w `$env:PSModulePath` zmiennej środowiskowej, jednak należy nie umieszczać w System32 (zarezerwowane dla wbudowanych modułów) lub folderu gdzie niezaufanych, łączenie użytkowników można zmodyfikować pliki.
Poniżej znajduje się przykład tworzenia podstawowych moduł skrypt programu PowerShell o nazwie *ContosoJEA* w ścieżce "Program Files".

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

Zobacz [opis modułu programu PowerShell](https://msdn.microsoft.com/library/dd878324.aspx) Aby uzyskać więcej informacji na temat modułów programu PowerShell, moduł manifesty i zmienną środowiskową PSModulePath.

## <a name="updating-role-capabilities"></a>Aktualizowanie możliwości roli

Aby zaktualizować plik możliwości roli w dowolnym momencie, po prostu zapisywanie zmian w pliku możliwości roli.
Wszystkie nowe sesje JEA pracę po zaktualizowaniu możliwości roli będą odzwierciedlać poprawione możliwości.

Jest to, dlaczego kontrola dostępu do folderu możliwości roli jest tak ważny.
Tylko wysoce zaufanych administratorów powinno być możliwe na zmianę plików możliwości roli.
Niezaufanego użytkownika mogą zmieniać pliki możliwości roli, łatwo udzielenie się dostępu do poleceń cmdlet, co pozwala je do podniesienia swoich uprawnień.

Dla administratorów chcących blokowanie dostępu do możliwości roli upewnij się, że System lokalny ma dostęp do odczytu do plików funkcji roli i zawierającego moduły.

## <a name="how-role-capabilities-are-merged"></a>Jak są scalane możliwości roli

Użytkownicy mogą uzyskać dostęp do wiele możliwości roli po użytkownik podał sesję JEA w zależności od roli mapowania w [plik konfiguracji sesji](session-configurations.md).
W takim przypadku JEA próbuje przyznać użytkownikowi *restrykcyjny* zestaw poleceń dozwolone przez dowolną rolę.

**VisibleCmdlets i VisibleFunctions**

Najbardziej złożoną logikę scalanie wpływa na poleceń cmdlet i funkcje, które mogą mieć ich parametrów i wartości parametrów ograniczone jea.

Dostępne są następujące reguły:

1. Jeśli polecenie cmdlet jest dostępne tylko widoczne w jednej roli, będzie widoczna dla użytkownika o wszelkich ograniczeń odpowiednich parametrów.
2. Jeśli polecenie cmdlet jest widoczny w więcej niż jednej roli, a każda rola ma ograniczenia tego samego polecenia cmdlet, polecenie cmdlet będzie widoczny dla użytkownika przy użyciu tych ograniczeń.
3. Jeśli polecenie cmdlet jest widoczny w więcej niż jednej roli, a każda rola umożliwia inny zbiór parametrów, polecenia cmdlet i wszystkich parametrów zdefiniowanych w każdej roli będą widoczne dla użytkownika. Jeśli jedna rola nie ma ograniczenia dotyczące parametrów, będą miały wszystkie parametry.
4. Jeśli jedna rola definiuje zestaw sprawdzania poprawności lub wzorca weryfikacji dla parametru polecenia cmdlet, a także innych ról pozwala parametru, ale nie ogranicza wartości parametrów, sprawdzanie poprawności zestawu lub wzorzec zostanie zignorowany.
5. Jeśli zestaw sprawdzania poprawności jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, może być wszystkie wartości z wszystkich zestawów sprawdzania poprawności.
6. Jeśli wzorzec sprawdzania poprawności jest zdefiniowany dla tego samego parametru polecenia cmdlet w więcej niż jednej roli, będą miały żadnych wartości, które pasuje do żadnego z wzorców.
7. Jeśli zestaw sprawdzania poprawności jest zdefiniowany w co najmniej jedną rolę, a wzorzec sprawdzania poprawności jest zdefiniowany w innej roli dla tego samego parametru polecenia cmdlet, zestaw sprawdzania poprawności jest ignorowana, a do pozostałych wzorców sprawdzania poprawności zostanie zastosowana reguła (6).

Poniżej przedstawiono przykładowy sposób role są łączone zgodnie z tymi zasadami:

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

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Wszystkie pola w pliku możliwości roli, po prostu są dodawane do zbiorczego zestawu poleceń zewnętrznych dopuszczalny rozmiar, aliasy, dostawców i skrypty uruchamiania.
Polecenia, alias, dostawca lub skryptu w jedną rolę możliwości będą dostępne dla użytkownika usługi JEA.

Uważaj upewnić się, że połączony zestaw dostawców z jednej roli funkcji i poleceń cmdlet/funkcje/poleceń z innego nie zezwalają na połączenia użytkowników niezamierzonego dostępu do zasobów systemowych.
Na przykład, jeśli zezwala na jedną rolę `Remove-Item` polecenia cmdlet, a drugi umożliwia `FileSystem` dostawcy, są narażeni użytkownika JEA usuwanie dowolnych plików na komputerze.
Dodatkowe informacje na temat identyfikowania czynnych uprawnień użytkowników można znaleźć w [inspekcji JEA temacie](audit-and-report.md).

## <a name="next-steps"></a>Następne kroki

- [Utwórz plik konfiguracji sesji](session-configurations.md)
