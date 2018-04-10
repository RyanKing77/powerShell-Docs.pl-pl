---
ms.date: 06/05/2017
keywords: polecenia cmdlet programu PowerShell
title: Podstawy programu Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-basics"></a>Podstawy programu Windows PowerShell
Graficzne interfejsy użytkownika użyj niektóre podstawowe założenia, które są powszechnie znane do większości użytkowników. Użytkownicy korzystają z znajomości tych interfejsów w celu wykonania określonych zadań. Systemy operacyjne zaprezentować użytkownikom graficzną reprezentację elementów, które można przeglądać, zazwyczaj z menu rozwijanego do uzyskiwania dostępu do określonych funkcji oraz kontekst menu do uzyskiwania dostępu do funkcji tego kontekstu.

Interfejsu wiersza polecenia (CLI), takie jak Windows PowerShell, aby należy użyć różne podejścia ujawnienie informacji, ponieważ nie ma menu lub graficznego systemów pomóc użytkownikowi. Należy znać nazwy polecenia przed ich użyciem. Mimo że można wpisać złożonych poleceń, które są równoważne funkcje w środowisku graficznym interfejsem użytkownika, użytkownik musi zapoznanie się z najczęściej używanych poleceń i parametrów polecenia.

Większość CLIs wzorców, które mogą pomóc użytkownikowi informacje interfejsu nie jest konieczne. Ponieważ CLIs pierwszy powłoki systemu operacyjnego, wiele nazw polecenia i parametru wybrano arbitralnie. Zazwyczaj wybrano nazw poleceń zwięzłym za pośrednictwem zwykłego z nich. Chociaż systemy pomocy i standardów projektu polecenia są zintegrowane z większości CLIs, zostały zazwyczaj zaprojektowane dla zgodności z najwcześniejszą poleceń, więc zestawu poleceń jest nadal w kształcie przez decyzji podjętych dekad wcześniej.

Środowisko Windows PowerShell została zaprojektowana w celu zalet historycznych znajomość CLIs użytkownika. W tym rozdziale będzie omawianiu niektóre podstawowe narzędzia i pojęcia, które umożliwiają szybkie informacje programu Windows PowerShell. Są to następujące wymagania:

- Przy użyciu [polecenia Get](/powershell/module/Microsoft.PowerShell.Core/get-command)

- Przy użyciu [Cmd.exe](/windows-server/administration/windows-commands/cmd) i [polecenia systemu UNIX](/windows/wsl/reference)

- [Przy użyciu uzupełniania po naciśnięciu tabulatora](../../core-powershell/console/using-tab-expansion.md)

- [Przy użyciu Get-Help](./getting-detailed-help-information.md)