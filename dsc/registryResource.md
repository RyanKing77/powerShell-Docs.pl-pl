---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób rejestru DSC
ms.openlocfilehash: fcd24b1dd729dbb0abd697a4a628dce01fdd5422
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-registry-resource"></a>Zasób rejestru DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

**Rejestru** zasób w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania kluczy rejestru i wartości w docelowym węźle.

## <a name="syntax"></a>Składnia

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Właściwości
|  Właściwość  |  Opis   |
|---|---|
| Klawisz| Określa ścieżkę klucza rejestru, dla którego chcesz zapewnić z określonym stanem. Ta ścieżka musi zawierać gałęzi.|
| ValueName| Wskazuje nazwę wartości rejestru. Aby dodać lub usunąć klucz rejestru, bez określenia ValueType lub Dane_wartości należy określić tę właściwość jako ciąg pusty. Aby zmodyfikować lub usunąć domyślną wartością klucza rejestru, należy określić tę właściwość jako ciąg pusty, jeśli określono również ValueType lub Dane_wartości.|
| Upewnij się| Wskazuje, czy istnieje klucz i wartość. Aby upewnić się, że ich ustaw wartość "Brak". Aby upewnić się, że nie istnieją, ustaw właściwość na "Brak". Wartość domyślna to "Brak".|
| Force| Jeśli określony klucz rejestru jest obecny, __życie__ zastępuje go przy użyciu nowej wartości. Jeśli usuwanie klucza rejestru za pomocą podkluczy, musi to być __$true__|
| Hex| Wskazuje, czy dane są wyrażane w formacie szesnastkowym. Jeśli jest określony, dane wartości DWORD/QWORD jest podana w formacie szesnastkowym. Nie jest prawidłowy dla innych typów. Wartość domyślna to __$false__.|
| dependsOn| Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Dane wartości rejestru.|
| ValueType| Wskazuje typ wartości. Obsługiwane typy to:
<ul><li>String (REG_SZ)</li>


<li>Dane binarne (REG BINARY)</li>


<li>DWORD 32-bitowych (REG_DWORD)</li>


<li>Qword 64-bitowych (REG_QWORD)</li>


<li>Multi-string (REG_MULTI_SZ)</li>


<li>Ciąg rozwijania (REG_EXPAND_SZ)</li></ul>

## <a name="example"></a>Przykład
W tym przykładzie zapewnia, że klucz o nazwie "ExampleKey" są obecne w **HKEY\_lokalnego\_maszyny** hive.
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

>**Uwaga:** zmiany ustawień rejestru **HKEY\_bieżącego\_użytkownika** gałęzi wymaga, czy konfiguracja jest uruchomiony przy użyciu poświadczeń użytkownika, a nie jako system.
>Można użyć **PsDscRunAsCredential** właściwość, aby określić poświadczenia użytkownika w konfiguracji. Na przykład zobacz [DSC uruchomiony przy użyciu poświadczeń użytkownika](runAsUser.md)