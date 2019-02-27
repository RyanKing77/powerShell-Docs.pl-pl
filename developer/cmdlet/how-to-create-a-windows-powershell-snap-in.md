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
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849441"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="142b6-102">Jak utworzyć przystawkę programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="142b6-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="142b6-103">Przystawka programu Windows PowerShell udostępnia mechanizm do rejestrowania zestawów poleceń cmdlet lub innego dostawcy środowiska Windows PowerShell za pomocą powłoki, w związku z tym rozszerzania funkcji powłoki.</span><span class="sxs-lookup"><span data-stu-id="142b6-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="142b6-104">Przystawkę programu Windows PowerShell można zarejestrować wszystkie polecenia cmdlet i dostawców w jednym zestawie, albo go określonej listy poleceń cmdlet i dostawców.</span><span class="sxs-lookup"><span data-stu-id="142b6-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="142b6-105">Zestawy w przystawce należy zainstalować w chronionym katalogu, tak, jak je z innymi systemami operacyjnymi.</span><span class="sxs-lookup"><span data-stu-id="142b6-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="142b6-106">W przeciwnym razie złośliwych użytkowników można zastąpić zestawu niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="142b6-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="142b6-107">Windows PowerShell w przystawce klas</span><span class="sxs-lookup"><span data-stu-id="142b6-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="142b6-108">Wszystkie klasy przystawkę programu Windows PowerShell pochodzić od [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) lub [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasy.</span><span class="sxs-lookup"><span data-stu-id="142b6-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="142b6-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="142b6-109">Examples</span></span>

<span data-ttu-id="142b6-110">[Zapisywanie przystawki programu PowerShell Windows](./writing-a-windows-powershell-snap-in.md): Ten przykład przedstawia sposób tworzenia przystawki, który służy do rejestrowania wszystkich poleceń cmdlet i dostawców w zestawie.</span><span class="sxs-lookup"><span data-stu-id="142b6-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="142b6-111">[Pisanie niestandardowych Windows PowerShell przystawką](./writing-a-custom-windows-powershell-snap-in.md): Ten przykład przedstawia sposób tworzenia niestandardowych przystawki używanego do zarejestrowania określonego zestawu poleceń cmdlet i dostawców, którzy mogą lub nie mogą istnieć w jednym zestawie.</span><span class="sxs-lookup"><span data-stu-id="142b6-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="142b6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="142b6-112">See Also</span></span>

[<span data-ttu-id="142b6-113">System.Management.Automation.Pssnapin</span><span class="sxs-lookup"><span data-stu-id="142b6-113">System.Management.Automation.Pssnapin</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="142b6-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="142b6-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="142b6-115">Rejestrowanie poleceń cmdlet</span><span class="sxs-lookup"><span data-stu-id="142b6-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="142b6-116">Powłoka programu Windows PowerShell zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="142b6-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
