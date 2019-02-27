---
title: Deklaracji atrybutu alias | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846144"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="f44f5-102">Alias, deklaracja atrybutu</span><span class="sxs-lookup"><span data-stu-id="f44f5-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="f44f5-103">Atrybut Alias umożliwia użytkownikowi określenie różnych nazw parametrów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f44f5-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="f44f5-104">Aliasy może służyć do zapewnienia skróty dla nazwy parametru lub zapewniają różne nazwy, które są odpowiednie dla różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f44f5-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="f44f5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f44f5-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="f44f5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f44f5-106">Parameters</span></span>

<span data-ttu-id="f44f5-107">`aliasName` (Ciąg[]) Wymagane.</span><span class="sxs-lookup"><span data-stu-id="f44f5-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="f44f5-108">Określa zestaw nazw rozdzielonych przecinkami aliasu dla parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f44f5-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="f44f5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f44f5-109">Remarks</span></span>

- <span data-ttu-id="f44f5-110">Atrybut Alias jest używany z atrybutem parametru, w przypadku określenia parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f44f5-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="f44f5-111">Aby uzyskać więcej informacji o tym, jak zadeklarować tych atrybutów, zobacz [jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f44f5-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="f44f5-112">Każda nazwa aliasu musi być unikatowa w obrębie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f44f5-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="f44f5-113">Nie sprawdza programu Windows PowerShell dla nazw duplikacji aliasu.</span><span class="sxs-lookup"><span data-stu-id="f44f5-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="f44f5-114">Atrybut Alias jest używany jeden raz dla każdego z parametrów polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f44f5-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="f44f5-115">Ten atrybut aliasu jest definiowany przez [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) klasy.</span><span class="sxs-lookup"><span data-stu-id="f44f5-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f44f5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f44f5-116">See Also</span></span>

[<span data-ttu-id="f44f5-117">Parametr aliasów</span><span class="sxs-lookup"><span data-stu-id="f44f5-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="f44f5-118">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f44f5-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
