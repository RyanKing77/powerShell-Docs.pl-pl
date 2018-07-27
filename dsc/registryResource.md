---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób rejestru DSC
ms.openlocfilehash: 8d74473d167b70182c3a16c1d39d2a9e797afb1b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267725"
---
# <a name="dsc-registry-resource"></a>Zasób rejestru DSC

_Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0_

**Rejestru** zasób w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania kluczy rejestru i wartości w węźle docelowym.

## <a name="syntax"></a>Składnia

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Właściwości

| Właściwość | Opis |
| --- | --- |
| Klawisz| Wskazuje ścieżkę klucza rejestru, dla którego chcesz zapewnić określonego stanu. Ta ścieżka musi zawierać gałęzi.|
| valueName| Wskazuje nazwę wartości rejestru. Aby dodać lub usunąć klucz rejestru, należy określić tę właściwość jako ciąg pusty, bez wcześniejszego określania ValueType lub Dane_wartości. Aby zmodyfikować lub usunąć domyślną wartością klucza rejestru, należy określić tę właściwość jako ciąg pusty podczas również określenie ValueType lub Dane_wartości.|
| Upewnij się| Wskazuje, czy istnieją kluczy i wartości. Aby upewnić się, że tak, należy ustawić tę właściwość na "Obecny". Aby upewnić się, że nie istnieją, należy ustawić właściwość na "Brak". Wartość domyślna to "Istnieje".|
| Force| Jeśli określony klucz rejestru jest obecny, **życie** zastępowane nową wartością. Jeśli usuwanie klucza rejestru za pomocą podkluczy, musi to być **$true** |
| Hex| Wskazuje, jeśli dane są wyrażane w formacie szesnastkowym. Jeśli zostanie określony, dane wartość DWORD/QWORD są prezentowane w formacie szesnastkowym. Nie jest prawidłowy dla innych typów. Wartość domyślna to **$false**.|
| DependsOn| Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest **ResourceName** a jej typ jest **ResourceType**, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| Dane_wartości| Dane wartości rejestru.|
| ValueType| Wskazuje typ wartości. Obsługiwane typy to: ciągu (REG_SZ), plik binarny (dane BINARNE REG), Dword 32-bitowych (REG_DWORD), Qword 64-bitowych (REG_QWORD), ciągu wielokrotnego (REG_MULTI_SZ), ciągu rozwijalnego (REG_EXPAND_SZ) |

## <a name="example"></a>Przykład

W tym przykładzie gwarantuje, że klucz o nazwie "ExampleKey" jest obecny w **HKEY\_lokalnego\_maszyny** hive.

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

> [!NOTE]
> Zmiany ustawień rejestru `HKEY\CURRENT\USER` gałęzi wymaga, że konfiguracja jest uruchamiany przy użyciu poświadczeń użytkownika, a nie jako system. Możesz użyć **PsDscRunAsCredential** właściwości w celu określenia poświadczeń użytkownika do konfiguracji. Aby uzyskać przykład, zobacz [systemem DSC przy użyciu poświadczeń użytkownika](runAsUser.md).