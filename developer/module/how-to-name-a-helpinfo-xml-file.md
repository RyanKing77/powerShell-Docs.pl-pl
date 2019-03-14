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
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794811"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Jak nazwać plik XML HelpInfo

W tym temacie wyjaśniono format plików można aktualizować informacje pomocy, powszechnie znane jako pliki HelpInfo XML wymaganą nazwą.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Jak nazwać plik XML HelpInfo

Plik HelpInfo XML musi mieć nazwę w następującym formacie.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Dostępne są następujące elementy o tej nazwie.

Modulename: wartość z **nazwa** właściwość **ModuleInfo** obiekt [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) polecenie cmdlet zwraca.

ModuleGUID wartość z **GUID** klucza w manifeście modułu.

Na przykład jeśli moduł identyfikator GUID jest 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 Nazwa modułu jest "TestModule", nazwa pliku HelpInfo XML modułu będzie:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`