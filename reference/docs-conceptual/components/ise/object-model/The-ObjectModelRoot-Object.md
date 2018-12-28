---
ms.date: 08/25/2017
keywords: polecenia cmdlet programu PowerShell
title: Obiekt ObjectModelRoot
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405586"
---
# <a name="the-objectmodelroot-object"></a>Obiekt ObjectModelRoot

**$PsISE** obiektu, który jest obiektem głównym jednostki w Windows PowerShell® zintegrowane Scripting Environment (ISE) jest wystąpieniem klasy Microsoft.PowerShell.Host.ISE.ObjectModelRoot.
W tym temacie opisano właściwości obiektu **ObjectModelRoot** obiektu.

## <a name="properties"></a>Właściwości

### <a name="currentfile"></a>CurrentFile

> Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która umożliwia pobieranie pliku, który jest skojarzony z tym obiektem hosta, który aktualnie ma fokus.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która kartę programu PowerShell, który ma fokus.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera aktualnie widoczne narzędzia Windows PowerShell ISE w dodatku, który znajduje się w okienku narzędzie poziomy w dolnej części edytora.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera aktualnie widoczne narzędzia Windows PowerShell ISE w dodatku, który znajduje się w okienku pionowy narzędzi po prawej stronie edytora.

### <a name="options"></a>Opcje

> Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która pobiera różne opcje, które można zmienić ustawienia w środowisku Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Obsługiwane w programie Windows PowerShell ISE 2.0 i nowszych.

Właściwość tylko do odczytu, która kolekcji kart programu PowerShell, które są otwarte w środowisku Windows PowerShell ISE. Domyślnie ten obiekt zawiera jedną kartę programu PowerShell. Można jednak dodać więcej kart programu PowerShell do tego obiektu, za pomocą skryptów lub przy użyciu menu w środowisku Windows PowerShell ISE.

## <a name="see-also"></a>Zobacz też

- [Cel modelu obiektów skryptowych środowiska Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarchia modeli obiektów środowiska ISE](The-ISE-Object-Model-Hierarchy.md)