---
title: Element DefaultSettings (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066349"
---
# <a name="defaultsettings-element-format"></a>DefaultSettings, element (format)

Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku. Typowe ustawienia obejmują wyświetlanie błędów, zawijania tekstu w tabelach, określające, jak kolekcje są rozwinięte i więcej.

Element DefaultSettings (Format) — Element konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `DefaultSettings` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element DisplayError (Format)](./displayerror-element-format.md)|Element opcjonalny.<br /><br /> Określa, czy ciąg #ERR są wyświetlane, gdy wystąpi błąd podczas wyświetlania elementu danych.|
|[Element EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)|Element opcjonalny.<br /><br /> Definiuje różne sposoby, które .NET obiekty zostaną rozwinięte, gdy są one wyświetlane w widoku.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Element opcjonalny.<br /><br /> Określa minimalną liczbę właściwości, które musi zawierać obiekt, aby wyświetlić obiekt w widoku tabeli.|
|[Element ShowError (Format)](./showerror-element-format.md)|Element opcjonalny.<br /><br /> Określa, czy rekord pełny komunikat o błędzie jest wyświetlany, gdy wystąpi błąd podczas wyświetlania elementu danych.|
|[Element WrapTables (Format)](./wraptables-element-format.md)|Element opcjonalny.<br /><br /> Określa, że dane w tabeli jest przenoszony do następnego wiersza, jeśli nie mieści się na szerokość kolumny.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element konfiguracji](./configuration-element-format.md)|Reprezentuje element najwyższego poziomu w pliku formatowania.|

## <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Element konfiguracji](./configuration-element-format.md)

[Element DisplayError (Format)](./displayerror-element-format.md)

[Element EnumerableExpansions (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[Element ShowError (Format)](./showerror-element-format.md)

[Element WrapTables (Format)](./wraptables-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
