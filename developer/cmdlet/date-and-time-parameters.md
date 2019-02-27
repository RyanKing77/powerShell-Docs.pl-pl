---
title: Data i godzina parametry | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846711"
---
# <a name="date-and-time-parameters"></a><span data-ttu-id="f855f-102">Parametry daty i godziny</span><span class="sxs-lookup"><span data-stu-id="f855f-102">Date and Time Parameters</span></span>

<span data-ttu-id="f855f-103">W poniższej tabeli wymieniono nazwy zalecane i funkcje dotyczące parametrów, które obsługują informacji daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="f855f-103">The following table lists recommended names and functionality for parameters that handle date and time information.</span></span> <span data-ttu-id="f855f-104">Parametry Data i godzina zazwyczaj są używane do rejestrowania, gdy coś, co zostanie utworzony lub uzyskać dostępu do.</span><span class="sxs-lookup"><span data-stu-id="f855f-104">Date and time parameters are typically used to record when something is created or accessed.</span></span>

<span data-ttu-id="f855f-105">Dostęp do danych, wpisz: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f855f-105">Accessed Data type: SwitchParameter</span></span>

<span data-ttu-id="f855f-106">Implementowanie tego parametru, jeśli jest określony, polecenie cmdlet będzie działać na zasoby, które były używane oparte na datę i godzinę, określonym przez `Before` i `After` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f855f-106">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been accessed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="f855f-107">Jeśli ten parametr jest określony, `Created` i `Modified` parametry muszą być nie można określić.</span><span class="sxs-lookup"><span data-stu-id="f855f-107">If this parameter is specified, the `Created` and `Modified` parameters must be not be specified.</span></span>

<span data-ttu-id="f855f-108">Po typ danych: DateTime</span><span class="sxs-lookup"><span data-stu-id="f855f-108">After Data type: DateTime</span></span>

<span data-ttu-id="f855f-109">Implementuje ten parametr, aby określić datę i godzinę, po którym użyto polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f855f-109">Implement this parameter to specify the date and time after which the cmdlet was used.</span></span> <span data-ttu-id="f855f-110">Dla `After` parametru, aby działać, musi mieć również polecenia cmdlet `Accessed`, `Created`, lub `Modified` parametru.</span><span class="sxs-lookup"><span data-stu-id="f855f-110">For the `After` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="f855f-111">A ten parametr musi być równa `true` po nosi nazwę polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f855f-111">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="f855f-112">Przed typ danych: DateTime</span><span class="sxs-lookup"><span data-stu-id="f855f-112">Before Data type: DateTime</span></span>

<span data-ttu-id="f855f-113">Implementuje ten parametr, aby określić datę i godzinę, przed którym użyto polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f855f-113">Implement this parameter to specify the date and time before which the cmdlet was used.</span></span> <span data-ttu-id="f855f-114">Dla `Before` parametru, aby działać, musi mieć również polecenia cmdlet `Accessed`, `Created`, lub `Modified` parametru.</span><span class="sxs-lookup"><span data-stu-id="f855f-114">For the `Before` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="f855f-115">A ten parametr musi być równa `true` po nosi nazwę polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f855f-115">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="f855f-116">Utworzony typ danych: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f855f-116">Created Data type: SwitchParameter</span></span>

<span data-ttu-id="f855f-117">Implementowanie tego parametru, gdy jest określony, polecenie cmdlet będzie działać na zasobach, które zostały utworzone na podstawie daty i czasu określonego przez `Before` i `After` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f855f-117">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been created based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="f855f-118">Jeśli ten parametr jest określony, `Accessed` i `Modified` parametrów nie może być określony.</span><span class="sxs-lookup"><span data-stu-id="f855f-118">If this parameter is specified, the `Accessed` and `Modified` parameters must not be specified.</span></span>

<span data-ttu-id="f855f-119">Dokładne dane, wpisz: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="f855f-119">Exact Data type: SwitchParameter</span></span>

<span data-ttu-id="f855f-120">Implementowanie tego parametru, gdy określono wyrażenie zasobu musi być zgodny nazwy zasobu.</span><span class="sxs-lookup"><span data-stu-id="f855f-120">Implement this parameter so that when it is specified the resource term must match the resource name exactly.</span></span> <span data-ttu-id="f855f-121">Jeśli nie określono parametru termin zasobów i nazwy nie powinny być dokładnie.</span><span class="sxs-lookup"><span data-stu-id="f855f-121">When the parameter is not specified the resource term and name do not need to match exactly.</span></span>

<span data-ttu-id="f855f-122">Zmodyfikowane dane, wpisz: DateTime</span><span class="sxs-lookup"><span data-stu-id="f855f-122">Modified Data type: DateTime</span></span>

<span data-ttu-id="f855f-123">Implementowanie tego parametru, gdy jest określony, polecenie cmdlet będzie działać na zasobach, które zostały zmienione na podstawie daty i czas określony przez `Before` i `After` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f855f-123">Implement this parameter so that when it is specified the cmdlet will operate on resources that have been changed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="f855f-124">Jeśli ten parametr jest określony, `Accessed` i `Created` parametrów nie może być określony.</span><span class="sxs-lookup"><span data-stu-id="f855f-124">If this parameter is specified, the `Accessed` and `Created` parameters must not be specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="f855f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f855f-125">See Also</span></span>

[<span data-ttu-id="f855f-126">Parametry polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="f855f-126">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="f855f-127">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f855f-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="f855f-128">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f855f-128">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
