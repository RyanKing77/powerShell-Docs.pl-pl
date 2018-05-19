---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: dfc171f9a3471f8fe7801283dd4a9b06860781a2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="fe5d7-102">Tworzenie typów niestandardowych przy użyciu klas programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe5d7-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="fe5d7-103">Ulepszono Definiowanie klas i inne typy danych zdefiniowane przez użytkownika przy użyciu składni formalnego i semantyki są podobne do innych języków programowania zorientowany obiektowo język programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe5d7-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="fe5d7-104">Celem jest umożliwienie deweloperom i informatykom obsługę programu PowerShell dla większej liczby przypadków użycia, upraszcza programowanie artefaktów środowiska PowerShell (takich jak zasoby DSC) i przyspieszyć pokrycia powierzchni zarządzania.</span><span class="sxs-lookup"><span data-stu-id="fe5d7-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="fe5d7-105">Scenariusze obsługiwane w tej wersji</span><span class="sxs-lookup"><span data-stu-id="fe5d7-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="fe5d7-106">Zdefiniuj DSC zasobów i ich związanych z nimi typów przy użyciu języka programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe5d7-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="fe5d7-107">Definiowanie typów niestandardowych w programie PowerShell przy użyciu znanych zorientowane obiektowo narzędzi programistycznych, takich jak klasy, właściwości, metody, itp.</span><span class="sxs-lookup"><span data-stu-id="fe5d7-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="fe5d7-108">Obsługa dziedziczenia z klasy podstawowej zasobów DSC środowiska PowerShell i klasa w programie</span><span class="sxs-lookup"><span data-stu-id="fe5d7-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="fe5d7-109">Debugowanie typów przy użyciu języka programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe5d7-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="fe5d7-110">Generowanie i obsługa wyjątków za pomocą mechanizmów formalnego i na odpowiedni poziom</span><span class="sxs-lookup"><span data-stu-id="fe5d7-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
