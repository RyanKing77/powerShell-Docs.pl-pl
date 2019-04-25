---
title: Jak utworzyć przystawki Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067998"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Jak utworzyć przystawkę programu Windows PowerShell

Przystawka programu Windows PowerShell udostępnia mechanizm do rejestrowania zestawów poleceń cmdlet lub innego dostawcy środowiska Windows PowerShell za pomocą powłoki, w związku z tym rozszerzania funkcji powłoki. Przystawkę programu Windows PowerShell można zarejestrować wszystkie polecenia cmdlet i dostawców w jednym zestawie, albo go określonej listy poleceń cmdlet i dostawców.

Zestawy w przystawce należy zainstalować w chronionym katalogu, tak, jak je z innymi systemami operacyjnymi. W przeciwnym razie złośliwych użytkowników można zastąpić zestawu niebezpieczny kod.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell w przystawce klas

Wszystkie klasy przystawkę programu Windows PowerShell pochodzić od [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) lub [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasy.

## <a name="examples"></a>Przykłady

[Zapisywanie przystawki programu PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Ten przykład przedstawia sposób tworzenia przystawki, który służy do rejestrowania wszystkich poleceń cmdlet i dostawców w zestawie.

[Pisanie niestandardowych Windows PowerShell przystawką](./writing-a-custom-windows-powershell-snap-in.md): Ten przykład przedstawia sposób tworzenia niestandardowych przystawki używanego do zarejestrowania określonego zestawu poleceń cmdlet i dostawców, którzy mogą lub nie mogą istnieć w jednym zestawie.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Rejestrowanie poleceń cmdlet](./registering-cmdlets.md)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
