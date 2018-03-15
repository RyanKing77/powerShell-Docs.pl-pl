---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Zasób skryptu konfiguracji DSC"
ms.openlocfilehash: d65a89ceba0b641ccb0ac3dfcc6d5ec1a48dc92a
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-script-resource"></a>Zasób skryptu konfiguracji DSC

 
> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**Skryptu** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający uruchamianie blokach skryptu programu Windows PowerShell w węzłach docelowych. `Script` Zasób ma `GetScript`, `SetScript`, i `TestScript` właściwości. Te właściwości powinien mieć ustawioną w blokach skryptu, które będą uruchamiane w każdym węźle docelowym. 

`GetScript` Bloku skryptu ma zwracać obiektu hashtable reprezentujący stan bieżącego węzła. Hashtable musi zawierać tylko jeden klucz `Result` i wartość musi być typu `String`. Zwraca niczego nie jest wymagane. DSC nie ma wpływu na dane wyjściowe tego bloku skryptu.

`TestScript` Bloku skryptu należy określić, czy bieżący węzeł ma zostać zmodyfikowana. Powinien on zwrócić `$true` Jeśli węzeł jest aktualny. Powinien on zwrócić `$false` Jeśli konfiguracji węzła jest przestarzały i powinien zostać zaktualizowany przez `SetScript` blok skryptu. `TestScript` Bloku skryptu jest wywoływana przez DSC.

`SetScript` Bloku skryptu należy modyfikować węzła. Jeśli jest wywoływana przez DSC `TestScript` zablokować powrotu `$false`.

Jeśli musisz używać zmiennych z skrypt konfiguracji w `GetScript`, `TestScript`, lub `SetScript` blokach skryptu, użyj `$using:` zakresu (patrz poniżej przedstawiono przykład).


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

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   | 
|---|---| 
| GetScript| Zawiera blok skryptu programu Windows PowerShell, który uruchamia po wywołaniu [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) polecenia cmdlet. Ten blok musi zwracać obiektu hashtable. Hashtable musi zawierać tylko jeden klucz **wynik** i wartość musi być typu **ciąg**.| 
| SetScript| Zawiera blok skryptu programu Windows PowerShell. Gdy wywołanie [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) polecenia cmdlet, **TestScript** bloku jest uruchamiany pierwszy. Jeśli **TestScript** zablokować zwraca **$false**, **SetScript** bloku zostanie uruchomiony. Jeśli **TestScript** zablokować zwraca **$true**, **SetScript** bloku nie zostaną uruchomione.| 
| TestScript| Zawiera blok skryptu programu Windows PowerShell. Podczas wywołania [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) działa ten blok polecenia cmdlet. Jeśli zmienna zwraca **$false**, blok SetScript zostanie uruchomiony. Jeśli zmienna zwraca **$true**, SetScript będzie blok, nie działać. **TestScript** bloku również uruchamiane przy wywołaniu [DscConfiguration testu](https://technet.microsoft.com/en-us/library/dn407382.aspx) polecenia cmdlet. Jednak w tym przypadku **SetScript** nie Uruchom, niezależnie od tego, jaka wartość TestScript zablokować zwraca bloku. **TestScript** bloku musi zwracać wartość True, jeśli rzeczywista konfiguracja zgodny z bieżącej konfiguracji żądanego stanu i wartość False, jeśli nie jest zgodny. (W bieżącej konfiguracji żądanego stanu jest ostatniej konfiguracji wdrożonymi na węźle, który używa DSC).| 
| Poświadczenie| Określa poświadczenia na potrzeby uruchomienie tego skryptu, jeśli są wymagane poświadczenia.| 
| dependsOn| Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **ResourceType**, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Przykład 1
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a>Przykład 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
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
```

Ten zasób jest zapisywania wersji konfiguracji do pliku tekstowego. Ta wersja jest dostępna na komputerze klienckim, ale nie znajduje się w dowolny z węzłów, więc musi zostać przekazane do każdego z `Script` blokach skryptu zasobu przy użyciu programu PowerShell w `using` zakresu. Podczas generowania MOF węzła pliku, wartość `$version` zmiennej jest do odczytu z pliku tekstowego na komputerze klienckim. Zamienia DSC `$using:version` zablokować zmiennych w każdego skryptu z wartością `$version` zmiennej.

