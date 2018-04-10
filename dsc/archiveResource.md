---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Archiwum DSC zasobów
ms.openlocfilehash: 1accd48f3862ee09b88d2792f9b7e5a7324bcf17
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-archive-resource"></a>Archiwum DSC zasobów

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Zasób archiwum w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm do rozpakowywania plików archiwów (.zip) w określonej ścieżce.

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
| Lokalizacja docelowa| Określa lokalizację, w której chcesz upewnij się, że są wyodrębniane zawartość archiwum.|
| Ścieżka| Określa ścieżkę źródłową pliku archiwum.|
| __Checksum__| Definiuje typ używany do określenia, czy dwa pliki są takie same. Jeśli __sumy kontrolnej__ nie zostanie określona, tylko nazwa pliku lub katalogu jest używana do porównania. Prawidłowe wartości to: SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji, none (ustawienie domyślne). Jeśli określisz __sumy kontrolnej__ bez __weryfikacji__, konfiguracja zakończy się niepowodzeniem.|
| Upewnij się| Określa, czy należy sprawdzić, czy zawartość archiwum istnieje w __docelowego__. Ta właściwość jest ustawiana __obecny__ zapewnienie zawartość istnieje. Ustaw ją na __nieobecne__ aby upewnić się, nie istnieją. Wartość domyślna to __obecny__.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator bloku skryptu konfiguracji zasobu, który chcesz uruchomić jest najpierw ResourceName i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Sprawdzanie poprawności| Używa właściwości sumy kontrolnej, aby określić, czy podpis jest zgodna z archiwum. Jeśli określisz sumy kontrolnej bez sprawdzania poprawności konfiguracji zakończy się niepowodzeniem. Jeśli określisz weryfikacji bez sum kontrolnych sumy kontrolnej algorytmu SHA-256 jest używany domyślnie.|
| Force| Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd. Za pomocą właściwości Force zastępuje takie błędy. Wartość domyślna to False.|

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie zasobu archiwum, aby upewnić się, że zawartość pliku archiwum o nazwie Test.zip istnieją i są wyodrębniane w danej lokalizacji docelowej.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```