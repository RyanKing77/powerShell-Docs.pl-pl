---
title: Odwołanie do schematu XML do formatu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac6f7aaa-d0cc-4c7b-a341-85e736174579
caps.latest.revision: 21
ms.openlocfilehash: 437b3d6bb62fdd3a74f3392ec71df360c01a1974
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065788"
---
# <a name="format-schema-xml-reference"></a>Dokumentacja dotycząca formatowania kodu XML schematu

Tematy w tej sekcji opisano elementy XML używane przez formatowanie pliki (Format.ps1xml). Pliki formatowania zdefiniować sposób wyświetlania obiektu .NET; nie należy zmieniać sam obiekt.

## <a name="in-this-section"></a>W tej sekcji

[Wyrównanie elementu TableColumnHeader dla tablecontrol — (w formacie)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) definiuje sposób wyświetlania danych w nagłówkach kolumn.

[Wyrównanie elementu TableColumnItem dla tablecontrol — (w formacie)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) definiuje sposób wyświetlania danych w wierszu.

[Tablecontrol — (w formacie) — AutoSize Element](./autosize-element-for-tablecontrol-format.md) Określa, czy dostosować rozmiar kolumny i liczba kolumn na podstawie rozmiaru danych.

[AutoSize Element WideControl (Format)](./autosize-element-for-widecontrol-format.md) Określa, czy dostosować rozmiar kolumny i liczba kolumn na podstawie rozmiaru danych.

[ColumnNumber Element WideControl (Format)](./columnnumber-element-for-widecontrol-format.md) określa liczbę kolumn wyświetlanych w szerokim oknie.

[Element konfiguracji (Format)](./configuration-element-format.md) reprezentuje element najwyższego poziomu w pliku formatowania.

[Kontrolowanie elementu dla formantów dla konfiguracji (Format)](./control-element-for-controls-for-configuration-format.md) definiuje typowe formant, który może być używany przez wszystkie widoki formatowania pliku i nazwę, która jest używana do odwołania kontrolki.

[Kontrolowanie elementu dla formantów widoku (Format)](./control-element-for-controls-for-view-format.md) definiuje formant, który może służyć przez widok i nazwę, która jest używana do odwołania kontrolki.

[Określa Element konfiguracji (Format)](./controls-element-for-configuration-format.md) definiuje wspólnych formantów, które mogą być używane przez wszystkie widoki formatowania pliku.

[Kontrolki elementu widoku (Format)](./controls-element-for-view-format.md) definiuje kontrolki widoku, które mogą być używane przez określonego widoku.

