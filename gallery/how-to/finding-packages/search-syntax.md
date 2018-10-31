---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Składnia wyszukiwania w galerii
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004077"
---
# <a name="gallery-search-syntax"></a>Składnia wyszukiwania w galerii

Galeria programu PowerShell oferuje searchbox tekstu, których można użyć słów i fraz wyrażeń — słowo kluczowe, aby zawęzić wyniki wyszukiwania.

## <a name="search-by-keywords"></a>Wyszukiwanie według słów kluczowych

    dsc azure sql

Wyszukiwanie wykonaj jego wszelkich starań, aby znaleźć odpowiednie dokumenty zawierające wszystkie 3 słowa kluczowe i zwracać pasujących dokumentów.

## <a name="search-using-phrases-and-keywords"></a>Wyszukaj przy użyciu słów kluczowych i fraz

    "azure sql" deployment

Wprowadź frazę między znakami cudzysłowu ("") zmodyfikuj wyszukiwanie, aby wyszukać określoną frazę zamiast oddzielnych słów kluczowych.
Pasujących dokumentów zazwyczaj powinna zawierać dokładnej frazy "azure sql", np. w tym odmiany wielkość liter "Usługa azure SQL", a także zwykle zawierają wyraz "wdrożenie".

## <a name="filtering-on-fields"></a>Filtrowanie według pól

Wyszukaj identyfikator określony pakiet (lub "Id" lub "id") lub niektóre inne pola przez dodanie przedrostka wyszukiwanego terminu z polem o nazwie.

Obecnie pola z możliwością wyszukiwania są "Id", "Version", "Autor", "DscResources", "Właściciel", "Poleceń cmdlet", "Tagów", "Funkcji" i "PowerShellVersion".

[Co to jest różnicą między identyfikator i tytuł? Identyfikator jest nazwą, używane w konsoli. Tytuł jest przedstawionego w górnej części strony pakietu w wynikach wyszukiwania.]

## <a name="examples"></a>Przykłady

    ID:"PSReadline"
    id:"AzureRM.Profile"

Umożliwia znalezienie pakietów o "PSReadline" lub "AzureRM.Profile" w polu Identyfikatora odpowiednio.

    Id:"AzureRM.Profile"

to kolejny sposób, aby znaleźć pakiety z "AzureRM.Profile" w polu Identyfikatora.

Filtr 'Id' jest podciąg być zgodne, dlatego w przypadku wyszukiwania dla następujących:

    Id:"azure"

Otrzymasz wyników, takich jak "AzureRM.Profile" i "Azure.Storage".

Możesz również wyszukać wiele słów kluczowych w jednym polu. Lub mieszanie i Dopasowywanie pól.

    id:azure tags:intellisense
    id:azure id:storage

I wyszukiwanie frazy:

    id:"azure.storage"


Aby wyszukać wszystkie pakiety z tagiem DSC.

    Tags:"DSC"

Aby wyszukać wszystkie pakiety przy użyciu określonej funkcji.

    Functions:"Update-AzureRM"

Aby wyszukać wszystkie pakiety za pomocą określonego polecenia cmdlet.

    Cmdlets:"Get-AzureRmEnvironment"

Aby wyszukać wszystkie pakiety z określoną nazwą zasobu DSC.

    DscResources:"xArchive"

Aby wyszukać wszystkie pakiety za pomocą określonego PowerShellVersion

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Ponadto jeśli używasz pola, które nie są obsługiwane, takich jak "poleceń", utworzymy po prostu go zignorować i wszystkie pola wyszukiwania. Rozważmy następujące zapytanie

    commands:blobs storage

Jest interpretowane tak samo jak to zapytanie:

    blobs storage
