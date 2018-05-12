---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Składnia poleceń wyszukiwania galerii
ms.openlocfilehash: 4c0e357957ef970826ee90868db78ac07a14c804
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="gallery-search-syntax"></a>Składnia poleceń wyszukiwania galerii

Galerii programu PowerShell oferuje searchbox tekst, gdzie można użyć słowa, wyrażenia i wyrażeń — słowo kluczowe, aby zawęzić wyniki wyszukiwania.

## <a name="search-by-keywords"></a>Wyszukiwanie według słów kluczowych

    dsc azure sql

Wyszukiwanie wykonaj jego starań, aby znaleźć odpowiednie dokumenty zawierające wszystkie 3 słowa kluczowe i zwracać pasujących dokumentów.

## <a name="search-using-phrases-and-keywords"></a>Wyszukiwanie przy użyciu wyrażeń i słów kluczowych

    "azure sql" deployment

Wprowadzanie frazę w cudzysłów ("") zmodyfikuj wyszukiwanie, aby wyszukać określonego frazy zamiast osobne słowa kluczowe.
Dopasowywanie dokumentów zwykle powinna zawierać dokładną frazę "azure sql", np. w tym odmiany wielkość liter "Azure SQL", a także zwykle zawiera słowo "wdrożenie".

## <a name="filtering-on-fields"></a>Filtrowanie według pól

Wyszukiwanie identyfikator określonego elementu (lub "Id" lub "id") lub niektóre inne pola, dodając terminy nazwą pola wyszukiwania.

Obecnie pól z możliwością wyszukiwania są "Id", "Version", "Tagi", "Autor", "Właściciel", "Funkcji", "Poleceń cmdlet", "DscResources" i "PowerShellVersion".

[Jaka jest różnica między identyfikator i tytuł? Identyfikator jest nazwą używanego w konsoli. Tytuł jest to, co jest wyświetlany w górnej części strony elementu w wynikach wyszukiwania.]

## <a name="examples"></a>Przykłady

    ID:"PSReadline"
    id:"AzureRM.Profile"

odpowiednio znajduje "PSReadline" lub "AzureRM.Profile" w polu Identyfikatora.

    Id:"AzureRM.Profile"

jest inny sposób, aby znaleźć elementy z "AzureRM.Profile" w polu Identyfikatora.

Filtr 'Id' jest podciągu są zgodne, to w przypadku następujących czynności:

    Id:"azure"

Można uzyskać wyników, takich jak "AzureRM.Profile" i "Azure.Storage".

Możesz również wyszukać wiele słów kluczowych w jednym polu. Lub mieszać i dopasować pola.

    id:azure tags:intellisense
    id:azure id:storage

I mogą wykonywać wyszukiwania fraz:

    id:"azure.storage"


Aby wyszukać wszystkie elementy z tagiem DSC.

    Tags:"DSC"

Aby wyszukać wszystkie elementy o określonej funkcji.

    Functions:"Update-AzureRM"

Aby wyszukać wszystkie elementy z określone polecenie cmdlet.

    Cmdlets:"Get-AzureRmEnvironment"

Aby wyszukać wszystkie elementy o określonej nazwie zasobu usługi Konfiguracja DSC.

    DscResources:"xArchive"

Aby wyszukać wszystkie elementy z określonej PowerShellVersion

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Ponadto użycie pola, które nie są obsługiwane, takie jak "polecenia", firma Microsoft będzie tylko ją zignorować i wyszukiwanie wszystkich pól. Dlatego po zapytania

    commands:blobs storage

Jest interpretowany tak samo jak to zapytanie:

    blobs storage