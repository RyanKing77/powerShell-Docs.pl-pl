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
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846242"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="46448-102">Wywoływanie poleceń cmdlet i skryptów w ramach polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="46448-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="46448-103">Polecenia cmdlet można wywoływać innych poleceń cmdlet i skryptów na dane wejściowe przetwarzania metody polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46448-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="46448-104">Dzięki temu można dodawać funkcjonalność istniejących poleceń cmdlet i skryptów do Twojego polecenia cmdlet bez konieczności ponownego pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="46448-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="46448-105">Invoke — metoda</span><span class="sxs-lookup"><span data-stu-id="46448-105">The Invoke Method</span></span>

<span data-ttu-id="46448-106">Wszystkie polecenia cmdlet istniejące polecenia cmdlet mogą być wywoływane przez wywołanie metody [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metodę z wejściem przetwarzania metody, takie jak [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), która zostaje zastąpiona przez polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46448-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="46448-107">Jednak można wywoływać tylko tych poleceń cmdlet, które pochodzą bezpośrednio z [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasy.</span><span class="sxs-lookup"><span data-stu-id="46448-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="46448-108">Nie można wywołać polecenia cmdlet, która pochodzi od klasy [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasy.</span><span class="sxs-lookup"><span data-stu-id="46448-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="46448-109">[System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metoda ma następujących wariantów.</span><span class="sxs-lookup"><span data-stu-id="46448-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="46448-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) wariantu wywołuje obiekt polecenia cmdlet i zwraca kolekcję obiektów typu "T".</span><span class="sxs-lookup"><span data-stu-id="46448-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="46448-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) wariantu wywołuje obiekt polecenia cmdlet i zwraca emumerator silnie typizowanych.</span><span class="sxs-lookup"><span data-stu-id="46448-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="46448-112">Ten wariant umożliwia użytkownikowi wykonywanie niestandardowych operacji za pomocą obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46448-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="46448-113">Przykłady</span><span class="sxs-lookup"><span data-stu-id="46448-113">Examples</span></span>

|<span data-ttu-id="46448-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="46448-114">Example</span></span>|<span data-ttu-id="46448-115">Opis</span><span class="sxs-lookup"><span data-stu-id="46448-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46448-116">Wywoływanie polecenia cmdlet w ramach polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="46448-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="46448-117">W tym przykładzie przedstawiono sposób wywołania polecenia cmdlet w ramach innego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46448-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="46448-118">Wywoływanie skryptów w ramach polecenia Cmdlet</span><span class="sxs-lookup"><span data-stu-id="46448-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="46448-119">W tym przykładzie przedstawiono sposób wywołania skryptu, który jest dostarczany do polecenia cmdlet z w ramach innego polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46448-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="46448-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46448-120">See Also</span></span>

[<span data-ttu-id="46448-121">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="46448-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
