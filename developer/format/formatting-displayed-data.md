---
title: Formatowanie wyświetlanych danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065669"
---
# <a name="formatting-displayed-data"></a>Formatowanie wyświetlanych danych

Można określić sposób wyświetlania poszczególnych punktów danych na liście, tabela lub szerokie. Możesz użyć `FormatString` elementu podczas definiowania elementów widoku, lub można użyć `ScriptBlock` elementu do wywołania `FormatString` metody dotyczące danych.

## <a name="using-the-formatstring-element"></a>Za pomocą elementu FormatString

W poniższym przykładzie wartość elementu `TotalProcessorTime` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu jest formatowana przy użyciu elementu FormatString. `TotalProcessorTime` Właściwości

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



