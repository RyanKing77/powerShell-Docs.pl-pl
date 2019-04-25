---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Składnia wyszukiwania w galerii
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084304"
---
# <a name="gallery-search-syntax"></a>Składnia wyszukiwania w galerii

Można wyszukiwać za pomocą galerii programu PowerShell [witryny sieci web galerii programu PowerShell](https://www.powershellgallery.com/).
Witryny sieci web galerii programu PowerShell oferuje searchbox tekstu, których można użyć słów i fraz wyrażeń — słowo kluczowe, aby zawęzić wyniki wyszukiwania.

## <a name="search-by-keywords"></a>Wyszukiwanie według słów kluczowych

    dsc azure sql

Wyszukiwanie próbuje znaleźć odpowiednie dokumenty zawierające wszystkie 3 słowa kluczowe i zwracać pasujących dokumentów.

## <a name="search-using-phrases-and-keywords"></a>Wyszukaj przy użyciu słów kluczowych i fraz

    "azure sql" deployment

Wprowadź frazę między znakami cudzysłowu ("") zmodyfikuj wyszukiwanie, aby wyszukać określoną frazę zamiast oddzielnych słów kluczowych.
Pasujących dokumentów zazwyczaj powinna zawierać dokładnej frazy "azure sql", np. w tym odmiany wielkość liter "Usługa azure SQL", a także zwykle zawierają wyraz "wdrożenie".

## <a name="filtering-on-fields"></a>Filtrowanie według pól

Wyszukaj identyfikator określony pakiet (lub "Id" lub "id") lub niektóre inne pola przez dodanie przedrostka wyszukiwanego terminu z polem o nazwie.

Obecnie pola z możliwością wyszukiwania są "Id", "Version", "Autor", "DscResources", "Właściciel", "Poleceń cmdlet", "Tagów", "Funkcji" i "PowerShellVersion".

[Co to jest różnicą między identyfikator i tytuł? Identyfikator jest nazwą, używane w konsoli. Tytuł jest przedstawionego w górnej części strony pakietu w wynikach wyszukiwania.]

## <a name="examples"></a>Przykłady

    ID:PSReadline
    
Umożliwia znalezienie pakietów o identyfikatorze zawierające "PSReadline".

    Id:"AzureRM.Profile"

to kolejny sposób, aby znaleźć pakiety z "AzureRM.Profile" w polu Identyfikatora.

Filtr 'Id' jest podciąg być zgodne, dlatego w przypadku wyszukiwania dla następujących:

    Id:"azure"

Dzięki temu wyniki, które obejmują AzureRM.Profile "i"Azure.Storage".

Możesz również wyszukać wiele słów kluczowych w jednym polu. 

    id:azure tags:intellisense

I wyszukiwanie frazy przy użyciu podwójnych cudzysłowów:

    id:"azure.storage"

Aby wyszukać wszystkie pakiety z tagiem DSC.

    Tags:DSC

Aby wyszukać wszystkie pakiety przy użyciu określonej funkcji.

    Functions:Get-TreeSize

Aby wyszukać wszystkie pakiety za pomocą określonego polecenia cmdlet.

    Cmdlets:Get-AzureRmEnvironment

Aby wyszukać wszystkie pakiety z określoną nazwą zasobu DSC.

    DscResources:xArchive

Aby wyszukać wszystkie pakiety za pomocą określonego PowerShellVersion

    PowerShellVersion:2.0

Ponadto jeśli używasz pola, które nie są obsługiwane, takich jak "poleceń", utworzymy po prostu go zignorować i wszystkie pola wyszukiwania. Rozważmy następujące zapytanie

    commands:blobs storage

Jest interpretowane tak samo jak to zapytanie:

    blobs storage
