---
title: Aliasy polecenia cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849966"
---
# <a name="cmdlet-aliases"></a>Aliasy poleceń cmdlet

Aliasy polecenia cmdlet można użyć, aby ulepszyć środowisko użytkownika polecenia cmdlet. Można dodawać aliasów do często używanych poleceń cmdlet, aby zmniejszyć, wpisując i ułatwiają wykonywanie zadań szybko. Może zawierać aliasy wbudowanych poleceń cmdlet lub użytkownicy mogą definiować własnych niestandardowych aliasów.

Na przykład [Get-Command](/powershell/module/microsoft.powershell.core/get-command) polecenie cmdlet ma wbudowaną `gcm` aliasu. Aliasy umożliwia również dodać nazwy poleceń w innych językach, tak, aby użytkownicy nie mają się nowych poleceń.

## <a name="alias-guidelines"></a>Wytyczne dotyczące aliasu

Podczas tworzenia aliasów wbudowanych poleceń cmdlet, należy przestrzegać następujących wytycznych:

- Przed przypisaniem aliasy, uruchom program Windows PowerShell, a następnie uruchom [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) polecenia cmdlet, aby wyświetlić aliasy, które są już używane.

- Dołącz prefiks alias, który odwołuje się polecenie Nazwa polecenia cmdlet i sufiks alias, który odwołuje się do rzeczownikiem nazwa polecenia cmdlet. Na przykład alias `Import-Module` polecenie cmdlet jest "ipmo". Aby uzyskać listę wszystkich poleceń i ich aliasy, zobacz [czasowników poleceń Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- W przypadku poleceń cmdlet, które mają ten sam zlecenie zawiera ten sam prefiks aliasu. Na przykład aliasów dla wszystkich Windows poleceń cmdlet programu PowerShell zawierających zlecenie "Get" w nazwie używać prefiksu "g".

- Dla poleceń cmdlet, które mają ten sam rzeczownik zawiera ten sam sufiksu aliasu. Na przykład aliasów dla wszystkich programu Windows PowerShell polecenia cmdlet które mają rzeczownik "Sesja" w nazwie Użyj sufiksu "sn".

- Dla poleceń cmdlet, które są równoważne poleceń w innych językach Użyj nazwy polecenia.

- Ogólnie rzecz biorąc należy możliwie krótkie aliasów. Upewnij się, że alias ma co najmniej jeden znak distinct dla zlecenia i jeden znak distinct dla rzeczownikiem. Dodawanie większej liczby znaków, zgodnie z potrzebami unikatowość alias.

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
