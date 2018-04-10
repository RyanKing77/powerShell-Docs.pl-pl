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
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="1782a-103">Jak rozwiązać "Ostrzeżenie: nie można pobrać pakietu"nazwę pakietu"" problem?</span><span class="sxs-lookup"><span data-stu-id="1782a-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="1782a-104">Został zgłoszony, że moduł instalacji lub aktualizacji modułu czasami kończy się niepowodzeniem na niektórych komputerach.</span><span class="sxs-lookup"><span data-stu-id="1782a-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="1782a-105">Na podstawie badania, jest związek z połączenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="1782a-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="1782a-106">Ostatnio Zaktualizowaliśmy NuGet dostawcy, aby niezawodnie można pobrać pakietów.</span><span class="sxs-lookup"><span data-stu-id="1782a-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="1782a-107">Można postępuj zgodnie z instrukcjami poniżej, aby zainstalować najnowszej kompilacji programu NuGet dostawcy, a następnie zainstaluj lub zaktualizuj modułu.</span><span class="sxs-lookup"><span data-stu-id="1782a-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="1782a-108">Poniższy przykład użyjmy modułu "Azure".</span><span class="sxs-lookup"><span data-stu-id="1782a-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```