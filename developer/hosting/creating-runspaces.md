---
title: Tworzenie obszary działania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082944"
---
# <a name="creating-runspaces"></a><span data-ttu-id="4a8dc-102">Tworzenie obszarów działania</span><span class="sxs-lookup"><span data-stu-id="4a8dc-102">Creating Runspaces</span></span>

<span data-ttu-id="4a8dc-103">W obszarze działania jest środowisko operacyjne dla poleceń, które są wywoływane przez aplikację hosta.</span><span class="sxs-lookup"><span data-stu-id="4a8dc-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="4a8dc-104">To środowisko zawiera polecenia i dane, które są aktualnie dostępne i wszelkie ograniczenia języka, które są obecnie stosowane.</span><span class="sxs-lookup"><span data-stu-id="4a8dc-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="4a8dc-105">Hostowanie aplikacji można użyć obszaru działania domyślne, dostarczone przez programu Windows PowerShell, co obejmuje wszystkich poleceń dostępnych rdzeni, lub utworzyć niestandardowe obszar działania, który zawiera tylko podzbiór dostępnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="4a8dc-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="4a8dc-106">Aby utworzyć dostosowanego obszaru działania, należy utworzyć [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiektu i przypisz go do Twojego obszaru działania.</span><span class="sxs-lookup"><span data-stu-id="4a8dc-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="4a8dc-107">Zadania w obszarze działania</span><span class="sxs-lookup"><span data-stu-id="4a8dc-107">Runspace tasks</span></span>

1. [<span data-ttu-id="4a8dc-108">Tworzenie InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="4a8dc-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="4a8dc-109">Tworzenie ograniczonego obszaru działania</span><span class="sxs-lookup"><span data-stu-id="4a8dc-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="4a8dc-110">Tworzenie wielu obszarach działania</span><span class="sxs-lookup"><span data-stu-id="4a8dc-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="4a8dc-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a8dc-111">See Also</span></span>
