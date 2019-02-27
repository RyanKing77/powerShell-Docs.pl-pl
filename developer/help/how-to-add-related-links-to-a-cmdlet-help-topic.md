---
title: Jak dodać powiązane linki do tematu pomocy polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846389"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="28178-102">Jak dodać powiązane linki do tematu pomocy dotyczącego polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="28178-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="28178-103">W tej sekcji opisano sposób dodawania odwołania do innej zawartości, która jest powiązana z tematu pomocy polecenia cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="28178-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="28178-104">Ponieważ te odwołania są wyświetlane w oknie polecenia, nie łączą bezpośrednio do zawartości, której dotyczy odwołanie.</span><span class="sxs-lookup"><span data-stu-id="28178-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="28178-105">W tematach pomocy polecenia cmdlet, które są objęte Windows PowerShell® te linki odwoływać się do innych poleceń cmdlet, zawartości koncepcyjnej ("about_") i inne dokumenty i pliki pomocy, które nie są związane z Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="28178-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="28178-106">Następujący kod XML pokazuje, jak dodać węzeł RelatedLinks, który zawiera dwa odwołania do powiązanych tematów.</span><span class="sxs-lookup"><span data-stu-id="28178-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



