---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845521"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="b448c-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="b448c-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="b448c-103">Ten przykład pokazuje sposób deklarowania klas dostawcy, który pochodzi bezpośrednio z [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="b448c-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="b448c-104">Została ona tutaj uwzględniona tylko w przypadku informacje były kompletne.</span><span class="sxs-lookup"><span data-stu-id="b448c-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b448c-105">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="b448c-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b448c-106">Klasa dostawcy będą najprawdopodobniej klasy pochodnej z jednego z następujących klas i prawdopodobnie zaimplementować inne interfejsy dostawcy:</span><span class="sxs-lookup"><span data-stu-id="b448c-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="b448c-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="b448c-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b448c-108">Zobacz [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="b448c-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="b448c-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="b448c-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="b448c-110">Zobacz [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="b448c-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="b448c-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="b448c-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="b448c-112">Zobacz [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="b448c-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="b448c-113">Aby uzyskać więcej informacji na temat wybierania klasy dostawcy, które pochodzi od na podstawie dostawcy funkcji, zobacz [projektowania Your Windows PowerShell dostawcy](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="b448c-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="b448c-114">W tym przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="b448c-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b448c-115">Deklarowanie `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b448c-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="b448c-116">Definiowanie klasy dostawcy, który pochodzi bezpośrednio z [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="b448c-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="b448c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="b448c-117">Example</span></span>

<span data-ttu-id="b448c-118">Ten przykład pokazuje, jak definiować klasy dostawcy i sposób deklarowania `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b448c-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="b448c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b448c-119">See Also</span></span>

[<span data-ttu-id="b448c-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b448c-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="b448c-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b448c-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="b448c-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b448c-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="b448c-123">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b448c-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)