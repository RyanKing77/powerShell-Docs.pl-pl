---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeria, programu powershell, polecenie cmdlet, psget
title: Rozwiązywanie problemów z poleceń cmdlet
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002466"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="7fde2-103">Rozwiązywanie problemów z poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="7fde2-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="7fde2-104">Jak rozwiązać problem "Ostrzeżenie: nie można pobrać pakietu"nazwą pakietu"" problem</span><span class="sxs-lookup"><span data-stu-id="7fde2-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="7fde2-105">Zostanie zgłoszone, `Install-Module` lub `Update-Module` czasami kończy się niepowodzeniem na niektórych komputerach.</span><span class="sxs-lookup"><span data-stu-id="7fde2-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="7fde2-106">Na podstawie badania, jest coś, co można zrobić za pomocą połączenia sieci.</span><span class="sxs-lookup"><span data-stu-id="7fde2-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="7fde2-107">Ostatnio Zaktualizowaliśmy dostawcy NuGet, aby je niezawodnie umożliwia pobranie pakietów.</span><span class="sxs-lookup"><span data-stu-id="7fde2-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="7fde2-108">Możesz postępuj zgodnie z poniższymi instrukcjami, aby zainstalować najnowszą wersję programu dostawcy NuGet i następnie instalowanie lub aktualizowanie modułu.</span><span class="sxs-lookup"><span data-stu-id="7fde2-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="7fde2-109">Na przykład poniżej użyjemy modułu "Azure".</span><span class="sxs-lookup"><span data-stu-id="7fde2-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
