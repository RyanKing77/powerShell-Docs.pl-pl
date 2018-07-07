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
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="188c1-103">Rozwiązywanie problemów z poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="188c1-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="188c1-104">Jak rozwiązać problem "Ostrzeżenie: nie można pobrać pakietu"nazwą pakietu"" problem</span><span class="sxs-lookup"><span data-stu-id="188c1-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="188c1-105">Zostanie zgłoszone, `Install-Module` lub `Update-Module` czasami kończy się niepowodzeniem na niektórych komputerach.</span><span class="sxs-lookup"><span data-stu-id="188c1-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="188c1-106">Na podstawie badania, jest coś, co można zrobić za pomocą połączenia sieci.</span><span class="sxs-lookup"><span data-stu-id="188c1-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="188c1-107">Ostatnio Zaktualizowaliśmy dostawcy NuGet, aby je niezawodnie umożliwia pobranie pakietów.</span><span class="sxs-lookup"><span data-stu-id="188c1-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="188c1-108">Możesz postępuj zgodnie z poniższymi instrukcjami, aby zainstalować najnowszą wersję programu dostawcy NuGet i następnie instalowanie lub aktualizowanie modułu.</span><span class="sxs-lookup"><span data-stu-id="188c1-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="188c1-109">Na przykład poniżej użyjemy modułu "Azure".</span><span class="sxs-lookup"><span data-stu-id="188c1-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```