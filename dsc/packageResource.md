---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób pakietu DSC
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-package-resource"></a>Zasób pakietu DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**Pakietu** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm umożliwiający instalowanie lub odinstalowywanie pakiety, takie jak pakietów Instalatora Windows i setup.exe w docelowym węźle.

## <a name="syntax"></a>Składnia

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a>Właściwości
|  Właściwość  |  Opis   |
|---|---|
| Nazwa| Określa nazwę pakietu, dla którego chcesz zapewnić z określonym stanem.|
| Ścieżka| Określa ścieżkę, w której znajduje się pakiet.|
| Identyfikator produktu| Wskazuje identyfikator produktu, który unikatowo identyfikuje pakiet.|
| Argumenty| Wyświetla ciąg argumentów, które zostaną przekazane do pakietu, tak jak została podana.|
| Poświadczenie| Umożliwia dostęp do pakietu zdalnego źródła. Ta właściwość nie jest używana do zainstalowania pakietu. Pakiet jest zawsze instalowany w systemie lokalnym.|
| Upewnij się| Wskazuje, czy pakiet jest zainstalowany. Ustaw tę właściwość na "Brak", upewnij się, że pakiet nie jest zainstalowany (lub odinstalować pakiet, jeśli jest zainstalowana). Ustaw "Przedstawić" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.|
| Ścieżka dziennika| Określa pełną ścieżkę, w którym ma dostawcy, aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest **ResourceName** i jej typ jest **ResourceType**, składnia za pomocą tej właściwości to "DependsOn ="[ResourceName ResourceType]"".|
| ReturnCode| Wskazuje oczekiwany kod powrotny. Jeśli kod powrotu rzeczywiste nie odpowiada oczekiwanej wartości podane w tym miejscu konfiguracji spowoduje zwrócenie błędu.|

## <a name="example"></a>Przykład

W tym przykładzie jest uruchamiany Instalator MSI, który znajduje się w określonej ścieżce i ma identyfikator określonego produktu.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```