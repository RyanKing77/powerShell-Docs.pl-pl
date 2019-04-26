---
title: Atrybuty w kodzie polecenia Cmdlet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068690"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="29944-102">Atrybuty w kodzie polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="29944-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="29944-103">Aby użyć typowe funkcje udostępniane przez środowisko Windows PowerShell, klas i właściwości publiczne zdefiniowane w kodzie polecenia cmdlet są oznaczone za pomocą atrybutów.</span><span class="sxs-lookup"><span data-stu-id="29944-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="29944-104">Na przykład poniższą definicję klasy używa atrybutu polecenia Cmdlet, aby zidentyfikować klasy programu Microsoft .NET Framework, w której **Get-Proc** polecenia cmdlet jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="29944-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="29944-105">(To polecenie cmdlet służy jako przykład w tym dokumencie i jest podobna do `Get-Process` dostarczane przez środowisko Windows PowerShell polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="29944-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="29944-106">Te atrybuty są uznawane za metadanych, ponieważ ich implementacji różni się od wykonania kodu polecenie cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29944-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="29944-107">Po uruchomieniu polecenia cmdlet programu Windows PowerShell środowiska uruchomieniowego rozpoznaje atrybutów, a następnie oblicza odpowiednią akcję dla każdego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="29944-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="29944-108">Mimo że można zaimplementować własną wersję funkcje udostępniane przez te atrybuty, projekcie dobre polecenia cmdlet są używane następujące typowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="29944-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="29944-109">Aby uzyskać więcej informacji na temat różnych atrybutów, które może być zadeklarowana w poleceń cmdlet, zobacz [typy atrybutów](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="29944-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29944-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29944-110">See Also</span></span>

[<span data-ttu-id="29944-111">Typy atrybutów</span><span class="sxs-lookup"><span data-stu-id="29944-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="29944-112">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="29944-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
