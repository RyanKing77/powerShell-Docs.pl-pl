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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846102"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="2073f-102">Formatowanie wyświetlanych danych</span><span class="sxs-lookup"><span data-stu-id="2073f-102">Formatting Displayed Data</span></span>

<span data-ttu-id="2073f-103">Można określić sposób wyświetlania poszczególnych punktów danych na liście, tabela lub szerokie.</span><span class="sxs-lookup"><span data-stu-id="2073f-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="2073f-104">Możesz użyć `FormatString` elementu podczas definiowania elementów widoku, lub można użyć `ScriptBlock` elementu do wywołania `FormatString` metody dotyczące danych.</span><span class="sxs-lookup"><span data-stu-id="2073f-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="2073f-105">Za pomocą elementu FormatString</span><span class="sxs-lookup"><span data-stu-id="2073f-105">Using the FormatString Element</span></span>

<span data-ttu-id="2073f-106">W poniższym przykładzie wartość elementu `TotalProcessorTime` właściwość [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) obiektu jest formatowana przy użyciu elementu FormatString.</span><span class="sxs-lookup"><span data-stu-id="2073f-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="2073f-107">`TotalProcessorTime` Właściwości</span><span class="sxs-lookup"><span data-stu-id="2073f-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



