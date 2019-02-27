---
title: Polecenia cmdlet atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845353"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="52673-102">Atrybuty poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="52673-102">Cmdlet Attributes</span></span>

<span data-ttu-id="52673-103">Program Windows PowerShell definiuje kilka atrybutów, których można użyć, aby dodać funkcje wspólne do poleceń cmdlet bez stosowania tej funkcji w obrębie własnego kodu.</span><span class="sxs-lookup"><span data-stu-id="52673-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="52673-104">Obejmuje to atrybut polecenia Cmdlet, który identyfikuje klasę program Microsoft .NET Framework jako klasa polecenia cmdlet, atrybut OutputType, który określa typów programu .NET Framework, zwracany przez polecenie cmdlet atrybut Parameter, który określa właściwości publiczne jako polecenia cmdlet Parametry i więcej.</span><span class="sxs-lookup"><span data-stu-id="52673-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="52673-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="52673-105">In This Section</span></span>

<span data-ttu-id="52673-106">[Atrybuty w kodzie polecenia Cmdlet](./attributes-in-cmdlet-code.md) opisuje korzyści z używania atrybutów w kodzie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52673-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="52673-107">[Typy atrybutów](./attribute-types.md) opisano różne atrybuty, które można dekoracji klasy polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52673-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="52673-108">[Deklaracji atrybutu alias](./alias-attribute-declaration.md) w tym artykule opisano sposób definiowania aliasów dla nazwy parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52673-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="52673-109">[Polecenia cmdlet deklaracji atrybutu](./cmdlet-attribute-declaration.md) opisuje jak definiować klasy .NET Framework jako polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52673-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="52673-110">[Poświadczenie deklaracji atrybutu](./credential-attribute-declaration.md) zawiera opis sposobu dodawania obsługa dla konwertowania ciąg wejściowy w [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) obiektu.</span><span class="sxs-lookup"><span data-stu-id="52673-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="52673-111">[Atrybutu OutputType deklaracji](./outputtype-attribute-declaration.md) opisuje sposób określania typów programu .NET Framework, zwracany przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52673-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="52673-112">[Deklaracji atrybutu parametru](./parameter-attribute-declaration.md) opisuje jak definiować parametry polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52673-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="52673-113">[Deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md) w tym artykule opisano sposób definiowania, ile argumentów są dozwolone dla parametru.</span><span class="sxs-lookup"><span data-stu-id="52673-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="52673-114">[Deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md) w tym artykule opisano sposób definiowania długość (w znakach) argument parametru.</span><span class="sxs-lookup"><span data-stu-id="52673-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="52673-115">[Deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md) opisuje jak definiować prawidłowe wzorce dla argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="52673-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="52673-116">[Deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md) w tym artykule opisano sposób definiowania prawidłowy zakres dla argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="52673-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="52673-117">[Deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md) w tym artykule opisano sposób definiowania możliwe wartości dla argumentu parametru.</span><span class="sxs-lookup"><span data-stu-id="52673-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="52673-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="52673-118">Reference</span></span>

[<span data-ttu-id="52673-119">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52673-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
