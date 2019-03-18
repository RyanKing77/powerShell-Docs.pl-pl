---
title: Stan sesji programu Windows PowerShell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059545"
---
# <a name="windows-powershell-session-state"></a>Stan sesji program Windows PowerShell

Stan sesji odnosi się do bieżącej konfiguracji sesji środowiska Windows PowerShell lub modułu. Sesję środowiska Windows PowerShell jest środowisko operacyjne, w którym używać hasła interaktywnie według wiersza polecenia użytkownika lub programowo aplikacji hosta. Stan sesji jest nazywana globalnego stanu sesji.

Z punktu widzenia projektanta sesję środowiska Windows PowerShell odnosi się do czasu między po otwarciu obszaru działania programu Windows PowerShell w aplikacji hosta, a kiedy zostanie zamknięty obszarze działania. Przyjrzano się w inny sposób, sesja jest okres istnienia wystąpienia aparatu programu Windows PowerShell, które jest wywoływane, gdy istnieje w obszarze działania.

## <a name="module-session-state"></a>Stan sesji modułu

Stany sesji modułu są tworzone w każdym przypadku, gdy moduł lub jednej z jego zagnieżdżonych moduły są importowane do sesji. Gdy moduł eksportuje element, na przykład polecenia cmdlet, funkcji lub skryptu, odwołania do tego elementu jest dodawany do stanu sesji globalnej sesji. Jednak gdy element zostanie uruchomiony, jest ono wykonywane w ramach stanu sesji modułu.

## <a name="session-state-data"></a>Dane stanu sesji

Dane stanu sesji może być publicznym lub prywatnym. Publiczne dane są dostępne dla wywołań spoza stanu sesji, gdy prywatne dane są dostępne tylko do wywołań z w ramach stanu sesji. Na przykład moduł może mieć prywatnych funkcja, która może być wywoływana tylko przez moduł lub tylko wewnętrznie przez element publiczny, który został wyeksportowany. Jest to podobne do prywatnych i publicznych elementów członkowskich typu .NET Framework.

Dane stanu sesji jest przechowywany przez bieżące wystąpienie aparatu wykonywania w kontekście bieżącej sesji programu Windows PowerShell. Dane stanu sesji obejmuje następujące elementy:

- Informacje o ścieżce

- Informacje o dysku

- Informacje o dostawcy programu Windows PowerShell

- Informacje o zaimportowanych modułów i odwołania do elementów modułu (takich jak polecenia cmdlet, funkcji i skryptów), które są eksportowane przez moduł. Te informacje i te odwołania są przeznaczone tylko stan globalny sesji.

- Informacje o zmiennej stanu sesji

## <a name="accessing-session-state-data-within-cmdlets"></a>Uzyskiwanie dostępu do danych stanu sesji w ramach polecenia cmdlet

Polecenia cmdlet mają dostęp do danych stanu sesji w wartość pośredni przez [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) właściwości klasy polecenia cmdlet lub bezpośrednio za pomocą [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasy. [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasy zawiera właściwości, które mogą służyć do badania różnego rodzaju dane stanu sesji.

## <a name="see-also"></a>Zobacz też

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Polecenia cmdlet programu Windows PowerShell](./cmdlet-overview.md)

[Zapisywanie polecenia Cmdlet programu Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Powłoka programu Windows PowerShell zestawu SDK](../windows-powershell-reference.md)
