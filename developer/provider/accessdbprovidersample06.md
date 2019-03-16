---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055550"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="db85b-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="db85b-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="db85b-103">W tym przykładzie pokazano, jak zastąpić treści metody umożliwiające obsługę wywołań `Clear-Content`, `Get-Content`, i `Set-Content` polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="db85b-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="db85b-104">Te metody powinny zostać wdrożone, gdy użytkownik musi zarządzać zawartością elementów w magazynie danych.</span><span class="sxs-lookup"><span data-stu-id="db85b-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="db85b-105">Klasa dostawcy, w tym przykładzie pochodzi z [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy która implementuje [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db85b-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="db85b-106">Przedstawiono</span><span class="sxs-lookup"><span data-stu-id="db85b-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db85b-107">Klasa dostawcy będą najprawdopodobniej klasy pochodnej z jednego z następujących klas i prawdopodobnie zaimplementować inne interfejsy dostawcy:</span><span class="sxs-lookup"><span data-stu-id="db85b-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="db85b-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="db85b-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="db85b-109">Zobacz [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="db85b-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="db85b-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="db85b-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="db85b-111">Zobacz [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="db85b-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="db85b-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy.</span><span class="sxs-lookup"><span data-stu-id="db85b-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="db85b-113">Aby uzyskać więcej informacji na temat wybierania klasy dostawcy, które pochodzi od na podstawie dostawcy funkcji, zobacz [projektowania Your Windows PowerShell dostawcy](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="db85b-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="db85b-114">W tym przykładzie pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="db85b-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="db85b-115">Deklarowanie `CmdletProvider` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="db85b-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="db85b-116">Definiowanie klasy dostawcy, która pochodzi od klasy [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasy i która deklaruje [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db85b-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="db85b-117">Zastępowanie [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metodę, aby zmienić zachowanie `Clear-Content` polecenia cmdlet, dzięki czemu użytkownik próbę usunięcia zawartości z elementu.</span><span class="sxs-lookup"><span data-stu-id="db85b-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="db85b-118">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Clear-Content` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="db85b-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="db85b-119">Zastępowanie [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metodę, aby zmienić zachowanie `Get-Content` polecenia cmdlet, co pozwala na pobieranie zawartości elementu.</span><span class="sxs-lookup"><span data-stu-id="db85b-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="db85b-120">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Get-Content` polecenia cmdlet.).</span><span class="sxs-lookup"><span data-stu-id="db85b-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="db85b-121">Zastępowanie [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) metodę, aby zmienić zachowanie `Set-Content` polecenia cmdlet, umożliwiając użytkownikowi na aktualizowanie zawartości elementu.</span><span class="sxs-lookup"><span data-stu-id="db85b-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="db85b-122">(Ten przykład pokazuje, jak dodać parametry dynamiczne `Set-Content` polecenia cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="db85b-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="db85b-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="db85b-123">Example</span></span>

<span data-ttu-id="db85b-124">W tym przykładzie pokazano, jak zastąpić metody potrzebne do wyczyszczenia, pobieranie i ustawianie zawartość elementów danych Microsoft Access bazy.</span><span class="sxs-lookup"><span data-stu-id="db85b-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="db85b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db85b-125">See Also</span></span>

[<span data-ttu-id="db85b-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="db85b-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="db85b-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="db85b-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="db85b-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="db85b-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="db85b-129">Projektowanie dostawcą Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="db85b-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)