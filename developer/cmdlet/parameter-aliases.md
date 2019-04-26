---
title: Parametr aliasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067590"
---
# <a name="parameter-aliases"></a><span data-ttu-id="06229-102">Aliasy parametrów</span><span class="sxs-lookup"><span data-stu-id="06229-102">Parameter Aliases</span></span>

<span data-ttu-id="06229-103">Parametry polecenia cmdlet mogą również mieć aliasy.</span><span class="sxs-lookup"><span data-stu-id="06229-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="06229-104">Podczas wpisywania lub określić parametr w poleceniu, można użyć aliasów zamiast nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="06229-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="06229-105">Korzyści z używania aliasów</span><span class="sxs-lookup"><span data-stu-id="06229-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="06229-106">Dodawanie aliasów parametrów zapewnia następujące korzyści.</span><span class="sxs-lookup"><span data-stu-id="06229-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="06229-107">Możesz podać skrót, dzięki czemu użytkownik musi używać nazwy parametru ukończone po wywołaniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="06229-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="06229-108">Na przykład można użyć aliasu "CN" zamiast nazwy parametru "Nazwa_komputera".</span><span class="sxs-lookup"><span data-stu-id="06229-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="06229-109">Jeśli chcesz zapewnić różne nazwy dla tego samego parametru, można zdefiniować wiele aliasów.</span><span class="sxs-lookup"><span data-stu-id="06229-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="06229-110">Można zdefiniować wiele aliasów, jeśli trzeba pracować z wieloma grupami użytkowników, które odwołują się do tych samych danych na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="06229-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="06229-111">Możesz podać wstecznej zgodności istniejące skrypty przypadku zmiany nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="06229-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="06229-112">Za pomocą atrybutu Alias wraz z atrybutem ValueFromPipelineByName można zdefiniować parametr, który umożliwia Twojego polecenia cmdlet powiązać z różnych typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="06229-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="06229-113">Na przykład załóżmy, że masz dwa obiekty o różnych typach i pierwszy obiekt ma właściwość zapisywania i drugi obiekt ma właściwość edytora.</span><span class="sxs-lookup"><span data-stu-id="06229-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="06229-114">Jeśli Twojego polecenia cmdlet parametr, który ma składnik zapisywania i Edytor aliasy i polecenia cmdlet zaakceptowane wejście potokowe w nazw właściwości, Twojego polecenia cmdlet można dowiązać do obu obiektów za pomocą dwóch aliasów parametrów.</span><span class="sxs-lookup"><span data-stu-id="06229-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="06229-115">Aby uzyskać więcej informacji na temat aliasy, które mogą być używane z określonymi parametrami, zobacz [typowych nazw parametrów](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="06229-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="06229-116">Definiowanie aliasów parametrów</span><span class="sxs-lookup"><span data-stu-id="06229-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="06229-117">Aby zdefiniować alias dla parametru, należy zadeklarować atrybut aliasu, jak pokazano w poniższej deklaracji parametru.</span><span class="sxs-lookup"><span data-stu-id="06229-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="06229-118">W tym przykładzie wiele aliasów są zdefiniowane dla tego samego parametru.</span><span class="sxs-lookup"><span data-stu-id="06229-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="06229-119">(Aby uzyskać więcej informacji, zobacz[jak deklarować parametry polecenia Cmdlet](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="06229-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="06229-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06229-120">See Also</span></span>

[<span data-ttu-id="06229-121">Nazwy wspólnych parametrów</span><span class="sxs-lookup"><span data-stu-id="06229-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="06229-122">Sposób deklarowania parametry polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="06229-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="06229-123">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="06229-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
