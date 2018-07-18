---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC pakietu
ms.openlocfilehash: 3046ba7d57776a996a0b917348a0e863db6cd0c8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093807"
---
# <a name="dsc-package-resource"></a>Zasób DSC pakietu

> Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0

**Pakietu** zasobów w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do zainstalowania lub odinstalowania pakietów, takie jak pakiety Instalatora Windows i setup.exe, w węźle docelowym.

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
| Nazwa| Określa nazwę pakietu, dla którego chcesz zapewnić określonego stanu.|
| Ścieżka| Wskazuje ścieżkę, w której znajduje się pakiet.|
| Identyfikator produktu| Określa identyfikator produktu, który unikatowo identyfikuje pakiet.|
| Argumenty| Wyświetla listę ciągów argumentów, które zostaną przekazane do pakietu dokładnie zgodnie z postanowieniami.|
| Poświadczenie| Umożliwia dostęp do pakietu zdalnego źródła. Ta właściwość nie jest używana do zainstalowania pakietu. Pakiet jest zawsze instalowany w systemie lokalnym.|
| Upewnij się| Wskazuje, czy zainstalowano pakiet. Ustaw tę właściwość na "Brak", upewnij się, że nie zainstalowano pakiet (lub odinstalować pakiet, jeśli jest zainstalowana). Ustaw dla niej "Przedstawia" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.|
| Ścieżka dziennika| Określa pełną ścieżkę, której chcesz dostawcę Aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości to "DependsOn ="[ ResourceName ResourceType]"".|
| Kod zwrotny| Wskazuje oczekiwany kod powrotny. Jeśli rzeczywiste zwróci kod nie odpowiada oczekiwanej wartości zostanie podany tutaj, konfiguracja zwróci błąd.|

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