---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Ulepszenia dotyczące aparatu programu PowerShell w programie WMF 5.1
ms.openlocfilehash: 3c69c4e13f64683f743eb78b0c9e177ff5b3a771
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
#<a name="powershell-engine-improvements"></a>Ulepszenia aparatu programu PowerShell

Wprowadzono następujące ulepszenia podstawowym aparatem programu PowerShell są zaimplementowane w wersji 5.1 WMF:


## <a name="performance"></a>Wydajność ##

Wydajność poprawiła w pewne ważne kwestie:

- Uruchamianie
- Przetwarzanie potokowe do poleceń cmdlet, takich jak ForEach-Object i Where-Object to około 50% szybsza

Niektóre ulepszenia przykład (wyniki mogą się różnić w zależności od sprzętu):

| Scenariusz | 5.0 czas (ms) | 5.1 czas (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Pierwszy kiedykolwiek uruchamiania programu PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Wbudowane buforu analizy polecenia: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> Należy pamiętać, że jeden zmiany dotyczące uruchamiania może mieć wpływ na niektóre nieobsługiwanych scenariuszy.
> PowerShell już odczytuje pliki `$pshome\*.ps1xml` — tych plików został przekonwertowany na C#, aby uniknąć niektórych plików i obciążenie procesora CPU przetwarzania XML pliki.
Pliki nadal istnieją obsługi V2 side-by-side, więc jeśli zmienisz zawartość pliku nie będzie miała wpływu na V5, tylko w wersji 2.
Należy pamiętać, że zmiany tych plików zawartości nigdy nie był obsługiwany scenariusz.

Inna zmiana widoczny jest sposób PowerShell buforuje wyeksportowany polecenia i inne informacje dla modułów, które są zainstalowane w systemie.
Wcześniej ta pamięć podręczna była przechowywana w katalogu `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
W wersji 5.1 WMF, pamięć podręczna jest pojedynczy plik `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Zobacz [moduł analizy w pamięci podręcznej](scenarios-features.md#module-analysis-cache) więcej szczegółów.