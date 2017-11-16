---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, programu powershell, ustawienia
title: Polecenia cmdlet katalogu
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a>Polecenia cmdlet katalogu  

Dodano dwa nowe polecenia cmdlet w [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) modułu, aby wygenerować i zweryfikować pliki w katalogu systemu windows.  

## <a name="new-filecatalog"></a>Nowe FileCatalog 
--------------------------------

`New-FileCatalog`Tworzy plik katalogu systemu windows dla zestawu plików i folderów. Skróty do wszystkich plików określonych ścieżek zawiera plik wykazu. Użytkownicy można rozpowszechniać zestaw folderów oraz odpowiadający plik wykazu, który reprezentuje te foldery. Plik wykazu mogą posłużyć odbiorcom zawartości do sprawdzania, czy wprowadzono zmiany do folderów po utworzeniu katalogu.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Firma Microsoft obsługuje tworzenie katalogu w wersji 1 i 2. W wersji 1 używa algorytmu wyznaczania wartości skrótu SHA1 do tworzenia plików, skrótów i w wersji 2 używa SHA256. 2. Wersja katalogu nie jest obsługiwana w *systemu Windows Server 2008 R2* i *Windows 7*. Zaleca się korzystają z katalogu w wersji 2 przy użyciu platform *systemu Windows 8*, *systemu Windows Server 2012* i powyżej.  

Aby użyć tego polecenia na istniejący moduł, określ zmienne CatalogFilePath i ścieżka do dopasowania lokalizacja manifestu modułu. W poniższym przykładzie manifestu modułu jest C:\Program Files\Windows PowerShell\Modules\Pester. 

![](../images/NewFileCatalog.jpg)

Spowoduje to utworzenie pliku wykazu. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Aby sprawdzić integralność pliku wykazu (Pester.cat w powyżej exmaple) powinien on być podpisany przy użyciu [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) polecenia cmdlet.   


## <a name="test-filecatalog"></a>FileCatalog testu 
--------------------------------

`Test-FileCatalog`weryfikuje katalogu, reprezentujący zestaw folderów. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

To polecenie cmdlet porównuje wartości skrótów wszystkich plików i ich ścieżek względnych znaleziono w pliku wykazu te są zapisywane na dysku. W przypadku wykrycia niezgodność wartości skrótu pliku i ścieżki zwraca stan `ValidationFailed`. Użytkownicy mogą pobrać wszystkie te informacje przy użyciu `Detailed` przełącznika. Stan podpisywania katalogu jest wyświetlany jako `Signature` pola, które jest taka sama jak wywołanie [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) polecenia cmdlet na plik wykazu. Użytkownicy mogą też pominąć każdego pliku, podczas sprawdzania poprawności przy użyciu `FilesToSkip` parametru. 

