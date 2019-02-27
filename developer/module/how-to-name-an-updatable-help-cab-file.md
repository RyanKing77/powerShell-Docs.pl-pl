---
title: Jak nazwać plik CAB aktualizowalnej pomocy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850512"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Jak nazwać plik CAB aktualizowalnej pomocy

W tym temacie opisano wymaganą nazwą format pliku cabinet aktualizowalnej pomocy (. Pliki CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Jak nazwać plik CAB aktualizowalnej pomocy

Można zaktualizować pliku cabinet (. Plik CAB) musi mieć nazwę w następującym formacie.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Dostępne są następujące elementy o tej nazwie.

Modulename: wartość z **nazwa** właściwość **ModuleInfo** obiekt [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet zwraca.
Wartość **nazwa** właściwość **ModuleInfo** obiekt [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet zwraca.

ModuleGUID wartość z **GUID** klucza w manifeście modułu.

Kultura interfejsu użytkownika UICulture pliki pomocy w pliku CAB. Ta wartość musi odpowiadać wartości jednego z **UICulture** elementy w pliku HelpInfo XML dla modułu.

Na przykład jeśli nazwa modułu jest "TestModule", moduł identyfikator GUID jest 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 i kultura interfejsu użytkownika jest "en US", nazwa pliku CAB:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`