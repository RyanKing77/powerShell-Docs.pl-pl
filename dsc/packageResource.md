---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób pakietu DSC
ms.openlocfilehash: cfa9d53d5ea588b0ec97e5503302a451caa09e03
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
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