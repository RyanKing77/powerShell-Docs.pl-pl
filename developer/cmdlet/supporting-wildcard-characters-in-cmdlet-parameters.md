---
title: Obsługa symboli wieloznacznych w parametry polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851373"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Obsługiwanie symboli wieloznacznych w parametrach poleceń cmdlet

Często należy zaprojektować polecenia cmdlet do uruchamiania w odniesieniu do grupy zasobów, a nie względem pojedynczy zasób. Na przykład polecenia cmdlet konieczne zlokalizować wszystkich plików w magazynie danych o takiej samej nazwie lub rozszerzenia. Podczas projektowania polecenia cmdlet, które będą uruchamiane w odniesieniu do grupy zasobów, musisz podać pomocy technicznej dla symboli wieloznacznych.

> [!NOTE]
> Przy użyciu symboli wieloznacznych jest czasami określane jako *symboli wieloznacznych*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Polecenia cmdlet programu PowerShell Windows, który używać symboli wieloznacznych

 Wiele poleceń cmdlet programu Windows PowerShell obsługuje znaki symboli wieloznacznych dla ich wartości parametrów. Na przykład niemal każdego polecenia cmdlet, ma `Name` lub `Path` parametr obsługuje znaki symboli wieloznacznych dla tych parametrów. (Mimo że większość poleceń cmdlet, które mają `Path` parametr również mieć `LiteralPath` parametr, który nie obsługuje symboli wieloznacznych.) Następujące polecenie pokazuje, jak symbolem wieloznacznym jest używana do zwracania wszystkich poleceń cmdlet w bieżącej sesji, którego nazwa zawiera zlecenia Get.

 **PS > get polecenia get -\***

## <a name="supported-wildcard-characters"></a>Obsługiwane symbole wieloznaczne

Program Windows PowerShell obsługuje następujące znaki symboli wieloznacznych.

|wieloznaczny|Opis|Przykład|Zgodne|Nie jest zgodny z|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Dopasowuje zero lub więcej znaków, zaczynając od określonej pozycji|a*|, Ag firmy Apple||
|?|Anycharacter dopasowań w określonym położeniu|?n|W polu, na|uruchomiono|
|[ ]|Dopasowuje szeroką gamę znaków|ook [a-l]|książki, Cooka, wygląd|trwała|
|[ ]|Pasuje do określonych znaków|ook [bc]|książki, Cooka|wygląd|

Podczas projektowania poleceń cmdlet, który obsługuje znaki symboli wieloznacznych, umożliwiają kombinacji symboli wieloznacznych. Na przykład następujące polecenie używa `Get-ChildItem` polecenie cmdlet do pobierania wszystkich plików txt znajdujących się w folderze c:\Techdocs i zaczynające się od liter "" do "l."

**polecenie GET-childitem c:\techdocs\\[a-l]\*txt**

Poprzednie polecenie korzysta z symbolami wieloznacznymi zakresu **[a-l]** do określenia, czy nazwa pliku ma się zacząć od znaków "" do "l." Następnie używa polecenia * wieloznacznego jako symbolu zastępczego dla żadnych znaków między pierwszą literę nazwy pliku i rozszerzenie txt.

W poniższym przykładzie użyto wzór symboli wieloznacznych zakres, który wyklucza literę "d", ale obejmuje wszystkie inne litery od "a" do "f."

**polecenie GET-childitem c:\techdocs\\[a cef]\*txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Obsługa znaków literałowych w wzorców symboli wieloznacznych

Jeśli wzór symboli wieloznacznych, które określisz zawiera znaki literału, należy użyć znaku początkowych ('), jako znak ucieczki. Po określeniu programowo znaków literałowych, należy użyć pojedynczej początkowych. Po określeniu znaków literałowych w wierszu polecenia, użyj dwa znaki grawisu. Na przykład następujący wzorzec zawiera dwa nawiasy kwadratowe, które należy podjąć, dosłownie.

"Jan Kowalski \`[*"] "(określony programowe)

"Jan Kowalski \` \`[*\`"] "(określony w wierszu polecenia)

Ten wzorzec pasuje do "Jan Kowalski [Marketing]" lub "Jan Kowalski [programowanie]".

## <a name="cmdlet-output-and-wildcard-characters"></a>Dane wyjściowe polecenia cmdlet i symboli wieloznacznych

Parametry polecenia cmdlet obsługuje znaki symboli wieloznacznych, działanie polecenia cmdlet zwykle generuje dane wyjściowe tablicy. Od czasu do czasu nie ma sensu obsługi tablicy danych wyjściowych, ponieważ użytkownik może użyć tylko pojedynczego elementu w danym momencie. Na przykład `Set-Location` polecenie cmdlet obsługuje tablicy danych wyjściowych, ponieważ użytkownik ustawia jednej lokalizacji. W tym wypadku polecenia cmdlet nadal obsługuje znaki symboli wieloznacznych, ale wymusza rozdzielczości w jednym miejscu.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Klasa WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
