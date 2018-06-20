---
ms.date: 08/25/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954606"
---
# <a name="the-objectmodelroot-object"></a>Obiekt ObjectModelRoot

**$PsISE** obiektu, który jest obiektem głównym podmiotu zabezpieczeń w systemie Windows PowerShell® Integrated Scripting Environment (ISE) jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
W tym temacie opisano właściwości **ObjectModelRoot** obiektu.

## <a name="properties"></a>Właściwości

### <a name="currentfile"></a>CurrentFile

> Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera plik, który jest skojarzony z tym obiektem hosta, który aktualnie ma fokus.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która karta programu PowerShell, który ma fokus.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera widoczne narzędzia dodatek programu Windows PowerShell ISE, który znajduje się w okienku narzędzie poziomy w dolnej części edytora.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera widoczne narzędzia dodatek programu Windows PowerShell ISE, który znajduje się w okienku narzędzie pionowy po prawej stronie edytora.

### <a name="options"></a>Opcje

> Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera różne opcje, które można zmienić ustawienia w środowisku Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Obsługiwane w programie Windows PowerShell ISE 2.0 lub nowszy.

Właściwość tylko do odczytu, która pobiera kolekcję kart środowiska PowerShell, które są otwarte w środowisku Windows PowerShell ISE. Domyślnie ten obiekt zawiera jedną kartę programu PowerShell. Można jednak dodać więcej kart programu PowerShell do tego obiektu, za pomocą skryptów lub za pomocą menu w środowisku Windows PowerShell ISE.

## <a name="see-also"></a>Zobacz też

- [Cel programu Windows PowerShell ISE skryptów modelu obiektów](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)