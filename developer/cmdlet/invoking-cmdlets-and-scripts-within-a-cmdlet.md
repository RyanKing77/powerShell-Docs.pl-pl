---
title: Wywoływanie polecenia cmdlet i skryptów w ramach polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067675"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Wywoływanie poleceń cmdlet i skryptów w ramach polecenia cmdlet

Polecenia cmdlet można wywoływać innych poleceń cmdlet i skryptów na dane wejściowe przetwarzania metody polecenia cmdlet. Dzięki temu można dodawać funkcjonalność istniejących poleceń cmdlet i skryptów do Twojego polecenia cmdlet bez konieczności ponownego pisania kodu.

## <a name="the-invoke-method"></a>Invoke — metoda

Wszystkie polecenia cmdlet istniejące polecenia cmdlet mogą być wywoływane przez wywołanie metody [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metodę z wejściem przetwarzania metody, takie jak [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), która zostaje zastąpiona przez polecenie cmdlet. Jednak można wywoływać tylko tych poleceń cmdlet, które pochodzą bezpośrednio z [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy. Nie można wywołać polecenia cmdlet, która pochodzi od klasy [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy.

[System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metoda ma następujących wariantów.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) wariantu wywołuje obiekt polecenia cmdlet i zwraca kolekcję obiektów typu "T".

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) wariantu wywołuje obiekt polecenia cmdlet i zwraca emumerator silnie typizowanych. Ten wariant umożliwia użytkownikowi wykonywanie niestandardowych operacji za pomocą obiektów w kolekcji.

## <a name="examples"></a>Przykłady

|Przykład|Opis|
|-------------|-----------------|
|[Wywoływanie polecenia cmdlet w ramach polecenia Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|W tym przykładzie przedstawiono sposób wywołania polecenia cmdlet w ramach innego polecenia cmdlet.|
|[Wywoływanie skryptów w ramach polecenia Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|W tym przykładzie przedstawiono sposób wywołania skryptu, który jest dostarczany do polecenia cmdlet z w ramach innego polecenia cmdlet.|

## <a name="see-also"></a>Zobacz też

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
