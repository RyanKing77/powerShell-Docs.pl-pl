---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
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