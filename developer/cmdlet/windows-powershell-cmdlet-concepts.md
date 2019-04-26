---
title: Pojęcia dotyczące polecenia Cmdlet programu PowerShell Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067081"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="a7afd-102">Zagadnienia dotyczące poleceń cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7afd-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="a7afd-103">W tej sekcji opisano, jak działają polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a7afd-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a7afd-104">In This Section</span></span>

<span data-ttu-id="a7afd-105">Ta sekcja zawiera następujące tematy.</span><span class="sxs-lookup"><span data-stu-id="a7afd-105">This section includes the following topics.</span></span>

<span data-ttu-id="a7afd-106">[Wskazówki dotyczące programowania polecenia cmdlet](./cmdlet-development-guidelines.md) w tym temacie przedstawiono wskazówki dotyczące programowania, które mogą służyć do tworzenia poprawnie sformułowanym poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="a7afd-107">[Deklaracja klasy polecenia cmdlet](./cmdlet-class-declaration.md) w tym temacie opisano deklaracji klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="a7afd-108">[Zatwierdzone czasowniki dla Windows PowerShell polecenia](./approved-verbs-for-windows-powershell-commands.md) ten temat zawiera listę zleceń wstępnie zdefiniowanego polecenia cmdlet, które można użyć, gdy Deklarujesz klasę polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="a7afd-109">[Polecenia cmdlet metody przetwarzania danych wejściowych](./cmdlet-input-processing-methods.md) w tym temacie opisano metody, które umożliwia polecenia cmdlet w celu wykonywania operacji przetwarzania wstępnego, dane wejściowe operacji przetwarzania i publikowania operacje przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a7afd-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="a7afd-110">[Parametry polecenia cmdlet](./cmdlet-parameters.md) w tej sekcji opisano różne typy parametrów, które można dodać do polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="a7afd-111">[Polecenia cmdlet atrybuty](./cmdlet-attributes.md) w tej sekcji opisano atrybuty, które są używane do deklarowania klas .NET Framework jako polecenia cmdlet, aby zadeklarować pola jako parametry polecenia cmdlet, a do deklarowania reguł sprawdzania poprawności danych wejściowych dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="a7afd-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="a7afd-112">[Aliasy polecenia cmdlet](./cmdlet-aliases.md) w tym temacie opisano aliasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="a7afd-113">[Dane wyjściowe polecenia cmdlet](./cmdlet-output.md) w tej sekcji opisano typ danych wyjściowych polecenia cmdlet mogą zwracać i jak zdefiniować i wyświetlić obiekty, które są zwracane przez polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7afd-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="a7afd-114">[Rejestrowanie poleceń cmdlet](./modules-and-snap-ins.md) w tej sekcji opisano, jak zarejestrować poleceń cmdlet przy użyciu modułów i przystawek.</span><span class="sxs-lookup"><span data-stu-id="a7afd-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="a7afd-115">[Żądanie potwierdzenia](./requesting-confirmation-from-cmdlets.md) w tej sekcji opisano, jak polecenia cmdlet żądania potwierdzenia przez użytkownika przed wprowadzeniem zmian w systemie.</span><span class="sxs-lookup"><span data-stu-id="a7afd-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="a7afd-116">[Raportowanie błędów programu Windows PowerShell](./error-reporting-concepts.md) w tej sekcji opisano, jak polecenia cmdlet raportowaniem błędów powodujący zakończenie i błędy niepowodujące i opisano w nim sposób interpretowania rekordów błędów.</span><span class="sxs-lookup"><span data-stu-id="a7afd-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="a7afd-117">[Zadania w tle](./background-jobs.md) w tym temacie opisano, jak polecenia cmdlet można wykonywać swoją pracę w ramach zadania w tle, które nie kolidują z poleceniami, które są wykonywane w bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="a7afd-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="a7afd-118">[Wywoływanie polecenia cmdlet i skryptów w ramach polecenia Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) w tym temacie opisano, jak polecenia cmdlet można wywoływać innych poleceń cmdlet i skryptów z poziomu metody przetwarzania danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a7afd-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="a7afd-119">[Polecenie cmdlet ustawia](./cmdlet-sets.md) w tym temacie opisano tworzenie zestawów poleceń cmdlet przy użyciu klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="a7afd-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="a7afd-120">[Stan sesji programu Windows PowerShell](./windows-powershell-session-state.md) w tym temacie opisano stanu sesji programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7afd-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
