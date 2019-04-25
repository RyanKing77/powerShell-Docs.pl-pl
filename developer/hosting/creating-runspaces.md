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
# <a name="creating-runspaces"></a>Tworzenie obszarów działania

W obszarze działania jest środowisko operacyjne dla poleceń, które są wywoływane przez aplikację hosta. To środowisko zawiera polecenia i dane, które są aktualnie dostępne i wszelkie ograniczenia języka, które są obecnie stosowane.

 Hostowanie aplikacji można użyć obszaru działania domyślne, dostarczone przez programu Windows PowerShell, co obejmuje wszystkich poleceń dostępnych rdzeni, lub utworzyć niestandardowe obszar działania, który zawiera tylko podzbiór dostępnych poleceń. Aby utworzyć dostosowanego obszaru działania, należy utworzyć [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) obiektu i przypisz go do Twojego obszaru działania.

## <a name="runspace-tasks"></a>Zadania w obszarze działania

1. [Tworzenie InitialSessionState](./creating-an-initialsessionstate.md)

2. [Tworzenie ograniczonego obszaru działania](./creating-a-constrained-runspace.md)

3. [Tworzenie wielu obszarach działania](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Zobacz też
