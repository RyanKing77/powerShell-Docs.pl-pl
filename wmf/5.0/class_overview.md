---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686446"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="66fb4-102">Tworzenie typów niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="66fb4-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="66fb4-103">Ulepszyliśmy języka PowerShell do definiowania klas i innych typów zdefiniowanych przez użytkownika za pomocą formalne składnia i semantyka, które są podobne do innych języków programowania obiektowego.</span><span class="sxs-lookup"><span data-stu-id="66fb4-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="66fb4-104">Celem jest umożliwienie deweloperom i informatykom przyjęcie programu PowerShell dla szerszego zakresu zastosowań, upraszczają proces tworzenia artefaktów programu PowerShell (takich jak zasoby DSC) oraz skrócenia procesu pokrycia powierzchni zarządzania.</span><span class="sxs-lookup"><span data-stu-id="66fb4-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="66fb4-105">Scenariusze obsługiwane w tej wersji</span><span class="sxs-lookup"><span data-stu-id="66fb4-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="66fb4-106">Zdefiniuj zasoby DSC i ich skojarzone typy przy użyciu języka programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="66fb4-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="66fb4-107">Definiowanie typów niestandardowych w programie PowerShell, za pomocą dobrze znanych zorientowane obiektowo narzędzi programistycznych, takich jak klasy, właściwości, metod itd.</span><span class="sxs-lookup"><span data-stu-id="66fb4-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="66fb4-108">Obsługa dziedziczenia z klasy w podstawowej zasobów DSC programu PowerShell i klasy</span><span class="sxs-lookup"><span data-stu-id="66fb4-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="66fb4-109">Debugowanie typów przy użyciu języka programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="66fb4-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="66fb4-110">Generowanie i obsługa wyjątków za pomocą mechanizmów formalne i na właściwym poziomie</span><span class="sxs-lookup"><span data-stu-id="66fb4-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
