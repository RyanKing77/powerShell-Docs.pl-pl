---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Rozwiązywanie problemów z poleceń cmdlet
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
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