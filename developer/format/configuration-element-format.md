---
title: Element konfiguracji (Format) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847040"
---
# <a name="configuration-element-format"></a>Configuration, element (format)

Reprezentuje element najwyższego poziomu w pliku formatowania.

Element konfiguracji

## <a name="syntax"></a>Składnia

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i element nadrzędny `Configuration` elementu. Ten element musi być elementem głównym dla każdego pliku formatowania, a ten element musi zawierać co najmniej jeden element podrzędny.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Kontrolki elementu konfiguracji (Format)](./controls-element-for-configuration-format.md)|Element opcjonalny.<br /><br /> Definiuje typowe formanty, które mogą być używane przez wszystkie widoki formatowania pliku.|
|[Element DefaultSettings (Format)](./defaultsettings-element-format.md)|Element opcjonalny.<br /><br /> Definiuje typowe ustawienia, które są stosowane do wszystkich widoków formatowania pliku.|
|[Format elementu SelectionSets](./selectionsets-element-format.md)|Element opcjonalny.<br /><br /> Definiuje typowe rodzaje obiektów platformy .NET, które mogą być używane przez wszystkie widoki formatowania pliku.|
|[Element ViewDefinitions (Format)](./viewdefinitions-element-format.md)|Element opcjonalny.<br /><br /> Zawiera definicje widoków, używany do wyświetlania obiektów.|

### <a name="parent-elements"></a>Elementy nadrzędne

Brak.

## <a name="remarks"></a>Uwagi

Pliki formatowania zdefiniować sposób wyświetlania obiektów. W większości przypadków zawiera ten element główny [ViewDefinitions](./viewdefinitions-element-format.md) element, który definiuje tabel, list i szeroki widoków formatowania pliku. Oprócz definicji widoku formatowania pliku można zdefiniować wspólne zestawów zaznaczenia, ustawienia i kontrolki używające tych widoków.

## <a name="see-also"></a>Zobacz też

[Kontrolki elementu konfiguracji (Format)](./controls-element-for-configuration-format.md)

[Element DefaultSettings (Format)](./defaultsettings-element-format.md)

[Element SelectionSets (Format)](./selectionsets-element-format.md)

[Element ViewDefinitions (Format)](./viewdefinitions-element-format.md)

[Pisanie programu PowerShell, formatowanie pliku](./writing-a-powershell-formatting-file.md)
