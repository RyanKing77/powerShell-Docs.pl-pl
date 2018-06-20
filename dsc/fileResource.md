---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Zasób plików konfiguracji DSC
ms.openlocfilehash: 86a5dcd97b4163b3780038c815d3de5a523ce4bf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218947"
---
# <a name="dsc-file-resource"></a>Zasób plików konfiguracji DSC

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Plik zasobów w Windows PowerShell Desired stan konfiguracji (DSC) zapewnia mechanizm zarządzania plikami i folderami w docelowym węźle.

>**Uwaga:** Jeśli **MatchSource** właściwość jest ustawiona na **$false** (która jest wartością domyślną), zawartość do skopiowania są buforowane konfiguracja zostanie zastosowana po raz pierwszy.
>Kolejne aplikacji konfiguracji nie będzie sprawdzać dostępność zaktualizowane pliki lub foldery w ścieżce określonej przez **Ścieżka_źródłowa**. Jeśli chcesz wyszukać aktualizacje do plików i/lub folderów w **Ścieżka_źródłowa** za każdym razem, gdy konfiguracja zostanie zastosowana, ustaw **MatchSource** do **$true**.

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
| Ścieżka_docelowa| Wskazuje lokalizację, do której chcesz zapewnić stan pliku lub katalogu.|
| Atrybuty| Określa stan odpowiednie atrybuty docelowego pliku lub katalogu.|
| Suma kontrolna| Wskazuje typ sumy kontrolnej używany do określenia, czy dwa pliki są takie same. Jeśli __sumy kontrolnej__ nie zostanie określona, tylko nazwa pliku lub katalogu jest używana do porównania. Prawidłowe wartości to: algorytmu SHA-1, SHA-256, SHA-512, createdDate, Data modyfikacji.|
| Zawartość| Określa zawartość pliku, takie jak określony ciąg.|
| Poświadczenie| Określa poświadczenia, które są wymagane do dostępu do zasobów, takich jak pliki źródłowe, jeśli taki dostęp jest wymagana.|
| Upewnij się| Wskazuje, czy istnieje plik lub katalog. Ustaw tę właściwość na "Brak", aby upewnić się, że plik lub katalog nie istnieje. Ustaw ją na "Brak", aby upewnić się, że istnieje plik lub katalog. Wartość domyślna to "Brak".|
| Force| Niektóre operacje na plikach (takie jak zastąpienie pliku lub usuwanie katalogu, który nie jest pusty) spowoduje błąd. Za pomocą właściwości Force zastępuje takie błędy. Wartość domyślna to __$false__.|
| Recurse| Wskazuje, czy podkatalogi są dołączone. Ta właściwość jest ustawiana __$true__ aby wskazać, że chcesz podkatalogów, które zostaną uwzględnione. Wartość domyślna to __$false__. **Uwaga**: Ta właściwość jest prawidłowy tylko, gdy właściwość Type ma ustawioną w katalogu.|
| dependsOn | Wskazuje, że konfiguracja inny zasób należy uruchomić przed ten zasób jest skonfigurowany. Na przykład jeśli identyfikator konfiguracji zasobu skryptu bloku, który chcesz uruchomić najpierw jest __ResourceName__ i jej typ jest __ResourceType__, składnia za pomocą tej właściwości jest `DependsOn = "[ResourceType]ResourceName"`.|
| SourcePath| Określa ścieżkę do skopiowania zasobów pliku lub folderu.|
| Typ| Wskazuje, czy zasób konfigurowany jest katalog lub plik. Ustaw tę właściwość na "Directory", aby wskazać, czy zasób jest katalogiem. Ustaw ją na "Plik", aby wskazać, czy zasób jest plik. Wartość domyślna to "Plik".|
| MatchSource| Jeśli ustawiono wartość domyślną __$false__, a następnie wszystkie pliki w źródle (, że pliki A, B i C) zostanie dodany do miejsca docelowego konfiguracja zostanie zastosowana po raz pierwszy. Jeśli nowy plik (D) jest dodawany do źródła, jego nie zostanie dodany do miejsca docelowego, nawet wtedy, gdy konfiguracja zostanie zastosowana ponownie później. Jeśli wartość jest __$true__, a następnie każdorazowo konfiguracja zostanie zastosowana, nowe pliki później znaleziono w źródle (na przykład plik D, w tym przykładzie) są dodawane do miejsca docelowego. Wartość domyślna to **$false**.|

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie pliku zasobu do upewnij się, że katalog o tej ścieżce `C:\Users\Public\Documents\DSCDemo\DemoSource` w źródle komputera (na przykład serwer "ściągania") występuje również (wraz z wszystkie podkatalogi) w docelowym węźle. Również zapisuje komunikat potwierdzający dziennika po ukończeniu i zawiera instrukcję, aby upewnić się, że operację sprawdzania plików jest uruchamiana przed operację rejestrowania.

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