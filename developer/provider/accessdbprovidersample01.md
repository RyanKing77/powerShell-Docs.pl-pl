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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081125"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="8044b-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="8044b-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="8044b-103">Ten przykład pokazuje sposób deklarowania klas dostawcy, który pochodzi bezpośrednio z [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8044b-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="8044b-104">Została ona tutaj uwzględniona tylko w przypadku informacje były kompletne.</span><span class="sxs-lookup"><span data-stu-id="8044b-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8044b-105">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="8044b-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8044b-106">Klasa dostawcy będą najprawdopodobniej klasy pochodnej z jednego z następujących klas i prawdopodobnie zaimplementować inne interfejsy dostawcy:</span><span class="sxs-lookup"><span data-stu-id="8044b-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="8044b-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8044b-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="8044b-108">Zobacz [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="8044b-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="8044b-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8044b-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="8044b-110">Zobacz [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="8044b-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="8044b-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8044b-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="8044b-112">Zobacz [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="8044b-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="8044b-113">Aby uzyskać więcej informacji na temat wybierania klasy dostawcy, które pochodzi od na podstawie dostawcy funkcji, zobacz [projektowania Your Windows PowerShell dostawcy](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="8044b-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="8044b-114">W tym przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="8044b-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="8044b-115">Deklarowanie `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8044b-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="8044b-116">Definiowanie klasy dostawcy, który pochodzi bezpośrednio z [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="8044b-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="8044b-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="8044b-117">Example</span></span>

<span data-ttu-id="8044b-118">Ten przykład pokazuje, jak definiować klasy dostawcy i sposób deklarowania `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8044b-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8044b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8044b-119">See Also</span></span>

[<span data-ttu-id="8044b-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8044b-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="8044b-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8044b-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="8044b-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8044b-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="8044b-123">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8044b-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)