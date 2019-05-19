---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Poprawki błędów w programie WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856210"
---
# <a name="bug-fixes-in-wmf-51"></a>Poprawki błędów w programie WMF 5.1

## <a name="bug-fixes"></a>Poprawki błędów

Następujące istotne błędy zostały usunięte w program WMF 5.1:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>Autowykrywanie modułu pełni honoruje PSModulePath

Funkcja autowykrywania modułu (ładowanie modułów automatycznie bez jawnego Import-Module podczas wywoływania polecenia) została wprowadzona w 3 programu WMF. Kiedy wprowadzony, program PowerShell sprawdzane pod kątem poleceń w `$PSHome\Modules` przed użyciem `$env:PSModulePath`.

Program WMF 5.1 zmienia to zachowanie, aby uwzględnić `$env:PSModulePath` całkowicie. Dzięki temu dla modułu utworzonych przez użytkownika, który definiuje poleceń programu PowerShell (np. `Get-ChildItem`) mają być automatycznie załadowane i poprawnie zastępowaniem wbudowanego polecenia.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Przekierowywanie plików nie dłużej twardych kodów — kodowanie Unicode

We wszystkich poprzednich wersjach programu PowerShell było niemożliwe do kontrolowania kodowanie pliku używane przez plik operatora przekierowania.

Począwszy od programu WMF 5.1 można teraz zmienić kodowanie pliku przekierowania, ustawiając `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Naprawiono regresję podczas uzyskiwania dostępu do elementów członkowskich System.Reflection.TypeInfo

Regresja wprowadzone w programie WMF 5.0 Przerwano uzyskiwania dostępu do elementów członkowskich `System.Reflection.RuntimeType`, na przykład `[int].ImplementedInterfaces`. Ten błąd został naprawiony w WMF 5.1.

### <a name="fixed-some-issues-with-com-objects"></a>Rozwiązano niektóre problemy z obiektami COM

Program WMF 5.0 wprowadzono nowe integratora modelu COM dla wywołania metod obiektów COM i uzyskiwania dostępu do właściwości obiektów COM. Ten nowy obiekt wiążący znacznie zwiększona wydajność, ale również wprowadzone pewne błędy, które usunięto w programie WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Konwersje argumentów nie zawsze wykonano poprawnie

W poniższym przykładzie:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

**WyślijKlawisze** metoda oczekuje ciągu, ale program PowerShell nie zostały przekonwertowane char na ciąg odkładania konwersji na **uwzględniając**, który używa **VariantChangeType**można wykonać konwersji. W tym przykładzie pozwoliło to odnotować przesyłanie kluczy '1', '7' i "3" zamiast oczekiwanej **Volume.Mute** klucza.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Wyliczalne obiektów COM nie zawsze obsługiwane poprawnie

PowerShell zwykle wylicza większość obiektów wyliczalny, ale regresji, wprowadzone w programie WMF 5.0 uniemożliwił wyliczenie obiektów COM, które implementują interfejs IEnumerable. Przykład:

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

W powyższym przykładzie nieprawidłowo napisany program WMF 5.0 **Scripting.Dictionary** do potoku zamiast wyliczania pary klucz/wartość.

### <a name="ordered-was-not-allowed-inside-classes"></a>[uporządkowane] był niedozwolony wewnątrz klasy

Program WMF 5.0 wprowadzono klasy z weryfikacją literałów typu, używany w klasach. `[ordered]` wygląda jak literał typu, ale nie jest to wartość true, typ platformy .NET. Program WMF 5.0 niepoprawnie zgłosił błąd na `[ordered]` wewnątrz klasy:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Pomoc na temat tematów z wieloma wersjami nie działa.

Zanim program WMF 5.1, jeśli masz wiele wersji zainstalować moduł, a wszystkie one udostępnione tematu pomocy, na przykład about_PSReadline, `help about_PSReadline` zwróci wiele tematów w oczywisty sposób wyświetlenia rzeczywiste pomocy.

Program WMF 5.1 rozwiązuje to zwracając pomocy dla najnowszej wersji tego tematu.

`Get-Help` nie zapewnia możliwość określenia, która wersja ma dotyczyć pomoc dla. Aby obejść ten problem, przejdź do katalogu modułów, a następnie Wyświetl Pomoc bezpośrednio za pomocą narzędzia, takiego jak ulubionego edytora.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>Odczytywanie z STDIN PowerShell.exe przerywane.

Klienci używają `powershell -command -` od natywnych aplikacji do wykonywania programu PowerShell przekazywanie skryptu za pomocą STDIN Niestety to został zaburzyć przez inne zmiany w konsoli hosta.

Jest to naprawione w wersji 5.1 w Rocznicowej aktualizacji systemu Windows 10.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe tworzy nagły wzrost użycia procesora CPU podczas uruchamiania

PowerShell używa kwerendy usługi WMI, aby sprawdzić, czy została uruchomiona przy użyciu zasad grupy, aby uniknąć, powodując opóźnienie podczas logowania. Kwerenda WMI kończy się wprowadzanie tzres.mui.dll na każdym etapie procesu w systemie od WMI **Win32_Process** klasy podejmie próbę pobrania informacje dotyczące lokalnej strefy czasowej. Skutkuje to duży wzrost procesora CPU w **wmiprvse** (host dostawcy WMI). Obejście polega na użyciu wywołań interfejsu API Win32 te same informacje, a nie przy użyciu usługi WMI.
