---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeria, programu powershell, polecenia cmdlet, psget
title: Rozwiązywanie problemów z poleceń cmdlet
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="af76e-103">Rozwiązywanie problemów z poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="af76e-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="af76e-104">Jak rozwiązać "Ostrzeżenie: nie można pobrać pakietu"nazwę pakietu"" problem?</span><span class="sxs-lookup"><span data-stu-id="af76e-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="af76e-105">Został zgłoszony, że moduł instalacji lub aktualizacji modułu czasami kończy się niepowodzeniem na niektórych komputerach.</span><span class="sxs-lookup"><span data-stu-id="af76e-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="af76e-106">Na podstawie badania, jest związek z połączenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="af76e-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="af76e-107">Ostatnio Zaktualizowaliśmy NuGet dostawcy, aby niezawodnie można pobrać pakietów.</span><span class="sxs-lookup"><span data-stu-id="af76e-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="af76e-108">Można postępuj zgodnie z instrukcjami poniżej, aby zainstalować najnowszej kompilacji programu NuGet dostawcy, a następnie zainstaluj lub zaktualizuj modułu.</span><span class="sxs-lookup"><span data-stu-id="af76e-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="af76e-109">Poniższy przykład użyjmy modułu "Azure".</span><span class="sxs-lookup"><span data-stu-id="af76e-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```