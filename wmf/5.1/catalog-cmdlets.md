---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Polecenia cmdlet wykazu
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057641"
---
# <a name="catalog-cmdlets"></a>Polecenia cmdlet wykazu

Dodaliśmy dwa nowe polecenia cmdlet w [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) modułu, aby wygenerować i zweryfikować pliki w katalogu systemu windows.

## <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

`New-FileCatalog` Tworzy plik katalogu systemu windows dla zestawu plików i folderów. Plik wykazu zawiera skróty dla wszystkich plików w określonych ścieżek. Użytkownicy mogą dystrybuować zestawu folderów oraz odpowiadający plik wykazu, który reprezentuje te foldery. Plik wykazu może służyć przez odbiorcę zawartości można sprawdzić, czy zmiany zostały wprowadzone do folderów, po utworzeniu wykazu.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Firma Microsoft obsługuje tworzenie katalogu w wersji 1 i 2. Wersja 1 używa algorytmu wyznaczania wartości skrótu SHA1 do tworzenia plików, skrótów i w wersji 2 używa SHA256. Wykaz w wersji 2 nie jest obsługiwana w *systemu Windows Server 2008 R2* i *Windows 7*. Zaleca się używać katalogu w wersji 2, jeśli przy użyciu platform *systemu Windows 8*, *systemu Windows Server 2012* i nowsze wersje.

Aby użyć tego polecenia na istniejący moduł, określ CatalogFilePath i Path zmienne jest zgodna z lokalizacją manifestu modułu. W poniższym przykładzie manifest modułu znajduje się w C:\Program Files\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Spowoduje to utworzenie pliku wykazu.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Aby sprawdzić integralność pliku wykazu (Pester.cat w powyżej przykładzie) powinien on być podpisany przy użyciu [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) polecenia cmdlet.


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` sprawdza poprawność wykazu, reprezentujący zestaw folderów.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

To polecenie cmdlet porównuje wartości skrótów wszystkich plików i ich ścieżek względnych znajdującą się w pliku wykazu z tymi zapisywany na dysku. Jeśli wykryje niezgodność skróty plików i ścieżek zwraca stan `ValidationFailed`.
Użytkownicy mogą pobrać wszystkie te informacje przy użyciu `Detailed` przełącznika. Stan podpisywania katalogu jest wyświetlany jako `Signature` pola, które jest taka sama jak wywołanie [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) polecenie cmdlet na plik wykazu.
Użytkownicy mogą również pomijać każdego pliku podczas weryfikacji za pomocą `FilesToSkip` parametru.
