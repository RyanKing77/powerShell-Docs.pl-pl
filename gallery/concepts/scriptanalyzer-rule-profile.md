---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Profil zasady ScriptAnalyzer dla galerii
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002500"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>Profil zasady ScriptAnalyzer dla galerii

Aby zapewnić jakość pakiety opublikowane w galerii programu PowerShell, przeprowadzamy [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) zasady w celu ustalenia, czy naruszenie w skryptach przesłane.

Można znaleźć na liście reguł, które są uruchamiane na ScriptAnalyzer [strony GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Jeśli masz jakiekolwiek wątpliwości dotyczące reguły, że będziemy działają, skontaktuj się z administratorami galerii programu PowerShell, lub otworzyć zgłoszenie do ScriptAnalzyer.

ScriptAnalyzer wyniki będą wyświetlane na każdej stronie poszczególnych pakietów w galerii w nadchodzącym wydaniu. Firma Microsoft zachęca właścicieli pakietu do sprawdzenia ich pakiety, aby upewnić się, że nie ma żadnych poważne błędy w opublikowane pakiety.
