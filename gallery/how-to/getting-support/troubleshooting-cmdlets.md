---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Rozwiązywanie problemów z poleceń cmdlet
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219831"
---
# <a name="troubleshooting-cmdlets"></a>Rozwiązywanie problemów z poleceń cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Jak rozwiązać "Ostrzeżenie: nie można pobrać pakietu"nazwę pakietu"" problem?

Został zgłoszony, że moduł instalacji lub aktualizacji modułu czasami kończy się niepowodzeniem na niektórych komputerach.
Na podstawie badania, jest związek z połączenia sieciowego.
Ostatnio Zaktualizowaliśmy NuGet dostawcy, aby niezawodnie można pobrać pakietów.
Można postępuj zgodnie z instrukcjami poniżej, aby zainstalować najnowszej kompilacji programu NuGet dostawcy, a następnie zainstaluj lub zaktualizuj modułu.
Poniższy przykład użyjmy modułu "Azure".

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```