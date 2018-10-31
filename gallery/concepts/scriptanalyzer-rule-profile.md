---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, programu powershell, polecenie cmdlet, galerii programu PowerShell
title: Profil zasady ScriptAnalyzer dla galerii
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002500"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="1f62d-103">Profil zasady ScriptAnalyzer dla galerii</span><span class="sxs-lookup"><span data-stu-id="1f62d-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="1f62d-104">Aby zapewnić jakość pakiety opublikowane w galerii programu PowerShell, przeprowadzamy [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) zasady w celu ustalenia, czy naruszenie w skryptach przesłane.</span><span class="sxs-lookup"><span data-stu-id="1f62d-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="1f62d-105">Można znaleźć na liście reguł, które są uruchamiane na ScriptAnalyzer [strony GitHub](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="1f62d-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="1f62d-106">Jeśli masz jakiekolwiek wątpliwości dotyczące reguły, że będziemy działają, skontaktuj się z administratorami galerii programu PowerShell, lub otworzyć zgłoszenie do ScriptAnalzyer.</span><span class="sxs-lookup"><span data-stu-id="1f62d-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="1f62d-107">ScriptAnalyzer wyniki będą wyświetlane na każdej stronie poszczególnych pakietów w galerii w nadchodzącym wydaniu.</span><span class="sxs-lookup"><span data-stu-id="1f62d-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="1f62d-108">Firma Microsoft zachęca właścicieli pakietu do sprawdzenia ich pakiety, aby upewnić się, że nie ma żadnych poważne błędy w opublikowane pakiety.</span><span class="sxs-lookup"><span data-stu-id="1f62d-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
