---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: "Moduł aktualizacji"
ms.openlocfilehash: 343c296dad2a3df35f13393b3796a1d484f5f535
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2017
---
# <a name="update-module"></a>Moduł aktualizacji

Pobiera i instaluje najnowszą wersję określone moduły z galerii online na komputerze lokalnym.

## <a name="description"></a>Opis

Polecenie cmdlet Update-Module instaluje nowsza wersja modułu programu Windows PowerShell, który został zainstalowany z galerii online, uruchamiając modułu instalacji na komputerze lokalnym.

Domyślnie najnowsza wersja określony moduł w galerii online jest zainstalowany, chyba że zostanie wymagana wersja. Możesz zaktualizować istniejący, zainstalowany moduł, określając nazwę modułu; Moduł aktualizacji wyszukuje $env: PSModulePath modułów, które chcesz zaktualizować.

Uruchomienie modułu aktualizacji bez parametr Name aktualizuje wszystkie moduły, które mogą zostać zaktualizowane na komputerze lokalnym.

### <a name="notes"></a>Uwagi

- To polecenie cmdlet jest uruchamiane w środowisku Windows PowerShell 3.0 ani nowszych wersji środowiska Windows PowerShell w systemie Windows 7 lub Windows 2008 R2 i nowszych wersjach systemu Windows.
- Jeśli moduł, który należy określić przy użyciu parametru Name nie został zainstalowany przy użyciu instalacji modułu, wystąpi błąd. Moduł aktualizacji można uruchamiać tylko w modułach zainstalowanych z galerii online, uruchamiając instalacji modułu.
- Jeśli aktualizacja modułu próbuje zaktualizować pliki binarne, które są używane, aktualizacji modułu zwraca błąd, który identyfikuje procesy problem i informuje użytkownika, aby ponowić próbę aktualizacji modułu po zatrzymaniu procesów.
- Na programu PowerShell w wersji 5.0 lub nowszej wersji podczas aktualizacji modułu aktualizacji modułu, dodaje najnowszej (lub został określony) wersji modułu, więc starszej i nowszych wersji są teraz side-by-side w tym samym katalogu. Jest przydatne, to znaczy i wyświetlania przykładowe dane wyjściowe tych poleceń.


## <a name="cmdlet-syntax"></a>Składnia polecenia cmdlet
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Dokumentacja poleceń cmdlet pomocy online

[Moduł aktualizacji](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a>Przykładowe polecenia

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>Zaktualizuj moduł TestDepWithNestedRequiredModules1 z zależności.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

