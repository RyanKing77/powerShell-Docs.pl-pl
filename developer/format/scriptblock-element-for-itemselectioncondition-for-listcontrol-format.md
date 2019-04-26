---
title: Element ScriptBlock ItemSelectionCondition dla elementu ListControl (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064411"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock, element — ItemSelectionCondition, ListControl (format)

Określa skrypt, który wyzwala warunku. Gdy ten skrypt jest oceniany w celu `true`, warunek jest spełniony, i jest używany w elemencie listy. Ten element jest używany podczas definiowania widoku listy.

— Element (w formacie) elementu ViewDefinitions (Format) widoku elementu (w formacie) elementu ListControl — Element (Format) ListEntries Element konfiguracji elementu ListControl (Format) elementu ListEntry ListEntries elementu ListControl (Format) elementu ListItems ListEntry dla elementu ListControl (Format) elementu ListItem ListItems listy kontroli (Format) ItemSelectionCondition elementu ListItem elementu ListControl (Format) elementu ScriptBlock ItemSelectionCondition dla elementu ListControl (Format)

## <a name="syntax"></a>Składnia

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne `ScriptBlock` elementu.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element ItemSelectionCondition dla elementu listy dla elementu ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Określa warunek, który musi istnieć przez ten element listy do użycia.|

## <a name="text-value"></a>Wartość tekstowa

Określ skrypt, który jest oceniany.

## <a name="remarks"></a>Uwagi

Jeśli ten element jest używany, nie można określić `PropertyName` elementu podczas definiowania warunek wyboru.

## <a name="see-also"></a>Zobacz też

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
