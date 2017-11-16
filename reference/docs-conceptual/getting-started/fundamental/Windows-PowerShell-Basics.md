---
ms.date: 2017-06-05
keywords: polecenia cmdlet programu PowerShell
title: "Windows PowerShell — podstawy"
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: 7b5cdfce876aa7d5559fe772379829011b275a02
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="a77e8-103">Windows PowerShell — podstawy</span><span class="sxs-lookup"><span data-stu-id="a77e8-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="a77e8-104">Graficzne interfejsy użytkownika użyj niektóre podstawowe założenia, które są powszechnie znane do większości użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a77e8-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="a77e8-105">Użytkownicy korzystają z znajomości tych interfejsów w celu wykonania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="a77e8-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="a77e8-106">Systemy operacyjne zaprezentować użytkownikom graficzną reprezentację elementów, które można przeglądać, zazwyczaj z menu rozwijanego do uzyskiwania dostępu do określonych funkcji oraz kontekst menu do uzyskiwania dostępu do funkcji tego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a77e8-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="a77e8-107">Interfejsu wiersza polecenia (CLI), takie jak Windows PowerShell, aby należy użyć różne podejścia ujawnienie informacji, ponieważ nie ma menu lub graficznego systemów pomóc użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="a77e8-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="a77e8-108">Należy znać nazwy polecenia przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="a77e8-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="a77e8-109">Mimo że można wpisać złożonych poleceń, które są równoważne funkcje w środowisku graficznym interfejsem użytkownika, użytkownik musi zapoznanie się z najczęściej używanych poleceń i parametrów polecenia.</span><span class="sxs-lookup"><span data-stu-id="a77e8-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="a77e8-110">Większość CLIs wzorców, które mogą pomóc użytkownikowi informacje interfejsu nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="a77e8-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="a77e8-111">Ponieważ CLIs pierwszy powłoki systemu operacyjnego, wiele nazw polecenia i parametru wybrano arbitralnie.</span><span class="sxs-lookup"><span data-stu-id="a77e8-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="a77e8-112">Zazwyczaj wybrano nazw poleceń zwięzłym za pośrednictwem zwykłego z nich.</span><span class="sxs-lookup"><span data-stu-id="a77e8-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="a77e8-113">Chociaż systemy pomocy i standardów projektu polecenia są zintegrowane z większości CLIs, zostały zazwyczaj zaprojektowane dla zgodności z najwcześniejszą poleceń, więc zestawu poleceń jest nadal w kształcie przez decyzji podjętych dekad wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a77e8-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="a77e8-114">Środowisko Windows PowerShell została zaprojektowana w celu zalet historycznych znajomość CLIs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a77e8-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="a77e8-115">W tym rozdziale będzie omawianiu niektóre podstawowe narzędzia i pojęcia, które umożliwiają szybkie informacje programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a77e8-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="a77e8-116">Są to następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="a77e8-116">They include:</span></span>

- <span data-ttu-id="a77e8-117">Za pomocą polecenia Get</span><span class="sxs-lookup"><span data-stu-id="a77e8-117">Using Get-Command</span></span>

- <span data-ttu-id="a77e8-118">Za pomocą poleceń Cmd.exe i UNIX</span><span class="sxs-lookup"><span data-stu-id="a77e8-118">Using Cmd.exe and UNIX commands</span></span>

- <span data-ttu-id="a77e8-119">Za pomocą poleceń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="a77e8-119">Using External Commands</span></span>

- <span data-ttu-id="a77e8-120">Przy użyciu uzupełniania po naciśnięciu tabulatora</span><span class="sxs-lookup"><span data-stu-id="a77e8-120">Using Tab-Completion</span></span>

- <span data-ttu-id="a77e8-121">Przy użyciu Get-Help</span><span class="sxs-lookup"><span data-stu-id="a77e8-121">Using Get-Help</span></span>

