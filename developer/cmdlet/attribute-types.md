---
title: Typy atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852276"
---
# <a name="attribute-types"></a><span data-ttu-id="f4274-102">Typy atrybutów</span><span class="sxs-lookup"><span data-stu-id="f4274-102">Attribute Types</span></span>

<span data-ttu-id="f4274-103">Polecenia cmdlet atrybuty mogą być grupowane według funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4274-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="f4274-104">W poniższych sekcjach opisano dostępne atrybuty i opisują, jakie środowisko uruchomieniowe wykonuje, gdy ten atrybut jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f4274-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="f4274-105">Atrybuty poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4274-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="f4274-106">Polecenie cmdlet</span><span class="sxs-lookup"><span data-stu-id="f4274-106">Cmdlet</span></span>

<span data-ttu-id="f4274-107">Określa klasę .NET Framework jako polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4274-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="f4274-108">Jest to wymaganego atrybutu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f4274-108">This is the required base attribute.</span></span>
<span data-ttu-id="f4274-109">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu polecenia Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="f4274-110">Atrybuty parametru</span><span class="sxs-lookup"><span data-stu-id="f4274-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="f4274-111">Parametr</span><span class="sxs-lookup"><span data-stu-id="f4274-111">Parameter</span></span>

<span data-ttu-id="f4274-112">Identyfikuje właściwość publiczna w klasie polecenia cmdlet jako parametr polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4274-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="f4274-113">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu parametru](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="f4274-114">Alias</span><span class="sxs-lookup"><span data-stu-id="f4274-114">Alias</span></span>

<span data-ttu-id="f4274-115">Określa jeden lub więcej aliasów dla parametru.</span><span class="sxs-lookup"><span data-stu-id="f4274-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="f4274-116">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="f4274-117">Argument atrybutów sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="f4274-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="f4274-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f4274-118">ValidateCount</span></span>

<span data-ttu-id="f4274-119">Określa minimalną i maksymalną liczbę argumentów, które są dozwolone dla parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4274-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="f4274-120">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="f4274-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="f4274-121">ValidateLength</span></span>

<span data-ttu-id="f4274-122">Określa minimalną i maksymalną liczbę znaków dla parametru w argumencie polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4274-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f4274-123">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="f4274-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="f4274-124">ValidatePattern</span></span>

<span data-ttu-id="f4274-125">Określa wzorzec wyrażenia regularnego, który argument parametru polecenia cmdlet muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="f4274-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="f4274-126">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="f4274-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f4274-127">ValidateRange</span></span>

<span data-ttu-id="f4274-128">Określa minimalne i maksymalne wartości dla argumentu parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4274-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="f4274-129">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="f4274-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="f4274-130">ValidateSet</span></span>

<span data-ttu-id="f4274-131">Określa zestaw prawidłowych wartości dla argumentu parametru polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4274-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="f4274-132">Aby uzyskać więcej informacji, zobacz [deklaracji atrybutu ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4274-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4274-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4274-133">See Also</span></span>

[<span data-ttu-id="f4274-134">Zestaw SDK programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4274-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
