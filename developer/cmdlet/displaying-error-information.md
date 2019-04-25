---
title: Wyświetlanie informacji o błędach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068287"
---
# <a name="displaying-error-information"></a>Wyświetlanie informacji o błędach

W tym temacie omówiono sposoby, w którym użytkownicy mogą wyświetlać informacje o błędzie.

Gdy Twojego polecenia cmdlet napotka błąd, prezentacja informacji o błędach będą domyślnie przypominają następujące dane wyjściowe błędu.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Jednak użytkownicy mogą wyświetlać błędy według kategorii, ustawiając `$ErrorView` zmienną `"CategoryView"`. W widoku kategorii wyświetlane szczegółowe informacje z rekordu błędu zamiast niezależnego opisu błędu. Ten widok może być przydatne, jeśli masz długą listę błędów do skanowania. W widoku kategorii poprzedniego komunikat o błędzie jest wyświetlany w następujący sposób.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Aby uzyskać więcej informacji na temat kategorii błędów, zobacz [rekordów błędów programu Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Zobacz też

[Windows PowerShell błąd rekordów](./windows-powershell-error-records.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
