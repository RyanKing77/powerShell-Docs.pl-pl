---
ms.date: 08/24/2018
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC skryptu
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43133897"
---
# <a name="dsc-script-resource"></a>Zasób DSC skryptu

> Dotyczy: Windows PowerShell 4.0, programu Windows PowerShell 5.x

**Skryptu** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do uruchomienia Bloki skryptu programu Windows PowerShell w węzłach docelowych. **Skryptu** używa zasobów `GetScript`, `SetScript`, i `TestScript` właściwości, które zawierają Bloki skryptu należy zdefiniować do wykonania odpowiednich DSC stanu operacji.

## <a name="syntax"></a>Składnia

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> `GetScript`, `TestScript`, I `SetScript` bloki są przechowywane w postaci ciągów.

## <a name="properties"></a>Właściwości

|Właściwość|Opis|
|--------|-----------|
|GetScript|Blok skryptu, który zwraca bieżący stan węzła.|
|SetScript|Blok skryptu DSC są używane do wymuszania zgodności, gdy węzeł nie jest w żądanym stanie.|
|TestScript|Blok skryptu, który określa, czy węzeł jest w żądanym stanie.|
|Poświadczenie| Określa poświadczenia do użycia dla tego skryptu, jeśli wymagane są poświadczenia.|
|DependsOn| Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC nie używa danych wyjściowych `GetScript`. [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) wykonuje polecenie cmdlet `GetScript` można pobrać stanu bieżącego węzła. Wartość zwracana nie jest wymagana od `GetScript`. Jeśli określisz wartość zwracana, musi on być `hashtable` zawierający **wynik** klucz, którego wartością jest `String`.

### <a name="testscript"></a>TestScript

`TestScript` Jest wykonywana przez DSC, aby określić, czy `SetScript` powinien zostać uruchomiony. Jeśli `TestScript` zwraca `$false`, wykonuje DSC `SetScript` można przenieść węzeł z powrotem do żądanego stanu. Aplikacja musi zwracać `boolean` wartość. Wynikiem `$true` wskazuje, że węzeł jest zgodny i `SetScript` nie powinien wykonać.

[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wykonuje polecenia cmdlet, `TestScript` można pobrać zgodności węzłów z **skryptu** zasobów. Jednak w tym przypadku `SetScript` nie działa, niezależnie od tego, co `TestScript` block zwraca.

> [!NOTE]
> Wszystkie dane wyjściowe z Twojej `TestScript` jest częścią jego zwracanej wartości. Program PowerShell interpretuje unsuppressed danych wyjściowych w formacie różna od zera, co oznacza, że Twoje `TestScript` zwróci `$true` niezależnie od tego, stan tego węzła.
> To powoduje produkuje nieoczekiwanych rezultatów, wyniki fałszywie dodatnie i powoduje trudności podczas rozwiązywania problemów.

### <a name="setscript"></a>SetScript

`SetScript` Modyfikuje węzeł, który ma enfore żądanego stanu. Jest ona wywoływana przez DSC, jeśli `TestScript` skrypt zwraca blok `$false`. `SetScript` Powinna posiadać wartości zwrotnej.

## <a name="examples"></a>Przykłady

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Przykład 1: Zapisywanie tekstu próbki, przy użyciu skryptu zasobu

W tym przykładzie, sprawdza istnienie `C:\TempFolder\TestFile.txt` w każdym węźle. Jeśli nie istnieje, tworzy go za pomocą `SetScript`. `GetScript` Zwraca zawartość pliku i jego wartość zwracana nie jest używany.

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Przykład 2: Porównać informacje o wersji przy użyciu skryptu zasobu

W tym przykładzie pobiera *zgodne* informacje o wersji z pliku tekstowego na komputerze, do tworzenia i zapisuje go w `$version` zmiennej. Podczas generowania pliku MOF tego węzła, DSC zastępuje `$using:version` zmiennych w każdego skryptu blokowania z wartością `$version` zmiennej. W czasie wykonywania *zgodne* wersji jest przechowywany w pliku tekstowym w każdym węźle w porównaniu i aktualizowane na kolejne wykonania.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```