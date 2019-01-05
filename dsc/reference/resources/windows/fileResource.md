---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Zasób DSC plików
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048522"
---
# <a name="dsc-file-resource"></a>Zasób DSC plików

> Dotyczy: Program Windows PowerShell 4.0, Windows PowerShell 5.0

Zasób pliku w Windows PowerShell Desired State Configuration (DSC) zapewnia mechanizm zarządzania plikami i folderami w docelowym węźle.

>**Uwaga:** Jeśli **MatchSource** właściwość jest ustawiona na **$false** (czyli wartość domyślna), treści, które mają być kopiowane są buforowane konfiguracja jest stosowana po raz pierwszy.
>Kolejne aplikacje konfiguracji nie będzie sprawdzać zaktualizowane pliki i/lub folderów w ścieżce określonej przez **Ścieżka_źródłowa**. Jeśli chcesz sprawdzać dostępność aktualizacji do plików i/lub folderów w **Ścieżka_źródłowa** za każdym razem, gdy konfiguracja jest stosowana, ustaw **MatchSource** do **$true**.

## <a name="syntax"></a>Składnia
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Właściwości

|  Właściwość  |  Opis   |
|---|---|
| Ścieżka_docelowa| Określa lokalizację, w którym chcesz upewnić się, stan dla pliku lub katalogu.|
| Atrybuty| Określa żądany stan atrybutów dla pliku docelowego lub katalogu.|
| Suma kontrolna| Wskazuje typ sumy kontrolnej, używany do określenia, czy dwa pliki są takie same. Jeśli __sumy kontrolnej__ nie jest określona, tylko nazwa pliku lub katalogu jest używana do porównania. Prawidłowe wartości to: SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji.|
| Zawartość| Określa zawartość pliku, na przykład określonego ciągu.|
| Poświadczenie| Określa poświadczenia, które są wymagane do dostępu do zasobów, takich jak pliki źródłowe, jeśli taki dostęp jest wymagany.|
| Upewnij się| Wskazuje, czy istnieje plik lub katalog. Ustaw tę właściwość na "Brak", aby upewnić się, że plik lub katalog nie istnieje. Ustaw ją na "Obecny", aby upewnić się, że plik lub katalog istnieje. Wartość domyślna to "Istnieje".|
| Force| Niektóre operacje na plikach (takich jak zastąpienie pliku lub usunięcie katalogu, który nie jest pusty) spowoduje wystąpienie błędu. Przy użyciu właściwości życie zastępuje takie błędy. Wartość domyślna to __$false__.|
| Recurse| Wskazuje, czy podkatalogi są uwzględniane. Ustaw tę właściwość na __$true__ aby wskazać, że podkatalogi do uwzględnienia. Wartość domyślna to __$false__. **Uwaga**: Ta właściwość jest prawidłowy tylko w przypadku, gdy właściwość Type jest ustawiona do katalogu.|
| DependsOn | Wskazuje, że konfiguracji inny zasób, należy uruchomić przed ten zasób jest skonfigurowany. Na przykład, jeśli identyfikator konfiguracji zasobu skryptu Blok, który chcesz uruchomić najpierw jest __ResourceName__ a jej typ jest __ResourceType__, składnia przy użyciu tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| SourcePath| Określa ścieżkę, z której można skopiować zasobu pliku lub folderu.|
| Typ| Wskazuje, czy zasób jest skonfigurowany katalog lub plik. Ustaw tę właściwość na "Directory", aby wskazać, czy zasób jest katalogiem. Ustaw ją na "Plik", aby wskazać, czy zasób jest plik. Wartość domyślna to "File".|
| MatchSource| Jeśli ustawiono wartość domyślną __$false__, a następnie wszystkie pliki w źródle (powiedzmy, pliki A, B i C) zostaną dodane do miejsca docelowego konfiguracja jest stosowana po raz pierwszy. Jeśli nowy plik (D) jest dodawany do źródła, go nie zostanie dodany do miejsca docelowego, nawet wtedy, gdy konfiguracja jest ponownie stosowana w dalszej części. Jeśli wartość jest __$true__, a następnie każdorazowo konfiguracja jest stosowana, nowe pliki, które okazały się dla źródła (na przykład plik D, w tym przykładzie) są dodawane do miejsca docelowego. Wartość domyślna to **$false**.|

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak na potrzeby zasobów pliku upewnij się, że katalog o ścieżce `C:\Users\Public\Documents\DSCDemo\DemoSource` w źródle komputera (na przykład serwer "pull") występuje także (oraz wszystkie podkatalogi) w docelowym węźle. Ponadto zapisuje komunikat potwierdzający dziennika po ukończeniu i zawiera instrukcję, aby upewnić się, że operacja sprawdzanie plików jest uruchamiany przed operację rejestrowania.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```