---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Profil zasady ScriptAnalyzer dla galerii
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084593"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Profil zasady ScriptAnalyzer dla galerii

Aby zapewnić jakość pakiety opublikowane w galerii programu PowerShell, przeprowadzamy [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) zasady w celu ustalenia, czy naruszenie w skryptach przesłane.

Można znaleźć na liście reguł, które są uruchamiane na ScriptAnalyzer [strony GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Jeśli masz jakiekolwiek wątpliwości dotyczące reguły, że będziemy działają, skontaktuj się z administratorami galerii programu PowerShell, lub otworzyć zgłoszenie do ScriptAnalyzer.

ScriptAnalyzer wyniki będą wyświetlane na każdej stronie poszczególnych pakietów w galerii w nadchodzącym wydaniu. Firma Microsoft zachęca właścicieli pakietu do sprawdzenia ich pakiety, aby upewnić się, że nie ma żadnych poważne błędy w opublikowane pakiety.
