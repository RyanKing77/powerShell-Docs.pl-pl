---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób archiwum DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048433"
---
# <a name="dsc-archive-resource"></a>Zasób archiwum DSC

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

Zasób archiwum w Windows PowerShell Desired State Configuration (DSC) udostępnia mechanizm do rozpakowywania plików archiwów (.zip) w określonej ścieżce.

## <a name="syntax"></a>Składnia
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Lokalizacja docelowa| Określa lokalizację, w której chcesz upewnić się, że zawartość archiwum zostały wyodrębnione.|
| Ścieżka| Określa ścieżkę źródłową pliku archiwum.|
| __Sumy kontrolnej__| Definiuje typ używany do określenia, czy dwa pliki są takie same. Jeśli __sumy kontrolnej__ nie jest określona, tylko nazwa pliku lub katalogu jest używana do porównania. Prawidłowe wartości to: SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji, none (wartość domyślna). Jeśli określisz __sumy kontrolnej__ bez __weryfikacji__, konfiguracja zakończy się niepowodzeniem.|
| Upewnij się| Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w __docelowy__. Ustaw tę właściwość na __obecne__ zapewnienie zawartość istnieje. Ustaw ją na __nieobecne__ aby upewnić się, nie istnieją. Wartość domyślna to __obecne__.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić najpierw ResourceName i jego typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Sprawdzanie poprawności| Używa właściwości sumy kontrolnej, aby ustalić, czy podpis jest zgodna z archiwum. Jeśli określisz sumy kontrolnej bez sprawdzania poprawności, konfiguracja zakończy się niepowodzeniem. Jeśli określisz weryfikacji bez sumy kontrolnej, sumy kontrolnej algorytmu SHA-256 jest używany domyślnie.|
| Force| Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu. Przy użyciu właściwości życie zastępuje takie błędy. Wartość domyślna to False.|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać zasób archiwum, aby upewnić się, że zawartość pliku archiwum o nazwie Test.zip istnieją i są wyodrębniane w danej lokalizacji docelowej.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```