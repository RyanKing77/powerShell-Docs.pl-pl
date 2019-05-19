---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Ulepszenia aparatu programu PowerShell w programie WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856182"
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

> [!NOTE]
> Jednej zmiany związane z uruchamiania mogą mieć wpływ na niektóre scenariusze nieobsługiwane. Program PowerShell nie jest już odczytuje pliki `$pshome\*.ps1xml` — te pliki zostały przekonwertowane na C# uniknąć niektórych plików i obciążenie Procesora przetwarzania plików XML. Pliki nadal istnieje do działu pomocy technicznej w wersji 2 side-by-side, więc w przypadku zmiany zawartość pliku nie będzie miała wpływu na V5, tylko w wersji 2. Należy zauważyć, że zmiany zawartości tych plików, nigdy nie było to obsługiwany scenariusz.

Inna zmiana widoczne polega na tym, jak program PowerShell buforuje wyeksportowanego polecenia i inne informacje dla modułów, które są zainstalowane w systemie. Wcześniej ta pamięć podręczna została zapisana w katalogu `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. W program WMF 5.1 pamięć podręczna to pojedynczy plik `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Zobacz [moduł analizy w pamięci podręcznej](release-notes.md#module-analysis-cache) Aby uzyskać więcej informacji.