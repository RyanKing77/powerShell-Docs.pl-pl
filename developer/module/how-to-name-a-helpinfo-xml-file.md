---
title: Jak nazwać plik HelpInfo XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848090"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Jak nazwać plik XML HelpInfo

W tym temacie wyjaśniono format plików można aktualizować informacje pomocy, powszechnie znane jako pliki HelpInfo XML wymaganą nazwą.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Jak nazwać plik XML HelpInfo

Plik HelpInfo XML musi mieć nazwę w następującym formacie.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Dostępne są następujące elementy o tej nazwie.

Modulename: wartość z **nazwa** właściwość **ModuleInfo** obiekt [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet zwraca.
Wartość **nazwa** właściwość **ModuleInfo** obiekt [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet zwraca.

ModuleGUID wartość z **GUID** klucza w manifeście modułu.

Na przykład jeśli moduł identyfikator GUID jest 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 Nazwa modułu jest "TestModule", nazwa pliku HelpInfo XML modułu będzie:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`