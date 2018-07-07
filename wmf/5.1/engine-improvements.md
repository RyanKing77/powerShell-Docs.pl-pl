---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia aparatu programu PowerShell w programie WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892896"
---
# <a name="powershell-engine-improvements"></a>Ulepszenia aparatu programu PowerShell

Następujące ulepszenia w aparacie programu PowerShell core zostały wdrożone w WMF 5.1:

## <a name="performance"></a>Wydajność

Wydajność poprawiła się w niektórych obszarach ważne:

- Uruchamianie
- Przetwarzanie potokowe poleceń cmdlet, takich jak `ForEach-Object` i `Where-Object` wynosi około 50% szybsza

Ulepszenia przykład (Twoje wyniki mogą się różnić w zależności od sprzętu):

| Scenariusz | W wersji 5.0, czas (ms) | 5.1 czas (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Pierwszy kiedykolwiek uruchamiania środowiska PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Analiza pamięci podręcznej poleceń wbudowane: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!Note]
> Jednej zmiany związane z uruchamiania mogą mieć wpływ na niektóre scenariusze nieobsługiwane.
> Program PowerShell nie jest już odczytuje pliki `$pshome\*.ps1xml` — te pliki zostały przekonwertowane na C#, aby uniknąć niektórych plików i obciążenie procesora CPU przetwarzania XML plików.
> Pliki nadal istnieje do działu pomocy technicznej w wersji 2 side-by-side, więc w przypadku zmiany zawartość pliku nie będzie miała wpływu na V5, tylko w wersji 2.
> Należy zauważyć, że zmiany zawartości tych plików, nigdy nie było to obsługiwany scenariusz.

Inna zmiana widoczne polega na tym, jak program PowerShell buforuje wyeksportowanego polecenia i inne informacje dla modułów, które są zainstalowane w systemie.
Wcześniej ta pamięć podręczna została zapisana w katalogu `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
W program WMF 5.1 pamięć podręczna to pojedynczy plik `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Zobacz [moduł analizy w pamięci podręcznej](scenarios-features.md#module-analysis-cache) Aby uzyskać więcej informacji.