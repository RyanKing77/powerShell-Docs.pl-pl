---
title: Element DisplayError (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066264"
---
# <a name="displayerror-element-format"></a>DisplayError, element (format)

Określa, czy ciąg #ERR są wyświetlane, gdy wystąpi błąd wyświetlania elementu danych.

Element DisplayError DefaultSettings — Element (w formacie) — Element (w formacie) konfiguracji (Format)

## <a name="syntax"></a>Składnia

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `DisplayError` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element DefaultSettings (Format)](./defaultsettings-element-format.md)|Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.|

## <a name="remarks"></a>Uwagi

Domyślnie gdy wystąpi błąd podczas próby wyświetlenia elementu danych, lokalizacja danych jest puste. Gdy ten element jest ustawiony na wartość true, ciąg #ERR będą wyświetlane.

## <a name="see-also"></a>Zobacz też

[Element DefaultSettings (Format)](./defaultsettings-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
