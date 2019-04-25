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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083352"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Jak dodać powiązane linki do tematu pomocy dotyczącego polecenia cmdlet

W tej sekcji opisano sposób dodawania odwołania do innej zawartości, która jest powiązana z tematu pomocy polecenia cmdlet Windows PowerShell®. Ponieważ te odwołania są wyświetlane w oknie polecenia, nie łączą bezpośrednio do zawartości, której dotyczy odwołanie.

W tematach pomocy polecenia cmdlet, które są objęte Windows PowerShell® te linki odwoływać się do innych poleceń cmdlet, zawartości koncepcyjnej ("about_") i inne dokumenty i pliki pomocy, które nie są związane z Windows PowerShell®.

Następujący kod XML pokazuje, jak dodać węzeł RelatedLinks, który zawiera dwa odwołania do powiązanych tematów.

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



