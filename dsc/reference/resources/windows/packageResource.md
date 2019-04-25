---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC pakietu
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077198"
---
# <a name="dsc-package-resource"></a>Zasób DSC pakietu

_Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_

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

| Właściwość | Opis |
| --- | --- |
| Nazwa| Określa nazwę pakietu, dla którego chcesz zapewnić określonego stanu.|
| Ścieżka| Wskazuje ścieżkę, w której znajduje się pakiet.|
| Identyfikator produktu| Określa identyfikator produktu, który unikatowo identyfikuje pakiet.|
| Argumenty| Wyświetla listę ciągów argumentów, które zostaną przekazane do pakietu dokładnie zgodnie z postanowieniami.|
| Poświadczenie| Umożliwia dostęp do pakietu zdalnego źródła. Ta właściwość nie jest używana do zainstalowania pakietu. Pakiet jest zawsze instalowany w systemie lokalnym.|
| Upewnij się| Wskazuje, czy zainstalowano pakiet. Ustaw tę właściwość na "Brak", upewnij się, że nie zainstalowano pakiet (lub odinstalować pakiet, jeśli jest zainstalowana). Ustaw dla niej "Przedstawia" (wartość domyślna) upewnij się, że pakiet jest zainstalowany.|
| Ścieżka dziennika| Określa pełną ścieżkę, której chcesz dostawcę Aby zapisać plik dziennika, aby zainstalować lub odinstalować pakiet.|
| dependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
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