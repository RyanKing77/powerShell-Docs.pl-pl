---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Poprawki błędów w WMF 5.1
ms.openlocfilehash: 1e46d6d0419b3497450e6eaddbaa47456b004691
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222194"
---
# <a name="bug-fixes-in-wmf-51"></a>Poprawki błędów w WMF 5.1#

## <a name="bug-fixes"></a>Poprawki błędów ##

Następujące godne usterki usunięto w wersji WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>Autowykrywanie modułu pełni honoruje `$env:PSModulePath` ###

Moduł Autowykrywanie (ładowania modułów automatycznie bez jawnego Import-Module podczas wywoływania polecenia) została wprowadzona w WMF 3.
Jeśli wprowadzone, programu PowerShell sprawdzenie poleceń w `$PSHome\Modules` przed użyciem `$env:PSModulePath`.

To zachowanie, aby uwzględnić zmiany WMF 5.1 `$env:PSModulePath` całkowicie.
Dzięki temu moduł utworzonymi przez użytkownika, który definiuje poleceń programu PowerShell (np. `Get-ChildItem`) mają być automatycznie załadowane i poprawnie zastępowaniem wbudowanego polecenia.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Przekierowywanie plików nie dłużej stałe umieszczana w kodzie `-Encoding Unicode` ###

We wszystkich wcześniejszych wersjach programu PowerShell, nie było możliwe do kontrolowania kodowanie pliku używana przez operator przekierowania pliku, np. `Get-ChildItem > out.txt` ponieważ PowerShell dodane `-Encoding Unicode`.

Począwszy od wersji 5.1 WMF, można teraz zmienić kodowanie pliku przekierowania przez ustawienie `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Stałe regresji podczas uzyskiwania dostępu do elementów członkowskich `System.Reflection.TypeInfo` ###

Regresja wprowadzone w programie WMF 5.0 spowodowało przerwanie podczas uzyskiwania dostępu do elementów członkowskich `System.Reflection.RuntimeType`, np. `[int].ImplementedInterfaces`.
Ten problem został rozwiązany w wersji 5.1 WMF.


### <a name="fixed-some-issues-with-com-objects"></a>Stałe problemy z obiektami COM ###

WMF 5.0 wprowadzono nowe integratora modelu COM dla wywoływanie metod obiektów COM i uzyskiwaniem dostępu do właściwości obiektów COM.
Ten nowy obiekt tworzący powiązanie znacznie wyższą wydajność, ale również wprowadzić pewne usterki, które zostały ustalone w wersji 5.1 WMF.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Konwersje argumentów nie zawsze wykonano poprawnie ####

W poniższym przykładzie:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Metoda SendKeys spodziewa się ciągu, ale programu PowerShell nie zostały przekonwertowane char na ciąg odkładanie konwersja IDispatch::Invoke, używający VariantChangeType można wykonać konwersji, co w tym przykładzie spowodowało zamiast wysyłania kluczy "1", "7" i "3" Oczekiwano klucza Volume.Mute.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Wyliczalny obiektów COM nie zawsze obsługiwana poprawnie ####

PowerShell wylicza zazwyczaj większość obiektów wyliczalny, ale regresji wprowadzone w programie WMF 5.0 uniemożliwił wyliczanie obiektów COM, które implementuje interfejs IEnumerable.  Przykład:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

W powyższym przykładzie WMF 5.0 nieprawidłowo napisane Scripting.Dictionary do potoku zamiast wyliczania pary klucz wartość.

Zmiana adresów [wystawiać 1752224 w Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` niedozwolone wewnątrz klasy ###

WMF 5.0 wprowadzono klasy z weryfikacją literałów typu używany w klasach.
`[ordered]` wygląda jak literału typu, ale nie jest typem .NET wartość true.
WMF 5.0 niepoprawnie zgłosił błąd na `[ordered]` wewnątrz klasy:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Pomoc na temat tematy z wieloma wersjami nie działa. ###

Przed WMF 5.1, jeśli ma wiele wersji modułów zainstalowanych i wszystkie udostępnione tematu pomocy, na przykład about_PSReadline, `help about_PSReadline` zwróci wiele tematów można w sposób jednoznaczny Wyświetl Pomoc prawdziwe.

WMF 5.1 rozwiązuje to zwracając pomocy dla najnowszej wersji tego tematu.

`Get-Help` nie zapewnia możliwość określenia, która wersja ma dotyczyć pomoc dla.
Aby obejść ten problem, przejdź do katalogu, moduły i wyświetlić Pomoc bezpośrednio z narzędzia, takiego jak edytor ulubionych.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>Odczytywanie z STDIN PowerShell.exe przestał działać

Użyj klientów `powershell -command -` z natywne aplikacje do wykonania programu PowerShell przekazywanie w skrypcie za pośrednictwem STDIN Niestety to został uszkodzony z powodu inne zmiany jej host konsoli.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe tworzy kolekcji wykorzystania Procesora przy uruchamianiu

Sprawdź, czy została uruchomiona przy użyciu zasad grupy, aby uniknąć opóźnienia podczas logowania PowerShell korzysta z kwerendy usługi WMI.
Kwerenda WMI kończy się wstrzykiwania tzres.mui.dll do każdego procesu w systemie, ponieważ klasa WMI Win32_Process próbuje pobrać informacje dotyczące lokalnej strefy czasowej.
Powoduje to duży kolekcji procesora CPU w wmiprvse (host dostawcy WMI).
Poprawka jest Użyj interfejsu API Win32, aby pobrać te same informacje, a nie za pomocą usługi WMI.