[Element formant niestandardowy do sterowania do konfiguracji (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md) definiuje formant. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[Formant niestandardowy Element dla formantu dla formantów widoku (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md) definiuje formant, który jest używany przez widok.

[Element formant niestandardowy do grupowania (w formacie)](./customcontrol-element-for-groupby-format.md) definiuje niestandardowy formant, który wyświetla nową grupę.

[Formant niestandardowy, Element (w formacie)](./customcontrol-element-for-groupby-format.md) definiuje format formantu niestandardowego dla widoku.

[CustomControlName Element ExpressionBinding dla formantów dla konfiguracji (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md) Określa nazwę formantu wspólnego. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[CustomControlName Element ExpressionBindine dla formantów widoku (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md) Określa nazwę wspólne kontrolki lub kontrolki widoku. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[CustomControlName Element GroupBy (Format)](./customcontrolname-element-for-groupby-format.md) Określa nazwę kontrolki niestandardowej, która jest używana do wyświetlania nowej grupy. Ten element jest używany podczas definiowania tabel, list, szeroki lub niestandardowe kontrolki widoku.

[CustomEntry Element formant niestandardowy dla formantów dla konfiguracji (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md) zawiera definicję wspólnej kontroli. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[CustomEntry Element CustomEntries dla formantów widoku (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md) zawiera definicję formantu. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[CustomEntry Element CustomEntries widoku (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md) zawiera definicję widoku formantu niestandardowego.

[CustomEntry Element formant niestandardowy do grupowania (w formacie)](./customentry-element-for-customcontrol-for-groupby-format.md) zawiera definicję formantu. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[CustomEntries Element formant niestandardowy do konfiguracji (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md) zawiera definicje wspólnej kontroli. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[CustomEntries Element formant niestandardowy dla formantów widoku (Format)](./customentries-element-for-customcontrol-for-controls-for-view-format.md) zawiera definicje dla formantu. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[CustomEntries Element formant niestandardowy do grupowania (w formacie)](./customentries-element-for-customcontrol-for-groupby-format.md) zawiera definicje dla formantu. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[CustomEntries Element formant niestandardowy dla widoku (Format)](./customentries-element-for-customcontrol-for-view-format.md) zawiera definicje widoku formantu niestandardowego. Wyświetl formant niestandardowy, należy określić co najmniej jedną definicję.

[CustomItem Element CustomEntry dla formantów dla konfiguracji](./customitem-element-for-customentry-for-controls-for-configuration-format.md) definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[CustomItem Element CustomEntry dla formantów widoku (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md) definiuje, jakie dane są wyświetlane przez kontrolkę i sposób wyświetlania. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[CustomItem Element CustomEntry widoku (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md) definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[CustomItem Element CustomEntry dla grupowania (w formacie)](./customitem-element-for-customentry-for-groupby-format.md) definiuje, jakie dane są wyświetlane w widoku formantu niestandardowego i sposób wyświetlania. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[DefaultSettings Element (Format)](./defaultsettings-element-format.md) definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku. Typowe ustawienia obejmują wyświetlanie błędów, zawijania tekstu w tabelach, określające, jak kolekcje są rozwinięte i więcej.

[DisplayError Element (Format)](./displayerror-element-format.md) Określa, czy ciąg #ERR są wyświetlane, gdy wystąpi błąd wyświetlania elementu danych.

[EntrySelectedBy Element CustomEntry dla formantów dla konfiguracji (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md) Określa typy .NET, korzystających z definicji formantu typowego lub warunek, który musi istnieć dla tej kontrolki ma być używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[EntrySelectedBy Element CustomEntry dla formantów widoku (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md) Określa typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[EntrySelectedBy Element CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) Określa typy .NET, korzystające z tego wpisu niestandardowych lub warunek, który musi istnieć dla tego wpisu do użycia.

[EntrySelectedBy Element EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md) Określa typy .NET, które używają tej definicji lub warunek, który musi istnieć, aby ta definicja ma być używany.

[EntrySelectedBy Element CustomEntry dla grupowania (w formacie)](./entryselectedby-element-for-customentry-for-groupby-format.md) Określa typy .NET, które używają tej definicji kontroli lub warunek, który musi istnieć, aby ta definicja ma być używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[EntrySelectedBy Element ListEntry dla elementu ListControl (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Określa typy .NET, korzystające z tej listy definicji widoku lub warunek, który musi istnieć, aby ta definicja ma być używany. W większości przypadków tylko jedną definicję, jest wymagany dla widoku listy. Może jednak zapewniać wiele definicji widoku listy, jeśli chcesz użyć tego samego widoku listy do wyświetlenia różnych danych do różnych obiektów.

[EntrySelectedBy Element TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Określa typy .NET, w których wartości właściwości są wyświetlane w wierszu.

[EntrySelectedBy Element WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md) Określa typy .NET używających tej definicji szerokie lub warunek, który musi istnieć, aby ta definicja ma być używany.

[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md) definiuje sposób określonej kolekcji .NET, które obiekty są rozszerzane, gdy są one wyświetlane w widoku.

[EnumerableExpansions Element (Format)](./enumerableexpansions-element-format.md) definiuje, jak rozszerzyć obiekty kolekcji .NET, gdy są one wyświetlane w widoku.

[EnumerateCollection Element ExpressionBinding dla formantów dla konfiguracji (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md) określono, że elementy kolekcji są wyświetlane przez kontrolkę. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[EnumerateCollection Element ExpressionBinding dla formantów widoku (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md) określono, że elementy kolekcji są wyświetlane. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[EnumerateCollection Element wyrażenia powiązania dla formant niestandardowy dla widoku (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md) Określa, czy elementy kolekcji są wyświetlane. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[EnumerateCollection Element ExpressionBinding dla grupowania (w formacie)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Określa, czy elementy kolekcji są wyświetlane. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[Rozwiń Element (w formacie)](./expand-element-format.md) Określa, jak obiekt kolekcji jest rozwinięta, dla tej definicji.

[ExpressionBinding Element CustomItem dla formantów dla konfiguracji (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md) definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[ExpressionBinding Element CustomItem dla formantów widoku (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md) definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[ExpressionBinding Element CustomItem dla formant niestandardowy dla widoku (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md) definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[ExpressionBinding Element CustomItem dla grupowania (w formacie)](./expressionbinding-element-for-customitem-for-groupby-format.md) definiuje dane, które jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[FirstLineHanging Element ramki dla formantów dla konfiguracji (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[FirstLineHanging Element ramkę z formantów z widoku (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[FirstLineHanging Element ramki dla formant niestandardowy dla widoku (Format)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[FirstLineHanging Element ramki dla grupowania (w formacie)](./firstlinehanging-element-for-frame-for-groupby-format.md) określa liczbę znaków w pierwszym wierszu danych zostanie przesunięty w lewo. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[FirstLineIndent Element ramki dla formantów dla konfiguracji (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[FirstLineIndent Element ramkę z formantów z widoku (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md) określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[FirstLineIndent Element ramki dla grupowania (w formacie)](./firstlineindent-element-for-frame-for-groupby-format.md) określa liczbę znaków w pierwszym wierszu danych jest przesuwany w prawo. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[FormatString Element dla elementu listy (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md) Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu.

[FormatString Element dla TableColumnItem (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md) Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skrypt tabeli.

[FormatString Element dla WideItem dla WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md) Określa wzorzec formatu, który definiuje sposób wyświetlania wartości właściwości lub skryptu w widoku.

[Ramkę elementu CustomItem dla formantów dla konfiguracji (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md) definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[Ramkę elementu CustomItem dla formantów widoku (Format)](./frame-element-for-customitem-for-controls-for-view-format.md) definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[Ramkę elementu dla CustomItem formant niestandardowy dla widoku (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md) definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[Ramkę elementu CustomItem dla grupowania (w formacie)](./frame-element-for-customitem-for-groupby-format.md) definiuje sposób wyświetlania danych, takie jak przesunięcie danych do lewej lub prawej strony. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[GroupBy — Element dla widoku (Format)](./groupby-element-for-view-format.md) definiuje, jak środowiska Windows PowerShell wyświetla nowe grupy obiektów.

[HideTableHeaders Element (Format)](./hidetableheaders-element-format.md) Określa, czy nagłówki tabeli nie są wyświetlane.

[ItemSelectionCondition Element ExpressionBinding dla formantów dla konfiguracji (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md) definiuje warunek, który musi istnieć dla tej kontrolki ma być używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[ItemSelectionCondition Element ExpressionBinding dla formantów widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md) definiuje warunek, który musi istnieć dla tej kontrolki ma być używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[ItemSelectionCondition Element wyrażenia powiązania dla formant niestandardowy dla widoku (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md) definiuje warunek, który musi istnieć dla tej kontrolki ma być używany. Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[ItemSelectionCondition Element ExpressionBinding dla grupowania (w formacie)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md) definiuje warunek, który musi istnieć dla tej kontrolki ma być używany. Nie ma żadnego limitu, liczbę warunków wyboru, które mogą być określone dla elementu kontrolki. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[Element ListItem (Format) ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) definiuje warunek, który musi istnieć przez ten element listy do użycia.

[Etykiety elementów dla elementu listy dla ListControl(Format)](./label-element-for-listitem-for-listcontrol-format.md) Określa etykietę dla wartości właściwości lub skryptu w wierszu.

[Etykieta elementu dla grupowania (w formacie)](./label-element-for-groupby-format.md) Określa etykietę, która jest wyświetlana, gdy zostanie osiągnięty nowej grupy.

[Etykieta elementu dla TableColumnHeader (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) definiuje etykietę, która jest wyświetlana w górnej części kolumny.

[LeftIndent Element ramki dla formantów dla konfiguracji (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md) określa liczbę znaków od lewego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[LeftIndent Element ramkę z formantów z widoku (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md) określa liczbę znaków od lewego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[LeftIndent Element ramki dla formant niestandardowy dla widoku (Format)](./leftindent-element-for-frame-for-customcontrol-for-view-format.md) określa liczbę znaków od lewego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[LeftIndent Element ramki dla grupowania (w formacie)](./leftindent-element-for-frame-for-groupby-format.md) określa liczbę znaków od lewego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[Element elementu ListControl (Format)](./listcontrol-element-format.md) definiuje format listy dla widoku.

[ListEntry Element (Format)](./listentry-element-for-listcontrol-format.md) zawiera definicję widoku listy.

[ListEntries Element (Format)](./listentries-element-for-listcontrol-format.md) definiuje sposób wyświetlania wierszy w widoku listy.

[ListItem — Element (w formacie)](./listitem-element-for-listitems-for-listcontrol-format.md) definiuje właściwość lub skryptu, którego wartość jest wyświetlana w wierszu w widoku listy.

[ListItems Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md) definiuje właściwości i skrypty, które są wyświetlane w widoku listy.

[Nazwa elementu dla formantu dla formantów dla konfiguracji (Format)](./name-element-for-control-for-controls-for-configuration-format.md) Określa nazwę formantu. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[Nazwa elementu dla SelectionSet (Format)](./name-element-for-selectionset-format.md) Określa nazwę używaną do odwoływać się do zestawu wyboru.

[Nazwa elementu widoku (Format)](./name-element-for-view-format.md) Określa nazwę, która służy do identyfikacji tego widoku.

[Element nowego wiersza dla CustomItem dla formantów dla konfiguracji (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md) dodaje pusty wiersz do wyświetlania kontrolki. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[Element nowego wiersza dla CustomItem dla formantów widoku (Format)](./newline-element-for-customitem-for-controls-for-view-format.md) dodaje pusty wiersz do wyświetlania kontrolki. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[Element nowego wiersza dla CustomItem dla formant niestandardowy dla widoku (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md) dodaje pusty wiersz do wyświetlania kontrolki. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[Element nowego wiersza dla CustomItem dla grupowania (w formacie)](./newline-element-for-customitem-for-groupby-format.md) dodaje pusty wiersz do wyświetlania kontrolki. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[PropertyName Element ExpressionBinding dla formantów dla konfiguracji (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md) określa właściwości platformy .NET, którego wartość jest wyświetlana za pomocą wspólnej kontroli. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[PropertyName Element ExpressionBinding dla formantów widoku (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md) określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[PropertyName Element ExpressionBinding dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md) określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania widoku formantu niestandardowego

[PropertyName Element ExpressionBinding dla grupowania (w formacie)](./propertyname-element-for-expressionbinding-for-groupby-format.md) określa właściwości platformy .NET, którego wartość jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[PropertyName Element GroupBy (Format)](./propertyname-element-for-groupby-format.md) określa właściwości platformy .NET, który uruchamia nową grupę, zmianie wartości.

[PropertyName Element ItemSeclectionCondition dla formantów dla konfiguracji (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[PropertyName Element ItemSelectionCondition dla formantów widoku (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[PropertyName Element ItemSelectionCondition dla formant niestandardowy dla widoku (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[PropertyName Element ItemSelectionCondition dla grupowania (w formacie)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[PropertyName Element ItemSelectionCondition dla elementu listy (Format)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, a widok jest używany. Ten element jest używany podczas definiowania widoku listy.

[Element ListItem dla elementu ListControl (Format) PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) określa właściwości platformy .NET, którego wartość jest wyświetlana na liście.

[PropertyName Element SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, a ten wpis jest używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[PropertyName Element SelectionCondition dla formantów widoku (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, a ten wpis jest używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[PropertyName Element SelectionCondition dla formant niestandardowy dla widoku (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[PropertyName Element SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.

[PropertyName Element SelectionCondition dla grupowania (w formacie)](./propertyname-element-for-selectioncondition-for-groupby-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[PropertyName Element SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i wpis na liście jest używany.

[PropertyName Element SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i służy wpisu tabeli.

[PropertyName Element SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) określa właściwości platformy .NET, która wyzwala warunku. Gdy ta właściwość jest obecny, lub jeśli wynikiem jego obliczenia `true`, warunek jest spełniony, i jest używany przez definicję.

[PropertyName Element TableColumnItem (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Określa właściwość, której wartość jest wyświetlana w kolumnie wiersza.

[PropertyName Element WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md) Określa właściwość obiektu, którego wartość jest wyświetlana w szerokim oknie.

[RightIndent Element ramki dla formantów dla konfiguracji (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md) określa liczbę znaków od prawego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[RightIndent Element ramkę z formantów z widoku (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md) określa liczbę znaków od prawego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md) określa liczbę znaków od prawego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[RightIndent Element ramki dla grupowania (w formacie)](./rightindent-element-for-frame-for-groupby-format.md) określa liczbę znaków od prawego marginesu zostanie przesunięty w danych. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[ScriptBlock Element ExpressionBinding dla formantów dla konfiguracji (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md) Określa skrypt, którego wartość jest wyświetlana za pomocą wspólnej kontroli. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[ScriptBlock Element ExpressionBinding dla formantów widoku (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md) Określa skrypt, którego wartość jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[ScriptBlock Element ExpressionBinding dla CustomCustomControl widoku (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md) Określa skrypt, którego wartość jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[ScriptBlock Element ExpressionBinding dla grupowania (w formacie)](./scriptblock-element-for-expressionbinding-for-groupby-format.md) Określa skrypt, którego wartość jest wyświetlany przez kontrolkę. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[ScriptBlock Element GroupBy (Format)](./scriptblock-element-for-groupby-format.md) Określa skrypt, który uruchamia nową grupę, zmianie wartości.

[ScriptBlock Element ItemSelectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[ScriptBlock Element ItemSelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[ScriptBlock Element ItemSelectionCondition dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[ScriptBlock Element ItemSelectionCondition dla grupowania (w formacie)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i formant jest używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[ScriptBlock Element ItemSelectionCondition dla elementu ListControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany w elemencie listy. Ten element jest używany podczas definiowania widoku listy.

[Element ListItem (Format) ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) Określa skrypt, którego wartość jest wyświetlana w wierszu listy.

[ScriptBlock Element SelectionCondition dla formantów dla konfiguracji (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[ScriptBlock Element SelectionCondition dla formantów widoku (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[ScriptBlock Element SelectionCondition dla formant niestandardowy dla widoku (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[ScriptBlock Element SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Określa skrypt, który wyzwala warunku.

[ScriptBlock Element SelectionCondition dla grupowania (w formacie)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany przez definicję. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[ScriptBlock Element SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i wpis na liście jest używany.

[ScriptBlock Element SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) określa Blok skryptu, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i służy wpisu tabeli.

[ScriptBlock Element SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i definicja szerokiego wpis jest używana.

[ScriptBlock Element TableColumnItem (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Określa skrypt, którego wartość jest wyświetlana w kolumnie wiersza.

[ScriptBlock Element WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Określa skrypt, którego wartość jest wyświetlana w szerokim oknie.

[SelectionCondition Element EntrySelectedBy dla CustomEntry konfiguracji (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md) definiuje warunek, który musi istnieć do wspólnej definicji kontrolki ma być używany. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[SelectionCondition Element EntrySelectedBy dla formantów widoku (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md) definiuje warunek, który musi istnieć dla definicji kontrolki ma być używany. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[SelectionCondition Element EntrySelectedBy dla formant niestandardowy dla widoku (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md) definiuje warunek, który musi istnieć dla definicji kontrolki ma być używany. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[SelectionCondition Element EntrySelectedBy dla EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md) definiuje warunek, który musi istnieć, aby rozwinąć kolekcji obiektów tej definicji.

[SelectionCondition Element EntrySelectedBy dla grupowania (w formacie)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md) definiuje warunek, który musi istnieć dla definicji kontrolki ma być używany. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[SelectionCondition Element EntrySelectedBy dla ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) definiuje warunek, którego można użyć tej definicji widoku listy, musi istnieć. Nie ma żadnego limitu liczby warunki wyboru, które mogą być określone dla definicji listy.

[SelectionCondition Element EntrySelectedBy dla TableRowEntry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md) definiuje warunek, który musi istnieć na potrzeby tej definicji widoku tabeli. Nie ma żadnego limitu liczby warunki wyboru, które można określić definicję tabeli.

[SelectionCondition Element EntrySelectedBy dla WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) definiuje warunek, który musi istnieć, aby ta definicja ma być używany. Nie ma żadnego limitu, liczbę warunków wyboru, które można określić dla definicji szerokiego wpisu.

[SelectionSet Element (Format)](./selectionset-element-format.md) definiuje zestaw obiektów platformy .NET, które mogą być przywoływane przez nazwę zestawu.

[SelectionSetName Element EntrySelectedBy dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) określa zestaw typów .NET, korzystających z tej definicji formantu. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[SelectionSetName Element EntrySelectedBy dla formantów widoku (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md) określa zestaw typów .NET, korzystających z tej definicji formantu. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[SelectionSetName Element EntrySelectedBy dla CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md) określa zestaw obiektów platformy .NET dla wpisu listy. Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.

[SelectionSetName Element EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md) określa zestaw typów .NET, które są rozszerzane przez tę definicję.

[SelectionSetName Element EntrySelectedBy dla grupowania (w formacie)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md) określa zestaw obiektów platformy .NET dla wpisu listy. Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[SelectionSetName Element EntrySelectedBy dla ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) określa zestaw obiektów platformy .NET dla wpisu listy. Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.

[SelectionSetName Element EntrySelectedBy dla TableRowEntry (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md) określa zestaw .NET typy użycia tego wpisu w widoku tabeli. Nie ma żadnego limitu liczby zestawów wybór, które można określić dla wpisu.

[SelectionSetName Element EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md) określa zestaw obiektów platformy .NET dla definicji. Definicja jest używana zawsze, gdy wyświetlony zostanie jeden z tych obiektów.

[SelectionSetName Element SelectionCondition dla formantów dla konfiguracji (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md) określa zestaw typów .NET, które mogą powodować warunku. Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[SelectionSetName Element SelectionCondition dla formantów widoku (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md) określa zestaw typów .NET, które mogą powodować warunku. Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[EntrySelectedBy Element CustomEntry widoku (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md) określa zestaw typów .NET, które mogą powodować warunku. Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[SelectionSetName Element SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) określa zestaw typów .NET, które mogą powodować warunku. Jeśli jeden z typów, w tym zestawie, warunek jest spełniony.

[SelectionSetName Element SelectionCondition dla grupowania (w formacie)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md) określa zestaw typów .NET, które mogą powodować warunku. Gdy dowolnego typu, w tym zestawie, warunek jest spełniony, i jest wyświetlany obiekt, za pomocą tego formantu. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[SelectionSetName Element SelectionCondition dla EntrySelectedBy dla ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md) określa zestaw typów .NET, które mogą powodować warunku. Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji widoku listy.

[SelectionSetName Element SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) określa zestaw typów .NET, które mogą powodować warunku. Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji widoku tabeli.

[SelectionSetName Element SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md) określa zestaw typów .NET, które mogą powodować warunku. Jeśli typy w tym zestawie, warunek jest spełniony, a obiekt jest wyświetlana przy użyciu tej definicji szerokie.

[SelectionSetName Element ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md) określa zestaw obiektów platformy .NET, które są wyświetlane w widoku.

[SelectionSets Element (Format)](./selectionsets-element-format.md) definiuje zestawów obiektów platformy .NET, które mogą być używane przez format poszczególnych widokach.

[ShowError Element (Format)](./showerror-element-format.md) Określa, czy rekord pełny komunikat o błędzie jest wyświetlany, gdy wystąpi błąd podczas wyświetlania elementu danych.

[TableColumnHeader Element TableHeaders dla tablecontrol — (w formacie)](./tablecolumnheader-element-format.md) definiuje etykietę, szerokość kolumny i wyrównanie etykiety w kolumnie tabeli.

[TableColumnItem Element (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) definiuje właściwość lub skryptu, którego wartość jest wyświetlana w kolumnie wiersza.

[TableColumnItems Element (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) definiuje właściwości lub skryptów, których wartości są wyświetlane w wierszu.

[Tablecontrol — Element (w formacie)](./tablecontrol-element-format.md) definiuje format tabeli w celu wyświetlenia.

[TableHeaders Element (Format)](./tableheaders-element-format.md) definiuje nagłówki kolumn w tabeli.

[TableRowEntries Element (Format)](./tablerowentries-element-for-tablecontrol-format.md) definiuje wiersze w tabeli.

[TableRowEntry Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) definiuje dane, które są wyświetlane w wierszu tabeli.

[Tekst elementu CustomItem dla formantów dla konfiguracji (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md) Określa tekst, który jest dodawany do danych, które jest wyświetlane według kontrolki, takie jak etykiety, nawiasy kwadratowe, należy ująć danych i miejsca do magazynowania, aby wciąć danych. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[Tekst elementu CustomItem dla formantów widoku (Format)](./text-element-for-customitem-for-controls-for-view-format.md) Określa tekst, który jest dodawany do danych, które jest wyświetlane według kontrolki, takie jak etykiety, nawiasy kwadratowe, należy ująć danych i miejsca do magazynowania, aby wciąć danych. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[Tekst elementu CustomItem (Format)](./text-element-for-customitem-for-customview-for-view-format.md) Określa tekst, który jest dodawany do danych, które jest wyświetlane według kontrolki, takie jak etykiety, nawiasy kwadratowe, należy ująć danych i miejsca do magazynowania, aby wciąć danych. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[Tekst elementu CustomItem dla grupowania (w formacie)](./text-element-for-customitem-for-groupby-format.md) Określa tekst, który jest dodawany do danych, które jest wyświetlane według kontrolki, takie jak etykiety, nawiasy kwadratowe, należy ująć danych i miejsca do magazynowania, aby wciąć danych. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[TypeName Element dla EntrySelectedBy dla formantów dla konfiguracji (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md) Określa typ architektury .NET, która używa tej definicji kontrolki. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[TypeName Element dla EntrySelectedBy dla formantów widoku (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md) Określa typ architektury .NET, która używa tej definicji kontrolki. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[TypeName Element dla EntrySelectedBy dla CustomEntry widoku (Format)](./typename-element-for-entryselectedby-for-customentry-for-view-format.md) Określa typ architektury .NET, który używa tej definicji widoku formantu niestandardowego. Nie ma żadnego limitu liczby typów, które można określić dla definicji.

[TypeName Element dla EntrySelectedBy dla EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md) Określa typ architektury .NET, która jest rozszerzana przez tę definicję. Ten element jest używany podczas definiowania ustawień domyślnych.

[TypeName Element dla EntrySelectedBy dla grupowania (w formacie)](./typename-element-for-entryselectedby-for-groupby-format.md) Określa typ architektury .NET, która używa tej definicji kontrolki niestandardowej. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[TypeName Element dla EntrySelectedBy dla elementu ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md) Określa typ architektury .NET, która używa tego wpisu w widoku listy. Nie ma żadnego limitu liczby typów, które mogą być określone dla wpisu listy.

[TypeName Element dla EntrySelectedBy dla TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md) Określa typ architektury .NET, który używa tego wpisu w widoku tabeli. Nie ma żadnego limitu liczby typów, które można określić dla wpisu tabeli.

[TypeName Element dla EntrySelectedBy dla WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md) Określa typ architektury .NET w definicji. Definicja jest używana zawsze, gdy zostanie wyświetlony ten obiekt.

[TypeName Element dla SelectionCondition dla formantów dla konfiguracji (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md) Określa typ architektury .NET, która wyzwala warunku. Ten element jest używany podczas definiowania wspólnej formant, który może być używany przez wszystkie widoki w formatowaniu pliku.

[TypeName Element dla SelectionCondition dla formantów widoku (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md) Określa typ architektury .NET, która wyzwala warunku. Ten element jest używany podczas definiowania formantów, które mogą być używane przez widok.

[TypeName Element dla SelectionCondition dla formant niestandardowy dla widoku (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md) Określa typ architektury .NET, która wyzwala warunku. Ten element jest używany podczas definiowania widoku formantu niestandardowego.

[TypeName Element dla SelectionCondition dla EntrySelectedBy dla EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md) Określa typ architektury .NET, która wyzwala warunku.

[TypeName Element dla SelectionCondition dla grupowania (w formacie)](./typename-element-for-selectioncondition-for-groupby-format.md) Określa typ architektury .NET, która wyzwala warunku. Ten element jest używany podczas definiowania sposobu wyświetlania nowej grupy obiektów.

[TypeName Element dla SelectionCondition dla EntrySelectedBy dla elementu ListControl (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md) Określa typ architektury .NET, która wyzwala warunku. Jeśli występuje ten typ wpisu listy jest używane.

[TypeName Element dla SelectionCondition dla EntrySelectedBy dla TableRowEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md) Określa typ architektury .NET, która wyzwala warunku. W przypadku tego typu jest obecny, warunek jest spełniony, i służy wiersza tabeli.

[TypeName Element dla SelectionCondition dla EntrySelectedBy dla WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md) Określa typ architektury .NET, która wyzwala warunku. Jeśli występuje ten typ definicji jest używany.

[TypeName Element dla typów (Format)](./typename-element-for-types-format.md) Określa typ architektury .NET, obiektu, który należy do zestawu zaznaczenia.

[TypeName Element dla ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md) określa obiekt .NET, który jest wyświetlany w widoku.

[Typy elementu (w formacie)](./types-element-for-selectionset-format.md) definiuje obiekty .NET, ustawionych w zaznaczeniu.

[Wyświetlanie elementu (w formacie)](./view-element-format.md) definiuje widok, który służy do wyświetlania jeden lub więcej obiektów platformy .NET.

[ViewDefinitions Element (Format)](./viewdefinitions-element-format.md) zawiera definicje widoków, używany do wyświetlania obiektów.

[ViewSelectedBy Element (Format)](./viewselectedby-element-format.md) definiuje obiekty .NET, które są wyświetlane w widoku.

[WideControl Element (Format)](./widecontrol-element-format.md) definiuje listę całej (pojedyncza wartość) format dla widoku. Ten widok przedstawia jedną właściwość wartość lub wartość skryptu dla każdego obiektu.

[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md) zawiera definicje szerokie. Szerokie, należy określić co najmniej jedną definicję.

[WideEntry Element (Format)](./wideentry-element-for-widecontrol-format.md) zawiera definicję szerokie.

[WideItem Element (Format)](./wideitem-element-for-widecontrol-format.md) definiuje właściwość lub skryptu, którego wartość jest wyświetlana.

[Szerokość elementu (w formacie)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) definiuje szerokość (w znakach) kolumny.

[OPAKOWYWANIE elementu (w formacie)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Określa, że tekst przekraczający szerokość kolumny są wyświetlane w następnym wierszu.

[WrapTables Element (Format)](./wraptables-element-format.md) Określa, czy dane w komórce tabeli jest przenoszone do następnego wiersza, jeśli danych jest dłuższa niż szerokość kolumny.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
