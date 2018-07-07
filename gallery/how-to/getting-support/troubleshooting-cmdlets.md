---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Rozwiązywanie problemów z poleceń cmdlet
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892478"
---
# <a name="troubleshooting-cmdlets"></a>Rozwiązywanie problemów z poleceń cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Jak rozwiązać problem "Ostrzeżenie: nie można pobrać pakietu"nazwą pakietu"" problem

Zostanie zgłoszone, `Install-Module` lub `Update-Module` czasami kończy się niepowodzeniem na niektórych komputerach.
Na podstawie badania, jest coś, co można zrobić za pomocą połączenia sieci.
Ostatnio Zaktualizowaliśmy dostawcy NuGet, aby je niezawodnie umożliwia pobranie pakietów.
Możesz postępuj zgodnie z poniższymi instrukcjami, aby zainstalować najnowszą wersję programu dostawcy NuGet i następnie instalowanie lub aktualizowanie modułu.
Na przykład poniżej użyjemy modułu "Azure".

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```