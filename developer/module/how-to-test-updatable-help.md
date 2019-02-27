---
title: Jak przetestować aktualizowalnej pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845927"
---
# <a name="how-to-test-updatable-help"></a>Jak przetestować aktualizowalną pomoc

W tym temacie opisano sposoby testowania aktualizowalnej pomocy dla modułu.

## <a name="using-verbose-to-detect-errors"></a>Za pomocą Verbose, aby wykrywać błędy

Po przekazaniu pliku HelpInfo XML i pliki CAB dla modułu, testować, uruchamiając [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia **pełne** parametru. **Pełne** kieruje parametr `Update-Help` zgłosić krytycznych czynności opisane w jego operacje odczytu **HelpInfoUri** klucza w manifeście modułu weryfikowania typów plików w pliku CAB nierozpakowane i umieszczanie plików w katalogu modułu specyficzny dla języka.
Po przekazaniu pliku HelpInfo XML i pliki CAB dla modułu, testować, uruchamiając [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) polecenia **pełne** parametru. **Pełne** kieruje parametr `Update-Help` zgłosić krytycznych czynności opisane w jego operacje odczytu **HelpInfoUri** klucza w manifeście modułu weryfikowania typów plików w pliku CAB nierozpakowane i umieszczanie plików w katalogu modułu specyficzny dla języka.

Gdy wszystkie komunikaty pełne są rozwiązywane, uruchom `Update-Help` polecenia **debugowania** parametru. Ten parametr powinien wykryć wszystkie pozostałe problemy z plików aktualizowalnej pomocy.