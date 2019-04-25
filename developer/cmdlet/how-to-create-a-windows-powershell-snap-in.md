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
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="29153-102">Jak utworzyć przystawkę programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29153-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="29153-103">Przystawka programu Windows PowerShell udostępnia mechanizm do rejestrowania zestawów poleceń cmdlet lub innego dostawcy środowiska Windows PowerShell za pomocą powłoki, w związku z tym rozszerzania funkcji powłoki.</span><span class="sxs-lookup"><span data-stu-id="29153-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="29153-104">Przystawkę programu Windows PowerShell można zarejestrować wszystkie polecenia cmdlet i dostawców w jednym zestawie, albo go określonej listy poleceń cmdlet i dostawców.</span><span class="sxs-lookup"><span data-stu-id="29153-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="29153-105">Zestawy w przystawce należy zainstalować w chronionym katalogu, tak, jak je z innymi systemami operacyjnymi.</span><span class="sxs-lookup"><span data-stu-id="29153-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="29153-106">W przeciwnym razie złośliwych użytkowników można zastąpić zestawu niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="29153-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="29153-107">Windows PowerShell w przystawce klas</span><span class="sxs-lookup"><span data-stu-id="29153-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="29153-108">Wszystkie klasy przystawkę programu Windows PowerShell pochodzić od [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) lub [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasy.</span><span class="sxs-lookup"><span data-stu-id="29153-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="29153-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="29153-109">Examples</span></span>

<span data-ttu-id="29153-110">[Zapisywanie przystawki programu PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Ten przykład przedstawia sposób tworzenia przystawki, który służy do rejestrowania wszystkich poleceń cmdlet i dostawców w zestawie.</span><span class="sxs-lookup"><span data-stu-id="29153-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="29153-111">[Pisanie niestandardowych Windows PowerShell przystawką](./writing-a-custom-windows-powershell-snap-in.md): Ten przykład przedstawia sposób tworzenia niestandardowych przystawki używanego do zarejestrowania określonego zestawu poleceń cmdlet i dostawców, którzy mogą lub nie mogą istnieć w jednym zestawie.</span><span class="sxs-lookup"><span data-stu-id="29153-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="29153-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29153-112">See Also</span></span>

[<span data-ttu-id="29153-113">System.Management.Automation.PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="29153-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="29153-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="29153-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="29153-115">Rejestrowanie poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="29153-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="29153-116">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="29153-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
